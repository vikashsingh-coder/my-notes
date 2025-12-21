Below is a **structured MySQL notes**, written with the exact purpose:

- Easy **revision in the future**
- Clear **real-world examples & use cases**

---

# MySQL Notes (Beginner to Practical Level)

---

## 1. Selecting a Database

Before running any query, select the database you want to work with.

```sql
USE sql_store;
```

---

## 2. Order of SQL Query Execution

The order in which SQL clauses are written **matters**.

```sql
SELECT 1, 2
-- FROM customers
-- WHERE customer_id = 1
-- ORDER BY first_name
```

**Execution order (important for understanding):**

1. FROM
2. WHERE
3. SELECT
4. ORDER BY

---

## 3. Selecting All Columns

Fetch all columns from a table.

```sql
SELECT *
FROM customers;
```

**Use case:**

- Quick data inspection
- Debugging

---

## 4. Selecting Specific Columns

Fetch only required columns and create calculated fields.

```sql
SELECT first_name, last_name, points + 10 AS discount_factor
FROM customers;
```

**Use case:**

- Optimized queries
- Creating derived values (discounts, scores, etc.)

---

## 5. Selecting Unique Values

Get only distinct values from a column.

```sql
SELECT DISTINCT state
FROM customers;
```

**Use case:**

- Dropdowns (State, City, Category)
- Data analysis

---

## 6. Column Alias (AS)

Rename columns in the output.

```sql
SELECT
  name,
  unit_price,
  (unit_price * 1.1) AS new_price
FROM products;
```

**Use case:**

- Price increase calculations
- Readable result sets

---

## 7. Comparison Operators

```sql
-- >
-- <
-- >=
-- <=
-- =
-- !=
-- <>
```

> `!=` and `<>` both mean **NOT EQUAL**

```sql
SELECT *
FROM customers
WHERE birthdate > '1990-01-01';
```

---

## 8. Logical Operators (AND, OR, NOT)

### AND / OR Example

```sql
SELECT *
FROM customers
WHERE birth_date > '1990-01-02'
   OR (points > 1000 AND state = 'CA');
```

### NOT Example

```sql
SELECT *
FROM customers
WHERE NOT (
  birth_date > '1990-01-02'
  OR (points > 1000 AND state = 'CA')
);
```

**Use case:**

- Complex business rules
- Filtering premium or restricted users

---

## 9. Real Use Case: Order Total Price

> Get items of **order 6** where total price is greater than **30**

```sql
SELECT *
FROM order_items
WHERE order_id = 6
  AND unit_price * quantity > 30;
```

---

## 10. IN Operator

### Multiple OR Conditions (Better Way)

```sql
SELECT *
FROM customers
WHERE state IN ('VA', 'GA', 'FL');
```

### NOT IN Example

```sql
SELECT *
FROM customers
WHERE state NOT IN ('VA', 'GA', 'FL');
```

---

## 11. IN with Numbers

> Find products with specific stock quantities.

```sql
SELECT *
FROM products
WHERE quantity_in_stock IN (49, 38, 72);
```

---

## 12. BETWEEN (Range Queries)

### Numeric Range

```sql
SELECT *
FROM customers
WHERE points BETWEEN 1000 AND 3000;
```

### Date Range

```sql
SELECT *
FROM customers
WHERE birth_date BETWEEN '1990-01-01' AND '2000-01-01';
```

---

## 13. LIKE Operator (Pattern Matching)

### Starts With

```sql
SELECT *
FROM customers
WHERE last_name LIKE 'Nas%';
```

### Contains Character

```sql
SELECT *
FROM customers
WHERE last_name LIKE '%b%';
```

### Ends With

```sql
SELECT *
FROM customers
WHERE last_name LIKE '%y';
```

### Fixed Length Pattern

```sql
SELECT *
FROM customers
WHERE last_name LIKE 'a___y';
```

### Address Search

```sql
SELECT *
FROM customers
WHERE address LIKE '%TRAIL%'
   OR address LIKE '%AVENUE%';
```

### Phone Number Ends With 9

```sql
SELECT *
FROM customers
WHERE phone LIKE '%9';
```

---

## 14. Regular Expressions (REGEXP)

```sql
SELECT *
FROM customers
WHERE last_name REGEXP '^Br|mac|field$';
```

### Common REGEXP Symbols

- `^` → starts with
- `$` → ends with
- `|` → OR
- `[abc]` → any of a, b, c
- `[a-f]` → range

### More Examples

```sql
SELECT *
FROM customers
WHERE first_name REGEXP 'elka|ambur';
```

```sql
SELECT *
FROM customers
WHERE last_name REGEXP 'ey$|on$';
```

```sql
SELECT *
FROM customers
WHERE last_name REGEXP 'b[ru]';
```

```sql
SELECT *
FROM customers
WHERE last_name REGEXP '^my|se';
```

---

## 15. NULL Checks

```sql
SELECT *
FROM customers
WHERE phone IS NULL;
```

```sql
SELECT *
FROM customers
WHERE phone IS NOT NULL;
```

```sql
SELECT *
FROM orders
WHERE shipped_date IS NULL;
```

---

## 16. ORDER BY Clause

Sort results using calculated columns.

```sql
SELECT *, quantity * unit_price AS total_price
FROM order_items
WHERE order_id = 2
ORDER BY total_price DESC;
```

---

## 17. LIMIT (Pagination)

### Top Records

```sql
SELECT *
FROM customers
ORDER BY points DESC
LIMIT 3;
```

### Pagination (Skip + Fetch)

```sql
SELECT *
FROM customers
ORDER BY points DESC
LIMIT 6, 3;
```

---

## 18. INNER JOIN

### Orders with Customer Info

```sql
SELECT order_id, o.customer_id, first_name, last_name
FROM orders o
INNER JOIN customers c
  ON c.customer_id = o.customer_id;
```

### Order Items with Product Info

```sql
SELECT order_id, i.product_id, name, quantity, i.unit_price
FROM order_items i
INNER JOIN products p
  ON i.product_id = p.product_id
ORDER BY quantity DESC;
```

