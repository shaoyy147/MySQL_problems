# 问题
Write a SQL query to find all numbers that appear at least three times consecutively.

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
For example, given the above Logs table, 1 is the only number that appears consecutively for at least three times.

+-----------------+
| ConsecutiveNums |
+-----------------+
| 1               |
+-----------------+

# 解答
```MySQL
SELECT DISTINCT a1.Num as ConsecutiveNums FROM Logs a1, Logs a2, Logs a3 WHERE a1.Id = a2.Id - 1 AND a2.id = a3.id -1 AND a1.num = a2.num
 AND a2.num = a3.num;
```

# 备注
自表元素比较。