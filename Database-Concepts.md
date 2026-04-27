# Database Design Core Concepts

## First: Requirements Analysis
- Compile user requirements
- Analyze business processes
- Identify entities
- Identify relationships
- Identify constraints
- Identify use cases
- Identify temporal scenarios (Workflow / Sequence)
- Identify required reports
- Identify inputs + outputs
- Define business rules

## Second: Conceptual Design
- Entity Relationship Diagram (ERD)
- Entities
- Attributes
- Primary Keys
- Relationships
    - One-to-One
    - One-to-Many
    - Many-to-Many
- Cardinality
- Conceptual Constraints
- Enhanced ERD (EERD)
- Generalization / Specialization
- Aggregation
- Composition

## Third: Logical Design
- Transform ERD to table structuring
- Define logical data types
- Define primary keys
- Define foreign keys
- Define indexing strategy (logical)
- Relationship mapping
- Derived attributes
- Rules & Constraints
    - NOT NULL
    - UNIQUE
    - CHECK
    - DEFAULT
    - DOMAIN rules
- Normalization
    - 1NF, 2NF, 3NF, BCNF, 4NF, 5NF
- Handle many-to-many relationships
- Handle weak entities

## Fourth: Physical Design
- Define physical data types
- Create table structures
- Design indexes
    - Clustered
    - Non-Clustered
    - Unique
    - Composite
- Design filegroups (e.g., SQL Server)
- Partitioning
- Design storage parameters
- Materialized views
- Triggers
- Stored Procedures
- Functions
- Views
- Sequences / Identity
- Security Design
    - Users, Roles, Permissions
- Backup strategy design
    - Full, Differential, Log
- Index maintenance plan
- Design for performance
    - Query optimization, Index tuning, Caching considerations
- Implement physical constraints

## Fifth: Supporting Components
- Data Dictionary
- Metadata Documentation
- Naming convention standards
- Version control for the database
- Database coding standards
- ERD documentation + description
- Data Flow Diagrams
- Business Process Modeling (BPMN)
- Security & compliance requirements
    - GDPR, HIPAA, PCI-DSS
- High availability design
    - Replication, Mirroring, Clustering
- Disaster Recovery Plan

## Sixth: Quality & Testing Components
- Data quality rules
- Test cases for data / queries
- Performance testing
- Stress testing
- Load testing
- Validation rules
- Referential integrity testing

## Seventh: Maintenance & Operations Plan
- Monitoring plan
- Logging
- Auditing
- Performance baseline
- Capacity planning
- Archiving strategy
- Index maintenance
- Backup/restore testing

---

# 10 Schemas × 10 Tables Each (100 Total Tables)

## Schema 1: core
1. **core.SystemConfig** - ConfigId (PK, INT), Key (VARCHAR100, UNIQUE), Value (NVARCHAR500)
2. **core.AppVersion** - VersionId (PK), VersionNumber, ReleasedAt
3. **core.Notification** - NotificationId (PK), Title, Message, CreatedAt
4. **core.ErrorLog** - ErrorId (PK), Message, StackTrace, CreatedAt
5. **core.JobQueue** - JobId (PK), JobType, Payload, Status
6. **core.SchedulerTask** - TaskId (PK), CronExpression, LastRunAt
7. **core.FileStorage** - FileId (PK), FileName, MIME, Path
8. **core.EmailTemplate** - TemplateId (PK), Code, Subject, Body
9. **core.Tag** - TagId (PK), Name, CreatedAt
10. **core.TagMapping** - MappingId (PK), TagId (FK), ObjectName, ObjectId

## Schema 2: identity
1. **identity.UserAccount** - UserId (PK), Username (UNIQUE), Email (UNIQUE)
2. **identity.UserProfile** - UserId (PK, FK), FirstName, LastName, BirthDate
3. **identity.Role** - RoleId (PK), RoleName (UNIQUE)
4. **identity.UserRole** - UserRoleId, UserId (FK), RoleId (FK)
5. **identity.Permission** - PermissionId, Key (UNIQUE)
6. **identity.RolePermission** - RolePermissionId, RoleId (FK), PermissionId (FK)
7. **identity.LoginHistory** - LoginId, UserId, IP, LoggedAt
8. **identity.PasswordReset** - ResetId, UserId, Token, ExpireAt
9. **identity.Session** - SessionId, UserId, Device, ExpiresAt
10. **identity.TwoFactor** - TwoFactorId, UserId, SecretKey, Enabled

