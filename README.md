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

### W($condition)
Adds `WHERE $condition` phrase to query

### O($order)
Adds `ORDER BY $order` phrase to query

### L($limit)
Adds `LIMIT $limit` phrase to query

### LK($like)
Adds `LIKE $like` phrase to query

### G($group)
Adds `GROUP BY $group` phrase to query

### B($begin, $end)
Adds `BETWEEN $begin AND $end` phrase to query

### ON($on)
Adds `ON $on` phrase to query

### J($table, $type = 'INNER')
Adds `$type JOIN $table` phrase to query

### F($free, $is_data = true)
Use `$free` as query. If any data will be fetched `$is_data` must be true

### A($add)
Adds `$add` phrase to query

### set_charset($names = 'utf8')
Sets charset.

### print_query($return = false)
If return is true, function returns the crated query. Otherwise prints query with echo

