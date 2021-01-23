---
title: "flatMap操作符"
linkTitle: "flatMap操作符"
weight: 360
date: 2021-01-23
description: >
  flatMap 操作符把流中的每个元素转换成一个流，再把所有流中的元素进行合并。
---

flatMap 和 flatMapSequential 操作符把流中的每个元素转换成一个流，再把所有流中的元素进行合并。

flatMapSequential 和 flatMap 之间的区别与 mergeSequential 和 merge 之间的区别是一样的：

- flatMap 按照所有流中元素的实际产生顺序来合并
- flatMapSequential 则按照所有流被订阅的顺序，以流为单位进行合并。

```java
Flux.just(5, 10)
        .flatMap(x -> Flux.intervalMillis(x * 10, 100).take(x))
        .toStream()
        .forEach(System.out::println);
```

上面的代码中，流中的元素被转换成每隔 100 毫秒产生的数量不同的流，再进行合并。由于第一个流中包含的元素数量较少，所以在结果流中一开始是两个流的元素交织在一起，然后就只有第二个流中的元素。

TODO：没理解，后面代码验证