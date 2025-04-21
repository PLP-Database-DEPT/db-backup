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
## How to Back Up and Restore All Databases in MySQL
#### Create sample database
```sql
CREATE DATABASE sampledb1;
CREATE DATABASE sampledb2;
CREATE DATABASE sampledb3;
```
## Backing up all databases
```sql
mysqldump -u root -p --all-databases > all_databases.sql
```
## Accidentally removing a database
```sql
drop database sampledb1;
drop database sampledb2;
```
### Restoring all databases
```sql
mysql -u root -p < all_databases.sql
```
## Backing Up MySQL Table
### Create sample database
```sql
CREATE DATABASE sales;
USE sales;
CREATE TABLE products (
    product_id INT AUTO_INCREMENT PRIMARY KEY,
    product_name VARCHAR(255),
    unit_price DECIMAL(10, 2)
);

CREATE TABLE customers (
    customer_id INT AUTO_INCREMENT PRIMARY KEY,
    customer_name VARCHAR(255),
    email VARCHAR(255)
);

CREATE TABLE orders (
    order_id INT AUTO_INCREMENT PRIMARY KEY,
    customer_id INT,
    order_date DATE,
    FOREIGN KEY (customer_id) REFERENCES customers(customer_id)
);

CREATE TABLE order_details (
    order_detail_id INT AUTO_INCREMENT PRIMARY KEY,
    order_id INT,
    product_id INT,
    quantity INT,
    total_price DECIMAL(10, 2),
    FOREIGN KEY (order_id) REFERENCES orders(order_id),
    FOREIGN KEY (product_id) REFERENCES products(product_id)
);
-- Inserting into Products Table
INSERT INTO products (product_name, unit_price)
VALUES
    ('Desktop Computer', 800.00),
    ('Tablet', 300.00),
    ('Printer', 150.00);

-- Inserting into Customers Table
INSERT INTO customers (customer_name, email)
VALUES
    ('Alice Johnson', 'alice@example.com'),
    ('Charlie Brown', 'charlie@example.com'),
    ('Eva Davis', 'eva@example.com');

-- Inserting into Orders Table
INSERT INTO orders (customer_id, order_date)
VALUES
    (1, '2023-02-01'),
    (2, '2023-02-02'),
    (3, '2023-02-03');

-- Inserting into Order_Details Table
INSERT INTO order_details (order_id, product_id, quantity, total_price)
VALUES
    -- Order 1 details
    (1, 1, 2, 1600.00),
    (1, 2, 3, 900.00),

    -- Order 2 details
    (2, 2, 2, 600.00),
    (2, 3, 1, 150.00),

    -- Order 3 details
    (3, 1, 3, 2400.00),
    (3, 3, 2, 300.00);
```
