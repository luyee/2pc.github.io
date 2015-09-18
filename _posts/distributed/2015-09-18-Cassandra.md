---
layout: post
title: "Google Spanner F1"
keywords: ["distributed"]
description: "Google Spanner F1"
category: "distributed"
tags: ["distributed","Spanner"]
---


#### 一致性等级ConsistencyLevel
```
ANY         (0),
ONE         (1),
TWO         (2),
THREE       (3),
QUORUM      (4),
ALL         (5),
LOCAL_QUORUM(6, true),
EACH_QUORUM (7),
SERIAL      (8),
LOCAL_SERIAL(9),
LOCAL_ONE   (10, true);
```

#### 维护最终一致性
>逆熵（Anti-Entropy）
读修复（Read Repair）
提示移交（Hinted Handoff）
分布式删除
