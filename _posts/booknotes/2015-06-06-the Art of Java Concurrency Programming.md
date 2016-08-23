---
layout: post
title: "Java并发编程的艺术-方腾飞笔记"
keywords: ["java","JUC"]
description: "Java Juc"
category: "java"
tags: ["Java","JUC"]
---

# The Art of Java Concurrency Programming

## 第一章 并发编程的挑战

### 1.1

#### 1.1.1

#### 1.1.2 
vmstat 命令显示CS(Content Switch),表示上下文切换次数

## 第二章 Java并发机制的底层实现原理

### volatile应用

#### 2.1 volatile的两条实现原则
1.Lock前缀指令会引起处理器缓存回写到内存
2.一个处理器的缓存回写到内存会导致其他处理器的缓存实效，MESI(修改，独占，共享，无效)

#### 2.2 synchronized实现原理与应用

#### 2.3 原子操作的实现原理
2.3.3
1.使用CAS实现愿次操作，基本思路：循环到进行CAS操作成功为止
2.CAS操作三大问题 ABA-->1A-2B-3A,循环时间长开销大，只能保证一个共享变量的原子操作

## 第三章 Java内存模型
### 3.1 Java内存模型的基础
#### 3.1.1
#### 3.1.5 happens-before
### 3.2  重排序
#### 3.2.1 数据依赖性
#### 3.2.2 as-if-serial语义
不管怎么重排序，（单线程）程序的执行结果不能被改变；编译器和处理器不会对存在数据以来关系的操作做重排序，因为这种重排序会改变执行结果
#### 3.2.3 程序顺序规则  注意happens-before传递性
#### 3.2.4 重排序对多线程的影响，对存在控制以来的操作重排序，可能会该此案程序的执行结果
### 3.3  顺序一致性

## 第四章 Java并发编程基础

## 第五章 Java中的锁

## 第六章 Java并发容器和框架

## 第七章 Java中13个原子操作类

## 第八章 Java并发工具类

## 第九章 Java中的线程池

## 第十章 Executor框架

## 第十一章 Java并发编程实战
