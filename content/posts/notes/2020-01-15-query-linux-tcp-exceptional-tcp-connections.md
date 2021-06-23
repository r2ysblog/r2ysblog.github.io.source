---
layout: post
title:  "query linux tcp exceptional tcp connections"
date:   2020-01-15 10:45:49 +0800
categories: linux
---

## 查询linux中各种状态的tcp连接
```shell
netstat -ant |grep CLOSE_WAIT|wc -l
```
### 同理可替换CLOSE_WAIT为
* TIME_WAIT
* ESTABLISHED
