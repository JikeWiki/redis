# key的通用操作

## 1. 概述

key 是一个字符串，通过 key 获取 redis 中保存的数据，那么 key 通常存在以下的操作

- 对于key自身状态的相关操作，例如：删除、判定是否存在、获取类型 等

- 对于key有效控制的相关操作，例如：有效期设定、判定是否有效、有效状态的切换 等

- 对于key快速查询操作，例如：按制定策略查询key


在本节，我们将介绍 key 的通用操作

## 2. key的基本通用操作

删除指定key

```shell
del key
```

判定key是否存在

```shell
exists key
```


获取 key 的类型

```shell
type key
```


## 3. key的实效性控制操作

**为指定key设置有效期**

```shell
# 设置key有效期为seconds秒
expire key seconds
# 设置key有效期为milliseconds毫秒
pexpire key milliseconds
# 设置key失效 的 秒级时间戳
expireat key timestamp
# 设置key失效的 毫秒级时间戳
pexpireat key milliseconds-timestamp
```


**获取key的有效时间**

```shell
# 获取key的秒级有效时间
ttl key
# 获取key的毫秒级有效时间
pttl key
```

对于获取有效时间的指令，key 不存在返回 -2，key 存在但是没有关联超时时间返回 -1，如果key存在并且有关联时间，则返回具体的剩余时间秒或者毫秒。


**切换key从实效性转为永久性**

```shell
persist key
```














