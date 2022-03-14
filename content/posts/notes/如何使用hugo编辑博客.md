+++
title = "如何使用hugo编辑博客"
description = ""
date = 2022-03-10T13:00:54+08:00
draft = false
comment = true
toc = true
reward = true
categories = [
  ""
]
tags = [
  ""
]
+++

<!--more-->

# 如何使用hugo编辑博客
我的电脑是mac m1芯片
arch -arm64 brew install hugo
准备工作参考hugo官方文档
[https://www.gohugo.org/](https://www.gohugo.org/)
### 博客目录初始化好之后，添加主题
git submodule add https://github.com/razonyang/hugo-theme-bootstrap themes/hugo-theme-bootstrap
并拷贝到themes目录下
cp -a themes/hugo-theme-bootstrap/exampleSite/* .
### 生成静态页面包括草稿
hugo -D --theme=hugo-theme-bootstrap --buildDrafts
### 启用本地调试服务
hugo server -D

## 如何使用工作流推送并生成博客页
### 开启github pages
### 创建两个仓库
### 新建工作流
### 使用推送功能触发工作流
### 预览

## 日常编辑笔记或博文
hugo new content/posts/notes/如何使用hugo编辑博客.md
vim content/posts/notes/如何使用hugo编辑博客.md
```shell
cd /Volumes/My\ Passport/course/life/r2ysblog/r2ysblog.github.io.source/
git add .
ls_date=`date +%Y%m%d%H%M`
git commit -m $ls_date
git push -u origin main
open -a "/Applications/Safari.app" https://blog.r2ys.life
```



### 结束。