## Schema 3: location
1. location.Country
2. location.State
3. location.City
4. location.District
5. location.Neighborhood
6. location.Currency
7. location.Language
8. location.TimeZone
9. location.Address
10. location.AddressType
(Each includes PK + Name + Code fields + FK relations where needed.)

## Schema 4: catalog
1. catalog.Product
2. catalog.ProductVariant
3. catalog.Category
4. catalog.ProductCategory
5. catalog.Brand
6. catalog.Attribute
7. catalog.AttributeValue
8. catalog.ProductAttribute
9. catalog.Review
10. catalog.Media
(Full fields include ProductId, Name, SKU, Price, etc.)

## Schema 5: finance
1. finance.Invoice
2. finance.InvoiceItem
3. finance.Payment
4. finance.Refund
5. finance.Tax
6. finance.CurrencyRate
7. finance.Wallet
8. finance.WalletTransaction
9. finance.Subscription
10. finance.SubscriptionPlan

## Schema 6: logistics
1. logistics.Warehouse
2. logistics.Inventory
3. logistics.StockMovement
4. logistics.Shipment
5. logistics.ShipmentItem
6. logistics.Carrier
7. logistics.DeliveryStatus
8. logistics.Package
9. logistics.Route
10. logistics.Vehicle

## Schema 7: analytics
1. analytics.Metric
2. analytics.MetricDaily
3. analytics.MetricHourly
4. analytics.Report
5. analytics.FeatureUsage
6. analytics.EventLog
7. analytics.UserEngagement
8. analytics.RetentionCohort
9. analytics.ForecastModel
10. analytics.ForecastResult

## Schema 8: audit
1. audit.AuditLog
2. audit.ChangeLog
3. audit.DataSnapshot
4. audit.EntityVersion
5. audit.LoginAttempt
6. audit.ApiAudit
7. audit.PermissionAudit
8. audit.BatchJobAudit
9. audit.EmailAudit
10. audit.SystemEvent

## Schema 9: integration
1. integration.ApiLog
2. integration.Webhook
3. integration.WebhookEvent
4. integration.IntegrationProvider
5. integration.ProviderConfig
6. integration.ImportJob
7. integration.ImportError
8. integration.ExportJob
9. integration.QueueMessage
10. integration.SyncHistory

## Schema 10: settings
1. settings.FeatureToggle
2. settings.AppSetting
3. settings.Theme
4. settings.LanguageSetting
5. settings.NotificationSetting
6. settings.SecuritySetting
7. settings.ApiKey
8. settings.ApiKeyPermission
9. settings.SystemRule
10. settings.WorkflowConfig

---

# SQL Core Topics for Querying and Analysis

## SQL Proficiency Levels

### Strong SQL Proficiency Means:
- Writing complex queries
- Analyzing data and extracting insights
- Filtering, sorting, joining, grouping, aggregation
- Subqueries, window functions, CTEs

### SQL for Data Analysis Includes:
- Sales analysis
- Time-period comparison
- Averages and growth rates
- Pattern detection
- Data quality handling
- Report building

## Stage 1 – Fundamentals
- SELECT, FROM, WHERE, ORDER BY, DISTINCT
- String, numeric, date functions
- Type conversion, NULL handling
- INNER JOIN, LEFT JOIN, RIGHT JOIN, FULL JOIN, SELF JOIN
- GROUP BY, HAVING, aggregate functions

## Stage 2 – Advanced Querying
- Subqueries
- CTEs (Common Table Expressions)
- Window functions (OVER, ROW_NUMBER, RANK, PARTITION BY)
- Pivot and unpivot
- Temporary tables, Views
- Index basics, execution plan basics

## Stage 3 – Data Analysis
- Time-series analysis (monthly growth, trend analysis, running totals)
- Sales analytics, customer segmentation, inventory analysis, HR analytics
- Removing duplicates, fixing inconsistent values, standardizing strings, validating data formats

## Practice Levels
1. Basic querying
2. Joins
3. Aggregations
4. Advanced SQL (ROW_NUMBER, window functions, CTE cleaning)
5. Data analysis queries

## Learning Plan (4 Weeks)
- Week 1: SQL foundations (Select, Where, Joins, Group By)
- Week 2: Functions, Aggregations, Subqueries
- Week 3: CTEs, Window Functions, Data Cleaning
- Week 4: Data Analysis with SQL and mini projects

## Mini Projects
- Sales analysis dashboard
- HR analytics
- E-commerce data analysis

---

# SQL Data Modification & Querying Details

