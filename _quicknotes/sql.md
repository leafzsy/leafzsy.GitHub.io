---
layout: post
title:  "Managing Big Data with MySQL                                                 "
date:   2020-12-11 17:02
comments: true
tag:
- sql
- notes
---

## Week1: Entity-Relationship Diagrams
> Which of the following statements are true about foreign keys? Check all that apply. (Note that you will need to select more than one correct response to answer this question correctly.)
A. Foreign keys allow information in different tables to be linked to each other
B. Foreign keys are columns with unique values for every row in the relation/table they are in
C. Foreign keys refer to columns with unique values for every row in other relations/tables
D. Foreign keys always have the same name as at least one primary key in another table
Correct	Answer: A,C

- 外键允许不同表中的信息相互链接
- 外键是引用其他关系/表中每一行具有唯一值的列

> The technical term for items in a relational schema that become columns in a real database is "attributes"
The technical term for items in a relational schema that become rows in a real database is "tuples"

- 关系模式中成为真实数据库中的列的项目的技术术语为“属性”
- 关系模式中成为真实数据库中的行的项目的技术术语为“元组”

> For relational databases to work most efficiently, which of the following requirements of set theory should be followed? Check all that apply. (Note that you will need to select more than one correct response to answer this question correctly.)
A. Each row in a table should represent a unique instance of the information in that table
B. Each column in a table should represent a unique category of information
C. Single tables should represent the smallest logical parts of a data set
D. There should be no NULL values allowed in the database
Correct	Answer: A,B,C

- 表中的每一行应代表该表中信息的唯一实例
- 表格中的每一列应代表唯一的信息类别
- 单个表应代表数据集的最小逻辑部分

## Week2: Queries to Extract Data from Single Tables
```sql
/*1.替换*/
SELECT DISTINCT breed,
REPLACE(breed,'-','') AS breed_fixed
FROM dogs
ORDER BY breed_fixed 
LIMIT 10

/*2.修剪 LEADING (起头), TRAILING (结尾), or BOTH (起头及结尾)*/
SELECT DISTINCT breed, TRIM(LEADING '-' FROM breed) AS breed_fixed
FROM dogs
ORDER BY breed
LIMIT 100


```
