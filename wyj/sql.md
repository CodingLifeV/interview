# Sql语句
<!-- TOC -->

- [Sql语句](#sql语句)
    - [一、单表操作](#一单表操作)
        - [1. 查找最晚入职员工的所有信息](#1-查找最晚入职员工的所有信息)
        - [2.查找入职员工时间排名倒数第三的员工所有信息](#2查找入职员工时间排名倒数第三的员工所有信息)
    - [二、多表操作](#二多表操作)
        - [1. 查找各个部门当前(to_date='9999-01-01')领导当前薪水详情以及其对应部门编号](#1-查找各个部门当前to_date9999-01-01领导当前薪水详情以及其对应部门编号)
        - [2. 查找所有已经分配部门的员工的last_name和first_name](#2-查找所有已经分配部门的员工的last_name和first_name)

<!-- /TOC -->
[SQL教程](http://www.w3school.com.cn/sql/index.asp)

## 一、单表操作
### 1. 查找最晚入职员工的所有信息

```sql
select * from employees  
where hire_date =  
(select max(hire_date) from employees)
```

### 2.查找入职员工时间排名倒数第三的员工所有信息

[`select distinct`](http://www.w3school.com.cn/sql/sql_distinct.asp)：返回唯一不同的值

`order by`：默认根据指定的列对结果集进行升序排序，降序可使用 `desc` 关键字

`limit m,n`：从第 m+1 条开始，取 n 条数据；
`limit n`：从第 0 条开始，取 n 条数据，是limit(0,n)的缩写。

```sql
select * from employees  
where hire_date = (  
    select distinct hire_date order by hire_date desc limit 2,1  
)
```


## 二、多表操作

### 1. 查找各个部门当前(to_date='9999-01-01')领导当前薪水详情以及其对应部门编号

```sql
select s.*, d.dept_no
from salaries s, dept_manager d
where s.to_date = '9999-01-01' 
AND d.to_date = '9999-01-01'  
AND s.emp_no = d.emp_no
```
`join`：如果表中有至少一个匹配，则返回行

```sql
select s.*, d.dept_no
from salaries s /*inner*/ join dept_manager d on s.emp_no = d.emp_no
where s.to_date = '9999-01-01' 
  AND d.to_date = '9999-01-01'
```

### 2. 查找所有已经分配部门的员工的last_name和first_name

`inner join`：在表中存在至少一个匹配时，INNER JOIN 关键字返回行。

```sql
select e.last_name, e.first_name, d.dept_no 
from dept_emp d inner join employees e  
on d.emp_no = e.emp_no
```