---

## 19. JOIN Across Databases

```sql
SELECT *
FROM order_items oi
INNER JOIN sql_inventory.products p
  ON p.product_id = oi.product_id;
```

---

## 20. SELF JOIN (Employee → Manager)

```sql
SELECT
  e.employee_id,
  e.first_name,
  m.first_name AS manager
FROM employees e
JOIN employees m
  ON e.reports_to = m.employee_id;
```

**Use case:**

- Organizational hierarchy
- Reporting structure

---

## 21. Multiple Table JOIN

```sql
SELECT
  o.order_id,
  c.first_name,
  c.last_name,
  os.name AS status
FROM orders o
JOIN customers c ON o.customer_id = c.customer_id
JOIN order_statuses os ON o.status = os.order_status_id;
```

---

## 22. Real-World Payment Example (Multiple Databases)

```sql
SELECT
  p.payment_id,
  p.client_id,
  p.invoice_id,
  p.date,
  p.amount,
  c.first_name,
  c.last_name,
  pm.name AS payment_mode
FROM payments p
JOIN sql_store.customers c
  ON c.customer_id = p.client_id
JOIN sql_invoicing.payment_methods pm
  ON pm.payment_method_id = p.payment_method;
```

---

# MySQL Notes – Advanced Joins & Data Manipulation

---

## 1. Compound Join Condition

Used when **multiple columns together uniquely identify a record**.

```sql
SELECT *
FROM order_items oi
JOIN order_item_notes oin
  ON oi.order_id = oin.order_id
 AND oi.product_id = oin.product_id;
```

**Use case:**

- Order items with notes
- Composite primary keys

---

## 2. Implicit vs Explicit Join Syntax

### Explicit Join (Recommended)

```sql
SELECT *
FROM orders o
JOIN customers c
  ON o.customer_id = c.customer_id;
```

### Implicit Join (Old Style)

```sql
SELECT *
FROM orders o, customers c
WHERE o.customer_id = c.customer_id;
```

### ❌ Dangerous Case (Missing WHERE)

```sql
SELECT *
FROM orders o, customers c;
```

⚠️ This creates a **Cartesian product**
If there are 10 orders and 10 customers → **100 rows**

**Best Practice:**
👉 Always use **explicit JOIN syntax**

---

## 3. OUTER JOINS

### LEFT JOIN

Returns **all rows from left table**, even if no match exists.

```sql
SELECT
  o.order_id,
  o.order_date,
  s.name AS shipper_name
FROM orders o
LEFT JOIN shippers s
  ON o.shipper_id = s.shipper_id;
```

**Use case:**

- Orders without assigned shippers

---

### RIGHT JOIN

Returns **all rows from right table**.

```sql
SELECT *
FROM shippers s
RIGHT JOIN orders o
  ON o.shipper_id = s.shipper_id
WHERE s.shipper_id IS NULL;
```

**Use case:**

- Find orders without shippers

---

### Products Without Orders

```sql
SELECT
  p.product_id,
  p.name,
  oi.quantity
FROM products p
LEFT JOIN order_items oi
  ON p.product_id = oi.product_id
ORDER BY p.name;
```

---

## 4. OUTER JOIN with Multiple Tables

```sql
SELECT
  c.customer_id,
  c.first_name,
  o.order_id,
  s.name AS shipper_name
FROM customers c
LEFT JOIN orders o
  ON c.customer_id = o.customer_id
LEFT JOIN shippers s
  ON o.shipper_id = s.shipper_id;
```

**Use case:**

- Customers with or without orders
- Orders with or without shippers

---

### Mixed INNER + OUTER JOIN

```sql
SELECT
  o.order_id,
  o.order_date,
  c.first_name,
  s.name AS shipper_name,
  os.name AS status
FROM orders o
JOIN customers c
  ON o.customer_id = c.customer_id
LEFT JOIN shippers s
  ON o.shipper_id = s.shipper_id
JOIN order_statuses os
  ON o.status = os.order_status_id;
```

---

## 5. SELF OUTER JOIN

Used to represent **hierarchical relationships**.

```sql
SELECT
  e.employee_id,
  e.first_name,
  m.first_name AS manager
FROM employees e
LEFT JOIN employees m
  ON e.reports_to = m.employee_id;
```

**Use case:**

- Employee → Manager mapping
- Organization hierarchy

---

## 6. USING Clause

Used when **column names are same in both tables**.

```sql
SELECT
  o.order_id,
  c.first_name,
  s.name AS shipper_name
FROM orders o
JOIN customers c
USING (customer_id)
LEFT JOIN shippers s
USING (shipper_id);
```

### Using Multiple Columns

```sql
SELECT *
FROM order_items oi
JOIN order_item_notes
USING (order_id, product_id);
```

**Benefit:**

- Cleaner syntax
- Less repetition

---

## 7. NATURAL JOIN (⚠️ Not Recommended)

```sql
SELECT *
FROM orders
NATURAL JOIN customers;
```

⚠️ Automatically joins on columns with same names
❌ Can break if schema changes

---

## 8. CROSS JOIN (Cartesian Product)

Each row from one table joins with **every row** of another table.

### Explicit Syntax (Recommended)

```sql
SELECT
  o.order_id,
  c.first_name
FROM orders o
CROSS JOIN customers c;
```

### Implicit Syntax

```sql
SELECT
  o.order_id,
  c.first_name
FROM orders o, customers c;
```

**Use case:**

- Generating combinations
- Testing data volume

---

## 9. UNION Operator

Used to **combine results of multiple SELECT queries**.

### Basic Rule

- Same number of columns
- Compatible data types

```sql
SELECT
  order_id,
  'ACTIVE' AS status
FROM orders
WHERE order_date >= '2019-01-01'
UNION
SELECT
  order_id,
  'INACTIVE' AS status
FROM orders
WHERE order_date < '2019-01-01';
```

---

### Different Columns (Still Valid but Rare)

```sql
SELECT first_name
FROM customers
UNION
SELECT comments
FROM orders;
```

---

