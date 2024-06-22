# 📝 Form Template Documentation  
   
## Form Template Enums  
   
### FormTemplate Type Enum  
   
The `Type` enum defines the various types of form templates available. It implements the `HasLabel` interface to provide a human-readable label for each enum value.  
   
#### Enum Values  
   
- **Default**: The default form template type.  
- **Feedback**: A form template type specifically for feedback forms.  
- **Multi_Rater**: A form template type for multi-rater assessments.  
   
#### Methods  
   
- **getLabel()**: Returns a human-readable label for the enum value.  
   
### FormTemplateOptions Enum  
   
The `FormTemplateOptions` enum defines the various field types available for form templates. It implements the `HasLabel` interface to provide a human-readable label for each enum value.  
   
#### Enum Values  
   
- **text**  
- **date**  
- **datetime**  
- **checkbox**  
- **radio**  
- **checkbox_list**  
- **select**  
- **multi_select**  
- **phone**  
- **email**  
- **url**  
- **user_select**  
- **user_multi_select**  
   
#### Methods  
   
- **isUser(string|FormTemplateOptions $type)**: Checks if the field type is a user selection type.  
- **fromValueSafe(string $type)**: Safely converts a string to a `FormTemplateOptions` enum value.  
- **fromValue(string $type)**: Converts a string to a `FormTemplateOptions` enum value.  
- **hasOptions(string|FormTemplateOptions $type)**: Checks if the field type has options.  
- **getLabel()**: Returns a human-readable label for the enum value.  
   
## Form Template Models  
   
### FormTemplate Model  
   
The `FormTemplate` model represents a form template and includes various attributes and relationships.  
   
#### Attributes  
   
- **title**: The title of the form template.  
- **description**: A description of the form template.  
- **is_active**: Indicates if the form template is active.  
- **is_public**: Indicates if the form template is public.  
- **is_once**: Indicates if the form can be filled only once.  
- **highlight**: Indicates if the form template is highlighted.  
- **code**: A shareable code for the form template.  
- **type**: The type of the form template.  
- **fields**: The fields of the form template.  
- **options**: Additional options for the form template.  
- **start**: The start date of the form template.  
- **end**: The end date of the form template.  
   
#### Relationships  
   
- **user()**: The user who created the form template.  
- **submissions()**: The submissions for the form template.  
- **sharedWith()**: The users with whom the form template is shared.  
   
#### Methods  
   
- **updateStatusIfHaveDate()**: Updates the status of the form template if it has a start and end date.  
- **availableFormTemplate(Builder $query)**: Returns available form templates.  
- **getSchema()**: Returns the schema for the form template fields.  
- **getFilamentTableColumns()**: Returns the columns for the Filament table.  
   
### FormSubmission Model  
   
The `FormSubmission` model represents a submission for a form template.  
   
#### Attributes  
   
- **form_template_id**: The ID of the form template.  
- **user_id**: The ID of the user who submitted the form.  
- **fields**: The fields of the form submission.  
   
#### Relationships  
   
- **formTemplate()**: The form template for the submission.  
- **user()**: The user who submitted the form.  
   
#### Methods  
   
- **getFormattedFieldsAttribute()**: Returns the formatted fields for the submission.  
   
## Form Template Migrations  
   
### 2024_06_21_184853_forms_table Migration  
   
The migration creates the `form_templates` and `form_submissions` tables.  
   
#### form_templates Table  
   
- **id**: Primary key.  
- **title**: The title of the form template.  
- **description**: A description of the form template.  
- **is_active**: Indicates if the form template is active.  
- **sort_order**: The sort order of the form template.  
- **user_id**: The user who created the form template.  
- **is_once**: Indicates if the form can be filled only once.  
- **highlight**: Indicates if the form template is highlighted.  
- **is_public**: Indicates if the form template is public.  
- **code**: A shareable code for the form template.  
- **type**: The type of the form template.  
- **fields**: The fields of the form template.  
- **options**: Additional options for the form template.  
- **start**: The start date of the form template.  
- **end**: The end date of the form template.  
- **timestamps**: Timestamps for the form template.  
   
#### form_submissions Table  
   
- **id**: Primary key.  
- **form_template_id**: The ID of the form template.  
- **user_id**: The ID of the user who submitted the form.  
- **fields**: The fields of the form submission.  
- **timestamps**: Timestamps for the form submission.  
   
## Form Template Factories  
   
### FormTemplateFactory  
   
The factory for creating `FormTemplate` instances.  
   
#### Methods  
   
- **definition()**: Defines the default state for the `FormTemplate` model.  
   
