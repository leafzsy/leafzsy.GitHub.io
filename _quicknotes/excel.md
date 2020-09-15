---
layout: post
title:  "Mastering Data Analysis in Excel notes"
date:   2020-5-27 16:22
comments: true
tag:
- notes
---
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
	
![Confusion Matrix]({{ site.url }}/images/notes/Confusion Matrix.png){:.center-image}

- Does the change in threshold change the test's Area under the ROC Curve? Use logic - no need to calculate any numbers.(no)
>阈值的变化是否会改变ROC曲线下的测试面积？使用逻辑-无需计算任何数字。（不会）

- Points on the ROC curve represent the false positive rate and true positive rate at each possible threshold. Changing the threshold signifies a different point on the ROC Curve, but does not change the overall shape of the curve.
>ROC曲线上的点代表每个可能阈值处的假阳性率和真阳性率。更改阈值表示ROC曲线上的其他点，但不会更改曲线的整体形状

### Third week
- 熵（entropy），不确定性的量度，因为越随机的信源的熵越大。

![entropy_chart]({{ site.url }}/images/notes/entropy_chart.png){:.center-image}

- 条件概率（conditional probability），P(A|B)*P(B)=P(AB), P(A)=P(AB)+P(A~B), P(B)+P(~B)=1
- 贝叶斯定理（Bayes' theorem），P(A|B)*P(B)=P(B|A)*P(A)
#### 错题

![entropy]({{ site.url }}/images/notes/entropy.png){:.center-image}

1. What is the remaining uncertainty or entropy of the test classification if we learn a chip is truly defective?（1bit）
>如果芯片确实有缺陷，那么测试分类的剩余不确定性或熵是多少？

2. What is the remaining uncertainty, or entropy, of the Test Classification, if we know that a chip is not-defective?（0.8113bit）
>如果芯片确实没有缺陷，那么测试分类的剩余不确定性或熵是多少？

3. What is the expected, or average, uncertainty or entropy, remaining regarding a Test Outcome, give knowledge of whether or not a chip is defective?（0.8490bit）
>关于测试结果，剩余多少预期或平均的不确定性熵能使您知道芯片是否有缺陷吗？

### Fourth week
- 正态分布（normal distribution）又名高斯分布（Gaussian distribution），是一个非常常见的连续概率分布。
- 若随机变量X服从一个位置参数为μ 、尺度参数为σ的正态分布，记为：X~N(μ,σ²)。

- 标准分数（Standard Score，又称z-score，中文称为Z-分数或标准化值）
- 其约化过程被称为“标准化”（standardizing）。
- 标准分数可借由以下公式求出：z=(x-μ)/σ，其中σ≠0。

- 函数stdev的根号里面的分母是n-1,而stdevp是n，如果是抽样当然用stdev。

- 任何高斯连续概率分布的熵（entropy）=2.05 + log2(σ)
- Percentage Information Gain（信息增益率） = -log2(SQRT(1-R-squared ))/2.05 ，其中R-squared是相关系数Correlation R的平方，2.05是熵（entropy）。
- 1=R^2+(error)^2=R^2+σ^2，其中error是均方根误差（标准偏差）= σ1/σ2

- 标准化后，回归线的斜率β将等于x和y的相关性。

- 线性回归（linear regression）是利用称为线性回归方程的最小二乘函数对一个或多个自变量和因变量之间关系进行建模的一种回归分析。
- 最小二乘法（least squares method），又称最小平方法，是一种数学优化建模方法。它通过最小化误差的平方和寻找数据的最佳函数匹配。以下例子来自维基

![entropy]({{ site.url }}/images/notes/least-squares.png){:.center-image}

- 中心极限定理说明，在适当的条件下，大量相互独立随机变量的均值经适当标准化后依分布收敛于正态分布。这组定理是数理统计学和误差分析的理论基础，指出了大量随机变量之和近似服从正态分布的条件。
> 一组“ n”个项目的样本均值的标准偏差与基础总体x的标准偏差（在这种情况下，“种群”具有单独的模型误差）相关，则样本均值的标准差是 x / sqrt( n )。

- 协方差定义为 R*Std.Dev(1)*Std.Dev(2).