### Real Use Case: Customer Tier System

```sql
SELECT customer_id, first_name, points, 'BRONZE' AS type
FROM customers
WHERE points < 2000
UNION
SELECT customer_id, first_name, points, 'SILVER' AS type
FROM customers
WHERE points BETWEEN 2000 AND 3000
UNION
SELECT customer_id, first_name, points, 'GOLD' AS type
FROM customers
WHERE points > 3000
ORDER BY points DESC;
```

---

## 10. INSERT Data (Single Row)

```sql
INSERT INTO customers (
  first_name,
  last_name,
  address,
  city,
  state
)
VALUES (
  'vikash',
  'singh',
  'hatt wali',
  'tekanpur',
  'GW'
);
```

---

## 11. INSERT Multiple Rows

```sql
INSERT INTO shippers (name)
VALUES
  ('shipper1'),
  ('shipper2'),
  ('shipper3');
```

```sql
INSERT INTO products (name, quantity_in_stock, unit_price)
VALUES
  ('Banana', 24, 5.2),
  ('Apple', 15, 3.4),
  ('Papaya', 26, 7.0);
```

---

## 12. Inserting Hierarchical Data (Parent → Child)

```sql
INSERT INTO orders (customer_id, order_date, status)
VALUES (1, '2019-01-01', 1);

INSERT INTO order_items
VALUES
  (LAST_INSERT_ID(), 1, 3, 2.5),
  (LAST_INSERT_ID(), 2, 2, 5.5),
  (LAST_INSERT_ID(), 3, 3, 4.5);
```

**Use case:**

- Order → Order Items

---

## 13. Copy Data Between Tables

### Create Backup Table

```sql
CREATE TABLE archive_orders AS
SELECT * FROM orders;
```

### Copy Selected Records

```sql
INSERT INTO archive_orders
SELECT *
FROM orders
WHERE order_date > '2019-01-01';
```

---

### Real-World Invoice Archive

```sql
CREATE TABLE invoice_archive AS
SELECT
  i.invoice_id,
  i.number,
  c.name AS client_name,
  i.invoice_total,
  i.invoice_date,
  i.due_date,
  i.payment_date
FROM invoices i
JOIN clients c
USING (client_id)
WHERE payment_date IS NOT NULL;
```

---

## 14. UPDATE Existing Records

### Update Single Record

```sql
UPDATE invoices
SET payment_total = 34.5,
    payment_date = '2023-02-25'
WHERE invoice_id = 1;
```

### Reset to Default

```sql
UPDATE invoices
SET payment_total = DEFAULT,
    payment_date = NULL
WHERE invoice_id = 1;
```

---

### Update Using Existing Values

```sql
UPDATE invoices
SET payment_total = invoice_total * 0.5,
    payment_date = due_date
WHERE invoice_id = 3;
```

---

### Update Multiple Records

```sql
UPDATE invoices
SET payment_total = invoice_total * 0.5,
    payment_date = due_date
WHERE invoice_id IN (3, 4);
```

---

### Update Using Conditions

```sql
UPDATE customers
SET points = points + 50
WHERE birth_date < '1990-01-01';
```

---

### Update Using Subquery

```sql
UPDATE customers
SET points = points + 50
WHERE customer_id IN (
  SELECT DISTINCT customer_id
  FROM orders
  WHERE shipper_id IS NULL
);
```

**Use case:**

- Reward customers affected by shipping delays

---

# MySQL Notes – Data Deletion, Aggregations, Subqueries & Functions

---

## 1. Deleting Data

### Delete Records Using a Subquery

```sql
DELETE FROM invoices
WHERE client_id = (
  SELECT client_id
  FROM clients
  WHERE name = 'Topiclounge'
);
```

**Use case:**

- Remove invoices related to a specific client

⚠️ **Tip:** Always run the subquery with `SELECT` first to verify results.

---

### Database Restore Tip

To restore deleted data:

- Open **SQL Script**
- Run the backup `.sql` file

---

## 2. Aggregate Functions

Used to perform calculations on a set of rows.

```sql
SELECT
  MAX(invoice_total) AS highest,
  MIN(invoice_total) AS lowest,
  AVG(invoice_total) AS average,
  SUM(invoice_total) AS total,
  SUM(invoice_total * 1.1) AS modified_total,
  COUNT(payment_date) AS payment_done_count,
  COUNT(*) AS total_records
FROM invoices;
```

**Use case:**

- Financial reports
- Sales dashboards

---

## 3. GROUP BY Clause

Used to **group rows** and apply aggregate functions.

### Total Invoice Amount Per Client

```sql
SELECT
  client_id,
  SUM(invoice_total) AS total
FROM invoices
GROUP BY client_id
ORDER BY total DESC;
```

---

### Grouping by City and State

```sql
SELECT
  city,
  state,
  SUM(invoice_total) AS total
FROM invoices
JOIN clients USING (client_id)
GROUP BY city, state
ORDER BY total DESC;
```

---

### Daily Sales by Payment Method

```sql
SELECT
  date,
  pm.name AS payment_method,
  SUM(amount) AS total_sale
FROM payments p
JOIN payment_methods pm
  ON p.payment_method = pm.payment_method_id
GROUP BY date, payment_method
ORDER BY date;
```

---

## 4. HAVING Clause (Filtering Grouped Data)

Used **after GROUP BY**, unlike `WHERE`.

```sql
SELECT
  client_id,
  SUM(amount) AS total_sale,
  COUNT(*) AS invoice_count
FROM payments
GROUP BY client_id
HAVING total_sale >= 75;
```

---

### Real Use Case: High-Value Customers

```sql
SELECT
  customer_id,
  first_name,
  state,
  SUM(oi.unit_price * oi.quantity) AS total_price
FROM customers c
JOIN orders USING (customer_id)
JOIN order_items oi USING (order_id)
WHERE state = 'VA'
GROUP BY customer_id, first_name
HAVING total_price > 100;
```

---

## 5. WITH ROLLUP

Provides **subtotals and grand totals**.

### Total Payments Per Client

