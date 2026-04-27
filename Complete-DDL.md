# Complete DDL (Data Definition Language) Course Material

## Course Overview
This course covers all Data Definition Language commands and concepts used to create, modify, and manage database structures including databases, schemas, tables, constraints, indexes, views, and other database objects.

---

## Module 1: Introduction to DDL

### 1.1 What is DDL?
- Definition and purpose of Data Definition Language
- DDL vs DML vs DCL vs TCL
- Automatic commit behavior in DDL
- DDL statements: CREATE, ALTER, DROP, TRUNCATE, RENAME

### 1.2 Database Architecture Fundamentals
- Three-level architecture (External, Conceptual, Internal)
- Data independence (Logical and Physical)
- System catalog / Data dictionary

---

## Module 2: Database-Level DDL

### 2.1 Creating Databases
- CREATE DATABASE syntax
- Specifying file locations (MDF, NDF, LDF)
- Setting initial size and auto-growth parameters
- Database collation settings

### 2.2 Modifying Databases
- ALTER DATABASE commands
- Adding and removing data files
- Adding and removing log files
- Changing database options (READ_ONLY, AUTO_CLOSE, RECOVERY MODEL)
- Setting compatibility level
- Changing database owner

### 2.3 Database Configuration
- Filegroups and tablespaces
- Adding filegroups
- Setting default filegroup
- Memory-optimized filegroups

### 2.4 Removing Databases
- DROP DATABASE syntax
- Handling active connections before drop
- Dropping multiple databases

### 2.5 Database Properties and Settings
- Setting database options
- Database collation
- Recovery models (Full, Bulk-Logged, Simple)
- Containment settings
- Encryption (TDE - Transparent Data Encryption)

### 2.6 Database Snapshots
- Creating database snapshots
- Using snapshots for reporting
- Reverting from snapshot

---

## Module 3: Schema-Level DDL

### 3.1 Understanding Schemas
- What is a database schema?
- Schema as a logical container
- Default schemas (dbo, sys, INFORMATION_SCHEMA)

### 3.2 Creating Schemas
- CREATE SCHEMA syntax
- Setting schema owner
- Creating objects within a schema

### 3.3 Modifying Schemas
- ALTER SCHEMA for transferring objects
- Changing schema ownership (ALTER AUTHORIZATION)

### 3.4 Dropping Schemas
- DROP SCHEMA requirements
- Moving objects before dropping schema

### 3.5 Schema Design Best Practices
- Logical grouping of objects
- Multi-schema architecture
- Permission management at schema level

---

## Module 4: Table-Level DDL

### 4.1 Creating Tables
- CREATE TABLE syntax
- Defining columns and data types
- Adding constraints inline and out-of-line

### 4.2 Table Creation Methods
- Standard table creation
- CREATE TABLE AS SELECT (CTAS) / SELECT INTO
- Creating empty copy of existing table
- Creating temporary tables (local and global)
- Creating memory-optimized tables
- Creating system-versioned temporal tables

