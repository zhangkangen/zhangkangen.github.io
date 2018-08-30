---
layout: post
title: redis 持久化
date: 2018-08-30 22:45:01
categories:
- redis 
tags:
- redis
description: redis 持久化
---
# Redis 持久化
## 持久化选项
### 快照（snapshotting）
将存在于某一时刻的所有数据都写入硬盘。

快照将被写入 dbfilename 选项制定的文件里面，并储存在 dir 选项指定的路径上面。如果在新的快照文件创建完毕之前， Redis、系统、或者硬件之中的这三者之中的任意一个崩溃了，那么 Redis 将丢失最后一次创建快照之后写入的所有数据。
创建快照的方法：
- 客户当向 Redis 发送 BGSAVE 命令，Redis 会调用 fork 来创建一个子进程，然后子进程负责将快照写入硬盘。
- 客户端向 Redis 发送 SAVE 命令来创建一个快照。
- 配置 save 配置选项。
- Redis 通过 SHUTDOWN 命令。会先执行一个 SAVE 命令，完毕之后关闭服务器。
- Redis 连接另外一个服务器，并向对方发送 SYNC 命令开始复制的时候。



### 追加（append-only file,AOF）
在执行写命令时，将被执行的写命令复制到硬盘。
appendfsync 选项及同步频率
- always 每个 Redis 命令都要同步写入硬盘。这样做会严重降低 Redis 的速度
- everysec 每秒执行一次同步，显式地将多个写命令同步到硬盘
- no 让操作系统决定应该何时同步




