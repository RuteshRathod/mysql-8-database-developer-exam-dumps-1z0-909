

Exam 1Z0-909: MySQL 8.0 Database Developer Dump Set


## 1. MySQL `GET_LOCK` Sequence Deadlock

**Question:**
Consider two sessions executing:

```
Session 1> SELECT GET_LOCK('mylock1', 70);
Session 2> SELECT GET_LOCK('mylock2', 70);
Session 2> SELECT GET_LOCK('mylock1', 70);
Session 1> SELECT GET_LOCK('mylock2', 70);
```

What happens after the last statement in Session 1?

**Options:**

- An error will be returned after 70 seconds.
- A timeout will be returned after the wait_timeout interval has expired.
- The statement will succeed immediately.
- MySQL detects deadlock and kills Session 2.

**Correct Answer:**

- An error will be returned after 70 seconds.


## 2. Metadata Lock with `OPTIMIZE TABLE`

**Question:**
Session 1 starts a transaction and reads from `test.t`. Session 2 executes `OPTIMIZE TABLE test.t;`
What happens in Session 2?

**Options:**

- The statement in Session 2 will return an error immediately.
- Session 2 will wait for a table metadata lock to be granted.
- The statement will proceed without blocking.
- Session 1 will be rolled back.

**Correct Answer:**

- The statement in Session 2 will wait for a table metadata lock to be granted.


## 3. Equivalent SQL Query with LEFT OUTER JOIN

**Question:**
Given:

```sql
SELECT c.firstname, c.lastname, o.order_number
FROM customers c LEFT OUTER JOIN orders o USING (customer_number)
ORDER BY c.customer_number;
```

Which query gives the same result?

**Options:**

1. Uses a `WHERE` clause with an equality join.
2. Uses an `INNER JOIN`.
3. Uses a `RIGHT OUTER JOIN` from orders to customers.
4. Uses `OUTER JOIN` from customers to orders with ON condition.

**Correct Answer:**

- Option 4:

```sql
SELECT c.firstname, c.lastname, o.order_number
FROM customers c OUTER JOIN orders o ON c.customer_number = o.customer_number
ORDER BY c.customer_number;
```


## 4. String Function to Extract Substring

**Question:**
Which string function can be used to extract a portion of a non-numeric character string?

**Options:**

- TRUNCATE()
- EXTRACT()
- INSTR()
- SUBSTR()

**Correct Answer:**

- SUBSTR()


## 5. True Statements About MySQL Stored Routines

**Question:**
Which statements are true of Stored Routines in MySQL 8.0?

**Options:**

- Cursors must be opened before being accessed.
- Variables must be declared before cursors.
- Cursors are only for updating records, not retrieving records.
- Handlers must be declared before cursors.
- Prepared statements must be declared before conditions.
- Handlers must be declared before conditions.

**Correct Answers:**

- Cursors must be opened before being accessed.
- Variables must be declared before cursors.
- Handlers must be declared before conditions.


## 6. Column Declaration Order in Stored Routines

**Question:**
Which is the second true statement from the list of correct statements about stored routines?

**Correct Answer:**

- Variables must be declared before cursors.


## 7. Inserting Out-of-Range Value with `STRICT_ALL_TABLES` Mode

**Question:**
Given `CREATE TABLE table1 (var1 TINYINT, var2 INT); SET sql_mode=STRICT_ALL_TABLES; INSERT INTO table1 (var1) VALUES(1000);`
What happens?

**Options:**

- The row is inserted with a warning.
- The row is inserted, truncating the value.
- It fails with an error.
- The value is rounded and inserted.

**Correct Answer:**

- It fails with an error.


## 8. Creating a View with Partial Columns

**Question:**
What happens when executing:

```sql
CREATE VIEW emp_vu
AS
SELECT lastname, salary FROM employees;
```

**Options:**

- Returns an error because NOT NULL columns are omitted.
- Returns an error because PRIMARY KEY not included.
- It creates the view and stores the definition.

**Correct Answer:**

- It creates the view and stores the view definition and data in the data dictionary.


## 9. Inserting Into a View Missing Primary Key Column

**Question:**
Given a base table with `id` (auto-increment), `name`, `salary`, `email`, and a view `emp_vu1` with only `name` and `salary`, what happens when executing:

```sql
INSERT INTO emp_vu1 VALUES ('Alice', 20000);
```

**Options:**

- It inserts a row in the emp table.
- It inserts a row in the view only.
- Returns an error because PRIMARY KEY column is not in the view.

