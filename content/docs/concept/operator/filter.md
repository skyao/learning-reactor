---
title: "filter操作符"
linkTitle: "filter操作符"
weight: 353
date: 2021-01-22
description: >
  filter操作符对流中的元素进行过滤
---

filter操作符对流中包含的元素进行过滤，只留下满足 Predicate 指定条件的元素。

下面代码的输出的是 1 到 10 中的所有偶数。

```java
Flux.range(1, 10).filter(i -> i % 2 == 0).subscribe(System.out::println);
```



