# 创建型模式

## 单例模式

### 简介

单例模式（Singleton Pattern）是 Java 中最简单的设计模式之一。这种类型的设计模式属于创建型模式，它提供了一种创建对象的最佳方式

这种模式涉及到一个单一的类，该类负责创建自己的对象，同时确保只有单个对象被创建。这个类提供了一种访问其唯一的对象的方式，可以直接访问，不需要实例化该类的对象

### 主要解决


+ 一个全局使用的类频繁地创建与销毁

### 优点

+ 在内存里只有一个实例，减少了内存的开销，尤其是频繁的创建和销毁实例（比如管理学院首页页面缓存）
+ 避免对资源的多重占用（比如写文件操作）

### 缺点

+ 没有接口，不能继承，与单一职责原则冲突，一个类应该只关心内部逻辑，而不关心外面怎么样来实例化

单例模式有众多种类

### 懒汉式（线程不安全）

```java
/**
 *
 * Lazy初始化
 * 多线程不安全
 *
 * 不支持多线程，因为没有加锁。再多线程模式下可能会产生多个instance
 *
 */
public class SingletonLazyNotThreadSafe {

    private static SingletonLazyNotThreadSafe instance;

    private SingletonLazyNotThreadSafe(){}

    public static SingletonLazyNotThreadSafe getInstance() {
        if (instance == null) {
            instance = new SingletonLazyNotThreadSafe();
        }
        return instance;
    }
}
```



### 懒汉式（线程安全）

```java
/**
 *
 * Lazy初始化
 *
 * 多线程安全
 *
 * 这种方式具备很好的 lazy loading，能够在多线程中很好的工作，但是，效率很低，99% 情况下不需要同步。
 * 优点：第一次调用才初始化，避免内存浪费。
 * 缺点：必须加锁 synchronized 才能保证单例，但加锁会影响效率。
 *
 */
public class SingletonLazyThreadSafe {

    private static SingletonLazyThreadSafe instance;


    private SingletonLazyThreadSafe() {}

    public static synchronized SingletonLazyThreadSafe getInstance() {
        if (instance == null) {
            instance = new SingletonLazyThreadSafe();
        }
        return instance;
    }

}
```



### 饿汉式

```java
/**
 * 多线程安全
 *
 * 种方式比较常用，但容易产生垃圾对象。
 * 优点：没有加锁，执行效率会提高。
 * 缺点：类加载时就初始化，浪费内存。
 * 它基于 classloader 机制避免了多线程的同步问题，不过，instance 在类装载时就实例化，
 * 虽然导致类装载的原因有很多种，在单例模式中大多数都是调用 getInstance 方法，
 * 但是也不能确定有其他的方式（或者其他的静态方法）导致类装载，这时候初始化 instance 显然没有达到 lazy loading 的效果。
 *
 */
public class SingletonHungry {

    private static SingletonHungry instance = new SingletonHungry();

    private SingletonHungry() {}

    public static SingletonHungry getInstance() {
        return instance;
    }

}
```



### DoubleCheckLock（重要）

```java
/**
 * Lazy初始化
 *
 * 线程安全
 *
 * 使用双锁机制，安全且在多线程情况下能保持高性能
 *
 */

public class SingletonDoubleCheckedLocking {

    private volatile static SingletonDoubleCheckedLocking singleton;

    private SingletonDoubleCheckedLocking () {}

    public static SingletonDoubleCheckedLocking getSingleton() {
        if (singleton == null) {
            synchronized (SingletonDoubleCheckedLocking.class) {
                if (singleton == null) {
                    singleton = new SingletonDoubleCheckedLocking();
                }
            }
        }
        return singleton;
    }

}
```



### 静态内部类实现

```java
/**
 * Lazy初始化
 *
 * 线程安全
 *
 * 这种方式能达到双检锁方式一样的功效，但实现更简单。
 * 对静态域使用延迟初始化，应使用这种方式而不是双检锁方式。这种方式只适用于静态域的情况，双检锁方式可在实例域需要延迟初始化时使用。
 *
 * 这种方式同样利用了 classloader 机制来保证初始化 instance 时只有一个线程，
 *
 * 它跟第 3 种方式不同的是：第 3 种方式只要 Singleton 类被装载了，那么 instance 就会被实例化（没有达到 lazy loading 效果）
 * ，而这种方式是 Singleton 类被装载了，instance 不一定被初始化。因为 SingletonHolder 类没有被主动使用，只有通过显式调用 getInstance 方法时，
 * 才会显式装载 SingletonHolder 类，从而实例化 instance。
 *
 * 想象一下，如果实例化 instance 很消耗资源，所以想让它延迟加载，另外一方面，又不希望在 Singleton 类加载时就实例化，
 * 因为不能确保 Singleton 类还可能在其他的地方被主动使用从而被加载，那么这个时候实例化 instance 显然是不合适的。这个时候，这种方式相比饿汉式就显得很合理。
 *
 */
public class SingletonStaticInnerClasses {

    private static class SingletonStaticInnerClassesHolder {
        private static final SingletonStaticInnerClasses INSTANCE = new SingletonStaticInnerClasses();
    }

    private SingletonStaticInnerClasses () {}

    public static final SingletonStaticInnerClasses getInstance() {
        return SingletonStaticInnerClassesHolder.INSTANCE;
    }
}
```