**Correct Answer:**

- It inserts a row in the emp table.


## 10. Inserting Into a View Without a View Table Storage

**Question:**
For a view:

```sql
CREATE VIEW emp_vu AS SELECT id, salary FROM employees;
```

What happens with `INSERT INTO emp_vu VALUES (104, 17000);`?

**Options:**

- Inserts a row in the view only.
- Returns an error.
- Inserts a row in the base table only.
- Inserts in both view and base table.

**Correct Answer:**

- It inserts a new row in the base table only.


## 11. Trigger Activation Timing

**Question:**
Given:

```sql
CREATE TRIGGER subtotal BEFORE INSERT ON income
FOR EACH ROW SET @subtotal = @subtotal + NEW.amount;
```

What causes the trigger to activate?

**Options:**

- Execution of an INSERT statement causes the trigger to activate.
- The SET in the trigger body activates the trigger.
- Activation happens after a row is inserted.
- UPDATE causes the trigger.

**Correct Answer:**

- Execution of an INSERT statement causes the trigger to activate.


## 12. Preventing Negative Ages

**Question:**
Which SQL statement will prevent negative ages from being inserted into the people table?

**Options:**

- (Trigger statement)
- (CHECK constraint)
- (Generated column)
- (Insert checking)

**Correct Answer:**

- `ALTER TABLE people ADD CONSTRAINT check_age CHECK (age>=0);`


## 13. Data Type for Preserving Numeric Precision

**Question:**
You need to insert and store the following values in a column: `12325.1251717137`, `6212`, `551.124111`.
Which data type will store the values without loss of precision?

**Options:**

- MEDIUMINT
- DECIMAL
- FLOAT
- DOUBLE

**Correct Answer:**

- DECIMAL


## 14. Tracking Maximum 10 Retakes

**Question:**
You need to add a column to the exam table to track the number of times a candidate has taken any exam (max 10, no date type). Which data type do you choose?

**Options:**

- MEDIUMINT
- TINYINT
- BIGINT
- INT
- SMALLINT

**Correct Answer:**

- TINYINT


## 15. Inserting Negative Value into UNSIGNED Column

**Question:**
Given `inventory_item_count INT UNSIGNED DEFAULT NULL` and `sql_mode=''`, what happens with:

```sql
INSERT INTO inventory_items (inventory_item_name, inventory_item_count)
VALUES ('Calculators', -1);
```

**Options:**

- Row inserted with a warning.
- Error is returned.
- Row is not inserted.

**Correct Answer:**

- It inserts a row with a warning.


## 16. Certificate Trust and Security Statements

**Question:**
Which two statements are true about certificate trust/security for MySQL server using certificates, private CA, and public trusted CAs?

**Options:**

- Public trusted CA certificates are more trustworthy than those signed by the corporate CA.
- Self signed certificates provide more trust than those signed by trusted CA.
- Public trusted CA certificates and those signed by the corporate CA provide the same level of trust in site destination host.
- Public trusted CA certificates and those signed by the corporate CA provide the same level of technical security.
- Public trusted CA certificates are more technically secure than those signed by the corporate CA.

**Correct Answers:**

- Public trusted CA certificates and those signed by the corporate CA provide the same level of technical security.
- Public trusted CA certificates and those signed by the corporate CA provide the same level of trust in site destination host.


## 17. MySQL Connector Authentication Plugin Error

**Question:**
Your program using a MySQL connector receives this error:
`Client does not support authentication protocol requested by server; consider upgrading MySQL client.`
Which two actions resolve this conflict?

**Options:**

- Place file in shell account.
- Upgrade connector to support `caching_sha2_password`.
- Use blank RSA/SSL certificates.
- Disable TLS/SSL authentication.
- Change user to use `mysql_native_password`.

**Correct Answers:**

- Upgrade connector to support `caching_sha2_password`.
- Change user to use `mysql_native_password`.


## 18. Updating Session Variable in MySQL

**Question:**
After `SET @r := 2;`, which query updates the value of `@r` to 0?

**Options:**

1. `SELECT 'Car' LIKE 'Ca?' INTO @r;`
2. `SELECT 'Car' REGEXP('Ca?') >= 0 INTO @r;`
3. `SELECT STRCMP('Car','Ca?') >= 0 INTO @r;`
4. `SELECT 'Car' RLIKE 'Ca?' INTO @r;`

**Correct Answer:**