### FormSubmissionFactory  
   
The factory for creating `FormSubmission` instances.  
   
#### Methods  
   
- **definition()**: Defines the default state for the `FormSubmission` model.  
- **fields(FormTemplate $template, ?Generator $faker = null)**: Generates fields for the form submission.  
   
## Form Template Resources  
   
### FormTemplateResource  
   
The resource for managing form templates in the Filament admin panel.  
   
#### Methods  
   
- **form(Form $form)**: Defines the form schema for the resource.  
- **getEloquentQuery()**: Returns the Eloquent query for the resource.  
- **table(Table $table)**: Defines the table schema for the resource.  
- **commonColumns()**: Returns the common columns for the resource.  
- **getRelations()**: Returns the relations for the resource.  
- **getPages()**: Returns the pages for the resource.  
   
### FormSubmissionResource  
   
The resource for managing form submissions in the Filament admin panel.  
   
#### Methods  
   
- **form(Form $form)**: Defines the form schema for the resource.  
- **table(Table $table)**: Defines the table schema for the resource.  
- **commonColumns()**: Returns the common columns for the resource.  
- **getRelations()**: Returns the relations for the resource.  
- **getPages()**: Returns the pages for the resource.  
   
## Form Template Relation Managers  
   
### SubmissionsRelationManager  
   
The relation manager for managing form submissions related to a form template.  
   
#### Methods  
   
- **table(Table $table)**: Defines the table schema for the relation.  
- **form(Form $form)**: Defines the form schema for the relation.  
   
### SharedWithRelationManagerForm  
   
The relation manager for managing users with whom the form template is shared.  
   
#### Methods  
   
- **geCommonHeaderActions()**: Returns the common header actions for the relation.  
- **table(Table $table)**: Defines the table schema for the relation.  
- **form(Form $form)**: Defines the form schema for the relation.  
- **getOwnerRecord()**: Returns the owner record for the relation.  
   
## Form Template Widgets  
   
### HighlightForm Widget  
   
The widget for displaying highlighted form templates.  
   
#### Methods  
   
- **canView()**: Determines if the widget can be viewed.  
- **table(Table $table)**: Defines the table schema for the widget.  
   
## Form Template Exports  
   
### FormSubmissionsExport  
   
The export class for exporting form submissions to Excel.  
   
#### Methods  
   
- **setUp()**: Sets up the export.  
   
## Form Template Providers  
   
### AdminPanelProvider  
   
The provider for the Filament admin panel.  
   
#### Methods  
   
- **register()**: Registers the provider.  
- **boot()**: Boots the provider.  
   
## Composer Configuration  
   
### composer.json  
   
The `composer.json` file includes the dependencies for the application.  
   
#### Dependencies  
   
- **ariaieboy/filament-currency**  
- **fakerphp/faker**  
- **filament/filament**  
- **guava/filament-icon-picker**  
- **laravel/framework**  
- **laravel/tinker**  
- **pxlrbt/filament-excel**  
   
### composer.lock  
   
The `composer.lock` file locks the dependencies for the application.  
   
## Database Seeds  
   
### FormTemplateSeeder  
   
The seeder for creating form templates.  
   
#### Methods  
   
- **run()**: Runs the seeder.  
   
### FormSubmissionSeeder  
   
The seeder for creating form submissions.  
   
#### Methods  
   
- **run()**: Runs the seeder.  
   
## Database Migrations  
   
### 2024_06_21_184853_forms_table Migration  
   
The migration creates the `form_templates` and `form_submissions` tables.  
   
#### form_templates Table  
   
- **id**: Primary key.  
- **title**: The title of the form template.  
- **description**: A description of the form template.  
- **is_active**: Indicates if the form template is active.  
- **sort_order**: The sort order of the form template.  
- **user_id**: The user who created the form template.  
- **is_once**: Indicates if the form can be filled only once.  
- **highlight**: Indicates if the form template is highlighted.  
- **is_public**: Indicates if the form template is public.  
- **code**: A shareable code for the form template.  
- **type**: The type of the form template.  
- **fields**: The fields of the form template.  
- **options**: Additional options for the form template.  
- **start**: The start date of the form template.  
- **end**: The end date of the form template.  
- **timestamps**: Timestamps for the form template.  
   
#### form_submissions Table  
   
- **id**: Primary key.  
- **form_template_id**: The ID of the form template.  
- **user_id**: The ID of the user who submitted the form.  
- **fields**: The fields of the form submission.  
- **timestamps**: Timestamps for the form submission.
