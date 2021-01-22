---
title: "reduce操作符"
linkTitle: "reduce操作符"
weight: 356
date: 2021-01-22
description: >
  reduce 操作符对流中包含的所有元素进行累积操作
---

reduce 和 reduceWith 操作符对流中包含的所有元素进行累积操作，得到一个包含计算结果的 Mono 序列。

累积操作是通过 BiFunction 来表示的。在操作时可以指定一个初始值。如果没有初始值，则序列的第一个元素作为初始值。

下面的示例代码中对流中的元素进行相加操作，结果为 5050；

```java
Flux.range(1, 100).reduce((x, y) -> x + y).subscribe(System.out::println);
```

下面的示例代码中也是同样的相加操作，不过通过 Supplier 给出了初始值 100，所以结果为 5050 + 100 = 5150；

```java
Flux.range(1, 100).reduceWith(() -> 100, (x, y) -> x + y).subscribe(System.out::println);
```




