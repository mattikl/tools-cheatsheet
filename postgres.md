# Postgres

Connection URIs

```
postgresql:/// # default database on localhost
postgresql:///dbname # database "dbname" on localhost
postgresql://user:password@host/dbname
postgresql://user:password@host/dbname?sslmode=require
```

## psql

```
psql dbname
psql connection_uri
psql -f file.sql
```

### Commands

| Command | Description |
| ------- | ----------- |
| `\conninfo` | Where am I connected and who am I |
| `\c dbname` | Connect to another database |
| `\l` | List databases in cluster |
| `\l+` | List databases with additional information |
| `\dn` | List all schemas |
| `\d` | List tables in `search_path` |
| `\d tablename` | Describe a table |
| `\i` | execute file contents |
| `\df` | List all functions |
| `\x` | Toggle expanded mode |
| `\!` | Execute bash command |

### Show connections

```sql
SELECT datname, pid, usename, client_addr, state, state_change FROM pg_stat_activity;
```

* [The Statictics Collector](https://www.postgresql.org/docs/9.2/static/monitoring-stats.html)

### Copying

Query results as CSV:

```sql
COPY (select ...) TO '/path/to/file.csv' (format CSV); -- without header
COPY (select ...) TO '/path/to/file.csv' (format CSV, header true);
```

* path must be absolute
* CSV encoding from database's Ctype?
* [COPY](https://www.postgresql.org/docs/current/static/sql-copy.html)

## pg_dump

Schema-only (no data) dump of the database:

    pg_dump --no-owner --no-acl --schema-only PG_URI -f schema.dump.sql

Schema-only (no data) dump of one database schema:

    pg_dump --no-owner --no-acl --schema-only --schema=name PG_URI -f schema.dump.sql

Data for one table:

    pg_dump --data-only --inserts -t schema.table PG_URI

Gotchas:

* COPY separate the fields with tabs, don't modify under a directory
  with `.editorconfig` that converts tabs to spaces
* ambiguous use of word "schema" (data definition vs schema of the database)
