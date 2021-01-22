---
title: "zipWith操作符"
linkTitle: "zipWith操作符"
weight: 355
date: 2021-01-22
description: >
  zipWith 操作符以一对一的方式合并两个流中的元素
---

zipWith 操作符把当前流中的元素与另外一个流中的元素按照一对一的方式进行合并。

### 合并方式：不做处理

在合并时可以不做任何处理，由此得到的是一个元素类型为 Tuple2 的流；

```java
Flux.just("a", "b")
   .zipWith(Flux.just("c", "d"))
   .subscribe(System.out::println);
```

两个流中包含的元素分别是 a，b 和 c，d。这里 zipWith 操作符没有使用合并函数，因此结果流中的元素类型为 Tuple2。

### 合并方式：通过 BiFunction 函数进行处理

zipWith 操作符也可以通过一个 BiFunction 函数对合并的元素进行处理，所得到的流的元素类型为该函数的返回值。

```java
Flux.just("a", "b")
   .zipWith(Flux.just("c", "d"), (s1, s2) -> String.format("%s-%s", s1, s2))
   .subscribe(System.out::println);
```

两个流中包含的元素分别是 a，b 和 c，d。zipWith 操作通过合并函数把元素类型变为 String。




