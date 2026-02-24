DAX Measures — Amazon India E-Commerce Dashboard
Overview
All measures in this project were written in DAX and stored in the Fact_Sales_Amazon table. Measures are organized into two categories — Core Measures and Time Intelligence Measures. Time intelligence measures require the Dim_Date table to be marked as a Date Table in Power BI, which was implemented using the CALENDAR() function.

Total Sales = 
SUM(Fact_Sales_Amazon[Sales_Amount])
Total Profit = 
SUM(Fact_Sales_Amazon[Profit])
Profit Margin % = 
DIVIDE([Total Profit], [Total Sales], 0)
Total Orders = 
DISTINCTCOUNT(Fact_Sales_Amazon[Order_ID])
Average Order Value = 
DIVIDE([Total Sales], [Total Orders], 0)
Assumed Cost = 
[Total Sales] - [Total Profit]

Time Intelligence Measures
Sales YTD = 
TOTALYTD([Total Sales], Dim_Date[Order_Date])
Sales YTD LY = 
CALCULATE(
    [Sales YTD],
    SAMEPERIODLASTYEAR(Dim_Date[Order_Date])
)

Sales YTD Growth % = 
DIVIDE(
    [Sales YTD] - [Sales YTD LY],
    [Sales YTD LY],
    0
)
Why DIVIDE() and Not Division Operator
All division in this project uses the DAX DIVIDE() function instead of the / operator. This is because DIVIDE() handles division by zero gracefully by returning the alternate result — in this case 0 — instead of returning an error. This is both a PL-300 best practice and a real-world data quality safeguard.

Why Time Intelligence Requires a Marked Date Table
For TOTALYTD() and SAMEPERIODLASTYEAR() to work correctly in Power BI, the Date Table must be explicitly marked as a Date Table. This was done by right clicking Dim_Date in the model view and selecting Mark as Date Table. Without this step time intelligence functions return blank or incorrect results — something I discovered and corrected during this project.