```sql
SELECT
  client_id,
  SUM(amount)
FROM payments
GROUP BY client_id WITH ROLLUP;
```

---

### Sales by State and City

```sql
SELECT
  state,
  city,
  SUM(amount)
FROM payments
JOIN clients USING (client_id)
GROUP BY state, city WITH ROLLUP;
```

---

### Payments by Mode

```sql
SELECT
  pm.name AS payment_mode,
  SUM(amount) AS total_payment
FROM payments p
JOIN payment_methods pm
  ON p.payment_method = pm.payment_method_id
GROUP BY payment_mode WITH ROLLUP;
```

---

## 6. Subqueries (Complex Queries)

### Products More Expensive Than Product ID = 3

```sql
SELECT *
FROM products
WHERE unit_price > (
  SELECT unit_price
  FROM products
  WHERE product_id = 3
);
```

---

### Employees Earning More Than Average Salary

```sql
SELECT *
FROM employees
WHERE salary > (
  SELECT AVG(salary)
  FROM employees
);
```

---

## 7. IN Operator with Subqueries

### Products Never Ordered

```sql
SELECT *
FROM products
WHERE product_id NOT IN (
  SELECT DISTINCT product_id
  FROM order_items
);
```

---

### Clients With No Invoices

```sql
SELECT *
FROM clients
WHERE client_id NOT IN (
  SELECT DISTINCT client_id
  FROM invoices
);
```

#### Same Result Using JOIN (Preferred)

```sql
SELECT *
FROM clients
LEFT JOIN invoices USING (client_id)
WHERE invoice_id IS NULL;
```

---

## 8. ALL Operator

### Invoices Larger Than All Invoices of Client ID = 3

```sql
SELECT *
FROM invoices
WHERE invoice_total > ALL (
  SELECT invoice_total
  FROM invoices
  WHERE client_id = 3
);
```

### Same Logic Using MAX()

```sql
SELECT *
FROM invoices
WHERE invoice_total > (
  SELECT MAX(invoice_total)
  FROM invoices
  WHERE client_id = 3
);
```

---

## 9. ANY Operator

### Clients With At Least Two Invoices

```sql
SELECT *
FROM clients
WHERE client_id = ANY (
  SELECT client_id
  FROM invoices
  GROUP BY client_id
  HAVING COUNT(*) >= 2
);
```

---

## 10. Correlated Subqueries

### Employees Earning More Than Their Office Average

```sql
SELECT *
FROM employees e
WHERE salary > (
  SELECT AVG(salary)
  FROM employees
  WHERE office_id = e.office_id
);
```

---

### Invoices Higher Than Client Average

```sql
SELECT *
FROM invoices i
WHERE invoice_total > (
  SELECT AVG(invoice_total)
  FROM invoices
  WHERE client_id = i.client_id
);
```

---

## 11. EXISTS Operator

### Clients Who Have Invoices

```sql
SELECT *
FROM clients c
WHERE EXISTS (
  SELECT 1
  FROM invoices
  WHERE client_id = c.client_id
);
```

---

### Products Never Ordered (Best Practice)

```sql
SELECT *
FROM products p
WHERE NOT EXISTS (
  SELECT 1
  FROM order_items
  WHERE product_id = p.product_id
);
```

---

## 12. Subqueries in SELECT Clause

### Invoice Comparison Report

```sql
SELECT
  invoice_id,
  invoice_total,
  (SELECT AVG(invoice_total) FROM invoices) AS invoice_avg,
  invoice_total - (SELECT AVG(invoice_total) FROM invoices) AS difference
FROM invoices;
```

---

### Client Sales Summary

```sql
SELECT
  client_id,
  name,
  (SELECT AVG(invoice_total) FROM invoices) AS average,
  (SELECT SUM(invoice_total)
   FROM invoices
   WHERE client_id = c.client_id) AS total_sales,
  (SELECT total_sales - average) AS difference
FROM clients c;
```

---

## 13. Derived Tables (Subquery as a Table)

```sql
SELECT *
FROM (
  SELECT
    client_id,
    name,
    (SELECT AVG(invoice_total) FROM invoices) AS average,
    (SELECT SUM(invoice_total)
     FROM invoices
     WHERE client_id = c.client_id) AS total_sales,
    (SELECT total_sales - average) AS difference
  FROM clients c
) AS sales_summary
WHERE total_sales IS NOT NULL;
```

---

## 14. Essential MySQL Functions

### 1️⃣ Numeric Functions

```sql
SELECT ROUND(5.25);
SELECT FLOOR(6.52);
SELECT CEILING(6.52);
SELECT ROUND(RAND() * 1000, 2);
SELECT TRUNCATE(52.36525, 2);
SELECT ABS(-5.2625);
```

---

### 2️⃣ String Functions

```sql
SELECT LENGTH('vikash');
SELECT UPPER('vikash');
SELECT LOWER('viKash');
SELECT LTRIM('   vikash');
SELECT RTRIM('vikash   ');
SELECT TRIM('   vikash   ');
SELECT SUBSTRING('kindergarten', 3, 4);
SELECT LEFT('kindergarten', 4);
SELECT RIGHT('kindergarten', 5);
SELECT CONCAT('vikash', ' ', 'singh');
SELECT LOCATE('g', 'kindergarten');
SELECT REPLACE('kindergarten', 'garden', 'garten');
```

---

### 3️⃣ Date & Time Functions

```sql
SELECT NOW(), CURDATE(), CURTIME();
SELECT YEAR(NOW()), MONTH(NOW()), DAY(NOW());
SELECT DAYNAME(NOW()), MONTHNAME(NOW());
SELECT HOUR(NOW()), MINUTE(NOW()), SECOND(NOW());
SELECT EXTRACT(DAY FROM NOW());
```

---

### 4️⃣ Date Formatting

```sql
SELECT DATE_FORMAT(NOW(), '%Y %M %D');
SELECT DATE_FORMAT(NOW(), '%y-%m-%d');
SELECT TIME_FORMAT(NOW(), '%h:%i:%s %p');
```

---

### 5️⃣ Date Calculations

