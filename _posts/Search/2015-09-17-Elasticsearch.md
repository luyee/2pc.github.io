---
layout: post
title: "Elasticsearch"
keywords: ["distributed","Search"]
description: "Elasticsearch"
category: "distributed"
tags: ["distributed","Search","Elasticsearch"]
---

### 安装配置
这里使用的2.3.3版本，这个版本默认不能用root直接启动。
具体参考[Bootstrap.java](https://github.com/elastic/elasticsearch/blob/93de1ed6068e8e9f35897f623efe00aa3cfafeea/core/src/main/java/org/elasticsearch/bootstrap/Bootstrap.java#L89)中的代码

```
public static void initializeNatives(Path tmpFile, boolean mlockAll, boolean seccomp, boolean ctrlHandler) {
  final ESLogger logger = Loggers.getLogger(Bootstrap.class);

  // check if the user is running as root, and bail
  if (Natives.definitelyRunningAsRoot()) {
      if (Boolean.parseBoolean(System.getProperty("es.insecure.allow.root"))) {
          logger.warn("running as ROOT user. this is a bad idea!");
      } else {
          throw new RuntimeException("don't run elasticsearch as root.");
      }
  }
```
可以通过参数-Des.insecure.allow.root=true 来实现
```
bin/elasticsearch  -Des.insecure.allow.root=true 
```

先给Elasticsearch启动，建立一个账户

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

[2.3版本的参考文档](https://www.elastic.co/guide/en/elasticsearch/reference/2.3/index.html)，可以看看

Breaking changes
>
* [2.3-Breaking changes](https://www.elastic.co/guide/en/elasticsearch/reference/2.3/breaking-changes-2.3.html)
* [2.2-Breaking changes](https://www.elastic.co/guide/en/elasticsearch/reference/2.3/breaking-changes-2.2.html)
* [2.1-Breaking changes](https://www.elastic.co/guide/en/elasticsearch/reference/2.3/breaking-changes-2.1.html)
* [2.0-Breaking changes](https://www.elastic.co/guide/en/elasticsearch/reference/2.3/breaking-changes-2.0.html)
* [1.6-Breaking changes](https://www.elastic.co/guide/en/elasticsearch/reference/2.3/breaking-changes-1.6.html)
* [1.4-Breaking changes](https://www.elastic.co/guide/en/elasticsearch/reference/2.3/breaking-changes-1.4.html)
* [1.0-Breaking changes](https://www.elastic.co/guide/en/elasticsearch/reference/2.3/breaking-changes-1.0.html)

参考

>
*[Elasticsearch 权威指南](http://learnes.net/index.html)


