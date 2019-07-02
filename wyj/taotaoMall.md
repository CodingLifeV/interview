<!-- TOC -->

- [淘淘商城](#淘淘商城)
    - [一、项目介绍](#一项目介绍)
        - [1、系统功能](#1系统功能)
        - [2、项目架构](#2项目架构)
    - [项目搭建](#项目搭建)
        - [1、使用Maven的好处](#1使用maven的好处)
        - [2、工程搭建](#2工程搭建)
    - [系统功能分析](#系统功能分析)
        - [1、首页轮播图功能分析](#1首页轮播图功能分析)
        - [2、首页轮播图数据库表结构分析](#2首页轮播图数据库表结构分析)
    - [redis项目相关](#redis项目相关)
        - [1、redis集群搭建](#1redis集群搭建)
        - [2、Jedis的使用](#2jedis的使用)
        - [3、redis代码实现](#3redis代码实现)
    - [redis基础知识](#redis基础知识)
        - [1、使用redis原因](#1使用redis原因)
        - [2、redis数据类型](#2redis数据类型)
        - [3、redis和memcached的区别？为什么不用memcached？](#3redis和memcached的区别为什么不用memcached)
        - [4、redis持久化方案](#4redis持久化方案)
        - [5、redis底层如何实现](#5redis底层如何实现)
        - [6、redis如何实现数据的同步与更新？](#6redis如何实现数据的同步与更新)
        - [#、redis应用场景](#redis应用场景)
    - [分布式基础知识](#分布式基础知识)
        - [1、分布式概念](#1分布式概念)
        - [2、分布式锁](#2分布式锁)
    - [七、Solr 集群](#七solr-集群)

<!-- /TOC -->

# 淘淘商城
## 一、项目介绍
### 1、系统功能
商城项目基于SOA架构，分为两部分：前台和后台。

* 后台：给商城管理员使用，其主要功能是用于进行商品信息的添加修改，删除，以及内容发布。后台采用Maven聚合工程和ssm框架。

  我们将商品的图片放在特殊的图片服务器中，将大文本信息放在文件服务器中，使用nginx反向代理管理图片服务器，文件服务器和数据库，由于后台访问量比较少因此不考虑缓存和分布式。

* 前台项目：采用Maven管理jar包和ssm框架，前台项目和后台公用同一个数据库，前台主要是供客户访问，包括商城页面的展示，搜索功能 ，商品详情展示，单点登陆系统，购物车和订单系统等。

  由于前台首页轮播图的访问量比较大，故此我们采用的是分布式架构，使用redis作用缓存，并搭建redis集群。我们将经常访问的数据放在redis中，并设置过期时间，以减缓大量访问时数据库的压力；对于商城项目而言，商品搜索时比较常见的，对于搜索的实现我们使用solr搜索引擎，==只需要简单配置就可以实现全文搜索，由于solr中默认是没有中文分析器，因此需要我们配置，接下来将数据库中的数据导入，solr自带缓存，所以不需要再配置redis；单点登陆系统主要是session和cookie，使用redis模拟session，将用户信息传给前台，当再某些特殊业务时需要强制登陆。==
### 2、项目架构

* 项目基于SOA架构，把工程都拆分成服务层工程、表现层工程和持久层。服务层中包含业务逻辑，只需要对外提供服务即可。表现层只需要处理和页面的交互，业务逻辑都是调用服务层的服务来实现
* ==表现层通过服务中间件Dubbo与服务层进行交互==
* ==服务层与redis缓存交互，redis缓存与持久层进行交互==
* ==Mysql数据库通过MyCat数据库中间件进行整合==
* 服务层中的搜索服务使用solr搜索引擎
![](https://ws1.sinaimg.cn/large/d4556b75ly1g3rg4tldhhj20o60eanpd.jpg)

## 项目搭建
### 1、使用Maven的好处
1. Jar包的管理
2. 工程之间的依赖管理
3. 自动打包
4. 统一的版本的控制

### 2、工程搭建

* Maven的常见打包方式：jar、war、pom。
pom工程一般都是父工程，用在聚合工程，管理jar包的版本、maven插件的版本、统一的依赖管理；
war包主要部署tomcat；单一的工程打包成jar包，别人用它的时候只需要依赖它的坐标就好了
        
![](https://ws1.sinaimg.cn/large/d4556b75ly1g3p7m70vjbj20l807rt99.jpg)

* 依赖结构（web-->interface表示taotao-manager-web依赖taotao-manager-interface）

`taotao-manager-web`依赖`taotao-manager-interface`

`taotao-manager-service`依赖`taotao-manager-interface/taotao-manager-dao`

`taotao-manager-interface`依赖`taotao-manager-pojo`

`taotao-manager-dao`依赖`taotao-manager-pojo`

在pom文件中依赖关系这样添加：
```
<dependencies>
		<!-- 依赖taotao-manager-pojo -->
		<dependency>
			<groupId>com.taotao</groupId>
			<artifactId>taotao-manager-pojo</artifactId>
			<version>0.0.1-SNAPSHOT</version>
		</dependency>
<dependencies>
```
以上是 taotao-manager 工程下模块taotao-manager-dao的pom.xml文件中添加的依赖关系


## 系统功能分析
### 1、首页轮播图功能分析

首页轮播图的展示只需要后台提供轮播图图片数据，将图片数据转化为一个json数据之后提供给前端，便可以进行展示。

数据的展示是在taotao-portal-web工程下的 index.jsp文件中，代码中的ad1变量便是后端提供用来展示的：
```
    if ( !cfg.DATA_MSlide ) {
        cfg.DATA_MSlide=[];
    }

	var data = ${ad1};
```

在taotao-portal-web工程下写一个controller，实现页面跳转，跳转到index.jsp这个页面：

```java
/**
 * 展示首页
 */
@Controller
public class PageController {
	
	@Autowired
	private ContentService contentservice;
	
	@Value("${AD1_CATEGORY_ID}")
	private Long categoryId;
	
	@Value("${AD1_HEIGHT_B}")
	private String AD1_HEIGHT_B;
	
	@Value("${AD1_HEIGHT}")
	private String AD1_HEIGHT;
	
	@Value("${AD1_WIDTH}")
	private String AD1_WIDTH;
	
	@Value("${AD1_WIDTH_B}")
	private String AD1_WIDTH_B;
	/**
	 * 展示首页
	 * @return
	 */
	//接收URL的请求http://localhost:8082/index.html
	@RequestMapping("/index")
	public String showIndex(Model model){
		//引入服务
		//注入服务
		//添加业务逻辑，根据内容分类的id查询内容列表
		List<TbContent> contentlist = contentservice.getContentListByCatId(categoryId);
		//转成自定义的POJO：AD1NOde的列表
		List<Ad1Node> nodes = new ArrayList<>();
		for (TbContent tbContent : contentlist) {
			Ad1Node node = new Ad1Node();
			node.setAlt(tbContent.getSubTitle());
			node.setHeight(AD1_HEIGHT);
			node.setHeightB(AD1_HEIGHT_B);
			node.setHref(tbContent.getUrl());
			node.setSrc(tbContent.getPic());
			node.setSrcB(tbContent.getPic2());
			node.setWidth(AD1_WIDTH);
			node.setWidthB(AD1_WIDTH_B);
			nodes.add(node);
		}
		//传递数据给JSP
		model.addAttribute("ad1", JsonUtils.objectToJson(nodes));
	    //响应jsp
		return "index";
	}
	
}

```


**PageController.java 文件分析：**

1. PageController.java 中实现一个映射请求方法 showIndex(Model model)，该方法实现根据内容分类的`id`
查询内容表数据，查询出来的数据存储在一个 List 列表中，最后转化成 json 数据后传递给前端显示页面。

2. List 列表中存储的是内容表数据，我们把内容表数据定义为了一个pojo：TbContent，与数据库中的tb_content表对应，把内容分类表数据定义为了另一个pojo：TbContentCategory，与数据库中的tb_contentCategory表对应

3. PageController.java 中通过 Spring 自动注入一个内容服务接口类对象 ContentService ，该接口及其实现在工程taotao-content下，通过方法getContentListByCatId(Long categoryId) 从数据库或者redis缓存中查询内容表数据返回给 PageController 类中的 showIndex() 方法。其中， `categoryId`表示内容分类`id`号

**taotao-content 工程分析:**

后台数据的提供以及转化主要在工程taotao-content中实现，taotao-content是项目中的一个聚合工程，包括 taotao-content-interface 和 taotao-content-service 模块（通过new Maven Module创建）
  
  * taotao-content-interface 内容处理的接口，依赖结构为:

    `taotao-content-interface` 依赖 `taotao-content-pojo`

    该接口主要定义了二个方法：saveContent()和getContentListByCatId()，这二个方法的实现使用了redis缓存，代码如下：
    
    ```java
    public interface ContentService {
    	/**
    	 * 插入内容表
    	 * @param content
    	 * @return
    	 */
    	public TaotaoResult saveContent(TbContent content);
    	/**
    	 * 根据内容分类的ID 查询其下的内容列表
    	 * @param categoryId
    	 * @return
    	 */
    	public List<TbContent> getContentListByCatId(Long categoryId);
    }
    ```


* taotao-content-service 内容处理接口的实现，该模块ContentServiceImpl类实现了taotao-content-interface模块中接口类ContentService定义的方法，并且使用了redis缓存，依赖结构为:

  `taotao-content-service` 依赖 `taotao-content-dao`
  
  `taotao-content-service` 依赖 `taotao-content-interface`
 
* getContentListByCatId方法通过内容分类`id`返回内容列表，流程如下：
1. 判断redis中是否有数据，如果有直接从redis中取出数据返回
2. 如果redis没有数据，从数据库中查询记录返回
3. 将数据写入到redis数据库中

* saveContent方法把新的内容数据插入到数据库的内容表中，此时数据库中的数据和redis缓存数据不一致，因此需要清空redis缓存。

  JedisClientPool实现类代码如下：

    ```java
    @Service
    public class ContentServiceImpl implements ContentService {
    
    	@Autowired
    	private JedisClient client;
    	
    	@Autowired
    	private TbContentMapper mapper;
    	
    	@Value("${CONTENT_KEY}")
    	private String CONTENT_KEY;
    	
    	@Override
    	public TaotaoResult saveContent(TbContent content) {
    		//1.注入mapper
    		
    		//2.补全其他的属性
    		content.setCreated(new Date());
    		content.setUpdated(content.getCreated());
    		//3.插入内容表中
    		mapper.insertSelective(content);
    		
    		//当添加内容的时候，需要清空此内容所属的分类下的所有的缓存
    		try {
    			client.hdel(CONTENT_KEY, content.getCategoryId()+"");
    			System.out.println("当插入时，清空缓存!!!!!!!!!!");
    		} catch (Exception e) {
    			e.printStackTrace();
    		}
    		
    		return TaotaoResult.ok();
    	}
    
    	@Override
    	public List<TbContent> getContentListByCatId(Long categoryId) {
    		
    		//判断是否redis中有数据，如果有直接从redis中获取数据返回
    		
    		try {
    		    //从redis数据库中获取内容分类下的所有的内容。
    			String jsonstr = client.hget(CONTENT_KEY, categoryId+"");
    			//如果存在，说明有缓存
    			if(StringUtils.isNotBlank(jsonstr)){
    			System.out.println("这里有缓存啦！！！！！");
    				return JsonUtils.jsonToList(jsonstr, TbContent.class);
    			}
    		} catch (Exception e1) {
    			e1.printStackTrace();
    		}
    		
    		//1.注入mapper
    		//2.创建example
    		TbContentExample example = new TbContentExample();
    		//3.设置查询的条件
    		example.createCriteria().andCategoryIdEqualTo(categoryId);//select × from tbcontent where category_id=1
    		//4.执行查询
    		List<TbContent> list = mapper.selectByExample(example);
    		
    		//将数据写入到redis数据库中   
    		try {
    			System.out.println("没有缓存！！！！！！");
    			client.hset(CONTENT_KEY, categoryId+"", JsonUtils.objectToJson(list));
    		} catch (Exception e) {
    			e.printStackTrace();
    		}
    				
    		return list;
    	}
    
    }
    
    ```








### 2、首页轮播图数据库表结构分析

![](https://ws1.sinaimg.cn/large/d4556b75ly1g3rg4bp7ywj20yp0jgwko.jpg)

可以根据首页大广告位的数据结构设计一张表，进行增删改查管理，其他部分的展示内容同样可以设计表，进行增删改查。如果每一个前端展示内容（大广告位、小广告位等等），单独建立表，进行CRUD操作，会有以下问题
1. 页面大量信息堆积，发布显得异常沉重
2. 内容繁杂，管理效率低下
3. 许多工作需要技术人员配合完成
4. 改版工作量大，系统扩展性差

解决方案：
对首页展示功能进行抽取，把首页的每个展示功能（如大广告位，淘淘快报），看作是一个分类
每个展示功能里面展示的多条信息看作是分类下的内容

例如：首页大广告，对应的是大广告分类，而大广告位展示的多张图片，就是大广告分类下的内容。
前台需要获取大广告的图片，只需要根据大广告的id查询对应的内容即可

这样就需要两张表：一张内容分类表 `tb_content_category` ；一张内容表 `tb_content`

* tb_content_category 表：

```
DROP TABLE IF EXISTS `tb_content_category`;
CREATE TABLE `tb_content_category` (
  `id` bigint(20) NOT NULL AUTO_INCREMENT COMMENT '类目ID',
  `parent_id` bigint(20) DEFAULT NULL COMMENT '父类目ID=0时，代表的是一级的类目',
  `name` varchar(50) DEFAULT NULL COMMENT '分类名称',
  `status` int(1) DEFAULT '1' COMMENT '状态。可选值:1(正常),2(删除)',
  `sort_order` int(4) DEFAULT NULL COMMENT '排列序号，表示同级类目的展现次序，如数值相等则按名称次序排列。取值范围:大于零的整数',
  `is_parent` tinyint(1) DEFAULT '1' COMMENT '该类目是否为父类目，1为true，0为false',
  `created` datetime DEFAULT NULL COMMENT '创建时间',
  `updated` datetime DEFAULT NULL COMMENT '创建时间',
  PRIMARY KEY (`id`),
  KEY `parent_id` (`parent_id`,`status`) USING BTREE,
  KEY `sort_order` (`sort_order`)
) ENGINE=InnoDB AUTO_INCREMENT=98 DEFAULT CHARSET=utf8 COMMENT='内容分类';
```
![](https://ws1.sinaimg.cn/large/d4556b75ly1g3ri0endalj20li08vjrr.jpg)

将内容分类设置为一个树形结构，最大的分类为一级类目，一级类目下划分子类目，以此表中定义了属性`parent_id`， `is_parent`；

==`status` 表示
`sort_order`表示==

* tb_content 表：

```
DROP TABLE IF EXISTS `tb_content`;
CREATE TABLE `tb_content` (
  `id` bigint(20) NOT NULL AUTO_INCREMENT,
  `category_id` bigint(20) NOT NULL COMMENT '内容类目ID',
  `title` varchar(200) DEFAULT NULL COMMENT '内容标题',
  `sub_title` varchar(100) DEFAULT NULL COMMENT '子标题',
  `title_desc` varchar(500) DEFAULT NULL COMMENT '标题描述',
  `url` varchar(500) DEFAULT NULL COMMENT '图片绝对路径',
  `pic` varchar(300) DEFAULT NULL COMMENT '图片1',
  `pic2` varchar(300) DEFAULT NULL COMMENT '图片2',
  `content` text COMMENT '内容',
  `created` datetime DEFAULT NULL,
  `updated` datetime DEFAULT NULL,
  PRIMARY KEY (`id`),
  KEY `category_id` (`category_id`),
  KEY `updated` (`updated`)
) ENGINE=InnoDB AUTO_INCREMENT=32 DEFAULT CHARSET=utf8;
```
![](https://ws1.sinaimg.cn/large/d4556b75ly1g3ri0u7imyj20wq038t8u.jpg)

设计二个字段`pic`，`pic2`，为了在不同的电脑展示（有的横屏，有的宽屏）



## redis项目相关

### 1、redis集群搭建

**redis集群概念：**

单机处理到达瓶颈的时候，把单机复制几份，这样就构成了一个“集群”。集群中每台服务器就叫做这个集群的一个“节点”，所有节点构成了一个集群。每个节点都提供相同的服务。

**方案：**

设计三个主节点，因为投票容错机制要求超过半数节点认为某个节点挂了该节点才是挂了，所以2个节点无法构成集群。要保证集群的高可用，需要每个节点都有从节点，也就是备份节点，所以Redis集群至少需要6台服务器。从而实现[redis集群的哈希slot和节点主从关系](https://app.yinxiang.com/fx/07027c47-921f-4432-9cad-7e850e45fae3)。我们搭建了一个伪分布式：在一台电脑运行6个redis实例，每一个redis实例端口需要设置不同（设置为7001到7006）

**redis集群搭建：**

[windows环境下搭建](https://www.cnblogs.com/yaozb/p/6911395.html)

[linux环境下搭建](https://blog.csdn.net/qq_42815754/article/details/82912130)

一般集群的搭建在linux下，这里搭建在了windows环境下。

* 节点创建流程：

1. 在下载好的redis目录中创建一个redis-cluster目录，用于放置集群节点

2. redis目录中创建六个文件夹（redis1~redis6）分别放置6个集群节点：
![](https://ws1.sinaimg.cn/large/d4556b75ly1g3vv1oqjjhj20eb05p0sy.jpg)

3. 修改文件夹中得分配置文件redis.windows.conf，配置内容如下：
port修改为7001~7006， 打开cluster-enabled：
    ```
    port 7001
    cluster-enabled yes
    ```
4. 开启redis服务，具体开启控制台，在当前文件夹执行：
   >redis-server.exe redis.windows.conf

5. 把redis部署到服务中，在控制台执行命令：
   > redis-server --service-install redis.windows.conf --service-name redis7001
  
   我的服务名称按照redis+端口号创建了。

创建好了节点，之后开始创建集群

* 集群创建流程：

1. 安装Ruby工具所需要的运行环境和ruby包（ruby gems）
   1. 安装此环境的原因是因为我们需要使用Ruby Gems中的redis-trib.rb来创建和操作集群
   2. 通过此Ruby包管理来获取操作Redis集群的redis-trib.rb

2. 把ruby工具（redis-trib.rb）复制到redis-cluster目录下
3. 打开服务器当前的端口7001~7006，输入创建集群命令,根据自己的服务器ip输入对应的ip地址：
    >C:Redis\redis-cluster>redis-trib.rb create --replicas 1 
10.1.16.43:7001 10.1.16.43:7002 10.1.16.43:7002 10.1.16.43:7004 10.1.16.43:7005 10.1.16.43:7006

    之后会出现三个主节点master，主节点会分配到具体的slot槽位，并为每一个master分配一个从结点：
    ![](https://ws1.sinaimg.cn/large/d4556b75ly1g3w0v83im4j20ib0bl74j.jpg)
4. 之后启动集群处理数据时，输入命令：
    >redis-cli -h <IP地址> -p <端口号> -c
   
    `-c`表示启动集群。

### 2、Jedis的使用

redis集群在代码中的使用需要在taotao-content工程下的模块taotao-content-service的pom.xml文件中添加Jedis依赖：

```java
<dependency>
			<groupId>redis.clients</groupId>
			<artifactId>jedis</artifactId>
			<version>${jedis.version}</version>
</dependency>
```

首页轮播图中redis的实现代码也是写在taotao-content-service下的。因为集群是比较消耗成本的，所以我们在项目整合中开发一个接口 JedisClient，有单机版的实现类JedisClientPool和集群版的实现类JedisClientCluster。使用时可以面向接口开发，不影响业务逻辑，使用spring管理实现类，部署时切换实现类即可。JedisClient 接口定义如下：

```java
public interface JedisClient {

	String set(String key, String value);
	String get(String key);
	Boolean exists(String key);
	Long expire(String key, int seconds);
	Long ttl(String key);
	Long incr(String key);
	Long hset(String key, String field, String value);
	String hget(String key, String field);	
	Long hdel(String key,String... field);//删除hkey
	
}
```
实现类JedisClientCluster通过Spring自动注入JedisCluster来重写接口方法；实现类JedisClientPool通过Spring自动注入JedisPool来重写接口方法。代码片段如下：


```java
public class JedisClientCluster implements JedisClient {
	
	@Autowired
	private JedisCluster jedisCluster;

	@Override
	public String set(String key, String value) {
		return jedisCluster.set(key, value);
	}
    ...
}
```


```
public class JedisClientPool implements JedisClient {
	
	@Autowired
	private JedisPool jedisPool;

	@Override
	public String set(String key, String value) {
		Jedis jedis = jedisPool.getResource();
		String result = jedis.set(key, value);
		jedis.close();
		return result;
	}
    ...
}
```

Spring的自动注入需要配置 xml 文件，项目中我们单独写了一个xml文件并且命名为`applicationContext-redis.xml`，单机版和集群版的bean通过构造器注入的方式进行属性注入：代码如下：

```
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
	xmlns:context="http://www.springframework.org/schema/context" xmlns:p="http://www.springframework.org/schema/p"
	xmlns:aop="http://www.springframework.org/schema/aop" >
	
	<!-- 配置单机版的 -->
	<bean class="redis.clients.jedis.JedisPool">
		<constructor-arg name="host" value="192.168.25.153"></constructor-arg>
		<constructor-arg name="port" value="6379"></constructor-arg>
	</bean>
	<bean class="com.taotao.content.jedis.JedisClientPool"></bean>
	
	<!-- 配置集群版 -->
	<bean class="redis.clients.jedis.JedisCluster">
		<constructor-arg name="nodes">
			<set>
				<bean class="redis.clients.jedis.HostAndPort">
					<constructor-arg name="host" value="10.1.16.43" />
					<constructor-arg name="port" value="7001" />
				</bean>
				<bean class="redis.clients.jedis.HostAndPort">
					<constructor-arg name="host" value="10.1.16.43" />
					<constructor-arg name="port" value="7002" />
				</bean>
				<bean class="redis.clients.jedis.HostAndPort">
					<constructor-arg name="host" value="10.1.16.43" />
					<constructor-arg name="port" value="7003" />
				</bean>
				<bean class="redis.clients.jedis.HostAndPort">
					<constructor-arg name="host" value="10.1.16.43" />
					<constructor-arg name="port" value="7004" />
				</bean>
				<bean class="redis.clients.jedis.HostAndPort">
					<constructor-arg name="host" value="10.1.16.43" />
					<constructor-arg name="port" value="7005" />
				</bean>
				<bean class="redis.clients.jedis.HostAndPort">
					<constructor-arg name="host" value="10.1.16.43" />
					<constructor-arg name="port" value="7006" />
				</bean>
			</set>
		</constructor-arg>
	</bean>
	<bean class="com.taotao.content.jedis.JedisClientCluster"></bean>
	
</beans>
```

### 3、redis代码实现

redis代码的实现主要在

















## redis基础知识

### 1、使用redis原因
* 基于redis的特性：

1. 性能极高：Redis是基于内存的，故此具有较高的读写频率。（能支持超过 100K+ 每秒的）
2. 丰富的数据类型：Redis可以存储键和五种不同类型的值之间的映射，键的类型只能为字符串，值支持五种数据类型：字符串、列表、集合、散列表、有序集合。
3. 原子性：Redis的所有操作都是原子性的，同时Redis还支持对几个操作全并后的原子性执行
4. 丰富的特性：Redis还支持发布订阅（publish/subscribe）, 通知, 键的过期时间等特性
5. 支持数据的持久化。redis会周期性的把更新的数据写入磁盘或者把修改操作写入追加的记录文件，并且在此基础上实现了master-slave(主从)同步

* 基于项目：

  首页是系统的门户，也就是系统的入口，所以首页的访问量是这个系统最大的。如果每次展示首页都从数据库中查询首页的内容信息，那么势必会对数据库造成很大的压力，所以需要使用缓存来减轻数据库压力，redis可以较好的实现缓存

### 2、redis数据类型
Redis支持五种数据类型：string（字符串），list（列表），set（集合），hash（哈希）及zset(sorted set：有序集合)。redis中的数据都是字符串,redis是单线程，不适合存储比较大的数据

* string：存储字符串、整数、浮点数
    
  1. 设置值：`set key value`
  2. 获取值：`get key`
  3. 删除键值：`del key`
  4. 值加一：`incr key`
  5. 值减一：`decr key`

* list：数据结构中的：双链表+队列，
	可作为链表 ，从左添加元素  也可以从右添加元素
  1. 从右边添加元素: `rpush listKey value1 value2 ... valueN`
  2. 从左边添加元素: `lpush listKey value1 value2 ... valueN`
  3. 获取指定范围内元素：`lrange listKey 0 -1`（-1代表最后一个元素，-2代表倒数第二个元素，以此类推）
  4. 从左边取值，删除：`lpop listKey`
  5. 从右边取值，删除：`rpop listKey`

* set：无顺序，不能重复，集合是通过哈希表实现的，所以添加，删除，查找的复杂度都是O(1)
  1. 添加元素：`sadd setKey value1 value2 ... valueN`
  2. 查询元素：`smembers setKey`
  3. 删除元素：`srem keySet value`
  
* hash：相当于一个key 对应一个map (map中又是key-value)
  1. 设置值：`hset hashKey sub-key value`
  2. 获取值：`hget hashKey sub-key`
  3. 获取所有值：`hgetall hashKey`
  4. 删除值：`hdel hashKey sub-key`

* zset：有顺序，不能重复
  1. 添加元素： `zadd key score1 member1 [score2 member2] `
  2. 查看分数：
     1. 从小到大：`zrange key 0 -1 [withscores]`：
     2. 从大到小：`zrevrange key 0 -1 [withscores]`
  3. 对元素member增加score：`zincrby key score member`


### 3、redis和memcached的区别？为什么不用memcached？

1. 数据类型：Memcached 仅支持字符串类型，而Redis支持五种不同的数据类型，可以更灵活地解决问题。
2. 数据持久化：Redis 支持RDB快照和AOF日志两种持久化策略，而Memcached不支持持久化。
3. 分布式：Memcached 不支持分布式，Redis Cluster实现了分布式的支持。
4. 内存管理机制：
   1. 在Redis中，并不是所有数据都一直存储在内存中，可以将一些很久没用的 value 交换到磁盘，而Memcached的数据则会一直在内存中。
   2. Memcached将内存分割成特定长度的块来存储数据，以完全解决内存碎片的问题。但是这种方式会使得内存的利用率不高。


### 4、redis持久化方案
Redis 支持两种持久化策略：RDB 快照和 AOF 日志，而 Memcached 不支持持久化。redis 默认开启RDB，同时开启两个持久化方案，则按照AOF的持久化放案恢复数据。
1. RDB快照：

   定期将当前时刻的数据保存磁盘中，会产生一个dump.rdb文件。特点是会存在数据丢失，性能较好，可以用于数据备份。
2. AOF日志
  
   所有对redis的操作命令记录在aof文件中，恢复数据时重新执行一遍即可。特点是每秒保存，数据比较完整，耗费性能。

   AOF开启设置：修改 redis.conf 文件，将appendonly设置为yes，数据存在appendonly.aof文件中


### 5、redis底层如何实现

Redis内部维护一个db数组，每个db都是一个数据库，默认情况下Redis会创建16个数据库。我们可以通过select命令来切换数据库，如select 1切换到数据库号为1的数据库。select实现是通过修改客户端的db指针，通过指针指向不同的数据库来实现数据库的切换操作的。

![](https://ws1.sinaimg.cn/large/d4556b75gy1g3yeo8ewlpj209l0ddq3a.jpg)

### 6、redis如何实现数据的同步与更新？

每次在键空间读取一个键之后，服务器会更新键的LRU时间，用于计算键的闲置时间。如果服务器在读取一个键时发现该键已经过期，那么服务器会先删除这个过期键，然后才执行后续操作。如果有客户端使用watch命令监视了某个键，那么服务器在对被监视的键进行修改之后，会将这个键标记为dirty，从而让事务注意到这个键被修改过。服务器每次修改一个键之后，都会对键计数器的值+1，这个计数器用来触发服务器的持久化操作。如果服务器开启了数据库通知功能，那么在对键进行修改之后，服务器将按配置发送相应的数据库通知。

### #、redis应用场景




## 分布式基础知识
### 1、分布式概念

分布式结构就是将一个完整的系统，按照业务功能，拆分成一个个独立的子系统，在分布式结构中，每个子系统就被称为“服务”。这些子系统能够独立运行在web容器中，它们之间通过RPC方式通信。

### 2、分布式锁

[分布式锁入门以及三种实现方式](https://app.yinxiang.com/fx/b38ebbb8-5c1c-48d6-b172-770de099b756)

**实现方式：**

* 基于数据库实现分布式锁

  在数据库中创建一个表，表中包含方法名等字段，并在方法名字段上创建唯一索引，想要执行某个方法，就使用这个方法名向表中插入数据，成功插入则获取锁，执行完成后删除对应的行数据释放锁。
  
  缺点：锁没有失效时间，不可重入

* 基于redis实现

  使用Redis实现分布式锁的时候，主要会使用到三个命令：
  > SETNX key val
  
  当且仅当key不存在时，set一个key为val的字符串，返回1；若key存在，则什么都不做，返回0;类似于数据库的唯一索引。
  > expire key timeout
  
  为key设置一个过期时间，单位为second，超过这个时间锁会自动释放，避免死锁。避免数据库唯一索引实现方式中释放锁失败的问题。
  >delete key
  
  删除key。
  
  **思想：**
  1. 获取锁的时候，使用setnx加锁，并使用expire命令为锁添加一个过期时间，超过该时间则自动释放锁，锁的value值为一个随机生成的UUID，通过此在释放锁的时候进行判断。
  2. 获取锁的时候还设置一个获取的超时时间，若超过这个时间则放弃获取锁。
  3. 释放锁的时候，通过UUID判断是不是该锁，若是该锁，则执行delete进行锁释放。
  
* 基于ZooKeeper的实现方式

## 七、Solr 集群






