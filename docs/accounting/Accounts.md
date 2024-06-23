# ✍️ Accounts

## Accountings Entity
The following properties for acc_accountings table:

| Name                      | Type      | Description                               | Unique | Required  |
|---------------------------|-----------|-------------------------------------------|--------|-----------|
| accounting_id             | INT       | Primary key, unique accounting ID         |   ✅   |    ✅    |
| accounting_name           | String    | Name of the accounting                    |   ❌   |    ✅    |
| accounting_description    | String    | Description of the accounting             |   ❌   |    ❌    |


## Categories Entity
The following properties for acc_categories table:

| Name                      | Type      | Description                               | Unique | Required  |
|---------------------------|-----------|-------------------------------------------|--------|-----------|
| category_id               | INT       | Primary key, unique category ID           |   ✅   |    ✅    |
| category_name             | String    | Name of the category                      |   ❌   |    ✅    |
| category_type             | String    | Type of the category (Debit/Credit)       |   ❌   |    ✅    |
| category_code             | String    | Code of the category                      |   ❌   |    ❌    |
| category_description      | String    | Description of the category               |   ❌   |    ❌    |
| accounting_id             | INT       | Foreign Key from Accountings table        |   ❌   |    ✅    |


## Accounts Entity
The following properties for acc_accounts table:

| Name                      | Type      | Description                                           | Unique | Required  |
|---------------------------|-----------|-------------------------------------------------------|--------|-----------|
| account_id                | INT       | Primary key, unique account ID                        |   ✅   |    ✅    |
| account_name              | String    | Name of the account                                   |   ❌   |    ✅    |
| account_type              | String    | Type of the account (Debit/Credit)                    |   ❌   |    ✅    |
| account_code              | String    | Code of the account                                   |   ❌   |    ❌    |
| account_description       | String    | Description of the account                            |   ❌   |    ❌    |
| account_parent_id         | INT       | Foreign Key from Acoount                              |   ❌   |    ❌    |
| category_id               | INT       | Foreign key from Categories Table                     |   ❌   |    ✅    |


NOTE
- Unique: Ensures the uniqueness of the values entered into a property of a database table.
- Required: Ensures that the values entered a property of a database table can NOT be NULL.


## Default Data

### Accountings
| accounting_id | accounting_name          | accounting_description    |
|---------------|--------------------------|---------------------------|
| 1             | Default                  | Default Accounting        |


### Categories
| category_id | category_name          | category_type   | category_code | category_description          |
|-------------|------------------------|-----------------|---------------|-------------------------------|
| 1           | Aset                   | Debit           | 1000          | Aset (Aktiva/Harta)            |
| 2           | Liabilitas             | Credit          | 2000          | Liabilitas (Pasiva/Kewajiban)  |
| 3           | Modal                  | Credit          | 3000          | Modal (Ekuitas)                |
| 4           | Pendapatan             | Credit          | 4000          | Pendapatan (Revenue)           |
| 5           | Beban/Biaya            | Debit           | 5000          | Beban (Biaya)                  |

### Accounts
| account_id | account_name            | account_type   | account_code | account_description    | account_parent_id | category_id |
|------------|-------------------------|----------------|--------------|------------------------|-------------------|-------------|
| 1          | Kas/Bank                | Debit          | 1001         |                        |                   | 1           |
| 2          | Piutang                 | Debit          | 1002         |                        |                   | 1           |
| 3          | Aset Lainnya            | Debit          | 1999         |                        |                   | 1           |
| 4          | Utang                   | Credit         | 2001         |                        |                   | 2           |
| 5          | Modal Pemilik           | Credit         | 3001         |                        |                   | 3           |
| 6          | Pendapatan Usaha        | Credit         | 4001         |                        |                   | 4           |
| 7          | Pendapatan Diluar Usaha | Credit         | 4002         |                        |                   | 4           |
| 8          | Pendapatan Lainnya      | Credit         | 4999         |                        |                   | 4           |
| 9          | Beban/Biaya Gaji        | Debit          | 5001         |                        |                   | 5           |
| 10         | Beban/Biaya Sewa        | Debit          | 5002         |                        |                   | 5           |
| 11         | Beban/Biaya Peralatan   | Debit          | 5003         |                        |                   | 5           |
| 12         | Beban/Biaya Lainnya     | Debit          | 5999         |                        |                   | 5           |


---
Powered by Berani Digital ID © 2024
