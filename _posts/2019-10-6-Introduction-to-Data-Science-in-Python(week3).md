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
```python3
#还原为数字索引
df.reset_index()
#how='outer' 匹配index合并，包含2表所有的index;'inner' 只包含2表重复的index;'left' 左连接，包含左边表的所有index.
pd.merge(x_df,y_df,how='outer',left_index=True,right_index=True)
#left_on='Name' 左右表匹配的列名columns; 出现重名columns,都保留
pd.merge(x_df, y_df, how='left', left_on=['First Name','Last Name'], right_on=['First Name','Last Name']) 
# 对函数按行或按列批量处理
df.apply(min_max, axis=1)
```

