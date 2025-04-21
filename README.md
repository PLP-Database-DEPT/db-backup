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

Start the server

```bash
  npm run start
```
