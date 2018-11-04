# MySQL

## mysql

Connecting

```bash
mysql -h 127.0.0.1 -P 3306 -u username -pPASSWORD dbname
```

Checking status and connections:

```sql
SHOW ENGINE INNODB STATUS \G
SHOW PROCESSLIST;
```

Switching default schema:

```sql
USE schema_name;
```

Tables:

```sql
SHOW TABLES;
DESC tablename;
SHOW CREATE TABLE tablename \G;
```

## Differences to Postgres

* `CREATE SCHEMA` is a synonym for `CREATE DATABASE`
* MySQL uses \` to quote system identifiers

[more differences](https://wiki.postgresql.org/wiki/Things_to_find_out_about_when_moving_from_MySQL_to_PostgreSQL)

