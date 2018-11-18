---
layout: post
title: Java 多线程基础
date: 2018-08-13 22:00:17
categories: Java Thread
tags:
- Java
- Thread
description: Java 多线程基础知识梳理
---

#Java 多线程基础
## 多线程创建
实现多线程编程的方式主要有两种：一种是继承 Thread 类，另一种是实现 Runnable 接口。
- 使用继承 Thread 类的方式来开发多线程应用程序在设计上是有局限性的，因为 Java 是单继承，不支持多继承，
所以为了改变这种限制，可以使用实现 Runnable 接口的方式来实现多线程。
- 多线程非线程安全：非线程安全是指多个线程对同一个对象中的同一个实例变量进行操作时会出现值被更改、值不同步的情况，进而影响程序的执行流程。

currentThread() 方法可返回代码段正在被那个线程调用的信息。
<br>isAlive() 判断当前的线程是否处于活动状态。
<br>sleep() 指定的毫秒内让当前正在执行的线程休眠。
<br>getId() 取得线程的唯一标识。
## 停止线程
- 使用退出标识，使线程正常退出，也就是当 run 方法完成之后线程终止。
- 使用 stop 方法强制终止，但是不推荐使用这个方法，因为 stop 和 suspend 及 resume 一样，
都是过期作废的方法，使用它们可能产生不可预测的结果。
- 使用 interrupt 方法中断线程。（仅仅是在当前线程中打了一个停止的标记，并不是真正的停止线程）
## 对象及变量的并发访问
### synchronized 同步方法
### synchronized 同步语句块
### volatile 关键字
### 原子类 （atomic），CAS (compare and swap) 
volatile 的作用是强制从公共堆栈中取得变量的值, 而不是从线程私有数据栈中取得变量的值.

### volatile 和 synchronized 比较
- volatile 是线程同步的轻量级实现, volatile 性能比 synchronized 好, 
volatile 只能修饰变量, synchronized 可以修饰方法, 以及代码块.
- 多线程访问 volatile 不会发生阻塞, 而 synchronized 会出现阻塞.
- volatile 能保证数据的可见性, 但不能保证原子性; 而 synchronized 可以保证原子性, 
也可以间接保证可见性, 因为他会将私有内存和公共内存中的数据做同步.
- volatile 解决的是变量在多个线程之间的可见性, 而 synchronized 解决的是多个线程之间访问资源的同步性.
## 锁
## 死锁
## 线程池
线程是一种轻量级的工具，但其创建和关闭依然需要花费时间。
线程本身也要占用内存空间，大量的线程会抢占内存资源。

线程池：让创建的线程可以复用。从池子中获取空闲线程，完成工作之后，不是关闭这个
线程，而是将这个线程退回到池子中。

java中使用 Executors，使用Executors 可以获取一个拥有特定功能的线程池。
ThreadPoolExecutor 实现了 Executor 接口。

Executor 提供了以下几种类型的线程池：
- newFixedThredPool():固定线程数量的线程池。
- newSingleThreadExecutor():创建只有一个线程的线程池。
- newCachedThreadPool(): 创建一个不限数量的线程池。
- newScheduledThreadPool(): 创建一个定长线程池，支持定时及周期性执行。
- newSingleThreadScheduledExecutor(): 只有一个线程的定长线程池。
- newWorkStealingPool(): java8 新增的创建并行处理任务的线程池。

ThreadPoolExecutor:
- corePoolSize: 指定线程池中的线程数量。
- maximumPoolSize: 线程此种的最大线程数量
- keepAliveTime: 空闲线程存活时间。
- unit： keepAliveTime 的单位。
- workQueue： 任务队列，被提交但尚未被执行的任务。
- threadFactory： 线程工厂
- handler: 拒绝策略
    - AbortPolicy: 直接抛出异常
    - CallerRunsPolicy：在调用者线程中，运行当前被丢弃的任务。
    - DiscardOldestPolicy: 丢弃最老的一个请求
    - DiscardPolicy: 丢弃无法处理的任务 

线程池数量设置：Nthreds = Ncpu * Ucpu * (1+ W/C)

## 并发集合
## ThreadLocal

## 其它
- 当一个线程执行的代码出现异常时, 该线程所持有的锁自动释放.

