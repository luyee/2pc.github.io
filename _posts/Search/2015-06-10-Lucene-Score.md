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

算法公式：
$$score(q,d)=coord(q,d)*queryNorm(q)\sum_{t\ in\ d }(tf( t\ in\ d )*idf(t)^2*t.getBoost()*norm(t,d)$$

其中，
*  tf(t in d) 
表示词频，
* idf(t)
词的逆词频