```sql
SELECT DATE_ADD(NOW(), INTERVAL 1 DAY);
SELECT DATE_ADD(NOW(), INTERVAL 1 HOUR);
SELECT DATE_SUB(NOW(), INTERVAL 1 YEAR);
SELECT TIME_TO_SEC('09:02') - TIME_TO_SEC('09:00');
SELECT DATEDIFF(NOW(), '1992-10-04');
```

---

## 15. IFNULL & COALESCE

```sql
SELECT
  order_id,
  IFNULL(shipper_id, 'Not Assigned') AS shipper
FROM orders;
```

**Use case:**

- Handling missing values in reports

---

# MySQL Notes – Conditional Logic, Views & Stored Procedures

---

## 1. Handling NULL Values (COALESCE & IFNULL)

### COALESCE – First Non-NULL Value

```sql
SELECT
  order_id,
  COALESCE(shipper_id, comments, 'Not Exist') AS shipper
FROM orders;
```

**Use case:**

- If `shipper_id` exists → show it
- Else show `comments`
- Else show `"Not Exist"`

---

### IFNULL – Replace NULL with Default

```sql
SELECT
  first_name,
  IFNULL(phone, 'Unknown') AS phone_number
FROM customers;
```

**Use case:**

- Display meaningful values instead of `NULL`

---

## 2. Conditional Logic Using IF()

### Product Order Frequency Report

```sql
SELECT
  product_id,
  name,
  COUNT(*) AS orders,
  IF(COUNT(*) = 1, 'Once', 'Many Times') AS frequency
FROM products
JOIN order_items USING (product_id)
GROUP BY product_id;
```

**Use case:**

- Identify fast-moving vs slow-moving products

---

### Order Status Based on Date

```sql
SELECT
  order_id,
  order_date,
  IF(YEAR(order_date) = YEAR(NOW()), 'Active', 'Archived') AS status
FROM orders;
```

**Use case:**

- Current vs old orders

---

## 3. Conditional Logic Using CASE (Switch Statement)

### Order Category by Year

```sql
SELECT
  order_id,
  CASE
    WHEN YEAR(order_date) = 2018 THEN 'Active'
    WHEN YEAR(order_date) = 2017 THEN 'Last Year'
    WHEN YEAR(order_date) < 2017 THEN 'Archived'
    ELSE 'Future'
  END AS category
FROM orders;
```

---

### Customer Tier Based on Points

```sql
SELECT
  CONCAT(first_name, ' ', last_name) AS customer_name,
  points,
  CASE
    WHEN points > 3000 THEN 'Gold'
    WHEN points BETWEEN 2000 AND 3000 THEN 'Silver'
    ELSE 'Bronze'
  END AS category
FROM customers
ORDER BY points DESC;
```

**Use case:**

- Loyalty programs
- Customer segmentation

---

## 4. Views in MySQL

A **VIEW** is a virtual table based on a query.

### Create a View for Client Sales Summary

```sql
CREATE VIEW invoice_filter_data AS
SELECT
  c.client_id,
  c.name,
  SUM(payment_total) AS total_sales
FROM clients c
JOIN invoices USING (client_id)
GROUP BY client_id, name;
```

---

### Use the View Like a Table

```sql
SELECT
  MAX(total_sales) AS maximum_sale,
  MIN(total_sales) AS minimum_sale
FROM invoice_filter_data;
```

---

### Create View for Client Remaining Balance

```sql
CREATE VIEW client_balance_remain AS
SELECT
  c.client_id,
  c.name,
  SUM(invoice_total - payment_total) AS client_balance
FROM clients c
JOIN invoices USING (client_id)
GROUP BY client_id, name;
```

**Use case:**

- Outstanding payment tracking

---

### Drop a View

```sql
DROP VIEW IF EXISTS client_balance_remain;
```

---

### Update (Replace) an Existing View

```sql
CREATE OR REPLACE VIEW client_balance_remain AS
SELECT
  c.client_id,
  c.name,
  SUM(invoice_total - payment_total) AS client_balance
FROM clients c
JOIN invoices USING (client_id)
GROUP BY client_id, name
HAVING client_balance > 500
ORDER BY client_balance DESC;
```

---

## 5. Updatable Views

A view is **updatable** if it does NOT contain:

- DISTINCT
- Aggregate functions
- GROUP BY / HAVING
- UNION

---

### Create an Updatable View

```sql
CREATE VIEW invoice_with_balance AS
SELECT
  invoice_id,
  number,
  client_id,
  invoice_total,
  payment_total,
  invoice_total - payment_total AS balance,
  invoice_date,
  due_date,
  payment_date
FROM invoices
WHERE invoice_total - payment_total > 0;
```

---

### Delete Using View

```sql
DELETE
FROM invoice_with_balance
WHERE invoice_id = 1;
```

---

### Update Using View

```sql
UPDATE invoice_with_balance
SET due_date = DATE_ADD(due_date, INTERVAL 2 DAY)
WHERE invoice_id = 3;
```

---

### Important Behavior (Row Disappears from View)

```sql
UPDATE invoice_with_balance
SET payment_total = invoice_total
WHERE invoice_id = 3;
```

✔ Record is updated
❌ Row disappears from view (balance becomes 0)

---

## 6. WITH CHECK OPTION

Prevents updates that cause rows to disappear from the view.

```sql
CREATE OR REPLACE VIEW invoice_with_balance AS
SELECT
  invoice_id,
  number,
  client_id,
  invoice_total,
  payment_total,
  invoice_total - payment_total AS balance,
  invoice_date,
  due_date,
  payment_date
FROM invoices
WHERE invoice_total - payment_total > 0
WITH CHECK OPTION;
```

```sql
UPDATE invoice_with_balance
SET payment_total = invoice_total
WHERE invoice_id = 3;
```

❌ Results in **CHECK OPTION failed** error

---

## 7. Benefits of Views

- Abstraction over base tables
- Reduced impact of schema changes
- Restricted access (security)
- Cleaner and reusable queries

⚠️ **Tip:** Use views only when they truly add value.

