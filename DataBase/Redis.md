# Redis

## Redis命令

[Redis命令](https://www.runoob.com/redis/redis-keys.html)

![image-20201013224430893](../img/DataBaseRedisRehash过程.png)

## RedisAPI

[RedisAPI](http://redisdoc.com/index.html)

## Redis分布式锁

setnx

redlock



[分布式锁](https://juejin.im/post/6844903830442737671)

## 缓存雪崩

大量key同时过期，导致数据库短时间接受大量请求。

针对 Redis 服务不可用的情况

+ 使用Redis 集群，避免单机问题
+ 限流操作，避免同时大量的请求同时落到数据库

针对热点缓存失效的情况：

+ 随机设置缓存的失效时间
+ 缓存永不失效



## 缓存击穿

大量key根本不存在，导致请求落在了数据库上

解决方法

+ 缓存无效key
+ 布隆过滤器

