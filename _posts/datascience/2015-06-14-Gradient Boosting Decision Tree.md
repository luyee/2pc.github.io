---
layout: post
title: "Gradient Boosting Decision Tree"
keywords: ["ML","Datascience","LambdaMART","RankNet","RankBoost","GBDT"]
description: "Datascience Guide"
category: "Datascience"
tags: ["ML","Datascience"]
---

分裂：分裂后的均方误差最小
随机选择rand_fea_num个特征进行分裂，确定最优的分裂特性
```
for (int i = 0; i < gbdt_inf.rand_fea_num; ++i) 
 {
  int select = rand() % (last+1);//随机选择一个特征
 }
```
