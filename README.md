# Postgres foreign data wrappers (FDW) YAML specification.

This projects aims to provide a YAML specification for Postgres foreign data wrappers (FDW) configuration.

## Template
Specification template consists of four main sections:
- `foreign_server`
- `user_mapping`
- `import_foreign_schema`
- `create_foreign_table`

Only `foreign_server` section is required.
In a sense that you must create a foreign server to be able to use the FDW.
All other sections are optional and subject to the specific FDW implementation.
Each section can have zero, one or set of options that can be used to configure the FDW.

**Note**:
> If `foreign_server` section has no options as per FDW implementation, it turns it into an optional section.
In this case, it can be ommited from the configuration file.

Option itself has a `name` denoted by `option` key and a set of properties:

- `required`: `true` | `false`. Flag, whether the option is required or not.
- `default`: default value, if any
- `description`: description of the option

```yaml
foreign_server:
[- <option>
 ...
 - <option>]
user_mapping:
[- <option>
 ...
 - <option>]
import_foreign_schema:
[- <option>
 ...
 - <option>]
create_foreign_table:
[- <option>
 ...
 - <option>]

<option> =
  option:
    required: true | false
    default:
    description:
```

## Supported FDWs
Each FDW has a dedicated folder. Within it, there are files per specific FDW version.

FDW official repo|Folder
-|-
[mysql_fdw](https://github.com/EnterpriseDB/mysql_fdw)|[mysql_fdw](./mysql_fdw/)
[oracle_fdw](https://github.com/laurenz/oracle_fdw)|[oracle_fdw](./oracle_fdw/)
[sqlite_fdw](https://github.com/pgspider/sqlite_fdw)|[sqlite_fdw](./sqlite_fdw/)
[mongo_fdw](https://github.com/EnterpriseDB/mongo_fdw)|[mongo_fdw](./mongo_fdw/)
[tds_fdw](https://github.com/tds-fdw/tds_fdw)|[tds_fdw](./tds_fdw/)
[redis_fdw](https://github.com/pg-redis-fdw/redis_fdw)|[redis_fdw](./redis_fdw/)
[postgres_fdw](https://www.postgresql.org/docs/current/postgres-fdw.html)|[postgres_fdw](./postgres_fdw/)
[file_fdw](https://www.postgresql.org/docs/current/file-fdw.html)|[file_fdw](./file_fdw/)
