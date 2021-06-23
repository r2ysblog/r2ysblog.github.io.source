---
layout: post
title:  "byzantine"
date:   2020-01-15 11:00:03 +0800
categories: algorithms
---

## byzantine：拜占庭问题的算法

https://www.zhihu.com/question/30288330

1.5（P - E） > P
3 / 2 * P - 3 / 2 * E  > P
1 / 2 * P > 3 / 2 * E
P > 3 E
1 / 3 * P > E

如果系统中有n个故障节点，系统要想正确运行，必须至少要有2n+1个正常节点

P = N + E
N > X > N/2 + E

1.5N > N + E

1 / 2 N > E
N > 2E


所有正确的节点最终会决定一个值（termination）
所有正确的节点决定的值必须相同（agreement）
所有正确的节点决定的值必须是被正确的节点提出来的（validity）

消息可能丢失的不可靠信道上试图通过消息传递的方式达到一致性是不可能的

安全的互相传递消息的前提下，一个忠臣提出的意见和其它忠臣的意见都相同，最终所有忠臣都同意这个意见。
我们要确定的就是需要最少几个忠臣。
分布式网络下需要最少几个正确节点


延伸问题
ProofOfWork
ProofOfStake
比特币、以太坊等的共识算法
