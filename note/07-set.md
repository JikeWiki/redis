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
smemberm key
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


## 2. set类型数据的扩展操作









