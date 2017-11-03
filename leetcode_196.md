# 问题
Write a SQL query to delete all duplicate email entries in a table named Person, keeping only unique emails based on its smallest Id.

+----+------------------+
| Id | Email            |
+----+------------------+
| 1  | john@example.com |
| 2  | bob@example.com  |
| 3  | john@example.com |
+----+------------------+
Id is the primary key column for this table.
For example, after running your query, the above Person table should have the following rows:

+----+------------------+
| Id | Email            |
+----+------------------+
| 1  | john@example.com |
| 2  | bob@example.com  |
+----+------------------+

# 解答
```MySQL
DELETE FROM Person WHERE Person.Id in (SELECT distinct a.Id FROM (SELECT * FROM person) as a, (SELECT * FROM person) as b WHERE a.id> b.id AND a.Email = b.Email);

或者
DELETE p1 FROM Person p1,
    Person p2
WHERE
    p1.Email = p2.Email AND p1.Id > p2.Id
```

# 备注
更新与选中不能同时进行！DELETE的进一步用法。