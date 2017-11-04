Write a SQL query to find all numbers that appear at least three times consecutively.

```bash
+----+-----+
| Id | Num |
+----+-----+
| 1  |  1  |
| 2  |  1  |
| 3  |  1  |
| 4  |  2  |
| 5  |  1  |
| 6  |  2  |
| 7  |  2  |
+----+-----+
```

For example, given the above `Logs` table, 1 is the only number that appears consecutively for at least three times.

```bash
+-----------------+
| ConsecutiveNums |
+-----------------+
| 1               |
+-----------------+
```

**解决方式1**
```sql
select DISTINCT num as ConsecutiveNums FROM
(select num,
	case 
		when @record = num then @count:=@count+1
		when @record <> @record:=num then @count:=1 end as n
    from 
	    Logs ,(select @count:=0,@record:=(SELECT num from Logs limit 0,1)) r
) a
where a.n>=3
```
