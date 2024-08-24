# 🔐 Roles
The roles and permissions are an important entities of the role access service. We will describe the role-related concepts and details in the following.

## Access Entity
The following properties for access table:

| Name                | Type      | Description                           | Unique | Required  |
|---------------------|-----------|---------------------------------------|--------|-----------|
| access_id           | INT       | Primary key, unique access ID         |   ✅   |    ✅    |
| access_name         | String    | Name of the access permissions        |   ❌   |    ✅    |
| access_description  | String    | Description of the access permissions |   ❌   |    ❌    |

This table is designed to facilitate the creation and management of access groups within a multi-tenant system. Each access group can contain multiple roles, allowing for flexible and granular access control.

## Roles Entity
The following properties for access_roles table:

| Name                  | Type      | Description                                      | Unique | Required  |
|-----------------------|-----------|--------------------------------------------------|--------|-----------|
| role_id               | INT       | Primary key, unique role ID                      |   ✅   |    ✅    |
| role_name             | String    | Name of the role                                 |   ❌   |    ✅    |
| role_description      | String    | Description of the role                          |   ❌   |    ❌    |

## Permissions Entity
The following properties for access_permissions table:

| Name                    | Type      | Description                                      | Unique | Required  |
|-------------------------|-----------|--------------------------------------------------|--------|-----------|
| permission_id           | INT       | Primary key, unique permission ID                |   ✅   |    ✅    |
| permission_name         | String    | Name of the permission                           |   ❌   |    ✅    |
| permission_description  | String    | Description of the permission                    |   ❌   |    ❌    |

## Role Permissions Entity
The following properties for access_role_permissions table (associative table for Roles and Permissions):

| Name                  | Type      | Description                                      | Unique | Required  |
|-----------------------|-----------|--------------------------------------------------|--------|-----------|
| role_id               | INT       | Foreign key from Roles table                     |   ❌   |    ✅    |
| permission_id         | INT       | Foreign key from Permissions table               |   ❌   |    ✅    |

## Access Roles Entity
The following properties for access_to_roles table (associative table for Access and Roles):

| Name                  | Type      | Description                                      | Unique | Required  |
|-----------------------|-----------|--------------------------------------------------|--------|-----------|
| access_id             | INT       | Foreign key from Access table                    |   ❌   |    ✅    |
| role_id               | INT       | Foreign key from Roles table                     |   ❌   |    ✅    |

This table is associate access group to the roles. The field ensures that access groups are properly segmented.

## User Access Entity
The following properties for acces_users table (associative table for Users and Access):

| Name             | Type      | Description                                      | Unique | Required  |
|------------------|-----------|--------------------------------------------------|--------|-----------|
| user_id          | String    | Foreign key from Users table                     |   ❌   |    ✅    |
| access_id        | INT       | Foreign key from Access table                    |   ❌   |    ✅    |

NOTE
- Unique: Ensures the uniqueness of the values entered into a property of a database table.
- Required: Ensures that the values entered a property of a database table can NOT be NULL.

This table is associate user to their access groups. The field ensures that access groups are properly segmented between different tenants, maintaining data isolation and security.

## Default Data

### System Role
We create default role `System` to allow all user access permissions, known as `Super Admin`. This role will be used for system maintenance and several administrator use cases only.


---
Powered by Berani Digital ID © 2024
