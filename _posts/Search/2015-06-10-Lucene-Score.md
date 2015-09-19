---
layout: post
title: "Lucene评分机制(Score)"
keywords: ["Lucene","Search"]
description: "Lucene Score"
category: "Lucene"
tags: ["Lucene","Search"]
---
Lucene Score 评分机制

先来看几个数学公式，参考官方文档对[TFIDFSimilarity](http://lucene.apache.org/core/5_3_0/core/org/apache/lucene/search/similarities/TFIDFSimilarity.html)的说明

### 分值算法公式：

$$score(q,d)=coord(q,d)*queryNorm(q)\sum_{t\ in\ d }(tf( t\ in\ d )*idf(t)^2*t.getBoost()*norm(t,d)$$

其中

* tf(t in d) 表示词频，Term在当前文档中出现的次数
* idf(t) 词的逆词频
* coord(q,d) 评分因子。越多的查询项(Term)在一个文档中，说明这些文档的匹配程序越高
* queryNorm(q) 标准化因子，用于查询时比较
* t.getBoost() 权重，这个可以在查询的时候给定，也可以在索引的时候给定
* norm(t,d)

#### 词频tf(t in d) 计算公式

$$tf(t in d)=sqrt{frequency}$$

