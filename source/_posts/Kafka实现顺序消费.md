---
title: Kafka如何实现顺序消费？
date: 2024-03-19 22:35:57
categories:
- Kafka
tags:
- 面试题
sticky: 1
toc: true # 无需显示目录
single_column: true
author: zhangyushuo
originalLink: https://baidu.com
---
Kafka的消息是存储在指定的topic中的某个`partition`中的。
并且一个topic是可以有多个partition的，同一个partition中的消息是有序的，但是跨partition，或者跨topic的消息就是无序的了。

### 为什么同一个partition的消息是有序的？

因为当生产者向某个partition发送消息的时候，消息会被追加到该partition的日志文件中，并且被分配一个唯一的offset，文件的读写是有顺序的。而消费者在从该分区消费消息时，会从该分区的最早`offset`开始逐个读取消息，保证了消息的顺序性。

### 基于此，要想实现消息的顺序消费，可以有以下几个办法：

1. 在一个topic中，只创建一个partition，这样这个topic下的消息都会按照顺序保存在同一个partition中，这就保证了消息的顺序消费。
2. 发送消息的时候指定partition，如果一个topic下有多个partition，那么可以把需要保证顺序的消息都发送到同一个partition中，这样也能做到顺序消费。
