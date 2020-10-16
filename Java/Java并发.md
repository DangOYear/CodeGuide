# Java并发

## 线程池

线程池总共有7个参数



### corePoolSize 

线程池核心线程大小

### maximumPoolSize 

线程池最大线程数量

keepAliveTime 空闲线程存活时间

unit 空间线程存活时间单位

workQueue 工作队列

threadFactory 线程工厂

handler 拒绝策略

这里需要注意的是：在刚刚创建ThreadPoolExecutor的时候，线程并不会立即启动，而是要等到有任务提交时才会启动，除非调用了prestartCoreThread/prestartAllCoreThreads事先启动核心线程。

