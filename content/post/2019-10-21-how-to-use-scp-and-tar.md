---
layout: post
title:  "how to use scp and tar"
date:   2019-10-21 11:45:00 +0800
categories: sh
---

## 转载

##### scp

```shell
scp /data/somefile.sometype tomcat@destinationhost:/data/newfile.type
```

##### tar

press:
```shell
tar czf result.tar.gz sourcefile/
```
unpress:
```shell
tar xzf result.tar.gz sourcefile/
```