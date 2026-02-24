# Amazon-India-Ecommerce-BI-Dashboard
My first BI portfolio project. Amazon India e-commerce profitability dashboard built in Power BI with a star schema data model, DAX time intelligence and executive-level report design. Download the PBIX file to explore locally.
Executive Performance Dashboard | Microsoft Power BI

"Data is only as powerful as the story it tells. This project taught me how to find that story."
— Boipelo Rethabile Nakedi
👋 About This Project
My name is Boipelo Rethabile Nakedi and this is my first end-to-end Business Intelligence portfolio project.
I built this dashboard while simultaneously studying for the Microsoft PL-300 Power BI Data Analyst Certification — which meant every concept I learned in theory, I immediately put into practice here. Star schemas, DAX time intelligence, data modeling, semantic design — I learned it, then I built it. That process was equal parts challenging and deeply rewarding.
This project represents more than a dashboard. It represents my transition into the tech industry — a deliberate, structured leap from where I was to where I am determined to go. I am actively pursuing roles as a Data Analyst and Business Intelligence Analyst, and this project is my proof of work.

🎯 Project Objective
Analyze Amazon India e-commerce sales performance to evaluate revenue trends, profitability, product performance and category contribution — in order to support strategic and operational decision-making.
Every visual, every measure, every design decision in this dashboard was built to serve that objective. Nothing exists on this dashboard without a business reason
![Executive Dashboard Overview](Executive_Overview)
📁 Repository Contents
To interact with the dashboard download the .pbix file and open it in Power BI Desktop which is completely free to download. All visuals, slicers, drill-downs and measures are fully functional. The dashboard is also shared as static screenshots for quick viewing directly on GitHub.
The repository contains the full Power BI Desktop file, static screenshots of the executive dashboard and semantic model, and the full 10-slide portfolio presentation.

📦 Dataset Context
Source: Amazon India Sales Channel — transactional e-commerce data
Scope: Amazon India only — one channel, one country, focused analysis
Rows: 731 transactional records
Key Columns: SKU Code, Product Category, Order Date, Sales Amount, Order Quantity, Fulfilment Method, Courier Status, B2B Flag, Size, ASIN, Ship State, Ship City
A note on scope — this project deliberately uses one dataset out of six that were available. The choice to focus on a single channel allowed for a cleaner, more honest analysis rather than surface-level coverage of many datasets. A BI analyst who can tell a complete story with constrained data is more valuable than one who needs everything.

🏗️ Data Modeling — Star Schema Architecture
One of the skills I was most intentional about demonstrating in this project is proper data modeling. Rather than working from a flat file I restructured the raw data into a star schema following Kimball methodology.
The model has three tables. Fact_Sales_Amazon sits at the center and contains all transactional data including Order ID, Order Date, Sales Amount, Order Quantity, Fulfilment method, Status and B2B flag. Dim_Date connects to the fact table on Order Date and contains Month Name, Month Number, Month Year, Quarter Number and Order Date. Dim_Product connects to the fact table and contains SKU, Category and Size and.
Key modeling decisions made:
Foreign keys and technical columns are hidden from report view for a clean user experience. Dim_Date was built using the CALENDAR() function and marked as a Date Table to enable time intelligence. Category and descriptive attributes are kept in Dim_Product and not duplicated in the fact table. One-to-many relationships are properly configured from each dimension table into the fact table.

📐 DAX Measures Built
Core Measures:
Total Sales = SUM of the Sales Amount column from the fact table
Total Profit = SUM of the Profit column from the fact table
Profit Margin % = DIVIDE of Total Profit by Total Sales with zero as the alternate result
Total Orders = DISTINCTCOUNT of the Order ID column
Total Quantity = SUM of the Order Quantity column
Average Order Value = DIVIDE of Total Sales by Total Orders with zero as the alternate result
Time Intelligence Measures:
Sales YTD = TOTALYTD of Total Sales using the Order Date from Dim_Date
Sales YTD LY = CALCULATE of Sales YTD using SAMEPERIODLASTYEAR on the Order Date
Sales YTD Growth % = DIVIDE of the difference between Sales YTD and Sales YTD LY by Sales YTD LY with zero as the alternate result
Time intelligence measures require the Date Table to be properly marked in Power BI. This is both a PL-300 exam requirement and a real-world best practice I implemented intentionally.

