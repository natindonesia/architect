# 💵 Transactions

## Transaction Entity
The following properties for fin_transactions table:

| Name              | Type      | Description                                   | Unique | Required  |
|-------------------|-----------|-----------------------------------------------|--------|-----------|
| trx_id            | INT       | Primary key, unique transaction ID            |   ✅   |    ✅    |
| trx_amount        | Decimal   | Amount of the transaction                     |   ❌   |    ✅    |
| trx_proof         | String    | Proof of the transaction                      |   ❌   |    ❌    |
| trx_method_id     | INT       | Method of the transaction (Cash/Transfer)     |   ❌   |    ✅    |
| trx_type_id       | INT       | Type of the transaction (Deposit/Withdrawal)  |   ❌   |    ✅    |
| trx_status_id     | INT       | Status of the transaction                     |   ❌   |    ✅    |
| wallet_id         | INT       | Foreign key from Wallet table                 |   ❌   |    ❌    |
| bank_account_id   | INT       | Foreign key from Bank Account table           |   ❌   |    ❌    |
| user_id           | INT       | Foreign key from User table                   |   ❌   |    ✅    |


## Transaction Type Entity
The following properties for fin_trx_types table:

| Name                    | Type      | Description                                 | Unique | Required  |
|-------------------------|-----------|---------------------------------------------|--------|-----------|
| trx_type_id             | INT       | Primary key, unique bank ID                 |   ✅   |    ✅    |
| trx_type_code           | String(6) | Code of the transaction type                |   ❌   |    ✅    |
| trx_type_name           | String    | Name of the transaction type                |   ❌   |    ✅    |
| trx_type_is_deleted     | boolean   | Is trx type deleted (Default: False)        |   ❌   |    ✅    |


## Transaction Method Entity
The following properties for fin_trx_methods table:

| Name                    | Type      | Description                                   | Unique | Required  |
|-------------------------|-----------|-----------------------------------------------|--------|-----------|
| trx_method_id           | INT       | Primary key, unique bank ID                   |   ✅   |    ✅    |
| trx_method_code         | String(6) | Code of the transaction method                |   ❌   |    ✅    |
| trx_method_name         | String    | Name of the transaction method                |   ❌   |    ✅    |
| trx_method_is_deleted   | boolean   | Is trx method deleted (Default: False)        |   ❌   |    ✅    |


## Transaction Status Entity
The following properties for fin_trx_types table:

| Name                    | Type      | Description                                   | Unique | Required  |
|-------------------------|-----------|-----------------------------------------------|--------|-----------|
| trx_status_id           | INT       | Primary key, unique status ID                 |   ✅   |    ✅    |
| trx_status_code         | String(6) | Code of the transaction status                |   ❌   |    ✅    |
| trx_status_name         | String    | Name of the transaction status                |   ❌   |    ✅    |
| trx_status_is_deleted   | boolean   | Is trx status deleted (Default: False)        |   ❌   |    ✅    |


NOTE
- Unique: Ensures the uniqueness of the values entered into a property of a database table.
- Required: Ensures that the values entered a property of a database table can NOT be NULL.


## Default Data

### Transaction Type
| trx_type_id | trx_type_code | trx_type_name          | trx_type_is_deleted     |
|-------------|---------------|------------------------|-------------------------|
| 1           | IN            | Setoran                | false                   |
| 2           | OUT           | Penarikan              | false                   |
| 3           | TF-IN         | Transfer Masuk         | false                   |
| 4           | TF-OUT        | Transfer Keluar        | false                   |


### Transaction Method
| trx_method_id | trx_method_code | trx_method_name          | trx_method_is_deleted    |
|---------------|-----------------|--------------------------|--------------------------|
| 1             | CASH            | Cash/Tunai               | false                    |
| 2             | BANK            | Bank Transfer            | false                    |
| 3             | SYSTEM          | Transaction              | false                    |


### Transaction Status
| trx_status_id | trx_status_code | trx_status_name          | trx_status_is_deleted    |
|---------------|-----------------|--------------------------|--------------------------|
| 1             | 001             | Approved                 | false                    |
| 2             | 002             | Cancelled                | false                    |
| 3             | 003             | Pending                  | false                    |
| 4             | 008             | Draft                    | false                    |
| 5             | 009             | Denied                   | false                    |


---
Powered by Berani Digital ID © 2024
