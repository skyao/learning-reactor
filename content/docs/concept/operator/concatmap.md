---
title: "concatMap操作符"
linkTitle: "concatMap操作符"
weight: 361
date: 2021-01-23
description: >
  concatMap 操作符把流中的每个元素转换成一个流，再把所有流中的元素进行合并。
---

concatMap 操作符的作用也是把流中的每个元素转换成一个流，再把所有流进行合并。

与 flatMap 不同的是，concatMap 会根据原始流中的元素顺序依次把转换之后的流进行合并；与 flatMapSequential 不同的是，concatMap 对转换之后的流的订阅是动态进行的，而 flatMapSequential 在合并之前就已经订阅了所有的流。

```java
Flux.just(5, 10)
        .concatMap(x -> Flux.intervalMillis(x * 10, 100).take(x))
        .toStream()
        .forEach(System.out::println);
```

上面的代码中，只不过把 flatMap 换成了 concatMap，结果流中依次包含了第一个流和第二个流中的全部元素。

TODO：没理解，后面代码验证