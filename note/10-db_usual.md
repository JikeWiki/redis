# redis数据库的通用操作

## 1. 概述

我们先来思考以下的几个问题：

- key是又程序员定义的
- redis在使用过程中，伴随着操作数据量的增加，会出现大量的数据以及对应的key
- 数据不区分种类、类别混杂在一起，容易出现重复或者冲突


于是redis提供了一个解决方案，如下

- redis为每个服务提供有16个数据库，编号从0到15
- 每个数据库之间的数据相互独立


在下文中，我们将一起研究redis数据库的通用操作


## 2. db 基本操作

* 切换数据库

```shell
select index
```

* 工具与服务操作

```shell
# 退出redis命令行终端
quit
# 检测服务是否正常
ping
# 打印信息
echo message
```

* 数据移动

```shell
move key db
```

如 将 haha 键移动到 数据库 1 中

```shell
move haha 1
```

* 数据清除相关

```shell
# 查看当前库中一共有多少个key
dbsize
# 清除当前库的所有数据
flushdb 
# 清除所有苦
flushall
```