## Data Modification Basics
- INSERT INTO (data insertion)
- SELECT (data retrieval)
- UPDATE (data modification)
- DELETE (data removal)

## Selecting Data
- Selecting all data (rows & columns)
- Selecting specific columns
- Column aliases (renaming output)
- Arithmetic operations in SELECT
- NULL handling
- String concatenation and data formatting
- Using arithmetic, string, numeric, date functions in SELECT
- Data type conversion (CAST & CONVERT)
- Rounding, floor, ceiling functions

## Filtering Data
- Comparison operators (=, >, <, LIKE)
- LIKE, IN, NOT IN, BETWEEN
- Logical operators (AND, OR, NOT)

## Grouping and Sorting
- Basic functions (COUNT, SUM, AVG, MIN, MAX)
- GROUP BY, HAVING
- ORDER BY (ASC/DESC, multiple columns, expressions)
- LIMIT results (TOP, OFFSET...FETCH, LIMIT)
- DISTINCT (single and multiple columns)

## Calculated Columns
- Arithmetic inside SELECT (e.g., Price * 1.15 AS PriceWithTax)
- String concatenation
- CASE expressions (conditional logic)

## Joins
- INNER, LEFT, RIGHT, FULL, CROSS, SELF JOIN
- Multi-table queries

## Advanced Querying
- Subqueries (inside SELECT, FROM, WHERE)
- Nested queries
- Common Table Expressions (WITH clause)
- Window functions (OVER, PARTITION BY, ROW_NUMBER, RANK, DENSE_RANK)
- CASE statements
- UNION vs UNION ALL
- INTERSECT and EXCEPT
- Views (CREATE VIEW)
- Stored procedures
- Transactions (BEGIN, COMMIT, ROLLBACK)
- Error handling

---

# Age Category Reference Table

| Category | Age Range | Conditions / Rules |
| :--- | :--- | :--- |
| Child | 0–12 | Must be ≤12; cannot be employed; requires guardian info. |
| Teenager | 13–17 | Age 13–17; limited permissions; cannot sign contracts; not eligible for full-time employment. |
| Young Adult | 18–24 | Age 18–24; eligible for full-time work; usually entry-level roles. |
| Adult | 25–59 | Age 25–59; fully eligible for employment; suitable for any job level. |
| Senior | 60+ | Age ≥60; may qualify for retirement; may shift to part-time or special roles. |

## Lookup Values
- **Marital Status:** 1 – Single, 2 – Married, 3 – Divorced, 4 – Widowed
- **Gender:** 1 – Male, 2 – Female, 3 – Other
- **Blood Type:** 1 – A+, 2 – A−, 3 – B+, 4 – B−, 5 – AB+, 6 – AB−, 7 – O+, 8 – O−
- **Status:** 0 – Inactive, 1 – Active

---

# SQL Function Types

## Scalar Functions (Return one value per input row)
- **String:** LEN(), UPPER(), LOWER(), SUBSTRING(), REPLACE()
- **Numeric:** ABS(), ROUND(), CEILING(), FLOOR(), POWER()
- **Date:** GETDATE(), DATEADD(), DATEDIFF(), DATEPART()
- **Conversion:** CAST(), CONVERT(), PARSE()
- **Null-handling:** ISNULL(), COALESCE(), NULLIF()

## Aggregate Functions (Return one result per group)
- COUNT(), SUM(), AVG(), MAX(), MIN()

## Mathematical Functions
- SQRT(), POWER(), RAND(), SIGN()

## Conditional Functions
- CASE, IIF() (SQL Server), CHOOSE() (SQL Server), DECODE() (Oracle)

---

# Concatenation & Output Formatting in SQL

## Basic Concatenation
- `+` operator
- `CONCAT()` function
- `CONCAT_WS()` function

## Handling NULLs
- `ISNULL()`, `COALESCE()`
- Behavior of `+` vs `CONCAT()` with NULL

## Formatting Techniques
- Adding spaces, commas, separators
- Using `CONCAT_WS(separator, …)`
- Manual formatting inside `CONCAT`

## Type Conversion for Formatting
- `CAST()`, `CONVERT()`
- Formatting numbers as strings
- Formatting date/time values

## Date Formatting
- `FORMAT(date, format-pattern, culture)`
- `CONVERT(varchar, date, style)`
- `DATENAME()`, `DATEPART()` for custom formats

## Numeric Formatting
- `FORMAT(number, pattern)`
- Rounding or padding numbers before concatenation

## Conditional Formatting
- Using `CASE` inside concatenation
- Building dynamic strings (e.g., “Status: Active”)

