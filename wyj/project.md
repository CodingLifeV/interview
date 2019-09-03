<!-- TOC -->

- [项目背景](#项目背景)
  - [项目介绍](#项目介绍)
  - [项目架构](#项目架构)
  - [使用 SOA 架构原因](#使用-soa-架构原因)
    - [SOA 架构](#soa-架构)
    - [使用到的技术](#使用到的技术)
- [项目搭建](#项目搭建)
  - [使用 Maven 的好处](#使用-maven-的好处)
  - [工程搭建](#工程搭建)
- [系统功能分析](#系统功能分析)
  - [首页数据库表结构分析](#首页数据库表结构分析)
  - [首页轮播图功能分析](#首页轮播图功能分析)
    - [Cotroller 层](#cotroller-层)
    - [配置文件](#配置文件)
    - [Service 层](#service-层)
    - [Dao 层](#dao-层)
  - [Redis 缓存同步](#redis-缓存同步)
  - [Redis 项目相关](#redis-项目相关)
    - [Redis 集群搭建](#redis-集群搭建)
    - [Jedis 的使用](#jedis-的使用)
    - [性能优化](#性能优化)
- [数据库表结构设计](#数据库表结构设计)
  - [ER 图和数据字典](#er-图和数据字典)
  - [数据中设计的范式与反范式](#数据中设计的范式与反范式)
  - [字段类型与合理的选择字段类型](#字段类型与合理的选择字段类型)
  - [表的垂直拆分和水平拆分](#表的垂直拆分和水平拆分)
  - [慢查询](#慢查询)
  - [Explain 优化查询检测](#explain-优化查询检测)
  - [索引](#索引)
- [ActiveMQ 消息队列](#activemq-消息队列)
  - [概念](#概念)
  - [消息模型](#消息模型)
  - [使用场景和优缺点](#使用场景和优缺点)
  - [可靠性](#可靠性)
- [ActiveMQ 消息队列项目相关](#activemq-消息队列项目相关)
  - [环境搭建](#环境搭建)
  - [代码实例](#代码实例)
    - [点对点生产者](#点对点生产者)
    - [点对点消费者](#点对点消费者)
    - [发布/订阅生产者消费者](#发布订阅生产者消费者)
    - [ActiveMQ 安全机制](#activemq-安全机制)
  - [ActiveMQ 整合 Spring](#activemq-整合-spring)
  - [ActiveMQ 整合到项目](#activemq-整合到项目)
    - [生产者 Producer](#生产者-producer)
    - [消费者 Consumer](#消费者-consumer)
- [Zookeeper 集群](#zookeeper-集群)
  - [zookeeper 集群搭建](#zookeeper-集群搭建)
- [Solr 集群](#solr-集群)
  - [solr 服务搭建](#solr-服务搭建)
- [项目问题排查](#项目问题排查)
  - [JVM Crash](#jvm-crash)
  - [Redis 相关错误](#redis-相关错误)
  - [JVM 调优](#jvm-调优)
  - [人员分工](#人员分工)

<!-- /TOC -->

# 项目背景

## 项目介绍

基于 SOA 架构的网上在线商城，整体以 SSM 完成整个系统后台的搭建，数据库是 MySQL 和 Redis，通过 Redis 集群的搭建实现数据的缓存，利用 ActiveMQ 实现商品同步索引库，另外项目涉及到 Dubbo 服务、Nginx 反向代理和 Solr 搜索引擎。其中自己主要负责：

1. 部分数据库表结构的设计
2. 门户首页轮播图数据显示后台功能的实现
3. Redis 集群搭建
4. 商品数据同步索引库

## 项目架构

## 使用 SOA 架构原因

一个完整的商城系统，包含了很多子系统，如后台管理系统、前台显示系统、订单系统等等。传统的系统架构将所有的子系统放在一个服务器上，缺点是：功能耦合度高、系统维护成本高以及无法解决高并发的问题。

因此考虑到分布式架构：按照功能点把系统拆分成独立的功能工程，单独为某一个节点添加服务器。优点是：模块拆分降低了模块之间的耦合度、可以进行并行开发，不同的人负责不同的子项目，而且可以灵活的进行分布式部署。但是缺点是：

1. 系统之间交互需要远程通信，需要开发接口，无形中增加了工作量
2. 各个模块有一些通用的业务逻辑无法公用

因此最终考虑到使用基于服务的 SOA 架构。

### SOA 架构

项目基于 SOA 架构（面向服务架构）。

把工程都拆分成服务层工程、表现层工程。服务层中包含业务逻辑，只需要对外提供服务即可，表现层只需要处理和页面的交互，业务逻辑都是调用服务层的服务来实现。工程都可以独立部署。优点是：

1. 继承了分布式架构的优点
2. 模块之间通过分布式的服务框架 Dubbo 来通信，只需要简单的配置即可，不需要独立开发接口，减少了工作量
3. 各个模块有一些通用的业务逻辑可以公用

### 使用到的技术

1. SSM 框架
2. MySQL、Redis 数据库
3. Solr 搜索
4. Dubbo 分布式服务框架
5. ActiveMQ 消息队列
6. Nginx (反向代理服务器）
7. MyCat (数据库中间件）

![image](https://ws1.sinaimg.cn/large/d4556b75ly1g3rg4tldhhj20o60eanpd.jpg)

# 项目搭建

## 使用 Maven 的好处

1. Jar 包的管理
2. 工程之间的依赖管理
3. 自动打包
4. 统一的版本的控制

## 工程搭建

**Maven 的常见打包方式：**

三种：jar、war、pom。

- pom：打包的工程一般都是父工程，用在聚合工程，管理 jar 包的版本、maven 插件的版本、统一的依赖管理。服务层工程的的父工程打包成 pom 工程。
- war：主要部署 tomcat，表现层的工程打包成 war 包形式。表现层打成 war 包进行发布好处是不会缺少目录，并且只管理好一个发布文件就好，并且 tomcat 服务器能够自动识别，将 war 包放在 tomcat 容器的 webapps 下，启动服务，即可运行该项目，该 war 包会自动解压出一个同名的文件夹。
- jar：用来打包单一的工程，别人用它的时候只需要依赖它的坐标就好了。服务层工程的的父工程打包成 pom 工程。

![image](https://ws1.sinaimg.cn/large/d4556b75ly1g3p7m70vjbj20l807rt99.jpg)

**工程之间的交互**

我们在项目中先写了一个父工程 `taotao-parent`，parent 项目中不存放任何代码，在`properties` 中写入版本号变量及相应版本号来集中定义依赖版本号，这里并不需要依赖具体的 jar 包，只是做为一个版本的管理，例如 mybatis 的版本管理：

```xml
<properties>
	<mybatis.spring.version>1.2.2</mybatis.spring.version>
</properties>

<dependency>
	<groupId>org.mybatis</groupId>
	<artifactId>mybatis-spring</artifactId>
	<version>${mybatis.spring.version}</version>
</dependency>
```

其它具体的子工程版本依赖时，需要在其 pom.xml 文件中添加 `parent` 标签，在标签中把 parent 项目的 pom 坐标添加进去即可：

```xml
<parent>
	<groupId>com.taotao</groupId>
	<artifactId>taotao-manager</artifactId>
	<version>0.0.1-SNAPSHOT</version>
</parent>
```

在一个项目中包含了多个模块，`modules` 标签用来管理同个项目中的各个模块。例如 taotao-manager 项目中包含四个模块，在 taotao-manager 中 pom.xml 文件中这样添加：

```xml
<modules>
	<module>taotao-manager-dao</module>
	<module>taotao-manager-pojo</module>
	<module>taotao-manager-interface</module>
	<module>taotao-manager-service</module>
</modules>
```

如果一个项目要依赖其它的项目，那么需要在其 pom.xml 文件中使用 `dependency` 标签来添加,在标签中写入坐标和 id。taotao-manager 项目中依赖项目 taotao-common：

```xml
<dependency>
	<groupId>com.taotao</groupId>
	<artifactId>taotao-common</artifactId>
	<version>0.0.1-SNAPSHOT</version>
</dependency>
```

# 系统功能分析

## 首页数据库表结构分析

![image](https://ws1.sinaimg.cn/large/d4556b75ly1g3rg4bp7ywj20yp0jgwko.jpg)

可以根据首页大广告位的数据结构设计一张表，进行增删改查管理，其他部分的展示内容同样可以设计表，进行增删改查。如果每一个前端展示内容（大广告位、小广告位等等），单独建立表，进行 CRUD 操作，会有以下问题

1. 页面大量信息堆积，发布显得异常沉重
2. 表信息内容繁杂，管理效率低下
3. 许多工作需要技术人员配合完成
4. 改版工作量大，系统扩展性差

解决方案：
对首页展示功能进行抽取，把首页的每个展示功能（如大广告位，淘淘快报），看作是一个大的分类，放在 `tb_content_category` 表中，每个大的分类里面展示的多条信息看作是分类下的内容，放在内容表 `tb_content` 中.

例如：首页大广告，对应的是大广告分类，而大广告位展示的多张图片，就是大广告分类下的内容。
前台需要获取大广告的图片，只需要根据大广告的 id 查询对应的内容即可

这样就需要两张表：一张内容分类表 `tb_content_category` ；一张内容表 `tb_content`

## 首页轮播图功能分析

1. 首页轮播图的展示只需要后台提供轮播图图片数据，将图片数据转化为一个 json 数据之后提供给前端，便可以进行展示。

2. 数据的展示是在 taotao-portal-web 工程下的 index.jsp 文件中，index.jsp 代码中的 `ad1` 变量便是后端提供用来展示的：

```
    if ( !cfg.DATA_MSlide ) {
        cfg.DATA_MSlide=[];
    }

	var data = ${ad1};
```

### Cotroller 层

在 taotao-portal-web 工程下写一个 controller，实现页面跳转，跳转到 index.jsp 页面：

该 controller 实现一个映射请求方法 `showIndex(Model model)`，该方法实现根据内容分类的 `id` 查询内容表数据，查询出来的数据存储在一个 List 列表中，最后转化成 json 数据后传递给前端显示页面。

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
	//接收URL的请求 http://localhost:8082/index.html
	@RequestMapping("/index")
	public String showIndex(Model model){
		//引入服务
		//注入服务
		//添加业务逻辑，根据内容分类的id查询内容列表
		List<TbContent> contentlist = contentservice.getContentListByCatId(categoryId);
		//转成自定义的 POJO：AD1NOde的列表
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

**使用到的注解**

- `@RequestMapping`

- `@Value`

- `@Controller`

- `@Autowired`

**web.xml 配置**

在 web.xml 文件中只需要配置一个映射请求上下文 `DispatcherServlet`。并为这个 `DispatcherServlet` 定义对应的 URL 映射和 `contextConfigLocation`，配置文件如下：

```xml
<!-- springmvc的前端控制器 -->
	<servlet>
		<servlet-name>taotao-manager-web</servlet-name>
		<servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
		<!-- contextConfigLocation不是必须的， 如果不配置contextConfigLocation， springmvc的配置文件默认在：默认为WEB-INF目录下，名称为 [<servlet-name>]-servlet.xml -->
		<init-param>
			<param-name>contextConfigLocation</param-name>
			<param-value>classpath:spring/springmvc.xml</param-value>
		</init-param>
		<load-on-startup>1</load-on-startup>
	</servlet>
	<servlet-mapping>
		<servlet-name>taotao-manager-web</servlet-name>
		<!--  /* 表示拦截所有，包括转发的 jsp 页面，这是错误的，不能用-->
		<!--  / 表示拦截所有的静态资源，不包括转发 jsp -->
		<url-pattern>/</url-pattern>
	</servlet-mapping>
```

以往 tomcat 下的 web.xml 文件下需要配置二个上下文：

1.  Web 容器上下文，即 Spring Ioc 容器上下文，该上下文需要配置 `ContextLoaderLister`，如下：

    ```xml
    <web-app >
    	<listener>
    		<listener-class>org.springframework.web.context.ContextLoaderListener</listener-class>
    	</listener>
    </web-app>
    ```

    `ContextLoaderLister` 被定义为一个监听器，这个监听器是与 Web 服务器的生命周期相关联的，由 `ContextLoaderLister` 监听器负责完成 Ioc 容器在 Web 环境中的启动工作

2.  映射请求上下文 `DispatcherServlet`

在 taotao-manager-web 工程下 web.xml 文件中不需要配置 Spring IOC 容器了，因为该工程为表现层工程，Spring IOC 容器的配置只需要在服务层配置就好了

**springmvc.xml 配置**

springmvc.xml 配置文件是为映射请求上下文 `DispatcherServlet` 使用的，提供其相关的 Spring MVC 配置，配置内容如下：

```xml

	<!-- 用于读取一些单独配置成属性文件的数据，如读取 jdbc 数据库文件 -->
	<context:property-placeholder location="classpath:resource/*.properties"/>

	<!-- 注解扫描指定包，需要通过参数 base-package 指定扫描指定包 -->
	<context:component-scan base-package="com.taotao.portal.controller" />
	<!-- 开启自动扫描注入配置，扩充了注解驱动，可以将请求参数绑定到控制器参数 -->
	<mvc:annotation-driven />
	<!-- 视图解析器 InternalResourceViewResolver，在处理 handler 的返回值之后，将由 InternalResourceViewResolver进行解析，获取视图 View。当处理器返回 index 时，InternalResourceViewResolver 解析器会自动添加前后缀：/WEB-INF/jsp/index.jsp
	-->
	<bean
		class="org.springframework.web.servlet.view.InternalResourceViewResolver">
		<property name="prefix" value="/WEB-INF/jsp/" />
		<property name="suffix" value=".jsp" />
	</bean>

	<!-- 引用 dubbo 服务，将自身端口号暴露给 dubbo 并注册在 zookeeper 中 -->
	<dubbo:application name="taotao-portal-web"/>
	<dubbo:registry protocol="zookeeper" address="192.168.25.128:2181"/>
	<dubbo:reference interface="com.taotao.content.service.ContentService" id="contentService" timeout="300000"/>
</beans>
```

关于二个不相关的工程如何进行交互，是通过 Dubbo 服务实现的。具体先不说了。

### 配置文件

ContentServiceImpl 使用 Spring 注解 `@Service` 注解，首先要在 taotao-content-service 的 web.xml 文件中配置 Spring Ioc 容器上下文，使用 `ContextLoaderListener`，并初始化配置文件：

```xml
<web-app>
   <!-- 初始化Spring Ioc容器 -->
  <context-param>
  	<param-name>contextConfigLocation</param-name>
  	<param-value>classpath:spring/applicationContext-*.xml</param-value>
  </context-param>
  <listener>
  	<listener-class>org.springframework.web.context.ContextLoaderListener</listener-class>
  </listener>
</web-app>
```

初始化参数 `contextConfigLocation` 下通过通配符的方法又配置了四个 xml 文件，分别做为数据库 dao 层、redis、service 层和事务的配置文件，下面逐一介绍：

**`contextConfigLocation` 配置文件内容：**

**1. applicationContext-service.xml**

```xml
<beans ...//省略>
	<!-- 开启组件扫描 -->
	<context:component-scan base-package="com.taotao.content.service"></context:component-scan>
	<!-- 使用dubbo发布服务 -->
	<!-- 提供方应用信息，用于计算依赖关系 -->
	<dubbo:application name="taotao-content" />
	<dubbo:registry protocol="zookeeper" address="192.168.25.128:2181" />
	<!-- 用dubbo协议在20881端口暴露服务 -->
	<dubbo:protocol name="dubbo" port="20881" />
	<!-- 声明需要暴露的服务接口 -->
	<dubbo:service interface="com.taotao.content.service.ContentCategoryService" ref="contentCategoryServiceImpl" timeout="300000"/>
	<dubbo:service interface="com.taotao.content.service.ContentService" ref="contentServiceImpl" timeout="300000"/>
</beans>
```

**2. applicationContext-dao.xml**

- 配置数据库连接池，使用 `DruidDataSource`，Druid 是阿里巴巴开源平台上一个数据库连接池实现，结合了 C3P0、DBCP、PROXOOL 等 DB 池的优点，同时加入了日志监控，天生就是针对监控而生的 DB 连接池。
- 配置 `SqlSessionFactoryBean`，让 Spring 容器管理该 Bean，`SqlSessionFactoryBean` 实现了 Spring 的 FactoryBean 接口，且有一个单独的必须属性 `dataSource`，一个通用的属性是 `configLocation`，它是用来指定 MyBatis 的 XML 配置文件路径的。MyBatis 配置文件 SqlMapConfig.xml 内容如下：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE configuration>
<configuration>
	<mappers>
		<mapper></mapper>
	</mappers>
</configuration>

```

- 配置 Mapper 自动扫描 `MapperScannerConfigurer`，从 Mapper 包中扫描出 Mapper 接口，自动创建代理对象并在 Spring Ioc 容器中注册。遵循规范：将 Mapper 的 .java 文件和 .xml 映射文件名保持一致，且在一个目录中。自动扫描出来的 Mapper 的 Bean 的 id 为 Mapper 的类名且首字母小写。

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans ...//省略>
	<!-- 数据源 -->
	<!-- 配置数据库连接池，使用 DruidDataSource -->
	<context:property-placeholder location="classpath:properties/*.properties"/>
	<bean id="dataSource" class="com.alibaba.druid.pool.DruidDataSource"
		destroy-method="close">
		<property name="url" value="${jdbc.url}" />
		<property name="username" value="${jdbc.username}" />
		<property name="password" value="${jdbc.password}" />
		<property name="driverClassName" value="${jdbc.driver}" />
		<property name="maxActive" value="10" />
		<property name="minIdle" value="5" />
	</bean>
	<!-- sqlSessionFactory -->
	<bean id="sqlSessionFactory" class="org.mybatis.spring.SqlSessionFactoryBean">
		<!-- 数据库连接池 -->
		<property name="dataSource" ref="dataSource" />
		<!-- 加载 MyBatis 的全局配置文件 -->
		<property name="configLocation" value="classpath:mybatis/SqlMapConfig.xml" />
	</bean>
	<!-- Mapper 自动扫描器 -->
	<bean class="org.mybatis.spring.mapper.MapperScannerConfigurer ">
		<property name="basePackage" value="com.taotao.mapper" />
		<!-- 指定 Repository 标准才扫描为 Mapper-->
		<property name="annotationClass" value="org.springframework.stereotype.Repository">
	</bean>
</beans>
```

**3. applicationContext-redis.xml**

主要配置 Redis 的实现类，单机版用于测试，配置 `JedisPool`，集群版用于实际项目 `JedisCluster`，并使用构造器方法注入属性。`JedisCluster` 是针对 RedisCluster 的 java 客户端，它封装了 java 访问 Redis 集群的各种操作，包括初始化连接、请求重定向等

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans ...//省略>
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

**4. applicationContext-transaction.xml**

主要配置 Spring 事务管理器，使用声明式事务，需要配置注解驱动

```xml

<!-- 事务管理器配置数据源 -->
<?xml version="1.0" encoding="UTF-8"?>
<beans ...//省略 >
	<bean id="transactionManager" class="org.springframework.jdbc.datasource.DataSourceTransactionManager">
		<property name="dataSource" ref="dataSource"/>
	</bean>
	<!-- 配置注解驱动 -->
	<tx:annotation-driven transaction-manager="transactionManager" />
</beans >
```

### Service 层

Service 层主要根据内容分类 id 查询内容列表数据，返回给 Controller 层。

Service 层的实现放在了服务层，因此需要新建一个工程 taotao-content ，taotao-content 工程下新建三个子模块 taotao-content-interface（jar） 、 taotao-content-service（war） 和 taotao-content-dao。 在 taotao-content-interface 模块下定义一个接口 ContentService ，里面新添加一个方法 `getContentListByCatId(categoryId)`，该方法的作用是**根据内容分类的 `id` 查询其下的内容列表内容**，taotao-content-service 子模块 ContentServiceImpl 类实现了 ContentService 接口的方法

```java
public interface ContentService {
	// 根据内容分类的 id 查询其下的内容列表
	public List<TbContent> getContentListByCatId(Long categoryId);
}
```

**代码实现：**

`getContentListByCatId(categoryId)` 方法通过内容分类 `id` 返回内容列表，流程如下：

1. 判断 redis 中是否有数据，如果有直接从 redis 中取出数据返回
2. 如果 redis 没有数据，从数据库中查询记录返回
3. 将数据写入到 redis 数据库中

代码如下：

```java


public class ContentServiceImpl implements ContentService {
	@Autowired
	private JedisClient client;

	@Autowired
	private TbContentMapper mapper;

	@Value("${CONTENT_KEY}")
	private String CONTENT_KEY;

	@Override
	@Transactional(propagation = Propagation.SUPPORTS, isolation = Isolation.READ_COMMITTED, readOnly = true)
	public List<TbContent> getContentListByCatId(Long categoryId) {
		// 判断是否 Redis 中有数据，如果有直接从redis中获取数据并返回
		try {
			String jsonstr = client.hget(CONTENT_KEY, categoryId + "");
			if (StringUtils.isNotBlank(jsonstr)) {
				System.out.println("这里有缓存");
				return JsonUtils.jsonToList(jsonstr, TbContent.class);
			}
		} catch (Exception e1) {
			e1.printStackTrace();
		}

		// 使用 Mapper 执行查询
		List<TbContent> list = mapper.selectByCategoryId(categoryId);

		// 将数据写入到redis数据库中
		try {
			System.out.println("没有缓存");
			client.hset(CONTENT_KEY, categoryId + "", JsonUtils.objectToJson(list));
		} catch (Exception e) {
			e.printStackTrace();
		}
		return list;
	}
}

```

方法中使用 Redis 存储 Hash 结构 `hset key sub-key value` 的数据类型。 定义一个 key 命名为 `CONTENT_KEY` 来表示大的内容分类，sub-key 用于存储检索不同内容分类 `id` 下的数据。通过 `hget()` 方法判断对应的内容分类 `id`-`categoryId` 是否存在，这里 Redis 存储的是 Json 格式的字符串数据，如果存在则 把 Json 数据转化为一个 `List<TbContent>` 类型的列表返回给 Controller。

方法中事务隔离级别使用 `READ_COMMITTED`，在大部分场景下有助于提高并发，又解决了脏读问题。但是会出现不可重复读的问题，可以考虑使用数据库中的悲观锁或者乐观锁解决数据不一致问题。

方法中传播行为使用 `SUPPORTS`，方法在单独被调用时，这个方法将以非事务的方式执行，事务配置为 `Propagration.SUPPORTS`，这样可以提高方法执行速度。从 MySQL 5.6 版本开始，InnoDB 增加了对只读事务的优化：InnoDB 引擎可以避免为只读事务创建事务 ID，进而避免多余的事务和锁操作。

[Propagation.SUPPORTS 有什么效果](https://www.jianshu.com/p/ec899855f049)

### Dao 层

Dao 层主要实现的业务是当从缓存中没有找到相应内容分类 `id` 对应的数据时，从数据库中查找。

代码实现首先要注入对应的 Mapper，之后执行查询语句

```java

//注入 Mapper
@Autowired
private TbContentMapper mapper;
// 执行查询
List<TbContent> list = mapper.selectByCategoryId(categoryId);
```

调用映射器相应方法的 SQL 语句，使用 Mybatis 动态 SQL 语句：

```java
@Repository
public interface TbContentMapper {
	List<TbContent> selectByCategoryId(@Param("categoryId") Long categoryId);
}
```

```xml
<mapper namespace="com.taotao.mapper.TbContentMapper" >
	<!-- resultMap 中的 column 为数据库表中的列字段，property 为对应 pojo 对象的属性 -->
	<resultMap id="BaseResultMap" type="com.taotao.pojo.TbContent" >
		<id column="id" property="id" jdbcType="BIGINT" />
		<result column="category_id" property="categoryId" jdbcType="BIGINT" />
		<result column="title" property="title" jdbcType="VARCHAR" />
		<result column="sub_title" property="subTitle" jdbcType="VARCHAR" />
		<result column="title_desc" property="titleDesc" jdbcType="VARCHAR" />
		<result column="url" property="url" jdbcType="VARCHAR" />
		<result column="pic" property="pic" jdbcType="VARCHAR" />
		<result column="pic2" property="pic2" jdbcType="VARCHAR" />
		<result column="created" property="created" jdbcType="TIMESTAMP" />
		<result column="updated" property="updated" jdbcType="TIMESTAMP" />
	</resultMap>
	<select parameterType="long" resultMap="BaseResultMap">
		select id, category_id, title, sub_title, title_desc, url, pic, pic2, created, updated
		from tb_content where
		<trim prefix="where" prefixOverrides="and">
			<if test="categoryId != null and categoryId != ''">
				category_id = #{categoryId}
			</if>
		</trim>
	<select>
</mapper>
```

上面的 SQL 语句对应为：

```sql
select id, category_id, title, sub_title, title_desc, url, pic, pic2, created, updated
from tb_content
where category_id = 89;
```

但是实际通过 `explain` 关键字进行分析的时候，虽然对 `category_id` 创建了索引，但是通过 `explain` 分析并没有用到索引查询，可能时因为查询优化器做了选择。改写 SQL 语句，使用 `inner join` 来拼接：

```sql
SELECT
	c.id, c.category_id, c.title, c.sub_title, c.title_desc, c.url, c.pic, c.pic2, c.created, c.updated
FROM tb_content_category category
INNER JOIN tb_content c ON category.id = c.category_id
WHERE c.category_id = 89;
```

使用 `show profiles` 查看 SQL 执行时间，执行时间相差无几。考虑到还是单表查询效率高一些。
![image](https://ws1.sinaimg.cn/large/d4556b75ly1g59tvmdunpj20ql0e00ts.jpg)

使用到的注解：

- `@Param`：如果你的映射器的方法需要多个参数, 这个注解可以被应用于映射器的方法参数来给每个参数一个名字。否则，多参数将会以它们的顺序位置来被命名。比如：#{param1} ，#{param2} 等，这是默认的。使用 @Param("person")，参数应该被命名为 #{person}

## Redis 缓存同步

在 tb_content 内容表中插入数据时，Redis 缓存中的数据与数据库的数据不一致，此时可清空此内容分类下的 Redis 缓存。代码实现如下：

```java
@Override
@Transactional(propagation = Propagation.REQUIRED, isolation = Isolation.READ_COMMITTED)
public TaotaoResult saveContent(TbContent content) {

	content.setCreated(new Date());
	content.setUpdated(content.getCreated());

	mapper.insertSelective(content);

	// 清空此内容所属的分类下的所有的缓存
	try {
		client.hdel(CONTENT_KEY, content.getCategoryId() + "");
		System.out.println("当插入时，清空缓存");
	} catch (Exception e) {
		e.printStackTrace();
	}

	return TaotaoResult.ok();
}
```

事务的传播行为使用 `REQUIRED`，考虑原因：事务写在了 Service 层，当我们调用 Service 层的一个方法的时候它能够保证我们的这个方法中执行的所有的对数据库的更新操作保持在一个事务中，在事务层里面调用的这些方法要么全部成功，要么全部失败。

Mapper 插入一条数据使用了 Mybatis 动态 SQL 语句进行拼接

```sql
<insert id="insertSelective" parameterType="com.taotao.pojo.TbContent" >
    insert into tb_content
    <trim prefix="(" suffix=")" suffixOverrides="," >
      <if test="id != null" >
        id,
      </if>
      <if test="categoryId != null" >
        category_id,
      </if>
      <if test="title != null" >
        title,
      </if>
	  ...//省略其它字段
	</trim>
	<trim prefix="values (" suffix=")" suffixOverrides="," >
      <if test="id != null" >
        #{id,jdbcType=BIGINT},
      </if>
      <if test="categoryId != null" >
        #{categoryId,jdbcType=BIGINT},
      </if>
      <if test="title != null" >
        #{title,jdbcType=VARCHAR},
      </if>
	  ...//省略其它字段
	</trim>
</insert>
```

实际的 SQL 语句：

```sql
insert into tb_content(id, categoryId, title) values(...)
```

## Redis 项目相关

### Redis 集群搭建

**Redis 集群概念：**

单机处理到达瓶颈的时候，把单机复制几份，这样就构成了一个“集群”。集群中每台服务器就叫做这个集群的一个“节点”，所有节点构成了一个集群。每个节点都提供相同的服务。

**方案：**

版本使用 Redis3.0，从 3.0 开始开始支持了 Redis 的分布式的实现 Redis Cluster。

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
3. 删除 redis01 目录下的快照文件 dump.rdb，并且修改该目录下的 redis.conf 文件，具体修改两处地方：一是端口号修改为 7001，二是开启集群创建模式，打开注释 `cluster-enabled yes` 即可
   > `rm -rf dump.rdb`
4. 将 redis-cluster/redis01 文件复制 5 份到 redis-cluster 目录下（redis02-redis06），创建 6 个 redis 实例，模拟 Redis 集群的 6 个节点。然后将其余 5 个文件下的 redis.conf 里面的端口号分别修改为 7002-7006
5. 创建一个 redis 节点的脚本启动文件，放别启动所有的 redis 节点，文件内容如下：
   ![image](https://ws1.sinaimg.cn/large/d4556b75ly1g4sgyhx62pj20i80c6jrl.jpg)
6. 修改脚本权限使之能够执行
   > `chmod +x start-all.sh`
7. 执行 start-all.sh 脚本，启动 6 个 redis 节点
   > `./start-all.sh`
8. 查看所有的 redis 节点是否均已启动成功
   > `ps aux|grep redis`

**集群搭建：**

1. 安装 ruby 工具所需要的运行环境
   > `apt-get install ruby`
2. 把 ruby 相关的包安装到服务器，可以先本地下载好 redis-3.0.0.gem 在安装
   > `gem install redis-3.0.0.gem`
3. 把 ruby 脚本工具复制到 usr/local/redis-cluster 目录下。这个 ruby 脚本工具在 redis 解压文件的源代码里，即 redis/`src` 目录下的 redis-trib.rb 文件
   > `cp redis-trib.rb /usr/local/redis-cluster`
4. 然后使用该脚本文件搭建集群，根据自己的服务器 ip 输入对应的 ip 地址和之前设置好的端口号

   > `./redis-trib.rb`  
   > `create --replicas 1`  
   > `192.168.107.130:7001`  
   > `192.168.107.130:7002`  
   > `192.168.107.130:7003`  
   > `192.168.107.130:7004`  
   > `192.168.107.130:7005`  
   > `192.168.107.130:7006`

   ![image](https://img-blog.csdn.net/20181001161757158?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQyODE1NzU0/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

至此，Redi 集群搭建成功，上图显示了每个节点所分配的 slots（哈希槽），这里总共 6 个节点，其中 3 个是从节点，所以 3 个主节点分别映射了 0-5460、5461-10922、10933-16383 solts。

最后连接集群节点，一定要加上 `-c`，表示连接集群，连接任意一个即可：

> `redis01/redis-cli -p 7001 -c`

### Jedis 的使用

Redis 集群在代码中的使用需要在 taotao-content 工程下的模块 taotao-content-service 的 pom.xml 文件中添加 Jedis 依赖：

```java
<dependency>
			<groupId>redis.clients</groupId>
			<artifactId>jedis</artifactId>
			<version>${jedis.version}</version>
</dependency>
```

首页轮播图中 Redis 的实现代码也是写在 taotao-content-service 下的。因为集群是比较消耗成本的，所以我们在项目整合中开发一个接口 `JedisClient`，有单机版的实现类 `JedisClientPool` 和集群版的实现类 `JedisClientCluster`，其中单机版和集群版的实现类分别通过注解 `@Autowired` 自动注入 Redis 的实现类 `JedisPool` 和 `JedisCluster`。使用时可以面向接口开发，不影响业务逻辑，使用 Spring 管理实现类，部署时切换实现类即可。`JedisClient` 接口定义如下：

```java
public interface JedisClient {
	// String 结构
	String set(String key, String value);
	String get(String key);
	Boolean exists(String key);
	Long expire(String key, int seconds);
	Long ttl(String key);
	Long incr(String key);
	// Hash 结构
	Long hset(String key, String field, String value);
	String hget(String key, String field);
	Long hdel(String key,String... field);

}
```

实现类 `JedisClientCluster` 通过 Spring 自动注入 `JedisCluster` 来重写接口方法；实现类 JedisClientPool 通过 Spring 自动注入 JedisPool 来重写接口方法。代码片段如下：

```java
public class JedisClientCluster implements JedisClient {

	@Autowired
	private JedisCluster jedisCluster;

	@Override
	public Long hset(String key, String field, String value) {
		return jedisCluster.hset(key, field, value);
	}

	@Override
	public String hget(String key, String field) {
		return jedisCluster.hget(key, field);
	}
    ...//省略其它方法
}
```

单机版的代码实现雷同集群版。

### 性能优化

不使用 Redis 的时候，无限循环测试，在 4000 并发量的情况下，最终吞吐量在 100 左右，好的情况下达到 200，都比较低。

使用 Redis 集群的时候，无限循环测试，在 4000 并发量的情况下，刚刚开始的时候并发效果很好，最高吞吐量可以达到 700 sec 左右，将近提升 5 倍多，但是时间长了之后会出现连接失败异常。

起初我们考虑是不是 JedisCluster 使用完毕之后没有及时释放，导致不够用了。后来发现我们使用的是 redis3.0 的集群， jedisCluster 内部使用了池化技术，每次使用完毕都会自动释放 Jedis 因此不需要关闭。如果调用 close 方法后再调用 jedisCluster 的 api 进行操作时就会出现集群连接关闭的情况。

之后我们又进行排查，考虑到是不是 JedisCluster 中的 poolConfig 不合理，于是对其进行了简单参数配置。

```xml
<bean id="jedisPoolConfig" class="redis.clients.jedis.JedisPoolConfig">
	<!--资源池最大连接数-->
	<property name="maxTotal" value="10"/>
	<!--资源池允许最大空闲数，建议 = maxTotle-->
	<property name="maxIdle" value="10"/>
	<!--资源池确保最少空闲连接数，预热 minIdle-->
	<property name="minIdle" value="8"/>
	<property name="maxWaitMillis" value="1000"/>
</bean>

<constructor-arg name="poolConfig" ref="jedisPoolConfig" />
```

但是实际中还是没有解决掉，最后我们观察服务器内容使用情况，突然发现内存使用非常高，于是认为是个人电脑的配置问题导致之后的。

# 数据库表结构设计

## ER 图和数据字典

**ER 图：**

用户表、订单表、订单物流表和订单商品表 ER 图：

![image](https://ws1.sinaimg.cn/large/d4556b75ly1g5e7590uyhj20pd0h70tj.jpg)

内容表和内容分类表 ER 图：

![image](https://ws1.sinaimg.cn/large/d4556b75ly1g5e76hftkjj20oh0duq3r.jpg)

商品表、商品描述表和商品分类表 ER 图：

![image](https://ws1.sinaimg.cn/large/d4556b75ly1g5e77h1j4gj20ol0g0aay.jpg)

**数据字典**

用户表 `tb_user`：

```sql
DROP TABLE IF EXISTS `tb_user`;
CREATE TABLE `tb_user` (
  `id` bigint(20) NOT NULL AUTO_INCREMENT,
  `username` varchar(50) NOT NULL COMMENT '用户名',
  `password` varchar(32) NOT NULL COMMENT '密码，加密存储',
  `phone` varchar(20) DEFAULT NULL COMMENT '注册手机号',
  `email` varchar(50) DEFAULT NULL COMMENT '注册邮箱',
  `created` datetime NOT NULL,
  `updated` datetime NOT NULL,
  PRIMARY KEY (`id`),
  UNIQUE KEY `username` (`username`) USING BTREE,
  UNIQUE KEY `phone` (`phone`) USING BTREE,
  UNIQUE KEY `email` (`email`) USING BTREE
) ENGINE=InnoDB AUTO_INCREMENT=37 DEFAULT CHARSET=utf8 COMMENT='用户表';
```

内容表 `tb_content`：

```sql
DROP TABLE IF EXISTS `tb_content`;
CREATE TABLE `tb_content` (
  `id` int(20) NOT NULL AUTO_INCREMENT,
  `category_id` int(20) NOT NULL COMMENT '内容类目ID',
  `title` varchar(200) DEFAULT NULL COMMENT '内容标题',
  `sub_title` varchar(100) DEFAULT NULL COMMENT '子标题',
  `title_desc` varchar(500) DEFAULT NULL COMMENT '标题描述',
  `url` varchar(500) DEFAULT NULL COMMENT '链接',
  `pic` varchar(300) DEFAULT NULL COMMENT '图片绝对路径',
  `pic2` varchar(300) DEFAULT NULL COMMENT '图片2',
  `content` text COMMENT '内容',
  `created` datetime DEFAULT NULL,
  `updated` datetime DEFAULT NULL,
  PRIMARY KEY (`id`),
  KEY `category_id` (`category_id`),
  KEY `updated` (`updated`)
) ENGINE=InnoDB AUTO_INCREMENT=32 DEFAULT CHARSET=utf8;
```

内容分类表 `tb_content_category`：

```sql
DROP TABLE IF EXISTS `tb_content_category`;
CREATE TABLE `tb_content_category` (
  `id` int(20) NOT NULL AUTO_INCREMENT COMMENT '类目ID',
  `parent_id` int(20) DEFAULT NULL COMMENT '父类目ID=0时，代表的是一级的类目',
  `name` varchar(50) DEFAULT NULL COMMENT '分类名称',
  `status` tinyint(1) DEFAULT '1' COMMENT '状态。可选值:1(正常),2(删除)',
  `sort_order` tinyint(4) DEFAULT NULL COMMENT '排列序号，表示同级类目的展现次序，如数值相等则按名称次序排列。取值范围:大于零的整数',
  `is_parent` tinyint(1) DEFAULT '1' COMMENT '该类目是否为父类目，1为true，0为false',
  `created` datetime DEFAULT NULL COMMENT '创建时间',
  `updated` datetime DEFAULT NULL COMMENT '创建时间',
  PRIMARY KEY (`id`),
  KEY `parent_id` (`parent_id`,`status`) USING BTREE,
  KEY `sort_order` (`sort_order`)
) ENGINE=InnoDB AUTO_INCREMENT=98 DEFAULT CHARSET=utf8 COMMENT='内容分类';
```

**商品表 `tb_item`**

```sql
CREATE TABLE `tb_item` (
  `id` bigint(20) NOT NULL COMMENT '商品id，同时也是商品编号',
  `title` varchar(100) NOT NULL COMMENT '商品标题',
  `sell_point` varchar(500) DEFAULT NULL COMMENT '商品卖点',
  `price` bigint(20) NOT NULL COMMENT '商品价格，单位为：分',
  `num` int(10) NOT NULL COMMENT '库存数量',
  `barcode` varchar(30) DEFAULT NULL COMMENT '商品条形码',
  `image` varchar(500) DEFAULT NULL COMMENT '商品图片',
  `cid` bigint(10) NOT NULL COMMENT '所属类目，叶子类目',
  `status` tinyint(4) NOT NULL DEFAULT '1' COMMENT '商品状态，1-正常，2-下架，3-删除',
  `created` datetime NOT NULL COMMENT '创建时间',
  `updated` datetime NOT NULL COMMENT '更新时间',
  PRIMARY KEY (`id`),
  KEY `price` (`price`),
  KEY `cid` (`cid`),
  KEY `status` (`status`),
  KEY `created` (`created`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COMMENT='商品表';
```

商品类目表 `tb_item_cat`：

```sql
CREATE TABLE `tb_item_cat` (
  `id` int(20) NOT NULL AUTO_INCREMENT COMMENT '类目ID',
  `parent_id` int(20) DEFAULT NULL COMMENT '父类目 ID=0 时，代表的是一级的类目',
  `name` varchar(50) DEFAULT NULL COMMENT '类目名称',
  `status` int(1) DEFAULT '1' COMMENT '状态。可选值:1(正常),2(删除)',
  `sort_order` int(4) DEFAULT NULL COMMENT '排列序号，表示同级类目的展现次序，如数值相等则按名称次序排列。取值范围:大于零的整数',
  `is_parent` tinyint(1) DEFAULT '1' COMMENT '该类目是否为父类目，1为true，0为false',
  `created` datetime DEFAULT NULL COMMENT '创建时间',
  `updated` datetime DEFAULT NULL COMMENT '创建时间',
  PRIMARY KEY (`id`),
  KEY `parent_id` (`parent_id`,`status`) USING BTREE,
  KEY `sort_order` (`sort_order`)
) ENGINE=InnoDB AUTO_INCREMENT=1183 DEFAULT CHARSET=utf8 COMMENT='商品类目';
```

商品描述表 `tb_item_desc`：

```sql
CREATE TABLE `tb_item_desc` (
  `item_id` bigint(20) NOT NULL COMMENT '商品ID',
  `item_desc` text COMMENT '商品描述',
  `created` datetime DEFAULT NULL COMMENT '创建时间',
  `updated` datetime DEFAULT NULL COMMENT '更新时间',
  PRIMARY KEY (`item_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COMMENT='商品描述表';
```

订单表 `tb_order`：

```sql
CREATE TABLE `tb_order` (
`order_id` varchar(50) COLLATE utf8_bin NOT NULL DEFAULT '' COMMENT '订单id',
`payment` varchar(50) COLLATE utf8_bin DEFAULT NULL COMMENT '实付金额。精确到2位小数;单位:元。如:200.07，表示:200元7分',
`payment_type` int(2) DEFAULT NULL COMMENT '支付类型，1-在线支付，2-货到付款',
`post_fee` varchar(50) COLLATE utf8_bin DEFAULT NULL COMMENT '邮费。精确到2位小数;单位:元。如:200.07，表示:200元7分',
`status` int(10) DEFAULT NULL COMMENT '状态：1-未付款，2-已付款，3-未发货，4-已发货，5-交易成功，6-交易关闭',
`create_time` datetime DEFAULT NULL COMMENT '订单创建时间',
`update_time` datetime DEFAULT NULL COMMENT '订单更新时间',
`payment_time` datetime DEFAULT NULL COMMENT '付款时间',
`consign_time` datetime DEFAULT NULL COMMENT '发货时间',
`end_time` datetime DEFAULT NULL COMMENT '交易完成时间',
`close_time` datetime DEFAULT NULL COMMENT '交易关闭时间',
`shipping_name` varchar(20) COLLATE utf8_bin DEFAULT NULL COMMENT '物流名称',
`shipping_code` varchar(20) COLLATE utf8_bin DEFAULT NULL COMMENT '物流单号',
`user_id` bigint(20) DEFAULT NULL COMMENT '用户id',
`buyer_message` varchar(100) COLLATE utf8_bin DEFAULT NULL COMMENT '买家留言',
`buyer_nick` varchar(50) COLLATE utf8_bin DEFAULT NULL COMMENT '买家昵称',
`buyer_rate` int(2) DEFAULT NULL COMMENT '买家是否已经评价',
PRIMARY KEY (`order_id`),
KEY `create_time` (`create_time`),
KEY `buyer_nick` (`buyer_nick`),
KEY `status` (`status`),
KEY `payment_type` (`payment_type`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;
```

订单商品表 `tb_order_item`：

```sql
CREATE TABLE `tb_order_item` (
  `id` varchar(20) COLLATE utf8_bin NOT NULL,
  `item_id` varchar(50) COLLATE utf8_bin NOT NULL COMMENT '商品id',
  `order_id` varchar(50) COLLATE utf8_bin NOT NULL COMMENT '订单id',
  `num` int(10) DEFAULT NULL COMMENT '商品购买数量',
  `title` varchar(200) COLLATE utf8_bin DEFAULT NULL COMMENT '商品标题',
  `price` bigint(50) DEFAULT NULL COMMENT '商品单价',
  `total_fee` bigint(50) DEFAULT NULL COMMENT '商品总金额',
  `pic_path` varchar(200) COLLATE utf8_bin DEFAULT NULL COMMENT '商品图片地址',
  PRIMARY KEY (`id`),
  KEY `item_id` (`item_id`),
  KEY `order_id` (`order_id`),
  KEY `order_item_id` (`order_id`,`item_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;
```

订单物流表 `tb_shipping`：

```sql
CREATE TABLE `tb_order_shipping` (
`order_id` varchar(50) NOT NULL COMMENT '订单ID',
`receiver_name` varchar(20) DEFAULT NULL COMMENT '收货人全名',
`receiver_phone` varchar(20) DEFAULT NULL COMMENT '固定电话',
`receiver_mobile` varchar(30) DEFAULT NULL COMMENT '移动电话',
`receiver_state` varchar(10) DEFAULT NULL COMMENT '省份',
`receiver_city` varchar(10) DEFAULT NULL COMMENT '城市',
`receiver_district` varchar(20) DEFAULT NULL COMMENT '区/县',
`receiver_address` varchar(200) DEFAULT NULL COMMENT '收货地址，如：xx路xx号',
`receiver_zip` varchar(6) DEFAULT NULL COMMENT '邮政编码,如：310001',
`created` datetime DEFAULT NULL,
`updated` datetime DEFAULT NULL,
PRIMARY KEY (`order_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```

## 数据中设计的范式与反范式

首先在设计表的过程中，首先我们会遵循第一范式。

每一列都是原子不可在分的。在例如商品表 `tb_item` 中，商品的信息有很多，包括商品的标题、商品卖点、库存、商品图片、商品条形码等等，我们把每一个信息都单独定义为商品表中的一个属性

在第一范式的基础上，满足第二范式，`tb_user` 表中非主属性关键字完全依赖于主键。在构建商品相关的数据表时，我们并没有使用联合索引，所有的属性完全依赖于主关键字，不存在部分依赖的情况。

在第二范式的基础上，我们又进一步对表结构进行划分，商品信息有很多：

| 商品 id | 商品标题 | 商品价格··· | 商品类目 id | 类目名称 | 类目信息··· |
| ------- | -------- | ----------- | ----------- | -------- | ----------- |


如果把商品的消息和商品类目下的消息都放在一张表中的话，是不满足第三范式的，因此我们将其拆分为二张表：

商品表 `tb_item` :

| 商品 id | 商品标题 | 商品价格··· | 商品类目 |
| ------- | -------- | ----------- | -------- |


商品类目表 `tb_item_cat`：

| 商品类目 id | 类目名称 | 类目信息··· |
| ----------- | -------- | ----------- |


商品表 `tb_item` 包含一个字段 `cid`，表示商品类目 id 号，并将 `cid` 定义为商品表的外键便好了。

订单表和订单商品表是一对多的关系，订单商品表在设计上，我们考虑到了反范式的设计思想，我们在订单商品表中添加了一些字段 `num`、`title`、`price` 等，这些数据本来可以通过 `tb_item` 表进行查询到，这样设计是为了减少了查询时的关联，提高查询效率。

订单物流表中将省份、城市和区/县分别定义为一个字段，保证其原子性不可再分。订单表和订单物流表一对一的关系，用户表和订单表是一对多的关系。

## 字段类型与合理的选择字段类型

[字段类型](https://segmentfault.com/a/1190000004177184)

不同的数据类型对数据库的性能影响很大：

1. 数据类型会影响存储空间的开销
2. 数据类型会影响数据查询性能

我们在表的设计上，考虑到各个字段的数据类型，如整型字段的选取，会考虑 int、mediumint、bigint：

**整型**

考虑到是我们自己写的小项目，内容分类和内容表的数据不会太多，因此二张表的主键 id 设置为 int 便好了。在内容分类表中，字状态 `status` 只有 1（正常）和 2（删除）二种、是否为父类目 `is_parent` 只有 1（true）和 2（false）二种，因此只需要使用 tinyint 存储便好了。

对于商品表而言，商品的数量较多，并且商品的 id 不能重复，因此考虑到商品的 id 可以在代码逻辑中生成：取当前时间的长整型值包含毫秒在加上二位随机数，如果不足二位前面补 0，这样就保证了商品的 id 唯一且随机了。我们将商品 id 定义为了 bigint 型字段。同样用户表的主键 id 同样定义为了 bigint 类型字段。商品表中的商品价格考虑到 float 和 double 类型会出现精度截断问题，所以考虑使用 decimal，但是我们又想价格参与的运算较多，整数运算是最基本的 CPU 指令，比浮点数、定点数更有效率。因此我们使用 bigint 代替 decimal 定义商品价格 `price` 字段。并且数据中 `price` 的单位为分，前端显示时把数据乘以 100 就好了。

订单表中的订单状态只有:未付款、已付款、未发货、已发货、交易成功和交易关闭 6 种，字符类型只有在线字符和货到付款二种，因此也用 tinyint 存储。

**字符串类型**

字符串数据类型是一个万能数据类型，可以储存数值、字符串、日期等。

字符串 char、varchar 类型我们考虑到固定数据类型和变长数据类型，数据长度相近的类型使用 char 存储，变长数据类型使用 varchar 来定义

~~用户表中的密码通过 md5 加密，手机号和邮箱都可以考虑使用 char 来定义，一则考虑到数据长度相近，二则考虑到用户会进行密码等个人信息的修改，使用 char 存储性能较高。~~

~~内容表中的标题、标题描述、链接以及图片的绝对路径等字段都使用 varchar 存储，考虑到是变长数据。~~

~~商品表中的商品标题，商品卖点，商品图片同样使用 varchar 存储~~

对很多数据的存储我们最终决定使用 varchar 进行存储，因此我们数据库存储引擎使用的是 InnoDB，而 InnoDB 数据表内部的行存储格式没有区分固定长度和可变长度列，使用 varchar 存储的有：

- 用户表中的密码通过 md5 加密，手机号和邮箱
- 内容表中的标题、标题描述、链接以及图片的绝对路径
- 商品表中的商品标题，商品卖点，商品图片
- 订单表中的订单 id、物流名称、物流单号、买家昵称以及买家昵称等字段
- 订单地址表中的收货人全名、电话、地址等信息

对于内容表的字段 `content` 和 商品描述表中的字段 `item_desc` 使用 varchar 来进行存储，考虑到不用 text 存储，因为描述信息不超过 64k，所以二者的性能相差无几，但是 varchar 存储更弹性，存储数据少的话性能更高，且创建索引的话查询速度快于 text，在都创建索引的情况下，text 的索引似乎不起作用。

**时间类型**

时间类型我们在表中主要定义了二个字段：

1. `created` 创建时间
2. `updated` 更新时间

在 timestamp 和 datetime 上，我们使用 datetime，考虑到到 timestamp 会自动更新时间，如果我们对字段 `updated` 进行修改，那么 `created` 存储为 timestamp 类型时也会自动更新。

## 表的垂直拆分和水平拆分

[表的垂直拆分和水平拆分](https://segmentfault.com/a/1190000006063258)

**垂直拆分**

商品表 `tb_item` 中，还包含对商品的描述等信息，我们把商品描述信息单独设置为一张商品描述表

商品描述信息被定义为一个 `text` 类型的字段，该字段一旦创建基本不会在用到其它地方了。

**水平拆分**

我们表的设计中最初没有考虑到水平拆分，因为考虑到一张表的数据量也不会超过 100w 设置 200w 更多，因此对数据库性能不会影响太大。如果设计的话，我们可以考虑通过取模的方式对表进行拆分，从而对数据进行查询和更新。

## 慢查询

当 MySQL 性能下降时，通过开启慢查询来获得哪条 SQL 语句造成的响应过慢，进行分析处理。当然开启慢查询会带来 CPU 损耗与日志记录的 IO 开销，所以我们要间断性的打开慢查询日志来查看 MySQL 运行状态。

## Explain 优化查询检测

## 索引

为了提高查询速度，我们同时在表的相关字段上创建了索引。

在商品表中，我们一般会在字段价格 `price` 上创建索引，因为用户经常会通过范围查找在某一个范围区间内的商品。我们测试查询商品表中价格在 1000 到 10000 的商品，发现不使用索引与使用所需执行时间从 0.0175 缩短到 0.0008。
![image](https://ws1.sinaimg.cn/large/d4556b75gy1g5d8u2qsscj20pt04v74u.jpg)
同时在商品表的字段 `status`、`cid`、`created` 上创建了索引。我们经常会出现通过选择一个商品类别来寻找所需商品，因此在 `cid` 上创建索引。用户浏览商品时经常想看最近更新上架的商品，尤其是电子产品，因此在字段 `created` 上创建索引。

在商品类目表中，我们有时选择浏览了一个类目状态下的商品，此时，需要返回上一级类目，SQL 语句会使用到连接查询，因此在连接查询的字段 `parent_id` 上创建了索引。同时我们把字段 `parent_id` 和 `status` 创建为了一个联合索引，并把 `parent_id` 放在前面，保证最左前缀原则。`status` 为一个可选状态，选择相应的状态后用户如果返回上一级商品类目时，该状态
不会发生变化，仍然是 SQL 语句中的执行条件。

![image](https://ws1.sinaimg.cn/large/d4556b75ly1g5d9y57qzjj20e8012743.jpg)

在订单表中，用户喜欢查看不同状态下的相应订单，查看订单的付款方式，因此在字段 `status` 和 `payment_type` 创建索引。

![image](https://ws1.sinaimg.cn/large/d4556b75ly1g5db1gg907j20q40bt3za.jpg)

在订单商品表中，增加了冗余设计，在 `item_id` 和 `order_id` 分别建立了索引。同时又把 `order_id` 和 `item_id` 建了联合索引，且 `order_id` 在前，因为我们常常会需要查询一个订单下的某一个具体商品。

在用户表中，我们在字段 `username`、`phone` 和 `email` 上分别创建了唯一索引。

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

## 使用场景和优缺点

[MQ(Message Queue)应用场景分析](https://my.oschina.net/bigdataer/blog/1923150)

[消息中间件及 ActiveMQ 介绍](https://segmentfault.com/a/1190000014958916)

**场景：**

**1. 异步处理**

发送者将消息发送给消息队列之后，不需要同步等待消息接收者处理完毕，而是立即返回进行其它操作。消息接收者从消息队列中订阅消息之后异步处理。

应用场景：
新用户注册之后发放 100 积分，180 元新手大礼包，激活会员卡

- 传统方式：

  ![image](https://segmentfault.com/img/bVbamXP?w=639&h=101)

- 使用消息队列：

  ![image](https://segmentfault.com/img/bVbamZn?w=674&h=249)

只有在业务流程允许异步处理的情况下才能这么做，例如上面的注册流程中，如果要求用户对验证邮件进行点击之后才能完成注册的话，就不能再使用消息队列。

**2. 应用解耦**

如果模块之间不直接进行调用，模块之间耦合度就会很低，那么修改一个模块或者新增一个模块对其它模块的影响会很小，从而实现可扩展性。

通过使用消息队列，一个模块只需要向消息队列中发送消息，其它模块可以选择性地从消息队列中订阅消息从而完成调用

应用场景：

- 订单系统：用户下单后，订单系统完成持久化处理，将消息写入消息队列，返回用户，下单成功
- 库存系统：订阅下单的消息，获取下单信息，库存系统根据下单信息，进行库存操作

**3. 流量削锋**

在高并发的场景下，如果短时间有大量的请求到达会压垮服务器。

可以将请求发送到消息队列中，服务器按照其处理能力从消息队列中订阅消息进行处理。

应用场景：秒杀活动，一般会因为流量过大，导致流量暴增，应用挂掉。为解决这个问题，一般需要在应用前端加入消息队列。可以控制活动的人数，可以缓解短时间内高流量压垮应用

**使用原因（优点）：**

项目上后台管理系统每一次修改商品之后，不同的系统会去处理不同的业务逻辑，例如搜索系统的话会拿到商品 id 去更新索引库，如果我们不使用消息队列的话，那么每一次拿到商品的 id 之后，搜索系统就需要立刻去调用相应业务逻辑来更新索引库。这样的话后台管理系统和索引库系统之间的耦合度比较高。如果使用了消息队列，索引库系统会通过异步的方式去拿商品的 id，且二个模块之间的耦合度降低了，系统的可扩展性也提高了。

**缺点：**

MQ 挂掉之后，整套系统就崩溃了。可以考虑使用 Zookeeper + ActiveMQ 集群实现高可用，暂时先不做。

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
2. 启动 bin 目录下的 activeMQ 命令
   > `./activemq start`
3. 关闭并查看状态
   > `./activemq stop`  
   > `./activemq status`
4. 查看端口 61616 是否开启
   > `netstat -an|grep 61616`
5. 网页登录 ActiveMQ 管控台
   > `http://192.168.0.115:8161/admin/`

## 代码实例

### 点对点生产者

主要流程：

1. 创建 ConnectionFactory 对象，需要指定服务端 ip 及端口号。默认端口为 "tcp://localhost:61616"；
2. 使用 ConnectionFactory 对象创建一个 Connection 对象；
3. 开启连接。调用 Connection 的 `start()` 方法；
4. 创建一个 Session 对象，提供发送消息等方法。调用 Connection 的 `createSession()` 方法；
5. 使用 Session 对象创建一个发送消息的 Destination 对象。指的是一个客户端用来指定生产消息目标和消费信息来源的对象。
   - Queue：点对点
   - Topic：发布/订阅
6. 使用 Session 对象创建一个生产者 Producer 对象。调用 Session 对象的 `createSession()` 方法。
7. 构建消息的内容
8. 发送消息
9. 关闭资源

代码如下：

```java
public class QueueProducer {
	//生产者发送消息
	@Test
	public void send() throws Exception{
		// 1.创建 ConnectionFactory 对象，需要指定服务端 ip 及端口号
		ConnectionFactory factory = new ActiveMQConnectionFactory("tcp://192.168.25.130:61616");
		//2.使用 ConnectionFactory 对象创建一个 Connection 对象
		Connection connection = factory.createConnection();
		//3.开启连接
		connection.start();
		//4.创建一个session对象，提供发送消息等方法
		//第一个参数：表示是否开启分布式事务（JTA），一般是 false 不开启。
		//第二个参数：就是设置消息的应答模式，如果第一个参数为 false 时，第二个参数设置才有意义。用的是自动应答
		Session session = connection.createSession(false, Session.AUTO_ACKNOWLEDGE);//
		//5.使用Session对象创建一个 Destination 对象（topic、queue），此处创建一个Queue对象。
		//参数：目的地的名称
		Queue queue = session.createQueue("queue-test");
		//6.使用 Session 对象创建一个 Producer 对象。
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

### 点对点消费者

主要流程：

1. 创建连接工厂
2. 创建连接
3. 开启连接
4. 创建 Session
5. 创建接收消息的一个目的地
6. 创建消费者
7. 接受消息
8. 关闭资源

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

### 发布/订阅生产者消费者

发布/订阅模式代码实现类似点对点模式，不同的是：

1. 发布/订阅模式创建目的地的时候使用类 `Topic`

2) Queue 默认是存在于 MQ 的服务器中的，发送消息之后，消费者随时取。但是一定是一个消费者取，消费完消息也就没有了。Topic 默认是不存在于 MQ 服务器中的，一旦发送之后，如果没有订阅，消息则丢失。

### ActiveMQ 安全机制

只有符合认证的用户才能进行发送和接收消息。

在 /usr/local/apache-activemq-5.15.8/conf/activemq.xml 的大约 123 行之前，之后加上上面的插件配置，重启 ActiveMQ
按之前的程序发送消息就会报 `java.lang.SecurityException:User name [null] or password is invalid` 的错误。

```xml
<plugins>
    <simpleAuthenticationPlugin>
        <users>
            <authenticationUser username="ysx" password="ysx" groups="users,admins"/>
        </users>
    </simpleAuthenticationPlugin>
</plugins>
```

需要对程序进行修改(生产者和消费者都要改)，创建连接工厂的时候指定在 activemq.xml 的 <plugin> 中配置的用户名和密码：

```java
ConnectionFactory factory = new ActiveMQConnectionFactory(
	"ysx",
	"ysx",
	"tcp://192.168.25.130:61616");
```

## ActiveMQ 整合 Spring

整合 Spring 主要是将消息端和发送端中的一些对象配置到 Spring 配置文件中，创建一个 Spring 配置文件 `applicationContext-activemq.xml`，主要需要配置的内容有：

- 通用的连接工厂 SingleConnectionFactory，属性填充 `targetConnectionFactory`，引用指定的目标工厂，这里应该是使用了简单工厂模式
- 目标连接工厂 ActiveMQConnectionFactory，属性填充 `brokerURL`，传入服务器的 ip 和 端口号
- 接收和发送消息时使用的模板对象类 JmsTemplate，属性填充通用的连接工厂
- 消息模型：ActiveMQTopic（发布/订阅）或者 ActiveMQQueue（一对一），构造器注入 `name` 属性，传入一个目的地名称
- 监听器 MyMessageListener，用于消费者接收消息
- 监听容器 DefaultMessageListenerContainer，用于启动线程做监听。属性填充连接工厂 `connectionFactory`、消息模型 `destination` 和监听器 `messageListener`

配置文件内容如下：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans ...//省略">

	<bean id="targetConnection" class="org.apache.activemq.ActiveMQConnectionFactory">
		<property name="brokerURL" value="tcp://192.168.25.130:61616"></property>
	</bean>
	<!-- 通用的 connectionfacotry 指定真正使用的连接工厂 -->
	<bean id="connectionFactory" class="org.springframework.jms.connection.SingleConnectionFactory">
		<property name="targetConnectionFactory" ref="targetConnection"></property>
	</bean>
	<!-- 接收和发送消息时使用的模板对象类-->
	<bean class="org.springframework.jms.core.JmsTemplate">
		<property name="connectionFactory" ref="connectionFactory"></property>
	</bean>
	<!-- <bean id="queueDestination" class="org.apache.activemq.command.ActiveMQQueue">
		<constructor-arg name="name" value="item-change-queue"></constructor-arg>
	</bean> -->
	<bean id="topicDestination" class="org.apache.activemq.command.ActiveMQTopic">
		<constructor-arg name="name" value="item-change-topic"></constructor-arg>
	</bean>

	<!-- 监听器 -->
	<bean id="myMessageListener" class="com.itheima.activemq.spring.MyMessageListener"></bean>
	<!-- 监听容器，作用：启动线程做监听 -->
	<bean class="org.springframework.jms.listener.DefaultMessageListenerContainer">
		<property name="connectionFactory" ref="connectionFactory"></property>
		<property name="destination" ref="topicDestination"></property>
		<property name="messageListener" ref="myMessageListener"></property>
	</bean>

	<bean id="myMessageListener2" class="com.itheima.activemq.spring.MyMessageListener"></bean>
	<!-- 监听容器，作用：启动线程做监听 -->
	<bean class="org.springframework.jms.listener.DefaultMessageListenerContainer">
		<property name="connectionFactory" ref="connectionFactory"></property>
		<property name="destination" ref="topicDestination"></property>
		<property name="messageListener" ref="myMessageListener2"></property>
	</bean>
</beans>

```

此时生产者需要实现简单的代码即可，主要流程：

1. 初始化 Spring 容器
2. 获取 JmsTemplate 对象
3. 获取 Desitination 对象
4. 发送消息，使用 `send()` 方法，方法中传入参数 Desitination 对象和提供创建消息的回调方法接口类 MessageCreator

```java
public class Producer {
	@Test
	public void send() throws Exception{
		//1.初始化spring容器
		ApplicationContext context = new ClassPathXmlApplicationContext("classpath:applicationContext-activemq.xml");
		//2.获取到 Jmstemplate 的对象
		JmsTemplate jmsTemplate = context.getBean(JmsTemplate.class);
		//3.获取destination
		Destination destination = (Destination) context.getBean(Destination.class);
		//4.发送消息
		jmsTemplate.send(destination, new MessageCreator() {

			@Override
			public Message createMessage(Session session) throws JMSException {
				return session.createTextMessage("通过spring发送的消息123");
			}
		});
		Thread.sleep(100000);
	}
}
```

消费者监听容器也只需要实现 MessageListener 类并重写 `onMessage()` 方法即可：

```java
public class MyMessageListener implements MessageListener {

	@Override
	public void onMessage(Message message) {
		//获取消息
		if(message instanceof TextMessage){
			TextMessage textMessage = (TextMessage)message;
			String text;
			try {
				text = textMessage.getText();
				System.out.println(text);
			} catch (JMSException e) {
				e.printStackTrace();
			}
		}
	}

}
```

## ActiveMQ 整合到项目

功能分析：

- 当后台管理系统添加一个商品之后，需要发送一个 TextMessage 对象，该 TextMessage 只需包含一个商品 id 即可。在 taotao-manager 的子工程 taotao-manager-service 工程中发送消息。
- 接收端搜索系统通过消息队列拿到商品 id 之后，通过数据库查询到商品的信息（搜索的结果商品的信息）再同步索引库。在 taotao-search 的子工程 taotao-search-service 工程中接收消息。

### 生产者 Producer

生产者 Producer 需要在 taotao-manager-service 工程下的 Spring 配置文件进行简单配置，新增一个 applicationContext-activemq.xml 配置文件。

**applicationContext-activemq.xml 配置内容：**

- 通用连接工厂 SingleConnectionFactory
- 目标连接工厂 ActiveMQConnectionFactory
- 接收和发送消息时使用的模板对象类 JmsTemplate
- 接收和发送消息的目的地 ActiveMQTopic（发布/订阅）

```xml
	<bean id="targetConnection" class="org.apache.activemq.ActiveMQConnectionFactory">
		<property name="brokerURL" value="tcp://192.168.25.130:61616"></property>
	</bean>
	<!-- 通用的connectionfacotry 指定真正使用的连接工厂 -->
	<bean id="connectionFactory" class="org.springframework.jms.connection.SingleConnectionFactory">
		<property name="targetConnectionFactory" ref="targetConnection"></property>
	</bean>
	<!-- 接收和发送消息时使用的类 -->
	<bean class="org.springframework.jms.core.JmsTemplate">
		<property name="connectionFactory" ref="connectionFactory"></property>
	</bean>
	<bean id="topicDestination" class="org.apache.activemq.command.ActiveMQTopic">
		<constructor-arg name="name" value="item-change-topic"></constructor-arg>
	</bean>
```

**发送消息**

消息的发送添加在 taotao-manager-service 工程中 ItemServiceImpl 类的 `saveItem()` 方法。

**ItemServiceImpl 类：**商品服务的实现类。商品服务的实现类，实现接口 ItemService，定义了方法：

```java
//商品相关的处理的service
public interface ItemService {
	//根据当前的页码和每页的行数进行分页查询
	public EasyUIDataGridResult getItemList(Integer page, Integer rows);
	//添加商品基本数据和描述数据
	public TaotaoResult saveItem(TbItem item, String desc);
	//根据商品的id查询商品的数据
	public TbItem getItemById(Long itemId);
	//据商品的id查询商品的描述
	public TbItemDesc getItemDescById(Long itemId);
}
```

ItemServiceImpl 类中需要注入的对象：

```java
@Service
public class ItemServiceImpl implements ItemService {
	@Autowired
	private TbItemMapper mapper;
	@Autowired
	private TbItemDescMapper descmapper;

	@Autowired
	private JmsTemplate jmstemplate;

	@Resource(name="topicDestination")
	private Destination destination;
}
```

这里 Destination 对象使用 `@Resource` 对象，传入一个 `name` 参数，通过 byName 方式自动注入，以防 Spring 配置了多个 Destination 对象后使用 `@AutoWired` 报错。

**saveItem() 方法**用于：

1. 把商品信息添加到商品表中
2. 把商品描述信息添加到商品描述表中
3. 把商品的 id 号发送到 ActiiveMQ 消息队列中

代码实现如下：

```java
public TaotaoResult saveItem(TbItem item, String desc) {
		// 生成商品的 id
		final long itemId = IDUtils.genItemId();
		// 1.补全item 的其他属性
		item.setId(itemId);
		item.setCreated(new Date());
		// 1-正常，2-下架，3-删除',
		item.setStatus((byte) 1);
		item.setUpdated(item.getCreated());
		// 2.插入到item表 商品的基本信息表
		mapper.insertSelective(item);
		// 3.补全商品描述中的属性
		TbItemDesc desc2 = new TbItemDesc();
		desc2.setItemDesc(desc);
		desc2.setItemId(itemId);
		desc2.setCreated(item.getCreated());
		desc2.setUpdated(item.getCreated());
		// 4.插入商品描述数据
		// 注入 tbitemdesc 的 Mapper
		descmapper.insertSelective(desc2);

		// 添加发送消息的业务逻辑
		jmstemplate.send(destination, new MessageCreator() {

			@Override
			public Message createMessage(Session session) throws JMSException {
				//发送的消息
				return session.createTextMessage(itemId+"");
			}
		});
		// 5.返回taotaoresult
		return TaotaoResult.ok();
	}
```

### 消费者 Consumer

在 taotao-search-service 中消费消息。需要加入 ActiveMQ 的依赖。

**applicationContext-activemq.xml 配置内容：**

- 通用连接工厂 SingleConnectionFactory
- 目标连接工厂 ActiveMQConnectionFactory
- 接收和发送消息的目的地 ActiveMQTopic（发布/订阅）
- 监听器 MyMessageListener，这里的监听器实现了监听接口类 MessageListener
- 监听容器 DefaultMessageListenerContainer

功能分析：

1. 接收消息，创建 MessageListener 接口的实现类 MyMessageListener

**MessageListener 接口的实现类：**

在 taotao-search-service 下创建一个类 ItemChangeMessageListener，实现了 MessageListener，用于消息的接收，接收的数据为新添加的商品的 `id` 号。实现接口的消息接收方法 `onMessage()`，该方法流程如下：

1. 判断消息的类型是否为 TextMessage
2. 如果是，获取商品的 id
3. 通过商品的 id 查询数据，需要开发 Mapper，通过 id 查询商品搜索时的数据

代码如下：

```java
public class ItemChangeListener implements MessageListener {

	@Autowired
	private SearchItemService searchItemService;

	@Override
	public void onMessage(Message message) {
		try {
			TextMessage textMessage = null;
			Long itemId = null;
			//取商品id
			if (message instanceof TextMessage) {
				textMessage = (TextMessage) message;
				itemId = Long.parseLong(textMessage.getText());
			}
			//向索引库添加文档
            searchservice.updateItemById(itemId);
		} catch (Exception e) {
			e.printStackTrace();
		}
	}
}
```

**服务层：**

服务层主要调用 dao 层方法 `updateSearchItemById(itemId)`，通过商品 id 来更新搜索商品信息。

代码如下：

```java
@Service
public class SearchServiceImpl implements SearchService {

	@Override
	public TaotaoResult updateSearchItemById(Long itemId) throws Exception {
		return searchdao.updateSearchItemById(itemId);
	}
}

```

**Dao 层：**

根据商品 id 查询商品信息。需要在 SearchItemMapper 接口中添加方法 `getSearchItemById(itemId)`，该方法通过商品的 id 来查询商品的数据。代码如下：

```java
public interface SearchItemMapper {
	//查询所有的商品的数据
	public  List<SearchItem> getSearchItemList();

	//根据商品的id查询商品的数据
	public SearchItem getSearchItemById(Long itemId);
}
```

Mapper 的映射 xml 文件 SearchItemMapper.xml 需要添加相对应的 select 语句：

```sql
<mapper namespace="com.taotao.search.mapper.SearchItemMapper" >
 	<select id="getSearchItemById" parameterType="long" resultType="com.taotao.common.pojo.SearchItem">
 		select a.id, a.title, a.image, a.price, a.sell_point, b.`name` as category_name, c.item_desc
		from tb_item a, tb_item_cat b, tb_item_desc c
		where a.cid = b.id
		and a.id = c.item_id
		and a.id = #{itemId}
 	</select>
</mapper>
```

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
4. 在每个 zookeeper 目录下创建一个 data 目录，在 data 目录下创建一个 myid 文件，文件名就叫做 `myid`。内容就是每个实例的 id。例如 1、2、3
   > `echo 1 >> myid`
5. 修改配置文件。把每一个 zookeeper 下的 conf 目录下的 zoo_sample.cfg 文件改名为 zoo.cfg
   > `mv zoo_sample.cfg zoo.cfg`
6. 配置每一个 Zookeeper 的 dataDir（zoo.cfg 配置文件中的内容） clientPort 分别为 2181 2182 2183
   ![image](https://ws1.sinaimg.cn/large/d4556b75ly1g4siwx9m06j20og0ditj0.jpg)
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

# 项目问题排查

## JVM Crash

分析原因：

1. JVM GC 时间过长，导致应用暂停/JVM 内存溢出

   排查：查看 JVM 日志进行日志分析。

   通过日志查看，并没有发现导致 JVM 内存溢出的错误，如果是因为 JVM 内存不足的话在日志里面应该会出现 java.lang.OutOfMemoryError: Java heap space （堆内存中的空间不足）错误 或者 java.lang.OutOfMemoryError: Metaspace （元数据区(Metaspace) 已被用满）

2. JVM Crash 日志分析

   日志文件在 tomcat 安装 bin 目录里面的 hs_err_pid%.log 日志文件中

   日志分析：

   首先看到日志头提示出现问题帧信息：`C [tcnative-1.dll+0X802e]`。
   C  表示帧类型为本地帧，并且出现问题的代码是 tomcat 的 native 包下的 tcnative-1.dll

   继续往下看导致出错的线程信息：
   看到导致 Error 线程信息是一个名字叫 `http-apr-8080-Poller` 的线程名，执行到 `tomcat.jni.Poll.poll` 方法方法（推测是一个本地方法），通过 JNI（java 本地接口）调用 tcnative.dll 中的代码时出现了异常。

因此我们推断是 tomcat 本地代码库出现了问题，因此我们会考虑更换 tomcat 版本。考虑到之前 tomcat 版本是 7.0 的，了解到 tomcat8.0.44 对 native 包进行了较大版本的升级（从 1.1x 到 1.2x），因此对 tomcat 进行升级到 8.0.44。之后问题解决

## Redis 相关错误

异常 `No reachable node in cluster`

分析原因：

1. 调用了 JedisCluster.close()方法，原因：我们使用的是 redis3.0 的集群，用 jedis 的 JedisCluster.close()方法造成的集群连接关闭的情况。 jedisCluster 内部使用了池化技术，每次使用完毕都会自动释放 Jedis 因此不需要关闭。如果调用 close 方法后再调用 jedisCluster 的 api 进行操作时就会出现如上错误。

2. Redis 集群宕机了。我们在 Redis 命令窗口中输入 cluster info 信息，发现：cluster_state:fail 的消息，知道 Redis 集群宕机了，之后使用 Redis 命令存储一个 key-value 值，的确发现提示错误：`(error)The cluster is down`。

于是我们通过`./redis-trib.rb check 192.168.107.132:7001` 检查了一个集群结点，Redis 会自动检查集群中的所有结点，发现 16384 个槽并没有被所有结点覆盖，其余结点都是不能连接的。

于是我通过 fix 命令进行修复，可是发现问题仍然没有解决

之后我检查其他结点，竟然都是这样的错误，说明整个集群出错了，于是我删除了集群下的 `dump.rdb` 和 `nodes.conf` 两个文件，并将将几个 Redis 数据库结点清空，并将 bind 配置为 0.0.0.0（如果绑定到 0.0.0.0 那么所有机器上的地址都可以访问服务，如果绑定到特定的 ip 那么只能是特定的 ip 能够到达 redis 服务） 重新创建，发现成功了！！！

## JVM 调优

我们使用 Visual VM 堆 JVM 堆内存进行监控，并安装 Visual GC 插件对 JVM 内存的各个区域进行监控，结合 JVM 日志进行分析调优

1. 首先发现堆空间进行了扩容，说明初始堆内存设置过小，初始堆内容起初是 128M，此时我把初始堆内容使用-Xms 命令设置到和最大堆内存一样大，为 512M

2. 并发测试我们发现频繁进行 minor gc，并且在 GC 日志中发现了频繁的 GC（Allocation Failure），Eden 区的总容量此时大约 300M，二个 Survivor 占 100M，可知新生代的空间设置过小了，因此我们考虑将堆内存从 512M 增大到 1.00G

3. 我们发现 Eden 区和二个 Survivor 大小比为 3：1：1，为了减少更多的对象在 Eden 区内，我们增大 Eden 区的空间，使得 Eden 区和二个 Survivor 为 8：1：1，使用参数-XX:SurvivorRatio=8

## 人员分工