- Option 1: `SELECT 'Car' LIKE 'Ca?' INTO @r;`


## 19. Effect of `ROLLBACK` After `AUTOCOMMIT=ON`

**Question:**
What happens if you execute `ROLLBACK;` after `AUTOCOMMIT` has been enabled in a session previously running in non-autocommit mode?

**Options:**

- Changes are rolled back.
- It has no effect.
- Uncommitted changes are rolled back.
- Transaction continues.

**Correct Answer:**

- It has no effect.

_Question Set Repository: https://github.com/RuteshRathod_
## 20. Transaction and Locking: Band Table Scenario

**Question:**
Given two sessions, one with `SELECT * FROM band FOR UPDATE` and `AUTOCOMMIT=1`, the other with an `UPDATE` inside a transaction:
Which two statements are true?

**Options:**

- Session 1 must commit before the UPDATE in Session 2 can complete.
- Session 2 takes an exclusive lock on all rows in band.
- Session 2 does not start a transaction.
- Session 1 takes a shared lock on all rows in band.
- Statements in Session 2 are committed.
- Session 1 does not block Session 2.

**Correct Answers:**

- Session 1 must commit before the UPDATE in Session 2 can complete.
- Session 1 takes a shared lock on all the rows in the band table.


## 21. Effects of `START TRANSACTION` in Autocommit Mode

**Question:**
When a program executes a `START TRANSACTION` statement in `AUTOCOMMIT` mode, which two statements are true?

**Options:**

- AUTOCOMMIT mode is enabled again after executing a ROLLBACK statement.
- AUTOCOMMIT mode is enabled again only by executing a COMMIT statement.
- All changes to any table rows commit immediately.
- Every SQL statement executes as a transaction.
- It temporarily disables AUTOCOMMIT mode.

**Correct Answers:**

- AUTOCOMMIT mode is enabled again after executing a ROLLBACK statement.
- It temporarily disables AUTOCOMMIT mode.


## 22. Optimal Types for Meeting Table Columns

**Question:**
Which column types are best for a `meeting` table with `start_time` and `duration`?

**Options:**

- start_time VARCHAR, duration VARCHAR
- start_time INT, duration INT
- start_time TIMESTAMP, duration TIME
- start_time DATE, duration TIME

**Correct Answer:**

- start_time TIMESTAMP, duration TIME


## 23. Efficient WHERE Clause for Customers Born in 2000

**Question:**
What's the most efficient WHERE clause for indexed DATETIME `date_of_birth`, to select all born in 2000?

**Options:**

- WHERE YEAR(date_of_birth) = 2000
- WHERE date_of_birth LIKE '2000%'
- WHERE date_of_birth >= '2000-01-01' AND date_of_birth < '2001-01-01'
- WHERE date_of_birth BETWEEN '2000-01-01' AND '2000-12-31'
- WHERE date_of_birth BETWEEN '2000-01-01' AND '2001-01-01'

**Correct Answer:**

- WHERE date_of_birth >= '2000-01-01' AND date_of_birth < '2001-01-01'


## 24. Obtain Query Execution Plan

**Question:**
Which statements can be used to obtain a query execution plan in MySQL?

**Options:**

- DESCRIBE
- EXPLAIN EXTENDED
- EXPLAIN
- ANALYZE QUERY FOR
- SHOW QUERY PLAN

**Correct Answers:**

- EXPLAIN EXTENDED
- EXPLAIN


## 25. Command Giving Query Timing Information

**Question:**
Which command displays timing information for a query?

**Options:**

- EXPLAIN FORMAT=TREE
- EXPLAIN ANALYZE
- EXPLAIN FORMAT=JSON
- EXPLAIN

**Correct Answer:**

- EXPLAIN ANALYZE


## 26. True Statements About Indexes

**Question:**
Which statements are true regarding MySQL 8.0 indexes?

**Options:**

- Primary index access will always be faster than a table scan.
- Indexing all of a table's columns improves performance.
- Indexes reduce disk space used.
- Indexes contain rows sorted by key values.
- Indexes are used to enforce unique constraints.

**Correct Answers:**

- Indexes contain rows sorted by key values.
- Indexes are used to enforce unique constraints.


## 27. Adding a Column to a MySQL Document Store Collection

**Question:**
When adding a new column to a MySQL Document Store collection table, what restriction applies?

**Options:**

- It must be a generated column referencing only an existing attribute of `doc`.
- The column must have a unique constraint.
- The column must have a default value.
- Any attribute can be referenced from any table.