📊 Dashboard Overview
Executive KPIs at a Glance:
Total Sales — 16.53K
Total Profit — 4.96K
Profit Margin % — 30%
Total Orders — 30
Sales Growth % — 32.3%
Visuals on the Dashboard:
Five KPI cards deliver business health at a glance. A pie chart shows Profit by Category. A waterfall chart shows Profit Margin % by Category. A combo chart shows Total Sales and Profit by Month Year with a trend line. A clustered horizontal bar chart shows Total Orders and Total Quantity by Category. A product performance table shows SKU-level Sales, Profit and Margin detail. A hierarchy slicer enables filtering by Year and Quarter.

💡 Key Business Insights
1. Category Concentration Risk
The Set category contributes 66% of total sales and profit. This level of dependency on a single product type represents a strategic risk. Leadership should evaluate diversification into Kurta and Western Dress categories which show growth potential.
2. Profit Margin Discipline
Despite a declining sales trend over time the overall profit margin holds steady at 30%. This indicates that cost control is effective even as top-line revenue falls — a positive signal for operational efficiency.
3. Strong Prior Period Growth
A Sales Growth Rate of 32.3% validates strong product-market fit in the Amazon India channel and sets a high benchmark for future performance targets.
4. Zero-Margin SKUs Require Attention
Several SKUs show 0% profit margin. These are immediate candidates for a pricing strategy review or product discontinuation to protect overall margin health.

🧗 Honest Reflections — The Highs and Lows
I want to be transparent about what this project was really like because I think honesty is more valuable than a polished story that makes everything sound easy.
The Highs
When I built the star schema and saw the relationships connect correctly for the first time I felt genuinely proud. Understanding why a star schema exists — not just how to build one — was a turning point for me. The moment my time intelligence DAX measures calculated correctly after days of troubleshooting felt like a real breakthrough.
Seeing the finished dashboard tell a complete business story — five KPI cards, a trend chart, category analysis, product-level detail, all on one page — made me realize I had crossed a line from learning to doing. That feeling is hard to describe but it is exactly why I chose this path.
The Lows
The date column gave me serious trouble. The raw data had formatting issues that caused my Order Date to load incorrectly which completely broke my time intelligence measures. I spent significant time diagnosing why my YTD calculations were returning wrong values before I realized the issue was upstream in Power Query and not in my DAX. That taught me that a BI analyst's first instinct when numbers look wrong should always be to go back to the source — not the formula.
I also struggled with the temptation to add more visuals than the dashboard needed. Early versions had duplicate category charts that answered the same question twice. Learning to remove things that look good but add no analytical value was a discipline I had to develop deliberately.
Signing into Power BI Service was a challenge due to organizational account restrictions during my studies which meant the dashboard is shared as a static file with a downloadable PBIX. That was frustrating but also a real-world lesson — constraints exist in professional environments and the ability to find a workable solution matters more than having perfect conditions.
What This Project Taught Me
This project taught me that building a dashboard is 20% technical skill and 80% analytical thinking. The hardest questions were never how do I write this DAX measure — they were what business question am I actually trying to answer and is this visual honestly answering it?

🎓 Certification Context
This project was built concurrently with my PL-300 Microsoft Power BI Data Analyst exam preparation. Every modeling decision, DAX pattern and design principle in this project maps directly to PL-300 curriculum topics including data modeling and star schema design, DAX measures and time intelligence functions, Power Query data transformation, report design and visual selection, and semantic model optimization.

🛠️ Tools and Technologies
Microsoft Power BI Desktop was used for dashboard development, DAX and data modeling. Power Query was used for data cleaning and transformation. DAX was used for all measure creation and time intelligence. Microsoft Excel was the raw data source. GitHub is used for version control and portfolio hosting.

🚀 About Me
I am Boipelo Rethabile Nakedi, an aspiring Data and Business Intelligence Analyst based in South Africa, actively transitioning into the tech industry.
I am passionate about turning raw data into decisions that matter. I believe that the most powerful thing an analyst can do is take something complex and overwhelming and make it instantly clear to the person who needs to act on it.
This is my first portfolio project. It will not be my last.
I am actively open to junior Data Analyst, BI Analyst and reporting analyst opportunities. If my work resonates with you I would love to connect.
LinkedIn: linkedin.com/in/boipelo-rethabile-n-433b5821a


Built with curiosity, persistence, and a lot of DAX debugging.
— Boipelo Rethabile Nakedi, 2026
