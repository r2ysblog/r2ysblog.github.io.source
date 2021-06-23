---
layout: post
title:  "AbstractQueuedSynchronizer"
date:   2019-08-09 08:30:00 +0800
categories: jdk
---

## AbstractQueuedSynchronizer


##### Lock

使用Lock接口是java实现锁的一种方式。
Lock接口在java.util.concurrent.locks包下。
ReentrantLock(可重入锁)、ReadLock(读锁)、WriteLock(写锁)是Lock接口最重要的三个实现类。
ReadWriteLock接口是一个工厂接口，ReentrantReadWriteLock是ReadWriteLock接口的实现类，它包含两个内部静态类ReadLock(读锁)、WriteLock(写锁)，这两个静态类又分别实现了Lock接口。

##### 悲观锁与乐观锁的定义
它们是在并发情况下的两种不同策略。java中没有明确的类就是乐观锁或者悲观锁。

* 悲观锁的策略：
就是很悲观，认为每次去拿的数据可能被别人修改过了。所以，自己去拿数据的时候会上锁，导致别人等到锁被释放才能获取数据。

* 乐观锁的策略：
每次去拿数据的时候认为别人不会修改，不上锁。
只是在更新的时候采用一种特殊方式，因为更新分为三步，先读取、然后检查、最后更新；所以在更新之前要先检查读取的数据是不是已经被别人修过过了。如果修改过了，就重新读取，再次重复检查步骤最后更新。
有的情况下，更新失败的所在的线程可能会放弃操作。

* 比较
所以说 悲观锁阻塞事务，乐观锁回滚重试。

对于写少的情况，即冲突少，采用乐观锁，可以省去锁的开销，增加数据系统的吞吐量。
如果冲突多，不断地回滚重试反倒是降低性能，不如采用悲观锁合适。

##### 乐观锁的回滚重试

通常把这种策略用概念CAS表示：Compare-and-swap

```java

```