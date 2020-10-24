# ZooKeeper

## ZooKeeper简介

### 介绍

ZooKeeper是一个开源的分布式协调服务，是Google Chubby的开源实现。

设计目的是将复杂且容易出错的分布式一致性服务封装起来，提供简单易用的接口给开发者使用。

ZooKeeper使用共享树型的名字空间来相互协调。

树型空间由一系列ZNode的数据节点组成，类似于一个文件系统的层级结构。

ZooKeeper的全量数据均存储在内存中。

### 集群

Leader、Follower和Observer三种角色。

Leader是通过选举算法得到的。

Leader服务器可以提供读和写服务

Leader、Follower和Observer都能提供读服务

Observer只用来提升集群的读性能，不参与Leader选举，也不参与写操作的过半写成功策略。

### 数据节点（ZNode）

ZooKeeper数据模型中的数据单元。

数据模型一棵树，路径由斜杠分割。类似树型文件系统。

/root/test

### Watcher

Zookeeper允许用户在指定节点上注册一些Watcher，并且在特定事件触发的时候，ZooKeeper服务端会将事件通知到对应的客户端上。

### ACL

ZooKeeper定义了5种权限

+ CREATE：创建子节点的权限
+ READ：获取节点数据和子节点列表的权限
+ WRITE：更新节点数据的权限
+ DELETE：删除子节点的权限
+ ADMIN：设置节点ACL的权限



## ZAB协议

ZooKeeper采用了一种被称为ZooKeeper Atomic Broadcast（ZAB，ZooKeeper原子消息广播协议）作为其数据一致性的核心算法。

ZooKeeper的核心流程：所有事务请求必须由一个全局唯一的服务器来协调处理。即Leader服务器将客户端的请求转换成一个提案，并且将提案发送给所有Follower服务器。之后等待Follower的回应，回应数超过半数，那么Leader服务器就会发送Commit消息，提交前一个Proposal。（Observer服务器不参与半数）

ZAB主要流程可以分为两个部分

+ 崩溃恢复
+ 消息广播

### 崩溃恢复



崩溃恢复主要指的是Leader的重新选举过程。

### 消息广播





## ZooKeeper部署

## JavaAPI使用

## 应用场景