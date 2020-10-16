# MySQL

## mysql引擎

+ InnoDB（默认）
+ MyISAM

其实有更多，但是主要是这两种。可以通过**SHOW ENGINES;**查看。

创建时可以指定，不指定则为默认引擎

```mysql
SQL CREATE TABLE 表名(
  	建表字段; 
) ENGINE = 存储引擎名称;
```

### InnoDB和MyISAM区别

+ **InnoDB支持事务，支持行级锁和外键（重要）**，MyISAM只支持表锁
+ InnoDB 是聚集索引，MyISAM 是非聚集索引。聚集索引的文件存放在主键索引的叶子节点上，因此 InnoDB 必须要有主键，通过主键索引效率很高。但是辅助索引需要两次查询，先查询到主键，然后再通过主键查询到数据。
+ InnoDB 不保存表的数据行数，执行 select count(*) from table 时需要全表扫描。而MyISAM 用变量保存了表的行数。

## 索引

### 使用索引的优缺点

+ 优点
  + 大大缩短查询的时间
+ 缺点
  + 创建和维护索引需要时间
  + 索引需要空间去存

InnoDB引擎采用B+树来实现

### B+树优点

+ B+树的磁盘读写代价更低
+ B+树的数据信息遍历更加方便
+ B+树的查询效率更加稳定



## Undo日志

## Redo日志

## 隔离级别与MVCC

### 默认级别

可重复读

### 隔离级别表格

| 隔离级别         | 脏读   | 不可重复读 | 幻读   |
| ---------------- | ------ | ---------- | ------ |
| READ UNCOMMITTED | 可能   | 可能       | 可能   |
| READ COMMITTED   | 不可能 | 可能       | 可能   |
| REPEATABLE READ  | 不可能 | 不可能     | 可能   |
| SERIALIZABLE     | 不可能 | 不可能     | 不可能 |

### ReadView

readview用来实现读已提交和可重复读

两个区别是通过生成readview的时机来区分的。

读已提交每次读都会重新生成ReadView

可重复读在第一次读的时候生成ReadView