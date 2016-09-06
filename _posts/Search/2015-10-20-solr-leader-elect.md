---
layout: post
title: "SolrCloud Leader Elect"
keywords: ["distributed","Search","SolrCloud"]
description: "SolrCloud Leader Elect"
category: "distributed"
tags: ["distributed","Search","SolrCloud"]
---
SolrCloud 领导选举，最小seq,这点有点同Kafka seq(0)


SolrCloud Group

```
Caused by: java.lang.OutOfMemoryError: Java heap space
        at org.apache.lucene.codecs.blocktree.SegmentTermsEnumFrame.<init>(SegmentTermsEnumFrame.java:53)
        at org.apache.lucene.codecs.blocktree.SegmentTermsEnum.<init>(SegmentTermsEnum.java:78)
        at org.apache.lucene.codecs.blocktree.FieldReader.iterator(FieldReader.java:156)
        at org.apache.lucene.index.ExitableDirectoryReader$ExitableTerms.iterator(ExitableDirectoryReader.java:141)
        at org.apache.lucene.index.TermContext.build(TermContext.java:94)
        at org.apache.lucene.search.TermQuery.createWeight(TermQuery.java:191)
        at org.apache.lucene.search.IndexSearcher.createWeight(IndexSearcher.java:851)
        at org.apache.lucene.search.BooleanWeight.<init>(BooleanWeight.java:57)
        at org.apache.lucene.search.BooleanQuery.createWeight(BooleanQuery.java:184)
        at org.apache.lucene.search.IndexSearcher.createWeight(IndexSearcher.java:851)
        at org.apache.lucene.search.BooleanWeight.<init>(BooleanWeight.java:57)
        at org.apache.lucene.search.BooleanQuery.createWeight(BooleanQuery.java:184)
        at org.apache.lucene.search.FilteredQuery.createWeight(FilteredQuery.java:81)
        at org.apache.lucene.search.IndexSearcher.createWeight(IndexSearcher.java:851)
        at org.apache.lucene.search.IndexSearcher.createNormalizedWeight(IndexSearcher.java:834)
        at org.apache.lucene.search.IndexSearcher.search(IndexSearcher.java:485)
        at org.apache.solr.search.Grouping.searchWithTimeLimiter(Grouping.java:456)
        at org.apache.solr.search.Grouping.execute(Grouping.java:407)
        at org.apache.solr.handler.component.QueryComponent.process(QueryComponent.java:492)
        at org.apache.solr.handler.component.SearchHandler.handleRequestBody(SearchHandler.java:255)
        at org.apache.solr.handler.RequestHandlerBase.handleRequest(RequestHandlerBase.java:143)
        at org.apache.solr.core.SolrCore.execute(SolrCore.java:2064)
        at org.apache.solr.servlet.HttpSolrCall.execute(HttpSolrCall.java:654)
        at org.apache.solr.servlet.HttpSolrCall.call(HttpSolrCall.java:450)
        at org.apache.solr.servlet.SolrDispatchFilter.doFilter(SolrDispatchFilter.java:227)
        at org.apache.solr.servlet.SolrDispatchFilter.doFilter(SolrDispatchFilter.java:196)
        at org.eclipse.jetty.servlet.ServletHandler$CachedChain.doFilter(ServletHandler.java:1652)
        at org.eclipse.jetty.servlet.ServletHandler.doHandle(ServletHandler.java:585)
        at org.eclipse.jetty.server.handler.ScopedHandler.handle(ScopedHandler.java:143)
        at org.eclipse.jetty.security.SecurityHandler.handle(SecurityHandler.java:577)
        at org.eclipse.jetty.server.session.SessionHandler.doHandle(SessionHandler.java:223)
        at org.eclipse.jetty.server.handler.ContextHandler.doHandle(ContextHandler.java:1127)
```
