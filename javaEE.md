[toc]
<!-- TOC -->

- [javaEE](#javaee)
    - [Spring](#spring)
        - [1、说一下IOC和AOP?](#1说一下ioc和aop)
        - [2、介绍一下bean的生命周期](#2介绍一下bean的生命周期)
        - [3、Spring里面注解用过没有？autowired 和resource区别？](#3spring里面注解用过没有autowired-和resource区别)
        - [4、@Controller和@RestController的区别？](#4controller和restcontroller的区别)
        - [5、依赖注入的方式有几种，哪几种？Bean的装配方式有几种，哪几种？](#5依赖注入的方式有几种哪几种bean的装配方式有几种哪几种)
        - [6、springIOC原理？自己实现IOC要怎么做，哪些步骤？](#6springioc原理自己实现ioc要怎么做哪些步骤)
        - [7、Spring中BeanFactory和ApplicationContext的区别？BeanFactory和FactoryBean的区别？](#7spring中beanfactory和applicationcontext的区别beanfactory和factorybean的区别)
        - [8、请问Spring中Bean的作用域有哪些？](#8请问spring中bean的作用域有哪些)
        - [9、谈谈Spring中自动装配的方式有哪些？](#9谈谈spring中自动装配的方式有哪些)
        - [10、aop的应用场景？日志记录和异常处理如何使用？](#10aop的应用场景日志记录和异常处理如何使用)
        - [11、AOP的原理是什么？](#11aop的原理是什么)
        - [12、你如何理解AOP中的连接点（Joinpoint）、切点（Pointcut）、增强（Advice）、引介（Introduction）、织入（Weaving）、切面（Aspect）这些概念？](#12你如何理解aop中的连接点joinpoint切点pointcut增强advice引介introduction织入weaving切面aspect这些概念)
        - [13、Spring支持的事务管理类型有哪些？你在项目中使用哪种方式？](#13spring支持的事务管理类型有哪些你在项目中使用哪种方式)
        - [14、介绍一下spring？](#14介绍一下spring)
        - [15、Struts拦截器和Spring AOP区别？](#15struts拦截器和spring-aop区别)
        - [16、spring框架的优点？缺点？](#16spring框架的优点缺点)
        - [17、选择使用Spring框架的原因（Spring框架为企业级开发带来的好处有哪些）？](#17选择使用spring框架的原因spring框架为企业级开发带来的好处有哪些)
        - [18、持久层设计要考虑的问题有哪些？你用过的持久层框架有哪些？](#18持久层设计要考虑的问题有哪些你用过的持久层框架有哪些)
        - [19、Spring声明式事务](#19spring声明式事务)
        - [20、Spring事务传播机制](#20spring事务传播机制)
        - [21、Spring中如何让A和B两个bean按顺序加载Spring中如何让A和B两个bean按顺序加载](#21spring中如何让a和b两个bean按顺序加载spring中如何让a和b两个bean按顺序加载)
        - [Spring源码](#spring源码)
    - [Mybatis](#mybatis)
        - [1、解释一下MyBatis中命名空间（namespace）的作用。](#1解释一下mybatis中命名空间namespace的作用)
        - [2、MyBatis中的动态SQL是什么意思？](#2mybatis中的动态sql是什么意思)
        - [3、Mybatis中Mapper接口编程原理](#3mybatis中mapper接口编程原理)
    - [SpringMVC](#springmvc)
        - [1、Spring MVC注解的优点](#1spring-mvc注解的优点)
        - [2、springmvc和spring-boot区别？](#2springmvc和spring-boot区别)
        - [3、SpringMVC的运行机制，运行机制的每一部分的相关知识？](#3springmvc的运行机制运行机制的每一部分的相关知识)
        - [4、谈谈Spring MVC的工作原理是怎样的？](#4谈谈spring-mvc的工作原理是怎样的)

<!-- /TOC -->
# javaEE
## Spring

[博客大致写了Spring的主要代码流程](https://www.jianshu.com/p/5c781f264467?from=groupmessage)

[博主自己动手写了一个Spring IOC](https://www.cnblogs.com/jeysin/p/10091269.html)


### 说一下IOC和AOP?

IOC：控制反转，控制权的转移，应用程序本身不负责依赖对象的创建和维护，而是由外部容器负责创建和维护。 许多应用都是通过彼此间的相互合作来实现业务逻辑的，如类A要调用类B的方法，以前我们都是在类A中，通过自身new一个类B，然后在调用类B的方法，现在我们把new类B的事情交给spring来做，在我们调用的时候，容器会为我们实例化。

AOP： 面向切面编程，它利用一种称为“横切”的技术，剖解开封装的对象内部，并将那些影响了多个类的公共行为封装到一个可重用模块，并将其名为“Aspect”，即切面。所谓“切面”，简单地说，就是将那些与业务无关，却为业务模块所共同调用的逻辑或责任封装起来，便于减少系统的重复代码，降低模块间的耦合度，并有利于未来的可操作性和可维护性。主要的功能是：日志记录，性能统计，安全控制，事务处理，异常处理。

### 介绍一下bean的生命周期

[spring 生命周期最详解](https://blog.csdn.net/qq_23473123/article/details/76610052)

[SpringBean生命周期详解](https://blog.csdn.net/lisongjia123/article/details/52091013)

[Spring中Bean的生命周期](https://cloud.tencent.com/developer/article/1362778)

所谓 Bean 的生命周期，就是一个 Bean 从创建到销毁，所经历的各种方法调用。大致包含下面几个方法（不是全部）:
* Bean 的实例化，调用了构造方法。
* 使用 setter 方法填充属性。
* 一旦依赖注入完成，调用 Spring 感知接口 BeanNameAware.setBeanName()。
* BeanFactoryAware.setBeanFactory() 方法
* ApplicationContextAware 的 setApplicationContext() 方法
* BeanPostProcessor.postProcessBeforeInitialization 方法。
* @PostConstruct 标注的方法。
* InitializingBean.afterPropertiesSet() 方法
* 自定义的 init-method 方法
* BeanPostProcessor.postProcessAfterInitialization()

此时 Bean 可以用了。当容器关闭的时候，则会调用：

* @PreDestroy 标注的方法
* DisposableBean.destroy()
* 自定义的 destroy-method
* 对象自定义的 finalize 方法

BeanPostProcessor 有一个不同于其他 3 个的点，实现 BeanPostProcessor 接口后，容器中的对象，在初始化前和初始化后，都会调用 postProcessBeforeInitialization 方法和 postProcessAfterInitialization 方法。即使这个对象并未实现 BeanPostProcessor 接口。而其他如@PostConstruct 注解等的实现方式中，仅作用在当前的 bean 上。因此 BeanPostProcessor 是全局性的，对容器中所有的对象都有效。

### Spring里面注解用过没有？autowired 和resource区别？

[@Autowired 与@Resource的区别（详细）](https://blog.csdn.net/weixin_40423597/article/details/80643990)

**共同点：**

两者都可以写在字段和setter方法上。两者如果都写在字段上，那么就不需要再写setter方法。

**不同点：**

1. @Autowired按byType自动注入，默认情况下它要求依赖对象必须存在，如果允许null值，可以设置它的required属性为false。如果我们想使用按照名称（byName）来装配，可以结合@Qualifier注解一起使用
2. @Resource默认按byName自动注入，@Resource有两个属性是比较重要的，分是name和type，Spring将@Resource注解的name属性解析为bean的名字，而type属性则解析为bean的类型。所以如果使用name属性，则使用byName的自动注入策略，而使用type属性时则使用byType自动注入策略。如果既不指定name也不指定type属性，这时将通过反射机制使用byName自动注入策略。 如果指定了name，则从上下文中查找名称（id）匹配的bean进行装配，找不到则抛出异常；如果指定了type，则从上下文中找到类型匹配的唯一bean进行装配，找不到或者找到多个，都会抛出异常

### @Controller和@RestController的区别？

[@Controller和@RestController源码解析](https://www.cnblogs.com/sgh1023/p/10165470.html)

[@Controller和@RestController的区别](https://www.cnblogs.com/clwydjgs/p/9255046.html)

@ResponseBody注解告知Spring，要将返回的对象作为资源发送给客户端。这个过程跳过正常的模型/视图流程中视图解析的过程，而是使用Spring自带的各种Http消息转换器将控制器产生的数据转换为客户端需要的表述形式。 当处理请求时候，@ResponseBody和@RequestBody是启用消息转换的一种简介和强大方式。但是，如果控制器里面的每个方法都需要信息转换功能的话，那么这些注解就会带有一定程度的重复性。所以，Spring 4.0引入了@RestController注解，如果在控制器类上面使用@RestController注解，我们不必再为每个方法添加@ResponseBody注解，因为Spring会为该控制器下面的所有方法应用消息转换功能。

**总结：**

1. @RestController 相当于 @ResponseBody ＋ @Controller 一起作用。
2. 使用 @Controller 注解，在对应的方法上，视图解析器可以解析return的jsp, html页面，并且跳转到相应页面，若返回json等内容到页面，则需要加@ResponseBody注解；
3. 相当于@Controller + @ResponseBody两个注解的结合，返回json数据不需要在方法前面加@ResponseBody注解了，但使用@RestController这个注解，就不能返回jsp,html页面，视图解析器无法解析jsp,html页面

### 依赖注入的方式有几种，哪几种？Bean的装配方式有几种，哪几种？

依赖注入方式：

1. 构造器注入；
2. setter注入。首先把构造方法声明为无参数的，然后使用setter注入为其设置对应的值；
3. 接口注入。例如外部的数据库连接资源，通过JNDI获取的数据源，通过Spring的接口注入实现

装配方式：
1. 通过XML方式装配Bean
2. 通过注解装配Bean。Spring中提供了二种方式来让Spring IOC容器发现Bean
   1. 组件扫描，@Component
   2. 自动装配，@Autowired

### springIOC原理？自己实现IOC要怎么做，哪些步骤？

[自己动手实现一个轻量级Spring IOC容器](https://www.cnblogs.com/jeysin/p/10091269.html)

IOC：控制反转，控制权的转移，应用程序本身不负责依赖对象的创建和维护，而是由外部容器负责创建和维护。 许多应用都是通过彼此间的相互合作来实现业务逻辑的，如类A要调用类B的方法，以前我们都是在类A中，通过自身new一个类B，然后在调用类B的方法，现在我们把new类B的事情交给spring来做，在我们调用的时候，容器会为我们实例化。

**自己要实现IOC，可以考虑以下步骤：**

1. 定义POJO，二个POJO相互引用，以测试我们的IOC容器在为bean注入属性的时候是否能解决这种相互依赖的问题；
2. 写一个配置文件application.xml，在配置文件中声明这两个bean，并给它们设置相应的属性。 我们希望我们的IOC容器最后能像Spring一样从这个xml中读取bean，然后注入属性，然后我们通过getBean方法可以从中直接取出bean来使用；
3. 实现一个类：BeanDefinition，从配置文件中读取出bean的信息后并封装在BeanDefinition类中。BeanDefinition的作用就是对bean的一层封装，封装bean的名字beanClassName， bean的属性值propertyMap，这个beanClassName是我们从配置文件中读取到的， propertyMap里面存的是每一个具体的bean的所有属性值；
4. 写一个读取配置文件的接口 InputStream并写一个实现类。用来读取配置文件信息；
5. 定义一个bean的引用类 BeanReference，用来解决类之间依赖的问题。 遇到配置文件中的value标签，可以直接将name和value作为一组键值对直接存入BeanDefinition中的propertyMap就好了， 如果遇到ref这种引用， 我们就可以把name和BeanReference作为一个键值对存入propertyMap中；
6. 定义解析配置文件的类. BeanDefinitionReader.java以及相应的实现XmlBeanDefinitionReader.java，配置文件解析信息存在一个beanDifinitionMap中，里面存的是name和BeanDidinition的对应关系；
7. 定义一个BeanFactory接口以及接口的实现。BeanFactory用来创建Bean并进行依赖注入，Bean的创建主要是拿到上文beanDifinitionMap解析的bean，之后通过反射机制创建一个相应的bean，创建bean之后，在通过注入属性的方式来解决依赖循环问题；
8. 定义ApplicationContext接口以及相应的实现 ClassPathXmlApplicationContext.java。ClassPathXmlApplicationContext实现一个refresh方法，该方法实现了将XmlBeanDefinitionReader中读取到的bean的定义向BeanFactory中转移的过程。

### Spring中BeanFactory和ApplicationContext的区别？BeanFactory和FactoryBean的区别？

**BeanFactory和ApplicationContext的区别：**

1. 两者都是通过xml配置文件加载bean,ApplicationContext和BeanFacotry相比,提供了更多的扩展功能，但其主要区别在于后者是延迟加载,如果Bean的某一个属性没有注入，BeanFacotry加载后，直至第一次使用调用getBean方法才会抛出异常；而ApplicationContext则在初始化自身是检验，这样有利于检查所依赖属性是否注入；所以通常情况下我们选择使用ApplicationContext 
2. BeanFactory和ApplicationContext都支持BeanPostProcessor、BeanFactoryPostProcessor的使用，但两者之间的区别是：BeanFactory需要手动注册，而ApplicationContext则是自动注册。

   Applicationcontext比beanFactory加入了一些更好使用的功能。而且beanFactory的许多功能需要通过编程实现而Applicationcontext可以通过配置实现。比如后处理bean ， Applicationcontext 直接配置在配置文件即可，而 beanFactory这要在代码中显示的写出来才可以被容器识别。

3. ApplicationContext 还提供了更完整的框架功能： MessageSource,提供国际化的消息访问；资源访问， 如URL和文件；事件传播特性，即支持aop特性

**BeanFactory和FactoryBean的区别：**

BeanFactory是个Factory，也就是IOC容器或对象工厂，FactoryBean是个Bean。在Spring中，所有的Bean都是由BeanFactory(也就是IOC容器)来进行管理的。但对FactoryBean而言，这个Bean不是简单的Bean，而是一个能生产或者修饰对象生成的工厂Bean,它的实现与设计模式中的工厂模式和修饰器模式类似。

一般情况下，Spring通过反射机制利用<bean>的class属性指定实现类实例化Bean，在某些情况下，实例化Bean过程比较复杂，如果按照传统的方式，则需要在<bean>中提供大量的配置信息，例如使用大量的<property>元素标签。配置方式的灵活性是受限的，FactoryBean的工厂类接口，用户可以通过实现该接口定制实例化Bean的逻辑，可以通过逗号分割符的方式一次性的为类的所有属性指定配置值。

FactoryBean支持泛型，即接口声明改为FactoryBean<T>的形式。一个Bean想要实现 FactoryBean ，必须实现以下三个接口：
1. Object getObject():返回由FactoryBean创建的Bean的实例
2. boolean isSingleton():确定由FactoryBean创建的Bean的作用域是singleton还是prototype；
3. getObjectType():返回FactoryBean创建的Bean的类型。


[BeanFactory、ApplicationContext以及FactoryBean](https://www.jianshu.com/p/d8b158fe595d)

[spring中BeanFactory和FactoryBean的区别](https://blog.csdn.net/qiesheng/article/details/72875315)

### 请问Spring中Bean的作用域有哪些？


1. singleton原型模式，默认值，IOC容器中仅存在一个Bean实例，Bean都以单例模式存在
2. prototype原型模式，在每次请求获取Bean的时候，都会创建一个新的实例，它在容器初始化的时候不会创建实例，采用的是延迟加载的形式注入Bean，当你使用的时候，才会进行实例化，每次实例化获取的对象都不是同一个，就像BeanFactory的实例化模式实例不唯一
3. request，http请求模式，在每一次http请求时会创建一个实例，该实例仅在当前http request有效
4. session会话，在每一次http请求时会创建一个实例，该实例仅在当前http session有效
5. globalSession，全局Session，供不同的portlet共享，portlet好像是类似于servlet的Web组件

如果不指定Bean的作用域，Spring默认使用singleton作用域。Java在创建Java实例时，需要进行内存申请；销毁实例时，需要完成垃圾回收，这些工作都会导致系统开销的增加。因此，prototype作用域Bean的创建、销毁代价比较大。而singleton作用域的Bean实例一旦创建成功，可以重复使用。因此，除非必要，否则尽量避免将Bean被设置成prototype作用域。

### 谈谈Spring中自动装配的方式有哪些？

1. no：不进行自动装配，手动设置Bean的依赖关系；
2. byName：根据Bean的名字进行自动装配；
3. byType：根据Bean的类型进行自动装配；
4. constructor：使用构造方法完成对象注入，其实也是根据构造方法的参数类型进行对象查找，相当于采用byType的方式；
5. autodetect：如果有默认的构造器，则通过constructor的方式进行自动装配，否则使用byType的方式进行自动装配。

### aop的应用场景？日志记录和异常处理如何使用？

[Spring AOP进行统一的异常处理和日志记录](https://segmentfault.com/a/1190000014827136)

1. 事务管理 
2. 日志记录
3. 异常处理
4. 缓存

**日志记录和异常处理步骤：**
1. 使用@Aspect注解标注一个java类，Spring将自动识别该类作为切面Bean。

```java
@Aspect
public class ExceptionAndLogAspect {
}
```
2. 在Spring配置文件中添加這個切面Bean,并启动@AspectJ支持。

```
<!-- 配置切面的类 -->
<bean id="ExceptionAndLogAspect" class="com.student.xl.util.ExceptionAndLogAspect"></bean>
<!--启动@AspectJ支持-->
<aop:aspectj-autoproxy/>
```

3. 在统一处理异常和日志的切面类中添加增强处理



```java
/**
* 统一处理异常和日志的切面类
* @author louzi
*/
@Aspect
public class ExceptionAndLogAspect {
    Logger log = Logger.getLogger(this.getClass().getName());

    //Before增强：在目标方法被执行的时候织入增强
    //匹配com.student.xl包下面的所有类的所有方法的执行作为切入点
    @Before("execution(* com.student.xl.*.*.*(..))")
    public void beforeWave(JoinPoint joinPoint){
        String className = joinPoint.getTarget().getClass().getName();
        String methodName = joinPoint.getSignature().getName();
        System.out.println("进入"+className+"类的"+methodName+"方法。");
    }
    
    //AfterReturning增强：在目标方法正常完成后被织入
    //rvt是目标方法的返回值
    @AfterReturning(returning="rvt",pointcut="execution(* com.student.xl.*.*.*(..))")
    public void afterWave(Object rvt){
        System.out.println("获得目标方法返回值："+rvt);
    }
    
    //AfterThrowing增强：处理程序中未处理的异常
    //ex是目标方法拋出的异常
    @AfterThrowing(throwing="ex",pointcut="execution(* com.student.xl.*.*.*(..))")
    public void exceptionDispose(JoinPoint joinPoint,Throwable ex){
        String className = joinPoint.getTarget().getClass().getName(); //切入方法所属类名
        String methodName = joinPoint.getSignature().getName(); //切入的方法名
        Object[] params = joinPoint.getArgs(); //目标方法传入的参数
        String param = "入参为：";
        
        if(params != null && params.length > 0){
            for(Object p : params){
                param += p + ",";
            }
            param = param.substring(0,param.lastIndexOf(","));
        }
        log.error("[Exception]:["+className+"]"+methodName+":" + ex);
        System.out.println("【"+className+"】:"+methodName+"执行时出现异常："+ex+"。");
        System.out.println(param);
    }
}
```

### AOP的原理是什么？

[Java动态代理技术](https://app.yinxiang.com/fx/63f8a49e-f979-4743-83f6-1bceb15b242b)

动态代理，在动态代理中使用了拦截器链。


动态代理实现主要是实现InvocationHandler接口，并且将目标对象注入到代理对象中，利用反射机制来执行目标对象的方法。目标对象的方法执行主要是通过调用InvocationHandler类的method.invoke()方法，在invoke()方法前后加入拦截器链来实现aop的横切技术。


### 你如何理解AOP中的连接点（Joinpoint）、切点（Pointcut）、增强（Advice）、引介（Introduction）、织入（Weaving）、切面（Aspect）这些概念？


1. 连接点（Joinpoint）：是程序执行中的一个精确执行点，例如类中的一个方法。它是一个抽象的概念，在实现AOP时，并不需要去定义一个join point；

2. 切点（Pointcut）：本质上是一个捕获连接点的结构。在AOP中，可以定义一个point cut，来捕获相关方法的调用；

3. 增强（Advice）： 增强是织入到目标类连接点上的一段程序代码。 Spring提供的增强接口都是带方位名的，如：BeforeAdvice、AfterReturningAdvice、ThrowsAdvice等；

4. 引介（Introduction）：是指在不更改源代码的情况，给一个现有类增加属性、方法，以及让现有类实现其它接口或指定其它父类等，从而改变类的静态结构；
5. 织入（Weaving）：织入是将增强添加到目标类具体连接点上的过程，AOP有三种织入方式：
    1. 编译期织入：需要特殊的Java编译期（例如AspectJ的ajc）；
    2. 装载期织入：要求使用特殊的类加载器，在装载类的时候对类进行增强；
    3. 运行时织入：在运行时为目标类生成代理实现增强。Spring采用了动态代理的方式实现了运行时织入，而AspectJ采用了编译期织入和装载期织入的方式。

5. 切面（Aspect）： 切面是由切点和增强（引介）组成的，它包括了对横切关注功能的定义，也包括了对连接点的定义。


### Spring支持的事务管理类型有哪些？你在项目中使用哪种方式？
Spring支持编程式事务管理和声明式事务管理。选择声明式事务管理， 因为这种方式和应用程序的关联较少，因此更加符合轻量级容器的概念。

### 介绍一下spring？

1. Spring的核心是一个轻量级（Lightweight）的容器（Container）.轻量级是指它的创建和销毁不需要消耗太多的资源，意味着可以在程序中经常创建和销毁session 的对象；重量级意味不能随意的创建和销毁它的实例，会占用很多的资源。
2. Spring是实现Ioc（Inversion of Control）容器和非入侵性（No intrusive）的框架
3. Spring提供AOP（Aspect-oriented programming）概念的实现方式
4. Spring提供对持久层（Persistence）、事务（Transaction）的支持
5. Spring提供MVC Web框架的是实现，并对一些常用的企业服务api提供一致的模型封装
6.Spring提供了对现存的各种框架（Structs、JSF、Hibernate、Ibatis、Webwork等）相整合的方案

### Struts拦截器和Spring AOP区别？
### spring框架的优点？缺点？

**优点：**
1. 轻量：基础版本只有2MB
2. 解耦方便：通过控制反转，实现松散耦合，对象们给出他们的依赖，而不是通过创建或查找对象的依赖
3. 支持AOP：通过面向切面编程，实现业务逻辑和系统服务分开，方便的实现对程序进行权限拦截、运行监控等功能
4. 支持声明式事务：spring提供事务管理接口，实现本地事务和全局事务的管理
5. 异常处理：提供异常处理接口，把hibernate或者jdbc的异常转为一致的unchecked异常
6. 易于集成其他优秀框架，Spring内部提供了对各种优秀框架的支持

**缺点：**
1. jsp中要写很多代码、控制器过于灵活，缺少一个公用控制器；
2. Spring不支持分布式，这也是EJB仍然在用的原因之一。


### 选择使用Spring框架的原因（Spring框架为企业级开发带来的好处有哪些）？

从（1）IoC容器（2） AOP（3） MVC（4）事务管理四方面将

### 持久层设计要考虑的问题有哪些？你用过的持久层框架有哪些？

所谓”持久”就是将数据保存到可掉电式存储设备中以便今后使用，简单的说，就是将内存中的数据保存到关系型数据库、文件系统、消息队列等提供持久化支持的设备中。持久层就是系统中专注于实现数据持久化的相对独立的层面。持久层设计的目标包括：
1. 数据存储逻辑的分离，提供抽象化的数据访问接口。
2. 数据访问底层实现的分离，可以在不修改代码的情况下切换底层实现。
3. 资源管理和调度的分离，在数据访问层实现统一的资源调度（如缓存机制）。
4. 数据抽象，提供更面向对象的数据操作。

持久层框架有：Hibernate、MyBatis


### Spring声明式事务

1. 声明式事务允许自定义事务接口——TransactionDefinition,它可以由XML或者注解@Transactional配置,XML的形式较少用；
2. 声明式事务需要配置注解驱动；
3. Transactional二个关键配置项isolation（隔离级别）和propagation（传播行为）。

**声明式事务流程：**

1. Spring通过事务管理器创建事务，并设置事务属性；
2. 执行开发者的代码逻辑；
3. 产生异常且满足事务回滚配置条件，事务回滚，否则事务提交；
4. 事务资源释放。

### Spring事务传播机制

[Spring的事务传播机制实例](https://www.jianshu.com/p/25c8e5a35ece)


1. Propagation.REQUIRED：如果当前没有事务，就新建一个事务，如果已经存在一个事务中，加入到这个事务中，这是Spring默认的传播行为
2. Propagation.SUPPORTS：支持当前事务，如果当前没有事务，就以非事务方式执行
3. Propagation.MANDATORY：使用当前的事务，如果当前没有事务，就抛出异常
4. Propagation.REQUIRES_NEW：无论是否存在当前事务，方法都会在新的事务中运行
5. Propagation.NOT_SUPPORTED： 以非事务方式执行操作，如果当前存在事务，就把当前事务挂起
6. Propagation.NEVER： 以非事务方式执行，如果当前存在事务，则抛出异常
7. Propagation.NESTED：嵌套事务，如果当前存在事务，则在嵌套事务内执行。也就是调用方法如果抛出异常只回滚自己内部执行的SQL，而不回滚主方法的SQL

### Spring中如何让A和B两个bean按顺序加载Spring中如何让A和B两个bean按顺序加载

1. 依赖关系

2. 使用depends-on属性，depends-on用来指定Bean初始化及销毁时的顺序。 

   适用的场景：用来确定bean定义中依赖关系不明确或者没有直接依赖关系时，指定bean在初始化或销毁时的明确顺序。一个bean可以依赖多个bean，可以通过逗号(",")或者分号(";")来定义多个依赖对象：

```
<bean id=a Class="com.twovv.A" depends-on="b,c,d" />
<bean id=b Class="com.twovv.B" />
<bean id=c Class="com.twovv.C" />
<bean id=d Class="com.twovv.D" />
```
### Spring源码了解吗？能讲一下大致过程吗？

[死磕 Spring（此人的博客写的超级棒，有很多值得参考的内容）](http://cmsblogs.com/?cat=206)

**1. Spring统一资源加载策略**

* 统一资源：Resource
   
   Spring 框架所有资源的抽象和访问接口,AbstractResource为其接口的默认实现
![](https://gitee.com/chenssy/blog-home/raw/master/image/201811/spring-201805091003.jpg)

* 统一资源定位：ResourceLoader

  Spring 将资源的定义和资源的加载区分开了，Resource 定义了统一的资源，ResourceLoader 为 Spring 资源加载的统一抽象，具体的资源加载则由相应的实现类来完成

  ResourceLoader 接口提供两个方法：`getResource()`和`getClassLoader()`。
  * `getResource()`：根据所提供资源的路径 location 返回 Resource 实例
  * `getClassLoader()`： 返回 ClassLoader 实例

  DefaultResourceLoader 同样也是 ResourceLoader 的默认实现  


**2. 装载 Bean**

装载资源整个过程大致分为三个步骤：资源定位、装载、注册

```java
//根据 Xml 配置文件创建 Resource 资源对象。ClassPathResource 是 Resource 接口的子类，bean.xml 文件中的内容是我们定义的 Bean 信息
ClassPathResource resource = new ClassPathResource("bean.xml");
//创建一个 BeanFactory。
DefaultListableBeanFactory factory = new DefaultListableBeanFactory();
//创建 XmlBeanDefinitionReader 读取器，用于载入 BeanDefinition 。
XmlBeanDefinitionReader reader = new XmlBeanDefinitionReader(factory);
//开启 Bean 的载入和注册进程，完成后的 Bean 放置在 IOC 容器中
reader.loadBeanDefinitions(resource);
```

* **Resource 资源定位**，通过统一资源加载策略
* **BeanDefinition 的载入和解析**。BeanDefinitionReader 读取、解析 Resource 资源，也就是将用户定义的 Bean 表示成 IOC 容器的内部数据结构：BeanDefinition。在 IOC 容器内部维护着一个 BeanDefinition Map 的数据结构，在配置文件中每一个 <bean> 都对应着一个BeanDefinition对象。
* **BeanDefinition 注册**，向IOC容器注册在第二步解析好的 BeanDefinition，这个过程是通过 BeanDefinitionRegistry 接口来实现的。在 IOC 容器内部其实是将第二个过程解析得到的 BeanDefinition 注入到一个 HashMap 容器中，IOC 容器就是通过这个 HashMap 来维护这些 BeanDefinition 的。这个过程并没有完成依赖注入。

整个代码大致流程将 Resource 资源封装成 EncodedResource，完成后从 encodedResource 获取封装的 Resource 资源并从 Resource 中获取相应的 InputStream， 之后获取 Document 实例， 根据获取的 Document实例注册 Bean信息

**3. 获取验证模型**

* DTD：文档类型定义，为 XML 文件的验证机制
* XSD：对DTD进行扩展
  

**4. BeanDefinition 的载入和解析**

`reader.loadBeanDefinitions(resource);` 开启 BeanDefinition 的解析过程.

在这个方法会将资源 resource 包装成一个 EncodedResource 实例对象，将 Resource 封装成 EncodedResource 主要是为了对 Resource 进行编码，保证内容读取的正确性，然后调用 `loadBeanDefinitions()` 方法。
在该方法中主要做两件事：
1. 根据 xml 解析源获取相应的 Document 对象
2. 调用 registerBeanDefinitions() 开启 BeanDefinition 的解析注册过程。

**转换为 Document 对象：**

调用 `doLoadDocument()` 会将 Bean 定义的资源转换为 Document 对象。

转换为 Document 对象后，下一步就是将其解析为 Spring IOC 管理的 Bean 对象并将其注册到容器中。

首先创建 BeanDefinition 的解析器 BeanDefinitionDocumentReader，然后调用 `documentReader.registerBeanDefinitions()` 开启解析过程，这里使用的是委派模式，具体的实现由子类 DefaultBeanDefinitionDocumentReader 完成。

```java
public void registerBeanDefinitions(Document doc, XmlReaderContext readerContext) {
       // 获得XML描述符
        this.readerContext = readerContext;
        logger.debug("Loading bean definitions");

        // 获得Document的根元素
        Element root = doc.getDocumentElement();

        // 解析根元素
        doRegisterBeanDefinitions(root);
    }
```

**对 Document 对象的解析：**

从 Document 对象中获取根元素 root，然后调用 `doRegisterBeanDefinitions()` 开启真正的解析过程。

迭代 root 元素的所有子节点，对其进行判断，若节点为默认命名空间，则ID调用 `parseDefaultElement()` 开启默认标签的解析注册过程，否则调用 `parseCustomElement()` 开启自定义标签的解析注册过程。

最终解析动作落地在两个方法处：`parseDefaultElement(ele, delegate)` 和 `delegate.parseCustomElement(root)`。我们知道在 Spring 有两种 Bean 声明方式：

* 配置文件式声明：`<bean id="studentService" class="org.springframework.core.StudentService" />`
* 自定义注解方式：`<tx:annotation-driven>`

两种方式采用不同的解析方法，如果根节点或者子节点采用默认命名空间的话，则调用 `parseDefaultElement()` 进行解析，否则调用 `delegate.parseCustomElement()` 方法进行自定义解析。

 四大标签：import、alias、bean、beans

**5. BeanDefinition注册**

经过上面的解析，则将 Document 对象里面的 Bean 标签解析成了一个个的 BeanDefinition ，下一步则是将这些 BeanDefinition 注册到 IOC 容器中。动作的触发是在解析 Bean 标签完成后。

其实这里面也是调用 BeanDefinitionRegistry 的 `registerBeanDefinition()` 来注册 BeanDefinition ，不过最终的实现是在 DefaultListableBeanFactory 中实现。

最核心的部分是 `this.beanDefinitionMap.put(beanName, beanDefinition)` ，所以注册过程也就是利用一个 Map 的集合对象来存放，key 是 beanName，value 是 BeanDefinition。

**6. 加载 Bean**

在注册好 BeanDefinition 之后，BeanDefinition 并不是我们真正想要的 bean，因为它还仅仅只是承载了我们需要的目标 bean 的信息，从 BeanDefinition 到我们需要的目标还需要一个漫长的 bean 的初始化阶段

bean 的初始化节点由第一次调用 `getBean()` (显式或者隐式)开启

```java
public Object getBean(String name) throws BeansException {
        return doGetBean(name, null, null, false);
}
```

`getBean()`内部调用 `doGetBean()` 方法，`doGetBean()` 可以分为以下几个过程：
1. 转换 beanName
2. 尝试从缓存中加载单例 bean
3. bean 的实例化
4. 原型模式的依赖检查
5. 尝试从 parentBeanFactory 获取 bean 实例
6. 获取 RootBeanDefinition，并对其进行合并检查
7. 依赖检查。某个 bean 依赖其他 bean ，则需要先加载依赖的 bean
8. 对不同的 scope 进行处理
9. 类型转换处理

**从缓存中获取 bean**

Spring 中根据 scope 可以将 bean 分为以下几类：singleton、prototype 和 其他。

* singleton：在 Spring 的 IoC 容器中只存在一个对象实例，所有该对象的引用都共享这个实例。Spring 容器只会创建该 bean 定义的唯一实例，这个实例会被保存到缓存中，并且对该bean的所有后续请求和引用都将返回该缓存中的对象实例。
* prototype：每次对该bean的请求都会创建一个新的实例
* 其他：其他包括 request、session、global session：
  * request：每次 http 请求将会有各自的 bean 实例。
  * session：在一个 http session 中，一个 bean 定义对应一个 bean 实例。
  * global session：在一个全局的 http session 中，一个 bean 定义对应一个 bean 实例。


从缓存中获取的 bean 一定是 singleton bean，这也是 Spring 为何只解决 singleton bean 的循环依赖。

**创建 bean 实例对象**

如果缓存中没有，也没有 parentBeanFactory ，则会调用 `createBean()` 创建 bean 实例，该方法主要是在处理不同 scope 的 bean 的时候进行调用。该抽象方法的默认实现是在类 AbstractAutowireCapableBeanFactory 中实现，该方法其实只是做一些检查和验证工作，真正的初始化工作是由 doCreateBean() 实现。

`doCreateBean()` 是创建 bean 实例的核心方法，方法调用 `populateBean()` 进行属性填充，调用 `initializeBean()` 初始化 bean

**属性填充**

属性填充其实就是将 BeanDefinition 的属性值赋值给 BeanWrapper 实例对象的过程。在填充的过程需要根据注入的类型不同来区分是根据类型注入 `autowireByType()` 还是名字注入 `autowireByName()`，当然在这个过程还会涉及循环依赖的问题的。

**初始化 bean**

初始化 bean 为 createBean() 的最后一个过程，该过程主要做三件事情：

* 激活 Aware 方法
* 后置处理器的应用
* 激活自定义的 init 方法

**从 bean 实例中获取对象**

无论是从单例缓存中获取的 bean 实例 还是通过 `createBean()` 创建的 bean 实例，最终都会调用 `getObjectForBeanInstance()` ，该方法是根据传入的 bean 实例获取对象，真正的实现逻辑是委托给 `getObjectFromFactoryBean()` 实现。

## Mybatis

### 解释一下MyBatis中命名空间（namespace）的作用。

在mybatis中，映射文件中的namespace是用于绑定Dao接口的， 当你的namespace绑定接口后，你可以不用写接口实现类，mybatis会通过该绑定自动帮你找到对应要执行的SQL语句。Mapper的XML文件的命名空间对应的是这个接口的全限定名，而方法就是那条SQL语句的id，这样mybatis就可以根据全路径名和方法名，将其和代理对象绑定起来，通过动态代理技术，让这个接口运行起来。

### MyBatis中的动态SQL是什么意思？


传统jdbc方法中，在写组合的多表复杂sql语句时，需要去拼接sql语句，稍不注意少写一个空格或“”，就会导致报错。 Mybatis动态sql的功能，就拥有有效的解决了这个问题，Mybatis动态sql语言可以被用在任意的sql语句映射中， 它可以帮助我们方便的在SQL语句中实现某些逻辑。

MyBatis中用于实现动态SQL的元素主要有：if、choose（when，otherwise）、trim、where、set、foreach

### Mybatis中Mapper接口编程原理

[Mybatis：Mapper接口编程原理分析（一）](https://www.jianshu.com/p/7529fe7508cf)

[Mybatis：Mapper接口编程原理分析（二）](https://www.jianshu.com/p/0cbbae26d23d)

[Mybatis：Mapper接口编程原理分析（三）](https://www.jianshu.com/p/466b97162917)

[Mybatis：Mapper接口编程原理分析（四）](https://www.jianshu.com/p/69dbb4ba21b8)

[Mybatis：Mapper接口编程原理分析（五）](https://www.jianshu.com/p/c4d60a4852a4)

1. 解析配置文件，获取mapper接口，将Mapper接口注册到MapperRegistry中，MapperRegistry 它是用来注册Mapper接口和获取Mapper接口代理类实例的工具类，完成这两个工作是通过 getMapper方法和addMapper方法。
2. 注册Mapper接口，获取生成代理类实例的工具类。Mapper 接口只会被加载一次，然后缓存在 HashMap 中，其中 key 是 mapper 接口类对象，value 是 mapper 接口对应的 代理工厂。需注意的是，每个 mapper 接口对应一个代理工厂。
3. 获取Mapper接口的代理对象。通过MapperRegistry类中的mapper的hashMap中获取mapper代理工厂

## SpringMVC
### Spring MVC注解的优点
1. 它可以充分利用 Java 的反射机制获取类结构信息，这些信息可以有效减少配置的工作。
2. 注释和 Java 代码位于一个文件中， 有助于增强程序的内聚性。
3. 编译期校验，错误的注解在编译期间就会报错。注解在java代码中，从而避免了额外的文件维护工作。

### springmvc和spring-boot区别？
### SpringMVC的运行机制，运行机制的每一部分的相关知识？

![](https://ws1.sinaimg.cn/large/d4556b75ly1g41oivbz5rj20s90ga3zj.jpg)

1. 步骤①, DispatcherServlet作为前端控制器, 统一的请求接收点, 控制全局的请求流程. 接收到用户请求, 自己不做处理, 而是将请求委托给其他的处理器进行处理.
2. 步骤②③, DispatcherServlet通过HandlerMapping(处理映射器), 将请求映射为一个HandlerExecutionChain对象, 其中包括了页面控制器和对其配置的拦截器.
3. 步骤④, DispatcherServlet通过获得的Handler(处理器, 页面控制器, Controller), 查找一个合适的HandlerAdapter(处理器适配器), 通过这个HandlerAdapter调用Handler实际处理请求的方法.
4. 步骤⑤, 提取请求中的模型数据, 调用Handler实际处理请求的方法. 在调用方法时, 填充参数过程中, spring会根据配置做一些工作, 如: 数据转换, 数据格式化, 数据验证等.
5. 步骤⑥⑦, Handler执行完成后, 将返回一个ModelAndView对象给DispatherServlet. ModelAndView对象中包含逻辑视图名或逻辑视图名和模型.
6. 步骤⑧, 根据ModelAndView对象选择一个合适的ViewResolver(视图解析器).
7. 步骤⑨, ViewResolver将ModelAndView中的逻辑视图名解释成View对象. ViewResolver也是接口, 同样采用了策略模式, 这样就很容易切换其他的视图类型.
8. 步骤⑩⑪, 渲染视图时, 将Model数据传入视图中, 这里的Model数据是一个Map, 容易与各种视图类型相结合.
9. 步骤⑫, 最后, 由DispatcherServlet将最终的响应结果返回给用户.

### 谈谈Spring MVC的工作原理是怎样的？


1. 用户发送请求至前端控制器DispatcherServlet。
2. DispatcherServlet收到请求调用HandlerMapping处理器映射器。
3. 处理器映射器找到具体的处理器(可以根据xml配置、注解进行查找)，生成处理器对象及处理器拦截器(如果有则生成)一并返回给DispatcherServlet。
4. DispatcherServlet调用HandlerAdapter处理器适配器。
5. HandlerAdapter经过适配调用具体的处理器(Controller，也叫后端控制器)。
6. Controller执行完成返回ModelAndView。
7. HandlerAdapter将controller执行结果ModelAndView返回给DispatcherServlet。
8. DispatcherServlet将ModelAndView传给ViewReslover视图解析器。
9. ViewReslover解析后返回具体View。
10. DispatcherServlet根据View进行渲染视图（即将模型数据填充至视图中）。
11. DispatcherServlet响应用户。





