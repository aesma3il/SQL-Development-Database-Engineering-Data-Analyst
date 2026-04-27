# SQL Coding Standards

## 1. Naming Conventions

### Database Objects
- Database names: PascalCase or snake_case (e.g., SalesDB, sales_db)
- Schema names: lowercase snake_case (e.g., sales, hr, inventory)
- Table names: plural PascalCase or singular snake_case (e.g., Customers, customer)
- Column names: lowercase snake_case (e.g., first_name, order_date)
- Primary key: id or tablename_id (e.g., customer_id)
- Foreign key: referencing_table_id (e.g., customer_id)

### Constraints
- Primary key: pk_table_name or tablename_pkey
- Foreign key: fk_table_name_ref_table
- Unique constraint: uq_table_name_column
- Check constraint: chk_table_name_condition
- Default constraint: df_table_name_column

### Indexes
- Non-clustered index: ix_table_name_column
- Unique index: ux_table_name_column
- Clustered index: cx_table_name_column
- Full-text index: ft_table_name_column

### Programmability
- Stored procedures: usp_ActionName or sp_action_name
- Functions: ufn_FunctionName or fn_calculate_total
- Triggers: trg_table_name_action (e.g., trg_orders_after_insert)
- Views: vw_EntityName or vw_action_name

## 2. Formatting Rules

### Indentation
- Use 4 spaces per indentation level (no tabs)
- Indent JOIN conditions one level
- Indent WHERE clause conditions one level
- Indent subqueries one level

### Line Breaks
- Place each major clause on a new line (SELECT, FROM, WHERE, GROUP BY, HAVING, ORDER BY)
- Place each column in SELECT on a new line
- Place each condition in WHERE on a new line
- Place each JOIN on a new line

### Capitalization
- SQL keywords: UPPERCASE (SELECT, INSERT, UPDATE, DELETE, FROM, WHERE, JOIN)
- Data types: UPPERCASE (INT, VARCHAR, DATE, DECIMAL)
- Function names: UPPERCASE (COUNT, SUM, COALESCE, NULLIF)
- Table and column names: lowercase
- Aliases: lowercase or meaningful abbreviation

## 3. Query Writing Standards

### SELECT Statements
```sql
-- Good
SELECT 
    c.customer_id,
    c.first_name,
    c.last_name,
    COALESCE(o.order_total, 0) AS total_spent
FROM customers c
LEFT JOIN orders o ON c.customer_id = o.customer_id
WHERE c.status = 'active'
    AND c.created_date >= '2024-01-01'
ORDER BY c.last_name ASC;

-- Bad
select c.customer_id,c.first_name, c.last_name,COALESCE(o.order_total,0) as total_spent from customers c left join orders o on c.customer_id=o.customer_id where c.status='active' order by c.last_name;