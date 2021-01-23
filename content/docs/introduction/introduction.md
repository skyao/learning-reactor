---
title: "Reactor介绍"
linkTitle: "Reactor介绍"
weight: 110
date: 2021-01-22
description: >
  Reactor是什么？
---

{{% pageinfo %}}
静态网站生成器，专注内容，快速创作。
{{% /pageinfo %}}

![](images/reactor-logo.png)

## Reactor是什么？

Reactor 框架是 Pivotal 公司开发的，实现了 Reactive Programming 思想，符合 [Reactive Streams 规范](https://links.jianshu.com/go?to=http%3A%2F%2Fwww.reactive-streams.org%2F)（Reactive Streams 是由 Netflix、TypeSafe、Pivotal 等公司发起的）的一项开源项目。

Reactor 是完全基于反应式流规范设计和实现的库，是 Spring 5 中反应式编程的基础。

Reactor 官方的描述：

> **Reactive Streams based projects for backpressure-ready asynchronous message passing.**





## Reactor 的主要模块

Reactor 框架主要有两个主要的模块：

- reactor-core：负责 Reactive Programming 相关的核心 API 的实现
- reactor-ipc：负责高性能网络通信的实现，目前是基于 Netty 实现的。

## Reactor 的主要类

在 Reactor 中，经常使用的类并不是很多，主要有以下两个：

- `Mono` 实现了 `org.reactivestreams.Publisher` 接口，代表0到1个元素的发布者。
- `Flux` 同样实现了 `org.reactivestreams.Publisher` 接口，代表0到N个元素的发表者。

可能会使用到的类

- `Scheduler` 表示背后驱动反应式流的调度器，通常由各种线程池实现。

