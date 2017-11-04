##  Department Highest Salary
The Employee table holds all employees. Every employee has an Id, a salary, and there is also a column for the department Id.


```bash
+----+-------+--------+--------------+
| Id | Name  | Salary | DepartmentId |
+----+-------+--------+--------------+
| 1  | Joe   | 70000  | 1            |
| 2  | Henry | 80000  | 2            |
| 3  | Sam   | 60000  | 2            |
| 4  | Max   | 90000  | 1            |
+----+-------+--------+--------------+
```

The Department table holds all departments of the company.


```bash
+----+----------+
| Id | Name     |
+----+----------+
| 1  | IT       |
| 2  | Sales    |
+----+----------+
```

Write a SQL query to find employees who have the highest salary in each of the departments. For the above 

tables, Max has the highest salary in the IT department and Henry has the highest salary in the Sales 

department.

```bash
+------------+----------+--------+
| Department | Employee | Salary |
+------------+----------+--------+
| IT         | Max      | 90000  |
| Sales      | Henry    | 80000  |
+------------+----------+--------+
```

**解决方式1**

```sql
SELECT 
    d.Name AS Department, e.Name AS Employee, e.Salary
FROM
    Employee e,
    Department d
WHERE
    e.DepartmentId = d.id
        AND e.Salary = (SELECT 
            MAX(Salary)
        FROM
            Employee e2
        WHERE
            e2.DepartmentId = d.id)
```