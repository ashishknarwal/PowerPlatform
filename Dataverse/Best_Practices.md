# Dataverse Best Practice

## Choosing the Right Table Type and Record Ownership

Dataverse offers four types of tables: Standard, Activity, Virtual, and Elastic. Selecting the appropriate table type is crucial to efficiently organize and manage your data.

## Table Types

### 1. Standard Tables

- **Description**: Standard tables are the default table type in Dataverse. They are suitable for most general-purpose data storage needs.
- **Use Cases**:
  - Storing structured data like customer information, product details, or financial records.
  - Storing customer information, such as accounts, contacts, and leads.
  - Tracking sales opportunities and pipeline.
  - Managing customer support cases.
  - Storing product information and inventory levels.
  - Maintaining transactional data, such as order history.
- **Record Ownership**: Records can be either organization-owned or user or team-owned. Organization-owned tables are accessible to all users in the organization, while user or team-owned tables are only accessible to the user or team that owns them.
- **Example**: A standard table can be used to store employee records in an HR management system.

### 2. Activity Tables

- **Description**: Activity tables are designed for tracking events, actions, or logs over time such as phone calls, emails, and meetings. They have a temporal aspect and are optimized for appending data. Activity tables are integrated with Dataverse calendars, so you can easily view and manage your schedule.
- **Use Cases**:
  - Logging user actions in a web application.
  - Tracking customer interactions, such as phone calls, emails, and meetings.
  - Recording sensor data, such as temperature readings over time.
  - Scheduling appointments and events.
- **Record Ownership**: Records in activity tables are always user or team-owned and often have system-generated ownership, as they are usually logged events. However, you can still associate ownership with user accounts for auditing purposes.
- **Example**: An activity table can be used to log user login/logout timestamps in a website's analytics system.

### 3. Virtual Tables

- **Description**: Virtual tables are used to connect to external data sources, such as SQL Server or Azure Storage. Virtual tables allow you to use Dataverse to query and analyze data from other systems. Virtual tables do not store data directly but are based on SQL queries that generate data on the fly. They are useful for creating dynamic views or aggregations.
- **Use Cases**:
  - Creating a summary report based on data from multiple standard tables.
  - Connecting to external data sources, such as SQL Server or Azure Storage.
  - Integrating with other systems, such as CRM or ERP systems
  - Creating data warehouses and data lakes.
  - Generating a virtual table to display real-time statistics.
- **Record Ownership**: Records in Virtual tables are always organization owned. This is because virtual tables are used to connect to external data sources, which are typically owned by the organization as a whole.
- **Example**: A virtual table can be used to calculate the average revenue per customer from a standard sales table.

### 4. Elastic Tables

- **Description**: Elastic tables are a new type of table that is designed to store and process very large datasets. Elastic tables are physically stored in Azure Cosmos DB, which provides scalability and performance for high-volume workloads. Elastic tables are designed for handling large volumes of data that require high scalability and performance. They are based on the Elasticsearch engine.
- **Use Cases**:
  - Indexing and searching unstructured or semi-structured data, such as text documents or logs.
  - Analyzing big data sets for insights and patterns.
  - Storing and processing very large datasets, such as customer transaction data, sensor data, or social media data.
  - Performing real-time analytics on large datasets.
  - Building machine learning models on large datasets.
- **Record Ownership**: Records in Elastic tables can be either organization-owned or user or team-owned. However, it is recommended to set elastic tables as organization owned to ensure that all users have access to the data.
- **Example**: An elastic table can be used to index and search through a massive collection of research papers for a digital library.

## Best Practices

- **Evaluate Your Data Needs**: Carefully assess your data requirements and choose the table type that best aligns with your project's objectives.

- **Consider Scalability**: If your data volume is expected to grow significantly, consider using Elastic tables for scalability and performance.

- **Normalize your data**: Data normalization is the process of organizing your data into a logical and efficient structure. This helps to improve performance, reduce redundancy, and ensure data integrity.

- **Think Temporal**: For time-series data, Activity tables are ideal as they optimize for appending records over time.

- **Use Virtual Tables Sparingly**: Virtual tables are powerful but can impact performance if overused. Reserve them for complex queries and aggregations.

- **Use meaningful field names and descriptions**: When creating fields, use clear and concise names and descriptions that accurately reflect the data that will be stored in the field. This will make it easier to understand and use your data.

- **Set appropriate field security**: Use field security to restrict access to sensitive data. This will help to protect your data from unauthorized access.

- **Use relationships to connect tables**: Relationships allow you to connect related data in different tables. This makes it easier to query and analyze your data.

- **Regular Maintenance & Data Backup**: Regularly clean up and optimize your tables to ensure optimal performance and efficient data storage.

- **Back up your data regularly**: It is important to back up your Dataverse data regularly to protect against data loss.

- **Documentation**: Maintain clear documentation for each table type's purpose, usage, and record ownership in your Dataverse project.

## Choosing the Correct Column Type and Data Type

In Dataverse, choosing the right column type and data type is essential for structuring your data effectively.

## Column Types

