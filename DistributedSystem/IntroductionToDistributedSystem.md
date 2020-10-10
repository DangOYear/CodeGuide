# 分布式系统简介

## ACID、CAP、BASE理论

+ ACID
  + 原子性
  + 一致性
  + 隔离性
  + 持久性

+ CAP理论：
  + C.一致性 
  + A.可用性 
  + P.分区容错性
  + 往往无法同时满足
+ BASE理论:
  + Basically Available（基本可用）
    + 在出现不可预知故障时候，允许使用部分可用性
  + Soft state（软状态）
    + 允许系统中的数据存在中间状态，允许数据同步存在时延
  + Eventually consistent（最终一致性）
    + 系统中所有的数据副本，经过一段时间的同步后，最终能够达到一个一致的状态（不同于强一致性）。

## 2PC

To do

## 3PC

To do

## Paxos

To do

## 一致性Hash

