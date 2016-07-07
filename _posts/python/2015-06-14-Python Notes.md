---
layout: post
title: "Python Notes"
keywords: ["python"]
description: "python"
category: "python"
tags: ["python","python"]
---

#### python列表类型 
extend()与append()
#####　append() 只追加得到额外的一个元素,可以认为是tuple，extend()只能是一个列表

```
>>> a=[1,2]
>>> b=[3,5]
>>> c=[3,5]
>>> b.append(a)
>>> c.extend(a)
>>> b
[3, 5, [1, 2]]
>>> c
[3, 5, 1, 2]
>>> len(b)
3
>>> len(c)
4
```

##### set list互转

```
>>> a=set('123456')
>>> a
set(['1', '3', '2', '5', '4', '6'])
>>> b=list(a)
>>> b
['1', '3', '2', '5', '4', '6']
>>> s=set(b)
>>> s
set(['1', '3', '2', '5', '4', '6'])
```
