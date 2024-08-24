# 💵 Currency

## Currency Entity
The following properties for fin_currency table:

| Name                      | Type      | Description                               | Unique | Required  |
|---------------------------|-----------|-------------------------------------------|--------|-----------|
| currency_id               | INT       | Primary key, unique currency ID           |   ✅   |    ✅    |
| currency_name             | String    | Name of the currency                      |   ❌   |    ✅    |
| currency_symbol           | String    | Symbol of the currency                    |   ❌   |    ❌    |
| currency_postfix          | String    | An optional postfix currency symbol       |   ❌   |    ❌    |
| currency_prefix           | String    | An optional prefix currency symbol        |   ❌   |    ❌    |


NOTE
- Unique: Ensures the uniqueness of the values entered into a property of a database table.
- Required: Ensures that the values entered a property of a database table can NOT be NULL.

## Curency Usage
The `fin_currency` table serves as a central repository for the currency information. The `fin_currency` table empowers financial systems to handle diverse currencies seamlessly, and supporting any transactions type.

1. `currency_id` (INT):
   - This column serves as the primary key for the table.
   - It uniquely identifies each currency record.
   - Typically, this value is automatically generated (e.g., using auto-increment) when a new currency is added to the system.
   - Usage: Used for referencing specific currencies in other tables or queries.

2. `currency_name` (String):
   - Represents the name of the currency (e.g., "IDR Rupiah", "US Dollar," "Euro," "Japanese Yen").
   - Not necessarily unique (multiple currencies can have the same name).
   - Usage: Displayed to end users in applications, reports, or interfaces.

3. `currency_symbol` (String):
   - Contains the symbol associated with the currency (e.g., "$" for US Dollar, "€" for Euro, "¥" for Japanese Yen).
   - Not necessarily unique (multiple currencies can share the same symbol).
   - Usage: Displayed alongside the currency amount to indicate the currency type (e.g., $100).

4. `currency_postfix` (String):
   - Represents an optional postfix symbol (e.g., "K" for thousands, "M" for millions) that can be appended to the currency amount.
   - Usage: Displayed postfix alongside the currency amount to indicate the currency (e.g., 100 IDR).

5. `currency_prefix` (String):
   - Similar to `currency_postfix`, but represents an optional prefix symbol (e.g., "USD" for US Dollar, "EUR" for Euro).
   - Usage: Displayed prefix alongside the currency amount to indicate the currency (e.g., Rp 100).


---
Powered by Berani Digital ID © 2024
