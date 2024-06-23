# 💰 Wallets

## User Wallet Entity
The following properties for fin_user_wallets table:

| Name                      | Type      | Description                                | Unique | Required  |
|---------------------------|-----------|--------------------------------------------|--------|-----------|
| wallet_id                 | INT       | Primary key, unique wallet ID              |   ✅   |    ✅    |
| wallet_name               | String    | Name of the wallet                         |   ❌   |    ✅    |
| wallet_balance            | Decimal   | Total Balance of the wallet                |   ❌   |    ✅    |
| wallet_description        | String    | Description of the wallet                  |   ❌   |    ❌    |
| wallet_default            | Decimal   | Default transaction of the wallet          |   ❌   |    ❌    |
| wallet_icon               | String    | Icon of the wallet                         |   ❌   |    ❌    |
| wallet_type_id            | INT       | Foreign key from Wallet Type table         |   ❌   |    ✅    |
| user_id                   | INT       | Foreign key from User table                |   ❌   |    ✅    |

## User Wallet Type Entity
The following properties for user_wallet_type table:

| Name                      | Type      | Description                               | Unique | Required  |
|---------------------------|-----------|-------------------------------------------|--------|-----------|
| wallet_type_id            | INT       | Primary key, unique bank ID               |   ✅   |    ✅    |
| wallet_type_name          | String    | Name of the wallet                        |   ❌   |    ✅    |
| wallet_account_type       | String    | Type of the wallet (Debit/Credit)         |   ❌   |    ✅    |
| wallet_description        | String    | Description of wallet type                |   ❌   |    ✅    |
| wallet_limit              | INT       | Limit of wallet type each user            |   ❌   |    ✅    |
| wallet_type_is_active     | boolean   | Is wallet type active (Default: True)     |   ❌   |    ✅    |
| wallet_type_is_creatable  | boolean   | Is wallet creatable (Default: True)       |   ❌   |    ✅    |
| wallet_type_is_creditable | boolean   | Is wallet creditable (Default: True)      |   ❌   |    ✅    |
| wallet_type_is_debitable  | boolean   | Is wallet debitable (Default: True)       |   ❌   |    ✅    |
| wallet_type_is_public     | boolean   | Is wallet type public (Default: False)    |   ❌   |    ✅    |
| wallet_type_is_user       | boolean   | Is wallet transactable (Default: True)    |   ❌   |    ✅    |
| currency_id               | boolean   | Foreign key from Currency table           |   ❌   |    ✅    |

NOTE
- Unique: Ensures the uniqueness of the values entered into a property of a database table.
- Required: Ensures that the values entered a property of a database table can NOT be NULL.

## Wallet Account Type

A Wallet Account Type is a classification used to indicate the nature of transactions associated with a wallet. It helps differentiate between different types of wallets based on their primary purpose. There are two main account types:

1. Account Debit Wallet: A debit wallet is primarily used for saving and accumulating funds.
   - When a transaction occurs in a debit wallet, it is considered an addition (i.e., funds are added to the wallet).
   - Examples of debit wallets include personal savings accounts, emergency funds, and investment accounts.

2. Account Credit Wallet: A credit wallet is typically associated with loans, credit lines, or borrowed funds.
   - When a transaction occurs in a credit wallet, it is considered a reduction (i.e., funds are deducted from the wallet).
   - Examples of credit wallets include credit cards, student loans, and mortgages.

3. Is Active Wallet: An active wallet represents the current operational state of the wallet.
   - The status of the wallet determines whether users can perform transactions with it.
   - Examples of inactive wallets include unauthorized access attempts, security concerns, or other exceptional cases.

4. Is Creatable Wallet: An creatable wallet represents the ability to create new wallet by the user directly.
   - By default, wallets are creatable. Users can directly create and transact with the wallets. Non creditable wallet only can be created by administrators or designated personnel have the authority to it.
   - Examples of non creatable wallets include benefits fund, allowance wallet, or other exceptional cases.

5. Is Creditable Wallet: A wallet represents the accessible to credit (out/withdraw) transaction by the user.
   - Users can directly initiate credit (out/withdraw) transactions with a creditable wallet. When a user wants to transact with a creditable wallet, they can initiate the process by making a request.
   - Examples of non creditable wallets include long term funds, saving plan, or other not withdrawable cases.

6. Is Debitable Wallet: A wallet represents the accessible to debit (in/deposit) transaction by the user.
   - Users can directly initiate debit (in/deposit) transactions with a debitable wallet. When a user wants to transact with a debitable wallet, they can initiate the process by making a request.
   - Examples of non creditable wallets include benefits fund, allowance wallets, or other not addable cases.
   
7. Is Public Wallet: A public wallet is accessible by all users, allowing them to view its balance and transaction history.
   - By default, wallets are not public. In other words, users cannot directly access or transact with a public wallet. Only administrators or designated personnel have the authority to manage and withdraw funds from a public wallet. It serves as a transparent account for various purposes.
   - Examples of public wallets include collaborative, sharing, and kindness wallet for a common cause.

8. Is User Wallet: A wallet represents the transactional wallet accessible to the user by default.
   - In contrast, a non user wallet is not directly transactable by the user. Instead, it is managed by an administrator or system. Users cannot directly initiate transactions with a non user wallet. When a user wants to transact with a non user wallet, they can initiate the process by making a request.
   - Examples of non user wallets include reserved funds that are not available for regular transactions.

By clearly defining the wallet account type, users can better understand the purpose and expected behavior of their wallets. Whether it's for saving or borrowing, choosing the right account type ensures effective financial management. 😊


---
Powered by Berani Digital ID © 2024
