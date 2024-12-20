# LITA_CAPSTONE_PROJECT_1
This repository contains my final project as a newbie Data Analyst, showing my skills in data analysis, visualization, and insights extraction.

### PROJECT TITLE:-RETAIL STORE SALES PERFORMANCE ANALYSIS

[PROJECT OVERVIEW](#project-overview)

[DATA SOURCES](#data-sources)

[DATA DESCRIPTION](#data-description)

[TOOLS USED](#tools-used)

[DATA CLEANING AND PREPARATIONS](#data-cleaning-and-preparations)

[EXPLORATORY DATA ANALYSIS](#exploratory-data-analysis)

[DATA ANALYSIS](#data-analysis)

[DATA VISUALIZATION](#data-visualization)

### PROJECT OVERVIEW
---
Project Objective:

To analyze the sales performance of a retail store across four regional divisions over a 2-year period, identifying key insights and trends to inform business decisions.

Project Scope:

This project will:

1. Explore sales data to uncover key insights on top-selling products, regional performance, and monthly sales trends.
2. Analyze sales data to identify areas of strength and weakness.
3. Develop an interactive Power BI dashboard to visualize sales performance.

Specific Goals:

1. Identify top-selling products by region 
2. Evaluate regional sales performance and trends.
3. Analyze monthly sales trends and seasonality.
4. Create a user-friendly Power BI dashboard for stakeholder access.

Timeline: 2 years

Deliverables:

1. Interactive Power BI dashboard
2. Written report summarizing key findings and insights

Assumptions:

1. Access to reliable sales data
2. Availability of necessary resources and tools

Expected Outcomes:

1. Improved understanding of sales performance
2. Data-driven insights for informed business decisions
3. Enhanced sales strategy and planning

### DATA SOURCES
---
The primary source of Data used here is Sales Data of a Retail Store across four regional divisions. 
Its an excel data provided by The Incubator Hub LITA facilitators, the data was converted to CSV format, before importing to SQL, for easy and seamless analysis. 

### DATA DESCRIPTION
---
The dataset includes the following fields:
1. Order ID : Order ID is the unique identifier assigned to a specific order 
2. Customer ID : Unique identifier given to each customers
3. Products: product is a tangible or intangible offering that meets the needs or wants of customers sold in the retail store. (Shirt, Gloves, Hat, Shoes, Socks and Jacket)
4. Region: The regional branches of the store (North, South, East and West)
5. Order Date: Dates transactions were made
6. Quantity: Quantity refers to the number of units of the product sold
7. Unit Price: The unit price is the cost per single unit of the product
8. Sales Revenue: Income from selling a products.
   It is calculated as  Sales Revenue = Quantity Sold x Unit Price


### TOOLS USED
---
1.  Microsoft Excel: [Download here](https://www.microsoft.com);
    In this Sale Performance Analysis Project i used Excel for
    - Data cleaning and formatting
    - Pivot tables for data summarization
    - Formulas for calculations (e.g., average sales, total revenue)
    - Data analysis and filtering.

2.  SQL- Structured Query Language [Download here](https://www.microsoft.com/en-us/sql-server/sql-server-downloads?msockid=2b7beaf97efb6b170d9dfff87f1b6a9f);
    In this Sales Performance Analysis i used SQL Server Environment for;
     -  Loading and managing sales data
     -  Writing queries to extract insights
     -  Performing aggregations and grouping
     -  Creating views and stored procedures
     -  Integrating with Power BI for data visualization
     -  Performing data analysis and reporting

3.  Power BI:
    In this Sales Performance Analysis i used Power BI for the following;
     -  For Creating interactive dashboards
     -  Visualizing sales data (e.g., bar charts, line charts, maps)
     -  Creating calculated fields and measures (DAX)
     -  Displaying top-performing products and categories
     -  Showcasing regional sales trends

4. Github for portfolio building [Click here to sign up](https://github.com/)
     -  For Sharing and tracking changes to code
     -  For Collaborating with team members
     -  For Documenting analysis process
     -  For Sharing results and insights
     -  Version control for data files

### DATA CLEANING AND PREPARATIONS
---
In the initial phase of the data cleaning and preparations, I perform the following actions;
1. Data loading and inspection; data quality was ensured by correcting any spelling error.
2. Handling missing variables
3. Data cleaning and formatting
4. Data import from Excel to SQL and Power BI

### EXPLORATORY DATA ANALYSIS
---
EDA involved the exploring of the data to answer some questions about the data such as:
This analysis will involve a deep exploration of the data to answer key questions that are essential for effective decision-making. These include:
1. Determining the total sales for each product category
2. Counting the number of sales transactions in each region
3. Identifying the highest-selling product based on total sales value
4. Calculating the total revenue for each product
5. Summing monthly sales totals for the current year
6. Finding the top 5 customers by total purchase amount
7. Calculating each region’s percentage contribution to total sales
8. Identifying products with no sales in the last quarter

### DATA ANALYSIS
---
Here are some basic lines of code, queries & some of the DAX expressions used during my analysis;

```SQL
SELECT * FROM [dbo].[SALESDATA]

---RETRIEVING THE TOTAL SALES OF EACH PRODUCT CATEGORY---

SELECT * FROM [dbo].[SALESDATA]

SELECT PRODUCT, 
SUM(QUANTITY*UNITPRICE) AS TOTALSALE
FROM [dbo].[SALESDATA]
GROUP BY PRODUCT;

---FINDING THE NUMBER OF SALES TRANSACTIONS IN EACH REGION---

SELECT REGION, 
COUNT(*) AS NUMBEROFTSALESTRANSACTIONS
FROM [dbo].[SALESDATA]
GROUP BY REGION;

---FINDING THE HIGHEST-SELLING PRODUCT BY TOTAL SALES VALUE---

SELECT TOP 1 PRODUCT, 
SUM(QUANTITY*UNITPRICE) AS TOTALSALES
FROM [dbo].[SALESDATA]
GROUP BY PRODUCT
ORDER BY TOTALSALES DESC;

---CALCULATING TOTAL REVENUE PER PRODUCT---

SELECT PRODUCT, 
SUM(QUANTITY*UNITPRICE) AS TOTALREVENUE
FROM [dbo].[SALESDATA]
GROUP BY PRODUCT
ORDER BY  TOTALREVENUE DESC;

---CALCULATING MONTHLY SALES TOTALS FOR THE CURRENT YEAR---

SELECT MONTH(ORDERDATE) AS MONTH, 
SUM(QUANTITY*UNITPRICE) AS MONTHLYSALES
FROM [dbo].[SALESDATA]
WHERE YEAR(ORDERDATE) = YEAR(GETDATE())
GROUP BY MONTH(ORDERDATE)
ORDER BY MONTH;

---FINDING THE TOP 5 CUSTOMERS BY TOTAL PURCHASE AMOUNT---

SELECT TOP 5 CUSTOMER_ID, 
SUM(QUANTITY*UNITPRICE) AS TOTALPURCHASEAMOUNT
FROM [dbo].[SALESDATA]
GROUP BY CUSTOMER_ID
ORDER BY TOTALPURCHASEAMOUNT DESC;

---CALCULATING THE PERCENTAGE OF TOTAL SALES CONTRIBUTED BY EACH REGION---

SELECT REGION, 
SUM(QUANTITY*UNITPRICE) AS TOTALSALES,
(SUM(QUANTITY*UNITPRICE) * 1.0 / (SELECT SUM(QUANTITY*UNITPRICE) 
FROM [dbo].[SALESDATA])) * 100 
AS PERCENTAGEOFTOTALSALES
FROM [dbo].[SALESDATA]
GROUP BY REGION
ORDER BY TOTALSALES DESC;

--- IDENTIFYING PRODUCTS WITH NO SALES IN THE LAST QUARTER---

SELECT Product FROM salesdata
GROUP BY Product
HAVING SUM(CASE 
WHEN OrderDate BETWEEN '2024-06-01' AND '2024-08-31' 
THEN 1 ELSE 0 END) = 0
``` 

### DATA VISUALIZATION
---


 



 
