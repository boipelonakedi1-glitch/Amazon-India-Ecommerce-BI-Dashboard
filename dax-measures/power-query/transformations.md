Power Query Transformations — Amazon India E-Commerce Dashboard
Overview
All data cleaning and transformation for this project was completed entirely in Power Query inside Power BI Desktop. No changes were made to the original source file. The raw data was a single flat Excel file which was restructured into a star schema consisting of one fact table and two dimension
tables.
Power Query Transformations — Amazon India E-Commerce Dashboard
Overview
All data cleaning and transformation for this project was completed entirely in Power Query inside Power BI Desktop. No changes were made to the original source file. The raw data was a single flat Excel file which was restructured into a star schema consisting of one fact table and two dimension tables.

Transformations Applied to Fact_Sales_Amazon
1. Changed Date Column Data Type
The Order_Date column was loaded as text from the source file. This was changed to a proper Date data type in Power Query. This step was critical — without it the Dim_Date relationship could not be established and all time intelligence DAX measures returned blank or incorrect values. This was one of the most important lessons learned during this project.

3. Removed Irrelevant Columns
Columns that added no analytical value to the dashboard were removed to keep the fact table lean and focused on measurable transactional data.
4. Renamed Columns
All column names were standardized to remove spaces and special characters, using underscore format for clean DAX referencing. For example "Order ID" became Order_ID and "Sales Amount" became Sales_Amount.
5. Filtered Null and Zero Value Rows
Rows where Sales_Amount was null were filtered out to prevent distortion in profitability and margin calculations.
6. Hidden Foreign Key Columns
Geography_Key, SKU and other foreign key columns used only for table relationships were hidden from report view to keep the field list clean for end users.

Dim_Date Table
Method Used
Dim_Date was created using the DAX CALENDAR() function rather than in Power Query. This is the recommended approach in Power BI as it ensures every single date is present with no gaps, which is required for time intelligence functions to work correctly.
Columns in Dim_Date

Order_Date
Month Name
Month Number
Month Year
Quarter Number

Marked as Date Table
After creation Dim_Date was right clicked in Model View and marked as a Date Table using the Order_Date column as the unique date identifier. This step is mandatory for TOTALYTD() and SAMEPERIODLASTYEAR() to function correctly.

Dim_Product Table
Method Used
Dim_Product was created by referencing the Fact_Sales_Amazon table in Power Query, keeping only the descriptive product attribute columns — SKU, Category, Size and Geography_Key — and then removing duplicates to produce one unique row per product.
Why This Matters
Moving descriptive attributes out of the fact table and into a dedicated dimension table is a core principle of star schema design. It reduces redundancy, improves query performance and makes DAX measures more reliable.

Key Lesson Learned
The most significant data quality issue encountered in this project was the date column formatting error. The raw data dates loaded incorrectly which caused the entire time intelligence layer of the model to fail silently — the measures returned values but they were wrong. The fix required going back to Power Query to correct the data type at source rather than trying to fix it in DAX. This reinforced a fundamental BI principle — always validate your data at the source before trusting your measures.
