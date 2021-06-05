---
layout: post
title:  "数据库系统概念"
date:   2019-1-4 19:00
description: (第六版)第一章--from "Database System Concepts" Avi Silberschatz, Henry F. Korth, S. Sudarshan
comments: true
tag:
- sql
- notes
---

[英文版课后习题答案资源](https://pan.baidu.com/s/1CBPC-SKRjmlvTonZrlzNnw)
提取码: y83f

# 1第一章引言
## 数据库日常维护
- 定期备份数据库;
- 确保运转空间;
- 确保数据库性能.

## 1课后习题
### 1.2数据库系统与类似于Jave或C++的语言中数据定义语言的不同之处
- 在DDL中执行操作会导致在数据库中创建对象;相反，编程语言类型声明只是程序中使用的抽象。
- 数据库DDL允许指定一致性约束，编程语言类型系统通常不允许。这些包括域约束和参照完整性约束。
- Database DDL支持授权，为不同用户提供不同的访问权限。编程语言类型系统不提供这样的保护（充其量，它们保护类中的属性不被另一个类中的方法访问）。
- 编程语言类型系统通常比SQL类型系统更丰富。大多数数据库仅支持基本类型，例如不同类型的数字和字符串，尽管某些数据库确实支持某些复杂类型，例如数组和对象。
- 数据库DDL专注于指定关系属性的类型;相反，编程语言允许创建对象和对象集合。

### 1.3为企业建立数据库的六个主要步骤
- 定义企业的高级需求（此步骤生成称为系统需求规范的文档。）
- 定义包含所有适当类型的数据和数据关系的模型。
- 定义数据的完整性约束。
- 定义物理层。
- 对于要定期解决的每个已知问题（例如，由职员或Web用户执行的任务）定义用于执行任务的用户界面，并编写必要的应用程序以实现用户界面。
- 创建/初始化数据库。

### 1.8文件处理系统和DBMS的四个主要区别
- 两个系统都包含一组数据和一组访问该数据的程序。数据库管理系统协调对数据的物理和逻辑访问，而文件处理系统仅协调物理访问。
- 数据库管理系统通过确保所有授权访问它的程序可以使用物理数据来减少数据复制量，而文件处理系统中一个程序写入的数据可能无法被其他程序读取。
- 数据库管理系统被设计为允许灵活地访问数据（即查询），而文件处理系统被设计为允许预先访问数据（即编译的程序）。
- 数据库管理系统旨在协调同时访问相同数据的多个用户。文件处理系统通常设计为允许一个或多个程序同时访问不同的数据文件。在文件处理系统中，只有当两个程序都具有对文件的只读访问权限时，才能同时访问两个程序的文件。

### 1.9
- 物理数据独立性是指在不必重写应用程序的情况下修改物理方案的能力。 此类修改包括从未阻止记录存储更改为阻止记录存储，或从顺序访问文件更改为随机访问文件。 这样的修改可能是在记录中添加一个字段; 应用程序的视图隐藏了程序中的此更改。

### 1.10数据库管理系统的五个职责,及不能履行时的问题
    通用数据库管理系统（DBMS）有五个职责：
    a.与文件管理器的交互。
    b.完整性实施。
    C.安全性实施。
    d.备份和恢复。
    e.并发控制。
    如果给定的DBMS没有满足这些职责（并且文本指出有时设计省略了责任，例如微型计算机的单用户DBMS上的并发控制），则可能分别出现以下问题：
    a.如果没有文件管理器交互，那么可以检索文件中存储的任何内容。
    b.可能不满足一致性约束，例如，教师可能属于不存在的部门，两个学生可能具有相同的ID，帐户余额可能低于允许的最小值等。
    C.未经授权的用户可以访问数据库，或者有权访问部分数据库的用户可能能够访问他们缺乏权限的数据库部分。例如，低级别用户可以访问国防密码，或者员工可以找出他们的主管赚取的东西（这可能是一个秘密）。
    d.数据可能会永久丢失，而不是至少在故障之前存在的一致状态下可用。
    e.尽管在每个事务中执行了适当的完整性，但可能违反一致性约束。例如，由于在同一帐户上同时提款和存款，可能会反映出错误的银行余额等。


### 1.15描述用于储存社交网络系统的至少三个表如Facebook中的信息
- 包含用户的用户表，其中包含帐户名称，真实姓名，年龄，性别，位置和其他个人资料信息等属性。
- 包含与用户上传内容相关联的其他用户提供的内容（例如文本和图像）的内容表。
- 为每个用户记录的朋友表，其他用户连接到该用户。 连接类型也可以记录在此表中。
- 权限表，记录允许哪类朋友查看用户上传的内容。 例如，用户可以与家人分享一些照片，但不与所有朋友分享。

# 2第二章关系模型介绍
## 超码、候选码、主码

| ID0  | ID1  | ID2  | ID3  |
| ---- | ---- | ---- | ---- |
| 1    | 1    | 1    | 1    |
| 2    | 1    | 2    | 1    |
| 3    | 2    | 1    | 1    |
| 4    | 2    | 2    | 1    |
{:.inner-borders}


- 超码：一个或多个属性组成的集合，可以把每行元组区分开来。如上表：ID1,ID2,ID3 或 ID1,ID2 等。
- 候选码：最小的超码，即任意超码的真子集不是超码，如上表：ID1,ID2 或 ID0。ID1和ID3就不是候选码。
- 主码：用于区分不同元组的候选码。如上表：ID0 或 ID1,ID2。

## 2课后练习
P29
### 2.5
查询学生ID与s_id匹配，并包含每种student和advisor的组合
- 结果包括student的所有属性值和advisor的所有属性的所有组合。 结果中的元组如下： 对于拥有advisor的每个学生，结果是包含学生属性，一个与学生ID属性相同的s_id属性，学生advisorID的i_id属性，而拥有多个顾问的学生将在结果中显示相应的次数。 没有advisor的学生将不会出现在结果中。

### 2.7
> ![answer](/images/2.7answer.png)

### 2.11 关系与关系模式意义上的区别
- 关系模式是类型定义，关系是该模式的实例。 例如，student(ss#,name)是关系模式，也是基于该模式的关系。

### 2.14 数据库引入空值的原因
- 因为实际值可能是未知的或不存在，所以可以将空引入数据库。 例如，地址已更改且其新地址尚不知道的员工应使用空地址保留。
- 如果员工元组具有复合属性dependents，并且特定员工没有dependents属性，则应该为该元组的dependents属性指定空值。

### 2.15 过程化与非过程化语言的相对优点
- 非过程语言极大地简化了查询的规范（至少，它们旨在处理的查询类型）。使用户不必担心如何评估查询; 这不仅减少了编程工作量，而且实际上，在大多数情况下，查询优化器可以做出更好的选择评估查询的最佳方法，而不是通过反复试验的程序员。
- 另一方面，程序语言在它们可以执行的计算方面要强大得多。 某些任务可能无法使用非过程语言完成，或者使用非过程语言很难表达，或者如果以非过程方式指定则执行效率非常低。

# 3第三章SQL
> 数据定义语言(DDL): 定义关系模式、删除关系和修改关系模式。
> 数据操纵语言(DML): 查询，以及插入、删除、修改数据库中的元组。

## 建表
```sql
-- 建表
create table department
	(dept_name	varchar(20),
	building	varchar(15),
	budget	numeric(12,2),
	primary key(dept_name));
create table course
	(course_id	varchar(7),
	title	varchar(50),
	dept_name	varchar(20),
	credits		numeric(2,0),
	primary key (course_id),
	foreigh key (dept_name) references department);
create table temp_instructor like instructor;
create table t1 as 
	(select *
    from instructor
    where dept_name = 'Music')
    with data;
```
## 插入
```sql
-- 插入元组
insert into `instructor`
	values(10211,'Smith','Biology',66000);
insert into `instructor`
	select ...;
insert into instructor(a,b,c)
	values(a,b,c)
```
## 删
```sql
-- 删除元组 where 可以和select里的一样复杂
delete from student where s between a and b;
-- 删除表
drop table r;
-- 增加属性,A为属性名，D为数据类型
alter table r add A D;
-- 删除属性
alter table r drop A;
```
## 更新
```sql
update A
set s =s * 1.05
where s < (select avg(s) from A);
-- case when ... then ...
update A
set s = case
	when s <= 100000 then s*1.05
	else s*1.03
	end;

update A
set t = (
	select case
		when sum(c) is not null then sum(c)
		else 0
		end
	from T where ...)

```
## 查询
### union并, intersect交, except差运算
```sql
-- 并运算，把查询对应列合并,去除重复
(select ...)
union
(select ...)

-- 保留重复
(select ...)
union all
(select ...)

-- 交运算
(select ...)
intersect
(select ...)
(select ...)
intersect all
(select ...)

-- 差运算
(select ...)
except
(select ...)
(select ...)
except all
(select ...)
```

### 空值
```sql
-- 不是true和false,是unknown
1<null
-- 应该用以下的判断
is null
is not null
-- and
true and unknown = unknown
false and unknown = false
unknown and unknown = unknown

-- or
true or unknown = true
false or unknown = unknown
unknown or unknown = unknown

-- not
not unknown = unknown
-- where对于false或unknown的元组不加入结果

-- 聚合
count(*) --包含空值，其他聚合函数都不包含空值
```
### 集合比较
```sql
-- in, not in
where x in (select x from...)
where (x,y) in (select x,y from...)
where (x,y) in (x1,y2)

-- some 
-- 在sql中，some与any同义
-- 至少比某一个大
where x > some(select ...)

-- = some等价于in
-- <>all 等价于 not in
having avg(salary) >= all(select avg(salary) from ...) 
```
### 空关系-唯一性测试
```sql
-- exists 存在
-- 存在总访问量(count 字段)大于 200 的网站
SELECT Websites.name, Websites.url 
FROM Websites 
WHERE EXISTS (SELECT count FROM access_log WHERE Websites.id = access_log.site_id AND count > 200);
-- not exists
-- 不存在总访问量(count 字段)大于 200 的网站
SELECT Websites.name, Websites.url 
FROM Websites 
WHERE NOT EXISTS (SELECT count FROM access_log WHERE Websites.id = access_log.site_id AND count > 200);

-- except 除了
(SELECT  ID, NAME, AMOUNT, DATE
     FROM CUSTOMERS
     LEFT JOIN ORDERS
     ON CUSTOMERS.ID = ORDERS.CUSTOMER_ID
EXCEPT
SELECT  ID, NAME, AMOUNT, DATE
     FROM CUSTOMERS
     RIGHT JOIN ORDERS
     ON CUSTOMERS.ID = ORDERS.CUSTOMER_ID);
     
-- unique 存在唯一的值
```
### with
```sql
-- 创建临时表
with dept(value) as (select)
```

### 标量子查询

```sql
-- 在select嵌套的子查询只返回一个单个值
select dept, (select count(*) from A where A.dept = B.dept) as c_A
    from B;
```




## 3书后习题
```sql

-- # 3.1
-- a
SELECT course_id FROM course WHERE credits=3 AND dept_name='Comp. Sci.';
-- b
SELECT DISTINCT * FROM ADVISOR join instructor on I_ID = ID WHERE name='Einstein'
--学生导师的查询

select distinct * --使用using不能限定
from (student join takes using(ID)) --学生课程
join (instructor join teaches using(ID)) --老师教的课程
using(course_id, sec_id, semester, year) 
where instructor.name = 'Einstein'

SELECT DISTINCT * from takes join (instructor join teaches using(ID)) using(COURSE_ID) WHERE instructor.name = 'Einstein'
-- c
SELECT max(salary) AS max_salary FROM instructor
-- d
SELECT name FROM instructor WHERE salary = (
SELECT max(salary) AS max_salary FROM instructor)
-- e
SELECT course_id,count(course_id) AS c_course FROM takes WHERE semester='Fall' GROUP BY course_id

select course_id, sec_id, count(ID)
from section natural join takes
where semester = 'Fall'
and year = 2009
group by course_id, sec_id

select course_id, sec_id,
(select count(ID)
from takes
where takes.year = section.year
and takes.semester = section.semester
and takes.course_id = section.course_id
and takes.sec_id = section.sec_id)
from section
where semester = 'Fall'
and year = 2009
--f
SELECT max(c_course) AS max_students FROM (
SELECT course_id,count(course_id) AS c_course FROM takes WHERE semester='Fall' and YEAR = 2009 GROUP BY course_id) fall_course

select max(enrollment)
from (select count(ID) as enrollment
from section natural join takes
where semester = 'Fall'
and year = 2009
group by course_id, sec_id)

--g
SELECT course_id FROM (
SELECT course_id,count(course_id) AS c_course FROM takes WHERE semester='Fall' GROUP BY course_id) fall_course WHERE c_course IN (
SELECT max(c_course) AS max_students FROM (
SELECT course_id,count(course_id) AS c_course FROM takes WHERE semester='Fall' GROUP BY course_id) fall_course)

with sec_enrollment as ( --子查询部分（subquery factoring）
select course_id, sec_id, count(ID) as enrollment
from section natural join takes
where semester ='Fall'
and year = 2009
group by course_id, sec_id)
select course_id, sec_id
from sec_enrollment
where enrollment = (select max(enrollment) from sec_enrollment)

-- #3.3
-- a
update INSTRUCTOR set SALARY = SALARY * 1.1 WHERE DEPT_NAME = 'Comp. Sci.'

-- b
DELETE from COURSE where COURSE_ID not in (SELECT COURSE_ID from SECTION)

-- c

INSERT INTO INSTRUCTOR SELECT ID,NAME,DEPT_NAME,10000 as SALARY FROM STUDENT WHERE TOT_CRED > 100 
--插入失败。salary要求大于29000

-- #3.6
SELECT * FROM DEPARTMENT WHERE LOWER(DEPT_NAME) LIKE '%sci%'

-- #3.11
-- a
SELECT DISTINCT NAME FROM STUDENT WHERE DEPT_NAME = 'Comp. Sci.'

select DISTINCT name
from student natural join takes natural join course --多此一举
where DEPT_NAME = 'Comp. Sci.'

-- b
SELECT DISTINCT ID,NAME FROM STUDENT JOIN TAKES using(ID) 
WHERE ID not in (SELECT ID FROM TAKES WHERE YEAR = 2009 and SEMESTER = 'Spring')

select id, name
from student 
MINUS -- Oracle ; 等同于 sql server 的 EXCEPT
select id, name from student natural join takes
where YEAR = 2009 and SEMESTER = 'Spring'

-- c
SELECT DEPT_NAME, MAX(SALARY) FROM INSTRUCTOR GROUP BY DEPT_NAME

-- d
WITH dept_salary as (SELECT DEPT_NAME, MAX(SALARY) as max_salary FROM INSTRUCTOR GROUP BY DEPT_NAME)
SELECT min(max_salary) FROM dept_salary

-- #3.12
-- a
INSERT into COURSE(COURSE_ID,TITLE,CREDITS) VALUES('CS-001','Weekly Seminar' ,0)

-- b
INSERT INTO SECTION(COURSE_ID,SEC_ID,SEMESTER,YEAR) VALUES('CS-001',1,'Fall',2009)

-- c
INSERT into TAKES(ID,COURSE_ID,SEC_ID,SEMESTER,YEAR) SELECT ID,'CS-001',1,'Fall',2009 FROM STUDENT WHERE DEPT_NAME = 'Comp. Sci.'

-- d
DELETE from TAKES WHERE ID = (SELECT ID FROM STUDENT WHERE NAME = 'Chavez') and COURSE_ID = 'CS-001'

-- e
DELETE FROM COURSE WHERE COURSE_ID = 'CS-001' 
--授课信息section和takes也会删除该课程段

-- true 要先删除takes和section 因为takes 外键引用 section ,而 section 外键引用course
delete from takes
where course_id = 'CS-001'
delete from section
where course_id = 'CS-001'
delete from course
where course_id = 'CS-001'
-- f
DELETE FROM TAKES WHERE COURSE_ID in (SELECT COURSE_ID FROM COURSE WHERE lower(TITLE) LIKE '%database%')

-- #3.13
create table person
	(driver_id  VARCHAR(50),
	 name       VARCHAR(50),
	 address    VARCHAR(50),
	 primary key (driver_id)
	);

create table car
	(license  VARCHAR(50),
	 model    VARCHAR(50),
	 year     INTEGER,
	 primary key (license)
	 );
	 
create table accident
	(report_number  INTEGER,
	 "date"           DATE,
	 location       VARCHAR(50),
	 primary key (report_number));
	 
create table owns
	(driver_id varchar(50),
	 license   varchar(50),
	 primary key (driver_id,license),
	 foreign key (driver_id) references person,
	 foreign key (license) references car
	 );
	 
create table participated
	(REPORT_NUMBER integer,
	 license       varchar(50),
	 driver_id     varchar(50),
	 damage_amount integer,
	 primary key (report_number,license),
	 foreign key (license) references car,
	 foreign key (report_number) references accident
   );
	 
-- 3.18

-- “null”表示未知值。
-- 当值不存在时，也使用“null”。

-- 3.19 <>all 等价于 not in


-- 3.22 不使用unique 重写
-- SELECT TITLE FROM COURSE where unique (SELECT title from COURSE) --缺失表达式
SELECT TITLE FROM COURSE where 1 <= (SELECT COUNT(title) from COURSE GROUP BY TITLE)
-- 参考答案
SELECT TITLE FROM COURSE where(
(select count(title)
from course) =
(select count (distinct title)
from course))

-- 3.23
select course_id, semester, year, sec_id, avg(TOT_CRED)
from takes natural join student
where year = 2009
group by course_id, semester, year, sec_id
having count(ID) >= 2;

select course_id, semester, year, sec_id, avg(TOT_CRED)
from (takes natural join student) NATURAL join SECTION
where year = 2009
group by course_id, semester, year, sec_id
having count(ID) >= 2;
--  take和section的公共属性构成了take的外键，并引用section。因此，每个元组最多只能匹配一个元组元组，并且任何组中都不会有任何额外的元组。 
--  此外，这些属性不能采用空值，因为它们是take的主键的一部分。 因此，from子句中的join部分不会导致任何组中的元组丢失。 所以结果没有变化。

-- 3.24 改写前
with dept_total (dept_name, value) as
(select dept_name, sum(salary)
from instructor
group by dept_name),
dept_total_avg(value) as
(select avg(value)
from dept_total)
select dept_name
from dept_total, dept_total_avg
where dept_total.value >= dept_total_avg.value;

-- 改写后
select dept_name
from (select dept_name, sum(salary) as value from instructor group by dept_name) dept_total , (select avg(value) as value 
from (select dept_name, sum(salary) as value from instructor group by dept_name)) dept_total_avg
where dept_total.value >= dept_total_avg.value;

```


# 4第四章中级SQL
## 4.1连接

### 4.1.1外连接-左、右、全-外连接
- 左外连接：保留左边的元组
- 右外连接：保留右边的元组
- 全外连接：保留两边的元组

## 4.2视图
### 4.2.1create view
```sql
create view v as <query expression>;
```
### 4.2.2物化视图
物化视图：如果用于定义视图的实际关系改变，视图也跟着修改。

## 4.3事务 
- commit work：提交当前事务
- rollback work：回滚当前事务
- 一旦执行了commit work，就不能用rollback work来撤销

## 4.4完整性约束
### not null
```sql
name varchar(20) not null,
```

### unique
```sql
unique(budget)
```
### check(P)
```SQL
check(budget>0),
check(semester in ('fall','winter','spring','summer'))
```

### 参照完整性

```sql
-- 可以是外码，也可以不是外码
dept_name varchar(20) references department；

-- 级联删除和级联更新
foreign key(dept_name) varchar(20) references department
	on delete cascade
	on update cascade
```

### 事务的检查延迟到结束时执行
```sql
set constraints constraint-list deferred
```

## 4.5数据类型与模式

### 日期和时间

```sql
date '2001-4-25'
time(0) '08:32:24'
timestamp(2) '2001-4-25 08:32:24.45'
-- 增加时区
time with timezone
-- 转换字符串为日期时间
cast e as t
-- 提取年，月，日，小时，分钟，秒,时区
-- year,month,day,hour,minute,second,timezone_hour,timezone_minute
extract(year from A)

-- 返回当前日期
current_date()
-- 返回当前时间(带时区)
current_time
-- 本地时间(不带时区)
localtime()
-- 时间戳
current_timestamp()
-- 时间加减
localtimestamp() + interval '1' day
```

### 默认值

```sql
tot numeric(3,0) default 0,
```

### 创建索引

```sql
-- 索引可以快速找到目标值，而不用读取整个关系
create index  studentID_index on student(ID);
```

### 大对象类型

- KB级，MB级，GB级

```sql
book_review clob (10KB)
image blob (10MB)
movie blob (2GB)
```

### 自定义的数据类型与域

- 独特类型
- 结构化数据类型：嵌套记录结构，数组，多重集的复杂数据类型

```sql
-- 独特类型
create type Dollars as numeric (12,2) final;
create type Pounds as numeric (12,2) final;

-- 定义域
create domain DDollars as numeric(12,2) not null;
-- check定义域
create domain YearlySalary numeric(8,2)
	constraint salary_value_test check(value >= 29000.00);
create domain degree_level varchar(10)
	constraint degree_test
    	check(value in ('Bachelors','Masters'))
```

- 类型与域的区别
  - 在域上可以声明约束或默认值，但是在用户定义类型上不能声明
  - 域不是强类型，可以被赋值另一个域类型，只要基本类型是相容的。

### 目录、模式与环境

```sql
-- 目录.模式.表
catalog5.univ_shema.course
-- 创建、删除模式
create schema
drop schema
```

## 4.6授权

对数据的授权包括：

- 读取数据-select权限
- 插入新数据-insert权限
- 更新数据-update权限
- 删除数据-delete权限

### 权限授权和收回

```sql
-- 授权Amit,Sato的department的查询权限
grant select on department to Amit,Sato;
-- 对元组的更新权限
grant update (budget) on department to Amit,Sato;
-- insert 也支持只开放部分属性插入，其他的为默认值或NULL
-- delete 删除元组
-- 收回权限，默认级联收回
revoke select on department to Amit,Sato;
-- 防止级联收回
revoke select on department to Amit,Sato restrict;

```

### 角色

```sql
-- 创建角色
create role instructor;
-- 对角色创建权限
grant select on takes to instructor;
-- 角色授予用户或其他角色
create role dean;
grant dean to Amit;
grant instructor to dean;
```

### 视图的授权

### 模式的授权references

```sql
-- 对于外码约束的权限
grant references(dept_name) on department to Mariano;
```

### 权限的转移with grant option

```sql
grant select on department to Amit with grant option;
```

## 4课后习题

# 第五章高级SQL
## 5.2函数和过程

### 声明和调用

- 表函数：支持返回关系作为结果的函数

```sql
-- 声明函数，返回int
create function dept_count(dept_name varchar(20))
	returns integer
	begin
	-- 声明变量
	declare d_count integer;
		select count(*) into d_count
		from instructor
		where instructor.dept_name=dept_name
	return d_count;
	end
	
-- 调用函数
select dept_name,budget
from department
where dept_count(dept_name)>12;

-- 声明函数，返回表
create function instructor_of(dept_name varchar(20))
	returns table(
    	ID varchar(5),
    	name varchar(20),
    	dept_name varchar(20),
    	salary numeric(8,2))
    return table
    	(select ID,name,dept_name,salary
        from instructor
        where instructor.dept_name = instructor_of.dept_name);
-- 调用
select *
from table(instructor_of('Finance'));

-- 过程
create procedure dept_count_proc(in dept_name varchar(20),out d_count integer)
	begin
		select count(*) into d_count
		from instructor
		where instructor.dept_name = dept_count_proc.dept_name
	end
-- 调用过程
-- ？？可以从一个SQL过程中或者嵌入式SQL中使用call语句调用过程：
declare d_count integer;
call dept_count_proc('Physics',d_count);
```

- 过程和函数都可以有相同的名字，但是过程需要参数个数不同，函数还可以是有一个参数类型不同。

### 支持过程和函数的语言构造

```sql
-- 循环while
while bool do
	...;
end while

-- 循环repeat
repeat
	...;
until bool
end repeat

-- for 可以对查询的所有结果进行执行
declare n integer default 0;
for r as 
		select budget from department
		where dept_name = 'Music'
do
	set n = n - r.budget
end for
-- 退出循环
leave
-- 跳过当前循环
iterate

-- if
if bool
	then ...
elseif bool
	then ...
else ...
end if
```