---

## 8. Stored Procedures

Stored procedures:

- Separate SQL logic from application code
- Improve security
- Allow controlled access to data

---

### Create a Simple Stored Procedure

```sql
DELIMITER $$

CREATE PROCEDURE get_clients()
BEGIN
  SELECT * FROM invoices;
END $$

DELIMITER ;
```

### Call the Procedure

```sql
CALL sql_invoicing.get_clients();
```

---

### Stored Procedure Using a View

```sql
DELIMITER $$

CREATE PROCEDURE get_invoices_with_balance()
BEGIN
  SELECT *
  FROM invoice_with_balance
  WHERE balance > 0;
END $$

DELIMITER ;
```

---

### Drop Stored Procedure

```sql
DROP PROCEDURE IF EXISTS get_payments;
```

---

### Create Procedure to Get All Payments

```sql
DELIMITER $$

CREATE PROCEDURE get_payments()
BEGIN
  SELECT * FROM payments;
END $$

DELIMITER ;
```

---

## 9. Stored Procedure with Parameters

### Get Clients by State

```sql
DELIMITER $$

CREATE PROCEDURE get_clients_by_state(
  state CHAR(2)
)
BEGIN
  SELECT *
  FROM clients
  WHERE state = state;
END $$

DELIMITER ;
```

---

### Default Parameter Value Handling

```sql
DELIMITER $$

CREATE PROCEDURE get_clients_by_state(
  state CHAR(2)
)
BEGIN
  IF state IS NULL THEN
    SET state = 'CA';
  END IF;

  SELECT *
  FROM clients
  WHERE state = state;
END $$

DELIMITER ;
```

```sql
CALL get_clients_by_state(NULL);
```

---

### Get Invoices by Client ID

```sql
DELIMITER $$

CREATE PROCEDURE get_invoices_by_client(
  client_id INT
)
BEGIN
  SELECT *
  FROM invoices
  WHERE client_id = client_id;
END $$

DELIMITER ;
```

---

# MySQL Advanced Concepts – Practical Notes (Procedures, Functions, Triggers, Events)

## 1. Conditional Logic in Stored Procedures (NULL Handling)

### Use Case

When building APIs or reports, sometimes filters are **optional**.
If the parameter is `NULL`, return **all records**, otherwise return **filtered data**.

---

### Example: Get Clients by State (Conditional Return)

#### Logic

- If `state` is `NULL` → return all clients
- Else → return clients for the given state

```sql
CREATE PROCEDURE get_clients_by_state(state CHAR(2))
BEGIN
    IF state IS NULL THEN
        SELECT * FROM clients;
    ELSE
        SELECT * FROM clients
        WHERE clients.state = state;
    END IF;
END;
```

✅ **Real-world use**:
Search filters in dashboards where state selection is optional.

---

### Shorthand Version Using IFNULL

```sql
SELECT *
FROM clients c
WHERE c.state = IFNULL(state, c.state);
```

📌 **Explanation**

- If `state` is NULL → `c.state = c.state` (always true)
- Else → filter is applied

✅ Cleaner, faster, and commonly used in production queries.

---

## 2. Filtering Data Using Multiple Optional Parameters

### Example: Filter Payments by Client ID and Payment Method

```sql
CREATE PROCEDURE get_payments_by_id(
    client_id INT,
    payment_method_id TINYINT
)
BEGIN
    SELECT *
    FROM payments p
    WHERE
        p.client_id = IFNULL(client_id, p.client_id)
    AND p.payment_method = IFNULL(payment_method_id, p.payment_method);
END;
```

✅ **Use Case**

- Advanced search forms
- Admin dashboards
- Reports with optional filters

---

## 3. Adding Validation in Stored Procedures

### Why Validation Matters

- Prevent invalid data
- Avoid silent failures
- Protect business rules

---

### Example: Validate Payment Method ID

```sql
IF payment_method_id > 4 THEN
    SIGNAL SQLSTATE '22003'
    SET MESSAGE_TEXT = 'Given payment method ID exceeds allowed range';
END IF;
```

📌 **Use Case**

- Enforce fixed enums (payment methods, status codes)
- Prevent invalid API inputs

---

## 4. OUT Parameters in Stored Procedures

### Concept

Stored procedures can **return multiple values** using `OUT` parameters.

---

### Example: Get Unpaid Invoice Count & Total for a Client

```sql
CREATE PROCEDURE get_unpaid_invoices_for_client(
    client_id INT,
    OUT invoices_count INT,
    OUT invoices_total DECIMAL(9,2)
)
BEGIN
    SELECT COUNT(*), SUM(invoice_total)
    INTO invoices_count, invoices_total
    FROM invoices
    WHERE client_id = client_id AND payment_total = 0;
END;
```

✅ **Use Case**

- Financial summaries
- Invoice dashboards
- Client risk analysis

---

## 5. Using Variables Inside Stored Procedures

### Example: Calculate Overall Risk Factor

```sql
DECLARE risk_factor DECIMAL(9,2) DEFAULT 0;
DECLARE invoices_count INT;
DECLARE invoices_total DECIMAL(9,2);
```

📌 **Explanation**

- `DECLARE` is used inside procedures/functions
- Variables help perform calculations step-by-step

---

### Risk Factor Logic

```sql
risk_factor = (total_invoice_amount / invoice_count) * 5
```

✅ **Use Case**

- Credit scoring
- Fraud detection
- Financial risk metrics

---

## 6. MySQL Functions (Return Single Value Only)

### Key Rules

- Functions return **one value**
- Can be used inside `SELECT`
- Faster for repeated calculations

---

### Function: Risk Factor for a Specific Client

```sql
CREATE FUNCTION get_risk_factor_for_client(client_id INT)
RETURNS INTEGER
READS SQL DATA
BEGIN
    DECLARE risk_factor DECIMAL(9,2);
    DECLARE invoices_count INT;
    DECLARE invoices_total DECIMAL(9,2);

    SELECT COUNT(*), SUM(invoice_total)
    INTO invoices_count, invoices_total
    FROM invoices
    WHERE client_id = client_id;

    SET risk_factor = invoices_total / invoices_count * 5;

    RETURN IFNULL(risk_factor, 0);
END;
```

