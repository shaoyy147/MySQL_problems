# 问题
Given a Weather table, write a SQL query to find all dates' Ids with higher temperature compared to its previous (yesterday's) dates.

+---------+------------+------------------+
| Id(INT) | Date(DATE) | Temperature(INT) |
+---------+------------+------------------+
|       1 | 2015-01-01 |               10 |
|       2 | 2015-01-02 |               25 |
|       3 | 2015-01-03 |               20 |
|       4 | 2015-01-04 |               30 |
+---------+------------+------------------+
For example, return the following Ids for the above Weather table:
+----+
| Id |
+----+
|  2 |
|  4 |
+----+

# 解答
```MySQL
SELECT a.Id FROM Weather AS a, Weather AS b WHERE DATEDIFF(a.Date,b.Date)= 1 AND a.Temperature > b.Temperature;
```

# 备注
DATEDIFF()函数返回天