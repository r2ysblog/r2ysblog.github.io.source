---
layout: post
title:  "learn shell from start"
date:   2020-01-15 11:01:03 +0800
categories: shell
---

## learn shell from start

### 打印日期的两种方式
```shell
echo today is `date "+%Y-%m-%d"`
echo today is $(date "+%Y-%m-%d")
```

### shell中变量的使用

mypid=$$
echo "mypid:$mypid"

paramCount=$#
echo "paramCount:$paramCount"

lastPid=$!
echo "lastPid:$lastPid"

lastResponse=$?
echo "lastResponse:$lastResponse"

setFlag=$-
echo "setFlag:$setFlag"

params=$*
echo "params:$params"

stringParams=$@
echo "stringParams:$params"

param0=$0
echo "param0:$param0"

param1=$1
echo "param1:$param1"
printf "param1 is %s\n" $param1


for i in $@; do
    echo $i
done

for i in $params; do
    echo $i
done

`` 和 $() 里面的都是命令
echo Linux `echo Shell `echo today is `date "+%Y-%m-%d"```
echo Linux `echo Shell $(echo today is $(date "+%Y-%m-%d"))`
echo Linux $(echo Shell $(echo today is $(date "+%Y-%m-%d")))

${}里面的是变量
A=Charlie
echo "variable AB is: $AB"
echo "variable A($A) concat charactor B is: ${A}B"


file=/Users/huray/Desktop/testshell.sh

## #是去掉左边(在键盘上 # 在 $ 之左边)
## % 是去掉右边(在键盘上 % 在 $ 之右边)
## 单一符号是最小匹配;两个符号是最大匹配
## *是用来匹配不要的字符，也就是想要去掉的那部分
## 还有指定字符分隔号，与*配合，决定取哪部分

# 拿掉第一条 / 及其左边的字符串
echo ${file#*/}

# 拿掉最后一条 / 及其左边的字符串
echo ${file##*/}

# 拿掉第一个 . 及其左边的字符串
echo ${file#*.}

# 拿掉最后一个 . 及其左边的字符串
echo ${file##*.}

# 拿掉最后一条 / 及其右边的字符串
echo ${file%/*}

# 拿掉第一条 / 及其右边的字符串
echo ${file%%/*}

# 拿掉最后一个 . 及其右边的字符串
echo ${file%.*}

# 拿掉第一个 . 及其右边的字符串
echo ${file%%.*}

# 参考文档
https://www.cnblogs.com/chengd/p/7803664.html

# 目录和路径的获取
https://blog.csdn.net/Jerry_1126/article/details/79872110

# 循环
# for((paramIdx=1; paramIdx<10; paramIdx++)); do
#     eachParam=`$paramIdx`
#     echo "eachparam:$eachParam"
# done

 # pcount=$#
 # if ((pcount==0)); then
 # echo no args;
 # exit;
 # fi
 #
 # #2 获取文件名称
 # p1=$1
 # fname=`basename $p1`
 #
 # echo $fname
 #
 # #3 获取上级目录到绝对路径
 # pdir=`cd -P $(dirname $p1); pwd`
 # echo $pdir
 #
 # #4 获取当前用户名称
 # user=`whoami`
 #
 # #5 循环
 # for((host=1; host<4; host++)); do
 #        echo ------------------- hadoopnode0$host --------------
 #        rsync -av $pdir/$fname $user@hadoopnode0$host:$pdir
 # done
