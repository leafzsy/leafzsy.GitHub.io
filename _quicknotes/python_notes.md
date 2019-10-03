---
layout: post
title:  "python_notes"
date:   2019-9-11 16:00
comments: true
tag:
- python3
- notes
---

## python base
<iframe src="https://nbviewer.jupyter.org/github/leafzsy/leafzsy.github.io/blob/master/images/ipynb/python_week1_notes.ipynb" width="100%" height="600" marginheight="0" marginwidth="0" frameborder="0"></iframe>

### 函数记背小节一
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

## pandas
<iframe src="https://nbviewer.jupyter.org/github/leafzsy/leafzsy.github.io/blob/master/images/ipynb/week2_notes.ipynb" width="100%" height="600" marginheight="0" marginwidth="0" frameborder="0"></iframe>

### 函数记背小节二
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

## pandas 作业
<iframe src="https://nbviewer.jupyter.org/github/leafzsy/leafzsy.github.io/blob/master/images/ipynb/Assignment2.ipynb" width="100%" height="600" marginheight="0" marginwidth="0" frameborder="0"></iframe>

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

