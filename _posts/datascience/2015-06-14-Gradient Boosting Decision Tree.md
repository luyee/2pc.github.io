---
layout: post
title: "Gradient Boosting Decision Tree"
keywords: ["ML","Datascience","LambdaMART","RankNet","RankBoost","GBDT"]
description: "Datascience Guide"
category: "Datascience"
tags: ["ML","Datascience"]
---

谈到GBDT的时候个人认为首先应该指出是残差版本还是Gradient版本，因为在原理，求解，实现上存在一些差异（这个差异在理解上可能会导致犯迷糊，绕不少弯路）,这里主要讨论残差版本。主要研究已知的开源C版本的实现方式和Java版本的实现（Ranklib和jforests,感觉Ranklib版本的更好理解）

>先贴几套开源实现代码的地址,这里主要研究的2,3，其中2是c版的残差版本,3是中的MART也是残差版本实现，用到LambdaMART

1. Xgboost[Xgboost源码-github](https://github.com/dmlc/xgboost/tree/master/)[Xgboost文档](https://xgboost.readthedocs.io/en/latest/)
2. [gbdt源码下载地址-CSDN,居然10积分](http://download.csdn.net/detail/w28971023/4837775)
3. Ranklib[sourceforge地址](https://sourceforge.net/p/lemur/wiki/RankLib/)
4. simple-gbdt[google code地址](https://code.google.com/archive/p/simple-gbdt/) 依赖tbb库[github 某同学fork版本](https://github.com/hcy0807/simple-gbdt)

1中Xgboost支持力度很大，支持python,R，Java.etc 甚至spark

2中所指gbdt是有几篇分析的文章都是用的这个版本，这个版本训练是没啥问题，不过predict的时候不友好，感觉简化了。改了下

3中Ranklib支持的算法也很多，基本可以开包即用了.

4中simple-gbdt，依赖tbb库.

分裂：分裂后的均方误差最小

随机选择rand_fea_num个特征进行分裂，确定最优的分裂特性

```
for (int i = 0; i < gbdt_inf.rand_fea_num; ++i) 
 {
  int select = rand() % (last+1);//随机选择一个特征
 }
```

Best split计算

计算公式：

![游园惊梦-GBDT原理实例演示 2](http://images.cnitblog.com/blog/61573/201503/251821497246538.png)

代码实现

```
for (int j=ninf.index_b; j< ninf.index_e; j++)
{
// d = y_result_score[data_set->order_i[j]];
d = data_set->y_list[data_set->order_i[j]];
  left_sum += d;
  right_sum -= d;
  left_num++;
  right_num--;
if (data_set->fv[j] < data_set->fv[j+1])
  {/** 均方误差Mean Squared Error, MSE）最小? */
	crit = (left_sum * left_sum / left_num) + (right_sum * right_sum / right_num) - ninf.critparent;
  	if (crit > critvar) 
	{
		tmpsplit = (data_set->fv[j] + data_set->fv[j+1]) / 2.0; // 实际分割用的feature value
		critvar = crit;
	}
  }
}

if (critvar > critmax) // 如果这个feature最终的critvar > cirtmax, 保存信息
{
spinf->bestsplit = tmpsplit; // split feature vale
  spinf->bestid = fid; // split feature id
  critmax = critvar; // split crit vaule
}
```

节点的输出值为该节点上所有sample的label的均值
ranklib中MART的实现,在GBDT中pseudoResponses就是残差，也就是label

```
protected void updateTreeOutput(RegressionTree rt)
{
	List<Split> leaves = rt.leaves();
	for(int i=0;i<leaves.size();i++)
	{
		float s1 = 0.0F;
		Split s = leaves.get(i);
		int[] idx = s.getSamples();
		
		System.out.println("leaves(i)" + i +" idx.length: "+idx.length);
		for(int j=0;j<idx.length;j++)
		{
			int k = idx[j];
			s1 += pseudoResponses[k];
		}
		s.setOutput(s1/idx.length);
	}
}
```

