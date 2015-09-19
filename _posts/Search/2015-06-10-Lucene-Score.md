---
layout: post
title: "Lucene Score"
keywords: ["Lucene","Search"]
description: "Lucene Score"
category: "Lucene"
tags: ["Lucene","Search"]
---
Lucene Score 评分机制

$$score(q,d)=coord(q,d)*queryNorm(q)\sum_{t -in- d }(tf( t- in -d)*idf(t)^2*t.getBoost()*norm(t,d)$$
