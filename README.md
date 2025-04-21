# Database Backup
The **mysqldump** is a command-line utility in MySQL used for creating backups of MySQL databases.
The **mysqldump** tool allows you to dump the structure and/or data of one or more databases into a file, which you can use to restore the databases later.
In practice, you often use the **mysqldump** for **backup** and **restore** operations, **database migration**, and **transferring databases** between servers.

## Commands

Creating a backup of a single database

```sql
  mysqldump -u username -p  db_name > path_to_backup_file
```

Creating a backup of all databases

```sql
  mysqldump -u username -p -A > path_to_backup_file
```

Creating a backup of data only

```bash
  mysqldump -u username -p -t db_name > path_to_backup_file
```

## How to Back Up and Restore a Database in MySQL

```sql
  CREATE DATABASE hr;
  USE hr;
  CREATE TABLE IF NOT EXISTS employees (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    email VARCHAR(255) NOT NULL UNIQUE
);
INSERT INTO employees (name, email) 
VALUES
    ('John Doe', 'john.doe@example.com'),
    ('Jane Smith', 'jane.smith@example.com'),
    ('Bob Johnson', 'bob.johnson@example.com'),
    ('Alice Jones', 'alice.jones@example.com'),
    ('Charlie Brown', 'charlie.brown@example.com');
```
### Backing up a database
```sql
mysqldump -u root -p hr > hr.sql
```
Accidentally deleting some rows from a table
```sql
 ????????????????????????????????
```
## Restoring a database
```sql
mysql -u root -p hr < hr.sql
```
### Retrieve data from the employees table to verify the restoration
```sql
USE hr;
SELECT * FROM employees;
```
