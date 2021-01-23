---
title: "combineLatest操作符"
linkTitle: "combineLatest操作符"
weight: 362
date: 2021-01-23
description: >
  combineLatest 操作符把流中的每个元素转换成一个流，再把所有流中的元素进行合并。
---

combineLatest 操作符把所有流中的最新产生的元素合并成一个新的元素，作为返回结果流中的元素。

只要其中任何一个流中产生了新的元素，合并操作就会被执行一次，结果流中就会产生新的元素。

```java
Flux.combineLatest(
        Arrays::toString,
        Flux.intervalMillis(100).take(5),
        Flux.intervalMillis(50, 100).take(5)
).toStream().forEach(System.out::println);
```

上面的代码中，流中最新产生的元素会被收集到一个数组中，通过 Arrays.toString 方法来把数组转换成 String。

TODO：没理解，后面代码验证