---

### Using the Function

```sql
SELECT
client_id,
get_risk_factor_for_client(client_id) AS risk_factor
FROM clients;
```

✅ **Use Case**

- Client ranking
- Risk dashboards
- Real-time analytics

---

## 7. Triggers – Automatic Actions on Data Change

### What is a Trigger?

A trigger executes **automatically** when:

- INSERT
- UPDATE
- DELETE occurs

📌 Naming Convention
`tableName_after|before_action`

---

### Example: After Insert Payment → Update Invoice Balance

```sql
CREATE TRIGGER payment_after_insert
AFTER INSERT ON payments
FOR EACH ROW
BEGIN
    UPDATE invoices
    SET payment_total = payment_total + NEW.amount
    WHERE invoice_id = NEW.invoice_id;
END;
```

✅ **Use Case**

- Maintain data consistency
- Remove manual updates
- Ensure business rules

---

### Trigger After Delete Payment

```sql
UPDATE invoices
SET payment_total = payment_total - OLD.amount
WHERE invoice_id = OLD.invoice_id;
```

📌 `NEW` → used with INSERT
📌 `OLD` → used with DELETE

---

## 8. Auditing with Triggers (Tracking User Actions)

### Why Auditing?

- Compliance
- Debugging
- User activity tracking

---

### Audit Table

```sql
CREATE TABLE payments_audit (
    client_id INT,
    date DATE,
    amount DECIMAL(9,2),
    action_type VARCHAR(50),
    action_date DATETIME
);
```

---

### Insert Audit Entry Inside Trigger

```sql
INSERT INTO payments_audit
VALUES (NEW.client_id, NEW.date, NEW.amount, 'Insert', NOW());
```

✅ **Use Case**

- Financial audit trails
- Security monitoring
- Compliance systems

---

## 9. MySQL Events (Scheduled Jobs)

### What is an Event?

A **cron-like job inside MySQL**.

---

### Enable Event Scheduler

```sql
SET GLOBAL event_scheduler = ON;
```

---

### Example: Delete Audit Records Older Than 1 Year

```sql
CREATE EVENT yearly_delete_stale_audit_data
ON SCHEDULE EVERY 1 YEAR
DO
DELETE FROM payments_audit
WHERE action_date < NOW() - INTERVAL 1 YEAR;
```

✅ **Use Case**

- Data cleanup
- Archiving
- Storage optimization

---

## 10. When to Use These Features

| Feature           | Best Use                        |
| ----------------- | ------------------------------- |
| Stored Procedures | Business logic, security, reuse |
| Functions         | Calculations inside SELECT      |
| Triggers          | Auto-sync, audit logs           |
| Events            | Scheduled cleanup jobs          |

⚠️ **Best Practice**
Do NOT overuse these blindly.
Always ask: _“Is this logic better in DB or Application layer?”_

---

# MySQL Advanced Concepts – Transactions, JSON, Data Modeling, Indexing

---

## 1. ACID Properties

**ACID** ensures database reliability:

| Property        | Explanation                                                                                  |
| --------------- | -------------------------------------------------------------------------------------------- |
| **Atomicity**   | Each transaction is a single unit of work. If one step fails, all rollback.                  |
| **Consistency** | Database remains consistent before and after a transaction (e.g., an order must have items). |
| **Isolation**   | Concurrent transactions work independently; one waits for the other.                         |
| **Durability**  | Committed changes are permanent; no data loss.                                               |

---

## 2. Transactions in MySQL

### Create a Transaction

```sql
START TRANSACTION;

INSERT INTO orders(customer_id, order_date, status)
VALUES(1, '2019-01-01', 1);

INSERT INTO order_items
VALUES (LAST_INSERT_ID(), 1, 1, 1);

COMMIT;
```

✅ Use case: Multiple related inserts must succeed together.

---

### Default Behavior

- Every query implicitly executes as a transaction if not explicitly started.
- Use `ROLLBACK` to undo in case of errors.

---

## 3. Concurrency & Isolation Levels

**Concurrency Issues:**

- **Lost Data**: Two users update the same record → one update overrides.
- **Dirty Reads**: Reading uncommitted data from another transaction.
- **Non-Repeating Reads**: Reading the same data twice gives different results.
- **Phantom Reads**: New records appear in a repeated query during a transaction.

**Isolation Levels:**

| Level                | Prevents                                       |
| -------------------- | ---------------------------------------------- |
| **READ UNCOMMITTED** | Nothing                                        |
| **READ COMMITTED**   | Dirty Reads                                    |
| **REPEATABLE READ**  | Lost Updates, Dirty Reads, Non-Repeating Reads |
| **SERIALIZABLE**     | Everything including Phantom Reads             |

---

### Example: Setting Isolation Level

```sql
SET TRANSACTION ISOLATION LEVEL REPEATABLE READ;

START TRANSACTION;

INSERT INTO orders(customer_id, order_date, status)
VALUES(1, '2019-01-01', 1);

INSERT INTO order_items
VALUES (LAST_INSERT_ID(), 1, 1, 1);

ROLLBACK;
```

✅ Default in MySQL is **REPEATABLE READ**.

---

### Deadlocks

- Occurs when two transactions wait for each other → no transaction completes.
- Solution: Optimize queries, access tables in a consistent order.

---

## 4. Data Types Overview

| Type                                          | Description                   |
| --------------------------------------------- | ----------------------------- |
| **DATE / TIME / DATETIME / TIMESTAMP / YEAR** | Dates and times               |
| **TINYBLOB / BLOB / MEDIUMBLOB / LONGBLOB**   | Binary large objects          |
| **JSON**                                      | Store structured JSON objects |

---

### JSON Example

```sql
UPDATE products
SET properties = JSON_OBJECT(
  'weight', 10,
  'dimensions', JSON_ARRAY(1,2,3,4,5),
  'manufacturer', JSON_OBJECT('name','sony')
)
WHERE product_id = 1;
```

