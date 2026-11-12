
# DCL – Data Control Language Commands

DCL (Data Control Language) is used to manage database security, user access, and permissions.

DCL allows database administrators to control who can access a database and what operations they are allowed to perform.

## 1\. DCL Commands Summary

| DCL Command | Description | Example / Purpose |
| --- | --- | --- |
| **GRANT** | Gives permissions to a database user. | Allows a user to retrieve data from a table. |
| **REVOKE** | Removes permissions from a database user. | Removes a user's permission to retrieve data. |

---

## 2\. SQL Code Examples

### 1\. GRANT

GRANT is used to give specific permissions to a database user.

**Grant SELECT permission:**

sql

```sql
GRANT SELECT
ON School.*
TO 'john'@'localhost';
```

Allows John to retrieve data from tables in the School database.

**Grant multiple permissions:**

sql

```sql
GRANT SELECT, INSERT, UPDATE
ON School.*
TO 'john'@'localhost';
```

Allows John to retrieve, insert, and update records in the School database.

**Grant all privileges:**

sql

```sql
GRANT ALL PRIVILEGES
ON School.*
TO 'john'@'localhost';
```

Gives John all applicable privileges on the School database.

### 2\. REVOKE

REVOKE is used to remove specific permissions from a database user.

**Revoke SELECT permission:**

sql

```sql
REVOKE SELECT
ON School.*
FROM 'john'@'localhost';
```

Removes John's permission to retrieve data from the School database.

**Revoke multiple permissions:**

sql

```sql
REVOKE INSERT, UPDATE
ON School.*
FROM 'john'@'localhost';
```

Removes John's permissions to insert and update records in the School database.

**Revoke all privileges:**

sql

```sql
REVOKE ALL PRIVILEGES
ON School.*
FROM 'john'@'localhost';
```

Removes the applicable database privileges granted to John on the School database.

---

## 3\. Common MySQL Permissions

| Permission | Description |
| --- | --- |
| **SELECT** | Allows users to retrieve data from tables. |
| **INSERT** | Allows users to add new records. |
| **UPDATE** | Allows users to modify existing records. |
| **DELETE** | Allows users to delete records. |
| **CREATE** | Allows users to create databases or tables, depending on the granted scope. |
| **ALTER** | Allows users to modify table structures. |
| **DROP** | Allows users to delete databases or tables, depending on the granted scope. |
| **INDEX** | Allows users to create and drop indexes. |
| **ALL PRIVILEGES** | Grants all applicable privileges at the specified scope. |

---

## 4\. Important Notes

- DCL stands for Data Control Language.
- DCL is primarily used to manage database security and permissions.
- `GRANT` gives permissions to database users.
- `REVOKE` removes permissions from database users.
- Permissions can be assigned at different levels, such as global, database, table, and column levels.
- Only authorized users with sufficient privileges can grant or revoke permissions.
- MySQL user accounts include both a username and a host.
- Granting or revoking privileges does not automatically create or delete a user account.

---

## 5\. GRANT vs REVOKE

| GRANT | REVOKE |
| --- | --- |
| Gives permissions to users. | Removes permissions from users. |
| Controls what users can do. | Restricts what users can do. |
| Used to provide database access. | Used to withdraw database access privileges. |

---
