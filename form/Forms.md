# 📑 Form Templates and Submissions Documentation  
   
## Form Templates  
   
### Form Template Entity  
   
The following properties are defined for the `form_templates` table:  
   
| Name          | Type      | Description                                                  | Unique | Required |  
|---------------|-----------|--------------------------------------------------------------|--------|----------|  
| id            | INT       | Primary key, unique template ID                              | ✅     | ✅       |  
| title         | String    | Title of the form template                                   | ❌     | ✅       |  
| description   | String    | Description of the form template                             | ❌     | ❌       |  
| is_active     | Boolean   | Indicates if the form template is active (Default: true)     | ❌     | ✅       |  
| sort_order    | INT       | Sort order of the form template (Default: 0)                 | ❌     | ✅       |  
| user_id       | INT       | Foreign key from User table, indicating the creator          | ❌     | ❌       |  
| is_once       | Boolean   | Indicates if the form can be filled only once (Default: false)| ❌     | ✅       |  
| highlight     | Boolean   | Indicates if the form is highlighted (Default: true)         | ❌     | ✅       |  
| is_public     | Boolean   | Indicates if the form is public (Default: true)              | ❌     | ✅       |  
| code          | String    | Shareable code, can be regenerated                           | ❌     | ❌       |  
| type          | String    | Type of form template (Default: 'Default')                   | ❌     | ✅       |  
| fields        | JSON      | Form fields                                                  | ❌     | ✅       |  
| options       | JSON      | Additional options that do not require querying              | ❌     | ✅       |  
| start         | DateTime  | The start date of the form template                          | ❌     | ❌       |  
| end           | DateTime  | The end date of the form template                            | ❌     | ❌       |  
| created_at    | DateTime  | Timestamp when the record was created                        | ❌     | ✅       |  
| updated_at    | DateTime  | Timestamp when the record was last updated                   | ❌     | ✅       |  
   
### Form Submission Entity  
   
The following properties are defined for the `form_submissions` table:  
   
| Name          | Type      | Description                                                  | Unique | Required |  
|---------------|-----------|--------------------------------------------------------------|--------|----------|  
| id            | INT       | Primary key, unique submission ID                            | ✅     | ✅       |  
| form_template_id | INT    | Foreign key from Form Template table                         | ❌     | ✅       |  
| user_id       | INT       | Foreign key from User table                                  | ❌     | ❌       |  
| fields        | JSON      | Submitted form fields                                        | ❌     | ✅       |  
| created_at    | DateTime  | Timestamp when the record was created                        | ❌     | ✅       |  
| updated_at    | DateTime  | Timestamp when the record was last updated                   | ❌     | ✅       |  
   
## Key Concepts  
   
### Form Template  
A form template defines the structure, appearance, and behavior of a form. It includes various properties such as title, description, active status, and more. Form templates can be created, managed, and utilized by users to collect information.  
   
### Form Submission  
A form submission records the data submitted by users through a form template. Each submission links to a specific form template and optionally to a user who submitted the form. The submitted data is stored in a JSON format.  
   
## Examples  
   
### Active Form Template  
An active form template is one that is currently available for use. Users can fill out and submit active form templates.  
   
### Highlighted Form Template  
A highlighted form template is marked as important or noteworthy. It may be displayed more prominently in the user interface.  
   
### Public Form Template  
A public form template is accessible by all users. Anyone can view and fill out public forms.  
   
### Single-Use Form Template  
A single-use form template can only be filled out once by each user. This is useful for applications like surveys or voting.  
   
## Notes  
   
- **Unique**: Ensures the uniqueness of the values entered into a property of a database table.  
- **Required**: Ensures that the values entered into a property of a database table cannot be NULL.  
   
By clearly defining the structure and properties of form templates and submissions, users can effectively manage and utilize forms for various purposes. 😊