**Correct Answer:**

- The column must be a GENERATED column referencing only an existing attribute of `doc`.


## 28. True Statements About Parameter Binding

**Question:**
Which two statements are true regarding parameter binding in CRUD operations?

**Options:**

- Binding can help avoid SQL injection attacks.
- Binding enables placeholders in statements which are executed with applied values.
- Binding is required for combining multiple tables.
- Binding improves efficiency for parallel data processing.
- Binding reduces overhead in aggregating data sets.

**Correct Answers:**

- Binding can help avoid SQL injection attacks.
- Binding enables placeholders in statements which are executed with applied values.


## 29. Query Using Generated Column with JSON_EXTRACT

**Question:**
Given a table:

```sql
CREATE TABLE work (
  job_no INT NOT NULL,
  data JSON NOT NULL,
  name VARCHAR(30) GENERATED ALWAYS AS (JSON_EXTRACT(`data`,'$.first_name')),
  PRIMARY KEY ('job_no')
) ENGINE=INNODB;
```

Why does:

```sql
SELECT job_no, name FROM work WHERE name = 'Robert';
```

return an empty set, even though Robert exists?

**Options:**

- The SELECT requires JSON_UNQUOTE() in the WHERE clause.
- The JSON datatype cannot be used in generated columns.
- Virtual/generated columns require special access methods.
- Table statistics affect the calculation.
- VARCHAR(30) is too short.

**Correct Answer:**

- The SELECT requires JSON_UNQUOTE() in the WHERE clause.


## 30. Python DB-API Query: Correct Fetch Usage

**Question:**
Given:

```python
hire_start = datetime.date(1999, 1, 1)
hire_end   = datetime.date(1999, 12, 31)
query = ("SELECT * FROM employees WHERE hired BETWEEN %s AND %s")
```

Which line returns data to the variable `d`?

**Options:**

- d = cursor.fetchall(query, (hire_start, hire_end))
- d = cursor.fetch(query, (hire_start, hire_end))
- d = cursor.fetch(query * (hire_start, hire_end))
- cursor.execute(query, (hire_start, hire_end))
- d = cursor.fetchall()

**Correct Answer:**

- d = cursor.fetchall()


## 31. `fetchall(query)` in Python DB-API

**Question:**
Is `fetchall(query)` valid in Python's DB-API?

**Options:**

- Yes
- No

**Correct Answer:**

- No


## 32. MySQL Connector/Python with `raw=True`

**Question:**
What is true about creating a MySQL Connector cursor with `raw=True`?

**Options:**

- It converts MySQL DATETIME to Python datetime values.
- The result is returned in a simple tabular form.
- It skips conversions from SQL to native formatted data types.
- The result is returned asynchronously.
- The result is returned as a raw BLOB.

**Correct Answer:**

- It skips conversions from SQL to native formatted data types.


## 33. Java Unable to Use Unix Socket with MySQL

**Question:**
A server uses a PDO MySQL connection with a Unix socket. Why can't Java/Connector/J use the same Unix socket method?

**Options:**

- The socket is not implemented in Connector/J driver.
- The X Dev API protocol must be enabled to use sockets in Connector/J.
- The socket can only be accessed from the local host.
- socket is a reserved word in Java.
- Java treats the socket file as insecure.

**Correct Answers:**

- The socket is not implemented in Connector/J driver.
- The socket can only be accessed from the local host.


_Question Set Repository: https://github.com/RuteshRathod_

## 34. Lock Wait Timeout with `innodb_rollback_on_timeout=OFF`

**Question:**
Given:

```sql
INSERT INTO band(song, year) VALUES('From Me to You', 1963);
UPDATE band SET year=1969 WHERE song='Come Together';
```

UPDATE times out with lock wait. `innodb_rollback_on_timeout=OFF`.

Which is true?

**Options:**

- The transaction is rolled back.
- The transaction is committed.
- Both statements complete successfully.
- The transaction never started.
- Only the INSERT statement completes successfully.

**Correct Answer:**

- Only the INSERT statement completes successfully.



### **Q35. Which SQL/JSON function correctly replaces the first element in a JSON array with the value `1`?**

**Options:**
A. `SELECT JSON_ARRAY_INSERT(@j, '$', 1);`
B. `SELECT JSON_SET(@j, '$', 1);`
C. `SELECT JSON_REPLACE(@j, '$', 1);`
D. `SELECT JSON_MERGE(@j, '1');`

