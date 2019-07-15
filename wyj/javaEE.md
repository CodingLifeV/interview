<!-- TOC -->

- [Spring](#spring)
    - [IOC 和 AOP?](#ioc-和-aop)
    - [bean 的生命周期](#bean-的生命周期)
    - [Spring 注解 autowired 和 resource 区别](#spring-注解-autowired-和-resource-区别)
    - [@Controller 和@RestController 的区别？](#controller-和restcontroller-的区别)
    - [依赖注入的方式有几种，哪几种？Bean 的装配方式有几种，哪几种？](#依赖注入的方式有几种哪几种bean-的装配方式有几种哪几种)
    - [springIOC 原理？自己实现 IOC 要怎么做，哪些步骤？](#springioc-原理自己实现-ioc-要怎么做哪些步骤)
    - [Spring 中 BeanFactory 和 ApplicationContext 的区别？BeanFactory 和 FactoryBean 的区别？](#spring-中-beanfactory-和-applicationcontext-的区别beanfactory-和-factorybean-的区别)
    - [请问 Spring 中 Bean 的作用域有哪些？](#请问-spring-中-bean-的作用域有哪些)
    - [谈谈 Spring 中自动装配的方式有哪些？](#谈谈-spring-中自动装配的方式有哪些)
    - [aop 的应用场景？日志记录和异常处理如何使用？](#aop-的应用场景日志记录和异常处理如何使用)
    - [AOP 的原理是什么？](#aop-的原理是什么)
    - [你如何理解 AOP 中的连接点（Joinpoint）、切点（Pointcut）、增强（Advice）、引介（Introduction）、织入（Weaving）、切面（Aspect）这些概念？](#你如何理解-aop-中的连接点joinpoint切点pointcut增强advice引介introduction织入weaving切面aspect这些概念)
    - [Spring 支持的事务管理类型有哪些？你在项目中使用哪种方式？](#spring-支持的事务管理类型有哪些你在项目中使用哪种方式)
    - [介绍一下 spring？](#介绍一下-spring)
    - [Struts 拦截器和 Spring AOP 区别？](#struts-拦截器和-spring-aop-区别)
    - [spring 框架的优点？缺点？](#spring-框架的优点缺点)
    - [选择使用 Spring 框架的原因（Spring 框架为企业级开发带来的好处有哪些）？](#选择使用-spring-框架的原因spring-框架为企业级开发带来的好处有哪些)
    - [持久层设计要考虑的问题有哪些？你用过的持久层框架有哪些？](#持久层设计要考虑的问题有哪些你用过的持久层框架有哪些)
    - [Spring 声明式事务](#spring-声明式事务)
    - [spring事务写在哪一部分，为什么不写在dao,controller层](#spring事务写在哪一部分为什么不写在daocontroller层)
    - [Spring 事务传播机制](#spring-事务传播机制)
    - [Spring 中如何让 A 和 B 两个 bean 按顺序加载 Spring 中如何让 A 和 B 两个 bean 按顺序加载](#spring-中如何让-a-和-b-两个-bean-按顺序加载-spring-中如何让-a-和-b-两个-bean-按顺序加载)
    - [Spring 源码总结](#spring-源码总结)
    - [Spring 中的设计模式](#spring-中的设计模式)
- [Mybatis](#mybatis)
    - [解释一下 MyBatis 中命名空间（namespace）的作用。](#解释一下-mybatis-中命名空间namespace的作用)
    - [MyBatis 中的动态 SQL 是什么意思？](#mybatis-中的动态-sql-是什么意思)
    - [Mybatis 中 Mapper 接口编程原理](#mybatis-中-mapper-接口编程原理)
- [SpringMVC](#springmvc)
    - [Spring MVC 注解的优点](#spring-mvc-注解的优点)
    - [springmvc 和 spring-boot 区别？](#springmvc-和-spring-boot-区别)
    - [SpringMVC 的运行机制，运行机制的每一部分的相关知识？](#springmvc-的运行机制运行机制的每一部分的相关知识)
    - [谈谈 Spring MVC 的工作原理是怎样的？](#谈谈-spring-mvc-的工作原理是怎样的)

<!-- /TOC -->

# Spring

[博客大致写了 Spring 的主要代码流程](https://www.jianshu.com/p/5c781f264467?from=groupmessage)

[博主自己动手写了一个 Spring IOC](https://www.cnblogs.com/jeysin/p/10091269.html)

## IOC 和 AOP?

IOC：控制反转，控制权的转移，应用程序本身不负责依赖对象的创建和维护，而是由外部容器负责创建和维护。 许多应用都是通过彼此间的相互合作来实现业务逻辑的，如类 A 要调用类 B 的方法，以前我们都是在类 A 中，通过自身 new 一个类 B，然后在调用类 B 的方法，现在我们把 new 类 B 的事情交给 spring 来做，在我们调用的时候，容器会为我们实例化。

AOP： 面向切面编程，它利用一种称为“横切”的技术，剖解开封装的对象内部，并将那些影响了多个类的公共行为封装到一个可重用模块，并将其名为“Aspect”，即切面。所谓“切面”，简单地说，就是将那些与业务无关，却为业务模块所共同调用的逻辑或责任封装起来，便于减少系统的重复代码，降低模块间的耦合度，并有利于未来的可操作性和可维护性。主要的功能是：日志记录，性能统计，安全控制，事务处理，异常处理。

## bean 的生命周期

[spring 生命周期最详解](https://blog.csdn.net/qq_23473123/article/details/76610052)

[SpringBean 生命周期详解](https://blog.csdn.net/lisongjia123/article/details/52091013)

[Spring 中 Bean 的生命周期](https://cloud.tencent.com/developer/article/1362778)

所谓 Bean 的生命周期，就是一个 Bean 从创建到销毁，所经历的各种方法调用。大致包含下面几个方法（不是全部）:

- Bean 的实例化，调用了构造方法。
- 使用 setter 方法填充属性。
- 一旦依赖注入完成，调用 Spring 感知接口 BeanNameAware.setBeanName()。
- BeanFactoryAware.setBeanFactory() 方法
- ApplicationContextAware 的 setApplicationContext() 方法
- BeanPostProcessor.postProcessBeforeInitialization 方法。
- @PostConstruct 标注的方法。
- InitializingBean.afterPropertiesSet() 方法
- 自定义的 init-method 方法
- BeanPostProcessor.postProcessAfterInitialization()

此时 Bean 可以用了。当容器关闭的时候，则会调用：

- @PreDestroy 标注的方法
- DisposableBean.destroy()
- 自定义的 destroy-method
- 对象自定义的 finalize 方法

BeanPostProcessor 有一个不同于其他 3 个的点，实现 BeanPostProcessor 接口后，容器中的对象，在初始化前和初始化后，都会调用 postProcessBeforeInitialization 方法和 postProcessAfterInitialization 方法。即使这个对象并未实现 BeanPostProcessor 接口。而其他如@PostConstruct 注解等的实现方式中，仅作用在当前的 bean 上。因此 BeanPostProcessor 是全局性的，对容器中所有的对象都有效。

## Spring 注解 autowired 和 resource 区别

[@Autowired 与@Resource 的区别（详细）](https://blog.csdn.net/weixin_40423597/article/details/80643990)

**共同点：**

两者都可以写在字段和 setter 方法上。两者如果都写在字段上，那么就不需要再写 setter 方法。

**不同点：**

1. @Autowired 按 byType 自动注入，默认情况下它要求依赖对象必须存在，如果允许 null 值，可以设置它的 required 属性为 false。如果我们想使用按照名称（byName）来装配，可以结合@Qualifier 注解一起使用
2. @Resource 默认按 byName 自动注入，@Resource 有两个属性是比较重要的，分是 name 和 type，Spring 将@Resource 注解的 name 属性解析为 bean 的名字，而 type 属性则解析为 bean 的类型。所以如果使用 name 属性，则使用 byName 的自动注入策略，而使用 type 属性时则使用 byType 自动注入策略。如果既不指定 name 也不指定 type 属性，这时将通过反射机制使用 byName 自动注入策略。 如果指定了 name，则从上下文中查找名称（id）匹配的 bean 进行装配，找不到则抛出异常；如果指定了 type，则从上下文中找到类型匹配的唯一 bean 进行装配，找不到或者找到多个，都会抛出异常

## @Controller 和@RestController 的区别？

[@Controller 和@RestController 源码解析](https://www.cnblogs.com/sgh1023/p/10165470.html)

[@Controller 和@RestController 的区别](https://www.cnblogs.com/clwydjgs/p/9255046.html)

@ResponseBody 注解告知 Spring，要将返回的对象作为资源发送给客户端。这个过程跳过正常的模型/视图流程中视图解析的过程，而是使用 Spring 自带的各种 Http 消息转换器将控制器产生的数据转换为客户端需要的表述形式。 当处理请求时候，@ResponseBody 和@RequestBody 是启用消息转换的一种简介和强大方式。但是，如果控制器里面的每个方法都需要信息转换功能的话，那么这些注解就会带有一定程度的重复性。所以，Spring 4.0 引入了@RestController 注解，如果在控制器类上面使用@RestController 注解，我们不必再为每个方法添加@ResponseBody 注解，因为 Spring 会为该控制器下面的所有方法应用消息转换功能。

**总结：**

1. @RestController 相当于 @ResponseBody ＋ @Controller 一起作用。
2. 使用 @Controller 注解，在对应的方法上，视图解析器可以解析 return 的 jsp, html 页面，并且跳转到相应页面，若返回 json 等内容到页面，则需要加@ResponseBody 注解；
3. 相当于@Controller + @ResponseBody 两个注解的结合，返回 json 数据不需要在方法前面加@ResponseBody 注解了，但使用@RestController 这个注解，就不能返回 jsp,html 页面，视图解析器无法解析 jsp,html 页面

## 依赖注入的方式有几种，哪几种？Bean 的装配方式有几种，哪几种？

依赖注入方式：

1. 构造器注入；
2. setter 注入。首先把构造方法声明为无参数的，然后使用 setter 注入为其设置对应的值；
3. 接口注入。例如外部的数据库连接资源，通过 JNDI 获取的数据源，通过 Spring 的接口注入实现

装配方式：

1. 通过 XML 方式装配 Bean
2. 通过注解装配 Bean。Spring 中提供了二种方式来让 Spring IOC 容器发现 Bean
   1. 组件扫描，@Component
   2. 自动装配，@Autowired

## springIOC 原理？自己实现 IOC 要怎么做，哪些步骤？

[自己动手实现一个轻量级 Spring IOC 容器](https://www.cnblogs.com/jeysin/p/10091269.html)

IOC：控制反转，控制权的转移，应用程序本身不负责依赖对象的创建和维护，而是由外部容器负责创建和维护。 许多应用都是通过彼此间的相互合作来实现业务逻辑的，如类 A 要调用类 B 的方法，以前我们都是在类 A 中，通过自身 new 一个类 B，然后在调用类 B 的方法，现在我们把 new 类 B 的事情交给 spring 来做，在我们调用的时候，容器会为我们实例化。

**自己要实现 IOC，可以考虑以下步骤：**

1. 定义 POJO，二个 POJO 相互引用，以测试我们的 IOC 容器在为 bean 注入属性的时候是否能解决这种相互依赖的问题；
2. 写一个配置文件 application.xml，在配置文件中声明这两个 bean，并给它们设置相应的属性。 我们希望我们的 IOC 容器最后能像 Spring 一样从这个 xml 中读取 bean，然后注入属性，然后我们通过 getBean 方法可以从中直接取出 bean 来使用；
3. 实现一个类：BeanDefinition，从配置文件中读取出 bean 的信息后并封装在 BeanDefinition 类中。BeanDefinition 的作用就是对 bean 的一层封装，封装 bean 的名字 beanClassName， bean 的属性值 propertyMap，这个 beanClassName 是我们从配置文件中读取到的， propertyMap 里面存的是每一个具体的 bean 的所有属性值；
4. 写一个读取配置文件的接口 InputStream 并写一个实现类。用来读取配置文件信息；
5. 定义一个 bean 的引用类 BeanReference，用来解决类之间依赖的问题。 遇到配置文件中的 value 标签，可以直接将 name 和 value 作为一组键值对直接存入 BeanDefinition 中的 propertyMap 就好了， 如果遇到 ref 这种引用， 我们就可以把 name 和 BeanReference 作为一个键值对存入 propertyMap 中；
6. 定义解析配置文件的类. BeanDefinitionReader.java 以及相应的实现 XmlBeanDefinitionReader.java，配置文件解析信息存在一个 beanDifinitionMap 中，里面存的是 name 和 BeanDidinition 的对应关系；
7. 定义一个 BeanFactory 接口以及接口的实现。BeanFactory 用来创建 Bean 并进行依赖注入，Bean 的创建主要是拿到上文 beanDifinitionMap 解析的 bean，之后通过反射机制创建一个相应的 bean，创建 bean 之后，在通过注入属性的方式来解决依赖循环问题；
8. 定义 ApplicationContext 接口以及相应的实现 ClassPathXmlApplicationContext.java。ClassPathXmlApplicationContext 实现一个 refresh 方法，该方法实现了将 XmlBeanDefinitionReader 中读取到的 bean 的定义向 BeanFactory 中转移的过程。

## Spring 中 BeanFactory 和 ApplicationContext 的区别？BeanFactory 和 FactoryBean 的区别？

**BeanFactory 和 ApplicationContext 的区别：**

1. 两者都是通过 xml 配置文件加载 bean,ApplicationContext 和 BeanFacotry 相比,提供了更多的扩展功能，但其主要区别在于后者是延迟加载,如果 Bean 的某一个属性没有注入，BeanFacotry 加载后，直至第一次使用调用 getBean 方法才会抛出异常；而 ApplicationContext 则在初始化自身是检验，这样有利于检查所依赖属性是否注入；所以通常情况下我们选择使用 ApplicationContext
2. BeanFactory 和 ApplicationContext 都支持 BeanPostProcessor、BeanFactoryPostProcessor 的使用，但两者之间的区别是：BeanFactory 需要手动注册，而 ApplicationContext 则是自动注册。

   Applicationcontext 比 beanFactory 加入了一些更好使用的功能。而且 beanFactory 的许多功能需要通过编程实现而 Applicationcontext 可以通过配置实现。比如后处理 bean ， Applicationcontext 直接配置在配置文件即可，而 beanFactory 这要在代码中显示的写出来才可以被容器识别。

3. ApplicationContext 还提供了更完整的框架功能： MessageSource,提供国际化的消息访问；资源访问， 如 URL 和文件；事件传播特性，即支持 aop 特性

**BeanFactory 和 FactoryBean 的区别：**

BeanFactory 是个 Factory，也就是 IOC 容器或对象工厂，FactoryBean 是个 Bean。在 Spring 中，所有的 Bean 都是由 BeanFactory(也就是 IOC 容器)来进行管理的。但对 FactoryBean 而言，这个 Bean 不是简单的 Bean，而是一个能生产或者修饰对象生成的工厂 Bean,它的实现与设计模式中的工厂模式和修饰器模式类似。

一般情况下，Spring 通过反射机制利用<bean>的 class 属性指定实现类实例化 Bean，在某些情况下，实例化 Bean 过程比较复杂，如果按照传统的方式，则需要在<bean>中提供大量的配置信息，例如使用大量的<property>元素标签。配置方式的灵活性是受限的，FactoryBean 的工厂类接口，用户可以通过实现该接口定制实例化 Bean 的逻辑，可以通过逗号分割符的方式一次性的为类的所有属性指定配置值。

FactoryBean 支持泛型，即接口声明改为 FactoryBean<T>的形式。一个 Bean 想要实现 FactoryBean ，必须实现以下三个接口：

1. Object getObject():返回由 FactoryBean 创建的 Bean 的实例
2. boolean isSingleton():确定由 FactoryBean 创建的 Bean 的作用域是 singleton 还是 prototype；
3. getObjectType():返回 FactoryBean 创建的 Bean 的类型。

[BeanFactory、ApplicationContext 以及 FactoryBean](https://www.jianshu.com/p/d8b158fe595d)

[spring 中 BeanFactory 和 FactoryBean 的区别](https://blog.csdn.net/qiesheng/article/details/72875315)

## 请问 Spring 中 Bean 的作用域有哪些？

1. singleton 原型模式，默认值，IOC 容器中仅存在一个 Bean 实例，Bean 都以单例模式存在
2. prototype 原型模式，在每次请求获取 Bean 的时候，都会创建一个新的实例，它在容器初始化的时候不会创建实例，采用的是延迟加载的形式注入 Bean，当你使用的时候，才会进行实例化，每次实例化获取的对象都不是同一个，就像 BeanFactory 的实例化模式实例不唯一
3. request，http 请求模式，在每一次 http 请求时会创建一个实例，该实例仅在当前 http request 有效
4. session 会话，在每一次 http 请求时会创建一个实例，该实例仅在当前 http session 有效
5. globalSession，全局 Session，供不同的 portlet 共享，portlet 好像是类似于 servlet 的 Web 组件

如果不指定 Bean 的作用域，Spring 默认使用 singleton 作用域。Java 在创建 Java 实例时，需要进行内存申请；销毁实例时，需要完成垃圾回收，这些工作都会导致系统开销的增加。因此，prototype 作用域 Bean 的创建、销毁代价比较大。而 singleton 作用域的 Bean 实例一旦创建成功，可以重复使用。因此，除非必要，否则尽量避免将 Bean 被设置成 prototype 作用域。

## 谈谈 Spring 中自动装配的方式有哪些？

1. no：不进行自动装配，手动设置 Bean 的依赖关系；
2. byName：根据 Bean 的名字进行自动装配；
3. byType：根据 Bean 的类型进行自动装配；
4. constructor：使用构造方法完成对象注入，其实也是根据构造方法的参数类型进行对象查找，相当于采用 byType 的方式；
5. autodetect：如果有默认的构造器，则通过 constructor 的方式进行自动装配，否则使用 byType 的方式进行自动装配。

## aop 的应用场景？日志记录和异常处理如何使用？

[Spring AOP 进行统一的异常处理和日志记录](https://segmentfault.com/a/1190000014827136)

1. 事务管理
2. 日志记录
3. 异常处理
4. 缓存

**日志记录和异常处理步骤：**

1. 使用@Aspect 注解标注一个 java 类，Spring 将自动识别该类作为切面 Bean。

```java
@Aspect
public class ExceptionAndLogAspect {
}
```

2. 在 Spring 配置文件中添加這個切面 Bean,并启动@AspectJ 支持。

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

## AOP 的原理是什么？

[Java 动态代理技术](https://app.yinxiang.com/fx/63f8a49e-f979-4743-83f6-1bceb15b242b)

动态代理，在动态代理中使用了拦截器链。

动态代理实现主要是实现 InvocationHandler 接口，并且将目标对象注入到代理对象中，利用反射机制来执行目标对象的方法。目标对象的方法执行主要是通过调用 InvocationHandler 类的 method.invoke()方法，在 invoke()方法前后加入拦截器链来实现 aop 的横切技术。

## 你如何理解 AOP 中的连接点（Joinpoint）、切点（Pointcut）、增强（Advice）、引介（Introduction）、织入（Weaving）、切面（Aspect）这些概念？

1. 连接点（Joinpoint）：是程序执行中的一个精确执行点，例如类中的一个方法。它是一个抽象的概念，在实现 AOP 时，并不需要去定义一个 join point；

2. 切点（Pointcut）：本质上是一个捕获连接点的结构。在 AOP 中，可以定义一个 point cut，来捕获相关方法的调用；

3. 增强（Advice）： 增强是织入到目标类连接点上的一段程序代码。 Spring 提供的增强接口都是带方位名的，如：BeforeAdvice、AfterReturningAdvice、ThrowsAdvice 等；

4. 引介（Introduction）：是指在不更改源代码的情况，给一个现有类增加属性、方法，以及让现有类实现其它接口或指定其它父类等，从而改变类的静态结构；
5. 织入（Weaving）：织入是将增强添加到目标类具体连接点上的过程，AOP 有三种织入方式：

   1. 编译期织入：需要特殊的 Java 编译期（例如 AspectJ 的 ajc）；
   2. 装载期织入：要求使用特殊的类加载器，在装载类的时候对类进行增强；
   3. 运行时织入：在运行时为目标类生成代理实现增强。Spring 采用了动态代理的方式实现了运行时织入，而 AspectJ 采用了编译期织入和装载期织入的方式。

6. 切面（Aspect）： 切面是由切点和增强（引介）组成的，它包括了对横切关注功能的定义，也包括了对连接点的定义。

## Spring 支持的事务管理类型有哪些？你在项目中使用哪种方式？

Spring 支持编程式事务管理和声明式事务管理。选择声明式事务管理， 因为这种方式和应用程序的关联较少，因此更加符合轻量级容器的概念。

## 介绍一下 spring？

1. Spring 的核心是一个轻量级（Lightweight）的容器（Container）.轻量级是指它的创建和销毁不需要消耗太多的资源，意味着可以在程序中经常创建和销毁 session 的对象；重量级意味不能随意的创建和销毁它的实例，会占用很多的资源。
2. Spring 是实现 Ioc（Inversion of Control）容器和非入侵性（No intrusive）的框架
3. Spring 提供 AOP（Aspect-oriented programming）概念的实现方式
4. Spring 提供对持久层（Persistence）、事务（Transaction）的支持
5. Spring 提供 MVC Web 框架的是实现，并对一些常用的企业服务 api 提供一致的模型封装
   6.Spring 提供了对现存的各种框架（Structs、JSF、Hibernate、Ibatis、Webwork 等）相整合的方案

## Struts 拦截器和 Spring AOP 区别？

## spring 框架的优点？缺点？

**优点：**

1. 轻量：基础版本只有 2MB
2. 解耦方便：通过控制反转，实现松散耦合，对象们给出他们的依赖，而不是通过创建或查找对象的依赖
3. 支持 AOP：通过面向切面编程，实现业务逻辑和系统服务分开，方便的实现对程序进行权限拦截、运行监控等功能
4. 支持声明式事务：spring 提供事务管理接口，实现本地事务和全局事务的管理
5. 异常处理：提供异常处理接口，把 hibernate 或者 jdbc 的异常转为一致的 unchecked 异常
6. 易于集成其他优秀框架，Spring 内部提供了对各种优秀框架的支持

**缺点：**

1. jsp 中要写很多代码、控制器过于灵活，缺少一个公用控制器；
2. Spring 不支持分布式，这也是 EJB 仍然在用的原因之一。

## 选择使用 Spring 框架的原因（Spring 框架为企业级开发带来的好处有哪些）？

从（1）IoC 容器（2） AOP（3） MVC（4）事务管理四方面将

## 持久层设计要考虑的问题有哪些？你用过的持久层框架有哪些？

所谓”持久”就是将数据保存到可掉电式存储设备中以便今后使用，简单的说，就是将内存中的数据保存到关系型数据库、文件系统、消息队列等提供持久化支持的设备中。持久层就是系统中专注于实现数据持久化的相对独立的层面。持久层设计的目标包括：

1. 数据存储逻辑的分离，提供抽象化的数据访问接口。
2. 数据访问底层实现的分离，可以在不修改代码的情况下切换底层实现。
3. 资源管理和调度的分离，在数据访问层实现统一的资源调度（如缓存机制）。
4. 数据抽象，提供更面向对象的数据操作。

持久层框架有：Hibernate、MyBatis

## Spring 声明式事务

1. 声明式事务允许自定义事务接口——TransactionDefinition,它可以由 XML 或者注解@Transactional 配置,XML 的形式较少用；
2. 声明式事务需要配置注解驱动；
3. Transactional 二个关键配置项 isolation（隔离级别）和 propagation（传播行为）。

**声明式事务流程：**

1. Spring 通过事务管理器创建事务，并设置事务属性；
2. 执行开发者的代码逻辑；
3. 产生异常且满足事务回滚配置条件，事务回滚，否则事务提交；
4. 事务资源释放。

## spring事务写在哪一部分，为什么不写在dao,controller层

一般写在 service 层。

原因：

结合事务的特点，如果我们的事务注解 @Transactional 加在 dao 层，那么只要与数据库做增删改，就要提交一次事务，如此做事务的特性就发挥不出来，尤其是事务的一致性，当出现并发问题是，用户从数据库查到的数据都会有所偏差。

一般的时候，我们的 service 层可以调用多个 dao 层，我们只需要在 service层加一个事务注解 @Transactional，这样我们就可以一个事务处理多个请求，事务的特性也会充分的发挥出来。



## Spring 事务传播机制

[Spring 的事务传播机制实例](https://www.jianshu.com/p/25c8e5a35ece)

1. Propagation.REQUIRED：如果当前没有事务，就新建一个事务，如果已经存在一个事务中，加入到这个事务中，这是 Spring 默认的传播行为
2. Propagation.SUPPORTS：支持当前事务，如果当前没有事务，就以非事务方式执行
3. Propagation.MANDATORY：使用当前的事务，如果当前没有事务，就抛出异常
4. Propagation.REQUIRES_NEW：无论是否存在当前事务，方法都会在新的事务中运行
5. Propagation.NOT_SUPPORTED： 以非事务方式执行操作，如果当前存在事务，就把当前事务挂起
6. Propagation.NEVER： 以非事务方式执行，如果当前存在事务，则抛出异常
7. Propagation.NESTED：嵌套事务，如果当前存在事务，则在嵌套事务内执行。也就是调用方法如果抛出异常只回滚自己内部执行的 SQL，而不回滚主方法的 SQL

## Spring 中如何让 A 和 B 两个 bean 按顺序加载 Spring 中如何让 A 和 B 两个 bean 按顺序加载

1. 依赖关系

2. 使用 depends-on 属性，depends-on 用来指定 Bean 初始化及销毁时的顺序。

   适用的场景：用来确定 bean 定义中依赖关系不明确或者没有直接依赖关系时，指定 bean 在初始化或销毁时的明确顺序。一个 bean 可以依赖多个 bean，可以通过逗号(",")或者分号(";")来定义多个依赖对象：

```
<bean id=a Class="com.twovv.A" depends-on="b,c,d" />
<bean id=b Class="com.twovv.B" />
<bean id=c Class="com.twovv.C" />
<bean id=d Class="com.twovv.D" />
```

## Spring 源码总结

[死磕 Spring（此人的博客写的超级棒，有很多值得参考的内容）](http://cmsblogs.com/?cat=206)

**1. Spring 统一资源加载策略**

- 统一资源：Resource

  Spring 框架所有资源的抽象和访问接口,AbstractResource 为其接口的默认实现
  ![](https://gitee.com/chenssy/blog-home/raw/master/image/201811/spring-201805091003.jpg)

- 统一资源定位：ResourceLoader

  Spring 将资源的定义和资源的加载区分开了，Resource 定义了统一的资源，ResourceLoader 为 Spring 资源加载的统一抽象，具体的资源加载则由相应的实现类来完成

  ResourceLoader 接口提供两个方法：`getResource()`和`getClassLoader()`。

  - `getResource()`：根据所提供资源的路径 location 返回 Resource 实例
  - `getClassLoader()`： 返回 ClassLoader 实例

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

- **Resource 资源定位**，通过统一资源加载策略
- **BeanDefinition 的载入和解析**。BeanDefinitionReader 读取、解析 Resource 资源，也就是将用户定义的 Bean 表示成 IOC 容器的内部数据结构：BeanDefinition。在 IOC 容器内部维护着一个 BeanDefinition Map 的数据结构，在配置文件中每一个 <bean> 都对应着一个 BeanDefinition 对象。
- **BeanDefinition 注册**，向 IOC 容器注册在第二步解析好的 BeanDefinition，这个过程是通过 BeanDefinitionRegistry 接口来实现的。在 IOC 容器内部其实是将第二个过程解析得到的 BeanDefinition 注入到一个 HashMap 容器中，IOC 容器就是通过这个 HashMap 来维护这些 BeanDefinition 的。这个过程并没有完成依赖注入。

整个代码大致流程将 Resource 资源封装成 EncodedResource，完成后从 encodedResource 获取封装的 Resource 资源并从 Resource 中获取相应的 InputStream， 之后获取 Document 实例， 根据获取的 Document 实例注册 Bean 信息

**3. 获取验证模型**

- DTD：文档类型定义，为 XML 文件的验证机制
- XSD：对 DTD 进行扩展

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

迭代 root 元素的所有子节点，对其进行判断，若节点为默认命名空间，则 ID 调用 `parseDefaultElement()` 开启默认标签的解析注册过程，否则调用 `parseCustomElement()` 开启自定义标签的解析注册过程。

最终解析动作落地在两个方法处：`parseDefaultElement(ele, delegate)` 和 `delegate.parseCustomElement(root)`。我们知道在 Spring 有两种 Bean 声明方式：

- 配置文件式声明：`<bean id="studentService" class="org.springframework.core.StudentService" />`
- 自定义注解方式：`<tx:annotation-driven>`

两种方式采用不同的解析方法，如果根节点或者子节点采用默认命名空间的话，则调用 `parseDefaultElement()` 进行解析，否则调用 `delegate.parseCustomElement()` 方法进行自定义解析。

四大标签：import、alias、bean、beans

**5. BeanDefinition 注册**

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

Spring 中根据 scope 可以将 bean 分为以下几类：singleton、prototype 和 其他（request、session 和 global session）。

从缓存中获取的 bean 一定是 singleton bean，这也是 Spring 为何只解决 singleton bean 的循环依赖。

在 `doGetBean()` 中，首先会根据 beanName 从单例 bean 缓存中获取，如果不为空则直接返回。调用 `getSingleton()` 方法从单例缓存中获取，如下：

```java
protected Object getSingleton(String beanName, boolean allowEarlyReference) {
        Object singletonObject = this.singletonObjects.get(beanName);
        if (singletonObject == null && isSingletonCurrentlyInCreation(beanName)) {
            synchronized (this.singletonObjects) {
                singletonObject = this.earlySingletonObjects.get(beanName);
                if (singletonObject == null && allowEarlyReference) {
                    ObjectFactory<?> singletonFactory = this.singletonFactories.get(beanName);
                    if (singletonFactory != null) {
                        singletonObject = singletonFactory.getObject();
                        this.earlySingletonObjects.put(beanName, singletonObject);
                        this.singletonFactories.remove(beanName);
                    }
                }
            }
        }
        return singletonObject;
    }
```

`getSingleton()` 整个过程如下：

1. 从一级缓存 singletonObjects 获取，如果没有且当前指定的 beanName 正在创建。bean 处于创建中也就是说 bean 在初始化但是没有完成初始化，此时会提前曝光 bean

2. 从二级缓存中 earlySingletonObjects 获取，如果还是没有获取到且允许运行 singletonFactories 通过 getObject() 获取对象（字段 allowEarlyReference 的字面意思），则从三级缓存获取

3. 从三级缓存获取，如果获取到则，通过其 getObject() 获取对象，并将其加入到二级缓存 earlySingletonObjects 中 从三级缓存 singletonFactories 删除，这样就从三级缓存升级到二级缓存了。

**创建 bean 实例对象**

如果缓存中没有，也没有 parentBeanFactory ，则会调用 `createBean()` 创建 bean 实例，该方法主要是在处理不同 scope 的 bean 的时候进行调用。该抽象方法的默认实现是在类 AbstractAutowireCapableBeanFactory 中实现，该方法其实只是做一些检查和验证工作，真正的初始化工作是由 doCreateBean() 实现。

`doCreateBean()` 是创建 bean 实例的核心方法，主要用于完成 bean 的创建和初始化工作，我们可以将其分为四个过程：

- createBeanInstance() 实例化 bean
- populateBean() 属性填充
- 循环依赖的处理
- initializeBean() 初始化 bean

**属性填充**

属性填充其实就是将 BeanDefinition 的属性值赋值给 BeanWrapper 实例对象的过程。根据注入类型的不同来判断是根据名称来自动注入`autowireByName()`还是根据类型来自动注入`autowireByType()`，统一存入到 PropertyValues 中，PropertyValues 用于描述 bean 的属性，最后将所有 PropertyValues 中的属性填充到 BeanWrapper 中。

`autowireByName()` 和 `autowireByType()` 主要过程和根据名称自动注入差不多都是找到需要依赖注入的属性，然后通过迭代的方式寻找所匹配的 bean，最后调用 registerDependentBean() 注册依赖。

**循环依赖处理**

![image](https://gitee.com/chenssy/blog-home/raw/master/image/201811/201808131001.png)

> 首先 A 完成初始化第一步并将自己提前曝光出来（通过 ObjectFactory 将自己提前曝光），在初始化的时候，发现自己依赖对象 B，此时就会去尝试 get(B)，这个时候发现 B 还没有被创建出来，然后 B 就走创建流程，在 B 初始化的时候，同样发现自己依赖 C，C 也没有被创建出来，这个时候 C 又开始初始化进程，但是在初始化的过程中发现自己依赖 A，于是尝试 get(A)，这个时候由于 A 已经添加至缓存中（一般都是添加至三级缓存 singletonFactories ），通过 ObjectFactory 提前曝光，所以可以通过 ObjectFactory.getObject() 拿到 A 对象，C 拿到 A 对象后顺利完成初始化，然后将自己添加到一级缓存中，回到 B ，B 也可以拿到 C 对象，完成初始化，A 可以顺利拿到 B 完成初始化。到这里整个链路就已经完成了初始化过程了。

Spring 循环依赖的场景有两种：

1. 构造器的循环依赖
2. field 属性的循环依赖

对于构造器的循环依赖，Spring 是无法解决的，只能抛出 BeanCurrentlyInCreationException 异常表示循环依赖。

Spring 解决 singleton bean 的关键因素为三级缓存，第一级为 singletonObjects，第二级为 earlySingletonObjects，第三级为 singletonFactories。

- singletonObjects ：单例对象的 cache
- earlySingletonObjects ：提前暴光的单例对象的 Cache
- singletonFactories ： 单例对象工厂的 cache

三级缓存 singletonFactories 是解决 Spring Bean 循环依赖的诀窍所在，
这段代码发生在 createBeanInstance() 方法之后，也就是说这个 bean 其实已经被创建出来了，但是它还不是很完美（没有进行属性填充和初始化），但是对于其他依赖它的对象而言已经足够了（可以根据对象引用定位到堆中对象），能够被认出来了。

Spring 关于 singleton bean 循环依赖的大致方案：Spring 在创建 bean 的时候并不是等它完全完成，而是在创建过程中将创建中的 bean 的 ObjectFactory 提前曝光（即加入到 singletonFactories 缓存中），这样一旦下一个 bean 创建的时候需要依赖 bean ，则直接使用 ObjectFactory 的 `getObject()` 获取了。

**初始化 bean**

初始化 bean 为 createBean() 的最后一个过程，该过程主要做三件事情：

- 激活 Aware 方法
- 后置处理器的应用
- 激活自定义的 init 方法

**从 bean 实例中获取对象**

无论是从单例缓存中获取的 bean 实例 还是通过 `createBean()` 创建的 bean 实例，最终都会调用 `getObjectForBeanInstance()` ，该方法是根据传入的 bean 实例获取对象，真正的实现逻辑是委托给 `getObjectFromFactoryBean()` 实现。

## Spring 中的设计模式

[这些 Spring 中的设计模式，你都知道吗？](https://mp.weixin.qq.com/s/Hy-qxNT0nJzcAkanbH93eA)

**简单工厂**

简单工厂模式的实质是由一个工厂类根据传入的参数，动态决定应该创建哪一个产品类。

spring 中的 BeanFactory 就是简单工厂模式的体现，根据传入一个唯一的标识来获得 bean 对象，但是否是在传入参数后创建还是传入参数前创建这个要根据具体情况来定。

**工厂模式**

[Spring 通过工厂方法(Factory Method)来配置 bean](https://blog.csdn.net/nvd11/article/details/51542360?utm_source=copy)

通常由应用程序直接使用 new 创建新的对象，为了将对象的创建和使用相分离，采用工厂模式，即应用程序将对象的创建及初始化职责交给工厂对象。

一般情况下，应用程序有自己的工厂对象来创建 bean。如果将应用程序自己的工厂对象交给 Spring 管理，那么 Spring 管理的就不是普通的 bean，而是工厂 Bean。

在 Spring 的世界中，我们通常会利用 bean config file 或者 annotation 注解方式来配置 bean。在第一种利用 bean config file(spring xml)方式中， 还包括如下三小类：

- 反射模式
- 工厂方法模式
- Factory Bean 模式

反射模式最常见， 我们需要在 bean 配置中指明我们需要的 bean object 的全类名，class 属性就是全类名， Spring 利用 java 反射机制创建这个 bean：

```xml
<bean id="car1" class="com.home.factoryMethod.Car">
  <property name="id" value="1"></property>
  <property name="name" value="Honda"></property>
  <property name="price" value="300000"></property>
</bean>
```

在工厂方法模式中，Spring 不会直接利用反射机制创建 bean 对象， 而是会利用反射机制先找到 Factory 类，然后利用 Factory 再去生成 bean 对象。而 Factory Mothod 方式也分两种，分别是静态工厂方法和实例工厂方法。

1. 静态工厂方法

   静态工厂方式就是指 Factory 类不本身不需要实例化，这个 Factory 类中提供了 1 个静态方法来生成 bean 对象。

   利用静态工厂方法定义的 bean， class 属性不在是 bean 的全类名， 而是静态工厂的全类名， 而且还需要通过参数`factory-method`指定工厂里的 getBean 静态方法名字和参数。

   ```xml
    <bean id="bmwCar" class="com.home.factoryMethod.CarStaticFactory" factory-method="getCar">
        <constructor-arg value="3"></constructor-arg>
    </bean>
   ```

   ```java
    public class CarStaticFactory {
        private static Map<Integer, Car> map = new HashMap<Integer,Car>();

        static{
            map.put(1, new Car(1,"Honda",300000));
            map.put(2, new Car(2,"Audi",440000));
            map.put(3, new Car(3,"BMW",540000));
        }
        // getBean 方法
        public static Car getCar(int id) {
            return map.get(id);
        }
    }

    public class Car {
        private int id;
        private String name;
        private int price;
        //省略get set方法
    }
   ```

2. 实例工厂方法
   实例工厂方式就是里面的 getBean 方法不是静态的，也就是代表要先实例 1 个工厂对象， 才能依靠这个工厂对象去获得 bean 对象。

   实例工厂本身要实例化， 所以我们可以在 xml 中 指定它里面容器的 data。解决了静态工厂方法把数据写在 class 里面而不是配置文件中违反了我们程序猿的常识和 spring 的初衷的缺点。

**单例模式**

保证一个类仅有一个实例，并提供一个访问它的全局访问点。
spring 中的单例模式完成了后半句话，即提供了全局的访问点 BeanFactory。但没有从构造器级别去控制单例，这是因为 spring 管理的是是任意的 java 对象。

核心提示点：Spring 下默认的 bean 均为 singleton，可以通过 `singleton=true|false` 或者 `scope` 来指定。

**适配器模式**

[Spring 中的设计模式-适配器模式](https://blog.csdn.net/adoocoke/article/details/8286902)

在 Spring 的 Aop 中，使用的 Advice（通知）来增强被代理类的功能。Spring 实现这一 AOP 功能的原理就使用代理模式（JDK 动态代理和 CGLib 字节码生成技术代理）对类进行方法级别的切面增强，即生成被代理类的代理类，并在代理类的方法前设置拦截器，通过执行拦截器中的内容增强了代理方法的功能，实现的面向切面编程。

Advice（通知）的类型有 BeforeAdvice、AfterReturningAdvice、Throwsadvice 的。在每个类型 Advice（通知）都有对应的拦截器，MethodBeforeAdviceInterceptor、AfterReturningAdviceInterceptor、ThrowsAdviceInterceptor。

Spring 需要将每个 Advice（通知）都封装成对应的拦截器类型，返回给容器，所以需要使用适配器模式对 Advice 进行转换。

Adaptee：MethodBeforeAdvice 类

```java
public interface MethodBeforeAdvice extends BeforeAdvice {
	void before(Method method, Object[] args, Object target) throws Throwable;
}
```

Target：Adapter 类接口

```java
public interface AdvisorAdapter {
	boolean supportsAdvice(Advice advice);
	MethodInterceptor getInterceptor(Advisor advisor);
}
```

Adapter：MethodBeforeAdviceAdapter 类

```java
class MethodBeforeAdviceAdapter implements AdvisorAdapter, Serializable {
	public boolean supportsAdvice(Advice advice) {
		return (advice instanceof MethodBeforeAdvice);
	}
	public MethodInterceptor getInterceptor(Advisor advisor) {
		MethodBeforeAdvice advice = (MethodBeforeAdvice) advisor.getAdvice();
		return new MethodBeforeAdviceInterceptor(advice);
	}
```

**装饰模式**

[spring 常用模式--------装饰者模式](https://www.jianshu.com/p/8f6ebeee1ae6)

[装饰者模式](https://blog.51cto.com/11545911/2147419)

Spring 的 ApplicationContext 中配置所有的 DataSource。 这些 DataSource 可能是各种不同类型的， 比如不同的数据库： Oracle、 SQL Server、 MySQL 等， 也可能是不同的数据源： 比如 Apache 提 供 的 org.apache.commons.dbcp.BasicDataSource 、 Spring 提 供 的 org.springframework.jndi.JndiObjectFactoryBean 等。 然后 SessionFactory 根据客户的每次请求， 将 DataSource 属性设置成不同的数据源， 以到达切换数据源的目的。

在 spring 的命名体现：Spring 中用到的包装器模式在类名上有两种表现： 一种是类名中含有 Wrapper， 另一种是类名中含有 Decorator。 基本上都是动态地给一个对象添加一些额外的职责。HttpServletRequestWrapper 就是一个典型的装饰者模式：

**代理模式**

为其他对象提供一种代理以控制对这个对象的访问。spring 的 Proxy 模式在 aop 中有体现，比如 JdkDynamicAopProxy 和 Cglib2AopProxy。

**观察者模式**

定义对象间的一种一对多的依赖关系，当一个对象的状态发生改变时，所有依赖于它的对象都得到通知并被自动更新。

spring 中 Observer 模式常用的地方是 listener 的实现。如 ApplicationListener。

**策略（Strategy）**

定义一系列的算法，把它们一个个封装起来，并且使它们可相互替换。本模式使得算法可独立于使用它的客户而变化。

[Spring 资源访问剖析和策略模式应用](https://www.ibm.com/developerworks/cn/java/j-lo-spring-resource/)

1. Spring 为资源访问提供了一个 Resource 接口，该接口是具体资源访问策略的抽象，其实现类包括 UrlResource、ClassPathResource、FileSystemResource 等等。

   ![image](https://www.ibm.com/developerworks/cn/java/j-lo-spring-resource/image004.jpg)

2. spring 中在实例化对象的时候用到 Strategy 模式。

**模板方法**

# Mybatis

## 解释一下 MyBatis 中命名空间（namespace）的作用。

在 mybatis 中，映射文件中的 namespace 是用于绑定 Dao 接口的， 当你的 namespace 绑定接口后，你可以不用写接口实现类，mybatis 会通过该绑定自动帮你找到对应要执行的 SQL 语句。Mapper 的 XML 文件的命名空间对应的是这个接口的全限定名，而方法就是那条 SQL 语句的 id，这样 mybatis 就可以根据全路径名和方法名，将其和代理对象绑定起来，通过动态代理技术，让这个接口运行起来。

## MyBatis 中的动态 SQL 是什么意思？

传统 jdbc 方法中，在写组合的多表复杂 sql 语句时，需要去拼接 sql 语句，稍不注意少写一个空格或“”，就会导致报错。 Mybatis 动态 sql 的功能，就拥有有效的解决了这个问题，Mybatis 动态 sql 语言可以被用在任意的 sql 语句映射中， 它可以帮助我们方便的在 SQL 语句中实现某些逻辑。

MyBatis 中用于实现动态 SQL 的元素主要有：if、choose（when，otherwise）、trim、where、set、foreach

## Mybatis 中 Mapper 接口编程原理

[Mybatis：Mapper 接口编程原理分析（一）](https://www.jianshu.com/p/7529fe7508cf)

[Mybatis：Mapper 接口编程原理分析（二）](https://www.jianshu.com/p/0cbbae26d23d)

[Mybatis：Mapper 接口编程原理分析（三）](https://www.jianshu.com/p/466b97162917)

[Mybatis：Mapper 接口编程原理分析（四）](https://www.jianshu.com/p/69dbb4ba21b8)

[Mybatis：Mapper 接口编程原理分析（五）](https://www.jianshu.com/p/c4d60a4852a4)

1. 解析配置文件，获取 mapper 接口，将 Mapper 接口注册到 MapperRegistry 中，MapperRegistry 它是用来注册 Mapper 接口和获取 Mapper 接口代理类实例的工具类，完成这两个工作是通过 getMapper 方法和 addMapper 方法。
2. 注册 Mapper 接口，获取生成代理类实例的工具类。Mapper 接口只会被加载一次，然后缓存在 HashMap 中，其中 key 是 mapper 接口类对象，value 是 mapper 接口对应的 代理工厂。需注意的是，每个 mapper 接口对应一个代理工厂。
3. 获取 Mapper 接口的代理对象。通过 MapperRegistry 类中的 mapper 的 hashMap 中获取 mapper 代理工厂

# SpringMVC

## Spring MVC 注解的优点

1. 它可以充分利用 Java 的反射机制获取类结构信息，这些信息可以有效减少配置的工作。
2. 注释和 Java 代码位于一个文件中， 有助于增强程序的内聚性。
3. 编译期校验，错误的注解在编译期间就会报错。注解在 java 代码中，从而避免了额外的文件维护工作。

## springmvc 和 spring-boot 区别？

## SpringMVC 的运行机制，运行机制的每一部分的相关知识？

![](https://ws1.sinaimg.cn/large/d4556b75ly1g41oivbz5rj20s90ga3zj.jpg)

1. 步骤 ①, DispatcherServlet 作为前端控制器, 统一的请求接收点, 控制全局的请求流程. 接收到用户请求, 自己不做处理, 而是将请求委托给其他的处理器进行处理.
2. 步骤 ②③, DispatcherServlet 通过 HandlerMapping(处理映射器), 将请求映射为一个 HandlerExecutionChain 对象, 其中包括了页面控制器和对其配置的拦截器.
3. 步骤 ④, DispatcherServlet 通过获得的 Handler(处理器, 页面控制器, Controller), 查找一个合适的 HandlerAdapter(处理器适配器), 通过这个 HandlerAdapter 调用 Handler 实际处理请求的方法.
4. 步骤 ⑤, 提取请求中的模型数据, 调用 Handler 实际处理请求的方法. 在调用方法时, 填充参数过程中, spring 会根据配置做一些工作, 如: 数据转换, 数据格式化, 数据验证等.
5. 步骤 ⑥⑦, Handler 执行完成后, 将返回一个 ModelAndView 对象给 DispatherServlet. ModelAndView 对象中包含逻辑视图名或逻辑视图名和模型.
6. 步骤 ⑧, 根据 ModelAndView 对象选择一个合适的 ViewResolver(视图解析器).
7. 步骤 ⑨, ViewResolver 将 ModelAndView 中的逻辑视图名解释成 View 对象. ViewResolver 也是接口, 同样采用了策略模式, 这样就很容易切换其他的视图类型.
8. 步骤 ⑩⑪, 渲染视图时, 将 Model 数据传入视图中, 这里的 Model 数据是一个 Map, 容易与各种视图类型相结合.
9. 步骤 ⑫, 最后, 由 DispatcherServlet 将最终的响应结果返回给用户.

## 谈谈 Spring MVC 的工作原理是怎样的？

1. 用户发送请求至前端控制器 DispatcherServlet。
2. DispatcherServlet 收到请求调用 HandlerMapping 处理器映射器。
3. 处理器映射器找到具体的处理器(可以根据 xml 配置、注解进行查找)，生成处理器对象及处理器拦截器(如果有则生成)一并返回给 DispatcherServlet。
4. DispatcherServlet 调用 HandlerAdapter 处理器适配器。
5. HandlerAdapter 经过适配调用具体的处理器(Controller，也叫后端控制器)。
6. Controller 执行完成返回 ModelAndView。
7. HandlerAdapter 将 controller 执行结果 ModelAndView 返回给 DispatcherServlet。
8. DispatcherServlet 将 ModelAndView 传给 ViewReslover 视图解析器。
9. ViewReslover 解析后返回具体 View。
10. DispatcherServlet 根据 View 进行渲染视图（即将模型数据填充至视图中）。
11. DispatcherServlet 响应用户。
