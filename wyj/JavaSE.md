[toc]
<!-- TOC -->

- [javaSE](#javase)
    - [1、Java基础](#1java基础)
        - [1. 为什么重写equals还要重写hashcode](#1-为什么重写equals还要重写hashcode)
        - [2、说一下map的分类和常见的情况](#2说一下map的分类和常见的情况)
        - [3、Object若不重写hashCode()的话，hashCode()如何计算出来的？](#3object若不重写hashcode的话hashcode如何计算出来的)
        - [4、==比较的是什么？](#4比较的是什么)
        - [5、若对一个类不重写，它的equals()方法是如何比较的？](#5若对一个类不重写它的equals方法是如何比较的)
        - [6、java8新特性](#6java8新特性)
        - [7、说说Lamda表达式的优缺点。](#7说说lamda表达式的优缺点)
        - [8、一个十进制的数在内存中是怎么存的？](#8一个十进制的数在内存中是怎么存的)
        - [9、为啥有时会出现4.0-3.6=0.40000001这种现象？](#9为啥有时会出现40-36040000001这种现象)
        - [10、Java支持的数据类型有哪些？什么是自动拆装箱？](#10java支持的数据类型有哪些什么是自动拆装箱)
        - [11、什么是值传递和引用传递？](#11什么是值传递和引用传递)
        - [12、数组(Array)和列表(ArrayList)有什么区别？什么时候应该使用Array而不是ArrayList？](#12数组array和列表arraylist有什么区别什么时候应该使用array而不是arraylist)
        - [13、你了解大O符号(big-Onotation)么？你能给出不同数据结构的例子么？](#13你了解大o符号big-onotation么你能给出不同数据结构的例子么)
        - [14、String是最基本的数据类型吗?](#14string是最基本的数据类型吗)
        - [15、int 和 Integer 有什么区别？](#15int-和-integer-有什么区别)
        - [16、String、StringBuffer、StringBuffer](#16stringstringbufferstringbuffer)
        - [17、我们在web应用开发过程中经常遇到输出某种编码的字符，如iso8859-1等，如何输出一个某种编码的字符串？](#17我们在web应用开发过程中经常遇到输出某种编码的字符如iso8859-1等如何输出一个某种编码的字符串)
        - [18、&和&&的区别？](#18和的区别)
        - [19、在Java中，如何跳出当前的多重嵌套循环？](#19在java中如何跳出当前的多重嵌套循环)
        - [20、你能比较一下Java和JavaSciprt吗？](#20你能比较一下java和javasciprt吗)
        - [21、正则表达式](#21正则表达式)
        - [22、请你说说Java和PHP的区别？](#22请你说说java和php的区别)
    - [2、关键字](#2关键字)
        - [1、介绍一下Syncronized锁，如果用这个关键字修饰一个静态方法，锁住了什么？如果修饰成员方法，锁住了什么？](#1介绍一下syncronized锁如果用这个关键字修饰一个静态方法锁住了什么如果修饰成员方法锁住了什么)
        - [2、介绍一下volatile？](#2介绍一下volatile)
        - [3、锁有了解嘛，说一下Synchronized和lock](#3锁有了解嘛说一下synchronized和lock)
        - [4、讲一讲Java里面的final关键字怎么用的？](#4讲一讲java里面的final关键字怎么用的)
    - [3、面向对象](#3面向对象)
        - [1、wait方法底层原理](#1wait方法底层原理)
        - [2、Java有哪些特性，举个多态的例子](#2java有哪些特性举个多态的例子)
        - [3、String为啥不可变？String能继承吗？](#3string为啥不可变string能继承吗)
        - [4、类和对象的区别](#4类和对象的区别)
        - [5、请列举你所知道的Object类的方法](#5请列举你所知道的object类的方法)
        - [6、重载(Overload)和重写(Override)的区别？相同参数不同返回值能重载吗？Overload的方法是否可以改变返回值的类型](#6重载overload和重写override的区别相同参数不同返回值能重载吗overload的方法是否可以改变返回值的类型)
        - [7、”static”关键字是什么意思？Java中是否可以覆盖(override)一个private或者是static的方法？](#7static关键字是什么意思java中是否可以覆盖override一个private或者是static的方法)
        - [8、静态变量存在哪?](#8静态变量存在哪)
        - [9、讲讲什么是泛型？](#9讲讲什么是泛型)
        - [10、解释extends 和super 泛型限定符-上界不存下界不取](#10解释extends-和super-泛型限定符-上界不存下界不取)
        - [11、是否可以在static环境中访问非static变量？](#11是否可以在static环境中访问非static变量)
        - [12、谈谈如何通过反射创建对象？](#12谈谈如何通过反射创建对象)
        - [13、Java支持多继承么？](#13java支持多继承么)
        - [14、接口和抽象类的区别是什么？](#14接口和抽象类的区别是什么)
        - [15、Comparable和Comparator接口是干什么的？列出它们的区别](#15comparable和comparator接口是干什么的列出它们的区别)
        - [16、面向对象的特征有哪些方面](#16面向对象的特征有哪些方面)
        - [17、final, finally, finalize的区别](#17final-finally-finalize的区别)
        - [18、Static Nested Class（嵌套类） 和 Inner Class（内部类）的不同](#18static-nested-class嵌套类-和-inner-class内部类的不同)
        - [19、当一个对象被当作参数传递到一个方法后，此方法可改变这个对象的属性，并可返回变化后的结果，那么这里到底是值传递还是引用传递?](#19当一个对象被当作参数传递到一个方法后此方法可改变这个对象的属性并可返回变化后的结果那么这里到底是值传递还是引用传递)
        - [20、Java的接口和C++的虚类的相同和不同处。](#20java的接口和c的虚类的相同和不同处)
        - [21、JAVA语言如何进行异常处理，关键字：throws,throw,try,catch,finally分别代表什么意义？在try块中可以抛出异常吗？](#21java语言如何进行异常处理关键字throwsthrowtrycatchfinally分别代表什么意义在try块中可以抛出异常吗)
        - [22、内部类可以引用他包含类的成员吗？有没有什么限制？](#22内部类可以引用他包含类的成员吗有没有什么限制)
        - [23、两个对象值相同(x.equals(y) == true)，但却可有不同的hash code说法是否正确？](#23两个对象值相同xequalsy--true但却可有不同的hash-code说法是否正确)
        - [24、如何通过反射获取和设置对象私有字段的值？](#24如何通过反射获取和设置对象私有字段的值)
        - [25、谈一下面向对象的"六原则一法则"](#25谈一下面向对象的六原则一法则)
        - [27、请问Query接口的list方法和iterate方法有什么区别？](#27请问query接口的list方法和iterate方法有什么区别)
        - [28、Java中，什么是构造函数？什么是构造函数重载？什么是复制构造函数？](#28java中什么是构造函数什么是构造函数重载什么是复制构造函数)
    - [4、集合](#4集合)
        - [1、ConcurrentHashMap？](#1concurrenthashmap)
        - [2、hashMap？](#2hashmap)
        - [3、如果hashMap的key是一个自定义的类，怎么办？](#3如果hashmap的key是一个自定义的类怎么办)
        - [4、ArrayList和LinkedList的区别，如果一直在list的尾部添加元素，用哪个效率高？](#4arraylist和linkedlist的区别如果一直在list的尾部添加元素用哪个效率高)
        - [5、TreeMap底层，红黑树原理？](#5treemap底层红黑树原理)
        - [6、ArrayList是否会越界？](#6arraylist是否会越界)
        - [7、Java集合类框架的基本接口有哪些？](#7java集合类框架的基本接口有哪些)
        - [8、为什么集合类没有实现Cloneable和Serializable接口？](#8为什么集合类没有实现cloneable和serializable接口)
        - [9、什么是迭代器？](#9什么是迭代器)
        - [10、Iterator和ListIterator的区别是什么？](#10iterator和listiterator的区别是什么)
        - [11、快速失败(fail-fast)和安全失败(fail-safe)的区别是什么？](#11快速失败fail-fast和安全失败fail-safe的区别是什么)
        - [12、HashMap和Hashtable有什么区别？](#12hashmap和hashtable有什么区别)
        - [13、ArrayList和LinkedList有什么区别？](#13arraylist和linkedlist有什么区别)
        - [14、ArrayList,Vector,LinkedList的存储性能和特性是什么？](#14arraylistvectorlinkedlist的存储性能和特性是什么)
        - [15、Collection 和 Collections的区别](#15collection-和-collections的区别)
        - [16、List、Map、Set三个接口存取元素时，各有什么特点？](#16listmapset三个接口存取元素时各有什么特点)
    - [5、线程](#5线程)
        - [1、多线程中的i++线程安全吗？为什么？](#1多线程中的i线程安全吗为什么)
        - [2、如何线程安全的实现一个计数器？](#2如何线程安全的实现一个计数器)
        - [3、多线程同步的方法](#3多线程同步的方法)
        - [4、介绍一下生产者消费者模式？](#4介绍一下生产者消费者模式)
        - [5、线程，进程，然后线程创建有很大开销，怎么优化？](#5线程进程然后线程创建有很大开销怎么优化)
        - [6、线程池运行流程，参数，策略](#6线程池运行流程参数策略)
        - [7、AQS](#7aqs)
        - [8、创建线程的方法，哪个更好，为什么？](#8创建线程的方法哪个更好为什么)
        - [9、Java中有几种方式启动一个线程？](#9java中有几种方式启动一个线程)
        - [10、什么是线程池？Java中有几种线程池？](#10什么是线程池java中有几种线程池)
        - [11、线程池有什么好处？](#11线程池有什么好处)
        - [12、cyclicbarrier和countdownlatch的区别](#12cyclicbarrier和countdownlatch的区别)
        - [13、如何理解Java多线程回调方法？](#13如何理解java多线程回调方法)
        - [14、概括的解释下线程的几种可用状态以及状态之间的关系](#14概括的解释下线程的几种可用状态以及状态之间的关系)
        - [15、同步方法和同步代码块的区别是什么？](#15同步方法和同步代码块的区别是什么)
        - [16、在监视器(Monitor)内部，是如何做线程同步的？程序应该做哪种级别的同步？](#16在监视器monitor内部是如何做线程同步的程序应该做哪种级别的同步)
        - [17、sleep() 和 wait() 有什么区别？](#17sleep-和-wait-有什么区别)
        - [18、同步和异步有何异同，在什么情况下分别使用他们？举例说明](#18同步和异步有何异同在什么情况下分别使用他们举例说明)
        - [19、设计4个线程，其中两个线程每次对j增加1，另外两个线程对j每次减少1，使用内部类实现线程，对j增减的时候没有考虑顺序问题](#19设计4个线程其中两个线程每次对j增加1另外两个线程对j每次减少1使用内部类实现线程对j增减的时候没有考虑顺序问题)
        - [20、启动一个线程是用run()还是start()?](#20启动一个线程是用run还是start)
        - [21、请说出你所知道的线程同步的方法](#21请说出你所知道的线程同步的方法)
        - [22、stop()和suspend()方法为何不推荐使用？](#22stop和suspend方法为何不推荐使用)
        - [23、线程的sleep()方法和yield()方法有什么区别？](#23线程的sleep方法和yield方法有什么区别)
        - [24、当一个线程进入一个对象的synchronized方法A之后，其它线程是否可进入此对象的synchronized方法B？](#24当一个线程进入一个对象的synchronized方法a之后其它线程是否可进入此对象的synchronized方法b)
    - [6、锁](#6锁)
        - [1、锁总结](#1锁总结)
        - [2、讲一下非公平锁和公平锁在reetrantlock里的实现](#2讲一下非公平锁和公平锁在reetrantlock里的实现)
        - [3、讲一下synchronized，可重入怎么实现](#3讲一下synchronized可重入怎么实现)
        - [4、锁和同步的区别](#4锁和同步的区别)
        - [5、什么是死锁(deadlock)？](#5什么是死锁deadlock)
        - [6、如何确保N个线程可以访问N个资源同时又不导致死锁？](#6如何确保n个线程可以访问n个资源同时又不导致死锁)
        - [7、ReentrantLock中公平锁和非公平锁在哪里体现的？](#7reentrantlock中公平锁和非公平锁在哪里体现的)
        - [8、volatile的实现原理](#8volatile的实现原理)
    - [7、JDK](#7jdk)
        - [1、Java中的LongAdder和AtomicLong的区别](#1java中的longadder和atomiclong的区别)
        - [2、JDK和JRE的区别是什么？](#2jdk和jre的区别是什么)
        - [3、java的跨平台](#3java的跨平台)
        - [4、机器码和字节码的区别](#4机器码和字节码的区别)
    - [8、反射](#8反射)
        - [1、反射的实现与作用](#1反射的实现与作用)
    - [9、JVM](#9jvm)
        - [1、JVM回收算法和回收器，CMS采用哪种回收算法，怎么解决内存碎片问题？](#1jvm回收算法和回收器cms采用哪种回收算法怎么解决内存碎片问题)
        - [2、JVM分区](#2jvm分区)
        - [3、eden区，survial区](#3eden区survial区)
        - [4、JAVA虚拟机的作用](#4java虚拟机的作用)
        - [5、GC中如何判断对象需要被回收](#5gc中如何判断对象需要被回收)
        - [6、JAVA虚拟机中，哪些可作为ROOT对象？](#6java虚拟机中哪些可作为root对象)
        - [7、Java内存模型是什么？JVM内存模型呢？](#7java内存模型是什么jvm内存模型呢)
        - [8、jvm是如何实现线程？](#8jvm是如何实现线程)
        - [9、jvm最大内存限制多少](#9jvm最大内存限制多少)
        - [10、什么是Java虚拟机？为什么Java被称作是“平台无关的编程语言”？](#10什么是java虚拟机为什么java被称作是平台无关的编程语言)
        - [11、描述一下JVM加载class文件的原理机制？](#11描述一下jvm加载class文件的原理机制)
        - [12、内存分配与回收策略](#12内存分配与回收策略)
        - [13、JVM调优？](#13jvm调优)
        - [14、类加载机制，双亲委派模型，好处是什么？如何破坏双亲委派模型？应用场景？](#14类加载机制双亲委派模型好处是什么如何破坏双亲委派模型应用场景)
    - [10、GC](#10gc)
        - [1、java中内存泄露是啥，什么时候出现内存泄露？内存溢出？](#1java中内存泄露是啥什么时候出现内存泄露内存溢出)
        - [2、minor gc如果运行的很频繁，可能是什么原因引起的，minorgc如果运行的很慢，可能是什么原因引起的?](#2minor-gc如果运行的很频繁可能是什么原因引起的minorgc如果运行的很慢可能是什么原因引起的)
        - [3、阐述GC算法](#3阐述gc算法)
        - [4、GC是什么? 为什么要有GC?](#4gc是什么-为什么要有gc)
        - [5、垃圾回收的优点和原理。并考虑2种回收机制](#5垃圾回收的优点和原理并考虑2种回收机制)
        - [6、垃圾回收器可以马上回收内存吗？有什么办法主动通知虚拟机进行垃圾回收？（垃圾回收）](#6垃圾回收器可以马上回收内存吗有什么办法主动通知虚拟机进行垃圾回收垃圾回收)
    - [1、IO和NIO、AIO](#1io和nioaio)
        - [1、怎么打印日志？](#1怎么打印日志)
        - [2、运行时异常与一般异常有何异同？](#2运行时异常与一般异常有何异同)
        - [3、error和exception有什么区别?](#3error和exception有什么区别)
        - [4、给我一个你最常见到的runtime exception](#4给我一个你最常见到的runtime-exception)
        - [5、Java中的异常处理机制的简单原理和应用。](#5java中的异常处理机制的简单原理和应用)
        - [6、java中有几种类型的流？JDK为每种类型的流提供了一些抽象类以供继承，请说出他们分别是哪些类？](#6java中有几种类型的流jdk为每种类型的流提供了一些抽象类以供继承请说出他们分别是哪些类)
        - [7、什么是java序列化，如何实现java序列化？](#7什么是java序列化如何实现java序列化)
        - [8、运行时异常与受检异常有什么区别？](#8运行时异常与受检异常有什么区别)

<!-- /TOC -->
# javaSE
## 1、Java基础
### 1. 为什么重写equals还要重写hashcode
Object类默认的equals比较规则就是比较两个对象的内存地址， 默认的hashcode方法是根据对象的内存地址经哈希算法得来的，因此，二个对象equals相等，hashcode一定相等。根据对象的某种性质重写了equals方法后，为了保证同一个对象，保证equals相同的情况下hashcode值必定相同，如果重写了equals而未重写hashcode方法，可能就会出现两个没有关系的对象equals相同的（因为equal都是根据对象的特征进行重写的），但hashcode确实不相同的。
如果你改写了equal()方法，令两个实际不是一个对象的两个实例在逻辑上相等了，但是hashcode却是不等。所以要记得改写hashcode。

因为重写的equal里一般比较的比较全面比较复杂，这样效率就比较低，而利用hashCode()进行对比，则只要生成一个hash值进行比较就可以了，效率很高，那么hashCode()既然效率这么高为什么还要equal()呢？因为hashCode()并不是完全可靠，有时候不同的对象他们生成的hashcode也会一样（生成hash值得公式可能存在的问题），所以hashCode()只能说是大部分时候可靠，并不是绝对可靠，所以我们可以得出：
1. equal()相等的两个对象他们的hashCode()肯定相等，也就是用equal()对比是绝对可靠的。
2. hashCode()相等的两个对象他们的equal()不一定相等，也就是hashCode()不是绝对可靠的。

### 2、说一下map的分类和常见的情况
Java为数据结构中的映射定义了一个接口java.util.Map，此接口主要有四个常用的实现类，分别是HashMap、Hashtable、LinkedHashMap和TreeMap
* HashMap：它根据键的hashCode值存储数据，大多数情况下可以直接定位到它的值，因而具有很快的访问速度，但遍历顺序却是不确定的。 HashMap最多只允许一条记录的键为null，允许多条记录的值为null。HashMap非线程安全，即任一时刻可以有多个线程同时写HashMap，可能会导致数据的不一致。如果需要满足线程安全，可以用 Collections的synchronizedMap方法使HashMap具有线程安全的能力，或者使用ConcurrentHashMap。
* Hashtable：Hashtable是遗留类，很多映射的常用功能与HashMap类似，不同的是它承自Dictionary类，并且是线程安全的，任一时间只有一个线程能写Hashtable，并发性不如ConcurrentHashMap，因为ConcurrentHashMap引入了分段锁。Hashtable不建议在新代码中使用，不需要线程安全的场合可以用HashMap替换，需要线程安全的场合可以用ConcurrentHashMap替换。
* LinkedHashMap：LinkedHashMap是HashMap的一个子类，保存了记录的插入顺序，在用Iterator遍历LinkedHashMap时，先得到的记录肯定是先插入的，也可以在构造时带参数，按照访问次序排序。
* TreeMap：TreeMap实现SortedMap接口，能够把它保存的记录根据键排序，默认是按键值的升序排序，也可以指定排序的比较器，当用Iterator遍历TreeMap时，得到的记录是排过序的。如果使用排序的映射，建议使用TreeMap。在使用TreeMap时，key必须实现Comparable接口或者在构造TreeMap传入自定义的Comparator，否则会在运行时抛出java.lang.ClassCastException类型的异常。

对于上述四种Map类型的类，要求映射中的key是不可变对象。不可变对象是该对象在创建后它的哈希值不会被改变。如果对象的哈希值发生变化，Map对象很可能就定位不到映射的位置了。


### 3、Object若不重写hashCode()的话，hashCode()如何计算出来的？
Object 的 hashcode 方法是本地方法，也就是用 c 语言或 c++ 实现的，该方法直接返回对象的内存地址。
### 4、==比较的是什么？
对于对象引用类型:“==”比较的是对象的内存地址。
      对于基本类型数据，其实比较的是它的值。

### 5、若对一个类不重写，它的equals()方法是如何比较的？
如果没有对equals方法进行重写，则比较的是引用类型的变量所指向的对象的地址；诸如String、Date等类对equals方法进行了重写的话，比较的是所指向的对象的内容。
### 6、java8新特性
1. Lambda 表达式 − Lambda允许把函数作为一个方法的参数（函数作为参数传递进方法中）
2. 接口的默认方法和静态方法 −  可以在接口中定义默认方法，使用default关键字，并提供默认的实现。所有实现这个接口的类都会接受默认方法的实现，除非子类提供的自己的实现
3. 方法引用 − 方法引用使得开发者可以直接引用现存的方法、Java类的构造方法或者实例对象。可以与lambda联合使用
4. 重复注解- 注解有一个很大的限制是：在同一个地方不能多次使用同一个注解。Java 8打破了这个限制，引入了重复注解的概念，允许在同一个地方多次使用同一个注解
    ......  等等（重点lambda表达式）

### 7、说说Lamda表达式的优缺点。
* 优点：1. 简洁; 2. 非常容易并行计算; 3. 可能代表未来的编程趋势
* 缺点：1. 若不用并行计算，很多时候计算速度没有比传统的 for 循环快。（并行计算有时需要预热才显示出效率优势）2. 不容易调试。3. 若其他程序员没有学过 lambda 表达式，代码不容易让其他语言的程序员看懂。

### 8、一个十进制的数在内存中是怎么存的？
二进制补码形式
[原码补码反码介绍]( https://www.cnblogs.com/wangsiting/p/7339192.html)

### 9、为啥有时会出现4.0-3.6=0.40000001这种现象？
 2进制的小数无法精确的表达10进制小数，计算机在计算10进制小数的过程中要先转换为2进制进行计算，这个过程中出现了误差。

### 10、Java支持的数据类型有哪些？什么是自动拆装箱？
八个基本数据类型：byte，short，int，long，float，double，char，boolean；以及引用类型，引用类型包括类类型、接口类型和数组。整数默认int型，小数默认是double型，float、long类型必须加后缀f、l；

自动装箱和拆箱就是基本类型和其对应引用类型之间的转换，基本类型转换为引用类型后，就可以直接调用包装类中封装好的一些方法
![](https://ws1.sinaimg.cn/large/d4556b75ly1g3mteb1k1kj20l00eidgb.jpg)

### 11、什么是值传递和引用传递？
[参考网址]( https://www.cnblogs.com/xiaoxiaoyihan/p/4883770.html)
* 值传递，在方法的调用过程中，实参把它的实际值传递给形参，此传递过程就是将实参的值复制一份传递到函数中，这样如果在函数中对该值（形参的值）进行了操作将不会影响实参的值。
* 引用传递，将对象的地址值传递过去，函数接收的是原始值的首地址值。在方法的执行过程中，形参和实参的内容相同，指向同一块内存地址，也就是说操作的其实都是源数据，所以方法的执行将会影响到实际对象

### 12、数组(Array)和列表(ArrayList)有什么区别？什么时候应该使用Array而不是ArrayList？
Array 可以包含基本类型和对象类型，ArrayList 只能包含对象类型。 Array 大小是固定的，ArrayList 的大小是动态变化的。
ArrayList 提供了更多的方法和特性，比如:addAll()，removeAll()，iterator()等等。

对于基本类型数据，集合使用自动装箱来减少编码工作量。但是，当处理固定大小的基本数据类型的时候，这种方式相对比较慢。

### 13、你了解大O符号(big-Onotation)么？你能给出不同数据结构的例子么？
O表示算法的时间或者空间复杂度上界。比如数组的插入时间复杂度为O(N),空间复杂度为O(1),链表的插入时间复杂度为O(1),空间复杂度为O(1)

### 14、String是最基本的数据类型吗?
不是，基本数据类型包括：byte,short,int,long,float,double,boolean,char。而String是类代表字符串，属于引用类型，所谓引用类型包括：类，接口，数组...

### 15、int 和 Integer 有什么区别？
[参考网址](http://www.cnblogs.com/liuling/archive/2013/05/05/intAndInteger.html)

Ingeter是int的包装类，int的初值为0，Ingeter的初值为null。java可以通过自动拆箱和装箱对int和Integer进行转化。

### 16、String、StringBuffer、StringBuffer
1. String为字符串常量，每次对string操作都会产生一个新的对象，而StringBuilder和StringBuffer均为字符串变量，即String对象一旦创建之后该对象是不可更改的，但后两者的对象是变量，是可以更改的。因此在运行速度快慢为：StringBuilder > StringBuffer > String
2. 在线程安全上，StringBuilder是线程不安全的，而StringBuffer是线程安全的
3. String适用于少量的字符串操作的情况；StringBuilder适用于单线程下在字符缓冲区进行大量操作的情况；StringBuffer适用多线程下在字符缓冲区进行大量操作的情况

### 17、我们在web应用开发过程中经常遇到输出某种编码的字符，如iso8859-1等，如何输出一个某种编码的字符串？
通过new一个字符串对象，把原始编码和需要输出编码类型传进构造器中

```java
public String translate (String str) {
    String tempStr = "";
    try {
        tempStr = new String(str.getBytes("ISO-8859-1"), "GBK");
        tempStr = tempStr.trim();
    } catch  (Exception e)  {
        System.err.println(e.getMessage());
    }
    return tempStr;
}
```

### 18、&和&&的区别？
1. Java中&&和&都是表示与的逻辑运算符，都表示逻辑运输符and，当两边的表达式都为true的时候，整个运算结果才为true，否则为false。
2. &&的短路功能，当第一个表达式的值为false的时候，则不再计算第二个表达式；&则两个表达式都执行。
3. &可以用作位运算符，当&两边的表达式不是Boolean类型的时候，&表示按位操作。

### 19、在Java中，如何跳出当前的多重嵌套循环？
在Java中，要想跳出多重循环，可以在外面的循环语句前定义一个标号，
然后在里层循环体的代码中使用带有标号的break语句，即可跳出外层循环

### 20、你能比较一下Java和JavaSciprt吗？
1. 基于对象和面向对象：Java 是一种真正的面向对象的语言，即使是开发简单的程序，必须设计对象；JavaScript 是种脚本语 言，它可以用来制作与网络无关的，与用户交互作用的复杂软件。它是一种基于对 象（Object Based）和事件驱动（Event Driver）的编程语言。因而它本身提供了非常丰富的内部对象供设计人员使用；
2. 解释和编译：Java 的源代码在执行之前，必须经过编译；JavaScript 是一种解释性编程语言，其源代码不需经过编译，由浏览器解释执行；
3. 强类型变量和类型弱变量： Java 采用强类型变量检查，即所有变量在编译之前必须作声明；JavaScript 中变量声明，采用其弱类型。即变量在使用前不需作声明，而是解释器在运行时检查其数据类型；
4. 代码格式不一样。

### 21、正则表达式
1. 概念：
在编写处理字符串的程序时，经常会有查找符合某些复杂规则的字符串的需要。正则表达式就是用于描述这些规则的工具。换句话说，正则表达式就是记录文本规则的代码。
2. java与正则相关的工具主要在java.util.regex包中；此包中主要有两个类：Pattern、Matcher
* Pattern：
Pattern类表示正则表达式对象，用于创建一个正则表达式,也可以说创建一个匹配模式,它的构造方法是私有的,不可以直接创建,但可以通过Pattern.complie(String regex)简单工厂方法创建一个正则表达式
pattern() 方法返回正则表达式的字符串形式,其实就是返回Pattern.complile(String regex)的regex参数
```java
Pattern p=Pattern.compile("\\w+");
p.pattern();//返回 \w+
```
* Matcher：Matcher对象是对输入字符串进行解释和匹配操作的引擎与Pattern类一样，Matcher 也没有公共构造方法。你需要调用Pattern对象的matcher方法来获得一个Matcher对象。
```java
// 创建 Pattern 对象
        Pattern r = Pattern.compile(pattern);
        // 现在创建 matcher 对象
        Matcher m = r.matcher(line);
        if (m.find( )) {
            System.out.println("Found value: " + m.group(0) );
            System.out.println("Found value: " + m.group(1) );
        } else {
            System.out.println("NO MATCH");
        }
```
### 22、请你说说Java和PHP的区别？
1. Java是一种静态类型语言（强类型语言），需要编译后才能执行；PHP是一种动态类型语言（弱类型语言），不需要编译即可执行。
2. java使用封装继承，最小的单位是类，php作为脚本，最小单位就是语句，用两者输出hello world就知道了，所以java语法比较严格，而php很灵活
3. java是自动内存分配回收，php是一次创建一次销毁。
4. java可以常驻内存，多线程;php无法常驻内存，也没有线程的概念。
5. PHP:就是为web而生的语言，除了web什么都做不了，这既是它的缺点，也是它的优点，语法简洁灵活，和java冗长的语法正好形成对比
6. java已经是一门很成熟的语言，或者说其语言的进一步提升已经不可能能了，php是在web繁荣之后兴起的语言，所以语言成熟度没有java高。


## 2、关键字
### 1、介绍一下Syncronized锁，如果用这个关键字修饰一个静态方法，锁住了什么？如果修饰成员方法，锁住了什么？
Syncronized锁是同步锁，如果关键字修饰静态方法的话是一个类锁（当前类的所有线程都必须等待同步线程执行）， 如果关键字修饰成员方法的话是一个对象锁（当前对象的所有进程必须等待同步进程执行完，释放锁）。

### 2、介绍一下volatile？
volatile关键字可以修饰共享变量。保证其他线程访问这个变量的时候始终是最新值。 也就是volatile会更新最新值到java主内存中去，其他线程使用这个变量的时候会从java主内存中去取得这个变量。（解决可见性和有序性）

### 3、锁有了解嘛，说一下Synchronized和lock
1. Lock是一个接口，而synchronized是Java中的关键字，synchronized是内置的语言实现；
2. synchronized可以用来修饰方法代码块，Lock的话需要它的一些实现类来做到加锁和解锁比如ReentrantLock、 ReentrantReadWriteLock
3. synchronized在发生异常时，会自动释放线程占有的锁，因此不会导致死锁现象发生；而Lock在发生异常时，如果没有主动通过unLock()去释放锁，则很可能造成死锁现象，因此使用Lock时需要在finally块中释放锁；
4. Lock可以让等待锁的线程响应中断，通过调用方法lock.lockInterruptibly(),而synchronized却不行，使用synchronized时，等待的线程会一直等待下去，不能够响应中断；
5. 通过Lock可以知道有没有成功获取锁，而synchronized却无法办到。
6. Lock可以提高多个线程进行读操作的效率。
7. 在性能上来说，如果竞争资源不激烈，两者的性能是差不多的，而当竞争资源非常激烈时（即有大量线程同时竞争），此时Lock的性能要远远优于synchronized。

### 4、讲一讲Java里面的final关键字怎么用的？
1. 修饰类：表示该类不能被继承；
2. 修饰方法：表示方法不能被重写；
3. 修饰变量：表示变量只能赋值一次且赋值以后值不能被修改（常量）。

## 3、面向对象
### 1、wait方法底层原理
Object中的方法，可以暂停线程，期间会释放对象锁，不像sleep方法，线程休眠期依然持有锁，wait方法的线程，必须调用notify或notifyAll方法唤醒线程。

### 2、Java有哪些特性，举个多态的例子
 封装、继承以及多态，其中方法的重写和重载都和多态有关。 多态的主要特征就是父类引用指向子类对象，生活中的例子：Animal animal = new Dog();

### 3、String为啥不可变？String能继承吗？
 Sting是这样定义的：public final class String extends Object，里边有final关键字，所以不可变也不能被继承，同时string底层是字符串数组也是final修饰，这样做首先是安全，比如hashset中用string做为键，不会出现string变化，导致违反唯一键。另外节约内存
 
```java
public final class String
    implements java.io.Serializable, Comparable<String>, CharSequence {
    /** The value is used for character storage. */
    private final char value[];
  ...
}
```

### 4、类和对象的区别
类是抽象的结果，也是一种数据结构，类里面有属性、方法、代码块、构造器这些是类的基本元素。如果想使用类 ，那么你需要创建一个具体的对象，才能够正常使用类里面的属性和方法，同时，也有专门属于类的属性和方法， 属于类的东西， 可以没有对象也可以使用。由此可见对象是从类创建而来。

### 5、请列举你所知道的Object类的方法
1. getClass():用于返回当前运行时对象的Class对象，使用了final关键字修饰，故不允许子类重写
2. equals():用于比较两个对象的地址是否相同，即两个引用是否指向同一个对象；
3. clone():用于创建并返回当前对象的一份拷贝；
4. toString():返回类的名字@实例的哈希码的16进制字符串；
5. notify():唤醒等待队列中的其中一个线程；notifyAll():唤醒线程等待队列中的所有线程；
6. wait(long timeout):让一个线程等待一段时间。

### 6、重载(Overload)和重写(Override)的区别？相同参数不同返回值能重载吗？Overload的方法是否可以改变返回值的类型
相同参数不同返回值不可以重载,重载可以改变返回值的类型，重载的方法不能根据返回类型进行区分
* 重写：一个类是继承一个父类时，从父类那儿继承来的方法，进行重新写过。
* 重载：多个同名方法，名称相同，但是参数不同，可以通过参数来识别调用的是哪一个方法。

### 7、”static”关键字是什么意思？Java中是否可以覆盖(override)一个private或者是static的方法？
static是静态的意思，被static修饰的变量，在内存中只有一份，被所有对象共享，static修饰额方法叫静态方法，从属于类，可以通过类调用，也可以通过对象调用，方法中不能访问非静态变量和方法。

静态，就是禁止多态。所以不能重写static方法。 private是私有的，肯定不能重写了。

### 8、静态变量存在哪?
方法区，静态变量是共享内容，栈是不共享的，堆存放new关键字创建的对象实例，方法区是共享的区域，它用于存储已被虚拟机加载的类信息，常量，静态变量，即时编译后的代码等数据

### 9、讲讲什么是泛型？
泛型是一种参数化类型，它的<>里面可以放任何类型，而且不要强转，它是多态的一种体现。 泛型多用于容器中，往容器中方数据，事先约定什么类型数据，放的时候会检查，不是正确的类型放入时会报错，这样可以建立安全的数据，也避免了强制类型转换。

泛型也是Java提供的语法糖,只不过是将类型检查从运行期提到编译器.运行时都会被擦除为Object.,运行的时候都会在方法的入口和出口进行转换(就是发生擦除的边界位置),

### 10、解释extends 和super 泛型限定符-上界不存下界不取
extends上限通配符，用来限制类型的上限，只能传入本类和子类，add方法受阻，可以从一个数据类型里获取数据；

```java
List<? extends Number> eList = null;
eList = new ArrayList<Integer>();
eList = new ArrayList<Long>();
```
super下限通配符，用来限制类型的下限，只能传入本类和父类，get方法受阻，可以把对象写入一个数据结构里；

```java
List<? super Integer> sList = null;
sList = new ArrayList<Number>();
```

### 11、是否可以在static环境中访问非static变量？
不可以在static环静中，不可以访问非static。因为静态的成员属于类，随着类的加载而加载到静态方法区内存，当类加载时，此时不一定有实例创建，没有实例，就不可以访问非静态的成员。类的加载先于实例的创建，因此静态环境中，不可以访问非静态。

### 12、谈谈如何通过反射创建对象？
[参考网址](https://www.cnblogs.com/qjlbky/p/5929452.html)
1. 通过默认的构造器通过Class的newInstance()方法来获取
2. 通过指定的构造器来创建
```java
Class clazz = Class.forName(className);

 //1.通过Class获取指定构造方法，比如带两个参数
Constructor cons =clazz.getConstructor(String.class,int.class);//拿的是公有的
        
//2.通过指定的构造器对象进行对象的初始化。
Object obj = cons.newInstance("lisisi",23);
```

### 13、Java支持多继承么？
java只支持单继承，这是由于安全性的考虑，如果子类继承的多个父类里面有相同的方法或者属性，子类将不知道具体要继承哪个，而接口可以多实现，是因为接口只定义方法，而没有具体的逻辑实现，多实现也要重新实现方法。

### 14、接口和抽象类的区别是什么？
1. 接口的方法默认是public，所有方法在接口中不能有实现，抽象类可以有非抽象的方法， 可以由public protected或者默认修饰。 java1.8以前接口中方法不能有方法体，1.8以后可以由default关键字修  饰，从而可以拥有方法体。
2. 接口中的实例变量默认是final类型的，而抽象类中则不一定
3. 一个类可以实现多个接口，但最多只能实现一个抽象类
4. 一个类实现接口的话要实现接口的所有方法，而抽象类不一定

### 15、Comparable和Comparator接口是干什么的？列出它们的区别
1. Comparable & Comparator接口都可以用来实现集合中元素的比较、排序。
2. Comparator位于包java.util下，而Comparable位于包java.lang下
3. Comparable接口将比较代码嵌入自身类中，而后者在一个独立的类中实现比较。像Integer、String等这些基本类型的JAVA封装类都已经实现了Comparable接口，这些类对象本身就支持自比较，直接调用Collections.sort()就可以对集合中元素的排序，无需自己去实现Comparable接口。而有些自定义类的List序列，当这个对象不支持自比较或者自比较函数不能满足你的要求时，你可以写一个比较器来完成两个对象之间大小的比较，也就是指定使用Comparator（临时规则排序，也称作专门规则排序），如果不指定Comparator，那么就用自然规则排序，这里的自然顺序就是实现Comparable接口设定的排序方式。
4. java集合的工具类Collections中提供了两种排序的方法,分别是:
* Collections.sort(List list)
* Collections.sort(List list,Comparator c)
 
    第一种称为自然排序,参与排序的对象需实现comparable接口,重写其compareTo()方法,方法体中实现对象的比较大小规则；
    
  第二种叫定制排序,或自定义排序,需编写匿名内部类,先new一个Comparator接口的比较器对象c,同时实现compare()其方法。

### 16、面向对象的特征有哪些方面
1. 封装： 面向对象的封装就是把描述一个对象的属性和行为的代码封装在一个“模块”中，也就是一个类中，属性用变量定义，行为用方法进行定义，方法可以直接访问同一个对象中的属性
2. 继承： 在定义和实现一个类的时候，可以在一个已经存在的类的基础之上来进行，把这个已经存在的类所定义的内容作为自己的内容，并可以加入若干新的内容，或修改原来的方法使之更适合特殊的需要，这就是继承。继承是子类自动共享父类数据和方法的机制，这是类之间的一种关系，提高了软件的可重用性和可扩展性
3. 多态是指程序中定义的引用变量所指向的具体类型和通过该引用变量发出的方法调用在编程时并不确定，而是在程序运行期间才确定，即一个引用变量倒底会指向哪个类的实例对象，该引用变量发出的方法调用到底是哪个类中实现的方法，必须在由程序运行期间才能决定。

### 17、final, finally, finalize的区别
1. final:被final修饰的变量，赋值后，被视为常量，被final修饰的方法，不能再重写，被final修饰的类不能在被继承 
2. finally是异常中的一个关键字，try catch finally不管异常是否发生，finally块中的代码都会执行，程序的出口
3. finallize是java垃圾回收中的一个关键字，在对垃圾对象回收时，会调用finalize方法

### 18、Static Nested Class（嵌套类） 和 Inner Class（内部类）的不同
Static Nested Class是被声明为静态（static）的内部类，它可以不依赖于外部类实例被实例化。而通常的内部类需要在外部类实例化后才能实例化

### 19、当一个对象被当作参数传递到一个方法后，此方法可改变这个对象的属性，并可返回变化后的结果，那么这里到底是值传递还是引用传递?
传递的是值， 在 Java应用程序中，当对象引用传递给方法的一个参数时，传递的是该引用的一个副本（按值传递），实际上传递的该对象的内存首地址

### 20、Java的接口和C++的虚类的相同和不同处。
c++的虚类与java的抽象方法相同，其与接口的不同之处在于
1. 只能继承一个虚类，可以实现多个接口
2. 虚类中可以有构造方法，接口没有构造方法
3. 虚类中可以有非抽象方法，接口中必须都是抽象方法
4. 虚类的访问权限可以为pubic、private、protected和default，接口的访问权限只能是public
5. 虚类中的方法可以是pubic、private、protected和default的，接口中的方法只能是public和default的

他们的相同之处在于：都不能被实例化。

### 21、JAVA语言如何进行异常处理，关键字：throws,throw,try,catch,finally分别代表什么意义？在try块中可以抛出异常吗？
Java使用面向对象的方式来处理异常，它把程序中发生的每个异常也都分别封装到一个对象来表示的，该对象中包含有异常的信息。throws、throw、try、catch、finally就是Java中用来对异常进行处理的几个关键字

在Java编程中规定Java编译器强制普通异常必须try..catch处理或用throws声明继续抛给上层调用方法处理，一般异常必须要求被捕获和处理，而系统异常可以处理也可以不处理，所以编译器不强制用try..catch处理或用throws、throw声明异常。而 finally一般与try或try\catch一起使用做为异常的最后，finally是无论有没有异常发生，都要执行的代码块。

### 22、内部类可以引用他包含类的成员吗？有没有什么限制？
完全可以，内部类拥有外围类的所有元素的访问权，不论是外围的的私有方法和属性都可以访问的的到。如果不是静态内部类，那没有什么限制。如果把静态嵌套类当作内部类的一种特例，那在这种情况下不可以访问外部类的普通成员变 量，而只能访问外部类中的静态成员

### 23、两个对象值相同(x.equals(y) == true)，但却可有不同的hash code说法是否正确？
如果两个对象相同，那么它们的hashCode值一定要相同；如果两个对象的hashCode相同，它们并不一定相同。 重写了equals方法就但没重写hashcode方法，就会出现这样的问题。

### 24、如何通过反射获取和设置对象私有字段的值？
可以通过类对象的getDeclaredField()方法字段Field对象，然后再通过字段对象的setAccessible(true)将其设置为可以访问，接下来就可以通过get/set方法来获取/设置字段的值了。

```java
public static Object dictConvert (Object obj) {try {    //得到对象的所有私有属性    Field fields[] = obj.getClass().getDeclaredFields();getDeclaredFields()：    for (Field field : fields) {        //获得注解        FieldRemark fieldRemark = field.getAnnotation(FieldRemark.class);        if (fieldRemark != null && StringUtils.isNotBlank(fieldRemark.dictType())) {
        //如果accessible标志被设置为true，那么反射对象在使用的时候，不会去检查Java语言权限控制（如private）；
        field.setAccessible(true);
        //field.get(obj)为获取属性值
        String dictVal = DictUtils.getDictLabel(field.get(obj).toString(),fieldRemark.dictType(), "");
        field.setAccessible(true);
        //通过反射给指定字段赋值
        field.set(obj, dictVal);
    }
}
} catch (IllegalAccessException e) 
{
    e.printStackTrace();
}
    return obj;
}
```

### 25、谈一下面向对象的"六原则一法则"
* 六原则：
  * 单一职责原则：一个类只做它该做的事情。（单一职责原则想表达的就是"高内聚"，写代码最终极的原则只有六个字"高内聚、低耦合"，所谓的高内聚就是一个代码模块只完成一项功能，在面向对象  中，如果只让一个类完成它该做的事，而不涉及与它无关的领域就是践行了高内聚的原则，这个类就只有单一职责。
  * 开闭原则：软件实体应当对扩展开放，对修改关闭。（在理想的状态下，当我们需要为一个软件系统增加新功能时，只需要从原来的系统派生出一些新类就可以，不需要修改原来的任何一行代码。要做到开闭有两个要点：①抽象是关键，一个系统中如果没有抽象类或接口系统就没有扩展点；②封装可变性，将系统中的各种可变因素封装到一个继承结构中，如果多个可变因素混杂在一起，系统将变得复杂而混乱。
  * 依赖倒转原则：面向接口编程。（该原则说得直白和具体一些就是声明方法的参数类型、方法的返回类型、变量的引用类型时，尽可能使用抽象类型而不用具体类型，因为抽象类型可以被它的任何一个子类型所替代。
  * 里氏替换原则：任何时候都可以用子类型替换掉父类型。但简单的说就是能用父类型的地方就一定能使用子类型。里氏替换原则可以检查继承关系是否合理，如果一个继承关系违背了里氏替换原则，那么这个继承关系一定是错误的，需要对代码进行重构。
  * 接口隔离原则：接口要小而专，绝不能大而全。
  * 合成聚合复用原则：优先使用聚合或合成关系复用代码。要说明的是，即使在Java的API中也有不少滥用继承的例子，例如Properties类继承了Hashtable类，Stack类继承了Vector类，这些继承明显就是错误的，更好的做法是在Properties类中放置一个Hashtable类型的成员并且将其键和值都设置为字符串来存储数据，而Stack类的设计也应该是在Stack类中放一个Vector对象来存储数据。记住：任何时候都不要继承工具类，工具是可以拥有并可以使用的，而不是拿来继承的。 

* 迪米特法则：迪米特法则又叫最少知识原则，一个对象应当对其他对象有尽可能少的了解。就是说：一个实体应当尽量少的与其他实体之间发生相互作用，使得系统功能模块相对独立。
总结：单一职责原则告诉我们实现类要职责单一；里氏替换原则告诉我们不要破坏继承体系；依赖倒置原则告诉我们要面向接口编程；接口隔离原则告诉我们在设计接口的时候要精简单一；迪米特法则告诉我们要降低耦合。而开闭原则是总纲，他告诉我们要对扩展开放，对修改关闭。


### 27、请问Query接口的list方法和iterate方法有什么区别？
1. 返回的类型不一样，list返回List，iterate返回iterator
2. 查询策略不同。获取数据的方式不一样，list会直接查询数据库，iterate会先到数据库中把id取出来，然后真正要遍历某个对象的时候先到缓存中找，如果找不到，以id为条件再发一条sql到数据库，这样如果缓存中没有数据，则查询数据库的次数为n+1

### 28、Java中，什么是构造函数？什么是构造函数重载？什么是复制构造函数？
新对象被创建的时候，构造方法会被调用。每一个类都有构造方法。在程序员没有给类提供构造方法的情况下，Java编译器会为这个类创建一个默认的构造方法。

Java中构造方法重载和方法重载很相似。可以为一个类创建多个构造方法。每一个构造方法必须有它自己唯一的参数列表。

Java不支持像C++中那样的复制构造方法，这个不同点是因为如果你不自己写构造方法的情况下，Java不会创建默认的复制构造方法。

## 4、集合
### 1、ConcurrentHashMap？
[参考网址](https://sky-xin.iteye.com/blog/2431255)

concurrenthashmap是hashmap的多线程版本

* jdk1.7  
  * 采用Segment + HashEntry的方式进行实现。锁加在了不同的Segment，ConcurrentHashMap将数据分段，在读写的时候只加到相应的数据段上，这样在多线程的时候，可以读写其他段的数据，提高效率。
  * put操作：对于ConcurrentHashMap的数据插入，这里要进行两次Hash去定位数据的存储位置
  * get操作: ConcurrentHashMap的get操作跟HashMap类似，只是ConcurrentHashMap第一次需要经过一次hash定位到Segment的位置，然后再hash定位到指定的HashEntry，遍历该HashEntry下的链表进行对比，成功就返回，不成功就返回null 。

* jdk1.8

  * 实现已经摒弃了Segment的概念，而是直接用Node数组+链表+红黑树的数据结构来实现，并发控制使用Synchronized和CAS来操作。直接采用transient volatile HashEntry<k,v>[] table保存数据，采用table数组元素作为锁，从而实现了对每一行数据进行加锁，进一步减少并发冲突的概率。
   * put操作
     1. 如果没有初始化就先调用initTable（）方法来进行初始化过程
     2. 如果没有hash冲突就直接CAS插入
     3. 如果还在进行扩容操作就先进行扩容
     4. 如果存在hash冲突，就加锁来保证线程安全，这里有两种情况，一种是链表形式就直接遍历到尾端插入，一种是红黑树就按照红黑树结构插入
     5. 最后一个如果该链表的数量大于阈值8，就要先转换成黑红树的结构，break再一次进入循环
     6. 如果添加成功就调用addCount（）方法统计size，并且检查是否需要扩容

  * get操作：
    1. 计算hash值，定位到该table索引位置，如果是首节点符合就返回
    2. 如果遇到扩容的时候，会调用标志正在扩容节点ForwardingNode的find方法，查找该节点，匹配就返回
    3. 以上都不符合的话，就往下遍历节点，匹配就返回，否则最后就返回null 

### 2、hashMap？
[hashmap参考1](https://zhuanlan.zhihu.com/p/21673805)

[hashmap参考2](http://yikun.github.io/2015/04/01/Java-HashMap%E5%B7%A5%E4%BD%9C%E5%8E%9F%E7%90%86%E5%8F%8A%E5%AE%9E%E7%8E%B0/)
* 概念：
1. HashMap是一个散列桶（数组和链表），它存储的内容是键值对(key-value)映射
2. HashMap采用了数组和链表的数据结构，能在查询和修改方便继承了数组的线性查找和链表的寻址修改
3. HashMap是非synchronized，所以HashMap很快
4. HashMap可以接受null键和值，而Hashtable则不能（原因就是equlas()方法需要对象，因为HashMap是后出的API经过处理才可以）
* 工作原理：

  JDK7中HashMap采用的是位桶+链表的方式，即我们常说的散列链表的方式，而JDK8中采用的是位桶+链表/红黑树。

  HashMap的底层主要是基于数组和链表来实现的，HashMap底层是通过链表来解决hash冲突的。HashMap底层就是一个数组结构，数组中存放的是一个Node对象，实现了Map.Entry接口，本质是就是一个映射(键值对)。如果产生的hash冲突，也就是说要存储的那个位置上面已经存储了对象了，这时候该位置存储的就是一个链表了。

* HashMap类中的一些关键属性：
Node[] table的初始化长度length默认值是16；loadFactor为负载因子(默认值是0.75)，threshold临界值大小,是HashMap所能容纳的最大数据量的Node(键值对)个数。threshold = length * loadFactor,；当实际大小超过临界值时，会进行扩容。loadFactor加载因子，其中加载因子是表示Hash表中元素的填满的程度.若加载因子越大,填满的元素越多,好处是,空间利用率高了,但冲突的机会加大了。反之,加载因子越小,填满的元素越少,好处是冲突的机会减小了,但空间浪费多了，取默认值0.75就好了；size就是HashMap中实际存在的键值对数量； 
modCount字段主要用来记录HashMap内部结构发生变化的次数，主要用于迭代的快速失败。强调一点，内部结构发生变化指的是结构发生变化，例如put新键值对，但是某个key对应的value值被覆盖不属于结构变化。
```java
int threshold;             // 所能容纳的key-value对极限
final float loadFactor;    // 负载因子
int modCount;
int size;
```
* 确定哈希桶数组索引位置
   * Hash算法本质上就是三步：取key的hashCode值、高位运算、取模运算。
   * 通过h & (table.length -1)来得到该对象的保存位，而HashMap底层数组的长度总是2的n次方，这是HashMap在速度上的优化。当length总是2的n次方时，h & (length-1)运算等价于对length取模，也就是h % length，但是&比%具有更高的效率。
   * 在JDK1.8的实现中，优化了高位运算的算法，通过hashCode()的高16位异或低16位实现的：(h = k.hashCode()) ^ (h >>> 16)，主要是从速度、功效、质量来考虑的，在n - 1为15(0x1111)时，其实散列真正生效的只是低4bit的有效位，容易发生碰撞。
   这么做可以在数组table的length比较小的时候，也能保证考虑到高低Bit都参与到Hash的计算中，同时不会有太大的开销。代码如下：
```java
方法一：
static final int hash(Object key) {   //jdk1.8 & jdk1.7
     int h;
     // h = key.hashCode() 为第一步 取hashCode值
     // h ^ (h >>> 16)  为第二步 高位参与运算
     //高16bit不变，低16bit和高16bit做了一个异或
     return (key == null) ? 0 : (h = key.hashCode()) ^ (h >>> 16);
     
}
方法二：
static int indexFor(int h, int length) {  //jdk1.7的源码，jdk1.8没有这个方法，但是实现原理一样的
     return h & (length-1);  //第三步 取模运算
}
```

* get()操作原理：
1. bucket里的第一个节点，直接命中；
2. 如果有冲突，则通过key.equals(k)去查找对应的entry
   * 若为树，则在树中通过key.equals(k)查找，O(logn)；
   * 若为链表，则在链表中通过key.equals(k)查找，O(n)。

* put()操作原理：
1. 对key的hashCode()做hash，然后再计算index;
2. 如果没碰撞直接放到bucket里；
3. 如果碰撞了，以链表的形式存在buckets后；
4. 如果碰撞导致链表过长(大于等于TREEIFY_THRESHOLD)，就把链表转换成红黑树；
5. 如果节点已经存在就替换old value(保证key的唯一性)
6. 如果bucket满了(超过load factor * current capacity)，就要resize。

* 扩容机制resize
   * JKD1.7：旧桶数组中的某个桶的外挂单链表的Node结点是通过头插法插入新桶数组中的，并且原链表中的Node结点并不一定仍然在新桶数组的同一链表。
   * JDK1.8：扩容使用的是2次幂的扩展(指长度扩为原来2倍)，所以，元素的位置要么是在原位置，要么是在原位置再移动2次幂的位置。
因此，在扩充HashMap的时候，不需要像JDK1.7的实现那样重新计算hash，只需要看原来的hash值新增的那个bit是1还是0就好了，是0的话索引没变，是1的话索引变成“原索引+oldCap”

* JDK1.8与JDK1.7的性能对比

  HashMap中，如果key经过hash算法得出的数组索引位置全部不相同，即Hash算法非常好，那样的话，getKey方法的时间复杂度就是O(1)，如果Hash算法技术的结果碰撞非常多，假如Hash算极其差，所有的Hash算法结果得出的索引位置一样，那样所有的键值对都集中到一个桶中，或者在一个链表中，或者在一个红黑树中，时间复杂度分别为O(n)和O(lgn)。 鉴于JDK1.8做了多方面的优化，总体性能优于JDK1.7。

* jdk1.8使用链表+红黑树原因

  在Java 8之前的实现中是用链表解决冲突的，在产生碰撞的情况下，进行get时，两步的时间复杂度是O(1)+O(n)。因此，当碰撞很厉害的时候n很大，O(n)的速度显然是影响速度的。
因此在Java 8中，利用红黑树替换链表，这样复杂度就变成了O(1)+O(logn)了，这样在n很大的时候，能够比较理想的解决这个问题

### 3、如果hashMap的key是一个自定义的类，怎么办？
必须重写该类的hashcode()方法和equals()方法

HashMap中，如果要比较key是否相等，要同时使用这两个函数:通过hashcode值定位bucket位置，如果发生冲突通过equal方法定位在链表或者红黑树中的插入位置
因为自定义的类的hashcode()方法继承于Object类，其hashcode码为默认的内存地 址，这样即便有相同含义的两个对象，比较也是不相等的，equals()比较的是内存地址是否相等。

### 4、ArrayList和LinkedList的区别，如果一直在list的尾部添加元素，用哪个效率高？
ArrayList是实现了基于动态数组的数据结构，LinkedList基于链表的数据结构

~~当输入的数据一直是小于千万级别的时候，大部分是Linked效率高, 而当数据量大于千万级别的时候，就会出现ArrayList的效率比较高了。~~

~~LinkedList每次增加的时候，会new 一个Node对象来存新增加的元素，所以当数据量小的时候，这个时间并不明显，而ArrayList需要扩容，所以LinkedList的效率就会比较高，其中如果ArrayList出现不需要扩容的时候，那么ArrayList的效率应该是比LinkedList高的，当数据量很大的时候，new对象的时间大于扩容的时间，那么就会出现ArrayList'的效率比Linkedlist高了~~

选择LinkedList，arraylist是静态内存。如果一直插，需要耗费时间，并且可能会造成没内存泄露，扩容有可能导致内存不够

### 5、TreeMap底层，红黑树原理？
[参考1](https://blog.csdn.net/sun_tttt/article/details/65445754)
[参考2](https://blog.csdn.net/qq_39295755/article/details/80182288)

* TreeMap：

  1. 继承于AbstractMap，是一个有序的key-value集合，基于红黑树(Red-Black tree)实现
  2. 该映射根据其键的自然顺序进行排序，或者根据创建时提供的Comparator进行排序
  3. 实现了NavigableMap接口，意味着它支持一系列的导航方法。比如返回有序的key集合
  4. 实现了Cloneable接口，意味着它能被克隆
  5. 实现了java.io.Serializable接口，意味着它支持序列化
  6. 基本操作 containsKey、get、put 和 remove 的时间复杂度是 log(n)
  7. TreeMap是非同步的。 它的iterator 方法返回的迭代器是fail-fast的。
  
* 红黑树
  
  * 概念：为一颗二叉搜索树，每个节点上增加了一个存储位来表示节点的颜色，通过对任意一条叶子节点到根节点的路径上的颜色进行约束，保证最长路径不超过最短路径的两倍，因此红黑树是近似平衡。
  
  * 性质（这五条性质约束了红黑树，满足这五条性质的二叉树可以将查找删除维持在对数时间内）：
    1. 每个节点要么是红色，要么是黑色
    2. 根节点永远是黑色的
    3. 所有的叶节点都是空节点（即 null，实际上是不存在的节点），并且是黑色的
    4. 每个红色节点的两个子节点都是黑色。（从每个叶子到根的路径上不会有两个连续的红色节点）
    5. 从任一节点到其子树中每个叶子节点的路径都包含相同数量的黑色节点

  * 节点插入：红黑树插入节点的时候需要考虑新节点的颜色是红色的还是黑色的，假设新节点缺省颜色是黑色的，那么只要插入进去，该路径上的黑色节点数比其他路径上的节点数多一个，这时就要对其他路径进行调整；如果插入的节点是红色节点，如果该节点父亲节点是黑色，直接插入，如果该节点父亲节点是红色，就只在该条路径上进行调整。

### 6、ArrayList是否会越界？
会的，ArrayList底层是数组实现，在执行add(int index， E element)操作时，给定的下标index可以在 0 到 size 之间，如果不在这个范围之内，则会出现数组下标越界问题： 

```java
if (index > size || index < 0) throw new IndexOutOfBoundsException(outOfBoundsMsg(index));
```

多线程环境下执行add操作时，若此时集合只够容纳一个元素，线程A执行add操作，首先通过函数函数ensureCapacityInternal(size + 1)确保还可以添加一个元素，故没有进行数组扩容，之后线程A被阻塞。另一个线程B进来执行add方法添加了一个元素，此时线程A被唤醒，由于之前判断数组还可以添加一个元素，故直接执行add反法，此时便会出现下标越界问题。

```java
public boolean add(E e) {
    ensureCapacityInternal(size + 1); // Increments modCount!!
    elementData[size++] = e;
    return true;
}
```

~~如果执行add++()方法的话，单线程环境下，当add一个元素时，size先会执行size++ 操作，之后将指定的元素添加到size+1的位置，如果是多线程环境下，也有可能出现下标越界问题，解释如下：由于add（E e）方法没有同步，若此时集合容量为15，当集合中已经添加了14个元素时，一个线程率先进入add()方法，在执行ensureCapacityInternal(size + 1)时，发现还可以添加一个元素，故数组没有扩容，但随后该线程被阻塞在此处。接着另一线程进入add()方法，执行ensureCapacityInternal(size + 1)，由于前一个线程并没有添加元素，故size依然为14，依然不需要扩容，所以该线程就开始添加元素，使得size++，变为15，数组已经满了。而刚刚阻塞在elementData[size++] = e语句之前的线程开始执行，它要在集合中添加第16个元素，而数组容量只有15个，所以就发生了数组下标越界异常。~~


### 7、Java集合类框架的基本接口有哪些？
总共有两大接口：Collection和Map ，一个元素集合，一个是键值对集合。 

* List和Set接口继承了Collection接口，其中List是有序元素集合，必须按照插入顺序保存元素；Set是无序元素集合，不能有重复元素。 而ArrayList和 LinkedList 实现了List接口，HashSet、TreeSet、LinkedHashSet实现了Set接口，HashSet是最快获取元素的方式，TreeSet按照比较结果的升序保存对象，LinkedHashSet按照被添加的结果保存对象。Queue按照排队规则来确定对象产生的顺序。
* HashMap、TreeMap、LinkedHashMap实现了Map接口，与HashSet一样，HashMap提供了最快的查询技术，TreeMap按照比较结果的升序保存键，LinkedHashMap按照插入顺序保存键

### 8、为什么集合类没有实现Cloneable和Serializable接口？
克隆(cloning)或者是序列化(serialization)的语义和含义是跟具体的实现相关的。因此，应该由集合类的具体实现来决定如何被克隆或者是序列化。

Collection表示一个集合，包含了一组对象。如何存储和维护这些对象是由具体实现来决定的。因为集合的具体形式多种多样，例如list允许重复，set则不允许。而克隆（clone）和序列化（serializable）只对于具体的实体，对象有意义，你不能说去把一个接口，抽象类克隆，序列化甚至反序列化。所以具体的collection实现类是否可以克隆，是否可以序列化应该由其自身决定，而不能由其超类强行赋予。

如果collection继承了clone和serializable，那么所有的集合实现都会实现这两个接口，而如果某个实现它不需要被克隆，甚至不允许它序列化（序列化有风险），那么就与collection矛盾了。

### 9、什么是迭代器？
Iterator接口提供了很多对集合元素进行迭代的方法。每一个集合类都包含了可以返回迭代器实例的迭代方法。迭代器可以在迭代的过程中删除底层集合的元素,但是不可以直接调用集合的remove(Object Obj)删除，可以通过迭代器的remove()方法删除。

### 10、Iterator和ListIterator的区别是什么？
* 两个都是集合的迭代器。Iterator使用范围是集合，ListIterator的使用范围是List接口。而且ListIterator是继承于Iterator的接口：


```java
public interface ListIterator<E> extends Iterator<E> {}
```

* 两者功能来说：Iterator：
  1. 是否存在下一个元素； 
  2. 获取下一个元素；
  3. 删除当前元素；

* ListIterator因为是继承Iterator接口所以拥有Iterator接口的全部功能外还有获取上一个元素的能力等：
  1. 是否存在上一个元素；
  2. 获取上一个元素； 
  3. 可以添加元素，但是Iterator不能添加元素

### 11、快速失败(fail-fast)和安全失败(fail-safe)的区别是什么？
* 快速失败（fail—fast）
  * 概念：在用迭代器遍历一个集合对象时，如果遍历过程中对集合对象的内容进行了修改（增加、删除修改），则会抛出Concurrent Modification Exception。
  * 原理：
迭代器在遍历时直接访问集合中的内容，并且在遍历过程中使用一个 modCount 变量。集合在被遍历期间如果内容发生变化，就会改变modCount的值。每当迭代器使用hashNext()/next()遍历下一个元素之前，都会检测modCount变量是否为expectedmodCount值，是的话就返回遍历；否则抛出异常，终止遍历。
  * 注意：这里异常的抛出条件是检测到 modCount！=expectedmodCount 这个条件。如果集合发生变化时修改modCount值刚好又设置为了expectedmodCount值，则异常不会抛出。因此，不能依赖于这个异常是否抛出而进行并发操作的编程，这个异常只建议用于检测并发修改的bug。
  * 场景：java.util包下的集合类都是快速失败的，不能在多线程下发生并发修改（迭代过程中被修改）。
* 安全失败（fail—safe）:
  * 采用安全失败机制的集合容器，在遍历时不是直接在集合内容上访问的，而是先复制原有集合内容，在拷贝的集合上进行遍历。
  * 原理：由于迭代时是对原集合的拷贝进行遍历，所以在遍历过程中对原集合所作的修改并不能被迭代器检测到，所以不会触发Concurrent Modification Exception。
  * 缺点：基于拷贝内容的优点是避免了Concurrent Modification Exception，但同样地，迭代器并不能访问到修改后的内容，即：迭代器遍历的是开始遍历那一刻拿到的集合拷贝，在遍历期间原集合发生的修改迭代器是不知道的。
  * 场景：java.util.concurrent包下的容器都是安全失败，可以在多线程下并发使用，并发修改

### 12、HashMap和Hashtable有什么区别？
1. HashMap线程不安全，操作速度较快；Hashtable使用 synchronized 来进行同步，线程安全，操作速度较慢。
2. HashMap允许键值为空，Hashtable不允许
3. HashMap 的迭代器是 fail-fast 迭代器

### 13、ArrayList和LinkedList有什么区别？ 
1. ArrayList和Linkedlist都实现List接口， ArrayList的实现用的是动态数组，LinkedList是基于链表
2. ArrayList支持随机访问，LinkedList是以元素列表的形式存储它的数据，每一个元素都和它的前一个元素和后一个元素链接起来，查找某个元素的时间复杂度为O（n）；
3. 相对于ArrayList，LinkedList的插入，增加，删除速度更快，因为其不需要像数组那样插入时需要重新计算索引；
4. LinkedList比ArrayList占用更大的内存，因为Linkedlist为每个节点存储俩个引用，一个指向前一个元素，另一个指向后一个元素。

### 14、ArrayList,Vector,LinkedList的存储性能和特性是什么？
1. ArrayList 和Vector他们底层的实现都是一样的，都是使用数组方式存储数据，此数组元素数大于实际存储的数据以便增加和插入元素，它们都允许直接按序号索引元素，但是插入元素要涉及数组元素移动等内存操作，所以索引数据快而插入数据慢。
2. LinkedList使用双向链表实现存储，按序号索引数据需要进行前向或后向遍历，但是插入数据时只需要记录本项的前后项即可，所以插入速度较快。
3. Vector属于遗留容器， 已经不推荐使用，但是由于ArrayList和LinkedListed都是非线程安全的，如果遇到多个线程操作同一个容器的场景，则可以通过工具类Collections中的synchronizedList方法将其转换成线程安全的容器后再使用

### 15、Collection 和 Collections的区别
1. Collection是集合类的上级接口，继承于它的接口主要有Set和List。
2. Collections是针对集合类的一个帮助类，它提供了一系列静态方法实现了对各种集合的排序，搜索和线程安全等操作。

### 16、List、Map、Set三个接口存取元素时，各有什么特点？
list数据有序允许数据重复，set数据无序不允许数据重复，map以键值对存，键不能重复，可以允许一个键为null，允许多个值为null

## 5、线程 
### 1、多线程中的i++线程安全吗？为什么？
* 如果i是局部变量（在方法里定义的），那么是线程安全的。因为局部变量是线程私有的，别的线程访问不到，其实也可以说没有线程安不安全之说，因为别的线程对他造不成影响。
* 如果i是全局变量（类的成员变量），那么是线程不安全的。因为如果是全局变量的话，同一进程中的不同线程都有可能访问到。
每个线程都有自己的工作内存，每个线程需要对共享变量操作时必须把共享变量从主内存中加载到自己的工作内存。等完成操作再保存到内存中。如果一个线程运算完成后还没刷到主内存中，另一个线程又对这个共享变量进行操作，那么读取到的数据就是脏数据了。
* 对于 i++ 这种线程不安全问题有以下几种解决方案：
  1. 对 i++ 操作的方法加同步锁，同时只能有一个线程执行 i++ 操作；
  2. 使用支持原子性操作的类，如 java.util.concurrent.atomic.AtomicInteger，它使用的是CAS 算法，效率优于第 1 种;

### 2、如何线程安全的实现一个计数器？
* 通过AtomicInteger类循环CAS操作

```java
private int count = 0;
private AtomicInteger atomicI = new AtomicInteger(0);

/**线程不安全的计数器*/
public void count(){
    count++;
}

/**线程安全的计数器，循环CAS*/
public void safeCount(){
    for(;;){
        int temp = atomicI.get();
        if(atomicI.compareAndSet(temp,++temp))
        break;
    }
}
```
* 通过关键字volatile和synchronized实现

```Java
public class AtomicCounter {
    private volatile int count = 0;

    public synchronized void increment() {
        count++;
    }
 
    public int getCount() {
        return count;
    }
}

```


### 3、多线程同步的方法
[参考](    https://www.cnblogs.com/XHJT/p/3897440.html)
1. 使用sychronized同步关键字修饰方法和代码块
2. 使用volatile修饰共享变量实现同步
3. 使用重入锁实现线程同步。ReentrantLock类是可重入、互斥、实现了Lock接口的锁，常用方法有：ReentrantLock() : 创建一个ReentrantLock实例 ； lock() : 获得锁；unlock() : 释放锁 
4. 使用局部变量实现线程同步。类ThreadLocal给每个线程绑定自己的值，实现每一个线程都有自己的共享变量。常用方法：
    1. ThreadLocal() : 创建一个线程本地变量 
    2. get() : 返回此线程局部变量的当前线程副本中的值 
    3. initialValue() : 返回此线程局部变量的当前线程的"初始值" 
    4. set(T value) : 将此线程局部变量的当前线程副本中的值设置为value
5. 使用阻塞队列实现线程同步。当队列满时，队列会阻塞插入元素的线程，队列为空时，获取元素的线程会阻塞直到等待队列变为空。发生阻塞的插入方法为put()，移除方法为take()。阻塞队列类似                     ArrayBlockingQueue、LinkedBlockingQueue。阻塞队列通常用来实现生产者和消费者模式。
6. 使用原子变量实现线程同步. 在java的util.concurrent.atomic包中提供了创建了原子类型变量的工具类，使用该类可以简化线程同步。 
AtomicInteger 表可以用原子方式更新int的值， AtomicInteger类常用方法：
   1. AtomicInteger(int initialValue) : 创建具有给定初始值的新的AtomicInteger
   2. addAddGet(int dalta) : 以原子方式将给定值与当前值相加
   3. get() : 获取当前值

### 4、介绍一下生产者消费者模式？
生产者和消费者模式是通过一个容器解决生存者和消费者的强耦合问题。生产者和消费者之间不直接通信，而是通过阻塞队列来进行通信，所以生产者生产完数据之后不用等待消费者来处理，而是直接扔给阻塞队列，消费者不找生产者要数据，而是直接从阻塞队列里取，阻塞队列相当于一个缓冲区，平衡了生产者和消费者的处理能力。

Java中的线程池实际就是一种生产者和消费者模式的实现方式，生产者把任务丢给线程池，线程池创建线程并处理任务，如果将要运行的任务数大于线程池的基本线程数就把任务扔到阻塞队列里面，这种做法比使用一个阻塞队列实现生产者和消费者模式要好的多，因为消费者能够处理直接就处理掉了，这样速度更快，而生产者先存，消费者再取这种方式显然要慢一些。

### 5、线程，进程，然后线程创建有很大开销，怎么优化？
进程是资源（CPU、内存等）分配的基本单位，它是程序执行时的一个实例。程序运行时系统就会创建一个进程，并为它分配资源，然后把该进程放入进程就绪队列，进程调度器选中它的时候就会为它分配CPU时间，程序开始真正运行。

线程是程序执行时的最小单位，它是进程的一个执行流，是CPU调度和分派的基本单位，一个进程可以由很多个线程组成，线程间共享进程的所有资源，每个线程有自己的堆栈和局部变量。

使用线程池进行优化。


### 6、线程池运行流程，参数，策略
* 处理流程：
首先判断核心线程池里的线程是否都在执行任务，如果不是则直接从核心线程池中创建一个线程来执行，如果都在忙则判断任务队列是否也满了，没满的话将任务放进去等待执行，满了就判断线程池的全部线程是否都在忙，如果都在忙就交给饱和策略来处理，否则就创建一个线程来帮助核心线程处理任务。
* 参数：
  1. corePoolSize:核心线程池大小
  2. MaximumPoolSize：线程池允许创建的最大线程数，如果使用无界队列该参数无效
  3. ThreadFactory：线程工厂，主要用来创建线程
  4. runnableTaskQueue：任务队列，用于保存等待执行的任务的阻塞队列
  5. RejectedExecutionHandler：饱和策略
* 策略
  1. ThreadPoolExecutor.AbortPolicy:丢弃任务并抛出RejectedExecutionException异常（默认情况）
  2. ThreadPoolExecutor.DiscardPolicy：也是丢弃任务，但是不抛出异常。
  3. ThreadPoolExecutor.DiscardOldestPolicy：丢弃队列最前面的任务，然后重新尝试执行任务4. ThreadPoolExecutor.CallerRunsPolicy：只用调用者所在线程来运行任务

### 7、AQS
[参考](https://www.jianshu.com/p/da9d051dcc3d)

* AQS全称为AbstractQueuedSynchronizer,是并发容器中的同步器，它是抽象的队列式的同步器，AQS定义了一套多线程访问共享资源的同步器框架，许多同步类都依赖它，如ReentrantLock、Semaphore、CyclicBarrier、Condition、FutureTask等


* AQS的实现依赖内部的同步队列（FIFO双向队列）， 维护了一个volatile int类型的变量state，用来表示当前同步状态，如果当前线程获取同步状态失败，AQS会将该线程以及等待状态等信息构造成一个Node，将其加入同步队列的尾部，同时阻塞当前线程，当同步状态释放时，唤醒队列的头节点


* 获取锁：AQS中维护了一个同步状态status来计数重入次数，status初始值为0。当线程尝试获取锁时，可重入锁先尝试获取并更新status值，如果status == 0表示没有其他线程在执行同步代码，则把status置为1，当前线程开始执行。如果status != 0，则判断当前线程是否是获取到这个锁的线程，如果是的话执行status+1，且当前线程可以再次获取锁。


* state的访问方式有三种, 这三种叫做均是原子操作，其中compareAndSetState的实现依赖于Unsafe的compareAndSwapInt()方法:
  1. getState()
  2. setState()
  3. compareAndSetState()


* AQS定义两种资源共享方式：Exclusive（独占，只有一个线程能执行，如ReentrantLock）和Share（共享，多个线程可同时执行，如Semaphore/CountDownLatch）


* 不同的自定义同步器争用共享资源的方式也不同。自定义同步器在实现时只需要实现共享资源state的获取与释放方式即可，至于具体线程等待队列的维护（如获取资源失败入队/唤醒出队等），AQS已经在顶层实现好了。自定义同步器实现时主要实现以下几种方法：
  1. tryAcquire(int)：独占方式。尝试获取资源，成功则返回true，失败则返回false。
  2. tryRelease(int)：独占方式。尝试释放资源，成功则返回true，失败则返回false。
  3. tryAcquireShared(int)：共享方式。尝试获取资源。负数表示失败；0表示成功，但没有剩余可用资源；正数表示成功，且有剩余资源。
  4. tryReleaseShared(int)：共享方式。尝试释放资源，如果释放后允许唤醒后续等待结点返回true，否则返回false。

* acquire(int)
  * 流程：
    1. 调用自定义同步器的tryAcquire()尝试直接去获取资源，如果成功则直接返回；
    2. 没成功，则addWaiter()将该线程加入等待队列的尾部，并标记为独占模式；
    3. acquireQueued()使线程在等待队列中休息，有机会时（轮到自己，会被unpark()）会去尝试获取资源。获取到资源后才返回。如果在整个等待过程中被中断过，则返回true，否则返回false
    4. 如果线程在等待过程中被中断过，它是不响应的。只是获取资源后才再进行自我中断selfInterrupt()，将中断补上
  * 其它方法：
    1. addWaiter(Node)：该方法用于将当前线程根据不同的模式（Node.EXCLUSIVE互斥模式、Node.SHARED共享模式）加入到等待队列的队尾，并返回当前线程所在的结点。如果队列不为空，则以通过compareAndSetTail方法以CAS的方式将当前线程节点加入到等待队列的末尾。否则，通过enq(node)方法初始化一个等待队列，并返回当前节点
    2. enq(node)用于将当前节点插入等待队列，如果队列为空，则初始化当前队列。整个过程以CAS自旋的方式进行，直到成功加入队尾为止
    3. acquireQueued(Node, int) 用于队列中的线程自旋地以独占且不可中断的方式获取同步状态（acquire），直到拿到锁之后再返回
      ```java
      public final void acquire(int arg) {
            if (!tryAcquire(arg) &&
                acquireQueued(addWaiter(Node.EXCLUSIVE), arg))
                selfInterrupt();
      }
    ```
* release(int)：独占模式下线程释放共享资源的顶层入口。它会释放指定量的资源，如果彻底释放了（即state=0）,它会唤醒等待队列里的其他线程来获取资源。这也正是unlock()的语义，当然不仅仅只限于unlock()。

  正常来说，tryRelease()都会成功的，因为这是独占模式，该线程来释放资源，那么它肯定已经拿到独占资源了，直接减掉相应量的资源即可(state-=arg)，也不需要考虑线程安全的问题。但要注意它的返回值，上面已经提到了，release()是根据tryRelease()的返回值来判断该线程是否已经完成释放掉资源了！所以自义定同步器在实现时，如果已经彻底释放资源(state=0)，要返回true，否则返回false
  
  release(int)源码如下：
    ```Java
    public final boolean release(int arg) {
            if (tryRelease(arg)) {
                Node h = head;
                if (h != null && h.waitStatus != 0)
                    unparkSuccessor(h);//唤醒等待队列中下一个线程
                return true;
            }
            return false;
    }
    ```
### 8、创建线程的方法，哪个更好，为什么？
1. 继承Thread类（真正意义上的线程类），是Runnable接口的实现。
2. 实现Runnable接口，并重写里面的run方法。
3. 使用Executor框架创建线程池。

一般情况下，常见的是第二种Runnable接口有如下好处：
1. 避免点继承的局限，一个类可以继承多个接口；
2. 适合于资源的共享

### 9、Java中有几种方式启动一个线程？
第一种:继承Thread类,重写run方法.第二种:实现Runable接口,重写run方法

### 10、什么是线程池？Java中有几种线程池？

* 线程池是存储线程的容器,线程事先创建好后放入线程池,当有任务需要执行时,直接从线程池拿空闲线程使用,使用完毕后归还给线程池

* ThreadPoolExcutor有以下三种：
  1. FixedThreadPool ：创建一个指定工作线程数量的线程池。每当提交一个任务就创建一个工作线程，如果工作线程数量达到线程池初始的最大数，则将提交的任务存入到池队列中,使用LinkedBlockingQueue作为线程池的工作队列；
  2. SingleThreadExecutor ：创建一个单线程化的Executor，即只创建唯一的工作者线程来执行任务，它只会用唯一的工作线程来执行任务，保证所有任务按照指定顺序(FIFO, LIFO, 优先级)执行。如果这个线程异常结束，会有另一个取代它，保证顺序执行，使用LinkedBlockingQueue作为线程池的工作队列；
  3. CachedThreadPool ：创建一个可缓存线程池， 如果线程池长度超过处理需要，可灵活回收空闲线程，若无可回收，则新建线程
* ScheduledThreadPoolExecutor有以下二种：
  1. ScheduledThreadPoolExecutor：适用于需要多个后台线程执行周期任务，包含若干个线程
  2. SingleThreadScheduledExecutor：适用于需要一个后台线程执行周期任务，只包含一个线程，同时需要保证顺序的执行各个任务的应用场景

### 11、线程池有什么好处？
1. 降低资源消耗，通过重复利用已经创建的线程降低线程创建和销毁造成的消耗
2. 提高响应速度，当任务达到时，任务可以不需要的等到线程创建就能够立即执行
3. 提高线程的可管理性，性程是稀缺资源，如果无限制的创建，不仅会消耗系统资源，还会降低系统的稳定性，故使用线程池可以进行统一的分配，调用和监控，但是也要做到合理的利用线程池，所以要对线程池的原理了如指掌

### 12、cyclicbarrier和countdownlatch的区别
1. CountdownLatch阻塞主线程，等所有子线程完结了再继续下去，其计数器只能使用一次
2. Syslicbarrier阻塞一组线程，直至某个状态之后再全部同时执行，并且所有线程都被释放后，还能通过reset来重用

### 13、如何理解Java多线程回调方法？
客户程序C调用服务程序S中的某个方法A，然后S又在某个时候反过来调用C中的某个方法B，对于C来说，这个B便叫做回调方法。

### 14、概括的解释下线程的几种可用状态以及状态之间的关系
1. 新建状态(New)：线程实例化后还从未执行start()方法时的状态；
2. 就绪状态(Runnable)：调用线程的start()方法启动线程，start()方法创建线程运行的系统资源，并调度线程运行run()方法。当start()方法返回后，线程就处于就绪状态。
处于就绪状态的线程并不一定立即运行run()方法，线程还必须同其他线程竞争CPU时间，只有获得CPU时间才可以运行线程。因为在单CPU的计算机系统中，不可能同时运行多个线程，一个时刻仅有一个线程处于运行状态。因此此时可能有多个线程处于就绪状态。对多个处于就绪状态的线程是由Java运行时系统的线程调度程序(thread scheduler)来调度的。
3. 运行状态(Running)： 当线程获得CPU时间后，它才进入运行状态，真正开始执行run()方法
4. 阻塞状态(Blocked)：出现在某一个线程等待锁的时候。 所谓阻塞状态是正在运行的线程没有运行结束，暂时让出CPU，这时其他处于就绪状态的线程就可以获得CPU时间，进入运行状态
5. 死亡状态(Dead)： 有两个原因会导致线程死亡：
   1. run方法正常退出而自然死亡，
   2. 一个未捕获的异常终止了run方法而使线程猝死。

创建线程通过start方法进入就绪状态，获取cpu的执行权进入运行状态，失去cpu执行权会回到就绪状态，运行状态完成进入消亡状态，运行状态通过sleep方法和wait方法进入阻塞状态，休眠结束或者通过notify方法或者notifyAll方法释放锁进入就绪状态。

### 15、同步方法和同步代码块的区别是什么？
1. 语法不同，同步方法写在方法上
2. 同步块需要注明锁定对象，同步方法默认锁定this
3. 在静态方法中，都是默认锁定类对象
4. 在考虑性能方面，最好使用同步块来减少锁定范围提高并发效率。

### 16、在监视器(Monitor)内部，是如何做线程同步的？程序应该做哪种级别的同步？

* JVM基于进入和退出Monitor对象来实现方法同步和代码块同步，但两者的实现细节不一样。本质都是对一个对象的监视器（monitor）进行获取，而这个获取过程是排他的，也就是同一时刻只能有一个线程获取到由synchronized所保护对象的监视器

* 代码块同步是使用monitorenter和monitorexit指令实现的。monitorenter指令是在编译后插入到同步代码块的开始位置，而monitorexit是插入到方法结束处和异常处，JVM要保证每个monitorenter必须有对应的monitorexit与之配对。任何对象都有一个monitor与之关联，当且一个monitor被持有后，它将处于锁定状态。线程执行到monitorenter指令时，将会尝试获取对象所对应的monitor的所有权，即尝试获得对象的锁。

* java 还提供了显式监视器(Lock)和隐式监视器(synchronized)两种锁方案

### 17、sleep() 和 wait() 有什么区别？

1. sleep方法没有释放锁，但是wait方法释放了锁，使得其他线程可以使用同步控制块
2. sleep可以在任何地方使用，wait notify notifyall只能使用在同步控制块中
3. sleep必须捕获异常，其他不需要
4. sleep方法是Thread的静态方法，wait方法是Object类的普通方法

### 18、同步和异步有何异同，在什么情况下分别使用他们？举例说明

同步是安全的，异步是不安全的。同步是发送一个请求，等待返回，然后在发送一个请求。异步是发送一个请求，不用等待，随时可发送下一个请求

如果数据将在线程间共享。例如正在写的数据以后可能被另一个线程读到，或者正在读的数据可能已经被另一个线程写过了，那么这些数据就是共享数据，必须进行同步存取。

当应用程序在对象上调用了一个需要花费很长时间来执行的方法，并且不希望让程序等待方法的返回时，就应该使用异步编程，在很多情况下采用异步途径往往更有效率。

B-S模式中，使用Form表单提交数据，发送的就是同步请求，当响应返回后，才可以继续操作；

B-S模式中，使用Ajax向服务器端发送异步请求，在响应没有返回客户端时，客户端可以继续操作，当响应返回客户端后，就能显示结果

### 19、设计4个线程，其中两个线程每次对j增加1，另外两个线程对j每次减少1，使用内部类实现线程，对j增减的时候没有考虑顺序问题

```java
public class ManyThreads {

    private int j;

    public static void main(String[] args) {
        // TODO Auto-generated method stub
        ManyThreads many = new ManyThreads();
        Inc inc = many.new Inc();
        Dec dec = many.new Dec();
        for (int i = 0; i < 2; i++) {
            Thread t = new Thread(inc);
            t.start();
            t = new Thread(dec);
            t.start();
        }
    }

    private synchronized void inc() {
        j++;
        System.out.println(Thread.currentThread().getName() + "inc" + j);
    }

    private synchronized void dec() {
        j--;
        System.out.println(Thread.currentThread().getName() + "dec" + j);
    }

    class Inc implements Runnable {
        @Override
        public void run() {
            // TODO Auto-generated method stub
            for (int i = 0; i < 20; i++) {
                inc();
            }
        }
    }

    class Dec implements Runnable {
        @Override
        public void run() {
            // TODO Auto-generated method stub
            for (int i = 0; i < 20; i++) {
                dec();
            }
        }
    }
}
```

### 20、启动一个线程是用run()还是start()?
启动一个线程是调用start()方法，使线程所代表的虚拟处理机处于可运行状态，这意味着它可以由JVM调度并执行。这并不意味着线程就会立即运行。

### 21、请说出你所知道的线程同步的方法
1. sychronized同步方法，同步代码块
2. wait()和notify()。wait():使一个线程处于等待状态，并且释放所持有的对象的lock;notify():唤醒一个处于等待状态的线程，注意的是在调用此方法的时候，并不能确切的唤醒某一个等待状态的线程，而是由JVM确定唤醒哪个线程，而且不是按优先级
3. sleep():使一个正在运行的线程处于睡眠状态，是一个静态方法，调用此方法要捕捉InterruptedException异常
4. Lock接口的ReentranLock，通过lock()获取锁和unlock()释放锁，Condition对象中的await()和signal()类似于wait()和notify()方法
5. ThreadLocal为每一个线程绑定自己的私有数据；
6. volatile使变量在多个线程间可见。


### 22、stop()和suspend()方法为何不推荐使用？

* stop()方法停止线程释放锁将会给数据造成不一致的结果，如果在同步块执行一半时，stop来了，后面还没执行完呢，锁没了，线程退出了，别的线程又可以操作你的数据了，所以就是线程不安全了。
* suspend()方法暂停线程，使用resume()方法恢复线程的执行，如果使用不恰当，容易造成公共的同步对象的独占，发生死锁；也容易发生因为线程的暂停而导致数据不同步的情况。 

### 23、线程的sleep()方法和yield()方法有什么区别？
yield()：放弃当前CPU资源，将它让给其它的任务去占用CPU执行时间。但放弃的时间不确定，有可能刚刚放弃，马上又获得CPU时间片。
1. sleep()方法给其他线程运行机会时不考虑线程的优先级，因此会给低优先级的线程以运行的机会；yield()方法只会给相同优先级或更高优先级的线程以运行的机会；
2. 线程执行sleep()方法后转入阻塞（blocked）状态，而执行yield()方法后转入就绪（ready）状态；
3. sleep()方法声明抛出InterruptedException，而yield()方法没有声明任何异常；

### 24、当一个线程进入一个对象的synchronized方法A之后，其它线程是否可进入此对象的synchronized方法B？

不能。其它线程只能访问该对象的非同步方法，同步方法则不能进入。因为非静态方法上的synchronized修饰符要求执行方法时要获得对象的锁，如果已经进入A方法说明对象锁已经被取走，那么试图进入B方法的线程就只能在等锁池（注意不是等待池哦）中等待对象的锁。

## 6、锁
### 1、锁总结
[参考美团技术团队](https://tech.meituan.com/2018/11/15/java-lock.html)
![](https://awps-assets.meituan.net/mit-x/blog-images-bundle-2018b/7f749fc8.png)

**1. 乐观锁 VS 悲观锁**

JDBC编程笔记中有总结

**2. 自旋锁 VS 适应性自旋锁**

> 阻塞或唤醒一个Java线程需要操作系统切换CPU状态来完成，这种状态转换需要耗费处理器时间。如果同步代码块中的内容过于简单，状态转换消耗的时间有可能比用户代码执行的时间还要长。

* 自旋锁：
请求锁的线程不放弃CPU的执行时间进行自旋操作。
在许多场景中，同步资源的锁定时间很短，为了这一小段时间去切换线程，线程挂起和恢复现场的花费可能会让系统得不偿失。
自旋等待虽然避免了线程切换的开销，但它要占用处理器时间。如果锁被占用的时间很短，自旋等待的效果就会非常好。反之，如果锁被占用的时间很长，那么自旋的线程只会白浪费处理器资源


* 自适应的自旋锁（适应性自旋锁）：
自适应意味着自旋的时间（次数）不再固定，而是由前一次在同一个锁上的自旋时间及锁的拥有者的状态来决定。如果在同一个锁对象上，自旋等待刚刚成功获得过锁，并且持有锁的线程正在运行中，那么虚拟机就会认为这次自旋也是很有可能再次成功，进而它将允许自旋等待持续相对更长的时间。如果对于某个锁，自旋很少成功获得过，那在以后尝试获取这个锁时将可能省略掉自旋过程，直接阻塞线程，避免浪费处理器资源。

**3. 无锁 VS 偏向锁 VS 轻量级锁 VS 重量级锁**

jdk1.6对锁的实现引入了大量的优化，如自旋锁、适应性自旋锁、锁消除、锁粗化、偏向锁、轻量级锁等技术来减少锁操作的开销。锁主要存在四中状态，依次是：无锁状态、偏向锁状态、轻量级锁状态、重量级锁状态。

>偏向锁通过对比Mark Word解决加锁问题，避免执行CAS操作。而轻量级锁是通过用CAS操作和自旋来解决加锁问题，避免线程阻塞和唤醒而影响性能。重量级锁是将除了拥有锁的线程以外的线程都阻塞。

![](https://ws1.sinaimg.cn/large/d4556b75ly1g3ny0kv6tyj20jw065myt.jpg)
* java对象头
  
  synchronized用的锁是存在Java对象头里的。synchronized是悲观锁，在操作同步资源之前需要给同步资源先加锁，这把锁就是存在Java对象头里的。Hotspot的对象头主要包括两部分数据：Mark Word（标记字段）、Klass Pointer（类型指针）
  * Mark Word ：默认存储对象的HashCode，分代年龄和锁标志位信息
  * Klass Pointer ：对象指向它的类元数据的指针，虚拟机通过这个指针来确定这个对象是哪个类的实例
* Moniter

  Monitor是线程私有的数据结构，每一个被锁住的对象都会和一个monitor关联，同时monitor中有一个Owner字段存放拥有该锁的线程的唯一标识，表示该锁被这个线程占用
* 无锁

  无锁没有对资源进行锁定，所有的线程都能访问并修改同一个资源，但同时只有一个线程能修改成功。CAS原理及应用即是无锁的实现
* 偏向锁
  * 概念：
  指一段同步代码一直被一个线程所访问，那么该线程会自动获取锁，降低获取锁的代价。
  * 介绍：
  当一个线程访问同步代码块并获取锁时，会在Mark Word里存储锁偏向的线程ID。在线程进入和退出同步块时不再通过CAS操作来加锁和解锁，而是检测Mark Word里是否存储着指向当前线程的偏向锁。引入偏向锁是为了在无多线程竞争的情况下尽量减少不必要的轻量级锁执行路径，因为轻量级锁的获取及释放依赖多次CAS原子指令，而偏向锁只需要在置换ThreadID的时候依赖一次CAS原子指令即可。
* 轻量级锁
  * 概念：
  是指当锁是偏向锁的时候，被另外的线程所访问，偏向锁就会升级为轻量级锁，其他线程会通过自旋的形式尝试获取锁，不会阻塞，从而提高性能。
  * 介绍：
    * 在代码进入同步块的时候，如果同步对象锁状态为无锁状态（锁标志位为“01”状态，是否为偏向锁为“0”），虚拟机首先将在当前线程的栈帧中建立一个名为锁记录（Lock Record）的空间，用于存储锁对象目前的Mark Word的拷贝，然后拷贝对象头中的Mark Word复制到锁记录中。
     * 拷贝成功后，虚拟机将使用CAS操作尝试将对象的Mark Word更新为指向Lock Record的指针，并将Lock Record里的owner指针指向对象的Mark Word。
    * 如果这个更新动作成功了，那么这个线程就拥有了该对象的锁，并且对象Mark Word的锁标志位设置为“00”，表示此对象处于轻量级锁定状态。
    * 如果轻量级锁的更新操作失败了，虚拟机首先会检查对象的Mark Word是否指向当前线程的栈帧，如果是就说明当前线程已经拥有了这个对象的锁，那就可以直接进入同步块继续执行，否则说明多个线程竞争锁。
    * 若当前只有一个等待线程，则该线程通过自旋进行等待。但是当自旋超过一定的次数，或者一个线程在持有锁，一个在自旋，又有第三个来访时，轻量级锁升级为重量级锁。
* 重量级锁

  升级为重量级锁时，锁标志的状态值变为“10”，此时Mark Word中存储的是指向重量级锁的指针，此时等待锁的线程都会进入阻塞状态。

**4. 公平锁 VS 非公平锁**
>公平锁就是通过同步队列来实现多个线程按照申请锁的顺序来获取锁，从而实现公平的特性。非公平锁加锁时不考虑排队等待问题，直接尝试获取锁，所以存在后申请却先获得锁的情况。
* 公平锁
  * 概念 ：多个线程按照申请锁的顺序来获取锁，线程直接进入队列中排队，队列中的第一个线程才能获得锁
  * 优点：等待锁的线程不会饿死
  * 缺点：整体吞吐效率相对非公平锁要低，等待队列中除第一个线程以外的所有线程都会阻塞，CPU唤醒阻塞线程的开销比非公平锁大
* 非公平锁
  * 概念 ：多个线程加锁时直接尝试获取锁，获取不到才会到等待队列的队尾等待。但如果此时锁刚好可用，那么这个线程可以无需阻塞直接获取到锁，所以非公平锁有可能出现后申请锁的线程先获取锁的场景
  * 优点：可以减少唤起线程的开销，整体的吞吐效率高，因为线程有几率不阻塞直接获得锁，CPU不必唤醒所有线程
  * 缺点：处于等待队列中的线程可能会饿死，或者等很久才会获得锁
* ReentrantLock
  * ReentrantLock实现代码如下：
![](https://awps-assets.meituan.net/mit-x/blog-images-bundle-2018b/6edea205.png)
ReentrantLock里面有一个内部类Sync，Sync继承AQS（AbstractQueuedSynchronizer），添加锁和释放锁的大部分操作实际上都是在Sync中实现的。它有公平锁FairSync和非公平锁NonfairSync两个子类。ReentrantLoc默认使用非公平锁，也可以通过构造器来显示的指定使用公平锁。
  * 公平锁与非公平锁的lock()方法唯一的区别：
就在于公平锁在获取同步状态时多了一个限制条件：hasQueuedPredecessors()，主要是判断当前线程是否位于同步队列中的第一个。如果是则返回true，否则返回false
![](https://awps-assets.meituan.net/mit-x/blog-images-bundle-2018b/bc6fe583.png)

  * lock方法对比非公平锁， 新来的线程没有插队的机会， 所有来的线程必须扔到队列尾部， acquire方法也会像非公平锁一样首先调用tryAcquire插队试试，但是只有队列为空或着本身就是head，那么才可能成功，如果队列非空那么肯定被扔到队列尾部去了。

**5. 可重入锁 VS 非可重入锁**
* 可重入锁
  * 概念：是指在同一个线程在外层方法获取锁的时候，再进入该线程的内层方法会自动获取锁（前提锁对象得是同一个对象或者class），不会因为之前已经获取过还没释放而阻塞
  * 优点：一定程度上可以避免死锁
 
**6. 独享锁 VS 共享锁**
* 独享锁：也叫排他锁，是指该锁一次只能被一个线程所持有，如果线程T对数据A加上排它锁后，则其他线程不能再对A加任何类型的锁
* 共享锁：该锁可被多个线程所持有，如果线程T对数据A加上共享锁后，则其他线程只能对A再加共享锁，不能加排它锁
* ReentrantReadWriteLock
下图为ReentrantReadWriteLock的部分源码：
![](https://awps-assets.meituan.net/mit-x/blog-images-bundle-2018b/762a042b.png)
由代码可知：ReentrantReadWriteLock有两把锁：ReadLock和WriteLock，ReadLock和WriteLock是靠内部类Sync实现的锁。读锁是共享锁，写锁是独享锁，读锁的共享锁可保证并发读非常高效，而读写、写读、写写的过程互斥
ReentrantReadWriteLock中的state变量“按位切割”切分成了两个部分，高16位表示读锁状态（读锁个数），低16位表示写锁状态（写锁个数）。

**7. AQS**

笔记中有总结

### 2、讲一下非公平锁和公平锁在reetrantlock里的实现
[参考](https://blog.csdn.net/lsgqjh/article/details/63685058)

非公平锁: 当线程争夺锁的过程中，会先进行一次CAS尝试获取锁，若失败，则进入acquire(1)函数，进行一次tryAcquire再次尝试获取锁，若再次失败，那么就通过addWaiter将当前线程封装成node结点加入到Sync队列，这时候该线程只能乖乖等前面的线程执行完再轮到自己了。

公平锁: 当线程在获取锁的时候，会先判断Sync队列中是否有在等待获取资源的线程。若没有，则尝试获取锁，若有，那么就那么就通过addWaiter将当前线程封装成node结点加入到Sync队列中。

### 3、讲一下synchronized，可重入怎么实现
实现方法是为每个锁关联一个线程持有者Moniter和计数器status，当计数器为0时表示该锁没有被任何线程持有，那么任何线程都可能获得该锁而调用相应的方法；当某一线程请求成功后，JVM会记下锁的持有线程，并且将计数器置为1；此时其它线程请求该锁，则必须等待；而该持有锁的线程如果再次请求这个锁，就可以再次拿到这个锁，同时计数器会递增；当线程退出同步代码块时，计数器会递减，如果计数器为0，则释放该锁。

### 4、锁和同步的区别

1. Lock是一个接口，而synchronized是Java中的关键字
2. synchronized是内置的语言实现，synchronized是在JVM层面上实现的，不但可以通过一些监控工具监控synchronized的锁定，而且在代码执行时出现异常，JVM会自动释放锁定，但是使用Lock则不行，lock是通过代码实现的，要保证锁定一定会被释放，就必须将 unLock()放到finally{} 中
3. Lock可以让等待的线程响应中断，线程可以去做别的事情；synchronized不行，等待的线程会一直等下去，不能够响应中断
4. Lock可以知道是否获取到锁，知道锁的状态，而synchronized却无法办到
5. Lock可以提高多个线程进行读操作的效率。

### 5、什么是死锁(deadlock)？

死锁是指两个或两个以上的进程在执行过程中，由于竞争资源或者由于彼此通信而造成的一种阻塞的现象，若无外力作用，它们都将无法推进下去。此时称系统处于死锁状态或系统产生了死锁。
死锁产生有四个必要条件，打破任意一个，就能打破死锁状态:
1. 互斥条件: 一个资源每次只能被一个进程使用 
2. 请求与保持: 一个进程因请求资源而阻塞时，对已获得的资源保持不放 
3. 不剥夺: 进程已获得的资源，在末使用完之前，不能强行剥夺 
4. 循环等待: 若干进程之间形成一种头尾相接的循环等待资源关系

### 6、如何确保N个线程可以访问N个资源同时又不导致死锁？

死锁产生有四个必要条件，打破任意一个，就能打破死锁状态:
互斥条件、请求与保持、不剥夺和循环等待。

1. 指定获取锁的顺序，并强制线程按照指定的顺序获取锁。因此，如果所有的线程都是以同样的顺序加锁和释放锁，就不会出现死锁了。 缺点：需要手动对锁的获得顺序进行分析
2. 指定加锁时限：线程指定超时时间，若无法获得锁的占用权，进行回退操作，并释放已占用的锁，经一段延时后再尝试进行任务。缺点 ：线程过多的话，可能造成频繁回退，运行效率不高。
3. 死锁检测：将线程和已获得锁的情况记录下来，定时检测是否所有死锁现象（线程循环等待现象），回退处于死锁状态的线程，延时后，重试这些线程，与添加加锁时限类似，缺点也同。


### 7、ReentrantLock中公平锁和非公平锁在哪里体现的？
lock方法对比非公平锁， 没有了if else 也就意味着新来的线程没有插队的机会， 所有来的线程必须扔到队列尾部， acquire方法也会像非公平锁一样首先调用tryAcquire插队试试，但是只有队列为空或着本身就是head，那么才可能成功，如果 队列非空那么肯定被扔到队列尾部去了。

### 8、volatile的实现原理

[Java并发编程：volatile关键字解析](https://www.cnblogs.com/dolphin0520/p/3920373.html)

synchronized是一个重量级的锁，虽然JVM对它做了很多优化，而volatile则是轻量级的synchronized

指令重排序不会影响单个线程的执行，但是会影响到线程并发执行的正确性，也就是说，要想并发程序正确地执行，必须要保证原子性、可见性以及有序性。在Java里面，可以通过volatile关键字来保证一定的“有序性”。另外可以通过synchronized和Lock来保证有序性。

**volatile有两层语义：**
1. 保证可见性、不保证原子性
   >可见性：对一个 volatile 变量的读，总能看到（任意线程）对这个 volatile 变量最后的写入
   
   >原子性：对任意单个 volatile 变量的读/写具有原子性，但类似于 volatile++ 这种符合操作不具有原子性。
2. 禁止指令重排序

**volatile 写-读内存语义：**

1. 当写一个 volatile 变量时，JVM 会把该线程对应的本地内存中的共享变量值刷新到主内存。
2. 当读一个 volatile 变量时，JVM 会把该线程对应的本地内存值置为无效，线程接下来从主内存中读取共享变量值。

**volatile 重排序规则：**

1. volatile 写之前的操作不会被编译器重排序到 volatile 写之后；
2. volatile 读之后的操作不会被编译器重排序到 volatile 读之前；
3. 第一个操作是 volatile 写，第二个操作是 volatile 读时，不能重排序。

加入volatile关键字时，会多出一个lock前缀指令，
lock前缀指令实际上相当于一个内存屏障（内存栅栏），内存屏障会提供3个功能：
1. 它确保指令重排序时不会把其后面的指令排到内存屏障之前的位置，也不会把前面的指令排到内存屏障的后面；即在执行到内存屏障这句指令时，在它前面的操作已经全部完成；
2. 它会强制将对缓存的修改操作立即写入主存；
3. 如果是写操作，它会导致其他CPU中对应的缓存行无效。

**通常来说，使用volatile必须具备以下2个条件：**
1. 对变量的写操作不依赖于当前值
2. 该变量没有包含在具有其他变量的不变式中

**volatile场景：**
1. 状态标记量
2. double check，单例模式下的双重检查

## 7、JDK
### 1、Java中的LongAdder和AtomicLong的区别
### 2、JDK和JRE的区别是什么？

* jRE： (Java Runtime Environment) JRE顾名思义是java运行时环境，包含了java虚拟机，java基础类库。是使用java语言编写的程序运行所需要的软件环境，是提供给想运行java程序的用户使用的。
* JDK：(Java Development Kit) JDK顾名思义是java开发工具包，是程序员使用java语言编写java程序所需的开发工具包，是提供给程序员使用的。JDK包含了JRE，同时还包含了编译java源码的编译器javac，还包含了很多java程序调试和分析的工具：jconsole，jvisualvm等工具软件，还包含了java程序编写所需的文档和demo例子程序。
如果你需要运行java程序，只需安装JRE就可以了。如果你需要编写java程序，需要安装JDK。

### 3、java的跨平台

 java源程序先经过javac编译器编译成二进制的.class字节码文件（java的跨平台指的就是.class字节码文件的跨平台，.class字节码文件是与平台无关的），.class文件再运行在jvm上，java解释器（jvm的一部分）会将其解释成对应平台的机器码执行，所以java所谓的跨平台就是在不同平台上安装了不同的jvm，而在不同平台上生成的.class文件都是一样的，而.class文件再由对应平台的jvm解释成对应平台的机器码执行

### 4、机器码和字节码的区别

* 机器码，完全依附硬件而存在，并且不同硬件由于内嵌指令集不同，即使相同的0 1代码意思也可能是不同的，换句话说，根本不存在跨平台性。比如：不同型号的CPU,你给他个指令10001101，他们可能会解析为不同的结果；
* java字节码是java的.class文件,我们知道JAVA是跨平台的，为什么呢？因为他有一个jvm,不论那种硬件，只要你装有jvm,那么他就认识这个JAVA字节码，至于底层的机器码，咱不用管，有jvm搞定，他会把字节码再翻译成所在机器认识的机器码

## 8、反射
### 1、反射的实现与作用

JAVA语言编译之后会生成一个.class文件，反射就是通过字节码文件找到某一个类、类中的方法以及属性等。反射的实现主要借助以下四个类：Class：类的对象，Constructor：类的构造方法，Field：类中的属性对象，Method：类中的方法对象。 

作用：反射机制指的是程序在运行时能够获取自身的信息。在JAVA中，只要给定类的名字，那么就可以通过反射机制来获取类的所有信息。


## 9、JVM
### 1、JVM回收算法和回收器，CMS采用哪种回收算法，怎么解决内存碎片问题？

* 回收算法：
  * 标记-清除算法：
  1. 方法：首先标记出所有需要回收的对象，在标记完成后统一回收所有被标记的对象
  2. 缺点：
     1. 效率问题，标记和清除二个过程的效率都不高；
     2. 空间问题，标记清除后会产生大量的不连续的内存碎片；
  * 复制算法
  1. 方法：将内容按容量划分为大小相等的两块，每次只使用其中的一块。当这一块的内存用完了，就将还存活的内存对象复制到另外一块上面，然后把已经使用过的内存空间一次性清理掉；
  2. 缺点：
     1. 对象存活率较高时就要进行较多的复制操作，效率将会变低；
     2. 每次只能使用一半内容，代价较高；
  * 标记-整理算法： 首先标记出所有需要回收的对象，在标记完成后让所有存活的对象都向一端移动，然后直接清理掉边界以外的内存；
  * 分代收集算法： 据对象的存活周期的不同将内存划分为几块，一般就分为新生代和老年代，根据各个年代的特点采用不同的收集算法。新生代（少量存活）用复制算法，老年代（对象存活率高）“标记-清理”算法或标记-清除算法


* 回收器：
* 新生代回收器：
  1. Serial：单线程，进行垃圾收集时，需暂停掉其它所有的用户线程，新生代复制算法，老年代标记-整理算法
  2. ParNew：Serial收集器的多线程版本，需暂停掉其它所有的用户线程，新生代复制算法，老年代标记-整理算法，目前只能与CMS收集器配合工作
  3. Parallel Scavenge：多线程并行，复制算法，“吞吐量优先”的收集器。吞吐量就是CPU用于运行用户代码的时间与总CPU总消耗时间的比值，即吞吐量=运行用户代码时间/（运行用户代码时间+垃圾回收时间）。并行是指同一时刻一起执行，并发是指同一时刻间隔执行。
* 老年代回收器：
  1. Serial Old：Serial的老年代版本，单线程，与Parallel Scavenge搭配使用，或作为CMS收集器的后备预案，新生代复制算法，老年代标记-整理算法
  2. Parallel Old：Parallel Scavenge的老年代版本，注重吞吐量以及CPU资源敏感的场合，都可以优先考虑Parallel Scavenge加Parallel Old收集器
  3. CMS：获取最短停顿时间为目标，尤其重视服务的响应速度，基于标记-清除算法；
    解决内存碎片问题： 让CMS在进行一定次数的Full GC（标记清除）的时候进行一次标记整理算法，CMS提供了以下参数来控制：-XX:UseCMSCompactAtFullCollection   -XX:CMSFullGCBeforeCompaction=5 也就是CMS在进行5次Full GC（标记清除）之后进行一次标记整理算法，从而可以控制老年带的碎片在一定的数量以内，甚至可以配置CMS在每次Full GC的时候都进行内存的整理；
  4. G1：并行的、并发的和增量式压缩短暂停顿的垃圾收集器。G1收集器不区分年轻代和年老代空间。它把堆空间划分为多个大小相等的区域。当进行垃圾收集时，它会优先收集存活对象较少的区域，因此叫“Garbage First”。

### 2、JVM分区

1. 程序计数器：字节码行号指示器，字节码解释器工作时就是通过改变这个计数器的值来选取下一条需要执行的字节码指令，线程私有；
2. 虚拟机栈：java方法执行的内存模型，每个方法执行的同时会创建一个栈帧，用于存放局部变量表、操作数栈、动态链接、方法出口等信息，每一个方法从调用到完成的过程，都对应着一个栈帧在虚拟机栈中入栈到出栈的过程，线程私有；
3. 本地方法栈：存放虚拟机使用到的Native方法信息；
4. 方法区：线程共享，存储已被虚拟机加载的类信息、常量、静态变量，即时编译后的代码数据等。运行时常量池是方法区的一部分，存放编译期生成的各种字面量和符号引用；
5. 堆：线程共享，存放对象实例，垃圾收集管理的主要区域，java堆细分为新生代和老年代

### 3、eden区，survial区

[新生代Eden与两个Survivor区的解释](https://www.jianshu.com/p/534ab3c8335f)

~~目前主流的虚拟机实现都采用了分代收集的思想，把整个堆区划分为新生代和老年代；新生代又被划分成Eden 空间、 From Survivor 和 To Survivor 三块区域。新生代有一个较大的Eden区和两个较小的Survivor区组成，绝大多数新创建的对象都是在Eden区分配的，其中大多数对象很快消亡。Eden是一块连续的内存，所以分配内存的速度很快。首先，Eden满时，进行一次minor gc ，将存活 的对象复制到 To Survivor（以下简称To），清除Eden消亡的对象。当Eden再次满时，进行minor gc,To中能够晋升的移动到老年代，存活的对象复制到From。清空Eden和To，如此切换（默认15），将存活的对象迁移到老年代。~~

HotSpot JVM把年轻代分为了三部分：1个Eden区和2个Survivor区（分别叫from和to）。默认比例为8：1。

一般情况下，新创建的对象都会被分配到Eden区(一些大对象特殊处理),这些对象经过第一次Minor GC后，如果仍然存活，将会被移到Survivor区。对象在Survivor区中每熬过一次Minor GC，年龄就会增加1岁，当它的年龄增加到一定程度时，就会被移动到年老代中

在GC开始的时候，对象只会存在于Eden区和名为“From”的Survivor区，Survivor区“To”是空的。紧接着进行GC，Eden区中所有存活的对象都会被复制到“To”，而在“From”区中，仍存活的对象会根据他们的年龄值来决定去向。年龄达到一定值(年龄阈值，可以通过-XX:MaxTenuringThreshold来设置)的对象会被移动到年老代中，没有达到阈值的对象会被复制到“To”区域。经过这次GC后，Eden区和From区已经被清空。这个时候，“From”和“To”会交换他们的角色，也就是新的“To”就是上次GC前的“From”，新的“From”就是上次GC前的“To”。不管怎样，都会保证名为To的Survivor区域是空的。



### 4、JAVA虚拟机的作用

解释运行字节码程序消除平台相关性。 jvm将java字节码解释为具体平台的具体指令。一般的高级语言如要在不同的平台上运行，至少需要编译成不同的目标代码。而引入JVM后，Java语言在不同平台上运行时不需要重新编译。Java语言使用模式Java虚拟机屏蔽了与具体平台相关的信息，使得Java语言编译程序只需生成在Java虚拟机上运行的目标代码（字节码），就可以在多种平台上不加修改地运行。Java虚拟机在执行字节码时，把字节码解释成具体平台上的机器指令执行。

### 5、GC中如何判断对象需要被回收

1. 首先，进行可达性算法分析，可达性算法基本思路是定义一些列称为"GC-Roots"的对象作为起始阶段，从这些节点向下搜索，搜索走过的路径称为引用链，当一个对象到GCRoots没有任何引用链时，即从GCRoots到这个对象不可达，则证明此对象是不可用的；
2. 其次，可达性算法中的不可达对象在真正宣告“死亡”需要回收之前，至少要经过两轮标记过程：
   1. 如果对象不可达，会被第一次标记并且进行一次筛选，筛选条件是此对象有没有必要执行finalize()方法，当对象没有覆盖finalize()方法或者这个方法以及被执行过了，那么就视为没有必要再执行；对于那些有必要执行finalize()方法的对象会被放在一个队列F-Queue中，稍后由虚拟机的一个线程去执行逐一执行队列中对象的finalize方法
   2. finalize()方法是对象逃脱死亡命运的最后一次机会，稍后GC会对F-Queue中的对象进行第二次小规模的标记，如果能在finalize中成功重新引用，第二次标记时就会将该对象从F-Queue集合中移除，而成功脱逃，否则就判定为该对象可回收。

### 6、JAVA虚拟机中，哪些可作为ROOT对象？

1. 虚拟机栈（栈帧中的本地变量表）中引用的对象
2. 方法区中的类静态属性引用的对象
3. 方法区中常量引用的对象
4. 本地方法栈中JNI（即一般说的native方法）引用的对象。

### 7、Java内存模型是什么？JVM内存模型呢？

**Java内存模型**

线程间共享变量存储在主内存，每个线程都有自己的本地内存，存储的是共享变量在本地的副本。线程对变量的所有操作都必须在工作内存中进行，不同线程也无法访问到对方工作内存中的变量，线程间变量值的传递都需要经过主内存来完成

**JVM内存模型：**

[Java内存与垃圾回收调优](https://my.oschina.net/kanlianhui/blog/356650)

JVM内存模型：虚拟机栈、本地方法栈、方法区、堆、程序计数器

![](http://cdn1.importnew.com/2014/12/ba45c5c11b55f2cc224cd098e7f4b038.png)

### 8、jvm是如何实现线程？

java虚拟机的多线程是通过线程轮流切换分配处理执行时间的方式来实现的，在任何一个确定的时刻，一个处理器（对于多核处理器来说是一个内核）都只会执行一条程序中的指令。因此，为了线程切换后能恢复到正确的执行位置，每条线程都需要一个独立的程序计数器，各条线程之间计数器互不影响，独立存储。

简单点说，对于单核处理器，是通过快速切换线程执行指令来达到多线程的，因为单核处理器同时只能处理一条指令，只是这种切换速度很快，我们根本不会感知到。

### 9、jvm最大内存限制多少

VM内存的最大值跟操作系统有很大的关系， 限制于实际的最大物理内存。简单的说就32位处理器虽然可控内存空间有4GB,但是具体的操作系统会给一个限制，这个限制一般是2GB-3GB（一般来说Windows系统下为1.5G-2G，Linux系统 下为2G-3G），而64bit以上的处理器就不会有限制了。 JVM主要管理两种类型的内存：堆和非堆。
1. 堆内存分配 ：JVM初始分配的内存由-Xms指定，默认是物理内存的1/64；JVM最大分配的内存由-Xmx 指定，默认是物理内存的1/4。默认空余堆内存小于40%时，JVM就会增大堆直到-Xmx的最大限制；空余堆内存大于70%时，JVM会减少堆直到- Xms的最小限制。因此服务器一般设置-Xms、-Xmx相等以避免在每次GC 后调整堆的大小。 
2. 非堆内存分配： JVM使用-XX:PermSize设置非堆内存初始值，默认是物理内存的1/64；由XX:MaxPermSize设置最大非堆内存的大小，默认是物理内存的1/4。 

### 10、什么是Java虚拟机？为什么Java被称作是“平台无关的编程语言”？

java虚拟机是执行字节码文件（.class）的虚拟机进程。java源程序（.java）被编译器编译成字节码文件（.class）。然后字节码文件，将由java虚拟机，解释成机器码（不同平台的机器码不同）。利用机器码操作硬件和操作系统。

因为不同的平台装有不同的JVM，它们能够将相同的.class文件，解释成不同平台所需要的机器码。正是因为有JVM的存在，java被称为平台无关的编程语言。

### 11、描述一下JVM加载class文件的原理机制？

JVM中类的装载是由ClassLoader和它的子类来实现的,Java ClassLoader 是一个重要的Java运行时系统组件。它负责在运行时查找和装入类文件的类。 Java中的所有类，都需要由类加载器装载到JVM中才能运行。类加载器本身也是一个类，而它的工作就是把class文件从硬盘读取到内存中。在写程序的时候，我们几乎不需要关心类的加载，因为这些都是隐式装载的，除非我们有特殊的用法，像是反射，就需要显式的加载所需要的类。 

类装载方式，有两种：
1. 隐式装载，程序在运行过程中当碰到通过new 等方式生成对象时，隐式调用类装载器加载对应的类到jvm中
2. 显式装载，通过class.forname()等方法，显式加载需要的类 

隐式加载与显式加载的区别：两者本质是一样的。 Java类的加载是动态的，它并不会一次性将所有类全部加载后再运行，而是保证程序运行的基础类(像是基类)完全加载到jvm中，至于其他类，则在需要的时候才加载。这当然就是为了节省内存开销。

### 12、内存分配与回收策略

1. 对象优先在Eden区分配。当Eden区没有内存可分配的时候，虚拟机发出一次Minor GC（垃圾回收）；
2. 大对象直接进入老年代。大对象指需要大量连续内存空间的java对象，典型的很长的字符串以及数组；
3. 长期存活的对象进入老年代。虚拟机为每一个对象定义一个对象年龄计数器，对象在Survivor区中每熬过一次Minor GC，年龄就增加 1 岁，当年龄增加到一定程度（默认15岁），就将会被晋升到老年代中；
4. 动态对象年龄判断。如果在Surivivor空间中相同年龄对象大小的总和大于Surivivor空间的一半，年龄大于或者等于该年龄的对象直接进入老年代；
5. 空间分配担保。

### 13、JVM调优？

[JVM调优浅谈](https://www.cnblogs.com/xingzc/p/5756119.html)

[Java内存与垃圾回收调优](https://my.oschina.net/kanlianhui/blog/356650)

**堆大小设置：**
  * 典型设置：
  1. java -Xmx3550m  -Xms3550m -Xmn2g  -Xss128k
  2. java  -Xmx3550m  -Xms3550m  -Xss128k  -XX:NewRatio=4  -XX:SurvivorRatio=4  -XX:MaxPermSize=16m  -XX:MaxTenuringThreshold=0
  
    | 命令     | 含义
    ----------|-------------
    -Xmx3550m       | 设置JVM最大可用内存为3550m
    -Xms3550m        | 设置JVM初始内存为3550m。此值可以设置与 -Xmx相同，以避免每次垃圾回收完成后JVM重新分配内存
    -Xmn2g | 设置年轻代大小为2G
    -Xss128k|设置每个线程的堆栈大小， 根据应用的线程所需内存大小进行调整
    -XX:NewRatio=4|设置年轻代（包括Eden和两个Survivor区）与年老代的比值（除去持久代）。设置为4，则年轻代与年老代所占比值为1:4，年轻代占整个堆栈的1/5。
    -XX:SurvivorRatio=4|设置年轻代中Eden区与Survivor区的大小比值。设置为4，则两个Survivor区与一个Eden区的比值为2:4，一个Survivor区占整个年轻代的1/6。
    -XX:MaxPermGen=16m|设置永久代最大值为16m。
    -XX:MaxTenuringThreshold=0|设置垃圾最大年龄。如果设置为0的话，则年轻代对象不经过Survivor区，直接进入年老代 
    -XX:PermGen|设置永久代内存的初始化大小。


**选择合适的垃圾收集算法：**

  * 吞吐量优先的并行收集器：
    1. java  -Xmx3800m  -Xms3800m  -Xmn2g  -Xss128k  -XX:+UseParallelGC  -XX:ParallelGCThreads=20
    2. java  -Xmx3550m  -Xms3550m  -Xmn2g  -Xss128k  -XX:+UseParallelGC  -XX:ParallelGCThreads=20 -XX:+UseParallelOldGC
     3. 还可以加入参数  -XX:MaxGCPauseMillis=100：设置每次年轻代垃圾回收的最长时间，如果无法满足此时间，JVM会自动调整年轻代大小，以满足此值

  * 响应时间优先的并发收集器：
    1. 典型配置：java  -Xmx3550m  -Xms3550  -Xmn2g  -Xss128k  -XX:ParallelGCThreads=20  -XX:+UseConcMarkSweepGC  -XX:+UseParNewGC
    2. 还可以使用参数  -XX:CMSFullGCsBeforeCompaction=5 ： 由于并发收集器不对内存空间进行压缩、整理，所以运行一段时间后会产生“碎片”，使得运行效率降低。此值设置运行多少次GC以后对内存空间进行压缩、整理。
-XX:+UseCMSCompactAtFullCollection ： 打开对年老代的压缩。可能会影响性能，但是可以消除碎片

    参数 | 含义
    ---|---
     -XX:+UseParallelGC|选择垃圾收集器为并行收集器。此配置仅对年轻代有效。 而年老代仍旧使用串行收集
    -XX:ParallelGCThreads=20|配置并行收集器的线程数
    -XX:+UseParallelOldGC|配置年老代垃圾收集方式为并行收集。 JDK6.0支持对年老代并行收集
    -XX:+UseConcMarkSweepGC|设置年老代为并发收集
    -XX:+UseParNewGC|设置年轻代为并行收集。可与CMS收集同时使用

    | | 适用情况|缺点|如何配置
    ---|---|---|---
    串行处理器|数据量比较小（100M左右），单处理器下并且对相应时间无要求的应用|只能用于小型应用|使用 -XX:+UseSerialGC
    并行处理器|对吞吐量有高要求，多CPU，对应用过响应时间无要求的中、大型应用。如后台处理、科学计算|垃圾收集过程中应用响应时间可能加长|使用-XX:+UseParallelGC 打开；最大垃圾回收暂停：指定垃圾回收时的最长暂停时间，通过-XX:MaxGCPauseMillis=<N>指定。 吞吐量：吞吐量为垃圾回收时间与非垃圾回收时间的比值，通过-XX:GCTimeRatio = <N> 来设定， 公式为 1/(1 + N)
    并发处理器|对响应时间有高要求，多CPU，对应用响应时间有较高要求的中大型应用。如Web服务器/应用服务器||使用 -XX:+UseConcMarkSweepGC打开

**java垃圾收集监控：**

[JAVA VisualVM介绍以及IDEA下使用](https://blog.csdn.net/qq_22741461/article/details/80451675)

1. IDEA安装VisualVM插件，之后运行工程的时候选择`Run With VisualVM`
2. 本地安装VisualVM，之后启动进入`VisualVM`页面，安装`java VisualVM`插件，之后在左侧便可以选择监视的相应IDE（例如idea或者eclipse）

之后便可以看到监控数据：

![](https://upload-images.jianshu.io/upload_images/13925206-9ecdf3da53f80e0b.png?imageMogr2/auto-orient/)

整个界面分为三个区域，分别为：Spaces、Graphs和Histogram：

[Visual GC 插件使用](https://www.jianshu.com/p/9e4ccd705709)

* **Spaces窗口：**

  ![](https://upload-images.jianshu.io/upload_images/13925206-1799221d7e7cfa8c.png?imageMogr2/auto-orient/)
  
  上图呈现了程序运行时我们比较关注的几个区域的内存使用情况：
  * Metaspace：方法区，如果JDK1.8之前的版本，就是Perm，JDK7和之前的版本都是以永久代(PermGen)来实现方法区的，JDK8之后改用元空间来实现(MetaSpace)。
  * Old：老年代
  * Eden: 新生代Eden区
  * S0和S1：新生代的两个 Survivor 区

* **Graphs窗口：**

  该窗口区域包含8个图标，以时间为横坐标动态展示各个指标的运行状态。

  ![](https://upload-images.jianshu.io/upload_images/13925206-d18f2631954ef5b3.png?imageMogr2/auto-orient/)

  * Compile Time：编译情况，包括编译总数和编译耗时，一个脉冲表示一次JIT编译；
  * Class Loader Time：类加载情况，包括加载的类，卸载的类以及耗时
  * GC Time：总的（包含新生代和老年代）gc情况记录
  * Eden Space：新生代Eden区内存使用情况，包括Eden区的最大容量、当前容量、当前已使用容量、从开始监控到现在该内存区域一共发生的 Minor GC 次数以及 GC 耗时情况
  * Survivor 0和Survivor 1：新生代的两个Survivor区内存使用情况
  * Old Gen：老年代内存使用情况
  * Metaspace：方法区内存使用情况

* **Histogram窗口：**

  Histogram窗口是对当前正在被使用的Survivor区内存使用情况的详细描述

  * Tenuring Threshold：晋升到老年代的年龄阈值，但是有动态年龄判断情况出现
  * Max Tenuring Threshold：表示新生代中对象的最大年龄值



**Java垃圾回收调优：**

[一次针对idea启动的JVM调优过程记录](https://www.jianshu.com/p/12adb143f149)

为了能看到idea运行时的gc日志，添加如下参数输出gc日志

```
-verbose:gc
-XX:+PrintGCDetails
-Xloggc:D:/gc.log
```
接下来打开VisualVM工具，准备监控idea。

* 如果在gc日志看到大量 Minor GC 信息，是由于年轻代空间不足而导致内存分配失败（Allocation Failure）而发起的，解决方案就是扩大新生代容量，以减少Minor GC发生的次数

* 观察堆空间的变化曲线图，
  idea的初始堆空间分配如下：
  ```
  -Xms 128m
  -Xmx 750m
  ```
  当内存占用过高时启动垃圾回收，虚拟机为了减少过于频繁的垃圾回收，会对堆空间进行扩容。
如果看到堆内容扩容次数较多，说明初始堆空间设置的过小，可以将初始值跟最大值一样大，防止因为堆扩容引发的消耗。

* 老年代空间设置过小或者Matespace（元空间）空间不足都会发生Full GC。

  如果Matespace的初始值非常小，程序在启动过程中由于空间不足会发生多次的扩容。如果在日志中看到`[Full GC (Metadata GC Threshold)`，说明这次的Full GC发生是由于Metadata GC Threshold导致的，因为元空间内存不足够而产生扩容导致的GC。通过参数`-XX MetaspaceSize`可以设置一个足够大的元空间初始容量

[理解CMS GC日志](https://www.jianshu.com/p/ba768d8e9fec)

[GC 性能优化文集](http://cmsblogs.com/?p=3819)

* 如果你在日志里看到 java.lang.OutOfMemoryError: PermGen space错误，表达的意思是: 永久代(Permanent Generation) 内存区域已满，主要原因,是加载到内存中的 class 数量太多或体积太大。那么可以尝试使用 -XX:PermGen 和 -XX:MaxPermGen JVM选项去监控并增加Perm Gen内存空间。

* 如果你在日志里看到 java.lang.OutOfMemoryError: Java heap space错误，主要是由代码问题导致的：
  * 超出预期的访问量/数据量
  * 内存泄露(Memory leak)

  解决方案：
  如果设置的最大内存不满足程序的正常运行, 只需要增大堆内存即可。但很多情况下, 增加堆内存空间并不能解决问题，要从根本上解决问题, 则需要排查分配内存的代码. 简单来说, 需要解决这些问题:
  1. 哪类对象占用了最多内存？
  2. 这些对象是在哪部分代码中分配的。

* 如果你在日志里看到 java.lang.OutOfMemoryError: Metaspace 错误所表达的信息是: 元数据区(Metaspace) 已被用满，Metaspace 错误的主要原因, 是加载到内存中的 class 数量太多或者体积太大。

  如果抛出与 Metaspace 有关的 OutOfMemoryError , 第一解决方案是增加 Metaspace 的大小. 使用下面这样的启动参数:
  ```
  -XX:MaxMetaspaceSize=512m
  ```
  
  

### 14、类加载机制，双亲委派模型，好处是什么？如何破坏双亲委派模型？应用场景？
[参考网址1](https://www.jianshu.com/p/60dbd8009c64)
[参考网址2](https://blog.csdn.net/yangcheng33/article/details/52631940)

* 概念：
  * 类加载机制：虚拟机把描述类的数据从Class文件加载到内存，并对数据进行校验，转化解析和初始化，最终形成可以被虚拟机直接使用的Java类型，这就是虚拟机的类加载机制。类加载的全过程包括加载、验证、准备、解析和初始化五个阶段。
  * 双亲委派模型：每次收到类加载请求时，先将请求委派给父类加载器完成，如果父类加载器无法完成加载，那么子类尝试自己加载

* 优点 ：采用双亲委派的一个好处是： 双亲委派模型很好地解决了各个类加载器的基础类统一问题 (越基础的类由越上层的加载器进行加载）。

  对于任意一个类，都需要由加载它的类加载器和这个类本身来一同确立其在Java虚拟机中的唯一性。如果不是同一个类加载器加载，即时是相同的class文件，也会出现判断不想同的情况，从而引发一些意想不到的情况，为了保证相同的class文件，在使用的时候，是相同的对象，jvm设计的时候，采用了双亲委派的方式来加载类。

  比如加载位于rt.jar包中的类java.lang.Object，不管是哪个加载器加载这个类，最终都是委托给顶层的启动类加载器进行加载，这样就保证了使用不同的类加载器最终得到的都是同样一个Object对象

* jvm提供了三种系统加载器：
  * 启动类加载器（Bootstrap ClassLoader）：C++实现，在java里无法获取，负责加载/lib下的类。
  * 扩展类加载器（Extension ClassLoader）： Java实现，可以在java里获取，负责加载/lib/ext下的类。
  * 系统类加载器/应用程序类加载器（Application ClassLoader）：是与我们接触对多的类加载器，我们写的代码默认就是由它来加载，ClassLoader.getSystemClassLoader返回的就是它。

* 如何打破：需要重写loadClass()方法，双亲委派模型主要体现在ClassLoader类中的 loadClass()方法中：

```java
  protected Class<?> loadClass(String name, boolean resolve)
        throws ClassNotFoundException
    {
        synchronized (getClassLoadingLock(name)) {
            Class<?> c = findLoadedClass(name);
            if (c == null) {
                long t0 = System.nanoTime();
                try {
                    //双亲委派模型的体现
                    if (parent != null) {
                        c = parent.loadClass(name, false);
                    } else {
                        c = findBootstrapClassOrNull(name);
                    }
                } catch (ClassNotFoundException e) {
                    // ClassNotFoundException thrown if class not found
                    // from the non-null parent class loader
                }
              .......
            }
            return c;
        }
    }
```
* 应用场景： Java中所有涉及SPI的加载动作基本上都采用这种方式，例如JNDI、JDBC、JCE、JAXB和JBI等， 也就是父类加载器请求子类加载器去完成类加载动作。

  例如JDBC中，引入线程上下文件类加载器， 程序就可以把原本需要由启动类加载器进行加载的类，由应用程序类加载器去进行加载了。
Java SPI机制：为某个接口寻找服务实现的机制。有点类似IOC的思想，就是将装配的控制权移到程序之外。




## 10、GC
### 1、java中内存泄露是啥，什么时候出现内存泄露？内存溢出？

* 内存泄露
  * 概念：不再会被使用的对象的内存不能被回收，就是内存泄露。
  * 场景：长生命周期的对象持有短生命周期对象的引用就很可能发生内存泄露，尽管短生命周期对象已经不再需要，但是因为长生命周期对象持有它的引用而导致不能被回收，例如：
     1. 集合类。集合类仅仅有添加元素的方法，而没有相应的删除机制，导致内存被占用。如果这个集合类如果仅仅是局部变量，根本不会造成内存泄露，在方法栈退出后就没有引用了会被jvm正常回收。而如果这个集合类是全局性的变量（比如类中的静态属性，全局性的map等即有静态引用或final一直指向它），那么没有相应的删除机制，很可能导致集合所占用的内存只增不减，因此提供这样的删除机制或者定期清除策略非常必要。
    2. 单例模式。不正确使用单例模式是引起内存泄露的一个常见问题，单例对象在被初始化后将在JVM的整个生命周期中存在（以静态变量的方式），如果单例对象持有外部对象的引用，那么这个外部对象将不能被jvm正常回收，导致内存泄露
* 内存溢出out of memory
  * 概念：是指程序在申请内存时，没有足够的内存空间供其使用，出现out of memory，包括：
    1. 方法区内存溢出（outOfMemoryError：permgem space）方法区主要存放的是类信息、常量、静态变量等。所以如果程序加载的类过多，或者使用反射、gclib等这种动态代理生成类的技术，就可能          导致该区发生内存溢出
    2. 线程栈溢出（java.lang.StackOverflowError）线程栈时线程独有的一块内存结构，所以线程栈发生问题必定是某个线程运行时产生的错误。 一般线程栈溢出是由于递归太深或方法调用层级过多导致的。
  * 引起原因：
     1. 内存中加载的数据量过于庞大，如一次从数据库取出过多数据；
     2. 代码中存在死循环或循环产生过多重复的对象实体；
     3. 集合类中有对对象的引用，使用完后未清空，使得JVM不能回收；
  * 解决方案：
    1. 修改JVM启动参数，直接增加内存。(-Xms，-Xmx参数一定不要忘记加。)
    2. 检查错误日志，查看“OutOfMemory”错误前是否有其它异常或错误。
    3. 对代码进行排查和分析，找出可能发生内存溢出的位置。

### 2、minor gc如果运行的很频繁，可能是什么原因引起的，minorgc如果运行的很慢，可能是什么原因引起的?

运行的很频繁可能是因为：
1. 产生了太多朝生夕灭的对象导致需要频繁minor gc
2. 新生代空间设置的比较小

运行的很频繁可能是因为：
1. 新生代空间设置过大。
2. 对象引用链较长，进行可达性分析时间较长。
3。 新生代survivor区设置的比较小，清理后剩余的对象不能装进去需要移动到老年代，造成移动开销。
4. 内存分配担保失败，由minor gc转化为full gc
5. 采用的垃圾收集器效率较低，比如新生代使用serial收集器

### 3、阐述GC算法

同JVM回收算法，标记清除算法、复制算法、标记整理算法和分代收集算法

### 4、GC是什么? 为什么要有GC?

GC是垃圾回收。

内存处理是编程人员容易出现问题的地方，忘记或错误的内存回收，会导致程序或系统不稳，甚至崩溃。Java的GC功能可自动监控对象是否超过作用域，从而达到自动回收内存的目的。Java语言没有提供释放已分配的显示操作方法。

### 5、垃圾回收的优点和原理。并考虑2种回收机制
[参考](https://www.cnblogs.com/pypua/articles/8779469.html)

* 优点：垃圾回收机制使得java程序员在编写程序的时候不再需要考虑内存管理。 有效的防止了内存泄露，可以有效的使用可使用的内存。 
* 原理： 当创建对象时，GC就开始监视这个对象的地址、大小以及使用情况。通常，GC采用有向图的方式记录和管理heap（堆）中的素有对象。通过这种方式确定哪些对象时“可达的”，哪些是“不可达的”。垃圾回收器通常作为一个单独的低级别的线程运行，在不可预知的情况下对内存堆中已经死亡的或很长时间没有用过的对象进行清除和回收， 程序员不能实时的对某个对象或所有对象调用垃圾回收器进行垃圾回收。
* 回收机制：分代复制垃圾回收和标记垃圾回收，增量垃圾回收。

### 6、垃圾回收器可以马上回收内存吗？有什么办法主动通知虚拟机进行垃圾回收？（垃圾回收）
可以马上回收内存。

程序员可以手动执行System.gc()，通知GC运行，但是Java语言规范并不保证GC一定会执行。

## 1、IO和NIO、AIO
### 1、怎么打印日志？
### 2、运行时异常与一般异常有何异同？
### 3、error和exception有什么区别?
### 4、给我一个你最常见到的runtime exception
### 5、Java中的异常处理机制的简单原理和应用。
### 6、java中有几种类型的流？JDK为每种类型的流提供了一些抽象类以供继承，请说出他们分别是哪些类？
### 7、什么是java序列化，如何实现java序列化？
### 8、运行时异常与受检异常有什么区别？
