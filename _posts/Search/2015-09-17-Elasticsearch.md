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

```
Elasticsearch运行账户：Elasticsearch
Elasticsearch环境路径：/data/elasticsearch
```

新增用户并将/data/elasticsearch目录权限给Elasticsearch用户组

```
mkdir  /data/elasticsearch/
useradd elasticsearch
passwd  elasticsearch
chown -R elasticsearch:elasticsearch  /data/elasticsearch/
cd /data/elasticsearch/
wget https://download.elastic.co/elasticsearch/release/org/elasticsearch/distribution/tar/elasticsearch/2.3.3/elasticsearch-2.3.3.tar.gz
tar zxvf elasticsearch-2.3.3.tar.gz 
chown -R elasticsearch:elasticsearch elasticsearch-2.3.3
su elasticsearch
cd /data/elasticsearch/elasticsearch-2.3.3
bin/elasticsearch
```
安装ik分词,[medcl](https://github.com/medcl)大神更新很快

```
wget https://github.com/medcl/elasticsearch-analysis-ik/releases/download/v1.9.3/elasticsearch-analysis-ik-1.9.3.zip
unzip  elasticsearch-analysis-ik-1.9.3.zip  -d  ./plugins/ik
```