#### Query JSON Fields

```sql
SELECT product_id, properties ->> '$.manufacturer.name'
FROM products
WHERE product_id = 1;
```

#### Update JSON Fields

```sql
UPDATE products
SET properties = JSON_SET(properties, '$.weight', 20, '$.age', 10)
WHERE product_id = 1;
```

✅ Use Case: Flexible product attributes, dynamic properties.

---

## 5. Data Modeling Workflow

1. **Understand Requirements**
2. **Conceptual Model** – High-level structure
3. **Logical Model** – Tables, relations
4. **Physical Model** – SQL implementation

**Flow:** Conceptual → Logical → Physical

---

## 6. Creating & Modifying Tables

### Create Customers Table

```sql
CREATE DATABASE IF NOT EXISTS sql_store2;
USE sql_store2;

CREATE TABLE IF NOT EXISTS customers (
  customer_id INT PRIMARY KEY AUTO_INCREMENT,
  first_name VARCHAR(50) NOT NULL,
  points INT NOT NULL DEFAULT 0,
  email VARCHAR(255) NOT NULL UNIQUE
);
```

---

### Modify Existing Table

```sql
ALTER TABLE customers
  ADD last_name VARCHAR(50) NOT NULL AFTER first_name,
  ADD city VARCHAR(50) NOT NULL,
  MODIFY COLUMN first_name VARCHAR(55) DEFAULT '',
  DROP COLUMN points;
```

---

### Create Orders Table with Relation

```sql
CREATE TABLE orders (
  order_id INT PRIMARY KEY,
  customer_id INT NOT NULL,
  FOREIGN KEY fk_orders_customers (customer_id)
    REFERENCES customers(customer_id)
    ON UPDATE CASCADE
    ON DELETE NO ACTION
);
```

---

### Alter Keys

```sql
ALTER TABLE orders
  ADD PRIMARY KEY(order_id),
  DROP PRIMARY KEY,
  DROP FOREIGN KEY fk_orders_customers,
  ADD FOREIGN KEY fk_orders_customers(customer_id)
    REFERENCES customers(customer_id)
    ON UPDATE CASCADE
    ON DELETE NO ACTION;
```

---

## 7. Indexing for Performance

### Why Index?

- Faster queries
- Optimizes `WHERE`, `JOIN`, `ORDER BY` clauses

---

### Example

```sql
CREATE INDEX idx_state ON customers(state);
CREATE INDEX idx_points ON customers(points);
```

- Check query plan:

```sql
EXPLAIN SELECT customer_id FROM customers WHERE state='CA';
```

- Analyze table:

```sql
ANALYZE TABLE customers;
SHOW INDEXES FROM customers;
```

✅ Use Case: Large tables, frequent searches on specific columns.

---

These notes cover:
**Transactions, Isolation, JSON, Data Modeling, Table Design, Indexing** – all essential for building **robust MySQL applications**.

---

# MySQL Indexing Notes

---

## 1. Indexing String Columns

### Create Index on Partial String

- Helps optimize searches on long text columns.
- You can index only the first N characters.

```sql
CREATE INDEX idx_last_name ON customers (last_name(20));
```

### Choosing Optimal Length

```sql
-- Check distribution for optimal length
SELECT
  COUNT(DISTINCT LEFT(last_name, 1)),
  COUNT(DISTINCT LEFT(last_name, 5)),
  COUNT(DISTINCT LEFT(last_name, 10))
FROM customers;
```

✅ Choose length that maximizes uniqueness but keeps index size manageable.

---

## 2. Full-Text Indexing

- Used for searching **keywords in text columns**.
- Supports **normal, boolean, and exact phrase search**.

### Full-Text Search – Normal Mode

```sql
CREATE FULLTEXT INDEX idx_title_body ON posts (title, body);

SELECT *, MATCH(title, body) AGAINST('react redux') AS relevancy_score
FROM posts
WHERE MATCH(title, body) AGAINST('react redux');
```

### Full-Text Search – Boolean Mode

```sql
SELECT *, MATCH(title, body) AGAINST('react -redux +form' IN BOOLEAN MODE) AS relevancy_score
FROM posts;
```

### Full-Text Search – Exact Phrase

```sql
SELECT *, MATCH(title, body) AGAINST('"handling form"' IN BOOLEAN MODE) AS relevancy_score
FROM posts;
```

✅ Use Case: Blogs, posts, product descriptions, or any textual content search.

---

## 3. Composite Indexing

- Combines **multiple columns into a single index**.
- Reduces query time when filtering on multiple columns.

### Check Existing Indexes

```sql
USE sql_store;
SHOW INDEXES IN customers;
```

### Normal Index Limitation

- Only **one single-column index** can be used per query.
- Composite indexes optimize queries with **multiple columns**.

---

### Create Composite Index

```sql
CREATE INDEX idx_state_points ON customers (state, points);

EXPLAIN SELECT *
FROM customers
WHERE state = 'CA' AND points > 1000;
```

### Rules for Column Order in Composite Index

1. Place **frequently used columns first**.
2. Place **high-cardinality columns first**.
3. Consider **query patterns** (WHERE, ORDER BY, JOIN).

---

### Choosing the Best Index

```sql
-- Different index options
CREATE INDEX idx_state_lastname ON customers (state, last_name);
CREATE INDEX idx_lastname_state ON customers (last_name, state);

EXPLAIN SELECT *
FROM customers
USE INDEX (idx_state_lastname)
WHERE state = 'CA' AND last_name LIKE 'a%';
```

✅ Inspect `EXPLAIN` output to see which index performs better.

---

### Drop Index

```sql
DROP INDEX idx_state_point ON customers;
DROP INDEX idx_lastname_state ON customers;
```

---

### Key Takeaways

- Use **partial indexing** for long string columns.
- Use **full-text indexing** for searching text content efficiently.
- Use **composite indexes** for queries with multiple filter columns.
- Always **check query plan with `EXPLAIN`** to optimize performance.
- Column order in indexes matters for query efficiency.

---
