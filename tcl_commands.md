# TCL – Transaction Control Language Commands

TCL (Transaction Control Language) is used to manage database transactions and control changes made to database records.

A transaction is a group of SQL operations treated as a single logical unit of work.

TCL allows users to save changes, undo changes, and create checkpoints within transactions.

## 1\. TCL Commands Summary

| TCL Command | Description | Example / Purpose |
| --- | --- | --- |
| **START TRANSACTION** | Begins a new transaction. | Starts a group of database operations. |
| **COMMIT** | Permanently saves transaction changes. | Saves changes made during a transaction. |
| **ROLLBACK** | Reverses uncommitted transaction changes. | Undoes changes made during a transaction. |
| **SAVEPOINT** | Creates a checkpoint within a transaction. | Creates a point to which a transaction can roll back. |
| **ROLLBACK TO SAVEPOINT** | Reverses changes made after a specified savepoint. | Returns the transaction to an earlier checkpoint. |
| **RELEASE SAVEPOINT** | Removes a previously created savepoint. | Deletes a transaction checkpoint. |

---

## 2\. SQL Code Examples

Assume we have a table named `Students`.

### 1\. START TRANSACTION

Begins a new transaction.

sql

```sql
START TRANSACTION;
```

Starts a transaction so that subsequent changes can be committed or rolled back.

### 2\. COMMIT

Saves all changes made during the current transaction.

sql

```sql
START TRANSACTION;

UPDATE Students
SET Age = 21
WHERE ID = 1;

COMMIT;
```

Saves the updated age permanently.

### 3\. ROLLBACK

Reverses uncommitted changes made during a transaction.

sql

```sql
START TRANSACTION;

UPDATE Students
SET Age = 25
WHERE ID = 1;

ROLLBACK;
```

Cancels the update and restores the previous value.

### 4\. SAVEPOINT

Creates a checkpoint within a transaction.

sql

```sql
START TRANSACTION;

UPDATE Students
SET Age = 21
WHERE ID = 1;

SAVEPOINT sp1;

UPDATE Students
SET Age = 22
WHERE ID = 2;
```

Creates a checkpoint named `sp1` after the first update.

### 5\. ROLLBACK TO SAVEPOINT

Reverses changes made after a specified savepoint without cancelling the entire transaction.

sql

```sql
ROLLBACK TO SAVEPOINT sp1;
```

Undoes changes made after `sp1` while keeping earlier transaction changes.

### 6\. RELEASE SAVEPOINT

Removes a previously created savepoint.

sql

```sql
RELEASE SAVEPOINT sp1;
```

Deletes the checkpoint named `sp1`. It does not undo the transaction changes.

---

## 3\. Important Notes

- TCL stands for Transaction Control Language.
- TCL is used to manage database transactions.
- `START TRANSACTION` begins a transaction.
- `COMMIT` saves transaction changes.
- `ROLLBACK` undoes uncommitted transaction changes.
- `SAVEPOINT` creates a checkpoint within a transaction.
- `ROLLBACK TO SAVEPOINT` returns to a previously created checkpoint.
- `RELEASE SAVEPOINT` removes a checkpoint.
- Transactions are commonly used when multiple database operations must succeed or fail together.
- In MySQL, transaction rollback requires a transactional storage engine, such as InnoDB.
- DDL statements generally cause implicit commits in MySQL, so they should not be treated as ordinary rollbackable transaction operations.

---

## 4\. COMMIT vs ROLLBACK

| COMMIT | ROLLBACK |
| --- | --- |
| Saves transaction changes. | Reverses uncommitted transaction changes. |
| Makes changes permanent. | Restores the previous state for the undone changes. |
| Ends the current transaction. | Ends the current transaction when used without a savepoint. |
| Used when operations are successful. | Used when operations need to be cancelled. |

---

## 5\. Example of a Complete Transaction

The following example demonstrates how a transaction works.

sql

```sql
START TRANSACTION;

UPDATE Students
SET Age = 21
WHERE ID = 1;

SAVEPOINT sp1;

UPDATE Students
SET Age = 22
WHERE ID = 2;

ROLLBACK TO SAVEPOINT sp1;

COMMIT;
```

**What happens?**

1. A transaction begins.
2. The age of student 1 is updated.
3. A savepoint named `sp1` is created.
4. The age of student 2 is updated.
5. The second update is undone by rolling back to `sp1`.
6. The transaction is committed, saving the first update.

---

**End of TCL Commands Reference Guide**
