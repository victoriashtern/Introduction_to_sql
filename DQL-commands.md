# DQL – Data Query Language Commands

DQL is used to retrieve, filter, sort, and display information stored in database tables.

The main DQL command is `SELECT`, supported by several clauses and operators.

## 1\. DQL Commands and Clauses Summary

| Command / Clause | Description | Example / Purpose |
| --- | --- | --- |
| **SELECT** | Retrieves data from one or more tables. | Displays student records. |
| **DISTINCT** | Removes duplicate values from query results. | Displays unique student names. |
| **WHERE** | Filters records based on a condition. | Finds students older than 18. |
| **AND** | Combines conditions; all must be true. | Finds students older than 18 AND in grade 12. |
| **OR** | Combines conditions; at least one must be true. | Finds students in grade 11 OR grade 12. |
| **NOT** | Reverses a condition. | Finds students NOT in grade 12. |
| **IN** | Matches values from a specified list. | Finds students in selected grades. |
| **BETWEEN** | Finds values within a specified range. | Finds students aged between 18 and 22. |
| **LIKE** | Searches for a specified pattern. | Finds names starting with J. |
| **IS NULL** | Finds records containing NULL values. | Finds students without an email address. |
| **IS NOT NULL** | Finds records that do not contain NULL values. | Finds students with an email address. |
| **ORDER BY** | Sorts query results in ascending or descending order. | Sorts students by name. |
| **GROUP BY** | Groups records with matching values. | Groups students by grade. |
| **HAVING** | Filters grouped results. | Displays grades with more than 10 students. |
| **LIMIT** | Restricts the number of records returned. | Displays the first 5 students. |
| **AS** | Assigns a temporary name (alias) to a column or table. | Displays Name as Student\_Name. |

---

## 2\. SQL Code Examples

Assume we have a table named `Students`.

### SELECT – Retrieve All Records

sql

```sql
SELECT * FROM Students;
```

### WHERE – Filter Records

sql

```sql
SELECT * FROM Students
WHERE Age > 18;
```

### DISTINCT – Remove Duplicates

sql

```sql
SELECT DISTINCT Age
FROM Students;
```

### ORDER BY – Sort Records

sql

```sql
SELECT * FROM Students
ORDER BY Name ASC;
```

### GROUP BY – Group Records

sql

```sql
SELECT Age, COUNT(*)
FROM Students
GROUP BY Age;
```

### HAVING – Filter Grouped Records

sql

```sql
SELECT Age, COUNT(*)
FROM Students
GROUP BY Age
HAVING COUNT(*) > 1;
```

### LIMIT – Restrict Results

sql

```sql
SELECT * FROM Students
LIMIT 5;
```

---

## 3\. Important Notes

- DQL stands for Data Query Language.
- `SELECT` is the primary DQL command.
- DQL retrieves information without modifying the stored records.
- `WHERE` filters individual records.
- `HAVING` filters grouped results.
- `ORDER BY` sorts query results.
- `GROUP BY` organizes records into groups.
- `DISTINCT` removes duplicate results.
- `LIMIT` restricts the number of returned records.

---

**End of DQL Commands Reference Guide**
