<!-- TOC -->

- [线程](#线程)
  - [多线程中的 i++线程安全吗？为什么？](#多线程中的-i线程安全吗为什么)
  - [如何线程安全的实现一个计数器？](#如何线程安全的实现一个计数器)
  - [多线程同步的方法](#多线程同步的方法)
  - [介绍一下生产者消费者模式？](#介绍一下生产者消费者模式)
  - [线程，进程，然后线程创建有很大开销，怎么优化？](#线程进程然后线程创建有很大开销怎么优化)
  - [线程池](#线程池)
  - [AQS](#aqs)
  - [创建线程的方法，哪个更好，为什么？](#创建线程的方法哪个更好为什么)
  - [Java 中有几种方式启动一个线程？](#java-中有几种方式启动一个线程)
  - [CountDownLatch，CyclicBarrier，Semaphore，CountDownLatch](#countdownlatchcyclicbarriersemaphorecountdownlatch)
  - [如何理解 Java 多线程回调方法？](#如何理解-java-多线程回调方法)
  - [概括的解释下线程的几种可用状态以及状态之间的关系](#概括的解释下线程的几种可用状态以及状态之间的关系)
  - [同步方法和同步代码块的区别是什么？](#同步方法和同步代码块的区别是什么)
  - [在监视器(Monitor)内部，是如何做线程同步的？程序应该做哪种级别的同步？](#在监视器monitor内部是如何做线程同步的程序应该做哪种级别的同步)
  - [sleep() 和 wait() 有什么区别？](#sleep-和-wait-有什么区别)
  - [同步和异步有何异同，在什么情况下分别使用他们？举例说明](#同步和异步有何异同在什么情况下分别使用他们举例说明)
  - [设计 4 个线程，其中两个线程每次对 j 增加 1，另外两个线程对 j 每次减少 1，使用内部类实现线程，对 j 增减的时候没有考虑顺序问题](#设计-4-个线程其中两个线程每次对-j-增加-1另外两个线程对-j-每次减少-1使用内部类实现线程对-j-增减的时候没有考虑顺序问题)
  - [启动一个线程是用 run()还是 start()?](#启动一个线程是用-run还是-start)
  - [请说出你所知道的线程同步的方法](#请说出你所知道的线程同步的方法)
  - [stop()和 suspend()方法为何不推荐使用？](#stop和-suspend方法为何不推荐使用)
  - [线程的 sleep()方法和 yield()方法有什么区别？](#线程的-sleep方法和-yield方法有什么区别)
  - [当一个线程进入一个对象的 synchronized 方法 A 之后，其它线程是否可进入此对象的 synchronized 方法 B？](#当一个线程进入一个对象的-synchronized-方法-a-之后其它线程是否可进入此对象的-synchronized-方法-b)
- [锁](#锁)
  - [锁总结](#锁总结)
    - [乐观锁 VS 悲观锁](#乐观锁-vs-悲观锁)
    - [自旋锁 VS 适应性自旋锁](#自旋锁-vs-适应性自旋锁)
    - [无锁 VS 偏向锁 VS 轻量级锁 VS 重量级锁](#无锁-vs-偏向锁-vs-轻量级锁-vs-重量级锁)
    - [公平锁 VS 非公平锁](#公平锁-vs-非公平锁)
    - [可重入锁 VS 非可重入锁](#可重入锁-vs-非可重入锁)
    - [独享锁 VS 共享锁](#独享锁-vs-共享锁)
  - [讲一下非公平锁和公平锁在 reetrantlock 里的实现](#讲一下非公平锁和公平锁在-reetrantlock-里的实现)
  - [讲一下 synchronized，可重入怎么实现](#讲一下-synchronized可重入怎么实现)
  - [锁和同步的区别](#锁和同步的区别)
  - [什么是死锁(deadlock)？](#什么是死锁deadlock)
  - [如何确保 N 个线程可以访问 N 个资源同时又不导致死锁？](#如何确保-n-个线程可以访问-n-个资源同时又不导致死锁)
  - [ReentrantLock 中公平锁和非公平锁在哪里体现的？](#reentrantlock-中公平锁和非公平锁在哪里体现的)
  - [volatile 的实现原理](#volatile-的实现原理)
- [底层原理](#底层原理)
  - [java 内存模型](#java-内存模型)
  - [synchronized 底层原理](#synchronized-底层原理)
  - [java 对象头](#java-对象头)
  - [Monitor](#monitor)
  - [Executors 线程池，为什么不建议使用这个类来创建线程池呢？如何创建？](#executors-线程池为什么不建议使用这个类来创建线程池呢如何创建)
  - [阻塞队列](#阻塞队列)
    - [ArrayBlockingQueue](#arrayblockingqueue)
    - [LinkedBlockingQueue](#linkedblockingqueue)
    - [二者对比](#二者对比)

<!-- /TOC -->

# 线程

## 多线程中的 i++线程安全吗？为什么？

- 如果 i 是局部变量（在方法里定义的），那么是线程安全的。因为局部变量是线程私有的，别的线程访问不到，其实也可以说没有线程安不安全之说，因为别的线程对他造不成影响。
- 如果 i 是全局变量（类的成员变量），那么是线程不安全的。因为如果是全局变量的话，同一进程中的不同线程都有可能访问到。
  每个线程都有自己的工作内存，每个线程需要对共享变量操作时必须把共享变量从主内存中加载到自己的工作内存。等完成操作再保存到内存中。如果一个线程运算完成后还没刷到主内存中，另一个线程又对这个共享变量进行操作，那么读取到的数据就是脏数据了。
- 对于 i++ 这种线程不安全问题有以下几种解决方案：
  1. 对 i++ 操作的方法加同步锁，同时只能有一个线程执行 i++ 操作；
  2. 使用支持原子性操作的类，如 java.util.concurrent.atomic.AtomicInteger，它使用的是 CAS 算法，效率优于第 1 种;

## 如何线程安全的实现一个计数器？

- 通过 AtomicInteger 类循环 CAS 操作

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

- 通过关键字 volatile 和 synchronized 实现

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

## 多线程同步的方法

[参考](https://www.cnblogs.com/XHJT/p/3897440.html)

1. 使用 sychronized 同步关键字修饰方法和代码块
2. 使用 volatile 修饰共享变量实现同步
3. 使用重入锁实现线程同步。ReentrantLock 类是可重入、互斥、实现了 Lock 接口的锁，常用方法有：ReentrantLock() : 创建一个 ReentrantLock 实例 ； lock() : 获得锁；unlock() : 释放锁
4. 使用局部变量实现线程同步。类 ThreadLocal 给每个线程绑定自己的值，实现每一个线程都有自己的共享变量。常用方法：
   1. ThreadLocal() : 创建一个线程本地变量
   2. get() : 返回此线程局部变量的当前线程副本中的值
   3. initialValue() : 返回此线程局部变量的当前线程的"初始值"
   4. set(T value) : 将此线程局部变量的当前线程副本中的值设置为 value
5. 使用阻塞队列实现线程同步。当队列满时，队列会阻塞插入元素的线程，队列为空时，获取元素的线程会阻塞直到等待队列变为空。发生阻塞的插入方法为 put()，移除方法为 take()。阻塞队列类似 ArrayBlockingQueue、LinkedBlockingQueue。阻塞队列通常用来实现生产者和消费者模式。
6. 使用原子变量实现线程同步. 在 java 的 util.concurrent.atomic 包中提供了创建了原子类型变量的工具类，使用该类可以简化线程同步。
   AtomicInteger 表可以用原子方式更新 int 的值， AtomicInteger 类常用方法：
   1. AtomicInteger(int initialValue) : 创建具有给定初始值的新的 AtomicInteger
   2. addAddGet(int dalta) : 以原子方式将给定值与当前值相加
   3. get() : 获取当前值

## 介绍一下生产者消费者模式？

生产者和消费者模式是通过一个容器解决生存者和消费者的强耦合问题。生产者和消费者之间不直接通信，而是通过阻塞队列来进行通信，所以生产者生产完数据之后不用等待消费者来处理，而是直接扔给阻塞队列，消费者不找生产者要数据，而是直接从阻塞队列里取，阻塞队列相当于一个缓冲区，平衡了生产者和消费者的处理能力。

Java 中的线程池实际就是一种生产者和消费者模式的实现方式，生产者把任务丢给线程池，线程池创建线程并处理任务，如果将要运行的任务数大于线程池的基本线程数就把任务扔到阻塞队列里面，这种做法比使用一个阻塞队列实现生产者和消费者模式要好的多，因为消费者能够处理直接就处理掉了，这样速度更快，而生产者先存，消费者再取这种方式显然要慢一些。

## 线程，进程，然后线程创建有很大开销，怎么优化？

进程是资源（CPU、内存等）分配的基本单位，它是程序执行时的一个实例。程序运行时系统就会创建一个进程，并为它分配资源，然后把该进程放入进程就绪队列，进程调度器选中它的时候就会为它分配 CPU 时间，程序开始真正运行。

线程是程序执行时的最小单位，它是进程的一个执行流，是 CPU 调度和分派的基本单位，一个进程可以由很多个线程组成，线程间共享进程的所有资源，每个线程有自己的堆栈和局部变量。

使用线程池进行优化。

## 线程池

[线程池的几种实现方式](https://www.jianshu.com/p/e9b0378db56a)

**概念**

线程池是存储线程的容器,线程事先创建好后放入线程池,当有任务需要执行时,直接从线程池拿空闲线程使用,使用完毕后归还给线程池

**FixedThreadPool**

创建一个指定工作线程数量的线程池。每当提交一个任务就创建一个工作线程，如果工作线程数量达到线程池初始的最大数，则将提交的任务存入到池队列中，使用 LinkedBlockingQueue 作为线程池的工作队列；

`corePoolSize` 和 `maximumPoolSize` 都被设置为创建 FixedThreadPool 时指定的参数 `nThreads`。当线程池中的线程数大于`corePoolSize` 时，`keepAliveTime` 为多余的空闲线程等待新任务的最长时间，超过这个时间后多余的线程将被终止。这里把`keepAliveTime` 设置为 0L，意味着多余的空闲线程会被立即终止。

FixedThreadPool 使用无界队列 LinkedBlockingQueue 作为线程池的工作队列，`maximumPoolSize`、`keepAliveTime` 将是一个无效参数。

**SingleThreadExecutor**

创建一个单线程化的 Executor，即只创建唯一的工作者线程来执行任务，它只会用唯一的工作线程来执行任务，保证所有任务按照指定顺序(FIFO， LIFO， 优先级)执行。如果这个线程异常结束，会有另一个取代它，保证顺序执行，使用 LinkedBlockingQueue 作为线程池的工作队列；

`corePoolSize` 和 `maximumPoolSize` 被设置为 1。其他参数与  FixedThreadPool 相同。

SingleThreadExecutor 使用无界队列 LinkedBlockingQueue 作为线程池的工作队列（队列的容量为 Integer.MAX_VALUE），`maximumPoolSize`、`keepAliveTime` 将是一个无效参数。

**CachedThreadPool**

创建一个可缓存线程池， 如果线程池长度超过处理需要，可灵活回收空闲线程，若无可回收，则新建线程

CachedThreadPool 的 `corePoolSize` 被设置为 0，即 corePool 为空；`maximumPoolSize` 被设置为  Integer.MAX_VALUE，即 maximumPool 是无界的。这里把 `keepAliveTime` 设置为 60L，意味着  CachedThreadPool 中的空闲线程等待新任务的最长时间为 60 秒，空闲线程超过 60 秒后将会被终止。

CachedThreadPool 使用没有容量的 SynchronousQueue 作为线程池的工作队列，但  CachedThreadPool 的 maximumPool 是无界的。这意味着，如果主线程提交任务的速度高于  maximumPool 中线程处理任务的速度时，CachedThreadPool 会不断创建新线程。极端情况下， CachedThreadPool 会因为创建过多线程而耗尽 CPU 和内存资源

**ScheduledThreadPoolExecutor**

有以下二种：

1. ScheduledThreadPoolExecutor：适用于需要多个后台线程执行周期任务，包含若干个线程
2. SingleThreadScheduledExecutor：适用于需要一个后台线程执行周期任务，只包含一个线程，同时需要保证顺序的执行各个任务的应用场景

**处理流程**

首先判断核心线程池里的线程是否都在执行任务，如果不是则直接从核心线程池中创建一个线程来执行，如果都在忙则判断任务队列是否也满了，没满的话将任务放进去等待执行，满了就判断线程池的全部线程是否都在忙，如果都在忙就交给饱和策略来处理，否则就创建一个线程来帮助核心线程处理任务。

**参数**

1. `corePoolSize`:核心线程池大小
2. `MaximumPoolSize`：线程池允许创建的最大线程数，如果使用无界队列该参数无效
3. `ThreadFactory`：线程工厂，主要用来创建线程
4. `runnableTaskQueue`：任务队列，用于保存等待执行的任务的阻塞队列
5. `RejectedExecutionHandler`：饱和策略

**策略**

1. `ThreadPoolExecutor.AbortPolicy`:丢弃任务并抛出 RejectedExecutionException 异常（默认情况）
2. `ThreadPoolExecutor.DiscardPolicy`：也是丢弃任务，但是不抛出异常。
3. `ThreadPoolExecutor.DiscardOldestPolicy`：丢弃队列最前面的任务，然后重新尝试执行任务
4. `ThreadPoolExecutor.CallerRunsPolicy`：只用调用者所在线程来运行任务

**使用线程池的优点：**

1. 降低资源消耗，通过重复利用已经创建的线程降低线程创建和销毁造成的消耗
2. 提高响应速度，当任务达到时，任务可以不需要的等到线程创建就能够立即执行
3. 提高线程的可管理性，性程是稀缺资源，如果无限制的创建，不仅会消耗系统资源，还会降低系统的稳定性，故使用线程池可以进行统一的分配，调用和监控，但是也要做到合理的利用线程池，所以要对线程池的原理了如指掌

## AQS

[参考](https://www.jianshu.com/p/da9d051dcc3d)

- AQS 全称为 AbstractQueuedSynchronizer,是并发容器中的同步器，它是抽象的队列式的同步器，AQS 定义了一套多线程访问共享资源的同步器框架，许多同步类都依赖它，如 ReentrantLock、Semaphore、CyclicBarrier、Condition、FutureTask 等

* AQS 的实现依赖内部的同步队列（FIFO 双向队列）， 维护了一个 volatile int 类型的变量 state，用来表示当前同步状态，如果当前线程获取同步状态失败，AQS 会将该线程以及等待状态等信息构造成一个 Node，将其加入同步队列的尾部，同时阻塞当前线程，当同步状态释放时，唤醒队列的头节点

- 获取锁：AQS 中维护了一个同步状态 status 来计数重入次数，status 初始值为 0。当线程尝试获取锁时，可重入锁先尝试获取并更新 status 值，如果 status == 0 表示没有其他线程在执行同步代码，则把 status 置为 1，当前线程开始执行。如果 status != 0，则判断当前线程是否是获取到这个锁的线程，如果是的话执行 status+1，且当前线程可以再次获取锁。

* state 的访问方式有三种, 这三种叫做均是原子操作，其中 compareAndSetState 的实现依赖于 Unsafe 的 compareAndSwapInt()方法:
  1. getState()
  2. setState()
  3. compareAndSetState()

- AQS 定义两种资源共享方式：Exclusive（独占，只有一个线程能执行，如 ReentrantLock）和 Share（共享，多个线程可同时执行，如 Semaphore/CountDownLatch）

* 不同的自定义同步器争用共享资源的方式也不同。自定义同步器在实现时只需要实现共享资源 state 的获取与释放方式即可，至于具体线程等待队列的维护（如获取资源失败入队/唤醒出队等），AQS 已经在顶层实现好了。自定义同步器实现时主要实现以下几种方法：

  1. tryAcquire(int)：独占方式。尝试获取资源，成功则返回 true，失败则返回 false。
  2. tryRelease(int)：独占方式。尝试释放资源，成功则返回 true，失败则返回 false。
  3. tryAcquireShared(int)：共享方式。尝试获取资源。负数表示失败；0 表示成功，但没有剩余可用资源；正数表示成功，且有剩余资源。
  4. tryReleaseShared(int)：共享方式。尝试释放资源，如果释放后允许唤醒后续等待结点返回 true，否则返回 false。

* acquire(int)
  - 流程：
    1. 调用自定义同步器的 tryAcquire()尝试直接去获取资源，如果成功则直接返回；
    2. 没成功，则 addWaiter()将该线程加入等待队列的尾部，并标记为独占模式；
    3. acquireQueued()使线程在等待队列中休息，有机会时（轮到自己，会被 unpark()）会去尝试获取资源。获取到资源后才返回。如果在整个等待过程中被中断过，则返回 true，否则返回 false
    4. 如果线程在等待过程中被中断过，它是不响应的。只是获取资源后才再进行自我中断 selfInterrupt()，将中断补上
  - 其它方法：
    1. addWaiter(Node)：该方法用于将当前线程根据不同的模式（Node.EXCLUSIVE 互斥模式、Node.SHARED 共享模式）加入到等待队列的队尾，并返回当前线程所在的结点。如果队列不为空，则以通过 compareAndSetTail 方法以 CAS 的方式将当前线程节点加入到等待队列的末尾。否则，通过 enq(node)方法初始化一个等待队列，并返回当前节点
    2. enq(node)用于将当前节点插入等待队列，如果队列为空，则初始化当前队列。整个过程以 CAS 自旋的方式进行，直到成功加入队尾为止
    3. acquireQueued(Node, int) 用于队列中的线程自旋地以独占且不可中断的方式获取同步状态（acquire），直到拿到锁之后再返回
    ```java
    public final void acquire(int arg) {
          if (!tryAcquire(arg) &&
              acquireQueued(addWaiter(Node.EXCLUSIVE), arg))
              selfInterrupt();
    }
    ```
* release(int)：独占模式下线程释放共享资源的顶层入口。它会释放指定量的资源，如果彻底释放了（即 state=0）,它会唤醒等待队列里的其他线程来获取资源。这也正是 unlock()的语义，当然不仅仅只限于 unlock()。

  正常来说，tryRelease()都会成功的，因为这是独占模式，该线程来释放资源，那么它肯定已经拿到独占资源了，直接减掉相应量的资源即可(state-=arg)，也不需要考虑线程安全的问题。但要注意它的返回值，上面已经提到了，release()是根据 tryRelease()的返回值来判断该线程是否已经完成释放掉资源了！所以自义定同步器在实现时，如果已经彻底释放资源(state=0)，要返回 true，否则返回 false

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

## 创建线程的方法，哪个更好，为什么？

1. 继承 Thread 类（真正意义上的线程类），是 Runnable 接口的实现。
2. 实现 Runnable 接口，并重写里面的 run 方法。
3. 使用 Executor 框架创建线程池。

一般情况下，常见的是第二种 Runnable 接口有如下好处：

1. 避免点继承的局限，一个类可以继承多个接口；
2. 适合于资源的共享

## Java 中有几种方式启动一个线程？

第一种:继承 Thread 类,重写 run 方法.第二种:实现 Runable 接口,重写 run 方法

## CountDownLatch，CyclicBarrier，Semaphore，CountDownLatch

**CountDownLatch：**

异步辅助类，它能让一个和多个线程处于等待状态，直到其他线程完成了一系列操作。countDown()方法代表

**CyclicBarrier：**

让一组线程等待至某个状态之后再全部同时执行。
最重要的是中最重要的方法就是 await 方法，用来挂起当前线程，直至所有线程都到达 barrier 状态再同时执行后续任务

**Semaphore：**

Semaphore 可以控制同时访问的线程个数，通过 acquire() 获取一个许可，如果没有就等待，而 release() 释放一个许可。

**总结：**

1. CountDownLatch 和 CyclicBarrier 都能够实现线程之间的等待，只不过它们侧重点不同：CountDownLatch 一般用于某个线程 A 等待若干个其他线程执行完任务之后，它才执行；而 CyclicBarrier 一般用于一组线程互相等待至某个状态，然后这一组线程再同时执行；另外，CountDownLatch 是不能够重用的，而 CyclicBarrier 是可以重用的。
2. Semaphore 其实和锁有点类似，它一般用于控制对某组资源的访问权限。
3. CountdownLatch 阻塞主线程，等所有子线程完结了再继续下去，其计数器只能使用一次
4. Syslicbarrier 阻塞一组线程，直至某个状态之后再全部同时执行，并且所有线程都被释放后，还能通过 reset 来重用

## 如何理解 Java 多线程回调方法？

客户程序 C 调用服务程序 S 中的某个方法 A，然后 S 又在某个时候反过来调用 C 中的某个方法 B，对于 C 来说，这个 B 便叫做回调方法。

## 概括的解释下线程的几种可用状态以及状态之间的关系

1. 新建状态(New)：线程实例化后还从未执行 start()方法时的状态；
2. 就绪状态(Runnable)：调用线程的 start()方法启动线程，start()方法创建线程运行的系统资源，并调度线程运行 run()方法。当 start()方法返回后，线程就处于就绪状态。
   处于就绪状态的线程并不一定立即运行 run()方法，线程还必须同其他线程竞争 CPU 时间，只有获得 CPU 时间才可以运行线程。因为在单 CPU 的计算机系统中，不可能同时运行多个线程，一个时刻仅有一个线程处于运行状态。因此此时可能有多个线程处于就绪状态。对多个处于就绪状态的线程是由 Java 运行时系统的线程调度程序(thread scheduler)来调度的。
3. 运行状态(Running)： 当线程获得 CPU 时间后，它才进入运行状态，真正开始执行 run()方法
4. 阻塞状态(Blocked)：出现在某一个线程等待锁的时候。 所谓阻塞状态是正在运行的线程没有运行结束，暂时让出 CPU，这时其他处于就绪状态的线程就可以获得 CPU 时间，进入运行状态
5. 死亡状态(Dead)： 有两个原因会导致线程死亡：
   1. run 方法正常退出而自然死亡，
   2. 一个未捕获的异常终止了 run 方法而使线程猝死。

创建线程通过 start 方法进入就绪状态，获取 cpu 的执行权进入运行状态，失去 cpu 执行权会回到就绪状态，运行状态完成进入消亡状态，运行状态通过 sleep 方法和 wait 方法进入阻塞状态，休眠结束或者通过 notify 方法或者 notifyAll 方法释放锁进入就绪状态。

## 同步方法和同步代码块的区别是什么？

1. 语法不同，同步方法写在方法上
2. 同步块需要注明锁定对象，同步方法默认锁定 this
3. 在静态方法中，都是默认锁定类对象
4. 在考虑性能方面，最好使用同步块来减少锁定范围提高并发效率。

## 在监视器(Monitor)内部，是如何做线程同步的？程序应该做哪种级别的同步？

- JVM 基于进入和退出 Monitor 对象来实现方法同步和代码块同步，但两者的实现细节不一样。本质都是对一个对象的监视器（monitor）进行获取，而这个获取过程是排他的，也就是同一时刻只能有一个线程获取到由 synchronized 所保护对象的监视器

- 代码块同步是使用 monitorenter 和 monitorexit 指令实现的。monitorenter 指令是在编译后插入到同步代码块的开始位置，而 monitorexit 是插入到方法结束处和异常处，JVM 要保证每个 monitorenter 必须有对应的 monitorexit 与之配对。任何对象都有一个 monitor 与之关联，当且一个 monitor 被持有后，它将处于锁定状态。线程执行到 monitorenter 指令时，将会尝试获取对象所对应的 monitor 的所有权，即尝试获得对象的锁。

- java 还提供了显式监视器(Lock)和隐式监视器(synchronized)两种锁方案

## sleep() 和 wait() 有什么区别？

1. sleep 方法没有释放锁，但是 wait 方法释放了锁，使得其他线程可以使用同步控制块
2. sleep 可以在任何地方使用，wait notify notifyall 只能使用在同步控制块中
3. sleep 必须捕获异常，其他不需要
4. sleep 方法是 Thread 的静态方法，wait 方法是 Object 类的普通方法

## 同步和异步有何异同，在什么情况下分别使用他们？举例说明

同步是安全的，异步是不安全的。同步是发送一个请求，等待返回，然后在发送一个请求。异步是发送一个请求，不用等待，随时可发送下一个请求

如果数据将在线程间共享。例如正在写的数据以后可能被另一个线程读到，或者正在读的数据可能已经被另一个线程写过了，那么这些数据就是共享数据，必须进行同步存取。

当应用程序在对象上调用了一个需要花费很长时间来执行的方法，并且不希望让程序等待方法的返回时，就应该使用异步编程，在很多情况下采用异步途径往往更有效率。

B-S 模式中，使用 Form 表单提交数据，发送的就是同步请求，当响应返回后，才可以继续操作；

B-S 模式中，使用 Ajax 向服务器端发送异步请求，在响应没有返回客户端时，客户端可以继续操作，当响应返回客户端后，就能显示结果

## 设计 4 个线程，其中两个线程每次对 j 增加 1，另外两个线程对 j 每次减少 1，使用内部类实现线程，对 j 增减的时候没有考虑顺序问题

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

## 启动一个线程是用 run()还是 start()?

启动一个线程是调用 start()方法，使线程所代表的虚拟处理机处于可运行状态，这意味着它可以由 JVM 调度并执行。这并不意味着线程就会立即运行。

## 请说出你所知道的线程同步的方法

1. sychronized 同步方法，同步代码块
2. wait()和 notify()。wait():使一个线程处于等待状态，并且释放所持有的对象的 lock;notify():唤醒一个处于等待状态的线程，注意的是在调用此方法的时候，并不能确切的唤醒某一个等待状态的线程，而是由 JVM 确定唤醒哪个线程，而且不是按优先级
3. sleep():使一个正在运行的线程处于睡眠状态，是一个静态方法，调用此方法要捕捉 InterruptedException 异常
4. Lock 接口的 ReentranLock，通过 lock()获取锁和 unlock()释放锁，Condition 对象中的 await()和 signal()类似于 wait()和 notify()方法
5. ThreadLocal 为每一个线程绑定自己的私有数据；
6. volatile 使变量在多个线程间可见。

## stop()和 suspend()方法为何不推荐使用？

- stop()方法停止线程释放锁将会给数据造成不一致的结果，如果在同步块执行一半时，stop 来了，后面还没执行完呢，锁没了，线程退出了，别的线程又可以操作你的数据了，所以就是线程不安全了。
- suspend()方法暂停线程，使用 resume()方法恢复线程的执行，如果使用不恰当，容易造成公共的同步对象的独占，发生死锁；也容易发生因为线程的暂停而导致数据不同步的情况。

## 线程的 sleep()方法和 yield()方法有什么区别？

yield()：放弃当前 CPU 资源，将它让给其它的任务去占用 CPU 执行时间。但放弃的时间不确定，有可能刚刚放弃，马上又获得 CPU 时间片。

1. sleep()方法给其他线程运行机会时不考虑线程的优先级，因此会给低优先级的线程以运行的机会；yield()方法只会给相同优先级或更高优先级的线程以运行的机会；
2. 线程执行 sleep()方法后转入阻塞（blocked）状态，而执行 yield()方法后转入就绪（ready）状态；
3. sleep()方法声明抛出 InterruptedException，而 yield()方法没有声明任何异常；

## 当一个线程进入一个对象的 synchronized 方法 A 之后，其它线程是否可进入此对象的 synchronized 方法 B？

不能。其它线程只能访问该对象的非同步方法，同步方法则不能进入。因为非静态方法上的 synchronized 修饰符要求执行方法时要获得对象的锁，如果已经进入 A 方法说明对象锁已经被取走，那么试图进入 B 方法的线程就只能在等锁池（注意不是等待池哦）中等待对象的锁。

# 锁

## 锁总结

[参考美团技术团队](https://tech.meituan.com/2018/11/15/java-lock.html)
![image](https://awps-assets.meituan.net/mit-x/blog-images-bundle-2018b/7f749fc8.png)

### 乐观锁 VS 悲观锁

**悲观锁**

总是假设最坏的情况，每次去拿数据的时候都认为别人会修改，所以每次在拿数据的时候都会上锁，这样别人想拿这个数据就会阻塞直到它拿到锁（共享资源每次只给一个线程使用，其它线程阻塞，用完后再把资源转让给其它线程）。传统的关系型数据库里边就用到了很多这种锁机制，比如行锁，表锁等，读锁，写锁等，都是在做操作之前先上锁。Java 中 synchronized 和 ReentrantLock 等独占锁就是悲观锁思想的实现。

**乐观锁**

总是假设最好的情况，每次去拿数据的时候都认为别人不会修改，所以不会上锁，但是在更新的时候会判断一下在此期间别人有没有去更新这个数据，可以使用版本号机制和 CAS 算法实现。乐观锁适用于多读的应用类型，这样可以提高吞吐量，像数据库提供的类似于 write_condition 机制，其实都是提供的乐观锁。在 Java 中 java.util.concurrent.atomic 包下面的原子变量类就是使用了乐观锁的一种实现方式 CAS 实现的。

**两种锁的使用场景**

乐观锁适用于写比较少的情况下（多读场景），即冲突真的很少发生的时候，这样可以省去了锁的开销，加大了系统的整个吞吐量。但如果是多写的情况，一般会经常产生冲突，这就会导致上层应用会不断的进行 retry，这样反倒是降低了性能，所以一般多写的场景下用悲观锁就比较合适。

**乐观锁常见的两种实现方式**

1. 版本号机制：

   一般是在数据表中加上一个数据版本号 version 字段，表示数据被修改的次数，当数据被修改时，version 值会加一。当线程 A 要更新数据值时，在读取数据的同时也会读取 version 值，在提交更新时，若刚才读取到的 version 值为当前数据库中的 version 值相等时才更新，否则重试更新操作，直到更新成功。

2. CAS 算法

   即 compare and swap（比较与交换），是一种有名的无锁算法。无锁编程，即不使用锁的情况下实现多线程之间的变量同步，也就是在没有线程被阻塞的情况下实现变量的同步，所以也叫非阻塞同步（Non-blocking Synchronization）。CAS 算法涉及到三个操作数：

   1. 需要读写的内存值 V
   2. 进行比较的值 A
   3. 拟写入的新值 B

   当且仅当 V 的值等于 A 时，CAS 通过原子方式用新值 B 来更新 V 的值，否则不会执行任何操作（比较和替换是一个原子操作）。一般情况下是一个自旋操作，即不断的重试。

**乐观锁的缺点**

1. ABA 问题。

   如果一个变量 V 初次读取的时候是 A 值，并且在准备赋值的时候检查到它仍然是 A 值，在这段时间它的值可能被改为其他值，然后又改回 A，那 CAS 操作就会误认为它从来没有被修改过。这个问题被称为 CAS 操作的 "ABA"问题。JDK 1.5 以后的 AtomicStampedReference 类就提供了此种能力，其中的 compareAndSet 方法就是首先检查当前引用是否等于预期引用，并且当前标志是否等于预期标志，如果全部相等，则以原子方式将该引用和该标志的值设置为给定的更新值。

2. 循环时间长开销大。

   自旋 CAS（也就是不成功就一直循环执行直到成功）如果长时间不成功，会给 CPU 带来非常大的执行开销。

3. 只能保证一个共享变量的原子操作。

   CAS 只对单个共享变量有效，当操作涉及跨多个共享变量时 CAS 无效。但是从 JDK 1.5 开始，提供了 AtomicReference 类来保证引用对象之间的原子性，你可以把多个变量放在一个对象里来进行 CAS 操作.所以我们可以使用锁或者利用 AtomicReference 类把多个共享变量合并成一个共享变量来操作。

**CAS 与 synchronized 的使用情景**

CAS 适用于写比较少的情况下（多读场景，冲突一般较少）

synchronized 适用于写比较多的情况下（多写场景，冲突一般较多）

对于资源竞争较少（线程冲突较轻）的情况，使用 synchronized 同步锁进行线程阻塞和唤醒切换以及用户态内核态间的切换操作额外浪费消耗 cpu 资源；而 CAS 基于硬件实现，不需要进入内核，不需要切换线程，操作自旋几率较少，因此可以获得更高的性能。

对于资源竞争严重（线程冲突严重）的情况，CAS 自旋的概率会比较大，从而浪费更多的 CPU 资源，效率低于 synchronized。

[乐观锁悲观锁参考文章](https://blog.csdn.net/qq_34337272/article/details/81072874)

### 自旋锁 VS 适应性自旋锁

> 阻塞或唤醒一个 Java 线程需要操作系统切换 CPU 状态来完成，这种状态转换需要耗费处理器时间。如果同步代码块中的内容过于简单，状态转换消耗的时间有可能比用户代码执行的时间还要长。

- 自旋锁：
  请求锁的线程不放弃 CPU 的执行时间进行自旋操作。
  在许多场景中，同步资源的锁定时间很短，为了这一小段时间去切换线程，线程挂起和恢复现场的花费可能会让系统得不偿失。
  自旋等待虽然避免了线程切换的开销，但它要占用处理器时间。如果锁被占用的时间很短，自旋等待的效果就会非常好。反之，如果锁被占用的时间很长，那么自旋的线程只会白浪费处理器资源

* 自适应的自旋锁（适应性自旋锁）：
  自适应意味着自旋的时间（次数）不再固定，而是由前一次在同一个锁上的自旋时间及锁的拥有者的状态来决定。如果在同一个锁对象上，自旋等待刚刚成功获得过锁，并且持有锁的线程正在运行中，那么虚拟机就会认为这次自旋也是很有可能再次成功，进而它将允许自旋等待持续相对更长的时间。如果对于某个锁，自旋很少成功获得过，那在以后尝试获取这个锁时将可能省略掉自旋过程，直接阻塞线程，避免浪费处理器资源。

### 无锁 VS 偏向锁 VS 轻量级锁 VS 重量级锁

jdk1.6 对锁的实现引入了大量的优化，如自旋锁、适应性自旋锁、锁消除、锁粗化、偏向锁、轻量级锁等技术来减少锁操作的开销。锁主要存在四中状态，依次是：无锁状态、偏向锁状态、轻量级锁状态、重量级锁状态。

> 偏向锁通过对比 Mark Word 解决加锁问题，避免执行 CAS 操作。而轻量级锁是通过用 CAS 操作和自旋来解决加锁问题，避免线程阻塞和唤醒而影响性能。重量级锁是将除了拥有锁的线程以外的线程都阻塞。

![](https://ws1.sinaimg.cn/large/d4556b75ly1g3ny0kv6tyj20jw065myt.jpg)

- java 对象头

  synchronized 用的锁是存在 Java 对象头里的。synchronized 是悲观锁，在操作同步资源之前需要给同步资源先加锁，这把锁就是存在 Java 对象头里的。Hotspot 的对象头主要包括两部分数据：Mark Word（标记字段）、Klass Pointer（类型指针）

  - Mark Word ：默认存储对象的 HashCode，分代年龄和锁标志位信息
  - Klass Pointer ：对象指向它的类元数据的指针，虚拟机通过这个指针来确定这个对象是哪个类的实例

- Moniter

  Monitor 是线程私有的数据结构，每一个被锁住的对象都会和一个 monitor 关联，同时 monitor 中有一个 Owner 字段存放拥有该锁的线程的唯一标识，表示该锁被这个线程占用

- 无锁

  无锁没有对资源进行锁定，所有的线程都能访问并修改同一个资源，但同时只有一个线程能修改成功。CAS 原理及应用即是无锁的实现

- 偏向锁
  - 概念：
    指一段同步代码一直被一个线程所访问，那么该线程会自动获取锁，降低获取锁的代价。
  - 介绍：
    当一个线程访问同步代码块并获取锁时，会在 Mark Word 里存储锁偏向的线程 ID。在线程进入和退出同步块时不再通过 CAS 操作来加锁和解锁，而是检测 Mark Word 里是否存储着指向当前线程的偏向锁。引入偏向锁是为了在无多线程竞争的情况下尽量减少不必要的轻量级锁执行路径，因为轻量级锁的获取及释放依赖多次 CAS 原子指令，而偏向锁只需要在置换 ThreadID 的时候依赖一次 CAS 原子指令即可。
- 轻量级锁
  - 概念：
    是指当锁是偏向锁的时候，被另外的线程所访问，偏向锁就会升级为轻量级锁，其他线程会通过自旋的形式尝试获取锁，不会阻塞，从而提高性能。
  - 介绍：
    - 在代码进入同步块的时候，如果同步对象锁状态为无锁状态（锁标志位为“01”状态，是否为偏向锁为“0”），虚拟机首先将在当前线程的栈帧中建立一个名为锁记录（Lock Record）的空间，用于存储锁对象目前的 Mark Word 的拷贝，然后拷贝对象头中的 Mark Word 复制到锁记录中。
    - 拷贝成功后，虚拟机将使用 CAS 操作尝试将对象的 Mark Word 更新为指向 Lock Record 的指针，并将 Lock Record 里的 owner 指针指向对象的 Mark Word。
    - 如果这个更新动作成功了，那么这个线程就拥有了该对象的锁，并且对象 Mark Word 的锁标志位设置为“00”，表示此对象处于轻量级锁定状态。
    - 如果轻量级锁的更新操作失败了，虚拟机首先会检查对象的 Mark Word 是否指向当前线程的栈帧，如果是就说明当前线程已经拥有了这个对象的锁，那就可以直接进入同步块继续执行，否则说明多个线程竞争锁。
    - 若当前只有一个等待线程，则该线程通过自旋进行等待。但是当自旋超过一定的次数，或者一个线程在持有锁，一个在自旋，又有第三个来访时，轻量级锁升级为重量级锁。
- 重量级锁

  升级为重量级锁时，锁标志的状态值变为“10”，此时 Mark Word 中存储的是指向重量级锁的指针，此时等待锁的线程都会进入阻塞状态。

### 公平锁 VS 非公平锁

> 公平锁就是通过同步队列来实现多个线程按照申请锁的顺序来获取锁，从而实现公平的特性。非公平锁加锁时不考虑排队等待问题，直接尝试获取锁，所以存在后申请却先获得锁的情况。

- 公平锁
  - 概念 ：多个线程按照申请锁的顺序来获取锁，线程直接进入队列中排队，队列中的第一个线程才能获得锁
  - 优点：等待锁的线程不会饿死
  - 缺点：整体吞吐效率相对非公平锁要低，等待队列中除第一个线程以外的所有线程都会阻塞，CPU 唤醒阻塞线程的开销比非公平锁大
- 非公平锁
  - 概念 ：多个线程加锁时直接尝试获取锁，获取不到才会到等待队列的队尾等待。但如果此时锁刚好可用，那么这个线程可以无需阻塞直接获取到锁，所以非公平锁有可能出现后申请锁的线程先获取锁的场景
  - 优点：可以减少唤起线程的开销，整体的吞吐效率高，因为线程有几率不阻塞直接获得锁，CPU 不必唤醒所有线程
  - 缺点：处于等待队列中的线程可能会饿死，或者等很久才会获得锁
- ReentrantLock

  - ReentrantLock 实现代码如下：
    ![](https://awps-assets.meituan.net/mit-x/blog-images-bundle-2018b/6edea205.png)
    ReentrantLock 里面有一个内部类 Sync，Sync 继承 AQS（AbstractQueuedSynchronizer），添加锁和释放锁的大部分操作实际上都是在 Sync 中实现的。它有公平锁 FairSync 和非公平锁 NonfairSync 两个子类。ReentrantLoc 默认使用非公平锁，也可以通过构造器来显示的指定使用公平锁。
  - 公平锁与非公平锁的 lock()方法唯一的区别：
    就在于公平锁在获取同步状态时多了一个限制条件：hasQueuedPredecessors()，该方法返回 true 或者 false，如果当前线程之前有一个排队的线程则返回 true，如果当前线程位于队列头部或者队列为空返回 false
    ![](https://awps-assets.meituan.net/mit-x/blog-images-bundle-2018b/bc6fe583.png)
    ```java
    final void lock() {
        acquire(1);
    }
    public final void acquire(int arg) {
        if (!tryAcquire(arg) &&
            acquireQueued(addWaiter(Node.EXCLUSIVE), arg))
            selfInterrupt();
    }
    ```
  - lock 方法对比非公平锁， 新来的线程没有插队的机会， 所有来的线程必须扔到队列尾部， acquire 方法也会像非公平锁一样首先调用 tryAcquire 插队试试，但是只有队列为空或着本身就是 head，那么才可能成功，如果队列非空那么肯定被扔到队列尾部去了。

### 可重入锁 VS 非可重入锁

- 可重入锁
  - 概念：是指在同一个线程在外层方法获取锁的时候，再进入该线程的内层方法会自动获取锁（前提锁对象得是同一个对象或者 class），不会因为之前已经获取过还没释放而阻塞
  - 优点：一定程度上可以避免死锁

### 独享锁 VS 共享锁

- 独享锁：也叫排他锁，是指该锁一次只能被一个线程所持有，如果线程 T 对数据 A 加上排它锁后，则其他线程不能再对 A 加任何类型的锁
- 共享锁：该锁可被多个线程所持有，如果线程 T 对数据 A 加上共享锁后，则其他线程只能对 A 再加共享锁，不能加排它锁
- ReentrantReadWriteLock
  下图为 ReentrantReadWriteLock 的部分源码：
  ![](https://awps-assets.meituan.net/mit-x/blog-images-bundle-2018b/762a042b.png)
  由代码可知：ReentrantReadWriteLock 有两把锁：ReadLock 和 WriteLock，ReadLock 和 WriteLock 是靠内部类 Sync 实现的锁。读锁是共享锁，写锁是独享锁，读锁的共享锁可保证并发读非常高效，而读写、写读、写写的过程互斥
  ReentrantReadWriteLock 中的 state 变量“按位切割”切分成了两个部分，高 16 位表示读锁状态（读锁个数），低 16 位表示写锁状态（写锁个数）。

## 讲一下非公平锁和公平锁在 reetrantlock 里的实现

[参考](https://blog.csdn.net/lsgqjh/article/details/63685058)

非公平锁: 当线程争夺锁的过程中，会先进行一次 CAS 尝试获取锁，若失败，则进入 acquire(1)函数，进行一次 tryAcquire 再次尝试获取锁，若再次失败，那么就通过 addWaiter 将当前线程封装成 node 结点加入到 Sync 队列，这时候该线程只能乖乖等前面的线程执行完再轮到自己了。

公平锁: 当线程在获取锁的时候，会先判断 Sync 队列中是否有在等待获取资源的线程。若没有，则尝试获取锁，若有，那么就那么就通过 addWaiter 将当前线程封装成 node 结点加入到 Sync 队列中。

## 讲一下 synchronized，可重入怎么实现

实现方法是为每个锁关联一个线程持有者 Moniter 和计数器 status，当计数器为 0 时表示该锁没有被任何线程持有，那么任何线程都可能获得该锁而调用相应的方法；当某一线程请求成功后，JVM 会记下锁的持有线程，并且将计数器置为 1；此时其它线程请求该锁，则必须等待；而该持有锁的线程如果再次请求这个锁，就可以再次拿到这个锁，同时计数器会递增；当线程退出同步代码块时，计数器会递减，如果计数器为 0，则释放该锁。

## 锁和同步的区别

1. Lock 是一个接口，而 synchronized 是 Java 中的关键字
2. synchronized 是内置的语言实现，synchronized 是在 JVM 层面上实现的，不但可以通过一些监控工具监控 synchronized 的锁定，而且在代码执行时出现异常，JVM 会自动释放锁定，但是使用 Lock 则不行，lock 是通过代码实现的，要保证锁定一定会被释放，就必须将 unLock()放到 finally{} 中
3. Lock 可以让等待的线程响应中断，线程可以去做别的事情；synchronized 不行，等待的线程会一直等下去，不能够响应中断
4. Lock 可以知道是否获取到锁，知道锁的状态，而 synchronized 却无法办到
5. Lock 可以提高多个线程进行读操作的效率。

## 什么是死锁(deadlock)？

死锁是指两个或两个以上的进程在执行过程中，由于竞争资源或者由于彼此通信而造成的一种阻塞的现象，若无外力作用，它们都将无法推进下去。此时称系统处于死锁状态或系统产生了死锁。
死锁产生有四个必要条件，打破任意一个，就能打破死锁状态:

1. 互斥条件: 一个资源每次只能被一个进程使用
2. 请求与保持: 一个进程因请求资源而阻塞时，对已获得的资源保持不放
3. 不剥夺: 进程已获得的资源，在末使用完之前，不能强行剥夺
4. 循环等待: 若干进程之间形成一种头尾相接的循环等待资源关系

## 如何确保 N 个线程可以访问 N 个资源同时又不导致死锁？

死锁产生有四个必要条件，打破任意一个，就能打破死锁状态:
互斥条件、请求与保持、不剥夺和循环等待。

1. 指定获取锁的顺序，并强制线程按照指定的顺序获取锁。因此，如果所有的线程都是以同样的顺序加锁和释放锁，就不会出现死锁了。 缺点：需要手动对锁的获得顺序进行分析
2. 指定加锁时限：线程指定超时时间，若无法获得锁的占用权，进行回退操作，并释放已占用的锁，经一段延时后再尝试进行任务。缺点 ：线程过多的话，可能造成频繁回退，运行效率不高。
3. 死锁检测：将线程和已获得锁的情况记录下来，定时检测是否所有死锁现象（线程循环等待现象），回退处于死锁状态的线程，延时后，重试这些线程，与添加加锁时限类似，缺点也同。

## ReentrantLock 中公平锁和非公平锁在哪里体现的？

lock 方法对比非公平锁， 没有了 if else 也就意味着新来的线程没有插队的机会， 所有来的线程必须扔到队列尾部， acquire 方法也会像非公平锁一样首先调用 tryAcquire 插队试试，但是只有队列为空或着本身就是 head，那么才可能成功，如果 队列非空那么肯定被扔到队列尾部去了。

## volatile 的实现原理

[Java 并发编程：volatile 关键字解析](https://www.cnblogs.com/dolphin0520/p/3920373.html)

synchronized 是一个重量级的锁，虽然 JVM 对它做了很多优化，而 volatile 则是轻量级的 synchronized

指令重排序不会影响单个线程的执行，但是会影响到线程并发执行的正确性，也就是说，要想并发程序正确地执行，必须要保证原子性、可见性以及有序性。在 Java 里面，可以通过 volatile 关键字来保证一定的“有序性”。另外可以通过 synchronized 和 Lock 来保证有序性。

**volatile 有两层语义：**

1. 保证可见性、不保证原子性

   > 可见性：对一个 volatile 变量的读，总能看到（任意线程）对这个 volatile 变量最后的写入

   > 原子性：对任意单个 volatile 变量的读/写具有原子性，但类似于 volatile++ 这种符合操作不具有原子性。

2. 禁止指令重排序

**volatile 写-读内存语义：**

1. 当写一个 volatile 变量时，JVM 会把该线程对应的本地内存中的共享变量值刷新到主内存。
2. 当读一个 volatile 变量时，JVM 会把该线程对应的本地内存值置为无效，线程接下来从主内存中读取共享变量值。

**volatile 重排序规则：**

1. volatile 写之前的操作不会被编译器重排序到 volatile 写之后；
2. volatile 读之后的操作不会被编译器重排序到 volatile 读之前；
3. 第一个操作是 volatile 写，第二个操作是 volatile 读时，不能重排序。

![image](https://gitee.com/chenssy/blog-home/raw/master/image/201905/201905161002.png)

加入 volatile 关键字时，会多出一个 lock 前缀指令，
lock 前缀指令实际上相当于一个内存屏障（内存栅栏），内存屏障会提供 3 个功能：

1. 它确保指令重排序时不会把其后面的指令排到内存屏障之前的位置，也不会把前面的指令排到内存屏障的后面；即在执行到内存屏障这句指令时，在它前面的操作已经全部完成；
2. 它会强制将对缓存的修改操作立即写入主存；
3. 如果是写操作，它会导致其他 CPU 中对应的缓存行无效。

**通常来说，使用 volatile 必须具备以下 2 个条件：**

1. 对变量的写操作不依赖于当前值
2. 该变量没有包含在具有其他变量的不变式中

**volatile 场景：**

1. 状态标记量
2. double check，单例模式下的双重检查

# 底层原理

[并发编程(好文强推)](https://www.hollischuang.com/archives/category/java/%e5%b9%b6%e5%8f%91%e7%bc%96%e7%a8%8b)

## java 内存模型

**Java 内存模型**

[求你了，再问你 Java 内存模型的时候别再给我讲堆栈方法区了…](https://www.hollischuang.com/archives/3781)

~~线程间共享变量存储在主内存，每个线程都有自己的本地内存，存储的是共享变量在本地的副本。线程对变量的所有操作都必须在工作内存中进行，不同线程也无法访问到对方工作内存中的变量，线程间变量值的传递都需要经过主内存来完成。存在的原子性、可见性（缓存一致性）以及有序性问题。~~

Java 内存模型，其实是保证了 Java 程序在各种平台下对内存的访问都能够得到一致效果的机制及规范。目的是解决由于多线程通过共享内存进行通信时，存在的原子性、可见性（缓存一致性）以及有序性问题。

除此之外，Java 内存模型还提供了一系列原语，封装了底层实现后，供开发者直接使用。如我们常用的一些关键字：synchronized、volatile 以及并发包等。

1. 原子性：  
   在 Java 中，为了保证原子性，提供了两个高级的字节码指令 monitorenter 和 monitorexit。这两个字节码，在 Java 中对应的关键字就是 synchronized，因此在 Java 中可以使用 synchronized 来保证方法和代码块内的操作是原子性的
2. 可见性：  
   Java 内存模型是通过在变量修改后将新值同步回主内存，在变量读取前从主内存刷新变量值的这种依赖主内存作为传递媒介的方式来实现的。Java 中的 volatile 关键字提供了一个功能，除了 volatile，Java 中的 synchronized 和 final 两个关键字也可以实现可见性。
3. 有序性：  
   在 Java 中，可以使用 synchronized 和 volatile 来保证多线程之间操作的有序性。实现方式有所区别：  
   volatile 关键字会禁止指令重排。synchronized 关键字保证同一时刻只允许一条线程操作。

## synchronized 底层原理

[Synchronized 的实现原理（一）](http://www.hollischuang.com/archives/1883)

synchronized 有两种使用形式，同步方法和同步代码块，对于同步方法，JVM 采用`ACC_SYNCHRONIZED`标记符来实现同步。 对于同步代码块。JVM 采用`monitorenter`、`monitorexit`两个指令来实现同步。

**同步方法：**

方法级的同步是隐式的。同步方法的常量池中会有一个 `ACC_SYNCHRONIZED` 标志。当某个线程要访问某个方法的时候，会检查是否有 `ACC_SYNCHRONIZED`，如果有设置，则需要先获得监视器锁，然后开始执行方法，方法执行之后再释放监视器锁。这时如果其他线程来请求执行方法，会因为无法获得监视器锁而被阻断住。值得注意的是，如果在方法执行过程中，发生了异常，并且方法内部并没有处理该异常，那么在异常被抛到方法外面之前监视器锁会被自动释放。

**同步代码块：**

同步代码块使用 `monitorenter` 和 `monitorexit`两个指令实现。

可以把执行 `monitorenter` 指令理解为加锁，执行 `monitorexit` 理解为释放锁。 每个对象维护着一个记录着被锁次数的计数器。未被锁定的对象的该计数器为 0，当一个线程获得锁（执行 monitorenter）后，该计数器自增变为 1 ，当同一个线程再次获得该对象的锁的时候，计数器再次自增。当同一个线程释放锁（执行 monitorexit 指令）的时候，计数器再自减。当计数器为 0 的时候，锁将被释放，其他线程便可以获得锁。

## java 对象头

[深入理解多线程（三）—— Java 的对象头](https://www.hollischuang.com/archives/1953)

在 HotSpot 虚拟机中，使用 oop-klass 模型来表示对象。每一个 Java 类，在被 JVM 加载的时候，JVM 会给这个类创建一个 `instanceKlass`，保存在方法区，用来在 JVM 层表示该 Java 类。

当我们在 Java 代码中，使用 new 创建一个对象的时候，JVM 会创建一个 `instanceOopDesc` 对象，这个对象中包含了两部分信息，对象头以及元数据。对象头中有一些运行时数据，其中就包括和多线程相关的锁的信息。元数据其实维护的是指针，指向的是对象所属的类的 `instanceKlass`。

对象头信息是与对象自身定义的数据无关的额外存储成本，考虑到虚拟机的空间效率，Mark Word 被设计成一个非固定的数据结构以便在极小的空间内存储尽量多的信息，它会根据对象的状态复用自己的存储空间。

![image](https://www.hollischuang.com/wp-content/uploads/2018/01/ObjectHead.png)

可以看出，对象头中主要包含了 GC 分代年龄、锁状态标记、哈希码、epoch 等信息。

从上图中可以看出，对象的状态一共有五种，分别是无锁态、轻量级锁、重量级锁、GC 标记和偏向锁，在 32 位的虚拟机中有两个 Bits 是用来存储锁的标记位的，第五种状态额外依赖 1Bit 的空间，使用 0 和 1 来区分来表示，额外的标记为用来区分无锁和偏向锁状态。

## Monitor

> 无论是同步方法还是同步代码块，无论是 `ACC_SYNCHRONIZED` 还是 `monitorenter`、`monitorexit` 都是基于 `Monitor` 实现的

Monitor 其实是一种同步工具，也可以说是一种同步机制，它通常被描述为一个对象，基于 c++ 实现的，表示为一个类 objectMonitor 对象，objectMonitor 中几个关键属性：

- `_owner`：指向持有 Monitor 对象的线程
- `_WaitSet`：存放处于 wait 状态的线程队列
- `_recursions`：锁的重入次数
- `count`：用来记录该线程获取锁的次数
- `_EntryList`：存放处于等待锁 block 状态的线程队列

当多个线程同时访问一段同步代码时，首先会进入`_EntryList`队列中，当某个线程获取到对象的 monitor 后进入`_Owner`区域并把 monitor 中的`_owner`变量设置为当前线程，同时 monitor 中的计数器`_count`加 1。即获得对象锁。

若持有 monitor 的线程调用 wait()方法，将释放当前持有的 monitor，`_owner`变量恢复为 null，`_count`自减 1，同时该线程进入`_WaitSet`集合中等待被唤醒。若当前线程执行完毕也将释放 monitor(锁)并复位变量的值，以便其他线程进入获取 monitor(锁)

![image](https://www.hollischuang.com/wp-content/uploads/2017/12/monitor.png)

ObjectMonitor 类中提供了几个方法，如`enter`、`exit`、`wait`、`notify`、`notifyAll`等。`sychronized` 加锁的时候，会调用 objectMonitor 的 `enter` 方法，解锁的时候会调用 `exit` 方法。

## Executors 线程池，为什么不建议使用这个类来创建线程池呢？如何创建？

[Java 中线程池，你真的会用吗？](https://www.hollischuang.com/archives/2888)

Executors 是一个 Java 中的工具类。提供工厂方法来创建不同类型的线程池。常用方法有以下几个：

- `newFiexedThreadPool(int Threads)`：创建固定数目线程的线程池。
- `newCachedThreadPool()`：创建一个可缓存的线程池，调用 execute 将重用以前构造的线程（如果线程可用）。如果没有可用的线程，则创建一个新线程并添加到池中。终止并从缓存中移除那些已有 60 秒钟未被使用的线程
- `newSingleThreadExecutor()`：创建一个单线程化的 Executor。
- `newScheduledThreadPool(int corePoolSize)`：创建一个支持定时及周期性的任务执行的线程池，多数情况下可用来替代 Timer 类。

使用 Executors 创建线程池可能会导致 OOM(OutOfMemory 内存溢出)，Executors 其实底层确实是通过 LinkedBlockingQueue 实现的，newFixedThreadPool 中创建 `LinkedBlockingQueue` 时，并未指定容量。此时，`LinkedBlockingQueue` 就是一个无边界队列，对于一个无边界队列来说，是可以不断的向队列中加入任务的，这种情况下就有可能因为任务过多而导致内存溢出问题。

避免使用 Executors 创建线程池，主要是避免使用其中的默认实现，那么我们可以自己直接调用 `ThreadPoolExecutor` 的构造函数来自己创建线程池。在创建的同时，给 `BlockingQueue` 指定容量就可以了。

```java
private static ExecutorService executor = new ThreadPoolExecutor(10, 10,
        60L, TimeUnit.SECONDS,
        new ArrayBlockingQueue(10)
    );
```

这种情况下，一旦提交的线程数超过当前可用线程数时，就会抛出 `java.util.concurrent.RejectedExecutionException`，这是因为当前线程池使用的队列是有边界队列，队列已经满了便无法继续处理新的请求。

## 阻塞队列

Java 中的阻塞队列 `BlockingQueue` 主要有两种实现，分别是 `ArrayBlockingQueue` 和 `LinkedBlockingQueue`。

### ArrayBlockingQueue

[【死磕 Java 集合】— ArrayBlockingQueue 源码分析](http://cmsblogs.com/?p=4755)

- 是一个用数组实现的有界阻塞队列，其大小在构造时由构造函数来决定，确认之后就不能再改变了。
- 支持对等待的生产者线程和使用者线程进行排序的可选公平策略，但是在默认情况下不保证线程公平的访问，在构造时可以选择公平策略（fair = true）。公平性通常会降低吞吐量，但是减少了可变性和避免了“不平衡性”。
- 继承 `AbstractQueue` ，实现 `BlockingQueue` 接口，继承 `java.util.Queue` 为阻塞队列的核心接口，提供了在多线程环境下的出列、入列操作。
- 内部使用可重入锁 ReentrantLock + Condition 来完成多线程环境的并发操，提供了诸多方法，可以将元素加入队列尾部。

**主要属性**

```java
// 保证并发访问的锁
final ReentrantLock lock;
// 非空条件
private final Condition notEmpty;
// 非满条件
private final Condition notFull;

// 初始化构造函数
public ArrayBlockingQueue(int capacity) {
    this(capacity, false);
}

public ArrayBlockingQueue(int capacity, boolean fair) {
    if (capacity <= 0)
        throw new IllegalArgumentException();
    // 初始化数组
    this.items = new Object[capacity];
    // 创建重入锁及两个条件
    lock = new ReentrantLock(fair);
    notEmpty = lock.newCondition();
    notFull =  lock.newCondition();
}
```

**入队**

`add(E e)` 将指定的元素插入到此队列的尾部，在成功时返回 true，如果此队列已满，则抛出 IllegalStateException

```java
  public boolean add(E e) {
      return super.add(e);
  }

  public boolean add(E e) {
      if (offer(e))
          return true;
      else
          throw new IllegalStateException("Queue full");
  }
```

`add` 方法调用 `offer(E e)`，如果返回 false 则抛出异常。`offer(E e)` 为其实现：

```java
  public boolean offer(E e) {
      checkNotNull(e);
      final ReentrantLock lock = this.lock;
      lock.lock();
      try {
          if (count == items.length)
              return false;
          else {
              enqueue(e);
              return true;
          }
      } finally {
          lock.unlock();
      }
  }
```

方法首先检查是否为 null，然后获取 lock 锁。获取锁成功后，如果队列已满则直接返回 false，否则调用 enqueue(E e)，enqueue(E e) 为入列的核心方法，所有入列的方法最终都将调用该方法在队列尾部插入元素：

```java
  private void enqueue(E x) {
      // assert lock.getHoldCount() == 1;
      // assert items[putIndex] == null;
      final Object[] items = this.items;
      items[putIndex] = x;
      if (++putIndex == items.length)
          putIndex = 0;
      count++;
      notEmpty.signal();
  }
```

该方法就是在 putIndex（队尾）处添加元素，最后使用 `notEmpty.signal()` 方法通知阻塞在**出列**的线程

**出队**

`poll()` 首先获取锁，如果队列为空 `count == 0` 返回 null，否则调用 `dequeue()` 获取列头元素：

```java
public E poll() {
        final ReentrantLock lock = this.lock;
        lock.lock();
        try {
            return (count == 0) ? null : dequeue();
        } finally {
            lock.unlock();
        }
    }
```

`dequeue()` 方法主要是从列头（takeIndex 位置）取出元素，同时如果迭代器 itrs 不为 null，则需要维护下该迭代器。最后调用`notFull.signal()` 唤醒**入列**线程。

`take()` 与 `poll()` 存在一个区别就是 count == 0 时的处理，`poll()` 直接返回 null，而 `take()` 则是在 notEmpty 上面等待直到被入列的线程唤醒。

### LinkedBlockingQueue

[【死磕 Java 集合】— LinkedBlockingQueue 源码分析](http://cmsblogs.com/?p=4759)

`LinkedBlockingQueue` 是一个用单链表实现的有界阻塞队列，容量可以选择进行设置，不设置的话，将是一个无边界的阻塞队列，最大长度为 Integer.MAX_VALUE。

**主要属性：**

```java
// 容量
private final int capacity;
// 元素数量
private final AtomicInteger count = new AtomicInteger();
// take锁
private final ReentrantLock takeLock = new ReentrantLock();
// notEmpty条件，当队列无元素时，take锁会阻塞在notEmpty条件上，等待其它线程唤醒
private final Condition notEmpty = takeLock.newCondition();
// 放锁
private final ReentrantLock putLock = new ReentrantLock();
// notFull条件，当队列满了时，put锁会会阻塞在notFull上，等待其它线程唤醒
private final Condition notFull = putLock.newCondition();
```

**入队**

`put(E e)` 方法主要流程：

1. 使用 putLock 加锁；
   ```java
    final ReentrantLock putLock = this.putLock;
   ```
2. 如果队列满了就阻塞在 notFull 条件上；

   ```java
    final AtomicInteger count = this.count;

    while (count.get() == capacity) {
            notFull.await();
    }
   ```

3. 否则就入队；
   ```java
    enqueue(node);
   ```
4. 如果入队后元素数量小于容量，唤醒其它阻塞在 notFull 条件上的线程；
   ```java
    c = count.getAndIncrement();
    if (c + 1 < capacity) {
        notFull.signal();
    }
   ```
5. 释放锁；
   ```java
    putLock.unlock();
   ```
6. 如果放元素之前队列长度为 0，就唤醒 notEmpty 条件；
   ```java
   // 如果原队列长度为0，现在加了一个元素后立即唤醒notEmpty条件
   if (c == 0)
       signalNotEmpty();
   ```

**出队**

`take()` 方法主要流程：

1. 使用 takeLock 加锁；
   ```java
    final ReentrantLock takeLock = this.takeLock;
    takeLock.lockInterruptibly();
   ```
2. 如果队列空了就阻塞在 notEmpty 条件上；
   ```java
    while (count.get() == 0) {
        notEmpty.await();
    }
   ```
3. 否则就出队；
   ```java
    x = dequeue();
    // 获取出队前队列的长度
    c = count.getAndDecrement();
   ```
4. 如果出队前元素数量大于 1，唤醒其它阻塞在 notEmpty 条件上的线程；
   ```java
    if (c > 1) {
        notEmpty.signal();
    }
   ```
5. 释放锁；
6. 如果取元素之前队列长度等于容量，就唤醒 notFull 条件；
   ```java
    // 如果取之前队列长度等于容量，取完之后则立即唤醒 notFull
    if (c == capacity)
        signalNotFull();
   ```

### 二者对比

1. `ArrayBlockingQueue` 入队出队采用一把锁，导致入队出队相互阻塞，效率低下；`LinkedBlockingQueue` 入队出队采用两把锁，入队出队互不干扰，效率较高；
2. 二者都是有界队列，如果长度相等且出队速度跟不上入队速度，都会导致大量线程阻塞；
3. `LinkedBlockingQueue` 如果初始化不传入初始容量，则使用最大 int 值，如果出队速度跟不上入队速度，会导致队列特别长，占用大量内存，有可能导致内存溢出
