# Amanat Library System – Database Design Requirements

## 1. Problem Statement
An Amanat (custody) library receives messages and parcels from senders and stores them until recipients arrive to collect them. Each message has a fee that can be paid by the sender at drop-off, by the recipient at pickup, or recorded on the client’s account (credit) if the client is trusted.

The system must manage and track:
- Clients (senders and recipients)
- Messages (parcels)
- Receipt vouchers (message intake)
- Delivery vouchers (message handover)
- Payments
- Account charges (credit)
- Account settlements
- Audit logs for tracking operations

The system should support reporting, enforce business rules, and ensure data integrity and traceability.

---

## 2. User Requirements

### Client Management
- Register new clients (sender, recipient, or both)
- Store client data: name, phone, optional image, identity details
- Mark clients as trusted (eligible for credit)

### Message Handling
- Register a new message upon receiving it from a sender
- Generate and store a receipt voucher linked to the message and sender
- Assign a unique tracking number
- Track message status (Received, Stored, Delivered, Returned, Lost)

### Delivery Process
- Create a delivery record when the recipient collects the message
- Capture recipient signature and identity image
- Record payment if applicable at delivery

### Financial Operations
- Record payments (linked to message or client account)
- Record account charges for trusted clients (credit system)
- Allow settlement of client account balances
- Maintain full transaction history

### Search & Filtering
- Search messages by tracking number, status, or client
- Filter messages by status or date

### Reporting
- Daily and monthly revenue reports
- List of undelivered messages
- Client account statements (charges, payments, balance)
- Payment logs by date range
- Messages received per day
- Trusted clients and outstanding balances

### User Management
- Manage system users and roles:
  - Operator
  - Accountant
  - Manager

### Audit & Logging
- Track all create/update operations
- Record user actions for messages and payments

---

## 3. Non-Functional Requirements

### Security
- Encrypt user passwords
- Role-based access control
- Protect identity images and sensitive data

### Performance
- Indexing for fast search (tracking number, status)
- Efficient query performance

### Reliability
- Backup and recovery mechanisms

---

## 4. Core Operations

### Client Operations
- Register client

### Message Operations
- Register message receipt
- Create receipt voucher
- Create delivery voucher

### Financial Operations
- Record payment
- Record account charge
- Settle client account

---

## 5. Outputs

- Client account statement
- Reports (financial, operational)

---

## 6. Core Entities

- Client
- Message
- Receipt
- Delivery
- Payment
- AccountCharge
- AccountJournalEntry

---

## 7. CRUD & System Features

### Core CRUD
- Create, Read, Update, Delete
- Search records
- Soft delete (archive)
- Restore archived records
- Lock / Unlock records
- Activate / Deactivate

### Listing & Navigation
- List all records
- Pagination
- Sorting
- Filtering
- Advanced search
- Column selection (show/hide)
- Grouping (by status, type, category)

### Attachments
- Add attachment
- View attachment
- Download attachment
- Delete or replace attachment
- Preview images
- Link entities
- View related records

---

## 8. Reports

### Basic Reports
- Daily / Monthly revenue (Payments)
- Undelivered messages
- Client account statement
- Payment history (by date range)
- Daily received messages
- Trusted clients with balances

### Advanced Reports
- Average storage duration (received → delivered)
- High outstanding balances
- User activity reports
- Storage location inventory
- Audit logs (changes tracking)

---

## 9. Inputs & Outputs

### Inputs
- Client data (name, phone, address, images)
- Message data (tracking number, description, weight, fee, payer)
- Payments (amount, method, reference)
- Delivery data (recipient info, ID image, signature)
- Account charges (amount, due date)

### Outputs
- Receipt voucher (PDF)
- Delivery slip (signed)
- Payment receipt
- Client statement (PDF/HTML)
- Reports (CSV/Excel)

---

## 10. Business Rules

### Message Rules
- Each message must have a receipt
- Tracking number must be unique
- Only non-delivered messages can be delivered

### Payment Rules
- If payer = sender → pay at receipt or mark unpaid
- If payer = recipient → pay at delivery or record charge
- If payer = on_account → record as account charge

### Credit Rules
- Only trusted clients can use credit
- شرط: current_balance + new_charge ≤ credit_limit

### Payment Application
- Payments must be applied to oldest charges first (FIFO)

### Data Integrity
- Cannot delete client with related records (use soft delete)
- Identity and signature required at delivery
- All actions must be logged with user ID

### Validation
- Payment amount must be > 0
- Payment methods must be valid (Cash, Card, Transfer)

### Notifications (Optional)
- Notify recipient when message arrives

---

## 11. Goal

Design a relational database that supports:
- Message lifecycle management
- Financial tracking (payments and credit)
- Client management
- Reporting and analytics
- Data integrity and auditability
- Scalable and maintainable architecture