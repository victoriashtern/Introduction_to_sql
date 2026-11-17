# MySQL Database Laboratory - Beginner to Intermediate

Estimated duration: 3–4 hours


### 1 Introduction

In this practical exercise, you will design and implement a relational database for a college or university student course management system.

The system will store information about students, instructors, courses, and student course registrations.

You will apply SQL concepts to create database structures, insert and manipulate records, retrieve information, establish relationships, and manage transactions.

The exercise is divided into progressive sections, starting with fundamental SQL commands and moving toward intermediate database operations.

###  Learning Objectives

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

###  Scenario

A post-secondary institution wants to develop a database to manage its student course registration system.

The database must maintain information about:

- Students enrolled at the institution.
- Instructors responsible for teaching courses.
- Courses offered by different departments.
- Student registrations for individual courses.

Each student can register for multiple courses, and each course can have multiple students.

An instructor can teach multiple courses, but each course is assigned to one instructor.

Your task is to design and implement the database using MySQL.


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

###  Basic SQL Queries 

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

### Data Manipulation 

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

### Aggregate Functions and Grouping (10 Points)

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

### JOIN Operations (15 Points)

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

### Subqueries 

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

