
# MySQL Commands – Quick Reference Guide

## 1\. MySQL Commands and Terminology

| Command / Term | Description | Example |
| --- | --- | --- |
| **CREATE TABLE** | Creates a new table in a database. | CREATE TABLE Students (ID INT, Name VARCHAR(50)); |
| **Data Type** | Defines the type of data stored in a column. | Age INT |
| **Default Database** | The database selected for use when no other database is specified. | USE School; |
| **DELETE** | Removes one or more records from a table. | DELETE FROM Students WHERE ID = 1; |
| **DESCRIBE** | Displays the structure of a table, including columns and data types. | DESCRIBE Students; |
| **DROP TABLE** | Permanently deletes a table and its data. | DROP TABLE Students; |
| **INSERT** | Adds new records to a table. | INSERT INTO Students (ID, Name) VALUES (1, 'John'); |
| **NOT NULL** | Ensures that a column cannot contain a NULL value. | Name VARCHAR(50) NOT NULL |
| **NULL** | Indicates that a column is allowed to have no value. | MiddleName VARCHAR(50) NULL |
| **NULL Data Value** | Represents missing, unknown, or unavailable information. | INSERT INTO Students (ID, Name) VALUES (2, NULL); |
| **Script** | A collection of SQL statements written together to perform database operations. | CREATE DATABASE School; |
| **Script File** | A file (usually ending in .sql) containing SQL commands. | school.sql |
| **Script Repository** | A storage location where SQL scripts are saved and organized. | A GitHub repository containing SQL files. |
| **SELECT** | Retrieves data from one or more tables. | SELECT * FROM Students; |
| **SHOW DATABASES** | Displays all databases available on the MySQL server. | SHOW DATABASES; |
| **Structured Query Language (SQL)** | A language used to create, manage, retrieve, and modify data in relational databases. | SELECT * FROM Students; |
| **UPDATE** | Modifies existing records in a table. | UPDATE Students SET Name = 'Mary' WHERE ID = 1; |
| **USE** | Selects a database to work with. | USE School; |

---

## 2\. Common MySQL Commands

### Create a Database

```
CREATE DATABASE School;
```

Creates a new database named School.

### Show All Databases

```
SHOW DATABASES;
```

Displays all available databases.

### Select a Database

```
USE School;
```

Selects School as the active database.

### Create a Table

```
CREATE TABLE Students (
    ID INT NOT NULL,
    Name VARCHAR(50) NOT NULL,
    Age INT,
    Email VARCHAR(100) NULL,
    PRIMARY KEY (ID)
);
```

Creates a Students table with four columns.

### Describe a Table

```
DESCRIBE Students;
```

Displays the table structure.

### Insert Records

```
INSERT INTO Students (ID, Name, Age, Email) VALUES (1, 'John', 20, 'john@email.com');
```

Adds a new student record.

### Select Records

```
SELECT * FROM Students;
```

Retrieves all records from the Students table.

To retrieve specific columns:

```
SELECT Name, Age FROM Students;
```

### Update Records

```
UPDATE Students
SET Age = 21
WHERE ID = 1;
```

Changes the age of the student with ID 1.

### Delete Records

```
DELETE FROM Students WHERE ID = 1;
```

Deletes the student record with ID 1.

### Drop a Table

```
DROP TABLE Students;
```

Permanently removes the Students table and its data.

---

## 3\. Important SQL Concepts

| Concept | Meaning |
| --- | --- |
| Database | An organized collection of data. |
| Table | A structure that stores data in rows and columns. |
| Row (Record) | A single entry in a table. |
| Column (Field) | A category of information in a table. |
| Primary Key | A column or combination of columns that uniquely identifies each record. |
| Foreign Key | A column that references a key in another table. |
| Constraint | A rule that controls the data allowed in a table. |
| VARCHAR | A variable-length text data type. |
| INT | An integer data type. |
| DATE | A data type used to store dates. |
| DECIMAL | A data type used to store exact numeric values, often for currency. |

---

## 4\. Important MySQL Reminders

- SQL commands generally end with a semicolon (;).
- MySQL keywords are not case-sensitive.
- Use single quotes for text values, such as 'John'.
- Use WHERE with UPDATE and DELETE to avoid changing or deleting every record unintentionally.
- NULL is different from zero (0) and an empty string ('').
- Use IS NULL to search for NULL values.

Example:

```
SELECT * FROM Students WHERE Email IS NULL;
```

---

## 5\. Quick Command Summary

| Purpose | SQL Command |
| --- | --- |
| Create database | CREATE DATABASE |
| Display databases | SHOW DATABASES |
| Select database | USE |
| Create table | CREATE TABLE |
| View table structure | DESCRIBE |
| Insert data | INSERT INTO |
| Retrieve data | SELECT |
| Modify data | UPDATE |
| Delete records | DELETE FROM |
| Delete table | DROP TABLE |

---

**End of MySQL Commands Quick Reference Guide**

You can copy this document into a file named MySQL_Commands.md and open it in Visual Studio Code, GitHub, or any Markdown editor.
