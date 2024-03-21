---
title: MySQL中如何指定引擎？
date: 2024-03-21 01:37:57
categories:
- MySQL
tags:
- 面试题
sticky: 1
toc: true # 无需显示目录
single_column: true
author: zhangyushuo
originalLink: https://baidu.com
---

1. 创建表时，可以通过`ENGINE`来指定存储引擎，在create语句最后加上“engine=存储引擎”即可；

   Create table table1(id int(11) primary key auto_increment) engine=MyISAM;

2. 修改表时，可以使用“`alter table` 表名 engine=存储引擎”；来指定存储引擎。

   ``` sql
   alter table table1 engine=InnoDB；
   ```