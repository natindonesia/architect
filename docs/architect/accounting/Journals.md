# 🧾 Journals

## Journals Entity
The following properties for acc_journals table:

| Name                      | Type      | Description                               | Unique | Required  |
|---------------------------|-----------|-------------------------------------------|--------|-----------|
| journal_id                | INT       | Primary key, unique journal entry ID      |   ✅   |    ✅    |
| journal_date              | DateTime  | Transaction date of the jorunal entry     |   ❌   |    ✅    |
| journal_description       | String    | Description of the Journal entry          |   ❌   |    ❌    |
| journal_reference         | String    | Reference of the journal entry            |   ❌   |    ❌    |
| user_id                   | String    | The identifier of the journal entry       |   ❌   |    ✅    |

## Journal Transactions Entity
The following properties for acc_journal_transactions table:

| Name                          | Type      | Description                                   | Unique | Required  |
|-------------------------------|-----------|-----------------------------------------------|--------|-----------|
| journal_id                    | INT       | Foreign key from Journals Table               |   ❌   |    ✅    |
| account_id                    | INT       | Foreign key from Account (CoA) Table          |   ❌   |    ✅    |
| transaction_type              | String    | Type of the transaction entry (Debit/Credit)  |   ❌   |    ✅    |
| transaction_total             | Decimal   | Total of the transaction entry                |   ❌   |    ✅    |
| transaction_description       | String    | Description of the transaction entry          |   ❌   |    ❌    |
| user_id                       | String    | The identifier of the transaction entry       |   ❌   |    ✅    |

NOTE
- Unique: Ensures the uniqueness of the values entered into a property of a database table.
- Required: Ensures that the values entered a property of a database table can NOT be NULL.


## Journal Transactions
We record transactions into a journal. It keeps track of the transaction item, and accounting linked accounts.

### Transaction - Prerequisite
Default Data:
- [a] Accountings
- [b] Categories
- [c] Accounts
- [d] Transaction Type
- [e] Transaction Method
- [f] Transaction Status

Used `Accounts` :
- `1 | Kas/Bank | 1001`
- `4 | Utang | 2001`

### Transaction 1 - 'Setoran'
- Transaction Type: [d] `1 | IN | Setoran`
- Transaction Method: [e] `1 | CASH | Cash/Tunai` or `2 | BANK | Bank Transfer`
- Transaction Status: [f] `3 | 003 | Pending` (Admin approval needed)
- Journal ID: {Incremental}
- 1 - Account ID: [c] `1 | Kas/Bank | 1001`
- 1 - Account Transaction Type: `Debit`
- 2 - Account ID: [c] `4 | Utang | 2XXX` (Berdasar COA user)
- 2 - Account Transaction Type: `Credit`

### Transaction 2 - 'Penarikan'
- Transaction Type: [d] `2 | OUT | Penarikan`
- Transaction Method: [e] `1 | CASH | Cash/Tunai` or `2 | BANK | Bank Transfer`
- Transaction Status: [f] `3 | 003 | Pending` (Admin approval needed)
- Journal ID: {Incremental}
- 1 - Account ID: [c] `1 | Kas/Bank | 1001`
- 1 - Account Transaction Type: `Credit`
- 2 - Account ID: [c] `4 | Utang | 2XXX` (Berdasar COA user)
- 2 - Account Transaction Type: `Debit`

### Transaction 3 - 'Transfer Sesama'
- Transaction Method: [e] `| 3 | SYSTEM | Transaction`
- Transaction Status: [f] `1 | 001 | Approved`
- Journal ID: {Incremental}
- Transaction Type: [d] `| 4 | TF-OUT | Transfer Keluar`
- 1 - Account ID: [c] `4 | Utang | 2XXX` (Berdasar COA user)
- 1 - Account Transaction Type: `Credit`
- Transaction Type: [d] `3 | TF-IN | Transfer Masuk`
- 2 - Account ID: [c] `4 | Utang | 2XXX` (Berdasar COA user)
- 2 - Account Transaction Type: `Debit`


---
Powered by Berani Digital ID © 2024