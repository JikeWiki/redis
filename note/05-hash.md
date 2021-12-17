# hash数据类型与基本操作


## 1. hash类型数据概述

> 我们先来看这个例子

在上一节我们一起了解了 string 存储类型。但是如果是对象数据的存储具有较频繁的更新需求，操作会显得笨重。例如：`user:id:100 -> {"id":100,"name":"春晚","fans":12355,"blogs":99,"focus:83}`，如果需要更新一个对象中的局部数据，就需要更新掉所有数据，于是有了以下的需求

**新的需求**：对一系列存储的数据进行编组，方便管理，比如存储一个对象的信息
**需要的存储结构**：一个存储空间保存多个键值对数据


如下图：
![01](./img/05-01.png)

hash 存储结构优化

- 如果 field 数量较小，存储结构优化为类数组结构
- 如果 field 数量较多，存储结构使用 HashMap 结构


为了解决这个问题，我们引入新的数据类型：`hash`。本文是该系列文章的第五篇，你可以通过下列链接阅读往期的篇章：


[01-redis入门知识第1篇-redis简介](./note/01-introduce.md)

[02-redis入门知识第2篇-redis的安装与测试](./note/02-installation.md)

[03-redis入门知识第3篇-redis的基本操作与数据类型](./note/03-basic.md)

[04-redis入门知识第4篇-redis中的string数据类型与基本的数据存取操作](./note/04-string.md)





## 2. hash 类型数据的基本操作

- 修改/添加数据

```shell
hset key field value
```

- 查询单个字段/查询所有字段

```shell
hget key field
hgetall key
```

- 删除操作

```shell
hdel key field1 [field2]
```

- 修改/添加多个数据

```shell
hmset key field1 value1 field2 value2
```

- 返回 hash 表中，一个或多个给定字段的值

```shell
hmget key field1 field2
```

- 获取 hash 表中字段的数量

```shell
hlen key
```

- 获取 hash 表中是否存在指定的字段

```shell
hexists key field
```

## 3. hash 类型数据的扩展操作

- 获取 hash 表中所有字段名或字段值

```shell
hkey key
hvals key
```

- 设置指定字符段的数值数据增加指定范围的值

```shell
hincrby key field increment
hincrbyfloat key field increment
```

hash 类型数据操作注意事项

- hash 类型下的 value 只能存储字符串，不允许存储其他数据类型，不存在嵌套对象。如果数据未获取到，对应的结果为(nil)；

- 每个 hash 可以存储 2 的 32 次方减 1 个键值对；

- hash 类型十分贴近对象的数据存储形式，并且可以灵活添加删除对象属性，但 hash 设计初衷不是为了存储大量对象而设计，切记不可滥用，更不可以将 hash 作为对象列表使用；

- hgetall 操作可以获取全部属性，如果内部 field 过多，遍历整个数据效率会很低，有可能成为数据访问瓶颈。


## 4. hash的应用案例

### 4.1. 用hash实现购物车


### 4.1. 用hash实现抢购








