# redis的基本操作于数据类型

## 1. 概述

在我的前两篇笔记中，介绍了redis的基本概念，以及安装了redis的学习环境。在这篇文章中，我们一起来熟悉 redis 的基本操作。redis数据存在内存中，可以让程序高效地读取。但它也能将数据写入硬盘内进行永久保存，在这篇文章开始，我们逐渐熟悉redis对数据的操作。

如果你还没阅读过之前的内容，可以通过以下链接阅读前面的部分


- [01-redis入门知识第1篇-redis简介](./01-introduce.md)

- [02-redis入门知识第2篇-redis的安装与测试](./02-installation.md)

## 2.1. redis的基本操作

### 1.添加信息

进入redis命令行模式。

```shell
./src/redis-cli
```

设置 key、value 数据

- 命令

```shell
set key value
```

- 范例

```shell
set name jkdev
```

### 2.信息查询

功能：根据 key 查询对应的 value，如果不存在，返回空 （nil）

- 命令

```shell
get key
```

- 范例

```shell
get name
```

### 3.清除屏幕信息

- 功能 ：清除屏幕信息

- 命令

```shell
clear
```

### 4.查看帮助

- 功能：获取命令帮助文档，获取组中所有命令信息名称

- 名称

```shell
help 命令名称
help @组名
```

- 示例
  获取`get`指令的帮助

```shell
127.0.0.1:6379> help get

  GET key
  summary: Get the value of a key
  since: 1.0.0
  group: string

127.0.0.1:6379>
```

### 5.退出命令行模式

- 功能：退出客户端

- 命令

```shell
quit
exit
```
