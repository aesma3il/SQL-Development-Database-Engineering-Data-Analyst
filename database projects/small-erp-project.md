# Database Case Study: Small ERP System

## Case Study Overview

**Project:** Small Enterprise Resource Planning (ERP) System

**Objective:** Design a relational database to support core business operations for a small to medium-sized enterprise, including HR, CRM, inventory, sales, purchasing, and accounting functions.

**Scale:** Small business environment with multiple departments, branches, and users.

---

## Business Context

A growing company needs an integrated database system to manage its daily operations. The current manual or disconnected systems are causing data redundancy, reporting delays, and operational inefficiencies. The goal is to build a centralized, normalized database that supports:

- Real-time data access across departments
- Accurate financial tracking
- Inventory management
- Customer and supplier relationship management
- Employee and payroll administration

---

## Functional Requirements by Domain

### 1. Company & Organizational Data

The system must store core company information and structural data:

- Company profile (name, address, tax identification numbers)
- Departments (e.g., Sales, HR, Accounting, Warehouse)
- Branches and physical locations
- User accounts for employees accessing the system
- User roles and permission levels (e.g., Admin, Manager, Staff, Viewer)

### 2. Human Resources (HR) Data

The system must manage employee-related information:

- Employee personal information (name, ID, contact, date of birth)
- Job titles and department assignments
- Attendance records (check-in/check-out times)
- Leave records (vacation, sick leave, unpaid leave)
- Payroll information (salary, deductions, bonuses)
- Employment contracts and employment history
- Performance records (optional, for annual reviews)

### 3. Customer Relationship Management (CRM) Data

The system must support customer management:

- Customer profiles (name, contact details, billing address)
- Multiple contacts per customer (phone, email, primary/secondary)
- Customer categorization (wholesale, retail, VIP, inactive)
- Customer credit limits and current account balances
- Customer purchase history (linked to sales orders and invoices)

### 4. Supplier / Vendor Data

The system must track all supplier relationships:

- Supplier profiles (company name, contact person, address, payment terms)
- Supplier categories (e.g., raw materials, packaging, logistics)
- Purchase terms (lead time, shipping method, discount agreements)
- Supplier account balances
- Supplier transaction history (purchase orders, payments, returns)

### 5. Inventory & Warehouse Data

The system must manage all product and stock information:

- Products and items (SKU, name, description, barcode)
- Item categories (e.g., Electronics, Furniture, Consumables)
- Units of measurement (piece, kg, liter, box)
- Item attributes (size, color, model, weight)
- Current stock levels per warehouse
- Multiple warehouse locations
- Batch numbers and lot numbers (for traceability, if required)
- Stock transactions (stock in, stock out, adjustments)
- Minimum and maximum stock thresholds (reorder alerts)
- Item cost and selling price information

### 6. Purchasing Data

The system must support the procurement process:

- Purchase requests (internal requests from departments)
- Purchase orders (issued to suppliers)
- Supplier quotations (optional, for comparison)
- Goods received notes (GRN) for incoming stock
- Supplier invoices (linked to purchase orders and GRNs)
- Supplier payments (payment records, due dates)
- Purchase returns (returned items to suppliers)

### 7. Sales Data

The system must manage the sales cycle:

- Sales quotations (sent to customers)
- Sales orders (confirmed customer orders)
- Delivery notes (proof of shipment)
- Customer invoices (billing documents)
- Customer payments (receipts, payment tracking)
- Sales returns (items returned by customers)
- Discounts and pricing rules (promotions, volume discounts)

### 8. Accounting & Finance Data

The system must track all financial transactions:

- Chart of accounts (COA) with account codes and types
- Journal entries (debits and credits for each transaction)
- Ledgers:
    - General Ledger (GL)
    - Accounts Payable (supplier balances)
    - Accounts Receivable (customer balances)
- Payment vouchers (cash payments, bank transfers)
- Receipts (customer payments)
- Financial statements (income statement, balance sheet)
- Tax management (VAT, GST, sales tax rates and calculations)

### 9. Production & Manufacturing Data (Optional)

If the company manufactures products, the system must include:

- Bill of Materials (BOM) – list of raw materials per finished product
- Work orders (production jobs)
- Raw material consumption tracking
- Production schedules (start/end dates per work order)
- Finished goods output (quantity produced, quality checks)

### 10. Project Management Data (Optional)

For project-based businesses, the system must support:

- Projects (name, start date, end date, budget)
- Tasks and milestones (assigned to employees)
- Project budgets (planned vs actual costs)
- Resource allocation (personnel and materials per project)

### 11. System & Audit Data

The system must maintain operational and security logs:

- Activity logs (user actions with timestamps)
- Change history (track modifications to critical records)
- Backup records (when backups were performed)
- Error logs (system errors and exceptions)
- Notification settings (email alerts, in-app messages)

---

## Data Summary by Category

| Domain | Key Tables |
| :--- | :--- |
| Company Structure | CompanyProfile, Department, Branch, UserAccount, Role, Permission |
| Human Resources | Employee, JobTitle, Attendance, Leave, Payroll, Contract |
| Customer (CRM) | Customer, CustomerContact, CustomerCategory, CustomerBalance |
| Supplier | Supplier, SupplierCategory, SupplierBalance, SupplierTransaction |
| Inventory | Product, ProductCategory, UnitOfMeasure, StockLevel, Warehouse, StockTransaction |
| Purchasing | PurchaseRequest, PurchaseOrder, GoodsReceivedNote, SupplierInvoice, SupplierPayment |
| Sales | SalesQuotation, SalesOrder, DeliveryNote, CustomerInvoice, CustomerPayment |
| Accounting | ChartOfAccount, JournalEntry, GeneralLedger, PaymentVoucher, Tax |
| Production (Optional) | BillOfMaterials, WorkOrder, ProductionSchedule |
| Projects (Optional) | Project, Task, ProjectBudget |
| System & Audit | ActivityLog, ChangeHistory, ErrorLog |

---

 
---

## Next Steps for Database Design

1. Identify all entities and attributes within each domain
2. Define primary keys and foreign key relationships
3. Apply normalization (target 3NF or BCNF)
4. Create Entity Relationship Diagram (ERD)
5. Define data types and constraints
6. Implement physical database schema
7. Populate with test data
8. Build and test key queries (sales reports, inventory status, financial summaries)
