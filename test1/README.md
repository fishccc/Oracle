# Oracle

## 教材查询语句
查询一：
```SQL
SELECT d.department_name，count(e.job_id)as "部门总人数"，
avg(e.salary)as "平均工资"
from hr.departments d，hr.employees e
where d.department_id = e.department_id
and d.department_name in ('IT'，'Sales')
GROUP BY department_name;
```
运行结果：

![result](https://github.com/fishccc/Oracle/blob/master/test1/1.png)

分析结果：

![result](https://github.com/fishccc/Oracle/blob/master/test1/1-1.png)

查询二：
```SQL
SELECT d.department_name，count(e.job_id)as "部门总人数"，
avg(e.salary)as "平均工资"
FROM hr.departments d，hr.employees e
WHERE d.department_id = e.department_id
GROUP BY department_name
HAVING d.department_name in ('IT'，'Sales');
```

运行结果：

![result](https://github.com/fishccc/Oracle/blob/master/test1/2.png)

分析结果：

![result](https://github.com/fishccc/Oracle/blob/master/test1/2-2.png)

## 自己的查询语句
查询语句：
```SQL

```
运行结果：

分析结果：
