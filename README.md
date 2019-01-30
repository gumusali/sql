# Connection
Class includes dsn file to connect db. It's `/app/system/dsn.php` by default. You can define new path on construction.
`$sql = new sql('path_to_dsn_file/from_root_dir')`

DSN file must contains `$_dsn` array that has `host`, `user`, `pass` and `db` keys.

### r($count = false)
Executes the query. If $count is true, returns only integer otherwise returns an array. If a select query executed it will return an array that contains data. 

If other queries executed and successful it will return an array with status, insert_id and affected_rows keys. Status key can only have two values: ok or error. On failure status will be error and array will have error and query keys.
```
Array ( 
  [status] => error 
  [error] => PDO error text
  [query] => executed query
)
```

### S($columns, $from)
Creates the query: `SELECT $columns FROM $from`

### U($table, $set)
Creates the query: `UPDATE $table SET $set`

### D($from)
Creates the query: `DELETE FROM $from`

### I($into, $columns, $values, $multiple = false)
Creates the query if `$multiple` is false: `INSERT INTO $into($columns) VALUES($values)`
if `$multiple` is true creates `INSERT INTO $into($columns) VALUES $values` so you can add multiple rows at once

