## Department Top Three Salaries
The Employee table holds all employees. Every employee has an Id, and there is also a column for the department Id.


```bash
+----+-------+--------+--------------+
| Id | Name  | Salary | DepartmentId |
+----+-------+--------+--------------+
| 1  | Joe   | 70000  | 1            |
| 2  | Henry | 80000  | 2            |
| 3  | Sam   | 60000  | 2            |
| 4  | Max   | 90000  | 1            |
| 5  | Janet | 69000  | 1            |
| 6  | Randy | 85000  | 1            |
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
Write a SQL query to find employees who earn the top three salaries in each of the department. For the above

tables, your SQL query should return the following rows.

```bash
+------------+----------+--------+
| Department | Employee | Salary |
+------------+----------+--------+
| IT         | Max      | 90000  |
| IT         | Randy    | 85000  |
| IT         | Joe      | 70000  |
| Sales      | Henry    | 80000  |
| Sales      | Sam      | 60000  |
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
        AND 3 > (SELECT 
            COUNT(DISTINCT (e2.Salary))
        FROM
            Employee e2
        WHERE
            e2.DepartmentId = d.id
                AND e2.Salary > e.Salary)
```
