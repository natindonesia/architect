# 📜 Audit Logs

Our audit log allows system to easily monitor user activity and events. It provides a strong foundation for various user management and health check business scenarios.

## Audits Entity
Our logs offer comprehensive details, ensuring ease of action and customer safety. They capture and record the following properties:

| Name                  | Type                | Description                                        | Unique | Required  |
|-----------------------|---------------------|----------------------------------------------------|--------|-----------|
| id                    | String    | A unique identifier for the event log entry                  |   ✅   |    ✅    |
| application_id        | String    | Application ID that associated with the event                |   ❌   |    ✅    |
| application_name      | String    | The name of the application related to the event             |   ❌   |    ✅    |
| event_id              | String    | Event ID of the nature or category of the event              |   ❌   |    ✅    |
| event_name            | String    | The nature or category of the event                          |   ❌   |    ✅    |
| user_id               | String    | The identifier of the user associated with the event         |   ❌   |    ✅    |
| data_before           | Object    | Additional data before changed in customizable properties    |   ❌   |    ✅    |
| data_changed          | Object    | Additional data after changed in customizable properties     |   ❌   |    ✅    |
| ip_address            | String    | The IP address from which the event originated               |   ❌   |    ✅    |
| user_agent            | String    | The browser or device information from which the event came  |   ❌   |    ✅    |
| timestamp             | Date time | The date and time when the event occurred                    |   ❌   |    ✅    |

NOTE
- Unique: Ensures the uniqueness of the values entered into a property of a database table.
- Required: Ensures that the values entered a property of a database table can NOT be NULL.

By maintaining these event records, organizations can effectively detect possible security risks and promptly address them to prevent unauthorized system access.

## View all logs
We captures and organizes authentication events into a table. It keeps track of the event name, user, application, and timestamp. You can narrow down the results by filtering based on the event name and application name. Filtering on a specific event will provide additional details.

## Perform a detailed analysis
Administrators can perform a detailed analysis of logs associated with specific users, facilitating comprehensive investigations into specific events. The navigation process is straightforward and user-friendly.

To access user-specific logs, follow these steps: Navigate to User Management, select the desired user, and click on User Logs. The resulting table will exclusively display log events performed and triggered by that particular user.

---
Powered by Berani Digital ID © 2024
