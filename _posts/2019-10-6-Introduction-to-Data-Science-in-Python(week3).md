---
layout: post
title:  "Introduction to Data Science in Python(week3)"
date:   2019-10-6 21:45
description: from "https://www.coursera.org/learn/python-data-analysis?"
comments: true
share: true
tag:
- python3
---

## pandas进阶
<iframe src="https://nbviewer.jupyter.org/github/leafzsy/leafzsy.github.io/blob/master/images/ipynb/week3_notes.ipynb" width="100%" height="600" marginheight="0" marginwidth="0" frameborder="0"></iframe>

### 记背小节
```python
#还原为数字索引
df.reset_index()
#how='outer' 匹配index合并，包含2表所有的index;'inner' 只包含2表重复的index;'left' 左连接，包含左边表的所有index.
pd.merge(x_df,y_df,how='outer',left_index=True,right_index=True)
#left_on='Name' 左右表匹配的列名columns; 出现重名columns,都保留
pd.merge(x_df, y_df, how='left', left_on=['First Name','Last Name'], right_on=['First Name','Last Name'])
# 对函数按行或按列批量处理
df.apply(min_max, axis=1)
# groupby对组进行循环
for group, frame in df.groupby('STNAME'):
  avg = np.average(frame['CENSUS2010POP'])
# groupby对组进行函数算法
df[['STNAME','CENSUS2010POP']].groupby(['STNAME']).mean()
# 按照fun分组
for group, frame in df.groupby(fun):
# DataFrame.agg(self, func, axis=0, *args, **kwargs) 对指定行列或多项求函数
df.groupby('STNAME').agg({'CENSUS2010POP': np.average})
# 改列名
df.rename(columns={0: 'Grades'}, inplace=True)
# 转化为类别数据类型'category'，可设置类别大小
grades = df['Grades'].astype('category',
         categories=['D', 'D+', 'C-', 'C', 'C+', 'B-', 'B', 'B+', 'A-', 'A', 'A+'],
         ordered=True)
# 对avg分成10组，类别属性是范围
pd.cut(df['avg'],10)
# labels 3个级别的名字
pd.cut(s, 3, labels=['Small', 'Medium', 'Large'])
# 数据透视表
df.pivot_table(values='(kW)', index='YEAR', columns='Make', aggfunc=[np.mean,np.min], margins=True)
# 时间数据类型
pd.Timestamp('9/1/2016 10:05AM')
pd.Period('1/2016')
pd.Period('3/5/2016')
# string转化为 datetime
pd.to_datetime(ts3.index)
# Timedelta 时间间隔
pd.Timestamp('9/2/2016 8:10AM') + pd.Timedelta('12D 3H')
# 输出为 Timedelta
pd.Timestamp('9/3/2016')-pd.Timestamp('9/1/2016')
# 每两周一天，从2016-10-01开始的9天
pd.date_range('10-01-2016', periods=9, freq='2W-SUN')
# 返回日期的星期
df.index.weekday_name
#返回与上一行的差异
df.diff()
# 按月求平均
df.resample('M').mean()
# 2017年的行
df['2017']
# 2016-12以后的
df['2016-12':]
# 按照间隔天数向下填充值
df.asfreq(freq='6D', method='ffill')
```

### Assignment 3记背小节
```python
# skiprows 开始跳过行数; skipfooter 末尾跳过行数
energy = pd.read_excel("Energy Indicators.xls",skiprows = 18,usecols =[2,3,4,5],header = None,skipfooter = 38,
                       names = ['Country', 'Energy Supply', 'Energy Supply per Capita', '% Renewable'])
# r' ' 正则匹配
df.str.replace(r'[0-9]+', '')
df.str.replace(r' \(.+\)', '')

# dataframe加上一个series,按照index匹配
Top15['continent'] = pd.Series(ContinentDict)

# 批量把数字改成带千分位string
Top15['PopEst'].map(lambda x:format(x,','))
```
