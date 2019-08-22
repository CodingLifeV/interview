<!-- TOC -->

- [Java 基础](#java-基础)
    - [为什么重写 equals 还要重写 hashcode](#为什么重写-equals-还要重写-hashcode)
    - [说一下 map 的分类和常见的情况](#说一下-map-的分类和常见的情况)
    - [Object 若不重写 hashCode()的话，hashCode()如何计算出来的？](#object-若不重写-hashcode的话hashcode如何计算出来的)
    - [==比较的是什么？](#比较的是什么)
    - [若对一个类不重写，它的 equals()方法是如何比较的？](#若对一个类不重写它的-equals方法是如何比较的)
    - [java8 新特性](#java8-新特性)
    - [说说 Lamda 表达式的优缺点。](#说说-lamda-表达式的优缺点)
    - [一个十进制的数在内存中是怎么存的？](#一个十进制的数在内存中是怎么存的)
    - [为啥有时会出现 4.0-3.6=0.40000001 这种现象？](#为啥有时会出现-40-36040000001-这种现象)
    - [Java 支持的数据类型有哪些？什么是自动拆装箱？](#java-支持的数据类型有哪些什么是自动拆装箱)
    - [什么是值传递和引用传递？](#什么是值传递和引用传递)
    - [数组(Array)和列表(ArrayList)有什么区别？什么时候应该使用 Array 而不是 ArrayList？](#数组array和列表arraylist有什么区别什么时候应该使用-array-而不是-arraylist)
    - [你了解大 O 符号(big-Onotation)么？你能给出不同数据结构的例子么？](#你了解大-o-符号big-onotation么你能给出不同数据结构的例子么)
    - [String 是最基本的数据类型吗?](#string-是最基本的数据类型吗)
    - [int 和 Integer 有什么区别？](#int-和-integer-有什么区别)
    - [String、StringBuffer、StringBuffer，什么时候会走 StringBuilder？](#stringstringbufferstringbuffer什么时候会走-stringbuilder)
    - [我们在 web 应用开发过程中经常遇到输出某种编码的字符，如 iso8859-1 等，如何输出一个某种编码的字符串？](#我们在-web-应用开发过程中经常遇到输出某种编码的字符如-iso8859-1-等如何输出一个某种编码的字符串)
    - [&和&&的区别？](#和的区别)
    - [在 Java 中，如何跳出当前的多重嵌套循环？](#在-java-中如何跳出当前的多重嵌套循环)
    - [你能比较一下 Java 和 JavaSciprt 吗？](#你能比较一下-java-和-javasciprt-吗)
    - [正则表达式](#正则表达式)
    - [请你说说 Java 和 PHP 的区别？](#请你说说-java-和-php-的区别)
    - [Java 语法糖](#java-语法糖)
- [关键字](#关键字)
    - [介绍一下 Syncronized 锁，如果用这个关键字修饰一个静态方法，锁住了什么？如果修饰成员方法，锁住了什么？](#介绍一下-syncronized-锁如果用这个关键字修饰一个静态方法锁住了什么如果修饰成员方法锁住了什么)
    - [锁有了解嘛，说一下 Synchronized 和 lock](#锁有了解嘛说一下-synchronized-和-lock)
    - [讲一讲 Java 里面的 final 关键字怎么用的？](#讲一讲-java-里面的-final-关键字怎么用的)
- [面向对象](#面向对象)
    - [wait 方法底层原理](#wait-方法底层原理)
    - [Java 有哪些特性，举个多态的例子](#java-有哪些特性举个多态的例子)
    - [String 为啥不可变？String 能继承吗？](#string-为啥不可变string-能继承吗)
    - [类和对象的区别](#类和对象的区别)
    - [请列举你所知道的 Object 类的方法](#请列举你所知道的-object-类的方法)
    - [重载(Overload)和重写(Override)的区别？相同参数不同返回值能重载吗？Overload 的方法是否可以改变返回值的类型](#重载overload和重写override的区别相同参数不同返回值能重载吗overload-的方法是否可以改变返回值的类型)
    - [static 关键字是什么意思？Java 中是否可以覆盖(override)一个 private 或者是 static 的方法？](#static-关键字是什么意思java-中是否可以覆盖override一个-private-或者是-static-的方法)
    - [静态变量存在哪?](#静态变量存在哪)
    - [讲讲什么是泛型？](#讲讲什么是泛型)
    - [解释 extends 和 super 泛型限定符-上界不存下界不取](#解释-extends-和-super-泛型限定符-上界不存下界不取)
    - [是否可以在 static 环境中访问非 static 变量？](#是否可以在-static-环境中访问非-static-变量)
    - [谈谈如何通过反射创建对象？](#谈谈如何通过反射创建对象)
    - [Java 支持多继承么？](#java-支持多继承么)
    - [接口和抽象类的区别是什么？](#接口和抽象类的区别是什么)
    - [Comparable 和 Comparator 接口是干什么的？列出它们的区别](#comparable-和-comparator-接口是干什么的列出它们的区别)
    - [面向对象的特征有哪些方面](#面向对象的特征有哪些方面)
    - [final, finally, finalize 的区别](#final-finally-finalize-的区别)
    - [Static Nested Class（嵌套类） 和 Inner Class（内部类）的不同](#static-nested-class嵌套类-和-inner-class内部类的不同)
    - [当一个对象被当作参数传递到一个方法后，此方法可改变这个对象的属性，并可返回变化后的结果，那么这里到底是值传递还是引用传递?](#当一个对象被当作参数传递到一个方法后此方法可改变这个对象的属性并可返回变化后的结果那么这里到底是值传递还是引用传递)
    - [Java 的接口和 C++的虚类的相同和不同处。](#java-的接口和-c的虚类的相同和不同处)
    - [JAVA 语言如何进行异常处理，关键字：throws,throw,try,catch,finally 分别代表什么意义？在 try 块中可以抛出异常吗？](#java-语言如何进行异常处理关键字throwsthrowtrycatchfinally-分别代表什么意义在-try-块中可以抛出异常吗)
    - [内部类可以引用他包含类的成员吗？有没有什么限制？](#内部类可以引用他包含类的成员吗有没有什么限制)
    - [两个对象值相同(x.equals(y) == true)，但却可有不同的 hash code 说法是否正确？](#两个对象值相同xequalsy--true但却可有不同的-hash-code-说法是否正确)
    - [如何通过反射获取和设置对象私有字段的值？](#如何通过反射获取和设置对象私有字段的值)
    - [谈一下面向对象的"六原则一法则"](#谈一下面向对象的六原则一法则)
    - [请问 Query 接口的 list 方法和 iterate 方法有什么区别？](#请问-query-接口的-list-方法和-iterate-方法有什么区别)
    - [Java 中，什么是构造函数？什么是构造函数重载？什么是复制构造函数？](#java-中什么是构造函数什么是构造函数重载什么是复制构造函数)
- [集合](#集合)
    - [ConcurrentHashMap？ConcurrentSkipListMap？二者的区别](#concurrenthashmapconcurrentskiplistmap二者的区别)
    - [hashMap？](#hashmap)
    - [如果 hashMap 的 key 是一个自定义的类，怎么办？](#如果-hashmap-的-key-是一个自定义的类怎么办)
    - [ArrayList 和 LinkedList 的区别，如果一直在 list 的尾部添加元素，用哪个效率高？](#arraylist-和-linkedlist-的区别如果一直在-list-的尾部添加元素用哪个效率高)
    - [TreeMap 底层，红黑树原理？](#treemap-底层红黑树原理)
    - [ArrayList 是否会越界？](#arraylist-是否会越界)
    - [Java 集合类框架的基本接口有哪些？](#java-集合类框架的基本接口有哪些)
    - [为什么集合类没有实现 Cloneable 和 Serializable 接口？](#为什么集合类没有实现-cloneable-和-serializable-接口)
    - [什么是迭代器？](#什么是迭代器)
    - [Iterator 和 ListIterator 的区别是什么？](#iterator-和-listiterator-的区别是什么)
    - [快速失败(fail-fast)和安全失败(fail-safe)的区别是什么？](#快速失败fail-fast和安全失败fail-safe的区别是什么)
    - [HashMap 和 Hashtable 有什么区别？](#hashmap-和-hashtable-有什么区别)
    - [ArrayList 和 LinkedList 有什么区别？](#arraylist-和-linkedlist-有什么区别)
    - [ArrayList,Vector,LinkedList 的存储性能和特性是什么？](#arraylistvectorlinkedlist-的存储性能和特性是什么)
    - [Collection 和 Collections 的区别](#collection-和-collections-的区别)
    - [List、Map、Set 三个接口存取元素时，各有什么特点？](#listmapset-三个接口存取元素时各有什么特点)
- [JDK](#jdk)
    - [Java 中的 LongAdder 和 AtomicLong 的区别](#java-中的-longadder-和-atomiclong-的区别)
    - [JDK 和 JRE 的区别是什么？](#jdk-和-jre-的区别是什么)
    - [java 的跨平台](#java-的跨平台)
    - [机器码和字节码的区别](#机器码和字节码的区别)
- [反射](#反射)
    - [反射的实现与作用](#反射的实现与作用)
- [IO 和 NIO、AIO](#io-和-nioaio)
    - [怎么打印日志？](#怎么打印日志)
    - [运行时异常与一般异常有何异同？](#运行时异常与一般异常有何异同)
    - [error 和 exception 有什么区别?](#error-和-exception-有什么区别)
    - [给我一个你最常见到的 runtime exception](#给我一个你最常见到的-runtime-exception)
    - [Java 中的异常处理机制的简单原理和应用。](#java-中的异常处理机制的简单原理和应用)
    - [java 中有几种类型的流？JDK 为每种类型的流提供了一些抽象类以供继承，请说出他们分别是哪些类？](#java-中有几种类型的流jdk-为每种类型的流提供了一些抽象类以供继承请说出他们分别是哪些类)
    - [什么是 java 序列化，如何实现 java 序列化？](#什么是-java-序列化如何实现-java-序列化)
    - [运行时异常与受检异常有什么区别？](#运行时异常与受检异常有什么区别)

<!-- /TOC -->

# Java 基础

## 为什么重写 equals 还要重写 hashcode

[为什么要重写 hashcode 和 equals 方法？初级程序员在面试中很少能说清楚。](https://www.cnblogs.com/JavaArchitect/p/10474448.html)

Object 类默认的 equals 比较规则就是比较两个对象的内存地址， 默认的 hashcode 方法是根据对象的内存地址经哈希算法得来的，因此，二个对象 equals 相等，hashcode 一定相等。

hashmap 中通过 hashcode 值来定位存储的索引号，如果处于相同索引位置但存在冲突，则在通过 equal 方法来比较二个对象是否相同。

根据对象的某种性质重写了 equals 方法后，为了保证同一个对象，保证 equals 相同的情况下 hashcode 值必定相同，如果重写了 equals 而未重写 hashcode 方法，可能就会出现两个没有关系的对象 equals 相同的（因为 equal 都是根据对象的特征进行重写的），但 hashcode 确实不相同的。
如果你改写了 equal()方法，令两个实际不是一个对象的两个实例在逻辑上相等了，但是 hashcode 却是不等。所以要记得改写 hashcode。

因为重写的 equal 里一般比较的比较全面比较复杂，这样效率就比较低，而利用 hashCode()进行对比，则只要生成一个 hash 值进行比较就可以了，效率很高，那么 hashCode()既然效率这么高为什么还要 equal()呢？因为 hashCode()并不是完全可靠，有时候不同的对象他们生成的 hashcode 也会一样（生成 hash 值得公式可能存在的问题），此时产生冲突，需要通过 equal 方法解决，所以 hashCode()只能说是大部分时候可靠，并不是绝对可靠，所以我们可以得出：

1. equal()相等的两个对象他们的 hashCode()肯定相等，也就是用 equal()对比是绝对可靠的。
2. hashCode()相等的两个对象他们的 equal()不一定相等，也就是 hashCode()不是绝对可靠的。

## 说一下 map 的分类和常见的情况

Java 为数据结构中的映射定义了一个接口 java.util.Map，此接口主要有四个常用的实现类，分别是 HashMap、Hashtable、LinkedHashMap 和 TreeMap

- HashMap：它根据键的 hashCode 值存储数据，大多数情况下可以直接定位到它的值，因而具有很快的访问速度，但遍历顺序却是不确定的。 HashMap 最多只允许一条记录的键为 null，允许多条记录的值为 null。HashMap 非线程安全，即任一时刻可以有多个线程同时写 HashMap，可能会导致数据的不一致。如果需要满足线程安全，可以用 Collections 的 synchronizedMap 方法使 HashMap 具有线程安全的能力，或者使用 ConcurrentHashMap。
- Hashtable：Hashtable 是遗留类，很多映射的常用功能与 HashMap 类似，不同的是它承自 Dictionary 类，并且是线程安全的，任一时间只有一个线程能写 Hashtable，并发性不如 ConcurrentHashMap，因为 ConcurrentHashMap 引入了分段锁。Hashtable 不建议在新代码中使用，不需要线程安全的场合可以用 HashMap 替换，需要线程安全的场合可以用 ConcurrentHashMap 替换。
- LinkedHashMap：LinkedHashMap 是 HashMap 的一个子类，保存了记录的插入顺序，在用 Iterator 遍历 LinkedHashMap 时，先得到的记录肯定是先插入的，也可以在构造时带参数，按照访问次序排序。
- TreeMap：TreeMap 实现 SortedMap 接口，能够把它保存的记录根据键排序，默认是按键值的升序排序，也可以指定排序的比较器，当用 Iterator 遍历 TreeMap 时，得到的记录是排过序的。如果使用排序的映射，建议使用 TreeMap。在使用 TreeMap 时，key 必须实现 Comparable 接口或者在构造 TreeMap 传入自定义的 Comparator，否则会在运行时抛出 java.lang.ClassCastException 类型的异常。

对于上述四种 Map 类型的类，要求映射中的 key 是不可变对象。不可变对象是该对象在创建后它的哈希值不会被改变。如果对象的哈希值发生变化，Map 对象很可能就定位不到映射的位置了。

## Object 若不重写 hashCode()的话，hashCode()如何计算出来的？

Object 的 hashcode 方法是本地方法，也就是用 c 语言或 c++ 实现的，该方法直接返回对象的内存地址。

## ==比较的是什么？

对于对象引用类型:“==”比较的是对象的内存地址。
对于基本类型数据，其实比较的是它的值。

## 若对一个类不重写，它的 equals()方法是如何比较的？

如果没有对 equals 方法进行重写，则比较的是引用类型的变量所指向的对象的地址；诸如 String、Date 等类对 equals 方法进行了重写的话，比较的是所指向的对象的内容。

## java8 新特性

1. Lambda 表达式 − Lambda 允许把函数作为一个方法的参数（函数作为参数传递进方法中）
2. 接口的默认方法和静态方法 − 可以在接口中定义默认方法，使用 default 关键字，并提供默认的实现。所有实现这个接口的类都会接受默认方法的实现，除非子类提供的自己的实现
3. 方法引用 − 方法引用使得开发者可以直接引用现存的方法、Java 类的构造方法或者实例对象。可以与 lambda 联合使用
4. 重复注解- 注解有一个很大的限制是：在同一个地方不能多次使用同一个注解。Java 8 打破了这个限制，引入了重复注解的概念，允许在同一个地方多次使用同一个注解
   ...... 等等（重点 lambda 表达式）

## 说说 Lamda 表达式的优缺点。

- 优点：1. 简洁; 2. 非常容易并行计算; 3. 可能代表未来的编程趋势
- 缺点：1. 若不用并行计算，很多时候计算速度没有比传统的 for 循环快。（并行计算有时需要预热才显示出效率优势）2. 不容易调试。3. 若其他程序员没有学过 lambda 表达式，代码不容易让其他语言的程序员看懂。

## 一个十进制的数在内存中是怎么存的？

二进制补码形式
[原码补码反码介绍](https://www.cnblogs.com/wangsiting/p/7339192.html)

## 为啥有时会出现 4.0-3.6=0.40000001 这种现象？

2 进制的小数无法精确的表达 10 进制小数，计算机在计算 10 进制小数的过程中要先转换为 2 进制进行计算，这个过程中出现了误差。

## Java 支持的数据类型有哪些？什么是自动拆装箱？

八个基本数据类型：byte，short，int，long，float，double，char，boolean；以及引用类型，引用类型包括类类型、接口类型和数组。整数默认 int 型，小数默认是 double 型，float、long 类型必须加后缀 f、l；

自动装箱和拆箱就是基本类型和其对应引用类型之间的转换，基本类型转换为引用类型后，就可以直接调用包装类中封装好的一些方法
![](https://ws1.sinaimg.cn/large/d4556b75ly1g3mteb1k1kj20l00eidgb.jpg)

## 什么是值传递和引用传递？

[参考网址](https://www.cnblogs.com/xiaoxiaoyihan/p/4883770.html)

- 值传递，在方法的调用过程中，实参把它的实际值传递给形参，此传递过程就是将实参的值复制一份传递到函数中，这样如果在函数中对该值（形参的值）进行了操作将不会影响实参的值。
- 引用传递，将对象的地址值传递过去，函数接收的是原始值的首地址值。在方法的执行过程中，形参和实参的内容相同，指向同一块内存地址，也就是说操作的其实都是源数据，所以方法的执行将会影响到实际对象

## 数组(Array)和列表(ArrayList)有什么区别？什么时候应该使用 Array 而不是 ArrayList？

Array 可以包含基本类型和对象类型，ArrayList 只能包含对象类型。 Array 大小是固定的，ArrayList 的大小是动态变化的。
ArrayList 提供了更多的方法和特性，比如:addAll()，removeAll()，iterator()等等。

对于基本类型数据，集合使用自动装箱来减少编码工作量。但是，当处理固定大小的基本数据类型的时候，这种方式相对比较慢。

## 你了解大 O 符号(big-Onotation)么？你能给出不同数据结构的例子么？

O 表示算法的时间或者空间复杂度上界。比如数组的插入时间复杂度为 O(N),空间复杂度为 O(1),链表的插入时间复杂度为 O(1),空间复杂度为 O(1)

## String 是最基本的数据类型吗?

不是，基本数据类型包括：byte,short,int,long,float,double,boolean,char。而 String 是类代表字符串，属于引用类型，所谓引用类型包括：类，接口，数组...

## int 和 Integer 有什么区别？

[参考网址](http://www.cnblogs.com/liuling/archive/2013/05/05/intAndInteger.html)

Ingeter 是 int 的包装类，int 的初值为 0，Ingeter 的初值为 null。java 可以通过自动拆箱和装箱对 int 和 Integer 进行转化。

## String、StringBuffer、StringBuffer，什么时候会走 StringBuilder？

三者区别：

1. String 为字符串常量，每次对 string 操作都会产生一个新的对象，而 StringBuilder 和 StringBuffer 均为字符串变量，即 String 对象一旦创建之后该对象是不可更改的，但后两者的对象是变量，是可以更改的。因此在运行速度快慢为：StringBuilder > StringBuffer > String
2. 在线程安全上，StringBuilder 是线程不安全的，而 StringBuffer 是线程安全的
3. String 适用于少量的字符串操作的情况；StringBuilder 适用于单线程下在字符缓冲区进行大量操作的情况；StringBuffer 适用多线程下在字符缓冲区进行大量操作的情况

以下情况走 StringBuilder：

[String 字符串拼接问题，到底什么时候会走 StringBuilder？](https://www.jianshu.com/p/a80c9b2b89cd)

1. 通过变量和字符串拼接，java 是需要先到内存找变量对应的值，才能进行完成字符串拼接的工作，这种方式 java 编译器没法优化，只能走 StringBuilder 进行拼接字符串，然后调用 toString 方法。当然返回的结果和常量池中的字符串的内存地址是不一样的。
2. 直接在表达式里写值，java 不用根据变量去内存里找对应的值，可以在编译的时候直接对这个表达式进行优化，不用走 StringBilder，优化后的表达式直接指向常量池的字符串

## 我们在 web 应用开发过程中经常遇到输出某种编码的字符，如 iso8859-1 等，如何输出一个某种编码的字符串？

通过 new 一个字符串对象，把原始编码和需要输出编码类型传进构造器中

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

## &和&&的区别？

1. Java 中&&和&都是表示与的逻辑运算符，都表示逻辑运输符 and，当两边的表达式都为 true 的时候，整个运算结果才为 true，否则为 false。
2. &&的短路功能，当第一个表达式的值为 false 的时候，则不再计算第二个表达式；&则两个表达式都执行。
3. &可以用作位运算符，当&两边的表达式不是 Boolean 类型的时候，&表示按位操作。

## 在 Java 中，如何跳出当前的多重嵌套循环？

在 Java 中，要想跳出多重循环，可以在外面的循环语句前定义一个标号，
然后在里层循环体的代码中使用带有标号的 break 语句，即可跳出外层循环

## 你能比较一下 Java 和 JavaSciprt 吗？

1. 基于对象和面向对象：Java 是一种真正的面向对象的语言，即使是开发简单的程序，必须设计对象；JavaScript 是种脚本语 言，它可以用来制作与网络无关的，与用户交互作用的复杂软件。它是一种基于对 象（Object Based）和事件驱动（Event Driver）的编程语言。因而它本身提供了非常丰富的内部对象供设计人员使用；
2. 解释和编译：Java 的源代码在执行之前，必须经过编译；JavaScript 是一种解释性编程语言，其源代码不需经过编译，由浏览器解释执行；
3. 强类型变量和类型弱变量： Java 采用强类型变量检查，即所有变量在编译之前必须作声明；JavaScript 中变量声明，采用其弱类型。即变量在使用前不需作声明，而是解释器在运行时检查其数据类型；
4. 代码格式不一样。

## 正则表达式

1. 概念：
   在编写处理字符串的程序时，经常会有查找符合某些复杂规则的字符串的需要。正则表达式就是用于描述这些规则的工具。换句话说，正则表达式就是记录文本规则的代码。
2. java 与正则相关的工具主要在 java.util.regex 包中；此包中主要有两个类：Pattern、Matcher

- Pattern：
  Pattern 类表示正则表达式对象，用于创建一个正则表达式,也可以说创建一个匹配模式,它的构造方法是私有的,不可以直接创建,但可以通过 Pattern.complie(String regex)简单工厂方法创建一个正则表达式
  pattern() 方法返回正则表达式的字符串形式,其实就是返回 Pattern.complile(String regex)的 regex 参数

```java
Pattern p=Pattern.compile("\\w+");
p.pattern();//返回 \w+
```

- Matcher：Matcher 对象是对输入字符串进行解释和匹配操作的引擎与 Pattern 类一样，Matcher 也没有公共构造方法。你需要调用 Pattern 对象的 matcher 方法来获得一个 Matcher 对象。

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

## 请你说说 Java 和 PHP 的区别？

1. Java 是一种静态类型语言（强类型语言），需要编译后才能执行；PHP 是一种动态类型语言（弱类型语言），不需要编译即可执行。
2. java 使用封装继承，最小的单位是类，php 作为脚本，最小单位就是语句，用两者输出 hello world 就知道了，所以 java 语法比较严格，而 php 很灵活
3. java 是自动内存分配回收，php 是一次创建一次销毁。
4. java 可以常驻内存，多线程;php 无法常驻内存，也没有线程的概念。
5. PHP:就是为 web 而生的语言，除了 web 什么都做不了，这既是它的缺点，也是它的优点，语法简洁灵活，和 java 冗长的语法正好形成对比
6. java 已经是一门很成熟的语言，或者说其语言的进一步提升已经不可能能了，php 是在 web 繁荣之后兴起的语言，所以语言成熟度没有 java 高。

## Java 语法糖

**switch 支持 String 与枚举**

Java 中的 swith 自身原本就支持基本类型。比如 int、char 等。对于 int 类型，直接进行数值的比较。对于 char 类型则是比较其 ascii 码，Java 7 中 switch 开始支持 String。

字符串的 switch 是通过 equals() 和 hashCode() 方法来实现的，反编译：

```java
public static void main(String args[])
{
    String str = "world";
    String s;
    switch((s = str).hashCode())
    {
    default:
        break;
    case 99162322:
        if(s.equals("hello"))
            System.out.println("hello");
        break;
    case 113318802:
        if(s.equals("world"))
            System.out.println("world");
        break;
    }
}
```

**泛型**

对于 Java 虚拟机来说，他根本不认识 Map<String, String> map 这样的语法。需要在编译阶段通过类型擦除的方式进行解语法糖。

**自动装箱与拆箱**

Integer 和 int 之间：在装箱的时候自动调用的是 Integer 的 `valueOf(int)` 方法。而在拆箱的时候自动调用的是 Integer 的 `intValue` 方法。

**方法变长参数**

可变参数在被使用的时候，他首先会创建一个数组，数组的长度就是调用该方法时传递的实参的个数，然后再把参数值全部放到这个数组当中，然后再把这个数组作为参数传递到被调用的方法中

**枚举**

当我们使用 enmu 来定义一个枚举类型的时候，编译器会自动帮我们创建一个 final 类型的类继承 Enum 类，所以枚举类型不能被继承

**内部类**

内部类之所以也是语法糖，是因为它仅仅是一个编译时的概念，outer.java 里面定义了一个内部类 inner，一旦编译成功，就会生成两个完全不同的 .class 文件了，分别是 outer.class 和 outer\$inner.class。所以内部类的名字完全可以和它的外部类名字相同。

**for-each**

for-each 的实现原理其实就是使用了普通的 for 循环和迭代器。

其它还有： 断言、条件编译、数值字面量、Lambda 表达式等

[Java 语法糖详解](https://www.hollischuang.com/archives/3655)

# 关键字

## 介绍一下 Syncronized 锁，如果用这个关键字修饰一个静态方法，锁住了什么？如果修饰成员方法，锁住了什么？

Syncronized 锁是同步锁，如果关键字修饰静态方法的话是一个类锁（当前类的所有线程都必须等待同步线程执行）， 如果关键字修饰成员方法的话是一个对象锁（当前对象的所有进程必须等待同步进程执行完，释放锁）。

## 锁有了解嘛，说一下 Synchronized 和 lock

1. Lock 是一个接口，而 synchronized 是 Java 中的关键字，synchronized 是内置的语言实现；
2. synchronized 可以用来修饰方法代码块，Lock 的话需要它的一些实现类来做到加锁和解锁比如 ReentrantLock、 ReentrantReadWriteLock
3. synchronized 在发生异常时，会自动释放线程占有的锁，因此不会导致死锁现象发生；而 Lock 在发生异常时，如果没有主动通过 unLock()去释放锁，则很可能造成死锁现象，因此使用 Lock 时需要在 finally 块中释放锁；
4. Lock 可以让等待锁的线程响应中断，通过调用方法 lock.lockInterruptibly(),而 synchronized 却不行，使用 synchronized 时，等待的线程会一直等待下去，不能够响应中断；
5. 通过 Lock 可以知道有没有成功获取锁，而 synchronized 却无法办到。
6. Lock 可以提高多个线程进行读操作的效率。
7. 在性能上来说，如果竞争资源不激烈，两者的性能是差不多的，而当竞争资源非常激烈时（即有大量线程同时竞争），此时 Lock 的性能要远远优于 synchronized。

## 讲一讲 Java 里面的 final 关键字怎么用的？

1. 修饰类：表示该类不能被继承；
2. 修饰方法：表示方法不能被重写；
3. 修饰变量：表示变量只能赋值一次且赋值以后值不能被修改（常量）。

# 面向对象

## wait 方法底层原理

Object 中的方法，可以暂停线程，期间会释放对象锁，不像 sleep 方法，线程休眠期依然持有锁，wait 方法的线程，必须调用 notify 或 notifyAll 方法唤醒线程。

## Java 有哪些特性，举个多态的例子

封装、继承以及多态，其中方法的重写和重载都和多态有关。 多态的主要特征就是父类引用指向子类对象，生活中的例子：Animal animal = new Dog();

## String 为啥不可变？String 能继承吗？

Sting 是这样定义的：public final class String extends Object，里边有 final 关键字，所以不可变也不能被继承，同时 string 底层是字符串数组也是 final 修饰，这样做首先是安全，比如 hashset 中用 string 做为键，不会出现 string 变化，导致违反唯一键。另外节约内存

```java
public final class String
    implements java.io.Serializable, Comparable<String>, CharSequence {
    /** The value is used for character storage. */
    private final char value[];
  ...
}
```

## 类和对象的区别

类是抽象的结果，也是一种数据结构，类里面有属性、方法、代码块、构造器这些是类的基本元素。如果想使用类 ，那么你需要创建一个具体的对象，才能够正常使用类里面的属性和方法，同时，也有专门属于类的属性和方法， 属于类的东西， 可以没有对象也可以使用。由此可见对象是从类创建而来。

## 请列举你所知道的 Object 类的方法

1. getClass():用于返回当前运行时对象的 Class 对象，使用了 final 关键字修饰，故不允许子类重写
2. equals():用于比较两个对象的地址是否相同，即两个引用是否指向同一个对象；
3. clone():用于创建并返回当前对象的一份拷贝；
4. toString():返回类的名字@实例的哈希码的 16 进制字符串；
5. notify():唤醒等待队列中的其中一个线程；notifyAll():唤醒线程等待队列中的所有线程；
6. wait(long timeout):让一个线程等待一段时间。

## 重载(Overload)和重写(Override)的区别？相同参数不同返回值能重载吗？Overload 的方法是否可以改变返回值的类型

相同参数不同返回值不可以重载,重载可以改变返回值的类型，重载的方法不能根据返回类型进行区分

- 重写：一个类是继承一个父类时，从父类那儿继承来的方法，进行重新写过。
- 重载：多个同名方法，名称相同，但是参数不同，可以通过参数来识别调用的是哪一个方法。

## static 关键字是什么意思？Java 中是否可以覆盖(override)一个 private 或者是 static 的方法？

static 是静态的意思，被 static 修饰的变量，在内存中只有一份，被所有对象共享，static 修饰额方法叫静态方法，从属于类，可以通过类调用，也可以通过对象调用，方法中不能访问非静态变量和方法。

静态，就是禁止多态。所以不能重写 static 方法。 private 是私有的，肯定不能重写了。

## 静态变量存在哪?

方法区，静态变量是共享内容，栈是不共享的，堆存放 new 关键字创建的对象实例，方法区是共享的区域，它用于存储已被虚拟机加载的类信息，常量，静态变量，即时编译后的代码等数据

## 讲讲什么是泛型？

泛型是一种参数化类型，它的<>里面可以放任何类型，而且不要强转，它是多态的一种体现。 泛型多用于容器中，往容器中方数据，事先约定什么类型数据，放的时候会检查，不是正确的类型放入时会报错，这样可以建立安全的数据，也避免了强制类型转换。

泛型也是 Java 提供的语法糖,只不过是将类型检查从运行期提到编译器.运行时都会被擦除为 Object.,运行的时候都会在方法的入口和出口进行转换(就是发生擦除的边界位置),

## 解释 extends 和 super 泛型限定符-上界不存下界不取

extends 上限通配符，用来限制类型的上限，只能传入本类和子类，add 方法受阻，可以从一个数据类型里获取数据；

```java
List<? extends Number> eList = null;
eList = new ArrayList<Integer>();
eList = new ArrayList<Long>();
```

super 下限通配符，用来限制类型的下限，只能传入本类和父类，get 方法受阻，可以把对象写入一个数据结构里；

```java
List<? super Integer> sList = null;
sList = new ArrayList<Number>();
```

## 是否可以在 static 环境中访问非 static 变量？

不可以在 static 环静中，不可以访问非 static。因为静态的成员属于类，随着类的加载而加载到静态方法区内存，当类加载时，此时不一定有实例创建，没有实例，就不可以访问非静态的成员。类的加载先于实例的创建，因此静态环境中，不可以访问非静态。

## 谈谈如何通过反射创建对象？

[参考网址](https://www.cnblogs.com/qjlbky/p/5929452.html)

1. 通过默认的构造器通过 Class 的 newInstance()方法来获取
2. 通过指定的构造器来创建

```java
Class clazz = Class.forName(className);

 //1.通过Class获取指定构造方法，比如带两个参数
Constructor cons =clazz.getConstructor(String.class,int.class);//拿的是公有的

//2.通过指定的构造器对象进行对象的初始化。
Object obj = cons.newInstance("lisisi",23);
```

## Java 支持多继承么？

java 只支持单继承，这是由于安全性的考虑，如果子类继承的多个父类里面有相同的方法或者属性，子类将不知道具体要继承哪个，而接口可以多实现，是因为接口只定义方法，而没有具体的逻辑实现，多实现也要重新实现方法。

## 接口和抽象类的区别是什么？

1. 接口的方法默认是 public，所有方法在接口中不能有实现，抽象类可以有非抽象的方法， 可以由 public protected 或者默认修饰。 java1.8 以前接口中方法不能有方法体，1.8 以后可以由 default 关键字修 饰，从而可以拥有方法体。
2. 接口中的实例变量默认是 final 类型的，而抽象类中则不一定
3. 一个类可以实现多个接口，但最多只能实现一个抽象类
4. 一个类实现接口的话要实现接口的所有方法，而抽象类不一定

## Comparable 和 Comparator 接口是干什么的？列出它们的区别

1. Comparable & Comparator 接口都可以用来实现集合中元素的比较、排序。
2. Comparator 位于包 java.util 下，而 Comparable 位于包 java.lang 下
3. Comparable 接口将比较代码嵌入自身类中，而后者在一个独立的类中实现比较。像 Integer、String 等这些基本类型的 JAVA 封装类都已经实现了 Comparable 接口，这些类对象本身就支持自比较，直接调用 Collections.sort()就可以对集合中元素的排序，无需自己去实现 Comparable 接口。而有些自定义类的 List 序列，当这个对象不支持自比较或者自比较函数不能满足你的要求时，你可以写一个比较器来完成两个对象之间大小的比较，也就是指定使用 Comparator（临时规则排序，也称作专门规则排序），如果不指定 Comparator，那么就用自然规则排序，这里的自然顺序就是实现 Comparable 接口设定的排序方式。
4. java 集合的工具类 Collections 中提供了两种排序的方法,分别是:

- Collections.sort(List list)
- Collections.sort(List list,Comparator c)

  第一种称为自然排序,参与排序的对象需实现 comparable 接口,重写其 compareTo()方法,方法体中实现对象的比较大小规则；

  第二种叫定制排序,或自定义排序,需编写匿名内部类,先 new 一个 Comparator 接口的比较器对象 c,同时实现 compare()其方法。

## 面向对象的特征有哪些方面

1. 封装： 面向对象的封装就是把描述一个对象的属性和行为的代码封装在一个“模块”中，也就是一个类中，属性用变量定义，行为用方法进行定义，方法可以直接访问同一个对象中的属性
2. 继承： 在定义和实现一个类的时候，可以在一个已经存在的类的基础之上来进行，把这个已经存在的类所定义的内容作为自己的内容，并可以加入若干新的内容，或修改原来的方法使之更适合特殊的需要，这就是继承。继承是子类自动共享父类数据和方法的机制，这是类之间的一种关系，提高了软件的可重用性和可扩展性
3. 多态是指程序中定义的引用变量所指向的具体类型和通过该引用变量发出的方法调用在编程时并不确定，而是在程序运行期间才确定，即一个引用变量倒底会指向哪个类的实例对象，该引用变量发出的方法调用到底是哪个类中实现的方法，必须在由程序运行期间才能决定。

## final, finally, finalize 的区别

1. final:被 final 修饰的变量，赋值后，被视为常量，被 final 修饰的方法，不能再重写，被 final 修饰的类不能在被继承
2. finally 是异常中的一个关键字，try catch finally 不管异常是否发生，finally 块中的代码都会执行，程序的出口
3. finallize 是 java 垃圾回收中的一个关键字，在对垃圾对象回收时，会调用 finalize 方法

## Static Nested Class（嵌套类） 和 Inner Class（内部类）的不同

Static Nested Class 是被声明为静态（static）的内部类，它可以不依赖于外部类实例被实例化。而通常的内部类需要在外部类实例化后才能实例化

## 当一个对象被当作参数传递到一个方法后，此方法可改变这个对象的属性，并可返回变化后的结果，那么这里到底是值传递还是引用传递?

传递的是值， 在 Java 应用程序中，当对象引用传递给方法的一个参数时，传递的是该引用的一个副本（按值传递），实际上传递的该对象的内存首地址

## Java 的接口和 C++的虚类的相同和不同处。

c++的虚类与 java 的抽象方法相同，其与接口的不同之处在于

1. 只能继承一个虚类，可以实现多个接口
2. 虚类中可以有构造方法，接口没有构造方法
3. 虚类中可以有非抽象方法，接口中必须都是抽象方法
4. 虚类的访问权限可以为 pubic、private、protected 和 default，接口的访问权限只能是 public
5. 虚类中的方法可以是 pubic、private、protected 和 default 的，接口中的方法只能是 public 和 default 的

他们的相同之处在于：都不能被实例化。

## JAVA 语言如何进行异常处理，关键字：throws,throw,try,catch,finally 分别代表什么意义？在 try 块中可以抛出异常吗？

Java 使用面向对象的方式来处理异常，它把程序中发生的每个异常也都分别封装到一个对象来表示的，该对象中包含有异常的信息。throws、throw、try、catch、finally 就是 Java 中用来对异常进行处理的几个关键字

在 Java 编程中规定 Java 编译器强制普通异常必须 try..catch 处理或用 throws 声明继续抛给上层调用方法处理，一般异常必须要求被捕获和处理，而系统异常可以处理也可以不处理，所以编译器不强制用 try..catch 处理或用 throws、throw 声明异常。而 finally 一般与 try 或 try\catch 一起使用做为异常的最后，finally 是无论有没有异常发生，都要执行的代码块。

## 内部类可以引用他包含类的成员吗？有没有什么限制？

完全可以，内部类拥有外围类的所有元素的访问权，不论是外围的的私有方法和属性都可以访问的的到。如果不是静态内部类，那没有什么限制。如果把静态嵌套类当作内部类的一种特例，那在这种情况下不可以访问外部类的普通成员变 量，而只能访问外部类中的静态成员

## 两个对象值相同(x.equals(y) == true)，但却可有不同的 hash code 说法是否正确？

如果两个对象相同，那么它们的 hashCode 值一定要相同；如果两个对象的 hashCode 相同，它们并不一定相同。 重写了 equals 方法就但没重写 hashcode 方法，就会出现这样的问题。

## 如何通过反射获取和设置对象私有字段的值？

可以通过类对象的 getDeclaredField()方法字段 Field 对象，然后再通过字段对象的 setAccessible(true)将其设置为可以访问，接下来就可以通过 get/set 方法来获取/设置字段的值了。

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

## 谈一下面向对象的"六原则一法则"

- 六原则：

  - 单一职责原则：一个类只做它该做的事情。（单一职责原则想表达的就是"高内聚"，写代码最终极的原则只有六个字"高内聚、低耦合"，所谓的高内聚就是一个代码模块只完成一项功能，在面向对象 中，如果只让一个类完成它该做的事，而不涉及与它无关的领域就是践行了高内聚的原则，这个类就只有单一职责。
  - 开闭原则：软件实体应当对扩展开放，对修改关闭。（在理想的状态下，当我们需要为一个软件系统增加新功能时，只需要从原来的系统派生出一些新类就可以，不需要修改原来的任何一行代码。要做到开闭有两个要点：① 抽象是关键，一个系统中如果没有抽象类或接口系统就没有扩展点；② 封装可变性，将系统中的各种可变因素封装到一个继承结构中，如果多个可变因素混杂在一起，系统将变得复杂而混乱。
  - 依赖倒转原则：面向接口编程。（该原则说得直白和具体一些就是声明方法的参数类型、方法的返回类型、变量的引用类型时，尽可能使用抽象类型而不用具体类型，因为抽象类型可以被它的任何一个子类型所替代。
  - 里氏替换原则：任何时候都可以用子类型替换掉父类型。但简单的说就是能用父类型的地方就一定能使用子类型。里氏替换原则可以检查继承关系是否合理，如果一个继承关系违背了里氏替换原则，那么这个继承关系一定是错误的，需要对代码进行重构。
  - 接口隔离原则：接口要小而专，绝不能大而全。
  - 合成聚合复用原则：优先使用聚合或合成关系复用代码。要说明的是，即使在 Java 的 API 中也有不少滥用继承的例子，例如 Properties 类继承了 Hashtable 类，Stack 类继承了 Vector 类，这些继承明显就是错误的，更好的做法是在 Properties 类中放置一个 Hashtable 类型的成员并且将其键和值都设置为字符串来存储数据，而 Stack 类的设计也应该是在 Stack 类中放一个 Vector 对象来存储数据。记住：任何时候都不要继承工具类，工具是可以拥有并可以使用的，而不是拿来继承的。

- 迪米特法则：迪米特法则又叫最少知识原则，一个对象应当对其他对象有尽可能少的了解。就是说：一个实体应当尽量少的与其他实体之间发生相互作用，使得系统功能模块相对独立。
  总结：单一职责原则告诉我们实现类要职责单一；里氏替换原则告诉我们不要破坏继承体系；依赖倒置原则告诉我们要面向接口编程；接口隔离原则告诉我们在设计接口的时候要精简单一；迪米特法则告诉我们要降低耦合。而开闭原则是总纲，他告诉我们要对扩展开放，对修改关闭。

## 请问 Query 接口的 list 方法和 iterate 方法有什么区别？

1. 返回的类型不一样，list 返回 List，iterate 返回 iterator
2. 查询策略不同。获取数据的方式不一样，list 会直接查询数据库，iterate 会先到数据库中把 id 取出来，然后真正要遍历某个对象的时候先到缓存中找，如果找不到，以 id 为条件再发一条 sql 到数据库，这样如果缓存中没有数据，则查询数据库的次数为 n+1

## Java 中，什么是构造函数？什么是构造函数重载？什么是复制构造函数？

新对象被创建的时候，构造方法会被调用。每一个类都有构造方法。在程序员没有给类提供构造方法的情况下，Java 编译器会为这个类创建一个默认的构造方法。

Java 中构造方法重载和方法重载很相似。可以为一个类创建多个构造方法。每一个构造方法必须有它自己唯一的参数列表。

Java 不支持像 C++中那样的复制构造方法，这个不同点是因为如果你不自己写构造方法的情况下，Java 不会创建默认的复制构造方法。

# 集合

## ConcurrentHashMap？ConcurrentSkipListMap？二者的区别

[ConcurrentHashMap 在 jdk1.8 和 1.7 中的区别](https://sky-xin.iteye.com/blog/2431255)  
[详解 ConcurrentHashMap 及 JDK8 的优化](https://mp.weixin.qq.com/s/kirY7_NQ-aZSqvsi4Nn21w)

**1. concurrenthashmap：**

concurrenthashmap 是 hashmap 的多线程版本

**jdk1.7**

- 采用 Segment + HashEntry 的方式进行实现。锁加在了不同的 Segment（默认为 16 段），ConcurrentHashMap 将数据分段，在读写的时候只加到相应的数据段上，这样在多线程的时候，可以读写其他段的数据，提高效率。
- put 操作：

  1. 首先对 key 进行第 1 次 hash，通过 hash 值确定 segment 的位置
  2. 然后在 segment 内进行操作，获取锁
  3. 获取当前 segment 的 HashEntry 数组后对 key 进行第 2 次 hash，通过 hash 值确定在 HashEntry 数组的索引位置
  4. 通过继承 ReentrantLock 的 tryLock 方法尝试去获取锁，如果获取成功就直接插入相应的位置，如果已经有线程获取该 Segment 的锁，那当前线程会以自旋的方式去继续的调用 tryLock 方法去获取锁，超过指定次数就挂起，等待唤醒
  5. 然后对当前索引的 HashEntry 链进行遍历，如果有重复的 key，则替换；如果没有重复的，则插入到链头
  6. 释放锁

- get 操作:

  ConcurrentHashMap 的 get 操作跟 HashMap 类似，只是 ConcurrentHashMap 第一次需要经过一次 hash 定位到 Segment 的位置，然后再 hash 定位到指定的 HashEntry，遍历该 HashEntry 下的链表进行对比，成功就返回，不成功就返回 null 。但是 get 操作的 concurrenthashmap 不需要加锁，原因是将存储元素都标记了 volatile

- size 操作：

  size 操作用来计算 ConcurrentHashMap 的元素大小。

  1. size 操作就是遍历了两次所有的 Segments，每次记录 Segment 的 modCount 值，然后将两次的 modCount 进行比较，如果相同，则表示期间没有发生过写入操作，就将原先遍历的结果返回。
  2. 如果经判断发现两次统计出的 modCount 并不一致，要重新启用全部 segment 加锁的方式来进行 count 的获取和统计了，这样在此期间每个 segement 都被锁住，无法进行其他操作，统计出的 count 自然很准确

**jdk1.8:**

- 实现已经摒弃了 Segment 分段锁的数据结构，而是直接用 Node 数组 + 链表 + 红黑树的数据结构来实现，并发控制使用 Synchronized（写）和 CAS（读）来操作，从而实现了对每一行数据进行加锁，进一步减少并发冲突的概率。
  ![](https://upload-images.jianshu.io/upload_images/2184951-3d2365ca5996274f.png?imageMogr2/auto-orient/)

- Node 类成员变量 Node 的元素 val 和指针 next 都标注 volatile，目的是在多线程环境下线程 A 修改结点的 val 或者新增节点的时候是对线程 B 可见的。因此，get 操作不需要加锁是因为 Node 的成员 val 是用 volatile 修饰的和数组用 volatile 修饰没有关系。
- ConcurrentHashMap 有成员变量 `transient volatile Node<K,V>[] table`，目的是为了使 Node 数组在扩容的时候对其他线程具有可见性而加的 volatile。
- ConcurrentHashMap 的初始化其实是一个空实现，并没有做任何事，初始化操作并不是在构造函数实现的，而是在 put 操作中实现。
- 1.8 中 get 操作不需要加锁，这也是它比其它并发集合比如 hashtable、用 Colletions.synchronizedMap() 包装的 hashmap 安全且效率高的原因

- 与 jdk1.7 区别：

  1. 数据结构不同
  2. 保证线程安全机制不同
  3. 锁的粒度不同
  4. 链表转化为红黑树，查询时间复杂度不同
  5. jdk1.8 推荐使用 mappingCount 方法而不是 size 方法获取当前 map 表的大小。因为这个方法的返回值是 long 类型，size 方法是返回值类型是 int

- put 操作

  对当前的 table 进行无条件自循环直到 put 成功

  1. 如果没有初始化就先调用 `initTable()` 方法来进行初始化过程
  2. 如果没有 hash 冲突就直接 CAS 插入
  3. 如果还在进行扩容操作就先进行扩容
  4. 如果存在 hash 冲突，就加锁来保证线程安全，这里有两种情况，一种是链表形式就直接遍历到尾端插入，一种是红黑树就按照红黑树结构插入
  5. 如果涉及到相同的 key 进行 put 就会覆盖原先的 value
  6. 最后一个如果该链表的数量大于阈值 8，就要先转换成黑红树的结构，break 再一次进入循环
  7. 如果添加成功就调用 addCount() 方法统计 size ，并且检查是否需要扩容

  ```java
  public V put(K key, V value) {
      return putVal(key, value, false);
  }
  /** Implementation for put and putIfAbsent */
  final V putVal(K key, V value, boolean onlyIfAbsent) {
      if (key == null || value == null) throw new NullPointerException();
      int hash = spread(key.hashCode()); //两次hash，减少hash冲突，可以均匀分布
      int binCount = 0;
      for (Node<K,V>[] tab = table;;) { //对这个table进行迭代
          Node<K,V> f; int n, i, fh;
          //这里就是上面构造方法没有进行初始化，在这里进行判断，为null就调用initTable进行初始化，属于懒汉模式初始化
          if (tab == null || (n = tab.length) == 0)
              tab = initTable();
          else if ((f = tabAt(tab, i = (n - 1) & hash)) == null) {//如果i位置没有数据，就直接无锁插入
              if (casTabAt(tab, i, null,
                          new Node<K,V>(hash, key, value, null)))
                  break;                   // no lock when adding to empty bin
          }
          else if ((fh = f.hash) == MOVED)//如果在进行扩容，则先进行扩容操作
              tab = helpTransfer(tab, f);
          else {
              V oldVal = null;
              //如果以上条件都不满足，那就要进行加锁操作，也就是存在hash冲突，锁住链表或者红黑树的头结点
              synchronized (f) {
                  if (tabAt(tab, i) == f) {
                      if (fh >= 0) { //表示该节点是链表结构
                          binCount = 1;
                          for (Node<K,V> e = f;; ++binCount) {
                              K ek;
                              //这里涉及到相同的key进行put就会覆盖原先的value
                              if (e.hash == hash &&
                                  ((ek = e.key) == key ||
                                  (ek != null && key.equals(ek)))) {
                                  oldVal = e.val;
                                  if (!onlyIfAbsent)
                                      e.val = value;
                                  break;
                              }
                              Node<K,V> pred = e;
                              if ((e = e.next) == null) {  //插入链表尾部
                                  pred.next = new Node<K,V>(hash, key,
                                                          value, null);
                                  break;
                              }
                          }
                      }
                      else if (f instanceof TreeBin) {//红黑树结构
                          Node<K,V> p;
                          binCount = 2;
                          //红黑树结构旋转插入
                          if ((p = ((TreeBin<K,V>)f).putTreeVal(hash, key,
                                                      value)) != null) {
                              oldVal = p.val;
                              if (!onlyIfAbsent)
                                  p.val = value;
                          }
                      }
                  }
              }
              if (binCount != 0) { //如果链表的长度大于8时就会进行红黑树的转换
                  if (binCount >= TREEIFY_THRESHOLD)
                      treeifyBin(tab, i);
                  if (oldVal != null)
                      return oldVal;
                  break;
              }
          }
      }
      addCount(1L, binCount);//统计size，并且检查是否需要扩容
      return null;
  }
  ```

- get 操作：

  1. 计算 hash 值，定位到该 table 索引位置，如果是首节点符合就返回
  2. 如果遇到扩容的时候，会调用标志正在扩容节点 ForwardingNode 的 find 方法，查找该节点，匹配就返回。
     - ForwardingNode：一个特殊的 Node 节点，hash 值为 -1，其中存储 nextTable 的引用。只有 table 发生扩容的时候，ForwardingNode 才会发挥作用，作为一个占位符放在 table 中表示当前节点为 null 或则已经被移动。
     - nextTable：默认为 null，扩容时新生成的数组，其大小为原数组的两倍
  3. 以上都不符合的话，就往下遍历节点，匹配就返回，否则最后就返回 null

  ```java
  public V get(Object key) {
      Node<K,V>[] tab; Node<K,V> e, p; int n, eh; K ek;
      int h = spread(key.hashCode()); //计算两次hash
      if ((tab = table) != null && (n = tab.length) > 0 &&
          (e = tabAt(tab, (n - 1) & h)) != null) { //读取首节点的Node元素
          if ((eh = e.hash) == h) {                //如果该节点就是首节点就返回
              if ((ek = e.key) == key || (ek != null && key.equals(ek)))
                  return e.val;
          }
          //hash值为负值表示正在扩容
          //这个时候查的是 ForwardingNode 的 find 方法来定位到 nextTable 来
          //查找，查找到就返回
          else if (eh < 0)
              return (p = e.find(h, key)) != null ? p.val : null;
          while ((e = e.next) != null) {//既不是首节点也不是ForwardingNode，那就往下遍历
              if (e.hash == h &&
                  ((ek = e.key) == key || (ek != null && key.equals(ek))))
                  return e.val;
          }
      }
      return null;
  }
  ```

- size 方法
  1. 通过二个变量 baseCount 和 counterCells 来计算 size
  2. baseCount 用于记录节点的个数，是个 volatile 变量
  3. counterCells 是一个辅助 baseCount 计数的数组，每个 counterCell 存着部分的节点数量，这样做的目的就是尽可能地减少冲突
  4. ConcurrentHashMap 节点的数量 = baseCount+counterCells 每个 cell 记录下来的节点数量
  5. 总体的原则就是：先尝试更新 baseCount，失败再利用 CounterCell。

**ConcurrentSkipListMap：**

是线程安全的有序的哈希表，适用于高并发的场景。

## hashMap？

[Java 8 系列之重新认识 HashMap](https://zhuanlan.zhihu.com/p/21673805)

[Java HashMap 工作原理及实现](http://yikun.github.io/2015/04/01/Java-HashMap%E5%B7%A5%E4%BD%9C%E5%8E%9F%E7%90%86%E5%8F%8A%E5%AE%9E%E7%8E%B0/)

**概念：**

1. HashMap 是一个散列桶（数组和链表），它存储的内容是键值对(key-value)映射
2. HashMap 采用了数组和链表的数据结构，能在查询和修改方便继承了数组的线性查找和链表的寻址修改
3. HashMap 是非 synchronized，所以 HashMap 很快
4. HashMap 可以接受 null 键和值，而 Hashtable 则不能（原因就是 equlas()方法需要对象，因为 HashMap 是后出的 API 经过处理才可以）

**工作原理：**

JDK7 中 HashMap 采用的是位桶+链表的方式，即我们常说的散列链表的方式，而 JDK8 中采用的是位桶+链表/红黑树。

HashMap 的底层主要是基于数组和链表来实现的，HashMap 底层是通过链表来解决 hash 冲突的。HashMap 底层就是一个数组结构，数组中存放的是一个 Node 对象，实现了 Map.Entry 接口，本质是就是一个映射(键值对)。如果产生的 hash 冲突，也就是说要存储的那个位置上面已经存储了对象了，这时候该位置存储的就是一个链表了。

**HashMap 类中的一些关键属性：**

Node[] table 的初始化长度 length 默认值是 16；loadFactor 为负载因子(默认值是 0.75)，threshold 临界值大小，是 HashMap 所能容纳的最大数据量的 Node (键值对)个数。threshold = length \* loadFactor；当实际大小超过临界值时，会进行扩容。loadFactor 加载因子，其中加载因子是表示 Hash 表中元素的填满的程度。若加载因子越大，填满的元素越多，好处是，空间利用率高了，但冲突的机会加大了。反之，加载因子越小，填满的元素越少，好处是冲突的机会减小了，但空间浪费多了，取默认值 0.75 就好了；size 就是 HashMap 中实际存在的键值对数量；
modCount 字段主要用来记录 HashMap 内部结构发生变化的次数，主要用于迭代的快速失败。强调一点，内部结构发生变化指的是结构发生变化，例如 put 新键值对，但是某个 key 对应的 value 值被覆盖不属于结构变化。

```java
int threshold;             // 所能容纳的key-value对极限
final float loadFactor;    // 负载因子
int modCount;
int size;
```

**确定哈希桶数组索引位置：**

- Hash 算法本质上就是三步：取 key 的 hashCode 值、高位运算、取模运算。
- 通过 h & (table.length -1)来得到该对象的保存位，而 HashMap 底层数组的长度总是 2 的 n 次方，这是 HashMap 在速度上的优化。当 length 总是 2 的 n 次方时，h & (length-1)运算等价于对 length 取模，也就是 h % length，但是&比%具有更高的效率。
- 在 JDK1.8 的实现中，优化了高位运算的算法，通过 hashCode()的高 16 位异或低 16 位实现的：(h = k.hashCode()) ^ (h >>> 16)，主要是从速度、功效、质量来考虑的，在 n - 1 为 15(0x1111)时，其实散列真正生效的只是低 4bit 的有效位，容易发生碰撞。
  这么做可以在数组 table 的 length 比较小的时候，也能保证考虑到高低 Bit 都参与到 Hash 的计算中，同时不会有太大的开销。代码如下：

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

**get()操作原理：**

1. bucket 里的第一个节点，直接命中；
2. 如果有冲突，则通过 key.equals(k)去查找对应的 entry
   - 若为树，则在树中通过 key.equals(k)查找，O(logn)；
   - 若为链表，则在链表中通过 key.equals(k)查找，O(n)。

**put()操作原理：**

1. 对 key 的 hashCode()做 hash，然后再计算 index;
2. 如果没碰撞直接放到 bucket 里；
3. 如果碰撞了，以链表的形式存在 buckets 后；
4. 如果碰撞导致链表过长(大于等于 TREEIFY_THRESHOLD)，就把链表转换成红黑树；
5. 如果节点已经存在就替换 old value(保证 key 的唯一性)
6. 如果 bucket 满了(超过 load factor \* current capacity)，就要 resize。

**扩容机制 resize**

- JKD1.7：旧桶数组中的某个桶的外挂单链表的 Node 结点是通过头插法插入新桶数组中的，并且原链表中的 Node 结点并不一定仍然在新桶数组的同一链表。
- JDK1.8：扩容使用的是 2 次幂的扩展(指长度扩为原来 2 倍)，所以，元素的位置要么是在原位置，要么是在原位置再移动 2 次幂的位置。
  因此，在扩充 HashMap 的时候，不需要像 JDK1.7 的实现那样重新计算 hash，只需要看原来的 hash 值新增的那个 bit 是 1 还是 0 就好了，是 0 的话索引没变，是 1 的话索引变成“原索引+oldCap”

**JDK1.8 与 JDK1.7 的性能对比：**

HashMap 中，如果 key 经过 hash 算法得出的数组索引位置全部不相同，即 Hash 算法非常好，那样的话，getKey 方法的时间复杂度就是 O(1)，如果 Hash 算法技术的结果碰撞非常多，假如 Hash 算极其差，所有的 Hash 算法结果得出的索引位置一样，那样所有的键值对都集中到一个桶中，或者在一个链表中，或者在一个红黑树中，时间复杂度分别为 O(n)和 O(lgn)。 鉴于 JDK1.8 做了多方面的优化，总体性能优于 JDK1.7。

**jdk1.8 使用链表+红黑树原因：**

在 Java 8 之前的实现中是用链表解决冲突的，在产生碰撞的情况下，进行 get 时，两步的时间复杂度是 O(1)+O(n)。因此，当碰撞很厉害的时候 n 很大，O(n)的速度显然是影响速度的。
因此在 Java 8 中，利用红黑树替换链表，这样复杂度就变成了 O(1)+O(logn)了，这样在 n 很大的时候，能够比较理想的解决这个问题

**Hashmap 时设置初始化容量多少合适：**

[关于 HashMap 容量的初始化，还有这么多学问。](https://mp.weixin.qq.com/s?__biz=MzI3NzE0NjcwMg==&mid=2650121359&idx=1&sn=c63d62be1a36db675c62e341044f10e0&chksm=f36bb9aec41c30b8b369428db1286d3de9bc04675057cde49632f3ba50db2d0a69451d6ec080&mpshare=1&scene=1&srcid=0529kU8fMyKTUrpKDwaLMJc6#rd)

1. 设置初始容量原因：

   如果我们没有设置初始容量大小，随着元素的不断增加，HashMap 会发生多次扩容，而 HashMap 中的扩容机制决定了每次扩容都需要重建 hash 表，是非常影响性能的。

2. 如何设置：

[为什么阿里巴巴建议集合初始化时，指定集合容量大小](https://www.hollischuang.com/archives/3545)

`initialCapacity = (需要存储的元素个数 / 负载因子) + 1`，负载因子默认 0.75，如果暂时无法确定元素个数，先设置为 16。

默认情况下，当我们设置 HashMap 的初始化容量时，实际上 HashMap 会采用第一个大于该数值的 2 的幂作为初始化容量。得到这个数字的算法其实是使用了使用无符号右移和按位或运算来提升效率。

**hashmap 在高并发场景下为什么会出现死循环：**

JDK1.7 中 resize 操作通过头插法将旧桶中的 Node 结点插入到新链表的桶位置中此过程多线程下会出现死循环

JDK1.8 中不使用头插法，用 head 和 tail 来保证链表的顺序和之前一样

但是 1.8 和 1.7 的 put 操作都会导致数据丢失的问题，因此还是线程不安全的

## 如果 hashMap 的 key 是一个自定义的类，怎么办？

必须重写该类的 hashcode()方法和 equals()方法

HashMap 中，如果要比较 key 是否相等，要同时使用这两个函数:通过 hashcode 值定位 bucket 位置，如果发生冲突通过 equal 方法定位在链表或者红黑树中的插入位置
因为自定义的类的 hashcode()方法继承于 Object 类，其 hashcode 码为默认的内存地 址，这样即便有相同含义的两个对象，比较也是不相等的，equals()比较的是内存地址是否相等。

## ArrayList 和 LinkedList 的区别，如果一直在 list 的尾部添加元素，用哪个效率高？

ArrayList 是实现了基于动态数组的数据结构，LinkedList 基于链表的数据结构

~~当输入的数据一直是小于千万级别的时候，大部分是 Linked 效率高, 而当数据量大于千万级别的时候，就会出现 ArrayList 的效率比较高了。~~

~~LinkedList 每次增加的时候，会 new 一个 Node 对象来存新增加的元素，所以当数据量小的时候，这个时间并不明显，而 ArrayList 需要扩容，所以 LinkedList 的效率就会比较高，其中如果 ArrayList 出现不需要扩容的时候，那么 ArrayList 的效率应该是比 LinkedList 高的，当数据量很大的时候，new 对象的时间大于扩容的时间，那么就会出现 ArrayList'的效率比 Linkedlist 高了~~

选择 LinkedList，arraylist 是静态内存。如果一直插，需要耗费时间，并且可能会造成没内存泄露，扩容有可能导致内存不够

## TreeMap 底层，红黑树原理？

[参考 1](https://blog.csdn.net/sun_tttt/article/details/65445754)
[参考 2](https://blog.csdn.net/qq_39295755/article/details/80182288)

- TreeMap：

  1. 继承于 AbstractMap，是一个有序的 key-value 集合，基于红黑树(Red-Black tree)实现
  2. 该映射根据其键的自然顺序进行排序，或者根据创建时提供的 Comparator 进行排序
  3. 实现了 NavigableMap 接口，意味着它支持一系列的导航方法。比如返回有序的 key 集合
  4. 实现了 Cloneable 接口，意味着它能被克隆
  5. 实现了 java.io.Serializable 接口，意味着它支持序列化
  6. 基本操作 containsKey、get、put 和 remove 的时间复杂度是 log(n)
  7. TreeMap 是非同步的。 它的 iterator 方法返回的迭代器是 fail-fast 的。

- 红黑树

  - 概念：为一颗二叉搜索树，每个节点上增加了一个存储位来表示节点的颜色，通过对任意一条叶子节点到根节点的路径上的颜色进行约束，保证最长路径不超过最短路径的两倍，因此红黑树是近似平衡。

  - 性质（这五条性质约束了红黑树，满足这五条性质的二叉树可以将查找删除维持在对数时间内）：

    1. 每个节点要么是红色，要么是黑色
    2. 根节点永远是黑色的
    3. 所有的叶节点都是空节点（即 null，实际上是不存在的节点），并且是黑色的
    4. 每个红色节点的两个子节点都是黑色。（从每个叶子到根的路径上不会有两个连续的红色节点）
    5. 从任一节点到其子树中每个叶子节点的路径都包含相同数量的黑色节点

  - 节点插入：红黑树插入节点的时候需要考虑新节点的颜色是红色的还是黑色的，假设新节点缺省颜色是黑色的，那么只要插入进去，该路径上的黑色节点数比其他路径上的节点数多一个，这时就要对其他路径进行调整；如果插入的节点是红色节点，如果该节点父亲节点是黑色，直接插入，如果该节点父亲节点是红色，就只在该条路径上进行调整。

## ArrayList 是否会越界？

会的，ArrayList 底层是数组实现，在执行 add(int index， E element)操作时，给定的下标 index 可以在 0 到 size 之间，如果不在这个范围之内，则会出现数组下标越界问题：

```java
if (index > size || index < 0) throw new IndexOutOfBoundsException(outOfBoundsMsg(index));
```

多线程环境下执行 add 操作时，若此时集合只够容纳一个元素，线程 A 执行 add 操作，首先通过函数函数 ensureCapacityInternal(size + 1)确保还可以添加一个元素，故没有进行数组扩容，之后线程 A 被阻塞。另一个线程 B 进来执行 add 方法添加了一个元素，此时线程 A 被唤醒，由于之前判断数组还可以添加一个元素，故直接执行 add 反法，此时便会出现下标越界问题。

```java
public boolean add(E e) {
    ensureCapacityInternal(size + 1); // Increments modCount!!
    elementData[size++] = e;
    return true;
}
```

~~如果执行 add++()方法的话，单线程环境下，当 add 一个元素时，size 先会执行 size++ 操作，之后将指定的元素添加到 size+1 的位置，如果是多线程环境下，也有可能出现下标越界问题，解释如下：由于 add（E e）方法没有同步，若此时集合容量为 15，当集合中已经添加了 14 个元素时，一个线程率先进入 add()方法，在执行 ensureCapacityInternal(size + 1)时，发现还可以添加一个元素，故数组没有扩容，但随后该线程被阻塞在此处。接着另一线程进入 add()方法，执行 ensureCapacityInternal(size + 1)，由于前一个线程并没有添加元素，故 size 依然为 14，依然不需要扩容，所以该线程就开始添加元素，使得 size++，变为 15，数组已经满了。而刚刚阻塞在 elementData[size++] = e 语句之前的线程开始执行，它要在集合中添加第 16 个元素，而数组容量只有 15 个，所以就发生了数组下标越界异常。~~

## Java 集合类框架的基本接口有哪些？

总共有两大接口：Collection 和 Map ，一个元素集合，一个是键值对集合。

- List 和 Set 接口继承了 Collection 接口，其中 List 是有序元素集合，必须按照插入顺序保存元素；Set 是无序元素集合，不能有重复元素。 而 ArrayList 和 LinkedList 实现了 List 接口，HashSet、TreeSet、LinkedHashSet 实现了 Set 接口，HashSet 是最快获取元素的方式，TreeSet 按照比较结果的升序保存对象，LinkedHashSet 按照被添加的结果保存对象。Queue 按照排队规则来确定对象产生的顺序。
- HashMap、TreeMap、LinkedHashMap 实现了 Map 接口，与 HashSet 一样，HashMap 提供了最快的查询技术，TreeMap 按照比较结果的升序保存键，LinkedHashMap 按照插入顺序保存键

## 为什么集合类没有实现 Cloneable 和 Serializable 接口？

克隆(cloning)或者是序列化(serialization)的语义和含义是跟具体的实现相关的。因此，应该由集合类的具体实现来决定如何被克隆或者是序列化。

Collection 表示一个集合，包含了一组对象。如何存储和维护这些对象是由具体实现来决定的。因为集合的具体形式多种多样，例如 list 允许重复，set 则不允许。而克隆（clone）和序列化（serializable）只对于具体的实体，对象有意义，你不能说去把一个接口，抽象类克隆，序列化甚至反序列化。所以具体的 collection 实现类是否可以克隆，是否可以序列化应该由其自身决定，而不能由其超类强行赋予。

如果 collection 继承了 clone 和 serializable，那么所有的集合实现都会实现这两个接口，而如果某个实现它不需要被克隆，甚至不允许它序列化（序列化有风险），那么就与 collection 矛盾了。

## 什么是迭代器？

Iterator 接口提供了很多对集合元素进行迭代的方法。每一个集合类都包含了可以返回迭代器实例的迭代方法。迭代器可以在迭代的过程中删除底层集合的元素,但是不可以直接调用集合的 remove(Object Obj)删除，可以通过迭代器的 remove()方法删除。

## Iterator 和 ListIterator 的区别是什么？

- 两个都是集合的迭代器。Iterator 使用范围是集合，ListIterator 的使用范围是 List 接口。而且 ListIterator 是继承于 Iterator 的接口：

```java
public interface ListIterator<E> extends Iterator<E> {}
```

- 两者功能来说：Iterator：

  1. 是否存在下一个元素；
  2. 获取下一个元素；
  3. 删除当前元素；

- ListIterator 因为是继承 Iterator 接口所以拥有 Iterator 接口的全部功能外还有获取上一个元素的能力等：
  1. 是否存在上一个元素；
  2. 获取上一个元素；
  3. 可以添加元素，但是 Iterator 不能添加元素

## 快速失败(fail-fast)和安全失败(fail-safe)的区别是什么？

- 快速失败（fail—fast）
  - 概念：在用迭代器遍历一个集合对象时，如果遍历过程中对集合对象的内容进行了修改（增加、删除修改），则会抛出 Concurrent Modification Exception。
  - 原理：
    迭代器在遍历时直接访问集合中的内容，并且在遍历过程中使用一个 modCount 变量。集合在被遍历期间如果内容发生变化，就会改变 modCount 的值。每当迭代器使用 hashNext()/next()遍历下一个元素之前，都会检测 modCount 变量是否为 expectedmodCount 值，是的话就返回遍历；否则抛出异常，终止遍历。
  - 注意：这里异常的抛出条件是检测到 modCount！=expectedmodCount 这个条件。如果集合发生变化时修改 modCount 值刚好又设置为了 expectedmodCount 值，则异常不会抛出。因此，不能依赖于这个异常是否抛出而进行并发操作的编程，这个异常只建议用于检测并发修改的 bug。
  - 场景：java.util 包下的集合类都是快速失败的，不能在多线程下发生并发修改（迭代过程中被修改）。
- 安全失败（fail—safe）:
  - 采用安全失败机制的集合容器，在遍历时不是直接在集合内容上访问的，而是先复制原有集合内容，在拷贝的集合上进行遍历。
  - 原理：由于迭代时是对原集合的拷贝进行遍历，所以在遍历过程中对原集合所作的修改并不能被迭代器检测到，所以不会触发 Concurrent Modification Exception。
  - 缺点：基于拷贝内容的优点是避免了 Concurrent Modification Exception，但同样地，迭代器并不能访问到修改后的内容，即：迭代器遍历的是开始遍历那一刻拿到的集合拷贝，在遍历期间原集合发生的修改迭代器是不知道的。
  - 场景：java.util.concurrent 包下的容器都是安全失败，可以在多线程下并发使用，并发修改

## HashMap 和 Hashtable 有什么区别？

1. HashMap 线程不安全，操作速度较快；Hashtable 使用 synchronized 来进行同步，线程安全，操作速度较慢。
2. HashMap 允许键值为空，Hashtable 不允许
3. HashMap 的迭代器是 fail-fast 迭代器

## ArrayList 和 LinkedList 有什么区别？

1. ArrayList 和 Linkedlist 都实现 List 接口， ArrayList 的实现用的是动态数组，LinkedList 是基于链表
2. ArrayList 支持随机访问，LinkedList 是以元素列表的形式存储它的数据，每一个元素都和它的前一个元素和后一个元素链接起来，查找某个元素的时间复杂度为 O（n）；
3. 相对于 ArrayList，LinkedList 的插入，增加，删除速度更快，因为其不需要像数组那样插入时需要重新计算索引；
4. LinkedList 比 ArrayList 占用更大的内存，因为 Linkedlist 为每个节点存储俩个引用，一个指向前一个元素，另一个指向后一个元素。

## ArrayList,Vector,LinkedList 的存储性能和特性是什么？

1. ArrayList 和 Vector 他们底层的实现都是一样的，都是使用数组方式存储数据，此数组元素数大于实际存储的数据以便增加和插入元素，它们都允许直接按序号索引元素，但是插入元素要涉及数组元素移动等内存操作，所以索引数据快而插入数据慢。
2. LinkedList 使用双向链表实现存储，按序号索引数据需要进行前向或后向遍历，但是插入数据时只需要记录本项的前后项即可，所以插入速度较快。
3. Vector 属于遗留容器， 已经不推荐使用，但是由于 ArrayList 和 LinkedListed 都是非线程安全的，如果遇到多个线程操作同一个容器的场景，则可以通过工具类 Collections 中的 synchronizedList 方法将其转换成线程安全的容器后再使用

## Collection 和 Collections 的区别

1. Collection 是集合类的上级接口，继承于它的接口主要有 Set 和 List。
2. Collections 是针对集合类的一个帮助类，它提供了一系列静态方法实现了对各种集合的排序，搜索和线程安全等操作。

## List、Map、Set 三个接口存取元素时，各有什么特点？

list 数据有序允许数据重复，set 数据无序不允许数据重复，map 以键值对存，键不能重复，可以允许一个键为 null，允许多个值为 null

# JDK

## Java 中的 LongAdder 和 AtomicLong 的区别

## JDK 和 JRE 的区别是什么？

- jRE： (Java Runtime Environment) JRE 顾名思义是 java 运行时环境，包含了 java 虚拟机，java 基础类库。是使用 java 语言编写的程序运行所需要的软件环境，是提供给想运行 java 程序的用户使用的。
- JDK：(Java Development Kit) JDK 顾名思义是 java 开发工具包，是程序员使用 java 语言编写 java 程序所需的开发工具包，是提供给程序员使用的。JDK 包含了 JRE，同时还包含了编译 java 源码的编译器 javac，还包含了很多 java 程序调试和分析的工具：jconsole，jvisualvm 等工具软件，还包含了 java 程序编写所需的文档和 demo 例子程序。
  如果你需要运行 java 程序，只需安装 JRE 就可以了。如果你需要编写 java 程序，需要安装 JDK。

## java 的跨平台

java 源程序先经过 javac 编译器编译成二进制的.class 字节码文件（java 的跨平台指的就是.class 字节码文件的跨平台，.class 字节码文件是与平台无关的），.class 文件再运行在 jvm 上，java 解释器（jvm 的一部分）会将其解释成对应平台的机器码执行，所以 java 所谓的跨平台就是在不同平台上安装了不同的 jvm，而在不同平台上生成的.class 文件都是一样的，而.class 文件再由对应平台的 jvm 解释成对应平台的机器码执行

## 机器码和字节码的区别

- 机器码，完全依附硬件而存在，并且不同硬件由于内嵌指令集不同，即使相同的 0 1 代码意思也可能是不同的，换句话说，根本不存在跨平台性。比如：不同型号的 CPU,你给他个指令 10001101，他们可能会解析为不同的结果；
- java 字节码是 java 的.class 文件,我们知道 JAVA 是跨平台的，为什么呢？因为他有一个 jvm,不论那种硬件，只要你装有 jvm,那么他就认识这个 JAVA 字节码，至于底层的机器码，咱不用管，有 jvm 搞定，他会把字节码再翻译成所在机器认识的机器码

# 反射

## 反射的实现与作用

JAVA 语言编译之后会生成一个.class 文件，反射就是通过字节码文件找到某一个类、类中的方法以及属性等。反射的实现主要借助以下四个类：Class：类的对象，Constructor：类的构造方法，Field：类中的属性对象，Method：类中的方法对象。

作用：反射机制指的是程序在运行时能够获取自身的信息。在 JAVA 中，只要给定类的名字，那么就可以通过反射机制来获取类的所有信息。

# IO 和 NIO、AIO

## 怎么打印日志？

## 运行时异常与一般异常有何异同？

## error 和 exception 有什么区别?

## 给我一个你最常见到的 runtime exception

- `Java.lang.NullPointerException`：空指针异常，应用程序试图在需要对象的地方使用 null 时
- `Java.lang.IndexOutOfBoundsException`：索引超出异常
- `ClassCastException`：类转换异常，试图将对象强制转换为不是实例的子类时
- `ArithmeticException`：算术异常，例如：`int a = 5 / 0;`

## Java 中的异常处理机制的简单原理和应用。

## java 中有几种类型的流？JDK 为每种类型的流提供了一些抽象类以供继承，请说出他们分别是哪些类？

Java 中的流分为两种，一种是字节流，另一种是字符流，分别由四个抽象类来表示（每种流包括输入和输出两种所以一共四个）:InputStream，OutputStream，InputStreamReader，OutputStreamWriter。二者区别：

1. 字节流可用于任何类型的对象，包括二进制对象，而字符流只能处理字符或者字符串；
2. 字节流提供了处理任何类型的 IO 操作的功能，但它不能直接处理 Unicode 字符，而字符流就可以。

## 什么是 java 序列化，如何实现 java 序列化？

序列化指把 Java 对象转换为字节序列的过程；反序列化指把字节序列恢复为 Java 对象的过程。

- java.io.ObjectOutputStream 代表对象输出流，它的 writeObject(Object obj) 方法可对参数指定的 obj 对象进行序列化，把得到的字节序列写到一个目标输出流中。
- java.io.ObjectInputStream 代表对象输入流，它的 readObject() 方法从一个源输入流中读取字节序列，再把它们反序列化为一个对象，并将其返回。

## 运行时异常与受检异常有什么区别？
