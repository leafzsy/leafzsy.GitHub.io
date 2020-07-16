---
layout: post
title:  "excel_tableau_mysql notes"
date:   2020-5-27 16:22
comments: true
tag:
- notes
---
## Mastering Data Analysis in Excel
### First week
- 标准普尔500指数（Standard & Poor's 500, S&P 500）：是一个由1957年起记录美国股市的平均记录，观察范围达美国的500家上市公司。公式：LN(A/B)， 其中A和B为开盘价

- 月回报率（monthly return）、年回报率（annual return）：是开盘价指数的和，即：SUM(LN(A/B),LN(B/C),LN(C/D)...)

- 夏普比率（Sharpe ratio），又叫夏普指数（Sharpe index）：衡量的是一项投资（例如证券或投资组合）在对其调整风险后，相对于无风险资产的表现。是投资收益与无风险收益之差的期望值，再除以投资标准差（即其波动性）。

### Second week
- 混淆矩阵（confusion matrix）

|         |               | 预测类别          |
|  ---- |   :-----:  | :---------:  | :----: |
|         |               |  真            |  假     |
|真实类别 | 阳性  |  真阳性TP  |  假阳性FP |
|         | 阴性  |  假阴性FN  |  真阴性TN |
{:.inner-borders}





## Data Visualization and Communication with Tableau
- SMART原则中的五个字母分别对应了五个英文单词：Specific（明确）、Measurable（可衡量）、Achievable（可达成）、Relevant（相关）和Time-bound（有时限）。

- 项目开始前，要清楚的定义数据分析应创造的价值。