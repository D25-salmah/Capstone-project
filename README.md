# Capstone-project
Sales Analysis for a retail store##
##Project Overview
This is a project that helped with exposure into the powerful world of Data Analysis, how to begin, the tools needed installations and navigation of the tools. Having this knowledge is a plus to me as I currently work as a Quality Analyst and having to combine the tools and knowledge is progress for me thanks to the Incubator Hub for this great opportunity to learn! We will make use of various tools some of which are ; EXCEL, POWER BI and SQL. You will be surprised at how broad this tools are but equally user friendly once you have a hang of it and how it can help your business regardless of how small or big it is to get Data right.
##Data Source
The primary source of data we will be using majorly is Sales.csv gotten from capstone project.
Data tool##
Microsoft Excel Download here
For Data Cleaning
For Analysis
For Data Visualization
SQL - Structured Query Language for Querying of Data, data management and Retrieval
GitHub for Portfolio Building
Power BI for Data visualizationa and reporting
##Data Cleaning & Preparation
In the initial phase of the Data cleaning and preparation we performed the following actions;
Data Loading from the sources and inspection
Handling missing variables
Data cleaning and formatting
##Exploratory Data Analysis
This involved the utilization of Data we worked on, to answer some questions about the Data such as;
Who are the top 5 selling markets
what is the overall sales trend
What is the average of the total revenue
##Data Analysis
```SQL
SELECT *
FROM "Retail"
--- 1. Total Sales for each product category
SELECT "Retail"."Product", SUM("Revenue") AS TotalSales
FROM "Retail"
GROUP BY "Product"
ORDER BY TotalSales DESC;

--- 2. Number of sates transactions in each region
SELECT "Retail"."Region", COUNT("Revenue") AS TransactionCount
FROM "Retail"
GROUP BY "Region"
ORDER BY TransactionCount DESC;

--- 3. Highest selling product by total sales value
SELECT "Retail"."Product", SUM("Revenue") AS TotalSales
FROM "Retail"
GROUP BY "Product"
ORDER BY TotalSales DESC
LIMIT 1;

--- 4. Total Revenue per Product
SELECT "Retail"."Product", SUM("Revenue") AS TotalRevenue
FROM "Retail"
GROUP BY "Product"
ORDER BY TotalRevenue DESC;

--- 5. Monthly sales totals for the current year
SELECT "Retail"."Month", SUM("Revenue") AS MonthlySales
FROM "Retail"
WHERE "Year" = 2024  -- Replace with a specific year if needed
GROUP BY "Month"
ORDER BY "Month";

--- 6. Top 5 customers by total purchase amount
SELECT "Retail"."CustomerID", SUM("Revenue") AS TotalPurchaseAmount
FROM "Retail"
GROUP BY "CustomerID"
ORDER BY TotalPurchaseAmount DESC
LIMIT 5;

--- 7. The percentage of total sales contributed by each region
SELECT 
    "Retail"."Region",
    SUM("Revenue") AS RegionSales,
    (SUM("Revenue") * 100.0 / SUM(SUM("Revenue")) OVER ()) AS SalesPercentage
FROM "Retail"
GROUP BY "Region"
ORDER BY SalesPercentage DESC;

--- 8. Products with no sales in the last quarter
WITH LastQuarter AS (
    SELECT "Retail"."Product"
    FROM "Retail"
    WHERE 
        "OrderDate" >= (DATE_TRUNC('quarter', CURRENT_DATE) - INTERVAL '3 months')
        AND "OrderDate" < DATE_TRUNC('quarter', CURRENT_DATE)
)
SELECT "Product"
FROM "Retail"
WHERE "Product" NOT IN (SELECT "Retail"."Product" FROM LastQuarter)
GROUP BY "Product";
```

This is used to include some basic lines of code or queries or even some of the DAX expression used during our analysis;
Select * from Employee
Where condition = TRUE
##Data Visualization
This enables stakeholders to visually see the representation of data in ways to which it helps tell the beautiful story they need through the use of Charts, graphs,tables, matrix, maps to solve a problem