**Correct Answer:**
B. `SELECT JSON_SET(@j, '$', 1);`

### **Q36. Which of the following SQL statements returns the top-level keys in a JSON document stored in variable `@j`?**

**Options:**
A. `SELECT JSON_KEYS(@j);`
B. `SELECT JSON_KEYS(@j, '$');`
C. `SELECT JSON_KEYS(@j, '$[*]');`
D. `SELECT JSON_KEYS(@j, '$[.*]');`
E. `SELECT JSON_KEYS(@j, '$.product');`

**Correct Answers:**
A. `SELECT JSON_KEYS(@j);`
B. `SELECT JSON_KEYS(@j, '$');`

### **Q37. Which privilege is required to create a stored procedure in MySQL?**

**Options:**
A. Only `CREATE` privilege is required
B. `CREATE ROUTINE` privilege is required
C. User must set a definer
D. `EXECUTE` privilege is required

**Correct Answer:**
B. `CREATE ROUTINE` privilege is required

### **Q38. Which of the following is a characteristic of NoSQL JSON document store databases?**

**Options:**
A. ACID Transactions
B. Well-defined Schemas
C. Complex Queries with JOINs
D. Ad hoc data format

**Correct Answer:**
D. Ad hoc data format

### **Q39. Which two SQL statements correctly reclaim memory used by a prepared statement named `prep`?**

**Options:**
A. `SET @a = '', EXECUTE prep USING @a;`
B. `DEALLOCATE PREPARE prep;`
C. `DROP PREPARE prep;`
D. `DROP PROCEDURE prep;`
E. `SET @prep = NULL;`

**Correct Answers:**
B. `DEALLOCATE PREPARE prep;`
C. `DROP PREPARE prep;`

### **Q40. Which connector makes PHP applications easier to migrate across different relational databases?**

**Options:**
A. MySQLi connector
B. PDO connector
C. mysql connector
D. mysql + X DevAPI

**Correct Answer:**
B. PDO connector

### **Q41. Which is an advantage of using `mysqli` over `mysql` in PHP?**

**Options:**
A. Supports databases from other vendors
B. Supports object-oriented programming
C. Includes X DevAPI functions
D. Supports blocking queries only

**Correct Answer:**
B. Supports object-oriented programming

### **Q42. Which SQL statement enforces data integrity on a JSON column in MySQL 8.0?**

**Options:**
A. `CREATE TABLE fshop (product JSON);`
B. `CREATE TABLE fshop (product JSON CHECK (JSON_LENGTH(product) > 1));`
C. `CREATE TABLE fshop (product JSON CHECK (JSON_VALID(product)));`
D. `CREATE TABLE fshop (product JSON DEFAULT '{}');`

**Correct Answer:**
C. `CREATE TABLE fshop (product JSON CHECK (JSON_VALID(product)));`

### **Q43. Which two SQL statements correctly add generated columns using `ALTER TABLE`?**

**Options:**
A. `ALTER TABLE col ADD COLUMN result INT GENERATED ALWAYS AS (doc->"$.result") STORED;`
B. `ALTER TABLE col ADD COLUMN result INT GENERATED ALWAYS AS (doc->"$.result") VIRTUAL;`
C. `ALTER TABLE col ADD COLUMN result INT GENERATED ALWAYS AS (doc->"$.result") STORED DEFAULT 0;`
D. `ALTER TABLE col ADD COLUMN result INT GENERATED ALWAYS AS (doc->"$.result") STORED NOT NULL;`

**Correct Answers:**
A. ... STORED
B. ... VIRTUAL

**Note:** Options with `DEFAULT 0` are invalid for generated columns.

### **Q44. Which SQL function call returns the number of non-null entries in the column `last_login`?**

**Options:**
A. `COUNT(*)`
B. `COUNT(last_login)`
C. `SUM(last_login)`
D. `FOUND_ROWS()`
E. `CHAR_LENGTH(last_login)`

**Correct Answer:**
B. `COUNT(last_login)`

### **Q45. Which two SQL queries generate a horizontal bar graph from a player's GPA using asterisks (`*`)?**

**Options:**
A. `REPEAT('*', GPA)`
B. `REPEAT('*', GPA * 10)`
C. `GROUP_CONCAT('*')`
D. `CHAR_LENGTH(GPA)`
E. `RPAD('*', GPA)`

**Correct Answers:**
A. `REPEAT('*', GPA)`
B. `REPEAT('*', GPA * 10)`