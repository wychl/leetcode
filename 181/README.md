The Employee table holds all employees including their managers. Every employee has an Id, and there is also a column for the manager Id.

```bash
+----+-------+--------+-----------+
| Id | Name  | Salary | ManagerId |
+----+-------+--------+-----------+
| 1  | Joe   | 70000  | 3         |
| 2  | Henry | 80000  | 4         |
| 3  | Sam   | 60000  | NULL      |
| 4  | Max   | 90000  | NULL      |
+----+-------+--------+-----------+
```

Given the Employee table, write a SQL query that finds out employees who earn more than their managers. For 

the above table, Joe is the only employee who earns more than his manager.

```bash
+----------+
| Employee |
+----------+
| Joe      |
+----------+
```

**解决方式1**

```sql
SELECT 
    Name AS Employee
FROM
    Employee e1
WHERE
    Salary > (SELECT 
            Salary
        FROM
            Employee e2
        WHERE
            e2.id = e1.ManagerId)
```

**解决方式2**
```sql
SELECT 
    E1.Name AS Employee
FROM
    Employee AS E1,
    Employee AS E2
WHERE
    E1.ManagerId = E2.Id
        AND E1.Salary > E2.Salary
```