## Building Complex Text Output
- Full name formatting
- Address formatting
- JSON-style or CSV-style formatting

## Whitespace Cleanup
- `LTRIM()`, `RTRIM()`, `TRIM()`
- Removing unwanted spaces in concatenated results

## Special Formatting Functions
- `STRING_AGG()` for grouped concatenation (with delimiter and ordering)

---

# Data Definition Language (DDL) Topics

## Database Object
- Create, drop, rename database
- Change collation, set options (READ_ONLY, AUTO_CLOSE, RECOVERY MODEL)
- Set compatibility level, metadata
- Configure filegroups, add data/log files
- Move database files (MDF/LDF)
- Set database owner
- Backup and restore database
- Assign database permissions (GRANT/REVOKE/DENY)
- Containment settings, encryption (TDE)
- Create/drop database snapshots

## Schema Object
- Create, drop, rename schema
- Transfer objects to another schema (ALTER SCHEMA TRANSFER)
- Create multiple schemas for a system
- Assign permissions for schema
- Ownership of a schema (ALTER AUTHORIZATION)

## Table Object
- Create, drop, rename, truncate table
- SELECT INTO (CTAS)
- Copy table structure only
- Alter table (add/modify/drop columns)
- Add/drop constraints (PK, FK, UNIQUE, CHECK)
- Change table lock settings, options (compression, filegroup)
- View table structure (INFORMATION_SCHEMA / sys.tables)
- Temporal tables (system-versioned)
- Memory-optimized tables, FileTable
- Partitioning tables
- Move a table to a different filegroup

## Columns
- Add, drop, rename column
- Change datatype
- Set default values
- Add/remove constraints
- Set identity property (or remove via SWAP/recreate)
- Sparse columns, masked columns (dynamic data masking)
- Computed columns (persisted or non-persisted)
- Column collation override, nullability change

## Keys
- **Primary Key:** Create in table definition, add after creation, drop, composite keys, identity columns as PK
- **Unique Key:** Define in table, add later, drop
- **Foreign Key:** Create, add ON DELETE/ON UPDATE rules, disable/enable, drop, check existing relationships
- **Composite Keys:** Keys made from multiple columns

## Constraints
- **Types:** NOT NULL, DEFAULT, UNIQUE, CHECK, PRIMARY KEY, FOREIGN KEY
- **Operations:** Add, drop, rename, disable/enable, view (sys.constraints), named constraints

## Triggers
- Create triggers (BEFORE/AFTER INSERT, UPDATE, DELETE)
- Use trigger variables (e.g., NEW, OLD)
- Drop, list, disable, enable triggers
- Use triggers for logging, validation, auditing

## Indexes
- Create (unique, filtered, composite, clustered, non-clustered, columnstore, XML, full-text, spatial)
- Drop, rebuild, reorganize, disable, enable index
- Move index to another filegroup
- Check index usage (DMVs, execution plan)
- Index fragmentation analysis and maintenance

## Views
- Create view, create WITH SCHEMABINDING, create indexed view
- Drop, alter, rename view
- Encryption of view definition
- View dependencies (sys.sql_dependencies)

## Stored Procedures
- Create, alter, drop, rename
- Create parameterized, encrypted, temporary procedures
- Use OUTPUT parameters, table-valued parameters
- View SP dependencies

## Functions
- **Types:** Scalar functions, inline table-valued functions, multi-statement table-valued functions
- **Operations:** Create, alter, drop, rename, create encrypted function, view function dependencies

## Synonyms
- Create synonym, drop synonym
- Use synonyms to reference remote objects

## Sequences
- Create, drop, alter sequence
- Restart sequence, use NEXT VALUE FOR
- Bind sequence to a table column

## User-Defined Types
- Table types (CREATE TYPE tableType AS TABLE)
- Scalar UDT, drop a type

## Security Objects
- Create login, user, map login to user, drop login/user
- Change password
- Grant, revoke, deny permissions
- Create roles, assign users to roles
- Row-level security, dynamic data masking, always encrypted
- Certificates, keys (Database Master Key, Private Keys)

## Full-Text Search
- Create full-text catalog, full-text index
- Drop or alter full-text index

## Partitioning
- Create partition function, partition scheme, partitioned table
- Split or merge partition

## Service Broker
- Message types, contracts, queues, services, routes

## SQL Agent Job
- Create job, drop job, create schedules, create job steps

## DDL Tracing & Auditing
- CREATE EVENT SESSION
- SQL Audit, database audit specification