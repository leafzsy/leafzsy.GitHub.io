---
layout: post
title:  "Introduction to Data Science in Python(week4)"
date:   2019-10-26 17:00
description: from "https://www.coursera.org/learn/python-data-analysis?"
comments: true
share: true
tag:
- python3
---

## Distributions in Pandas
 [week4](https://github.com/leafzsy/leafzsy.github.io/blob/master/images/Introduction%20to%20Data%20Science%20in%20Python/Week_4.ipynb)

## week4 记背小节
```python
#二项式分布 np.random.binomial(n, p, size) 
np.random.binomial(1, 0.01,200) 
#均匀分布
np.random.uniform(0, 1, 10)
#正态分布，高斯分布 np.random.normal(u,a,size=10)
np.random.normal(0,1,size=10)
#卡方分布
np.random.chisquare(2, size=10000)

import scipy.stats as stats
# 峰度 
stats.kurtosis(distribution)
# 样本偏度
stats.skew(distribution)
#T检验
stats.ttest_ind(early['assignment1_grade'], late['assignment1_grade'])

```
## Assignment 4记背小节
```python
# 读取txt
file = open('university_towns.txt','r',encoding='utf-8')
ut = file.readlines()
# 创建循环日期
pd.period_range(start = '2000-01',end = '2016-06',freq = '3M')
```


