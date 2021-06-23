---
layout: post
title:  "difference from array and arraylist"
date:   2020-01-15 10:44:25 +0800
categories: Java
---

## Array和ArrayList的各自特点和区别

### Array
* 内存中是连续的
* 读取和赋值很快
* 扩容和收缩很慢
* 需要指定内存大小

### ArrayList
* 不需要指定容量
* 方便动态扩容和收缩
* 可以保存不同类型，本质都当作Object处理
* ArrayList不是类型安全，需要拆装箱
* 通过指定泛型，通过编译来强制使用正确统一的数据类型，也减少了类型转换
