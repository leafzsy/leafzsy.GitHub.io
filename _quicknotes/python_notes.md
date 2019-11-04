---
layout: post
title:  "python_notes"
date:   2019-9-11 16:00
comments: true
tag:
- python3
- notes
---

## base记背小节一
- x.split(' ')  #通过制定分隔符，进行分割
- x.formart(x) #在string插入变量
- with open('mpg.csv') as csvfile:
    mpg = list(csv.DictReader(csvfile)) #打开csv
- x.keys() #表头
- x.append(a) #列表末尾添加元素
- dt.datetime.fromtimestamp(tm.time()).year #当前年(datetime as dt, time as tm)
-  dt.timedelta(days = 100) # 100天，可与时间加减
- map(fun, iter) # 循环列表执行函数
- x.shape # x的(行, 列)
- numpy.arange(start, stop, step, dtype) #创建一个间隔为step的1维数组ndarray
- np.linspace(0, 4, 9) # 生成9个元素的等差ndarray
- n.reshape(3, 5) # 返回重排列的数组
- n.rasize(3, 5) # 直接改变数据n的排列
- np.repeat([1,2,3],3) #数组每个元素按顺序扩展到3个
- np.vstack([p, 2*p]) #对应行连接
- np.hstack([p, 2*p]) #对应列连接
- z = z.astype('f') #改变数据类型
- z.stype() #返回数据类型
- a.argmax()  #返回最大值索引
- s[-5::-2] #返回索引从-5开始-2的数
- r[-1, ::2] #返回-1行，索引从0开始+2的数
- np.random.randint(0, 10, (4,3)) #生成范围0-10的int随机数组
- zip(a,b) #把a、b打包为元组的列表，类型为zip

## pandas函数记背小节二
```python
%%timeit -n 100  # jupyter 中的测量代码块时间
Series.iloc[3]  # 等同于 Series[3]
Series.loc['Golf'] # 等同于 Series['Golf']
Series.drop('a')  # 除了行名index是‘a’的
pd.read_csv('a.csv', index_col=0, skiprows=1 )  # index_col 可选择哪一列为index ; skiprows 可选择从哪一行开始读取。
DataFrame.rename(index={old_name1: new_name2}, columns={old_name2: new_name2,old_name3: new_name3}, inplace=True) #columns 列; inplace 如果是true 则不进行copy，直接在DataFrame上更改.
DataFrame.dropna()  # 返回一个去掉存在nan行的DataFrame
DataFrame.set_index('Gold')  # 改变index列
DataFrame.reset_index()  # 回到初始index列
DataFrame['SUMLEV'].unique()  # 返回一列中不同的值
DataFrame.fillna(method='ffill')  # 向下传播值，补全nan
DataFrame.fillna({'A': 0, 'B': 1, 'C': 2, 'D': 3}, limit=1)  #只补全第一行
```

## pandas记背小节三
```python
df['Gold'].idxmax()  # 返回最大值index
df['Points']  # 选取 'Points' 列
census_df[['STNAME','one']].set_index('STNAME').sum(level='STNAME')['one'].idxmax()  # 算出每个相同的 STNAME 的和，并找出求和后 one 中最大的index
df.sort_values(by=['STNAME','CENSUS2010POP'], ascending = False)  # 按先后倒序排列
state_top = pd.DataFrame(columns=['CENSUS2010POP'])  # 创建空 DataFrame
state_top.loc[state] = 1  # 添加或更改行
df7.max(axis = 1)  # 每行的最大值
(census_df['REGION']==1) | (census_df['REGION']==2)  # 要加括号
df8[df8['CTYNAME'].str.contains('Washington')]  # Series.str.contains(self, pat, case=True, flags=0, na=nan, regex=True) 包含string
```

## pandas进阶记背小节四
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
df.asfreq(freq='6D', method='ffill'
```

## Assignment 3记背小节
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
```
