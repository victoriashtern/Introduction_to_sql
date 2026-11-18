# SQL Error Detection & Correction Assessment 

Each question contains an incorrect SQL query.

Your tasks:

1. Read the SQL query carefully.
2. Decide whether the query is correct or incorrect.
3. Identify the error.
4. Rewrite the query correctly.
5. Explain briefly why the original query was incorrect.

# Database
## Table 1: Customers

| customer\_id | customer\_name | city | age |
| --- | --- | --- | --- |
| 1 | John | Toronto | 25 |
| 2 | Sarah | Vancouver | 32 |
| 3 | Mike | Toronto | 28 |
| 4 | Emma | Calgary | 35 |
| 5 | David | Montreal | 22 |
| 6 | Lisa | Vancouver | 29 |
| 7 | James | Ottawa | 40 |
| 8 | Anna | Toronto | 31 |

## Table 2: Products

| product\_id | product\_name | category | price |
| --- | --- | --- | --- |
| 101 | Laptop | Electronics | 1200 |
| 102 | Mouse | Electronics | 25 |
| 103 | Chair | Furniture | 150 |
| 104 | Desk | Furniture | 300 |
| 105 | Phone | Electronics | 800 |
| 106 | Notebook | Stationery | 5 |
| 107 | Pen | Stationery | 2 |
| 108 | Monitor | Electronics | 350 |

## Table 3: Orders

| order\_id | customer\_id | order\_date | total\_amount |
| --- | --- | --- | --- |
| 1001 | 1 | 2025-01-10 | 1225 |
| 1002 | 2 | 2025-01-12 | 800 |
| 1003 | 3 | 2025-02-05 | 150 |
| 1004 | 1 | 2025-02-15 | 350 |
| 1005 | 4 | 2025-03-01 | 300 |
| 1006 | 5 | 2025-03-10 | 25 |
| 1007 | 6 | 2025-03-15 | 1200 |
| 1008 | 2 | 2025-04-01 | 350 |
| 1009 | 8 | 2025-04-05 | 800 |
| 1010 | 3 | 2025-04-10 | 500 |

## Table 4: Order\_Items

| item\_id | order\_id | product\_id | quantity |
| --- | --- | --- | --- |
| 1 | 1001 | 101 | 1 |
| 2 | 1001 | 102 | 1 |
| 3 | 1002 | 105 | 1 |
| 4 | 1003 | 103 | 1 |
| 5 | 1004 | 108 | 1 |
| 6 | 1005 | 104 | 1 |
| 7 | 1006 | 102 | 1 |
| 8 | 1007 | 101 | 1 |
| 9 | 1008 | 108 | 1 |
| 10 | 1009 | 105 | 1 |
| 11 | 1010 | 104 | 1 |
| 12 | 1010 | 108 | 1 |

## Database Relationships

| Parent Table | Primary Key | Child Table | Foreign Key |
| --- | --- | --- | --- |
| Customers | customer\_id | Orders | customer\_id |
| Orders | order\_id | Order\_Items | order\_id |
| Products | product\_id | Order\_Items | product\_id |

![DataBases](/img/sales_db.jpg)



# Is query correct, if not correct it (30 Minutes)

**Topics:** SELECT, WHERE, ORDER BY, DISTINCT, LIKE, LIMIT

### 1: Display All Customers

```sql
SELECT customer_name, age FROM Orders;
```

### 2: Display Customer Names and Cities


```sql
SELECT customer_name AND city FROM Customers;
```

### 3: Find Customers from Toronto

```sql
SELECT * FROM Customers WHERE city = 'Vancouver';
```

### 4: Find Customers Older Than 30

```sql
SELECT * FROM Customers WHERE age < 30;
```

### 5: Find Products Costing More Than $100

```sql
SELECT product_name, price FROM Products WHERE price = 100;
```

### 6: Sort Products by Price

```sql
SELECT * FROM Products ORDER BY price ASC;
```

### Question 7: Find Unique Cities

**Incorrect Query:**

sql

```sql
SELECT city FROM Customers;
```

### 8: Find the Five Most Expensive Products


```sql
SELECT * FROM Products ORDER BY price ASC LIMIT 5;
```

### 9: Find Customers Whose Names Start with A

```sql
SELECT * FROM Customers WHERE customer_name LIKE '%A';
```


### 10: Find Electronics Products

```sql
SELECT * FROM Products WHERE category = 'Furniture';
```

# Part B: Intermediate SQL (40 Minutes)

**Topics:** COUNT, SUM, AVG, MIN, MAX, GROUP BY, HAVING, CASE

### 11: Count Total Customers


```sql
SELECT SUM(customer_id)
FROM Customers;
```

### 12: Calculate Average Customer Age

```sql
SELECT SUM(age) FROM Customers;
```

### 13: Find Maximum and Minimum Product Prices

```sql
SELECT MAX(price), AVG(price) FROM Products;
```


### 14: Calculate Total Revenue

```sql
SELECT AVG(total_amount) FROM Orders;
```

### 15: Count Customers in Each City

```sql
SELECT city, COUNT(customer_id) FROM Customers;
```

### 16: Average Product Price by Category

```sql
SELECT category, SUM(price) FROM Products GROUP BY product_id;
```

### 17: Categories with Average Price Greater Than $100

```sql
SELECT category, AVG(price) FROM Products WHERE AVG(price) > 100 GROUP BY category;
```

### 18: Count Orders for Each Customer

```sql
SELECT customer_id, SUM(order_id) FROM Orders GROUP BY order_id;
```

### 19: Total Order Amount for Each Customer

```sql
SELECT customer_id, COUNT(total_amount) FROM Orders GROUP BY customer_id;
```

### 20: Classify Products Using CASE

```sql
SELECT product_name,
       price,
       CASE
           WHEN price >= 500 THEN 'Cheap'
           WHEN price >= 100 THEN 'Expensive'
           ELSE 'Moderate'
       END AS price_category
FROM Products;
```


You can copy the document into a file named `SQL_Error_Detection_Assessment.md`.
