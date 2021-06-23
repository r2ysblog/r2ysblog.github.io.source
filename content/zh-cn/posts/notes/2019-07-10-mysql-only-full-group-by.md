+++
title = "mysql only full group by"
date = "2019-07-10 16:01:00 +0800"
description = "mysql如何分组实现数据选择"
featured = false
categories = [
"mysql"
]
tags = [
"语法"
]
series = [
"MySQL由浅入深"
]
images = [
]
+++



## MySQL SQL GROUP BY是如何选择哪一条数据留下的


#### 示例

```mysql
-- 建表
CREATE TABLE `src2` (
  `id` int(11) DEFAULT NULL,
  `name` varchar(20) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
-- 查询
SELECT id, name FROM src2;
```

查询到的结果
id  name
1   alpha
1   bravo
2   charlie
2   dolphin

#### 查看当前mysql版本，并且看是否开启了only full group by
```mysql
SELECT version(), @@sql_mode;
```
5.7.20  STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION

#### 根据id使用group by查询id,name

```mysql
SELECT id, NAME FROM src2 GROUP BY id;
```

如无异常会查询到两条数据，但是同样为id1的两条数据是如何选择留哪一条呢
1 alpha
2 charlie

##### 稍后再看，先解决这个问题

#### 关闭only full group by
```mysql
-- 去除
SET sql_mode=(SELECT REPLACE(@@sql_mode,'ONLY_FULL_GROUP_BY',''));
-- 再次查询
SELECT version(), @@sql_mode;
```

#### 如何恢复？
5.7之前的mysql其实是处于未定义规则状态，官方文档不承诺一定会返回哪条数据。而到了MySQL5.7，仍然是未定义状态，并且默认直接不允许未定义状态的grouping查询，会报错：

```console 
Expression #2 of SELECT list is not in GROUP BY clause and contains nonaggregated column 'learn.src2.name' which is not functionally dependent on columns in GROUP BY clause; this is incompatible with sql_mode=only_full_group_by
```

```mysql
-- 重新开启only full group by
SET sql_mode=(SELECT CONCAT(@@sql_mode, ',ONLY_FULL_GROUP_BY'));
```

#### 那么查询的重复id的数据应该返回哪一条呢

要看查询具体使用的b-tree索引中第一个命中的数据。


#### 如何优化或者改变查询方式

```mysql
-- 加入max条件或者其它
SELECT * FROM src2 WHERE NAME IN (SELECT max(NAME) FROM src2 GROUP BY id) ORDER BY id ASC
```

参考mysql文档：
[group by handling](https://dev.mysql.com/doc/refman/8.0/en/group-by-handling.html)