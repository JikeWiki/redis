# set数据类型与基本操作

## 1. 概述

假设我们存在这样的需求：我们需要存储大量的数据，且需要在查询上要求更高的效率。似乎前面提到的数据类型已不满足我们现有的需求，在本篇文章中，我们引入一个全新的概念：set数据类型。与hash存储结构完全类似，但是仅存储键，不存储值（nil），并且不重复存储。


本篇是该系列文章的第七篇，你可以通过一下链接阅读之前的内容

- [01-redis入门知识第1篇-redis简介](./note/01-introduce.md)

- [02-redis入门知识第2篇-redis的安装与测试](./note/02-installation.md)

- [03-redis入门知识第3篇-redis的基本操作与数据类型](./note/03-basic.md)

- [04-redis入门知识第4篇-redis中的string数据类型与基本的数据存取操作](./note/04-string.md)

- [05-redis入门知识第5篇-hash数据类型与基本操作](./note/05-hash.md)

- [06-redis入门知识第6篇-list 类型以及基本操作](./note/06-list.md)


## 2. set类型数据的基本操作

- 添加数据
```shell
sadd key member1 [member2]
```

- 获取全部数据
```shell
smembers key
```

- 删除数据
```shell
srem key member1 [member2]
```

- 获取集合数据总数
```shell
scard key
```

- 判断集合中是否包含指定数据
```shell
sismember key member
```


## 2. set随机数据操作


**需求案例**

假设我们现在有这样的需求：每位用户首次使用新闻APP时，会推荐三项的爱好内容。但是后期为了增加用户的活跃度、兴趣点，必须让用户对其他信息类别逐渐产生兴趣，增加客户存留度，如何实现？

**解决方案**

- 系统分析出各个分类的最新热点信息条目并组织成 set 集合
- 随机挑选部分信息
- 配合用户关注信息分类中的热点信息组织成展示的全信息集合


**操作指令**

- 随机获取集合中指定数量的数据

```shell
srandmember key [count]
```

- 随机获取集合中的指定数量的数据 并 将该数据迁移出集合

```shell
spop key [count]
```

> 通过 redis 的随机特性，我们可以将 redis 应用于随机类信息的检索，例如点歌单推荐，热点信息推荐，热卖旅游路线，应用 APP 推荐，大 V 推荐等等。



## 3. set的对比操作

**需求案例**

假设我们有如下需求

社交APP为了促进用户之间的交流，需要让每位用户拥有大量的好友，如何快速为用户积累更多的好友？

社区APP为了增加用户热度，提高用户存留性，需要用户在关注更多的人，以此获得更多的信息或热门话题，如何提高用户关注他人的总量？

外卖APP为了提升成单量，必须帮助用户挖掘美食需求，如何推荐用户最适合自己的美食？


**解决方案**

用户同类信息的进行关联搜索，二度关联搜索，深度关联搜索，示例如下：

- 显示共同关注（一度检索）
- 显示共同好友（一度检索）
- 由用户 A 出发，获取到好友用户 B 的好友信息列表（一度检索）
- 由用户 A 出发，获取到好友用户 B 的购物清单列表（二度检索）
- 由用户 A 出发，获取到好友用户 B 的游戏充值列表（二度检索）


**操作指令**

在redis中，我们可以使用以下操作指令操作进行集合操作


- 求两个集合的交、并、差集

```shell
# 求交叉的数据
sinter key1 [key2]
# 求合并的数据
sunion key1 [key2]
# 求相差的数据，有方向性，用key1的集合  减去key1与key2的并集，得到的结果就是差集
sdiff key1 [key2]
```

- 求两个集合的交、并、差，并存储到指定的集合中

```shell
sinterstore desination key1 [key2]
sunionstore desination key1 [key2]
sdiffstore desination key1 [key2]
```

如 将 u1 与 u2 的交集存到 u3

```shell
sinterstore u3 u1 u2
```

- 将指定数据从原始数据集合中移动到目标集合

```shell
smove source destination member
```

如将 u2 的 w1 移到 u1

```shell
smove u2 u1 w1
```







