You can add an index on an expression.

This query:

```sql
SELECT * FROM test1 WHERE lower(col1) = 'value';
```

Can be faster if we created and index on the lower function.

```sql
CREATE INDEX test1_lower_col1_idx ON test1 (lower(col1));
```

https://www.postgresql.org/docs/current/indexes-expressional.html
