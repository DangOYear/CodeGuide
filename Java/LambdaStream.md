# Lambda、Stream

## Lambda

## 函数式接口

### 自定义函数式接口

```java
@FunctionalInterface
interface SayHello
{
    void sayMessage(String message);
}

public class GreetingService {
    public static void main(String[] args) {
        SayHello sayHello = message -> {
            System.out.println("Say Hello " + message);
        };
        sayHello.sayMessage("Ni hao");
    }
}
```

### 内置函数式接口

内置的函数式接口主要分为以下四大类

Function、Comsumer、Predicate、Supplier

**Function**

```java
import java.util.function.BiFunction;

/**
 * @author SaltedFish
 * @date 2021/2/18
 * 一个接受两个输入参数的方法，并且返回一个结果
 */
public class FunctionDemo {
    public static void main(String[] args) {
        BiFunction<Integer, Integer, Integer> biFunction = (a, b) -> a + b;
        System.out.println(biFunction.apply(1, 2));
    }
}

```

**Comsumer**

```java
import java.util.function.Consumer;

/**
 * @author SaltedFish
 * @date 2021/2/18
 * 接受一个输入参数并且无返回的操作
 */
public class ConsumerDemo {
    public static void main(String[] args) {
        int b = 2;
        Consumer<Integer> consumer = (a) -> System.out.println(a + b);
        consumer.accept(1);
    }
}
```

**Predicate**

```java
import java.util.function.Predicate;

/**
 * @author SaltedFish
 * @date 2021/2/18
 * 接受一个输入参数，返回一个布尔值结果。
 */
public class PredicateDemo {
    public static void main(String[] args) {
        int b = 1;
        Predicate<Integer> biPredicate = a -> a > b;
        System.out.println(biPredicate.test(2));
    }
}
```

**Supplier**

```java
import java.util.function.Supplier;

/**
 * @author SaltedFish
 * @date 2021/2/18
 * 无参数，返回一个结果。
 */
public class SupplierDemo {
    public static void main(String[] args) {
        int a = 1;
        int b = 2;
        Supplier<Integer> supplier = () -> a + b;
        System.out.println(supplier.get());
    }
}
```



## Stream（日常开发中经常会用到）

stream是从Java8开始引入的。用来“做什么而非怎么做”的方式处理集合。

stream提供了一种更直观的操作容器的方式。之前操作容器往往需要显式的使用循环。而使用stream之后，对容器的处理更加直观了。

stream方法实现在Collection接口中。

### 常用的操作

### 创建流





| 操作名                                            | 操作介绍                    |
| ------------------------------------------------- | --------------------------- |
| Stream<T> filter(Predicate<? super T> predicate); | 产生一个满足当前条件P的元素 |
| count                                             | 产生当前流中元素的个数      |
|                                                   |                             |



### 并行操作

在产生流的过程中可以使用parallelStream()产生并行流





