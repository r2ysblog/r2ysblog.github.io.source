---
layout: post
title:  "linux close selinux"
date:   2020-01-15 10:52:25 +0800
categories: linux
---

## CentOS7关闭SELinux

```shell
[root@dev-server ~]# getenforce
Disabled
[root@dev-server ~]# /usr/sbin/sestatus
SELinux status:                 disabled

# 永久关闭
vi /etc/selinux/config
# 将SELINUX=enforcing改为SELINUX=disabled
# 重启后生效
```