# Dataverse Column Types and Behaviors

In Dataverse, you have a variety of column types to choose from, each with its own specific subtypes and behaviors. Understanding these options is crucial for effectively structuring your data. This guide provides an overview of the available column types, their subtypes, and behaviors, along with real-life examples of how they can be used.

## 1. Text

### 1A. Single Line of Text

- **Plain Text**: Allows storage of basic alphanumeric characters.
- **Text Area**: Similar to plain text but with a larger character limit.
- **Rich Text**: Allows formatting and styling of text.
- **Email**: Specifically designed for storing email addresses.
- **Phone Number**: Designed for storing phone numbers.
- **Ticker Symbol**: Suitable for stock ticker symbols.
- **URL**: Used for storing website URLs.

**Real-life Example**: In a customer database, you can use a single line of text to store customer names, email addresses, or phone numbers.

### 1B. Multiple Lines of Text

- **Plain Text**: Similar to single line of text but with a larger character limit.
- **Rich Text**: Allows formatting and styling of longer text entries.

**Real-life Example**: In a content management system, you can use multiple lines of text to store blog posts or articles with rich formatting.

## 2. Number

- **Whole Number**: Stores integer values.
- **Decimal**: Stores numbers with decimal places for precision.
- **Float**: Represents floating-point numbers.
- **Language Code**: Used for language codes.
- **Duration**: Stores time durations.
- **Time Zone**: Specifically designed for time zone information.

**Real-life Example**: In an e-commerce platform, you can use a whole number to store the quantity of items in an order and decimal to store the price per item.

## 3. Date and Time

- **Date and Time**: Stores both date and time values.
- **Date Only**: Records date values without time.

**Real-life Example**: In a project management tool, you can use date and time to track task deadlines and date only to record project start dates.

## 4. Lookup

- **Lookup**: Creates a reference to another table.
- **Customer**: Specifically designed for customer-related information.

**Real-life Example**: In a CRM system, you can use lookup columns to link customers to their orders or opportunities.

## 5. Choice

- **Choice**: Allows users to select from predefined options.
- **Yes/No**: Provides a binary choice (yes or no).

**Real-life Example**: In a survey application, you can use choice columns for multiple-choice questions, and yes/no for questions with binary responses.

## 6. Currency

- **Currency**: Specifically designed for currency values.

**Real-life Example**: In an accounting system, you can use currency columns to store financial transaction amounts.

## 7. Autonumber

- **Autonumber**: Automatically generates unique numerical values.

**Real-life Example**: In a ticketing system, you can use autonumber columns to assign unique ticket IDs to customer inquiries.

## 8. File

- **File**: Stores file attachments.
- **Image**: Specifically designed for image files.

**Real-life Example**: In a document management system, you can use file columns to attach documents to records, and image columns to store profile pictures.

## 9. Formula

- **Formula**: Calculates values based on expressions or operations involving other columns within the same table.

**Real-life Example**: In a project management tool, you can use formula columns to calculate the total project cost based on individual task costs.

These Dataverse column types offer flexibility for structuring and managing data in various real-world scenarios, allowing you to capture, calculate, and display data effectively.

### 7. Formula, Calculated, and Roll-up Columns

- **Description**:
  - `Formula Columns`: These columns calculate values based on expressions or operations involving other columns within the same table. Formula columns allow you to calculate values based on other values in the same record. For example, you could create a formula column to calculate the total price of an order by multiplying the quantity by the price of each item in the order.
- **Example**:
- Use a formula column to calculate the total cost of items in an order based on quantity and unit price.
- Use a formula column to calculate the total price of an order by multiplying the quantity by the price of each item in the order.
  - `Calculated Columns`: Similar to formula columns, calculated columns perform calculations but can also reference related tables. Calculated columns are similar to formula columns, but they are calculated automatically when the record is saved. This makes them more efficient for calculations that need to be performed frequently.
- **Example**:
-   - Use a calculated column to determine a customer's total purchases by referencing related sales transactions.
    - Use a calculated column to calculate the total sales for a customer by aggregating the sales from all of the customer's orders.
  - `Roll-up Columns`: Roll-up columns aggregate data from related tables, performing calculations like sum, average, or count. Roll-up columns allow you to calculate values based on related records. For example, you could create a roll-up column to calculate the total sales for a customer by aggregating the sales from all of the customer's orders.
- **Example**:
  - Use a roll-up column to find the total number of products sold in a specific category by aggregating sales data from related tables.
  - Use a roll-up column to calculate the average response time for a customer support team by aggregating the response times for all of the cases handled by the team.

## Best Practices

- **Understand Data Requirements**: Analyze your data and understand the nature of the information you need to store to choose the appropriate column and data types.

- **Keep Data Consistency**: Enforce consistent data types across columns to avoid data entry errors and ensure accurate analysis.

- **Optimize for Querying**: Consider the types of queries you'll run on your data when selecting data types, especially for numeric and date columns.

- **Use Formula, Calculated, and Roll-up Columns Sparingly**: While these columns offer powerful capabilities, use them judiciously to avoid unnecessary complexity.

