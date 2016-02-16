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

