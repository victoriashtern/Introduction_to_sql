
**Duration:** 3 Hours  
**Total Marks:** 100  
**Level:** Intermediate

## Exam Objectives

Evaluate practical MySQL skills, including:

- SQL queries
- JOIN operations
- INSERT, UPDATE, DELETE
- WHERE and ORDER BY
- GROUP BY and HAVING
- Aggregate functions
- Subqueries
- Database creation and management
- Transactions

---

## Section 1 – SQL Fundamentals (15 Marks)

1. Write a query to display all employees whose salary is greater than 5,000.
2. Write a query to retrieve employees whose names start with the letter 'A'.
3. Display employees hired between January 1, 2023, and December 31, 2024.
4. Write a query to display the five employees with the highest salaries.
5. Find employees whose department_id is NULL.
6. Write a query using DISTINCT to display all unique department IDs.
7. Find the total, minimum, maximum, and average employee salary.

## Section 2 – INSERT, UPDATE and DELETE (20 Marks)

8. Write an INSERT statement to add a new employee with the following details:
   - Employee ID: 101
   - Name: John Smith
   - Salary: 6500
   - Department ID: 2

9. Insert three employees into the employees table using a single INSERT statement.

10. Update the salary of employee ID 101 to 7500.

11. Increase the salary of all employees in department ID 2 by 10%.

12. Delete the employee whose ID is 101.

13. Delete all employees whose salary is below 3000.

14. Explain the difference between DELETE, TRUNCATE, and DROP.

15. Write a query to delete employees who do not belong to any department. Consider how foreign-key constraints may affect the operation.

## Section 3 – JOIN Tables (25 Marks)

Assume the following tables:

### Employees

- employee_id
- employee_name
- salary
- department_id
- manager_id

### Departments

- department_id
- department_name
- location_id

### Locations

- location_id
- city
- country

16. Write an INNER JOIN query to display employee names and their department names.

17. Write a LEFT JOIN query to display all employees, including those who are not assigned to a department.

18. Write a RIGHT JOIN query to display all departments and their employees, including departments without employees.

19. Write a query to display employee names, department names, and city names by joining all three tables.

20. Find departments that do not have any employees.

21. Write a SELF JOIN query to display each employee's name and their manager's name.

22. Explain the difference between INNER JOIN, LEFT JOIN, RIGHT JOIN, and CROSS JOIN.

23. Write a query to find employees working in the same department as employee ID 105.

## Section 4 – GROUP BY, HAVING and Aggregate Functions (15 Marks)

24. Find the total number of employees in each department.

25. Display the average salary for each department.

26. Find departments where the average salary is greater than 5000.

27. Find the department with the highest total salary expenditure.

28. Count how many employees earn more than 6000 in each department.

29. Explain the difference between WHERE and HAVING with examples.

## Section 5 – Subqueries and Advanced SQL (15 Marks)

30. Find employees whose salary is greater than the company's average salary.

31. Find the second-highest salary in the employees table.

32. Find employees who earn more than their department's average salary.

33. Write a query using EXISTS to find departments that have at least one employee.

34. Find employees who work in the same department as the employee named 'John Smith'.

35. Explain the difference between a subquery and a JOIN.

## Section 6 – Practical Database Challenges (10 Marks)

36. Create a database named company_db.

37. Create the employees and departments tables with appropriate primary keys and foreign keys.

38. Insert at least five departments and ten employees.

39. Write a query to display the department with the highest-paid employee.

40. Write a transaction that updates an employee's salary and demonstrates COMMIT and ROLLBACK.

---

## Suggested 3-Hour Examination Schedule

| Section | Topic | Time |
|---|---|---:|
| 1 | SQL Fundamentals | 25 min |
| 2 | INSERT, UPDATE, DELETE | 30 min |
| 3 | JOIN Operations | 45 min |
| 4 | GROUP BY and HAVING | 25 min |
| 5 | Subqueries | 25 min |
| 6 | Practical Challenges | 30 min |
| **Total** | | **180 min** |

## Examination Instructions

- Write executable MySQL queries.
- Use appropriate aliases for tables and columns.
- Apply correct JOIN conditions.
- Avoid unnecessary duplicate records.
- Pay attention to primary keys and foreign-key constraints.
- Explain your logic wherever requested.
- Execute your queries using MySQL Workbench or MySQL Server.

---

**End of Examination**
```
