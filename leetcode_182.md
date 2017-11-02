# 问题
Write a SQL query to find all duplicate emails in a table named Person.

+----+---------+
| Id | Email   |
+----+---------+
| 1  | a@b.com |
| 2  | c@d.com |
| 3  | a@b.com |
+----+---------+
For example, your query should return the following for the above table:

+---------+
| Email   |
+---------+
| a@b.com |
+---------+
Note: All emails are in lowercase.

# 解答
```MySQL
select Email
from Person
group by Email
having count(Email) > 1;

#或者
SELECT DISTINCT Person1.Email AS Email FROM Person AS Person1 CROSS JOIN Person AS Person2 ON Person1.Email = Person2.Email AND Person1.Id != Person2.Id;
```

# 备注
DISTINCT 字段，JOIN ON

GROUP BY计数用法