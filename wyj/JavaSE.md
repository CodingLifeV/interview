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
        - [1、ConcurrentHashMap？ConcurrentSkipListMap？二者的区别](#1concurrenthashmapconcurrentskiplistmap二者的区别)
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
    - [5、JDK](#5jdk)
        - [1、Java中的LongAdder和AtomicLong的区别](#1java中的longadder和atomiclong的区别)
        - [2、JDK和JRE的区别是什么？](#2jdk和jre的区别是什么)
        - [3、java的跨平台](#3java的跨平台)
        - [4、机器码和字节码的区别](#4机器码和字节码的区别)
    - [6、反射](#6反射)
        - [1、反射的实现与作用](#1反射的实现与作用)
    - [7、IO和NIO、AIO](#7io和nioaio)
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
### 1、ConcurrentHashMap？ConcurrentSkipListMap？二者的区别
[ConcurrentHashMap在jdk1.8和1.7中的区别](https://sky-xin.iteye.com/blog/2431255)  
[详解ConcurrentHashMap及JDK8的优化](https://mp.weixin.qq.com/s/kirY7_NQ-aZSqvsi4Nn21w)

**1. concurrenthashmap：**

concurrenthashmap是hashmap的多线程版本

**jdk1.7**  

  * 采用Segment + HashEntry的方式进行实现。锁加在了不同的Segment（默认为16段），ConcurrentHashMap将数据分段，在读写的时候只加到相应的数据段上，这样在多线程的时候，可以读写其他段的数据，提高效率。
  * put操作：
    1. 首先对key进行第1次hash，通过hash值确定segment的位置
    2. 然后在segment内进行操作，获取锁
    3. 获取当前segment的HashEntry数组后对key进行第2次hash，通过hash值确定在HashEntry数组的索引位置
    4. 通过继承ReentrantLock的tryLock方法尝试去获取锁，如果获取成功就直接插入相应的位置，如果已经有线程获取该Segment的锁，那当前线程会以自旋的方式去继续的调用tryLock方法去获取锁，超过指定次数就挂起，等待唤醒
    5. 然后对当前索引的HashEntry链进行遍历，如果有重复的key，则替换；如果没有重复的，则插入到链头
    6. 释放锁

  * get操作:  
  
    ConcurrentHashMap的get操作跟HashMap类似，只是ConcurrentHashMap第一次需要经过一次hash定位到Segment的位置，然后再hash定位到指定的HashEntry，遍历该HashEntry下的链表进行对比，成功就返回，不成功就返回null 。但是get操作的concurrenthashmap不需要加锁，原因是将存储元素都标记了volatile

* size操作：
  
  size操作用来计算ConcurrentHashMap的元素大小。
  1. size操作就是遍历了两次所有的Segments，每次记录Segment的modCount值，然后将两次的modCount进行比较，如果相同，则表示期间没有发生过写入操作，就将原先遍历的结果返回。
  2. 如果经判断发现两次统计出的modCount并不一致，要重新启用全部segment加锁的方式来进行count的获取和统计了，这样在此期间每个segement都被锁住，无法进行其他操作，统计出的count自然很准确

**jdk1.8:**

* 实现已经摒弃了Segment分段锁的数据结构，而是直接用Node数组+链表+红黑树的数据结构来实现，并发控制使用Synchronized（写）和CAS（读）来操作，从而实现了对每一行数据进行加锁，进一步减少并发冲突的概率。
  ![](https://upload-images.jianshu.io/upload_images/2184951-3d2365ca5996274f.png?imageMogr2/auto-orient/)

* Node类成员变量Node的元素val和指针next都标注volatile，目的是在多线程环境下线程A修改结点的val或者新增节点的时候是对线程B可见的
* ConcurrentHashMap有成员变量transient volatile Node<K,V>[] table，目的是为了使Node数组在扩容的时候对其他线程具有可见性而加的volatile。
* ConcurrentHashMap的初始化其实是一个空实现，并没有做任何事，初始化操作并不是在构造函数实现的，而是在put操作中实现。

* 与 jdk1.7 区别：
  1. 数据结构不同
  2. 保证线程安全机制不同
  3. 锁的粒度不同
  4. 链表转化为红黑树，查询时间复杂度不同
  5. jdk1.8 推荐使用 mappingCount 方法而不是 size 方法获取当前 map 表的大小。因为这个方法的返回值是long类型，size方法是返回值类型是int

* put操作
  
  对当前的table进行无条件自循环直到put成功
    1. 如果没有初始化就先调用initTable（）方法来进行初始化过程
    2. 如果没有hash冲突就直接CAS插入
    3. 如果还在进行扩容操作就先进行扩容
    4. 如果存在hash冲突，就加锁来保证线程安全，这里有两种情况，一种是链表形式就直接遍历到尾端插入，一种是红黑树就按照红黑树结构插入
    5. 如果涉及到相同的key进行put就会覆盖原先的value  
    6. 最后一个如果该链表的数量大于阈值8，就要先转换成黑红树的结构，break再一次进入循环
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

* get操作：
  1. 计算hash值，定位到该table索引位置，如果是首节点符合就返回
  2. 如果遇到扩容的时候，会调用标志正在扩容节点ForwardingNode的find方法，查找该节点，匹配就返回。
     * ForwardingNode：一个特殊的Node节点，hash值为-1，其中存储nextTable的引用。只有table发生扩容的时候，ForwardingNode才会发挥作用，作为一个占位符放在table中表示当前节点为null或则已经被移动。
     * nextTable：默认为null，扩容时新生成的数组，其大小为原数组的两倍
  3. 以上都不符合的话，就往下遍历节点，匹配就返回，否则最后就返回null 

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
* size 方法
  1. 通过二个变量 baseCount 和 counterCells 来计算 size
  2. baseCount 用于记录节点的个数，是个 volatile 变量
  3. counterCells 是一个辅助 baseCount 计数的数组，每个 counterCell 存着部分的节点数量，这样做的目的就是尽可能地减少冲突
  4. ConcurrentHashMap节点的数量 = baseCount+counterCells每个cell记录下来的节点数量
  5. 总体的原则就是：先尝试更新 baseCount，失败再利用 CounterCell。

**ConcurrentSkipListMap：**

是线程安全的有序的哈希表，适用于高并发的场景。

### 2、hashMap？
[hashmap参考1](https://zhuanlan.zhihu.com/p/21673805)

[hashmap参考2](http://yikun.github.io/2015/04/01/Java-HashMap%E5%B7%A5%E4%BD%9C%E5%8E%9F%E7%90%86%E5%8F%8A%E5%AE%9E%E7%8E%B0/)

**概念：**
1. HashMap是一个散列桶（数组和链表），它存储的内容是键值对(key-value)映射
2. HashMap采用了数组和链表的数据结构，能在查询和修改方便继承了数组的线性查找和链表的寻址修改
3. HashMap是非synchronized，所以HashMap很快
4. HashMap可以接受null键和值，而Hashtable则不能（原因就是equlas()方法需要对象，因为HashMap是后出的API经过处理才可以）
   
**工作原理：**

JDK7中HashMap采用的是位桶+链表的方式，即我们常说的散列链表的方式，而JDK8中采用的是位桶+链表/红黑树。

HashMap的底层主要是基于数组和链表来实现的，HashMap底层是通过链表来解决hash冲突的。HashMap底层就是一个数组结构，数组中存放的是一个Node对象，实现了Map.Entry接口，本质是就是一个映射(键值对)。如果产生的hash冲突，也就是说要存储的那个位置上面已经存储了对象了，这时候该位置存储的就是一个链表了。

**HashMap类中的一些关键属性：**

Node[] table的初始化长度length默认值是16；loadFactor为负载因子(默认值是0.75)，threshold临界值大小,是HashMap所能容纳的最大数据量的Node(键值对)个数。threshold = length * loadFactor,；当实际大小超过临界值时，会进行扩容。loadFactor加载因子，其中加载因子是表示Hash表中元素的填满的程度.若加载因子越大,填满的元素越多,好处是,空间利用率高了,但冲突的机会加大了。反之,加载因子越小,填满的元素越少,好处是冲突的机会减小了,但空间浪费多了，取默认值0.75就好了；size就是HashMap中实际存在的键值对数量； 
modCount字段主要用来记录HashMap内部结构发生变化的次数，主要用于迭代的快速失败。强调一点，内部结构发生变化指的是结构发生变化，例如put新键值对，但是某个key对应的value值被覆盖不属于结构变化。
```java
int threshold;             // 所能容纳的key-value对极限
final float loadFactor;    // 负载因子
int modCount;
int size;
```
**确定哈希桶数组索引位置：**

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

**get()操作原理：**
1. bucket里的第一个节点，直接命中；
2. 如果有冲突，则通过key.equals(k)去查找对应的entry
   * 若为树，则在树中通过key.equals(k)查找，O(logn)；
   * 若为链表，则在链表中通过key.equals(k)查找，O(n)。

**put()操作原理：**
1. 对key的hashCode()做hash，然后再计算index;
2. 如果没碰撞直接放到bucket里；
3. 如果碰撞了，以链表的形式存在buckets后；
4. 如果碰撞导致链表过长(大于等于TREEIFY_THRESHOLD)，就把链表转换成红黑树；
5. 如果节点已经存在就替换old value(保证key的唯一性)
6. 如果bucket满了(超过load factor * current capacity)，就要resize。

**扩容机制resize**
   * JKD1.7：旧桶数组中的某个桶的外挂单链表的Node结点是通过头插法插入新桶数组中的，并且原链表中的Node结点并不一定仍然在新桶数组的同一链表。
   * JDK1.8：扩容使用的是2次幂的扩展(指长度扩为原来2倍)，所以，元素的位置要么是在原位置，要么是在原位置再移动2次幂的位置。
因此，在扩充HashMap的时候，不需要像JDK1.7的实现那样重新计算hash，只需要看原来的hash值新增的那个bit是1还是0就好了，是0的话索引没变，是1的话索引变成“原索引+oldCap”

**JDK1.8与JDK1.7的性能对比：**

  HashMap中，如果key经过hash算法得出的数组索引位置全部不相同，即Hash算法非常好，那样的话，getKey方法的时间复杂度就是O(1)，如果Hash算法技术的结果碰撞非常多，假如Hash算极其差，所有的Hash算法结果得出的索引位置一样，那样所有的键值对都集中到一个桶中，或者在一个链表中，或者在一个红黑树中，时间复杂度分别为O(n)和O(lgn)。 鉴于JDK1.8做了多方面的优化，总体性能优于JDK1.7。

**jdk1.8使用链表+红黑树原因：**

在Java 8之前的实现中是用链表解决冲突的，在产生碰撞的情况下，进行get时，两步的时间复杂度是O(1)+O(n)。因此，当碰撞很厉害的时候n很大，O(n)的速度显然是影响速度的。
因此在Java 8中，利用红黑树替换链表，这样复杂度就变成了O(1)+O(logn)了，这样在n很大的时候，能够比较理想的解决这个问题

**Hashmap时设置初始化容量多少合适：**

[关于HashMap容量的初始化，还有这么多学问。](https://mp.weixin.qq.com/s?__biz=MzI3NzE0NjcwMg==&mid=2650121359&idx=1&sn=c63d62be1a36db675c62e341044f10e0&chksm=f36bb9aec41c30b8b369428db1286d3de9bc04675057cde49632f3ba50db2d0a69451d6ec080&mpshare=1&scene=1&srcid=0529kU8fMyKTUrpKDwaLMJc6#rd)

1. 设置初始容量原因：

   如果我们没有设置初始容量大小，随着元素的不断增加，HashMap会发生多次扩容，而HashMap中的扩容机制决定了每次扩容都需要重建hash表，是非常影响性能的。

2. 如何设置：

   `initialCapacity = (需要存储的元素个数 / 负载因子) + 1`，负载因子默认0.75，如果暂时无法确定元素个数，先设置为16。

   但是，JDK并不会直接拿用户传进来的数字当做默认容量，而是会进行一番运算，最终得到一个2的幂。得到这个数字的算法其实是使用了使用无符号右移和按位或运算来提升效率。

**hashmap在高并发场景下为什么会出现死循环：**

JDK1.7中 resize 操作通过头插法将旧桶中的 Node 结点插入到新链表的桶位置中此过程多线程下会出现死循环

JDK1.8中不使用头插法，用 head 和 tail 来保证链表的顺序和之前一样

但是1.8和1.7的 put 操作都会导致数据丢失的问题，因此还是线程不安全的

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

## 5、JDK
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

## 6、反射
### 1、反射的实现与作用

JAVA语言编译之后会生成一个.class文件，反射就是通过字节码文件找到某一个类、类中的方法以及属性等。反射的实现主要借助以下四个类：Class：类的对象，Constructor：类的构造方法，Field：类中的属性对象，Method：类中的方法对象。 

作用：反射机制指的是程序在运行时能够获取自身的信息。在JAVA中，只要给定类的名字，那么就可以通过反射机制来获取类的所有信息。

## 7、IO和NIO、AIO
### 1、怎么打印日志？
### 2、运行时异常与一般异常有何异同？
### 3、error和exception有什么区别?
### 4、给我一个你最常见到的runtime exception
### 5、Java中的异常处理机制的简单原理和应用。
### 6、java中有几种类型的流？JDK为每种类型的流提供了一些抽象类以供继承，请说出他们分别是哪些类？
### 7、什么是java序列化，如何实现java序列化？
### 8、运行时异常与受检异常有什么区别？
