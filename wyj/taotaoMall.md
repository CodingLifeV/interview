<!-- TOC -->

- [项目介绍](#项目介绍)
  - [系统功能](#系统功能)
  - [项目架构](#项目架构)
- [项目搭建](#项目搭建)
  - [使用 Maven 的好处](#使用-maven-的好处)
  - [工程搭建](#工程搭建)
- [系统功能分析](#系统功能分析)
  - [首页轮播图功能分析](#首页轮播图功能分析)
  - [首页轮播图数据库表结构分析](#首页轮播图数据库表结构分析)
- [redis 项目相关](#redis-项目相关)
  - [redis 集群搭建](#redis-集群搭建)
  - [Jedis 的使用](#jedis-的使用)
- [Solr 集群](#solr-集群)
  - [solr 服务搭建](#solr-服务搭建)
- [Zookeeper 集群](#zookeeper-集群)
  - [zookeeper 集群搭建](#zookeeper-集群搭建)
- [ActiveMQ 消息队列](#activemq-消息队列)
  - [概念](#概念)
  - [消息模型](#消息模型)
  - [使用场景](#使用场景)
  - [可靠性](#可靠性)
- [ActiveMQ 消息队列项目相关](#activemq-消息队列项目相关)
  - [环境搭建](#环境搭建)
  - [代码实例](#代码实例)
    - [生产者](#生产者)
    - [消费者](#消费者)

<!-- /TOC -->

# 项目介绍

## 系统功能

商城项目基于 SOA 架构，分为两部分：前台和后台。

- 后台：给商城管理员使用，其主要功能是用于进行商品信息的添加修改，删除，以及内容发布。后台采用 Maven 聚合工程和 ssm 框架。

  我们将商品的图片放在特殊的图片服务器中，将大文本信息放在文件服务器中，使用 nginx 反向代理管理图片服务器，文件服务器和数据库，由于后台访问量比较少因此不考虑缓存和分布式。

- 前台项目：采用 Maven 管理 jar 包和 ssm 框架，前台项目和后台公用同一个数据库，前台主要是供客户访问，包括商城页面的展示，搜索功能 ，商品详情展示，单点登陆系统，购物车和订单系统等。

  由于前台首页轮播图的访问量比较大，故此我们采用的是分布式架构，使用 redis 作用缓存，并搭建 redis 集群。我们将经常访问的数据放在 redis 中，并设置过期时间，以减缓大量访问时数据库的压力；对于商城项目而言，商品搜索时比较常见的，对于搜索的实现我们使用 solr 搜索引擎，只需要简单配置就可以实现全文搜索，由于 solr 中默认是没有中文分析器，因此需要我们配置，接下来将数据库中的数据导入，solr 自带缓存，所以不需要再配置 redis；单点登陆系统主要是 session 和 cookie，使用 redis 模拟 session，将用户信息传给前台，当再某些特殊业务时需要强制登陆。

## 项目架构

- 项目基于 SOA 架构，把工程都拆分成服务层工程、表现层工程和持久层。服务层中包含业务逻辑，只需要对外提供服务即可。表现层只需要处理和页面的交互，业务逻辑都是调用服务层的服务来实现
- 表现层通过服务中间件 Dubbo 与服务层进行交互
- 服务层与 redis 缓存交互，redis 缓存与持久层进行交互
- Mysql 数据库通过 MyCat 数据库中间件进行整合
- 服务层中的搜索服务使用 solr 搜索引擎
  ![](https://ws1.sinaimg.cn/large/d4556b75ly1g3rg4tldhhj20o60eanpd.jpg)

# 项目搭建

## 使用 Maven 的好处

1. Jar 包的管理
2. 工程之间的依赖管理
3. 自动打包
4. 统一的版本的控制

## 工程搭建

**1. Maven 的常见打包方式：**

三种：jar、war、pom。  
pom 工程一般都是父工程，用在聚合工程，管理 jar 包的版本、maven 插件的版本、统一的依赖管理；  
war 包主要部署 tomcat；  
单一的工程打包成 jar 包，别人用它的时候只需要依赖它的坐标就好了

![](https://ws1.sinaimg.cn/large/d4556b75ly1g3p7m70vjbj20l807rt99.jpg)

**2. 依赖结构**

`taotao-manager-web` 依赖 `taotao-manager-interface`

`taotao-manager-service` 依赖 `taotao-manager-interface` 和 `taotao-manager-dao`

`taotao-manager-interface` 依赖 `taotao-manager-pojo`

`taotao-manager-dao` 依赖 `taotao-manager-pojo`

在 pom 文件中依赖关系这样添加：

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

以上是 taotao-manager 工程下模块 taotao-manager-dao 的 pom.xml 文件中添加的依赖关系

# 系统功能分析

## 首页轮播图功能分析

首页轮播图的展示只需要后台提供轮播图图片数据，将图片数据转化为一个 json 数据之后提供给前端，便可以进行展示。

数据的展示是在 taotao-portal-web 工程下的 index.jsp 文件中，代码中的 ad1 变量便是后端提供用来展示的：

```
    if ( !cfg.DATA_MSlide ) {
        cfg.DATA_MSlide=[];
    }

	var data = ${ad1};
```

在 taotao-portal-web 工程下写一个 controller，实现页面跳转，跳转到 index.jsp 这个页面：

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

2. List 列表中存储的是内容表数据，我们把内容表数据定义为了一个 pojo：TbContent，与数据库中的 tb_content 表对应，把内容分类表数据定义为了另一个 pojo：TbContentCategory，与数据库中的 tb_contentCategory 表对应

3. PageController.java 中通过 Spring 自动注入一个内容服务接口类对象 ContentService ，该接口及其实现在工程 taotao-content 下，通过方法 getContentListByCatId(Long categoryId) 从数据库或者 redis 缓存中查询内容表数据返回给 PageController 类中的 showIndex() 方法。其中， `categoryId`表示内容分类`id`号

**taotao-content 工程分析:**

后台数据的提供以及转化主要在工程 taotao-content 中实现，taotao-content 是项目中的一个聚合工程，包括 taotao-content-interface 和 taotao-content-service 模块（通过 new Maven Module 创建）

- taotao-content-interface 内容处理的接口，依赖结构为:

  `taotao-content-interface` 依赖 `taotao-content-pojo`

  该接口主要定义了二个方法：saveContent()和 getContentListByCatId()，这二个方法的实现使用了 redis 缓存，代码如下：

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

* taotao-content-service 内容处理接口的实现，该模块 ContentServiceImpl 类实现了 taotao-content-interface 模块中接口类 ContentService 定义的方法，并且使用了 redis 缓存，依赖结构为:

  `taotao-content-service` 依赖 `taotao-content-dao`

  `taotao-content-service` 依赖 `taotao-content-interface`

* getContentListByCatId 方法通过内容分类`id`返回内容列表，流程如下：

1. 判断 redis 中是否有数据，如果有直接从 redis 中取出数据返回
2. 如果 redis 没有数据，从数据库中查询记录返回
3. 将数据写入到 redis 数据库中

- saveContent 方法把新的内容数据插入到数据库的内容表中，此时数据库中的数据和 redis 缓存数据不一致，因此需要清空 redis 缓存。

  JedisClientPool 实现类代码如下：

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

## 首页轮播图数据库表结构分析

![](https://ws1.sinaimg.cn/large/d4556b75ly1g3rg4bp7ywj20yp0jgwko.jpg)

可以根据首页大广告位的数据结构设计一张表，进行增删改查管理，其他部分的展示内容同样可以设计表，进行增删改查。如果每一个前端展示内容（大广告位、小广告位等等），单独建立表，进行 CRUD 操作，会有以下问题

1. 页面大量信息堆积，发布显得异常沉重
2. 内容繁杂，管理效率低下
3. 许多工作需要技术人员配合完成
4. 改版工作量大，系统扩展性差

解决方案：
对首页展示功能进行抽取，把首页的每个展示功能（如大广告位，淘淘快报），看作是一个分类
每个展示功能里面展示的多条信息看作是分类下的内容

例如：首页大广告，对应的是大广告分类，而大广告位展示的多张图片，就是大广告分类下的内容。
前台需要获取大广告的图片，只需要根据大广告的 id 查询对应的内容即可

这样就需要两张表：一张内容分类表 `tb_content_category` ；一张内容表 `tb_content`

- tb_content_category 表：

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

- tb_content 表：

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

# redis 项目相关

## redis 集群搭建

**redis 集群概念：**

单机处理到达瓶颈的时候，把单机复制几份，这样就构成了一个“集群”。集群中每台服务器就叫做这个集群的一个“节点”，所有节点构成了一个集群。每个节点都提供相同的服务。

**方案：**

设计三个主节点，因为投票容错机制要求超过半数节点认为某个节点挂了该节点才是挂了，所以 2 个节点无法构成集群。要保证集群的高可用，需要每个节点都有从节点，也就是备份节点，所以 Redis 集群至少需要 6 台服务器。从而实现[redis 集群的哈希 slot 和节点主从关系](https://app.yinxiang.com/fx/07027c47-921f-4432-9cad-7e850e45fae3)。我们搭建了一个伪分布式：在一台电脑运行 6 个 redis 实例，每一个 redis 实例端口需要设置不同（设置为 7001 到 7006）

**redis 集群搭建：**

[windows 环境下搭建](https://www.cnblogs.com/yaozb/p/6911395.html)

[linux 环境下搭建](https://blog.csdn.net/qq_42815754/article/details/82912130)

**1. 单机版搭建**

1. 下载 redis 压缩包，然后解压压缩文件；
2. 进入到解压缩后的 redis 文件目录（此时可以看到 Makefile 文件），编译 redis 源文件；
3. 把编译好的 redis 源文件安装到/usr/local/redis 目录下，如果/local 目录下没有 redis 目录，会自动新建 redis 目录；
4. 进入/usr/local/redis/bin 目录，直接./redis-server 启动 redis（此时为前端启动 redis）；
5. 将 redis 启动方式改为后端启动，具体做法：把解压缩的 redis 文件下的 redis.conf 文件复制到/usr/local/redis/bin 目录下，然后修改该 redis.conf 文件->daemonize：no 改为 daemonize：yes；
6. 在/bin 目录下通过./redis-server redis.conf 启动 redis（此时为后台启动）

**2. 集群版搭建（linux 环境下）**

**节点创建:**

创建 6 个 redis 实例（6 个节点）并启动（注意使用到的 linux 命令）：

1. 在 usr/local 目录下新建 redis-cluster 目录，用于存放集群节点
   > `mkdir redis-cluster`
2. 把 redis 目录下的 bin 目录下的所有文件复制到/usr/local/redis-cluster/redis01 目录下
   > `cp -r redis/bin/ redis-cluster/redis01`
3. 删除 redis01 目录下的快照文件 dump.rdb，并且修改该目录下的 redis.cnf 文件，具体修改两处地方：一是端口号修改为 7001，二是开启集群创建模式，打开注释 `cluster-enabled yes` 即可
   > `rm -rf dump.rdb`
4. 将 redis-cluster/redis01 文件复制 5 份到 redis-cluster 目录下（redis02-redis06），创建 6 个 redis 实例，模拟 Redis 集群的 6 个节点。然后将其余 5 个文件下的 redis.conf 里面的端口号分别修改为 7002-7006
5. 创建一个 redis 节点的脚本启动文件，放别启动所有的 redis 节点，文件内容如下：
   ![](https://ws1.sinaimg.cn/large/d4556b75ly1g4sgyhx62pj20i80c6jrl.jpg)
6. 修改脚本权限使之能够执行
   > `chmod +x start-all.sh`
7. 执行 start-all.sh 脚本，启动 6 个 redis 节点
   > `./start-all.sh`
8. 查看所有的 redis 节点是否均已启动成功
   > `ps aux|grep redis`

**集群搭建：**

1. 安装 ruby 工具所需要的运行环境
   > `yum install ruby`
2. 把 ruby 相关的包安装到服务器
   > `gem install redis-3.0.0.gem`
3. 把 ruby 脚本工具复制到 usr/local/redis-cluster 目录下。这个 ruby 脚本工具在 redis 解压文件的源代码里，即 redis/src 目录下的 redis-trib.rb 文件
   > `cp redis-trib.rb /usr/local/redis-cluster`
4. 然后使用该脚本文件搭建集群，根据自己的服务器 ip 输入对应的 ip 地址和之前设置好的端口号

   > `./redis-trib.rb`  
   > `create --replicas 1`  
   > `47.106.219.251:7001`  
   > `47.106.219.251:7002`  
   > `47.106.219.251:7003`  
   > `47.106.219.251:7004`  
   > `47.106.219.251:7005`  
   > `47.106.219.251:7006`

   ![image](https://img-blog.csdn.net/20181001161757158?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQyODE1NzU0/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

至此，Redi 集群搭建成功，上图显示了每个节点所分配的 slots（哈希槽），这里总共 6 个节点，其中 3 个是从节点，所以 3 个主节点分别映射了 0-5460、5461-10922、10933-16383 solts。

最后连接集群节点，一定要加上 `-c`，表示连接集群，连接任意一个即可：

> `redis01/redis-cli -p 7001 -c`

## Jedis 的使用

redis 集群在代码中的使用需要在 taotao-content 工程下的模块 taotao-content-service 的 pom.xml 文件中添加 Jedis 依赖：

```java
<dependency>
			<groupId>redis.clients</groupId>
			<artifactId>jedis</artifactId>
			<version>${jedis.version}</version>
</dependency>
```

首页轮播图中 redis 的实现代码也是写在 taotao-content-service 下的。因为集群是比较消耗成本的，所以我们在项目整合中开发一个接口 JedisClient，有单机版的实现类 JedisClientPool 和集群版的实现类 JedisClientCluster。使用时可以面向接口开发，不影响业务逻辑，使用 spring 管理实现类，部署时切换实现类即可。JedisClient 接口定义如下：

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

实现类 JedisClientCluster 通过 Spring 自动注入 JedisCluster 来重写接口方法；实现类 JedisClientPool 通过 Spring 自动注入 JedisPool 来重写接口方法。代码片段如下：

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

```java
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

Spring 的自动注入需要配置 xml 文件，项目中我们单独写了一个 xml 文件并且命名为`applicationContext-redis.xml`，单机版和集群版的 bean 通过构造器注入的方式进行属性注入：代码如下：

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

# Solr 集群

## solr 服务搭建

[Solr 环境搭建（linux）](https://segmentfault.com/a/1190000014779011)

在 5.0 版本之前，solr 无法作为独立的服务器进行使用，需要将其打包为 war 包部署在任何 Servlet 容器内才能使用

主要将 solr 的 war 包部署到 tomcat 的 webapps 下，再根据 solr 的依赖导入相关的 jar 包。最后配置 web.xml 来指定 solr 的主目录

1.  安装好 java 环境、tomcat 环境
2.  下载 solr 的压缩包，解压
    > `wget http://archive.apache.org/dist/lucene/solr/4.10.3/solr-4.10.3.tgz`  
    > `tar -zxvf solr-4.10.3.tgz`
3.  找到目录下的 solr.war 包，部署到 tomcat 中
    > `cd solr-4.10.3/example/webapps/`
4.  将 solr.war 包 copy 到 tomcat 的 webapps 下
    > `cp /opt/solr-4.10.3/example/webapps/solr.war /opt/tomcat-8.5.31/webapps/`
5.  解压 tomcat/webapp 下的 solr.war 包，将解压后的文件放到 webapp 下创建的 solr 文件夹下，并删除 solr.war 包
    > `mkdir solr && unzip solr.war -d solr && rm -rf solr.war`
6.  拷贝 solr 相关 jar 包到工程目录下
    > `cp /opt/solr-4.10.3/example/lib/ext/* /opt/tomcat-8.5.31/webapps/solr/WEB-INF/lib`
7.  修改 solr 的 web.xml 配置

    > `vim /opt/tomcat-8.5.31/webapps/solr/WEB-INF/web.xml`

    ```
    <env-entry>
    	<env-entry-name>solr/home</env-entry-name>
    	<env-entry-value>/opt/solr-4.10.3/example/solr</env-entry-value> <!-- solr的home目录 -->
    	<env-entry-type>java.lang.String</env-entry-type>
    </env-entry>
    ```

8.  启动
    > `/opt/tomcat-8.5.31/bin/startup.sh`
9.  查看 tomcat 后 20 行日志，防止有报错

    > `tail -n 20 /opt/tomcat-8.5.31/logs/catalina.out`

10. 访问地址：`http://127.0.0.1:8080/solr`，查看 solr 的管控台
    ![image](https://segmentfault.com/img/bVbaaQQ?w=1085&h=721)

# Zookeeper 集群

## zookeeper 集群搭建

真实的集群是需要部署在不同的服务器上的，但是在我们测试时同时启动十几个虚拟机内存会吃不消，所以这里我们搭建伪集群，重新部署一台虚拟机作为我们搭建集群的测试服务器。

[关于 Linux 系统下 zookeeper 集群的搭建](https://www.cnblogs.com/likemebee/p/7891300.html)

1. 安装 JDK
2. Zookeeper 压缩包上传到服务器，解压缩
   > `tar -xvzf zookeeper-3.4.5.tar.gz`
3. 创建 solr-cloud 文件夹，把 zookeeper 复制三份
   > `mkdir /usr/local/solr-cloud`  
   > `cp -r zookeeper-3.4.5 /usr/local/solr-cloud/zookeeper01`  
   > `cp -r zookeeper-3.4.6 /usr/local/solr-cloud/zookeeper02`  
   > `cp -r zookeeper-3.4.6 /usr/local/solr-cloud/zookeeper03`
4. 在每个 zookeeper 目录下创建一个 data 目录，在 data 目录下创建一个 myid 文件，文件名就叫做“myid”。内容就是每个实例的 id。例如 1、2、3
   > `echo 1 >> myid`
5. 修改配置文件。把每一个 zookeeper 下的 conf 目录下的 zoo_sample.cfg 文件改名为 zoo.cfg
   > `mv zoo_sample.cfg zoo.cfg`
6. 配置每一个 Zookeeper 的 dataDir（zoo.cfg 配置文件中的内容） clientPort 分别为 2181 2182 2183
   ![](https://ws1.sinaimg.cn/large/d4556b75ly1g4siwx9m06j20og0ditj0.jpg)
7. 创建启动实例的批处理文件：在 solr-cloud 下创建

   > `naco zookeeper_start_all.sh`

   .sh 编辑内容如下：

   > `cd /usr/local/solr-cloud/zookeeper01/bin`  
   > `./zkServer.sh start`  
   > `cd /usr/local/solr-cloud/zookeeper02/bin`  
   > `./zkServer.sh start`  
   > `cd /usr/local/solr-cloud/zookeeper03/bin`  
   > `./zkServer.sh start`

8. 改成可执行权限
   > `chmod u+x zookeeper_start_all.sh`
9. 启动所有的 zookeeper 实例
   > `./zookeeper_start_all.sh`
10. 查看 zookeeper 状态
    > `zookeeper01/bin/zkServer.sh status`

# ActiveMQ 消息队列

[消息队列](https://github.com/CyC2018/CS-Notes/blob/master/notes/%E6%B6%88%E6%81%AF%E9%98%9F%E5%88%97.md)

[消息中间件及 ActiveMQ 介绍](https://segmentfault.com/a/1190000014958916)

## 概念

> JMS 即 Java 消息服务（Java Message Service）应用程序接口，是一个 Java 平台中关于面向消息中间件（MOM）的 API，用于在两个应用程序之间，或分布式系统中发送消息，进行异步通信

JMS 定义了五种不同的消息正文格式，以及调用的消息类型，允许你发送并接收以一些不同形式的数据，提供现有消息格式的一些级别的兼容性：

- StreamMessage：Java 原始值的数据流
- MapMessage：一套名称-值对
- TextMessage：一个字符串对象
- ObjectMessage：一个序列化的 Java 对象
- BytesMessage：一个字节的数据流

ActiveMQ 是 Apache 软件基金下的一个开源软件，它遵循 JMS1.1 规范（Java Message Service），是消息驱动中间件软件（MOM）。

## 消息模型

**点对点**

消息生产者向消息队列中发送了一个消息之后，只能被一个消费者消费一次。

![image](https://ws1.sinaimg.cn/large/d4556b75ly1g4uu6c5mnej20jx07vt8y.jpg)

**发布/订阅**

消息生产者向频道发送一个消息之后，多个消费者可以从该频道订阅到这条消息并消费。

![image](https://ws1.sinaimg.cn/large/d4556b75ly1g4uu6m501nj20k007ejrn.jpg)

发布与订阅模式和观察者模式有以下不同：

- 观察者模式中，观察者和主题都知道对方的存在；而在发布与订阅模式中，生产者与消费者不知道对方的存在，它们之间通过频道进行通信。
- 观察者模式是同步的，当事件触发时，主题会调用观察者的方法，然后等待方法返回；而发布与订阅模式是异步的，生产者向频道发送一个消息之后，就不需要关心消费者何时去订阅这个消息，可以立即返回。
  ![image](https://ws1.sinaimg.cn/large/d4556b75ly1g4uu6v3hg7j20i60cx74p.jpg)

## 使用场景

[MQ(Message Queue)应用场景分析](https://my.oschina.net/bigdataer/blog/1923150)

[消息中间件及 ActiveMQ 介绍](https://segmentfault.com/a/1190000014958916)

**异步处理**

发送者将消息发送给消息队列之后，不需要同步等待消息接收者处理完毕，而是立即返回进行其它操作。消息接收者从消息队列中订阅消息之后异步处理。

应用场景：
注册流程中通常需要发送验证邮件来确保注册用户身份的合法性，可以使用消息队列使发送验证邮件的操作异步处理，用户在填写完注册信息之后就可以完成注册，而将发送验证邮件这一消息发送到消息队列中。

只有在业务流程允许异步处理的情况下才能这么做，例如上面的注册流程中，如果要求用户对验证邮件进行点击之后才能完成注册的话，就不能再使用消息队列。

**应用解耦**

如果模块之间不直接进行调用，模块之间耦合度就会很低，那么修改一个模块或者新增一个模块对其它模块的影响会很小，从而实现可扩展性。

通过使用消息队列，一个模块只需要向消息队列中发送消息，其它模块可以选择性地从消息队列中订阅消息从而完成调用

应用场景：

- 订单系统：用户下单后，订单系统完成持久化处理，将消息写入消息队列，返回用户，下单成功
- 库存系统：订阅下单的消息，获取下单信息，库存系统根据下单信息，进行库存操作

**流量削锋**

在高并发的场景下，如果短时间有大量的请求到达会压垮服务器。

可以将请求发送到消息队列中，服务器按照其处理能力从消息队列中订阅消息进行处理。

应用场景：秒杀活动，一般会因为流量过大，导致流量暴增，应用挂掉。为解决这个问题，一般需要在应用前端加入消息队列。可以控制活动的人数，可以缓解短时间内高流量压垮应用

## 可靠性

- 发送端的可靠性
  发送端完成操作后一定能将消息成功发送到消息队列中。

  实现方法：在本地数据库建一张消息表，将消息数据与业务数据保存在同一数据库实例里，这样就可以利用本地数据库的事务机制。事务提交成功后，将消息表中的消息转移到消息队列中，若转移消息成功则删除消息表中的数据，否则继续重传。

- 接收端的可靠性
  接收端能够从消息队列成功消费一次消息。

  两种实现方法：

  1. 保证接收端处理消息的业务逻辑具有幂等性：只要具有幂等性，那么消费多少次消息，最后处理的结果都是一样的。
  2. 保证消息具有唯一编号，并使用一张日志表来记录已经消费的消息编号。

# ActiveMQ 消息队列项目相关

## 环境搭建

[Linux 下安装 ActiveMQ-5.15.8](https://yq.aliyun.com/articles/672413)

1. 下载解压
   > `tar -xzvf apache-activemq-5.8.0-bin.tar.gz`
2. 启动 bin 目录下的 activemq 命令
   > `./activemq start`
3. 关闭并查看状态
   > `./activemq stop`  
   > `./activemq status`
4. 网页登录 ActiveMQ 管控台
   > `http://192.168.0.115:8161/admin/`

## 代码实例

### 生产者

代码如下：

```java
public class QueueProducer {
	//生产者发送消息
	@Test
	public void send() throws Exception{
		// 1.创建ConnectionFactory对象，需要指定服务端 ip 及端口号
		ConnectionFactory factory = new ActiveMQConnectionFactory("tcp://192.168.25.130:61616");
		//2.使用 ConnectionFactory 对象创建一个 Connection 对象
		Connection connection = factory.createConnection();
		//3.开启连接
		connection.start();
		//4.创建一个session对象，提供发送消息等方法
		//第一个参数：表示是否开启分布式事务（JTA）  一般是false 不开启。
		//第二个参数：就是设置消息的应答模式，如果第一个参数为false时，第二个参数设置才有意义。用的是自动应答
		Session session = connection.createSession(false, Session.AUTO_ACKNOWLEDGE);//
		//5.使用Session对象创建一个Destination对象（topic、queue），此处创建一个Queue对象。
		//参数：目的地的名称
		Queue queue = session.createQueue("queue-test");
		//6.使用Session对象创建一个Producer对象。
		MessageProducer producer = session.createProducer(queue);
		//7.构建消息的内容
		TextMessage textMessage = session.createTextMessage("queue测试发送的消息");
		//TextMessage message = session.createTextMessage();
		//message.setText("queue测试发送的消息");
		//8.发送消息
		producer.send(textMessage);
		//9.关闭资源
		producer.close();
		session.close();
		connection.close();
	}
}

```

### 消费者

代码如下：

```java
public class QueueCustomer {
	@Test
	public void recieve() throws Exception {
		//1.创建连接的工厂
		ConnectionFactory factory = new ActiveMQConnectionFactory("tcp://192.168.25.130:61616");
		//2.创建连接
		Connection connection = factory.createConnection();
		//3.开启连接
		connection.start();
		//4.创建session
		//第一个参数：表示是否开启分布式事务（JTA）  一般是false 不开启。
		//第二个参数：就是设置消息的应答模式   如果 第一个参数为false时，第二个参数设置才有意义。用的是自动应答
		Session session = connection.createSession(false, Session.AUTO_ACKNOWLEDGE);
		//5.创建接收消息的一个目的地
		Queue queue = session.createQueue("queue-test");
		//6.创建消费者
		MessageConsumer consumer = session.createConsumer(queue);
		//7.接收消息 打印
		//第一种
		/*while(true){
			Message message = consumer.receive(1000000);//设置接收消息的超时时间
			//没有接收到消息就跳出循环
			if(message==null){
				break;
			}
			if(message instanceof TextMessage){
				TextMessage message2 = (TextMessage) message;
				System.out.println("接收的消息为"+message2.getText());
			}
		}*/

		//第二种：设置一个监听器
		//这里其实开辟了一个新的线程
		consumer.setMessageListener(new MessageListener() {

			//当有消息的时候会执行以下的逻辑
			@Override
			public void onMessage(Message message) {
				if(message instanceof TextMessage){
					TextMessage message2 = (TextMessage) message;
					try {
						System.out.println("接收的消息为"+message2.getText());
					} catch (JMSException e) {
						e.printStackTrace();
					}
				}
			}
		});
		Thread.sleep(199999);
		//8.关闭资源
		consumer.close();
		session.close();
		connection.close();
	}
}

```
