I suggest creating a hands-on MySQL laboratory exercise that gradually takes students from basic SQL operations to intermediate database management concepts.

For post-secondary students, the exercise should emphasize practical problem-solving rather than simply memorizing SQL commands. Students should design a database, create relationships, insert data, retrieve information, modify records, and work with transactions.

Below is a complete classroom-ready exercise that you can use as a lab assignment.

# MySQL Database Laboratory

## From Beginner to Intermediate

Beginner–IntermediatePost-secondaryHands-on SQL

A Visual Query Builder for PostgreSQL

[dbschema.com](<https://dbschema.com/blog/postgresql/a-visual-query-builder-for-postgresql/?utm_source=chatgpt.com>)

Estimated duration

3–4 hours

Suggested weighting

100 points

Database system

MySQL 8.x

Environment

MySQL Workbench

# MySQL Practical Exercise: Student Course Management System

Writing

# MySQL Practical Exercise

## Student Course Management System

### 1\. Introduction

In this practical exercise, you will design and implement a relational database for a college or university student course management system.

The system will store information about students, instructors, courses, and student course registrations.

You will apply SQL concepts to create database structures, insert and manipulate records, retrieve information, establish relationships, and manage transactions.

The exercise is divided into progressive sections, starting with fundamental SQL commands and moving toward intermediate database operations.

### 2\. Learning Objectives

By completing this exercise, you should be able to:

- Create and manage a MySQL database.
- Identify and select appropriate MySQL data types.
- Create tables using SQL DDL commands.
- Define primary keys and foreign keys.
- Insert, update, and delete records using DML commands.
- Retrieve information using SELECT statements.
- Filter and sort query results.
- Use aggregate functions and GROUP BY.
- Retrieve data from multiple tables using JOIN operations.
- Create and use database views.
- Manage transactions using COMMIT and ROLLBACK.
- Apply basic database design principles.

### 3\. Scenario

A post-secondary institution wants to develop a database to manage its student course registration system.

The database must maintain information about:

- Students enrolled at the institution.
- Instructors responsible for teaching courses.
- Courses offered by different departments.
- Student registrations for individual courses.

Each student can register for multiple courses, and each course can have multiple students.

An instructor can teach multiple courses, but each course is assigned to one instructor.

Your task is to design and implement the database using MySQL.

---

## Part 1: Database Creation (10 Points)

### Task 1.1 – Create a Database

Create a database named:

`college_db`

Write the SQL statement to:

1. Create the database.
2. Display all available databases.
3. Select `college_db` as the active database.

### Task 1.2 – Create the Database Tables

Create the following four tables.

**Table 1: students**

| Column | Data Type | Constraints |
| --- | --- | --- |
| student\_id | INT | Primary Key, Auto Increment |
| first\_name | VARCHAR(50) | NOT NULL |
| last\_name | VARCHAR(50) | NOT NULL |
| email | VARCHAR(100) | UNIQUE |
| date\_of\_birth | DATE |  |
| enrollment\_date | DATE |  |

**Table 2: instructors**

| Column | Data Type | Constraints |
| --- | --- | --- |
| instructor\_id | INT | Primary Key, Auto Increment |
| first\_name | VARCHAR(50) | NOT NULL |
| last\_name | VARCHAR(50) | NOT NULL |
| email | VARCHAR(100) | UNIQUE |
| department | VARCHAR(100) |  |

**Table 3: courses**

| Column | Data Type | Constraints |
| --- | --- | --- |
| course\_id | INT | Primary Key, Auto Increment |
| course\_name | VARCHAR(100) | NOT NULL |
| course\_code | VARCHAR(20) | UNIQUE |
| credits | TINYINT UNSIGNED | NOT NULL |
| instructor\_id | INT | Foreign Key |

**Table 4: registrations**

| Column | Data Type | Constraints |
| --- | --- | --- |
| registration\_id | INT | Primary Key, Auto Increment |
| student\_id | INT | Foreign Key |
| course\_id | INT | Foreign Key |
| registration\_date | DATE | NOT NULL |
| grade | DECIMAL(5,2) | NULL allowed |

**Requirements:**

- Use appropriate primary keys.
- Establish foreign key relationships.
- Ensure that student and instructor email addresses are unique.
- Use InnoDB as the storage engine.
- Prevent a student from registering for the same course more than once by using an appropriate UNIQUE constraint.

---

## Part 2: Insert Data (10 Points)

### Task 2.1 – Insert Students

Insert at least five students into the `students` table.

Use the following sample information:

| First Name | Last Name | Email | Date of Birth | Enrollment Date |
| --- | --- | --- | --- | --- |
| John | Smith | john@college.edu | 2002-04-15 | 2025-09-01 |
| Sarah | Johnson | sarah@college.edu | 2003-07-22 | 2025-09-01 |
| Michael | Brown | michael@college.edu | 2001-11-10 | 2025-09-01 |
| Emily | Davis | emily@college.edu | 2002-02-18 | 2025-09-01 |
| David | Wilson | david@college.edu | 2003-05-30 | 2025-09-01 |

### Task 2.2 – Insert Instructors

Insert at least three instructors.

| First Name | Last Name | Email | Department |
| --- | --- | --- | --- |
| Robert | Taylor | robert@college.edu | Computer Science |
| Jennifer | Anderson | jennifer@college.edu | Mathematics |
| William | Thomas | william@college.edu | Information Technology |

### Task 2.3 – Insert Courses

Insert at least five courses.

| Course Name | Course Code | Credits | Instructor |
| --- | --- | --- | --- |
| Database Management | DB101 | 3 | Robert Taylor |
| Programming Fundamentals | CS101 | 4 | Robert Taylor |
| Mathematics I | MATH101 | 3 | Jennifer Anderson |
| Web Development | WEB101 | 3 | William Thomas |
| Network Fundamentals | NET101 | 4 | William Thomas |

### Task 2.4 – Insert Registrations

Register students in different courses.

Create at least ten registration records.

Some students should be registered in multiple courses, and some courses should have multiple students.

Leave the grade column NULL for some registrations.

---

## Part 3: Basic SQL Queries (10 Points)

Use SELECT statements to retrieve information from your database.

Write SQL queries to:

1. Display all students.
2. Display all instructors.
3. Display all available courses.
4. Display only the first and last names of students.
5. Display students whose first name is John.
6. Display students enrolled after January 1, 2025.
7. Display courses worth three credits.
8. Display students whose last name starts with the letter S.
9. Display all courses ordered alphabetically by course name.
10. Display the five most recent registrations.

---

## Part 4: Data Manipulation (10 Points)

Practice modifying existing database records.

Write SQL statements to:

1. Change John's email address to `john.smith@college.edu`.
2. Change the number of credits for WEB101 to 4.
3. Update Sarah's date of birth.
4. Assign a grade of 85.50 to one registration.
5. Delete a registration record using its registration ID.
6. Insert a new student into the database.
7. Insert a new course into the courses table.

**Important:** Before executing UPDATE or DELETE statements, use SELECT to identify the records that will be affected.

---

## Part 5: Aggregate Functions and Grouping (10 Points)

Use SQL aggregate functions to summarize database information.

Write queries to:

1. Count the total number of students.
2. Count the total number of instructors.
3. Count the total number of courses.
4. Calculate the average number of credits across all courses.
5. Find the highest grade assigned.
6. Find the lowest grade assigned.
7. Count the number of students registered in each course.
8. Calculate the average grade for each course.
9. Display the total number of courses taught by each instructor.
10. Display only courses with more than two registered students.

**Hint:** Explore the following SQL functions and clauses:

- COUNT()
- AVG()
- MAX()
- MIN()
- SUM()
- GROUP BY
- HAVING

---

## Part 6: JOIN Operations (15 Points)

One of the most important features of relational databases is the ability to retrieve related information from multiple tables.

Write SQL queries using JOIN operations.

1. Display each student’s full name and the courses in which they are registered.
2. Display course names and their assigned instructors.
3. Display student names, course names, and registration dates.
4. Display all students, including those who have not registered for any courses.
5. Display all courses, including those that currently have no registered students.
6. Display the student name, course name, and grade for each registration.
7. Display each instructor and the courses they teach.

**Hint:** Use the following JOIN types:

- INNER JOIN
- LEFT JOIN
- RIGHT JOIN

---

## Part 7: Subqueries (10 Points)

Practice retrieving information using nested SQL queries.

Write queries to:

1. Find students who are registered in the course named Database Management.
2. Find courses taught by Robert Taylor.
3. Find students who have registered for more courses than the average student.
4. Find courses with credits greater than the average course credit value.
5. Find students who have not registered for any courses.

**Hint:** Explore:

- IN
- EXISTS
- NOT EXISTS
- AVG()
- Nested SELECT statements

---

## Part 8: Views (5 Points)

A database view is a virtual table based on the result of a SQL query.

Create a view named `student_course_view` that displays:

- Student ID
- Student full name
- Course name
- Course code
- Registration date
- Grade

Write SQL statements to:

1. Create the view.
2. Retrieve all records from the view.
3. Display students registered in Database Management using the view.
4. Modify or replace the view definition.
5. Drop the view.

---

## Part 9: Transaction Control Language (TCL) (10 Points)

Practice managing database transactions using TCL commands.

### Task 9.1 – COMMIT

1. Start a transaction.
2. Insert a new student.
3. Commit the transaction.
4. Verify that the student has been inserted.

### Task 9.2 – ROLLBACK

1. Start a transaction.
2. Update a student's email address.
3. Execute ROLLBACK.
4. Verify that the original email address remains unchanged.

### Task 9.3 – SAVEPOINT

1. Start a transaction.
2. Update a student's email address.
3. Create a savepoint named `email_checkpoint`.
4. Update the student's enrollment date.
5. Roll back to `email_checkpoint`.
6. Commit the transaction.
7. Verify which changes were saved.

**Hint:** Use:

- START TRANSACTION
- COMMIT
- ROLLBACK
- SAVEPOINT
- ROLLBACK TO SAVEPOINT

---

## Part 10: Challenge Activities (Optional – Intermediate)

Complete the following tasks to demonstrate your ability to combine multiple SQL concepts.

### Challenge 1 – Course Enrollment Report

Create a query that displays:

- Course name.
- Course code.
- Instructor name.
- Total registered students.
- Average course grade.

Sort the results by the total number of registered students in descending order.

Include courses with no registrations.

### Challenge 2 – Student Performance Report

Create a query that displays:

- Student full name.
- Number of registered courses.
- Average grade.
- Highest grade.

Only display students who have received at least one grade.

### Challenge 3 – Unregistered Students

Identify students who are not registered in any courses.

### Challenge 4 – Instructor Workload

Create a report showing:

- Instructor name.
- Department.
- Number of courses assigned.
- Total student registrations across those courses.

Include instructors who have no assigned courses.

### Challenge 5 – Database Integrity

Try inserting:

1. A student with an email address that already exists.
2. A course with an existing course code.
3. A registration referencing a student who does not exist.
4. A duplicate registration for the same student and course.

Observe the errors returned by MySQL.

Explain how primary keys, unique constraints, and foreign keys protect database integrity.

---

## 11\. Submission Requirements

Submit the following:

1. A complete SQL script containing your database and table creation statements.
2. SQL statements used to insert sample data.
3. SQL queries for all exercise sections.
4. Screenshots of selected query results.
5. A short explanation of the relationships between the four tables.
6. A brief explanation of how COMMIT, ROLLBACK, and SAVEPOINT work.

### File Naming Convention

Save your SQL script using the following format:

`studentname_mysql_lab.sql`

### Submission Checklist

- [ ]Database created successfully.
- [ ]All four tables created successfully.
- [ ]Primary and foreign keys implemented.
- [ ]Sample records inserted.
- [ ]Basic SELECT queries completed.
- [ ]UPDATE and DELETE operations completed.
- [ ]Aggregate queries completed.
- [ ]JOIN queries completed.
- [ ]Subqueries completed.
- [ ]View created and tested.
- [ ]Transaction operations tested.
- [ ]Challenge activities attempted.

---

## 12\. Grading Rubric

| Section | Points |
| --- | --- |
| Database creation and table design | 10 |
| Data insertion | 10 |
| Basic SQL queries | 10 |
| Data manipulation | 10 |
| Aggregate functions and grouping | 10 |
| JOIN operations | 15 |
| Subqueries | 10 |
| Views | 5 |
| Transaction control | 10 |
| SQL accuracy, organization, and submission | 10 |
| **Total** | **100** |

---

## Final Learning Outcome

By completing this laboratory exercise, you will have practical experience designing and managing a relational database using MySQL.

You will also develop the skills required to write SQL queries, establish relationships between tables, retrieve meaningful information, maintain data integrity, and manage database transactions.

These skills provide a foundation for more advanced topics, including database normalization, indexing, stored procedures, triggers, and database performance optimization.

## Database relationship diagram

I recommend including a database diagram with the exercise so students can visualize the relationships before writing SQL.

Entity Relationship Diagram (ERD)

Student Course Management System

Universal Data Modeling Series 5: Conceptual Model 3. ER Design Patterns | by Jun Shan | Medium

[medium.com](<https://medium.com/%40junshan0/universal-data-modeling-series-4-conceptual-model-3-er-design-patterns-5992971548eb?utm_source=chatgpt.com>)

Relationships

- One instructor can teach many courses.
- One student can have many registrations.
- One course can have many registrations.
- Students and courses have a many-to-many relationship resolved through the registrations table.

## Instructor preparation: Suggested teaching progression

I would divide the exercise into three classroom sessions to avoid overwhelming beginners.

| Session | Topics | Difficulty |
| --- | --- | --- |
| 1 | Database creation, tables, data types, INSERT, SELECT, UPDATE, DELETE | Beginner |
| 2 | WHERE, ORDER BY, aggregate functions, GROUP BY, JOIN, subqueries | Beginner–Intermediate |
| 3 | Views, transactions, savepoints, database integrity, challenges | Intermediate |

## Additional exercises worth considering

For a stronger post-secondary assessment, I would also introduce these three activities after students complete the main lab:

1. Database normalization: Ask students to identify repeating data and explain why the registration table is necessary.
2. Database security: Introduce `CREATE USER` and `GRANT` so students understand database access permissions.
3. Performance: Introduce indexes and ask students to compare queries using `EXPLAIN`.

My recommendation: Keep the main exercise as a 100-point laboratory assignment and make the challenge activities optional or part of a separate practical examination. This provides a gradual learning path without making the first MySQL project too difficult.
