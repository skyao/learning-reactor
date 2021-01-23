---
title: "merge操作符"
linkTitle: "merge操作符"
weight: 358
date: 2021-01-23
description: >
  merge 操作符将多个流合并成一个Flux序列
---

merge 和 mergeSequential 操作符用来把多个流合并成一个 Flux 序列。

不同之处在于 ：

- merge 按照所有流中元素的实际产生顺序来合并
- mergeSequential 则按照所有流被订阅的顺序，以流为单位进行合并。

进行合并的流都是每隔 100 毫秒产生一个元素，不过第二个流中的每个元素的产生都比第一个流要延迟 50 毫秒。

```java
Flux.merge(Flux.intervalMillis(0, 100).take(5), Flux.intervalMillis(50, 100).take(5))
        .toStream()
        .forEach(System.out::println);
```

在使用 merge 的结果流中，来自两个流的元素是按照时间顺序交织在一起。

```java
Flux.mergeSequential(Flux.intervalMillis(0, 100).take(5), Flux.intervalMillis(50, 100).take(5))
        .toStream()
        .forEach(System.out::println);
```

而使用 mergeSequential 的结果流则是首先产生第一个流中的全部元素，再产生第二个流中的全部元素。

