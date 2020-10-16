# Java容器源码剖析

## ArrayList源码

## LinkedList源码

## HashMap源码
HashMap成环原因
假设1下面有a、b两个元素
每次扩容transfer，都是倒置。
线程1循环完毕后。其实线程2看到的

[成环原因](https://juejin.im/post/6844903942720061447)

HashMap

### 为什么Hashmap是两次幂

(n-1)&做hash来获得桶

做resize的时候会非常的方便



JDK1.8之后单个桶元素大于8个会使用红黑树



### HashMap和HashTable的区别

+ 线程安全和线程不安全

+ HashTable中的hash数组初始大小是11，增加的方式是 old*2+1。HashMap中hash数组的默认大小是16，而且一定是2的指数。
+ HashTable直接使用对象的hashCode。而HashMap重新计算hash值
+ HashMap允许null，在HashMap中不能由get()方法来判断HashMap中是否存在某个键， 而应该用containsKey()方法来判断
+ Hashtable是继承Dictionary类，HashMap继承AbstractMap。

### JDK1.7

### JDK1.8

## ConcurrentHashMap源码

