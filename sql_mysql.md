
# SQL – Structured Query Language

## 1\. What is SQL?

**SQL (Structured Query Language)** is a standard language used to communicate with relational database management systems (RDBMS), such as MySQL.

SQL is used to:

- Create and manage databases.
- Create and manage tables.
- Insert records into tables.
- Retrieve information from databases.
- Update existing records.
- Delete records.
- Manage database permissions.
- Control database transactions.

---

## 2\. Types of SQL Languages

SQL commands are divided into five main categories:

| Category | Full Form | Purpose | Common Commands |
| --- | --- | --- | --- |
| DDL | Data Definition Language | Defines and manages database structures. | CREATE, ALTER, DROP, TRUNCATE |
| DML | Data Manipulation Language | Adds, modifies, and deletes table records. | INSERT, UPDATE, DELETE |
| DQL | Data Query Language | Retrieves information from database tables. | SELECT |
| DCL | Data Control Language | Manages database access and permissions. | GRANT, REVOKE |
| TCL | Transaction Control Language | Manages database transactions. | COMMIT, ROLLBACK, SAVEPOINT |

---

## 3\. DDL – Data Definition Language

DDL is used to create, modify, and delete database structures.

| Command | Description |
| --- | --- |
| CREATE DATABASE | Creates a new database. |
| CREATE TABLE | Creates a new table. |
| ALTER TABLE | Modifies an existing table structure. |
| DROP DATABASE | Deletes an entire database. |
| DROP TABLE | Deletes a table and its contents. |
| TRUNCATE TABLE | Removes all records while keeping the table structure. |

---

## 4\. DML – Data Manipulation Language

DML is used to manipulate the actual records stored inside database tables.

| Command | Description |
| --- | --- |
| INSERT | Adds new records to a table. |
| UPDATE | Modifies existing records. |
| DELETE | Removes records from a table. |

---

## 5\. DQL – Data Query Language

DQL is used to retrieve information from database tables.

| Command | Description |
| --- | --- |
| SELECT | Retrieves data from one or more tables. |

### Common SELECT Clauses

| Clause | Description |
| --- | --- |
| WHERE | Filters records based on a condition. |
| ORDER BY | Sorts records in ascending or descending order. |
| GROUP BY | Groups records with matching values. |
| HAVING | Filters grouped results. |
| DISTINCT | Removes duplicate results. |
| LIMIT | Limits the number of returned records. |

---

## 6\. DCL – Data Control Language

DCL is used to manage database security and user permissions.

| Command | Description |
| --- | --- |
| GRANT | Gives permissions to a database user. |
| REVOKE | Removes permissions from a database user. |

---

## 7\. TCL – Transaction Control Language

TCL is used to manage database transactions and control changes made to records.

| Command | Description |
| --- | --- |
| START TRANSACTION | Begins a transaction. |
| COMMIT | Saves transaction changes. |
| ROLLBACK | Reverses uncommitted transaction changes. |
| SAVEPOINT | Creates a point within a transaction to which you can roll back. |
