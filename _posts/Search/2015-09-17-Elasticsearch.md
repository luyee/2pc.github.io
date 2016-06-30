---
layout: post
title: "Elasticsearch"
keywords: ["distributed","Search"]
description: "Elasticsearch"
category: "distributed"
tags: ["distributed","Search","Elasticsearch"]
---

### 安装配置
这里使用的2.3.3版本，这个版本已经不能用root启动了。需要先给Elasticsearch启动，建立一个账户
>Elasticsearch运行账户：Elasticsearch
>Elasticsearch环境路径：/data/elasticsearch

新增用户并将/data/elasticsearch目录权限给Elasticsearch用户组

```
mkdir  /data/elasticsearch/
useradd elasticsearch
passwd  elasticsearch
chown -R elasticsearch:elasticsearch  /data/elasticsearch/
cd /data/elasticsearch/
wget https://download.elastic.co/elasticsearch/release/org/elasticsearch/distribution/tar/elasticsearch/2.3.3/elasticsearch-2.3.3.tar.gz
```

