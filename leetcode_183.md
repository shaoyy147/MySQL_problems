# 问题
Suppose that a website contains two tables, the Customers table and the Orders table. Write a SQL query to find all customers who never order anything.

Table: Customers.

+----+-------+
| Id | Name  |
+----+-------+
| 1  | Joe   |
| 2  | Henry |
| 3  | Sam   |
| 4  | Max   |
+----+-------+
Table: Orders.

+----+------------+
| Id | CustomerId |
+----+------------+
| 1  | 3          |
| 2  | 1          |
+----+------------+
Using the above tables as example, return the following:

+-----------+
| Customers |
+-----------+
| Henry     |
| Max       |
+-----------+

# 解答
```MySQL
SELECT Customers.Name AS 'Customers' FROM Customers LEFT JOIN Orders ON Customers.Id = Orders.CustomerId WHERE isnull(Orders.CustomerId)=1;

或者
select customers.name as 'Customers'
from customers
where customers.id not in
(
    select customerid from orders
);
```

# 备注
isnull函数，与ON WHERE子句的理解；子表+not in函数。