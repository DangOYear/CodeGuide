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