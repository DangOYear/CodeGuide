# Dubbo

## RPC

RPC（Remote Procedure Call）远程过程调用

![RPC原理时序图](../img/NettyandRPC流程.png)

## API与SPI

### API（Application Programming Interface）

大多数情况下，都是实现方来制定接口并完成对接口的不同实现，调用方仅仅依赖却无权选择不同实现。

### SPI（Service Provider Interface）

而如果是调用方来制定接口，实现方来针对接口来实现不同的实现，调用方来选择自己需要的实现方。

## 架构

![image-20201013215845687](../img/NettyAndDubboDubbo架构.png)

![/dev-guide/images/dubbo-framework.jpg](../img/NettyandDubbo框架.png)

**各层说明**：

- **config 配置层**：对外配置接口，以 `ServiceConfig`, `ReferenceConfig` 为中心，可以直接初始化配置类，也可以通过 spring 解析配置生成配置类
- **proxy 服务代理层**：服务接口透明代理，生成服务的客户端 Stub 和服务器端 Skeleton, 以 `ServiceProxy` 为中心，扩展接口为 `ProxyFactory`
- **registry 注册中心层**：封装服务地址的注册与发现，以服务 URL 为中心，扩展接口为 `RegistryFactory`, `Registry`, `RegistryService`
- **cluster 路由层**：封装多个提供者的路由及负载均衡，并桥接注册中心，以 `Invoker` 为中心，扩展接口为 `Cluster`, `Directory`, `Router`, `LoadBalance`
- **monitor 监控层**：RPC 调用次数和调用时间监控，以 `Statistics` 为中心，扩展接口为 `MonitorFactory`, `Monitor`, `MonitorService`
- **protocol 远程调用层**：封装 RPC 调用，以 `Invocation`, `Result` 为中心，扩展接口为 `Protocol`, `Invoker`, `Exporter`
- **exchange 信息交换层**：封装请求响应模式，同步转异步，以 `Request`, `Response` 为中心，扩展接口为 `Exchanger`, `ExchangeChannel`, `ExchangeClient`, `ExchangeServer`
- **transport 网络传输层**：抽象 mina 和 netty 为统一接口，以 `Message` 为中心，扩展接口为 `Channel`, `Transporter`, `Client`, `Server`, `Codec`
- **serialize 数据序列化层**：可复用的一些工具，扩展接口为 `Serialization`, `ObjectInput`, `ObjectOutput`, `ThreadPool`



## 负载均衡

### Random LoadBalance(默认，基于权重的随机负载均衡机制)

随机，按权重设计随机概率。

### RoundRobin LoadBalance(不推荐，基于权重的轮询负载均衡机制)

### LeastActive LoadBalance

### ConsistentHash LoadBalance

- 一致性 Hash，相同参数的请求总是发到同一提供者。
- 挂掉了一台，会平摊到其他节点
- 缺省只对第一个参数 Hash
- 缺省用 160 份虚拟节点