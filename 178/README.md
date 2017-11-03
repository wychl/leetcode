## Rank Scores

Write a SQL query to rank scores. If there is a tie between two scores, both should have the same ranking. Note that after a tie, the next 

ranking number should be the next consecutive integer value. In other words, there should be no "holes" between ranks.

```bash
+----+-------+
| Id | Score |
+----+-------+
| 1  | 3.50  |
| 2  | 3.65  |
| 3  | 4.00  |
| 4  | 3.85  |
| 5  | 4.00  |
| 6  | 3.65  |
+----+-------+
```

For example, given the above Scores table, your query should generate the following report (order by highest score):

```bash
+-------+------+
| Score | Rank |
+-------+------+
| 4.00  | 1    |
| 4.00  | 1    |
| 3.85  | 2    |
| 3.65  | 3    |
| 3.65  | 3    |
| 3.50  | 4    |
+-------+------+
```

## solution1 
```sql
select s1.Score as Score, count(s2.Score) as Rank from Scores as s1 left join (select distinct Score from Scores) as s2 on s1.Score <= s2.Score group by s1.id order by s1.Score desc;

```

## reference

http://blog.csdn.net/wzy_1988/article/details/45173277