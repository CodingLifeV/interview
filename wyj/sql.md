# Sql 语句

<!-- TOC -->

- [Sql 语句](#sql-语句)
  - [一、单表操作](#一单表操作)
    - [1. 查找最晚入职员工的所有信息](#1-查找最晚入职员工的所有信息)
    - [2.查找入职员工时间排名倒数第三的员工所有信息](#2查找入职员工时间排名倒数第三的员工所有信息)
    - [3. 查找薪水涨幅超过 15 次的员工号 emp_no 以及其对应的涨幅次数 t](#3-查找薪水涨幅超过-15-次的员工号-emp_no-以及其对应的涨幅次数-t)
  - [二、多表操作](#二多表操作)
    - [1. 查找各个部门当前(to_date='9999-01-01')领导当前薪水详情以及其对应部门编号](#1-查找各个部门当前to_date9999-01-01领导当前薪水详情以及其对应部门编号)
    - [2. 查找所有已经分配部门的员工的 last_name 和 first_name](#2-查找所有已经分配部门的员工的-last_name-和-first_name)
    - [3. 查找所有员工的 last_name 和 first_name 以及对应部门编号 dept_no，也包括展示没有分配具体部门的员工](#3-查找所有员工的-last_name-和-first_name-以及对应部门编号-dept_no也包括展示没有分配具体部门的员工)
    - [4. 查找所有员工入职时候的薪水情况，给出 emp_no 以及 salary， 并按照 emp_no 进行逆序](#4-查找所有员工入职时候的薪水情况给出-emp_no-以及-salary-并按照-emp_no-进行逆序)

<!-- /TOC -->

[SQL 教程](http://www.w3school.com.cn/sql/index.asp)

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
`limit n`：从第 0 条开始，取 n 条数据，是 limit(0,n)的缩写。

```sql
select * from employees
where hire_date = (
    select distinct hire_date order by hire_date desc limit 2,1
)
```

### 3. 查找薪水涨幅超过 15 次的员工号 emp_no 以及其对应的涨幅次数 t

`count(*)`：返回表中的记录数

`count(column_name)`：返回指定列的值的数目（NULL 不计入）

`having`：增加 `having` 子句原因是，`where` 关键字无法与合计函数一起使用

`group by`：结合合计函数，根据一个或多个列对结果集进行分组。合计函数例如`count`，`sum`，`avg`，`max`，`min`等

```sql
select emp_no, count(emp_no) as t
from salaries
group by emp_no
having t > 15
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

### 2. 查找所有已经分配部门的员工的 last_name 和 first_name

`inner join`：在表中存在至少一个匹配时，INNER JOIN 关键字返回行。

```sql
select e.last_name, e.first_name, d.dept_no
from dept_emp d inner join employees e
on d.emp_no = e.emp_no
```

### 3. 查找所有员工的 last_name 和 first_name 以及对应部门编号 dept_no，也包括展示没有分配具体部门的员工

`left join`：从左表那里返回所有的行，即使在右表中没有匹配的行。

```sql
select e.last_name, e.first_name, d.dept_no
from employees e
left join dept_emp d
on e.emp_no = d.emp_no
```

### 4. 查找所有员工入职时候的薪水情况，给出 emp_no 以及 salary， 并按照 emp_no 进行逆序

salaries.emp_no 不唯一（因为号码为 emp_no 的员工会有多次涨薪的可能,注意到 salaries.from_date 和 employees.hire_date 的值应该要相等

```sql
select e.emp_no, s.salary
from employees e
inner join salaries s
on e.emp_no = s.emp_no
and e.hire_date = s.from_date
order by s.emp_no desc
```
