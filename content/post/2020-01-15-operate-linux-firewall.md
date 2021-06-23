---
layout: post
title:  "operate linux firewall"
date:   2020-01-15 10:51:33 +0800
categories: linux
---

## centOS7永久关闭防火墙

```shell
# 查看状态
systemctl status firewalld.service

# 关闭
systemctl stop firewalld.service

# 开机禁用
systemctl disable firewalld.service

# 开启
systemctl start firewalld.service

# 开机启用
systemctl enable firewalld.service
```
