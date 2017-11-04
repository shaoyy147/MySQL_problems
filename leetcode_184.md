# 问题
The Employee table holds all employees. Every employee has an Id, a salary, and there is also a column for the department Id.

+----+-------+--------+--------------+
| Id | Name  | Salary | DepartmentId |
+----+-------+--------+--------------+
| 1  | Joe   | 70000  | 1            |
| 2  | Henry | 80000  | 2            |
| 3  | Sam   | 60000  | 2            |
| 4  | Max   | 90000  | 1            |
+----+-------+--------+--------------+
The Department table holds all departments of the company.

+----+----------+
| Id | Name     |
+----+----------+
| 1  | IT       |
| 2  | Sales    |
+----+----------+
Write a SQL query to find employees who have the highest salary in each of the departments. For the above tables, Max has the highest salary in the IT department and Henry has the highest salary in the Sales department.

+------------+----------+--------+
| Department | Employee | Salary |
+------------+----------+--------+
| IT         | Max      | 90000  |
| Sales      | Henry    | 80000  |
+------------+----------+--------+

# 解答
```MySQL
SELECT d.Name as Department, e.Name as Employee, Salary FROM Employee as e JOIN Department as d ON e.DepartmentId = d.Id 
WHERE (e.DepartmentID, Salary) in 
(SELECT DepartmentID , max(Salary) FROM Employee GROUP BY DepartmentID)
ORDER BY Salary DESC;
```

# 备注
分组寻找:两个变量的in，组名与极值的匹配。找极值数据，靠匹配。注意group显示的个例与极值找到的个例不一定是同一个数据，只有分组名是肯定的。