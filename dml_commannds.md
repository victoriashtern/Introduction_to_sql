
# DML – Data Manipulation Language Commands

DML is used to manipulate the actual data (records) stored inside database tables.

DML commands allow users to insert, retrieve, modify, and delete records in a database.

## 1\. DML Commands Summary

| DML Command | Description | Example |
| --- | --- | --- |
| **INSERT** | Adds new records to a table. | Adds a new student to Students. |
| **UPDATE** | Modifies existing records in a table. | Changes a student's name or age. |
| **DELETE** | Removes specific records from a table. | Deletes a student from Students. |

---

## 2\. SQL Code Examples

### 1\. INSERT

Adds new records to an existing table.

**Insert a single record:**

sql

```sql
INSERT INTO Students (ID, Name, Age)
VALUES (1, 'John', 20);
```

**Insert multiple records:**

sql

```sql
INSERT INTO Students (ID, Name, Age)
VALUES
    (2, 'Mary', 21),
    (3, 'David', 22),
    (4, 'Sarah', 19);
```

### 2\. UPDATE

Modifies existing records in a table.

**Update a student's age:**

sql

```sql
UPDATE Students
SET Age = 21
WHERE ID = 1;
```

**Update multiple columns:**

sql

```sql
UPDATE Students
SET Name = 'John Smith',
    Age = 22
WHERE ID = 1;
```

### 3\. DELETE

Removes specific records from a table.

**Delete a specific student:**

sql

```sql
DELETE FROM Students
WHERE ID = 1;
```

**Delete records based on a condition:**

sql

```sql
DELETE FROM Students
WHERE Age < 18;
```

---

## 3\. Important Notes

- DML stands for Data Manipulation Language.
- DML commands work with the records stored inside database tables.
- `INSERT` adds new records.
- `UPDATE` modifies existing records.
- `DELETE` removes records.
- Always use a `WHERE` clause with `UPDATE` and `DELETE` when you intend to affect specific records.
- Without a `WHERE` clause, `UPDATE` can modify all records and `DELETE` can remove all records.
- DML changes can be managed with transactions when the table uses a transactional storage engine such as InnoDB.

---

## 4\. DDL vs DML

| DDL | DML |
| --- | --- |
| Data Definition Language | Data Manipulation Language |
| Manages database structures. | Manages data inside tables. |
| Creates, modifies, and deletes database objects. | Inserts, updates, and deletes records. |
| Examples: CREATE, ALTER, DROP, TRUNCATE. | Examples: INSERT, UPDATE, DELETE. |

---
