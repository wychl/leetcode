##  Duplicate Emails

Write a SQL query to find all duplicate emails in a table named Person.

```bash
+----+---------+
| Id | Email   |
+----+---------+
| 1  | a@b.com |
| 2  | c@d.com |
| 3  | a@b.com |
+----+---------+
```

For example, your query should return the following for the above table:

```bash
+---------+
| Email   |
+---------+
| a@b.com |
+---------+
```

**解决方式1**
```sql
SELECT 
    Email
FROM
    Person
GROUP BY Email
HAVING COUNT(*) > 1
```