# 🏠 Home

## Home Entity
The following properties for home_content table:

| Name                      | Type      | Description                               | Unique | Required  |
|---------------------------|-----------|-------------------------------------------|--------|-----------|
| home_content_id           | INT       | Primary key, unique content ID            |   ✅   |    ✅    |
| home_content_type_id      | INT       | Foreign key from home type table          |   ❌   |    ✅    |
| home_title                | String    | Title of the content                      |   ❌   |    ✅    |
| home_description          | String    | WYSWYG of the content (html)              |   ❌   |    ✅    |
| home_poster               | String    | Poster of the content                     |   ❌   |    ❌    |
| home_files                | Array     | Attachments of the content (multiple)     |   ❌   |    ❌    |
| home_comments             | Array     | Comments of the content (Plugin/Library)  |   ❌   |    ❌    |
| home_is_active            | boolean   | Is content active (Default: True)         |   ❌   |    ✅    |

## Home Type Entity
The following properties for home_type table:

| Name                      | Type      | Description                               | Unique | Required  |
|---------------------------|-----------|-------------------------------------------|--------|-----------|
| home_content_type_id      | INT       | Primary key, unique content type ID       |   ✅   |    ✅    |
| home_content_type_name    | String    | Name of the content type                  |   ❌   |    ✅    |

NOTE
- Unique: Ensures the uniqueness of the values entered into a property of a database table.
- Required: Ensures that the values entered a property of a database table can NOT be NULL.

---
Powered by Berani Digital ID © 2024
