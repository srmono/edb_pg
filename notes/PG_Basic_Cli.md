# PostgreSQL Commands

This guide provides a comprehensive list of common PostgreSQL commands used for database management, querying, and administration.

## Basic Commands

### Connecting to a Database
```sql
psql -U username -d database_name -h host -p port
```
- **-U**: Specifies the username.
- **-d**: Specifies the database name.
- **-h**: Specifies the host.
- **-p**: Specifies the port.

### Disconnecting from a Database
```sql
\q
```

### Viewing All Databases
```sql
\l
```

### Switching Databases
```sql
\c database_name
```

### Viewing All Tables
```sql
\dt
```

### Viewing the Structure of a Table
```sql
\d table_name
```

## Data Definition Language (DDL)

### Creating a Database
```sql
CREATE DATABASE database_name;
```

### Dropping a Database
```sql
DROP DATABASE database_name;
```

### Creating a Table
```sql
CREATE TABLE table_name (
    column_name1 data_type1 constraints,
    column_name2 data_type2 constraints,
    ...
);
```

### Dropping a Table
```sql
DROP TABLE table_name;
```

### Altering a Table
```sql
ALTER TABLE table_name ADD column_name data_type constraints;
ALTER TABLE table_name DROP COLUMN column_name;
ALTER TABLE table_name ALTER COLUMN column_name SET DATA TYPE new_data_type;
```

### Creating an Index
```sql
CREATE INDEX index_name ON table_name (column_name);
```

### Dropping an Index
```sql
DROP INDEX index_name;
```

## Data Manipulation Language (DML)

### Inserting Data
```sql
INSERT INTO table_name (column1, column2, ...) VALUES (value1, value2, ...);
```

### Updating Data
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```

### Deleting Data
```sql
DELETE FROM table_name WHERE condition;
```

### Selecting Data
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```

## Data Control Language (DCL)

### Granting Privileges
```sql
GRANT privilege ON object TO user;
```
- Example: `GRANT SELECT ON table_name TO username;`

### Revoking Privileges
```sql
REVOKE privilege ON object FROM user;
```
- Example: `REVOKE SELECT ON table_name FROM username;`

## Transaction Control

### Starting a Transaction
```sql
BEGIN;
```

### Committing a Transaction
```sql
COMMIT;
```

### Rolling Back a Transaction
```sql
ROLLBACK;
```

## Utility Commands

### Viewing Current Database Connection Info
```sql
\conninfo
```

### Listing All Users
```sql
\du
```

### Showing Query Execution Plan
```sql
EXPLAIN query;
```

### Analyzing Query Performance
```sql
EXPLAIN ANALYZE query;
```

### Creating a User
```sql
CREATE USER username WITH PASSWORD 'password';
```

### Dropping a User
```sql
DROP USER username;
```

### Changing a User's Password
```sql
ALTER USER username WITH PASSWORD 'new_password';
```

## Example Usage

### Creating a Database and Table
```sql
CREATE DATABASE example_db;
\c example_db;
CREATE TABLE employees (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    position VARCHAR(50),
    salary NUMERIC
);
```

### Inserting Data into the Table
```sql
INSERT INTO employees (name, position, salary) VALUES ('John Doe', 'Manager', 60000);
INSERT INTO employees (name, position, salary) VALUES ('Jane Smith', 'Developer', 50000);
```

### Querying Data from the Table
```sql
SELECT * FROM employees;
```

### Updating Data in the Table
```sql
UPDATE employees SET salary = 65000 WHERE name = 'John Doe';
```

### Deleting Data from the Table
```sql
DELETE FROM employees WHERE name = 'Jane Smith';
```

### Granting Privileges to a User
```sql
CREATE USER example_user WITH PASSWORD 'example_password';
GRANT SELECT ON employees TO example_user;
```

## Summary

These commands cover the basics of PostgreSQL database management, including connecting to databases, creating and modifying tables, manipulating data, controlling user access, and managing transactions. For more advanced usage and detailed documentation, refer to the official [PostgreSQL documentation](https://www.postgresql.org/docs/).
