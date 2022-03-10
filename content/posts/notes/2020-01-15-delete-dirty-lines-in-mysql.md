---
layout: post
title:  "delete dirty lines in mysql"
date:   2020-01-15 10:38:28 +0800
categories: mysql
---

## 清楚重复数据

### 建表
```mysql
CREATE TABLE `src5` (
  `userid` int(11) unsigned NOT NULL AUTO_INCREMENT,
  `username` varchar(20) DEFAULT NULL,
  `usercode` varchar(20) DEFAULT NULL,
  PRIMARY KEY (`userid`)
) ENGINE=InnoDB AUTO_INCREMENT=7 DEFAULT CHARSET=utf8;
```
### 如果usercode重复，那么可能会出现以下数据
userid  username  usercode
1 ... code0
2 ... code0
3 ... code0

### 删除id最大的那一行，比如删除code0，userid为3的那行
```mysql
DELETE FROM src5
WHERE userid IN (
		SELECT id
		FROM (
			SELECT MAX(userid) AS id, COUNT(usercode) AS ucount
			FROM src5
			GROUP BY usercode
			HAVING ucount > 1
			ORDER BY ucount DESC
		) tab
	)
```

### 如果没有自增主键，需要先临时增加，以tmpid为count
```mysql
ALTER TABLE src5
  	ADD COLUMN tmpid INT(11) PRIMARY KEY AUTO_INCREMENT;
```

### 最后再删除
```mysql
ALTER TABLE src5
	DROP COLUMN tmpid;
```

### 同时修改原来的主键column
```mysql
ALTER table table_name add PRIMARY KEY (user_role_id)
```
