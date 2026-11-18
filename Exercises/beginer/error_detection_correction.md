# SQL Error Detection & Correction Assessment 

Each question contains an incorrect SQL query.

Your tasks:

1. Read the SQL query carefully.
2. Decide whether the query is correct or incorrect.
3. Identify the error.
4. Rewrite the query correctly.
5. Explain briefly why the original query was incorrect.


# Part Is query correct, if not correct it (30 Minutes)

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
