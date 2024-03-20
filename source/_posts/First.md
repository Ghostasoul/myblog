---
title: 使用消息队列的主要目的：解耦、异步、削峰填谷
date: 2024-03-19 22:31:22
categories:
  - Kafka
tags:
  - 面试题目
comments: true
---
**解耦**：在一个复杂的系统中，不同的模块或服务之间可能需要互相依赖，如果直接使用`函数调用`或者`API`调用的方式，会造成模块之间的耦合，当其中一个模块发生改变时，需要同时修改调用方和被调用方的代码。而使用消息队列作为中间件，不同的模块可以将消息发送到消息队列中，不需要知道具体的接收方是谁，接收方可以独立的消费消息，实现了模块之间的解耦。


**异步**：有些操作比较耗时，例如`发送邮件`、`生成报表`等，如果使用同步的方式处理，会阻塞主线程或者进程，导致系统的性能下降。而使用消息队列，可以讲这些操作封装成消息，放入消息队列中，异步处理这些操作，不影响主流程的执行，提高了系统的性能和相应速度。