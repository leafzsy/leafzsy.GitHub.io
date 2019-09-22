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

## 记背小节
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