### 4.3 Table Types
- Regular (heap) tables
- Clustered tables
- Temporary tables (#temp and ##temp)
- Table variables
- External tables
- Partitioned tables
- FileTables (SQL Server)

### 4.4 Modifying Tables
- ALTER TABLE syntax
- Adding new columns
- Dropping existing columns
- Modifying column data types
- Renaming columns
- Changing column nullability
- Adding constraints
- Dropping constraints
- Enabling/disabling constraints

### 4.5 Table Properties and Options
- Compression settings (ROW, PAGE)
- Filegroup placement
- Lock escalation settings
- Change tracking settings

### 4.6 Removing Data vs Removing Structure
- DELETE vs TRUNCATE vs DROP
- TRUNCATE TABLE (fast deletion, resets identity)
- DROP TABLE (removes structure and data)
- Difference between TRUNCATE and DELETE

### 4.7 Renaming Objects
- RENAME statement
- Using sp_rename (SQL Server)
- Renaming tables and columns

### 4.8 Temporal Tables
- System-versioned temporal tables
- PERIOD FOR SYSTEM_TIME
- History tables
- Querying temporal data (FOR SYSTEM_TIME)

---

## Module 5: Column-Level DDL

### 5.1 Data Types Overview
- Numeric types (INT, BIGINT, DECIMAL, FLOAT, MONEY)
- Character types (CHAR, VARCHAR, TEXT, NCHAR, NVARCHAR)
- Date and time types (DATE, TIME, DATETIME, TIMESTAMP)
- Binary types (BINARY, VARBINARY, BLOB)
- Other types (XML, JSON, GEOGRAPHY, HIERARCHYID)

### 5.2 Column Properties
- NULL and NOT NULL
- DEFAULT values
- IDENTITY / AUTO_INCREMENT properties
- SEQUENCE vs IDENTITY
- Computed columns
- Persisted computed columns
- Sparse columns
- Masked columns (Dynamic Data Masking)

### 5.3 Column Modifications
- Adding new columns
- Dropping columns
- Changing data types
- Adding/dropping DEFAULT constraints
- Setting/resetting IDENTITY seed
- Adding/dropping computed columns

### 5.4 Special Column Types
- RowVersion / Timestamp columns
- UniqueIdentifier (GUID) columns
- HierarchyID columns
- Spatial columns (GEOMETRY, GEOGRAPHY)

---

## Module 6: Constraint DDL

### 6.1 Types of Constraints
- NOT NULL constraint
- UNIQUE constraint
- PRIMARY KEY constraint
- FOREIGN KEY constraint
- CHECK constraint
- DEFAULT constraint

### 6.2 Creating Constraints
- Inline constraint definition (at column level)
- Out-of-line constraint definition (at table level)
- Named vs unnamed constraints
- Creating composite primary keys
- Creating composite unique constraints

### 6.3 Foreign Key Constraints
- Referential integrity
- ON DELETE actions (NO ACTION, CASCADE, SET NULL, SET DEFAULT)
- ON UPDATE actions
- Self-referencing foreign keys
- Circular references

### 6.4 Check Constraints
- Creating CHECK constraints with expressions
- Multiple conditions in one CHECK
- Domain constraints using CHECK

### 6.5 Managing Constraints
- Adding constraints to existing tables
- Dropping constraints
- Renaming constraints
- Disabling and enabling constraints
- Disabling constraints for bulk operations
- Checking existing data before adding constraints

### 6.6 Constraint Metadata
- Querying constraint information
- INFORMATION_SCHEMA views for constraints
- System catalog views

---

## Module 7: Index DDL

### 7.1 Introduction to Indexes
- What are indexes?
- Clustered vs Non-clustered indexes
- Index key columns
- Included columns

### 7.2 Creating Indexes
- CREATE INDEX syntax
- Creating clustered indexes
- Creating non-clustered indexes
- Creating unique indexes
- Creating composite indexes

### 7.3 Special Index Types
- Filtered indexes (partial indexes)
- Columnstore indexes (clustered and non-clustered)
- XML indexes (primary and secondary)
- Full-text indexes
- Spatial indexes
- Hash indexes

### 7.4 Managing Indexes
- ALTER INDEX commands
- Disabling indexes
- Enabling indexes
- Rebuilding indexes
- Reorganizing indexes
- Moving indexes to different filegroups

### 7.5 Dropping Indexes
- DROP INDEX syntax
- Dropping primary key constraints (drops clustered index)
- Dropping unique constraints

### 7.6 Index Options
- FILLFACTOR setting
- PAD_INDEX option
- SORT_IN_TEMPDB
- STATISTICS_NORECOMPUTE
- DROP_EXISTING (for index recreation)
- ONLINE vs OFFLINE index operations

---

## Module 8: View DDL

### 8.1 Creating Views
- CREATE VIEW syntax
- Simple views (single table)
- Complex views (multiple tables with JOINs)
- Views with WITH CHECK OPTION

### 8.2 View Options
- WITH ENCRYPTION (hiding view definition)
- WITH SCHEMABINDING (preventing underlying table changes)
- WITH VIEW_METADATA

### 8.3 Indexed Views (Materialized Views)
- Requirements for indexed views
- Creating unique clustered index on view
- Creating additional non-clustered indexes
- When to use indexed views

### 8.4 Partitioned Views
- Creating partitioned views with UNION ALL
- Distributed partitioned views

### 8.5 Managing Views
- ALTER VIEW (modifying view definition)
- DROP VIEW
- Renaming views
- View dependencies

### 8.6 Updatable Views
- Conditions for updating through views
- Using INSTEAD OF triggers for complex updates

---

## Module 9: Stored Procedure DDL

### 9.1 Creating Stored Procedures
- CREATE PROCEDURE syntax
- Creating parameterized procedures
- Default parameter values
- OUTPUT parameters

### 9.2 Procedure Types
- Regular stored procedures
- Temporary stored procedures (local and global)
- System stored procedures
- Extended stored procedures
- CLR stored procedures

### 9.3 Procedure Options
- WITH ENCRYPTION
- WITH RECOMPILE (for different execution plans)
- EXECUTE AS (setting execution context)

### 9.4 Managing Procedures
- ALTER PROCEDURE
- DROP PROCEDURE
- Renaming procedures
- Viewing procedure definitions

---

## Module 10: Function DDL

### 10.1 Types of Functions
- Scalar functions (return single value)
- Inline table-valued functions (return table)
- Multi-statement table-valued functions

### 10.2 Creating Functions
- CREATE FUNCTION syntax for each type
- Function parameters (input only, no OUTPUT)
- RETURN clause
- BEGIN...END block for multi-statement functions

### 10.3 Function Options
- WITH SCHEMABINDING
- WITH ENCRYPTION
- RETURNS NULL ON NULL INPUT
- CALLED ON NULL INPUT

### 10.4 Managing Functions
- ALTER FUNCTION
- DROP FUNCTION
- Function determinism (DETERMINISTIC / NOT DETERMINISTIC)

---

## Module 11: Trigger DDL

### 11.1 Trigger Types
- DML Triggers (AFTER, INSTEAD OF, BEFORE)
- DDL Triggers (for database/server events)
- LOGON Triggers

### 11.2 Creating DML Triggers
- CREATE TRIGGER syntax
- AFTER INSERT triggers
- AFTER UPDATE triggers
- AFTER DELETE triggers
- INSTEAD OF triggers
- Trigger order specification (sp_settriggerorder)

### 11.3 Using Special Tables
- inserted table (new values)
- deleted table (old values)
- UPDATE() function (checking specific columns)

### 11.4 DDL Triggers
- Creating database-scoped DDL triggers
- Creating server-scoped DDL triggers
- Trigger event types (CREATE_TABLE, ALTER_TABLE, DROP_TABLE, etc.)

### 11.5 Managing Triggers
- ALTER TRIGGER
- DROP TRIGGER
- Disabling triggers
- Enabling triggers
- Viewing trigger information
- Nested triggers and recursive triggers settings

---

## Module 12: Sequence DDL

### 12.1 Creating Sequences
- CREATE SEQUENCE syntax
- Defining START WITH value
- Setting INCREMENT BY
- MINVALUE and MAXVALUE
- CYCLE / NO CYCLE
- CACHE size

### 12.2 Using Sequences
- NEXT VALUE FOR function
- Using sequences in DEFAULT constraints
- Using sequences in INSERT statements

### 12.3 Managing Sequences
- ALTER SEQUENCE
- Restarting sequences
- Changing sequence properties
- DROP SEQUENCE

---

## Module 13: Synonym DDL

### 13.1 Creating Synonyms
- CREATE SYNONYM syntax
- Synonyms for local objects (tables, views, procedures, functions)
- Synonyms for remote objects (linked servers)

### 13.2 Managing Synonyms
- DROP SYNONYM
- Synonym use cases (abstraction, migration, simplification)

---

## Module 14: User-Defined Types (UDT) DDL

### 14.1 Creating User-Defined Types
- CREATE TYPE from base types (SQL Server)
- CREATE TYPE AS TABLE (table types)
- User-defined CLR types

### 14.2 Using UDTs
- Using UDTs as column data types
- Using table-valued parameters

### 14.3 Managing UDTs
- Dropping UDTs
- Dependency checking

---

## Module 15: Partition DDL

### 15.1 Partition Functions
- CREATE PARTITION FUNCTION
- RANGE LEFT vs RANGE RIGHT
- Defining boundary values

### 15.2 Partition Schemes
- CREATE PARTITION SCHEME
- Mapping partitions to filegroups
- ALL TO (single filegroup) vs multiple mappings

### 15.3 Creating Partitioned Tables
- Creating tables on partition scheme
- Adding constraints to partitioned tables

### 15.4 Managing Partitions
- ALTER PARTITION FUNCTION (SPLIT, MERGE)
- Switching partitions (ALTER TABLE SWITCH)
- Partition metadata queries

---

## Module 16: Security DDL

### 16.1 Login Management
- CREATE LOGIN syntax
- Windows authentication vs SQL Server authentication
- Password policies
- DROP LOGIN
- ALTER LOGIN (enable, disable, change password)

### 16.2 User Management
- CREATE USER syntax
- Mapping users to logins
- Creating users without logins (contained databases)
- DROP USER
- ALTER USER (default schema, name change)

### 16.3 Role Management
- CREATE ROLE
- Fixed server roles (sysadmin, dbcreator, etc.)
- Fixed database roles (db_owner, db_datareader, etc.)
- User-defined database roles
- Application roles
- ALTER ROLE (adding/dropping members)
- DROP ROLE

### 16.4 Permission Management
- GRANT statement
- REVOKE statement
- DENY statement
- Permission hierarchy (server, database, schema, object)
- Permission types (SELECT, INSERT, UPDATE, DELETE, EXECUTE, REFERENCES, etc.)

### 16.5 Security Features
- CREATE CERTIFICATE
- CREATE MASTER KEY
- Row-Level Security (security policies)
- Dynamic Data Masking (ALTER TABLE ... ADD MASKED WITH)

---

## Module 17: Full-Text Search DDL

### 17.1 Full-Text Catalog
- CREATE FULLTEXT CATALOG
- ALTER FULLTEXT CATALOG (rebuild, reorganize)
- DROP FULLTEXT CATALOG

### 17.2 Full-Text Index
- CREATE FULLTEXT INDEX
- Specifying language and stoplists
- Change tracking settings (AUTO, MANUAL, OFF)
- ALTER FULLTEXT INDEX
- DROP FULLTEXT INDEX

---

## Module 18: Service Broker DDL (SQL Server)

### 18.1 Message Types
- CREATE MESSAGE TYPE
- Validation options (NONE, EMPTY, WELL_FORMED_XML, VALID_XML)

### 18.2 Contracts
- CREATE CONTRACT
- Specifying message types and directions

### 18.3 Queues
- CREATE QUEUE
- Queue retention and status
- Activation stored procedures

### 18.4 Services
- CREATE SERVICE
- Binding services to contracts
- DROP SERVICE, DROP QUEUE, DROP CONTRACT, DROP MESSAGE TYPE

---

## Module 19: DDL Best Practices

### 19.1 Naming Conventions
- Database naming standards
- Schema naming standards
- Table naming standards (singular vs plural)
- Column naming standards
- Constraint naming standards (PK_, FK_, UQ_, CK_, DF_)
- Index naming standards (IX_, UX_, CX_)

### 19.2 Documentation
- Using extended properties (sp_addextendedproperty)
- Documenting object purposes and business rules
- Maintaining data dictionary

### 19.3 Change Management
- Version control for DDL scripts
- Migration scripts (UP and DOWN)
- CI/CD for database deployments
- Tools: Flyway, Liquibase, SSDT

### 19.4 Performance Considerations
- Order of operations for large tables
- Minimizing logging in DDL operations
- Impact of DDL on query plans

---

## Module 20: DDL in Different RDBMS

### 20.1 SQL Server Specifics
- SQL Server DDL syntax and features
- T-SQL extensions

### 20.2 PostgreSQL Specifics
- CREATE TABLE with inheritance
- CREATE SCHEMA authorization
- PostgreSQL data types (SERIAL, UUID, ARRAY, JSONB)

### 20.3 MySQL Specifics
- ENGINE specification (InnoDB, MyISAM)
- AUTO_INCREMENT vs IDENTITY
- Partitioning differences

### 20.4 Oracle Specifics
- Tablespaces and segments
- CREATE TABLE with storage clauses
- Synonyms and sequences
- Packages

### 20.5 Cross-Platform Compatibility
- Writing portable DDL
- Data type mapping between RDBMS
- Feature availability differences

---

## Module 21: Hands-On Exercises

### 21.1 Database Creation Exercises
- Create database with custom file locations
- Add secondary data files
- Create filegroup and add files to it

### 21.2 Schema Exercises
- Create multiple schemas (HR, Sales, Inventory, Finance)
- Transfer objects between schemas

### 21.3 Table Creation Exercises
- Create tables with all constraint types
- Create temporary tables
- Create tables with identity columns
- Create computed columns

### 21.4 Index Exercises
- Create clustered and non-clustered indexes
- Create unique and filtered indexes
- Create composite indexes

### 21.5 View Exercises
- Create standard views
- Create indexed views
- Create partitioned views

### 21.6 Security Exercises
- Create logins and users
- Create roles and assign permissions
- Implement row-level security

### 21.7 Full Project Exercises
- Complete database design and creation for:
    - Library Management System
    - Hospital Management System
    - E-commerce Database
    - Banking System

---

## Module 22: Common DDL Patterns and Templates

### 22.1 Create Database Template
```sql
-- Cross-platform template for database creation