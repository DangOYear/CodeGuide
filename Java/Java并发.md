# Java并发

## 线程池

线程池总共有7个参数



### corePoolSize 线程池核心线程大小

### maximumPoolSize 线程池最大线程数量

### keepAliveTime 空闲线程存活时间

### unit 空间线程存活时间单位

### workQueue 工作队列

### threadFactory 线程工厂

### handler 拒绝策略



**这里需要注意的是：在刚刚创建ThreadPoolExecutor的时候，线程并不会立即启动，而是要等到有任务提交时才会启动，除非调用了prestartCoreThread/prestartAllCoreThreads事先启动核心线程。**

### 四个线程池

- newCachedThreadPool创建一个可缓存线程池，如果线程池长度超过处理需要，可灵活回收空闲线程，若无可回收，则新建线程。
- newFixedThreadPool 创建一个定长线程池，可控制线程最大并发数，超出的线程会在队列中等待。
- newScheduledThreadPool 创建一个定长线程池，支持定时及周期性任务执行。
- newSingleThreadExecutor 创建一个单线程化的线程池，它只会用唯一的工作线程来执行任务，保证所有任务按照指定顺序(FIFO, LIFO, 优先级)执行。

## Synchronize

因为监视器锁（monitor）是依赖于底层的操作系统的 Mutex Lock来实现的，Java 的线程是映射到操作系统的原生线程之上的。如果要挂起或者唤醒一个线程，都需要操作系统帮忙完成，而操作系统实现线程之间的切换时需要从用户态转换到内核态，这个状态之间的转换需要相对比较长的时间，时间成本相对高。

Synchronize同步语句块使用monitorenter和monitorexit，修饰方法的时候用的是ACC_SYNCHRONIZED来标记是一个同步方法。

不过本质上都是对监视器锁的获取。



## Synchronize和ReentrantLock区别

### 相似点

+ 都是可重入的

### 不同点

+ Synchronize由JVM底层实现。ReentrantLock它是JDK 1.5之后提供的API层面的互斥锁
+ ReentrantLock可以放弃当前等待，转而处理其他事情。
+ ReentrantLock可以实现公平锁。
+ ReentrantLock可实现选择性通知。

## volatile关键字

+ volatile可保证**可见性**，保证每次都是去内存读取。
+ 可以禁止指令重排序。
+ 不能保证原子性。



## ThreadLocal

### 用途

主要用于线程拥有属于自己的变量。

主要方法是使用get()和set()。

创建一个ThreadLocal变量，访问该变量的所有线程都会有这个变量的本地副本。

### 实现原理

调用get()和set()其实调用的是ThreadLocalMap对应的get()和set()方法。

```java
    /**
     * Returns the value in the current thread's copy of this
     * thread-local variable.  If the variable has no value for the
     * current thread, it is first initialized to the value returned
     * by an invocation of the {@link #initialValue} method.
     *
     * @return the current thread's value of this thread-local
     */
    public T get() {
        Thread t = Thread.currentThread();
        ThreadLocalMap map = getMap(t);
        if (map != null) {
            ThreadLocalMap.Entry e = map.getEntry(this);
            if (e != null) {
                @SuppressWarnings("unchecked")
                T result = (T)e.value;
                return result;
            }
        }
        return setInitialValue();
    }
```

```java

    /**
     * Sets the current thread's copy of this thread-local variable
     * to the specified value.  Most subclasses will have no need to
     * override this method, relying solely on the {@link #initialValue}
     * method to set the values of thread-locals.
     *
     * @param value the value to be stored in the current thread's copy of
     *        this thread-local.
     */
    public void set(T value) {
        Thread t = Thread.currentThread();
        ThreadLocalMap map = getMap(t);
        if (map != null)
            map.set(this, value);
        else
            createMap(t, value);
    }
```

## CAS（Compare and swap）

### 简介

在不使用锁的情况下实现同步

CAS涉及到三个操作数。需要读写的内存值等于比较的值（之前读取的内存值）时，通过原子方式用新值来更新内存值。

### 存在问题

+ ABA问题
  + 可能其他线程进行了修改但是改回来了，此时当前进程会认为没有修改。可以使用版本号来处理。
+ 循环时间开销大
  + 一直重试开销大。

## AQS

![AQS原理图](../img/JavaJava并发AQS原理图.png)