- **Document Column Definitions**: Clearly document the purpose and usage of each column in your Dataverse project.

## Types of Relationships in Dataverse

### 1. One-to-many (1:N)

- **Description**: In a 1:N relationship, each record in the primary table can be associated with multiple records in the related table, but each record in the related table can only be associated with one record in the primary table.
- **Use Cases**:
  - A single office has many employees.
  - A teacher can teach multiple classes.
  - A customer can have many sales orders.
  - A customer can have many accounts.
 
### 2. Many-to-many (N:N)

- **Description**:  In an N:N relationship, each record in the primary table can be associated with multiple records in the related table, and each record in the related table can be associated with multiple records in the primary table.
- **Use Cases**:
  - Customers and products
  - Employees and skills
  - Users and communities
  - Orders and customers
  - Courses taken in a college

## Choosing the Correct Type of Relationship
When choosing the correct type of relationship to use, you need to consider the following factors:

-**What is the cardinality of the relationship?** The cardinality of a relationship refers to the number of records in one table that can be associated with a single record in the other table. In a 1:N relationship, the cardinality is one-to-many, while in an N:N relationship, the cardinality is many-to-many.

-**Do you need to store additional data about the relationship?** If you need to store additional data about the relationship, such as the date and time the relationship was established or the role of one record in the relationship to the other, you will need to create an N:N relationship.

# Advanced Settings and Behaviors of Relationships in Dataverse
When you create a relationship in Dataverse, you can configure a number of advanced settings, including the following:

-**Referential integrity**: Referential integrity ensures that the data in the two tables is consistent. For example, if you delete a record from the primary table, you can choose to have the related records in the related table automatically deleted as well.

-**Cascade behavior**: Cascade behavior controls what happens to the related records in the related table when you update or delete a record in the primary table. For example, if you update a record in the primary table, you can choose to have the related records in the related table automatically updated as well.

### Permutation and Combination of Behavior of Relationships in Context to Referential, Parental, and Custom

The following table explains the permutation and combination of the behavior of relationships in the context to referential, parental, and custom:

| Relationship Type   | Referential Integrity | Parental | Custom |
|---------------------|-----------------------|----------|--------|
| One-to-Many (1:N)  | Yes                   | Yes      | Yes    |
| Many-to-Many (N:N) | Yes                   | Yes      | Yes    |

### Permutation and Combination of Each Type in Context to Remove Link, Restrict, Delete, Assign, Share, Unshare, Reparent, etc
The following table explains the permutation and combination of each type in context to remove link, restrict, delete, assign, share, unshare, reparent, etc.:

| Behavior     | Remove Link | Restrict | Delete | Assign | Share | Unshare | Reparent |
|--------------|-------------|----------|--------|--------|-------|---------|----------|
| Referential  | Yes         | Yes      | Yes    | Yes    | Yes   | Yes     | No       |
| Parental     | Yes         | Yes      | Yes    | No     | No    | No      | Yes      |
| Custom       | Yes         | Yes      | Yes    | Yes    | Yes   | Yes     | Yes      |

By understanding the different types of relationships available in Dataverse and how to configure them, you can create a data model that accurately reflects the relationships between your entities. This will help you to improve the quality and accuracy of your data and make it easier to query and analyze your data.

## Best Practices

-**Normalize your data**: Data normalization is the process of organizing your data into a logical and efficient structure. This includes creating separate tables for different types of entities and using relationships to connect the tables.

-**Use the correct relationship type**: There are two types of relationships in Dataverse: one-to-many and many-to-many. Choose the correct relationship type based on the cardinality of the relationship.

-**Set appropriate referential integrity constraints**: Referential integrity constraints ensure that the data in the two tables is consistent. For example, if you delete a record from the primary table, you can choose to have the related records in the related table automatically deleted as well.

-**Use cascade behavior to automate updates and deletes**: Cascade behavior controls what happens to the related records in the related table when you update or delete a record in the primary table. You can configure cascade behavior to automatically update or delete related records, or to prevent updates and deletes from cascading.

-**Use lookup fields to link records between tables**: Lookup fields allow you to link records from one table to another table. Lookup fields are more efficient than storing foreign keys in the tables, and they also make it easier to maintain the relationships between tables.

-**Use relationship filtering to improve performance**: Relationship filtering allows you to filter related records based on criteria that are specific to the relationship. This can improve the performance of queries that involve related records.

-**Document your relationships**: It is important to document the relationships between your tables. This will help you to understand how your data is connected and make it easier to maintain your data model in the future.

-**Use descriptive relationship names**: Give your relationships descriptive names that accurately reflect the relationship between the two tables. This will make it easier to understand your data model.
-**Avoid creating circular relationships**: Circular relationships can cause performance problems and make it difficult to maintain your data model.

-**Use caution when deleting relationships**: Deleting a relationship can have unintended consequences. It is important to understand the impact of deleting a relationship before you do it.

-**Test your relationships**: It is important to test your relationships before you deploy them to production. This will help you to identify any potential problems with your relationships.
