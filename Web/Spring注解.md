# Spring注解



## @Resource与@Autowired区别

+ @Autowired是Spring的注解，@Resource是JDK的注解
+ @Autowired默认按类型装配（byType），@Resource默认是按名称装配（byName）

## @Bean注解

使用@Bean注解的原因，Component , @Repository , @ Controller , @Service这些只能使用在自己编写的类中。而第三方Jar包中的类要加入到IOC容器中可以使用@Bean。

```java
    class test{
        @Bean
        public DataSource dataSource(){
            return new DataSource();
        }
    }
```

