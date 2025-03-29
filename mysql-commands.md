# Essential MySQL Commands Reference

## Database Management
```sql
-- Create a new database
CREATE DATABASE database_name;

-- Show all databases
SHOW DATABASES;

-- Select a database to use
USE database_name;

-- Delete a database
DROP DATABASE database_name;

-- Show current database
SELECT DATABASE();
```

## Table Operations
```sql
-- Create a new table
CREATE TABLE table_name (
    column1 datatype constraints,
    column2 datatype constraints,
    ...
);

-- Show all tables in current database
SHOW TABLES;

-- Show table structure
DESCRIBE table_name;
SHOW COLUMNS FROM table_name;

-- Delete a table
DROP TABLE table_name;

-- Rename a table
RENAME TABLE old_name TO new_name;

-- Empty a table (delete all rows)
TRUNCATE TABLE table_name;
```

## Table Modification
```sql
-- Add a new column
ALTER TABLE table_name ADD column_name datatype;

-- Modify an existing column
ALTER TABLE table_name MODIFY column_name new_datatype;

-- Rename a column
ALTER TABLE table_name CHANGE old_column_name new_column_name datatype;

-- Drop a column
ALTER TABLE table_name DROP COLUMN column_name;

-- Add a primary key
ALTER TABLE table_name ADD PRIMARY KEY (column_name);

-- Add a foreign key
ALTER TABLE table_name ADD CONSTRAINT constraint_name
FOREIGN KEY (column_name) REFERENCES referenced_table(referenced_column);
```

## Data Manipulation
```sql
-- Insert data
INSERT INTO table_name (column1, column2, ...) 
VALUES (value1, value2, ...);

-- Multiple row insert
INSERT INTO table_name (column1, column2, ...) 
VALUES 
    (value1, value2, ...),
    (value1, value2, ...),
    ...;

-- Update data
UPDATE table_name SET column1 = value1, column2 = value2 
WHERE condition;

-- Delete data
DELETE FROM table_name WHERE condition;
```

## Querying Data
```sql
-- Select all columns and rows
SELECT * FROM table_name;

-- Select specific columns
SELECT column1, column2, ... FROM table_name;

-- Select with conditions
SELECT * FROM table_name WHERE condition;

-- Sorting results
SELECT * FROM table_name ORDER BY column_name ASC|DESC;

-- Limit results
SELECT * FROM table_name LIMIT number;

-- Select distinct values
SELECT DISTINCT column_name FROM table_name;

-- Group results
SELECT column1, COUNT(*) FROM table_name GROUP BY column1;

-- Join tables
SELECT * FROM table1 
JOIN table2 ON table1.column_name = table2.column_name;
```

## Aggregation Functions
```sql
-- Count rows
SELECT COUNT(*) FROM table_name;

-- Sum values
SELECT SUM(column_name) FROM table_name;

-- Average
SELECT AVG(column_name) FROM table_name;

-- Maximum value
SELECT MAX(column_name) FROM table_name;

-- Minimum value
SELECT MIN(column_name) FROM table_name;
```

## Indexes
```sql
-- Create an index
CREATE INDEX index_name ON table_name (column_name);

-- Create a unique index
CREATE UNIQUE INDEX index_name ON table_name (column_name);

-- Show indexes
SHOW INDEX FROM table_name;

-- Drop an index
DROP INDEX index_name ON table_name;
```

## Transactions
```sql
-- Start a transaction
START TRANSACTION;

-- Commit changes
COMMIT;

-- Rollback changes
ROLLBACK;
```

## User Management
```sql
-- Create a new user
CREATE USER 'username'@'host' IDENTIFIED BY 'password';

-- Grant privileges
GRANT privileges ON database_name.table_name TO 'username'@'host';

-- Show all users
SELECT user FROM mysql.user;

-- Show user privileges
SHOW GRANTS FOR 'username'@'host';

-- Revoke privileges
REVOKE privileges ON database_name.table_name FROM 'username'@'host';

-- Delete a user
DROP USER 'username'@'host';
```

## Advanced Operations
```sql
-- Create a view
CREATE VIEW view_name AS
SELECT columns FROM table_name WHERE condition;

-- Create a stored procedure
DELIMITER //
CREATE PROCEDURE procedure_name()
BEGIN
    -- SQL statements
END //
DELIMITER ;

-- Execute a stored procedure
CALL procedure_name();

-- Create a trigger
DELIMITER //
CREATE TRIGGER trigger_name
BEFORE|AFTER INSERT|UPDATE|DELETE ON table_name
FOR EACH ROW
BEGIN
    -- SQL statements
END //
DELIMITER ;
```
