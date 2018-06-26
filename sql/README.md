# SQL Style Guide

1. [General](#general)
2. [SELECT](#select)
3. [FROM](#from)
4. [JOIN](#join)
5. [WHERE](#where)
6. [CASE](#case)

## General

* No tabs. 2 spaces per indent.
* No trailing whitespace.
* Always capitalize SQL keywords (e.g., `SELECT` or `AS`)
* Variable names should be underscore separated:

  __GOOD__:
  `SELECT COUNT(*) AS product_count`

  __BAD__:
  `SELECT COUNT(*) AS productCount`

* Comments should go near the top of your query, or at least near the closest `SELECT`
* Try to only comment on things that aren't obvious about the query (e.g., why a particular ID is hardcoded, etc.)
* Don't use single letter variable names be as descriptive as possible given the context:

  __GOOD__:
  `SELECT products.name AS product_name`

  __BAD__:
  `SELECT products.name AS n`

## `SELECT`

Align all columns to the first column on their own line:

```sql
SELECT
  orders.id,
  users.email,
  addresses.street,
  COUNT(items.id) AS items_count
FROM ...
```

`SELECT` goes on its own line:

```sql
SELECT
  name,
  ...
```

Always rename aggregates and function-wrapped columns:

```sql
SELECT
  name,
  SUM(amount) AS sum_amount
FROM ...
```

Always rename all columns when selecting with table aliases:

```sql
SELECT
  orders.id AS order_id,
  COUNT(line_items.id) AS items_count
FROM spree_orders AS orders
INNER JOIN spree_line_items AS line_items ON ...
```

Always use `AS` to rename columns:

__GOOD__:

```sql
SELECT
  orders.id AS order_id,
  COUNT(line_items.id) AS items_count
...
```

__BAD__:

```sql
SELECT
orders.id order_id,
COUNT(line_items.id) items_count
...
```

## `FROM`

Only one table should be in the `FROM`. Never use `FROM`-joins:

__GOOD__:

```sql
SELECT
  orders.id AS order_id,
  COUNT(line_items.id) AS items_count
FROM spree_orders AS orders
INNER JOIN spree_line_items AS line_items
  ON line_items.order_id = orders.id
...
```

__BAD__:

```sql
SELECT
  orders.id AS order_id,
  COUNT(line_items.id) AS items_count
FROM spree_orders AS orders, spree_line_items AS line_items
WHERE
  orders.id = line_items.order_id
...
```

## `JOIN`

Explicitly use `INNER JOIN` not just `JOIN`, making multiple lines of `INNER JOIN`s easier to scan:

__GOOD__:

```sql
SELECT
  orders.id AS order_id,
  COUNT(line_items.id) AS items_count
FROM spree_orders AS orders
INNER JOIN spree_line_items AS line_items ON line_items.order_id = orders.id
INNER JOIN ...
LEFT JOIN users ON orders.user_id = users.id
LEFT JOIN ...
```

__BAD__:

```sql
SELECT
  orders.id AS order_id,
  COUNT(line_items.id) AS items_count
FROM spree_orders AS orders
JOIN spree_line_items AS line_items ON line_items.order_id = orders.id
LEFT JOIN users ON orders.user_id = users.id
LEFT JOIN ...
```

Additional filters in the `JOIN`s go on new indented lines:

```sql
SELECT
  orders.id AS order_id,
  COUNT(line_items.id) AS items_count
FROM spree_orders AS orders
INNER JOIN spree_line_items AS line_items ON line_items.order_id = orders.id
INNER JOIN users ON orders.user_id = users.id
  AND users.b2b = 1
...
```

## `WHERE`

Multiple `WHERE` clauses should go on different lines and begin with the SQL operator:

```sql
SELECT
  id,
  total
FROM spree_orders AS orders
WHERE
  state = 'complete'
  AND total >= 1000
...
```

## `CASE`

`CASE` statements aren't always easy to format but try to align `WHEN`, `THEN`, and `ELSE` together inside `CASE` and `END`:

```sql
CASE WHEN state = 'complete'
     THEN 'Order complete'
     ELSE NULL
END
```
