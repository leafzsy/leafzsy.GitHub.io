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

|         |              | Test Classification  Y
|  ---- |   :-----:  | :---------:  | :----: |
|         |               |  positive |  negative  |
| Condition | +阳性  |  真阳性TP  |  假阳性FN |
| X        | -阴性  |  假阴性FP  |  真阴性TN |
{:.inner-borders}
	
![My helpful screenshot]({{ site.url }}/images/notes/Confusion Matrix.png){:.center-image}

- Does the change in threshold change the test's Area under the ROC Curve? Use logic - no need to calculate any numbers.(no)
···
阈值的变化是否会改变ROC曲线下的测试面积？使用逻辑-无需计算任何数字。（不会）
···
- Points on the ROC curve represent the false positive rate and true positive rate at each possible threshold. Changing the threshold signifies a different point on the ROC Curve, but does not change the overall shape of the curve.
···
ROC曲线上的点代表每个可能阈值处的假阳性率和真阳性率。更改阈值表示ROC曲线上的其他点，但不会更改曲线的整体形状
···

### Third week



## Data Visualization and Communication with Tableau
- SMART原则中的五个字母分别对应了五个英文单词：Specific（明确）、Measurable（可衡量）、Achievable（可达成）、Relevant（相关）和Time-bound（有时限）。

- 项目开始前，要清楚的定义数据分析应创造的价值。