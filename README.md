# SQL Project

## Project Title: Sales Performance Analysis

### Project Overview: 

### Tools Used
- SQL Server Management Studio for Importing data, accessing database tables, writing and executing SQL queries, and viewing query results
- GitHub for portfolio building

### Data Preparation
The data was imported into SQL Server Management Studio and it was 

### Exploratory Data Analysis
EDA involved the exploring of the data to answer some questions such as:
- What is total sales for each product category?
- What is the number of sales transactions in each region?
- What is the the highest-selling product by total sales value?

### Data Analysis
The queries used in analyzing the data are:
 Total Sales by Product Category
 Calculated total sales for each product category to compare their sales performance.
 ```SELECT PRODUCT, SUM(TOTAL_REVENUE) AS [TOTAL SALES FOR EACH PRODUCT] FROM [dbo].[LITA CAPSTONE CSV] GROUP BY PRODUCT
```

**SQL Query**
```sql
-- Insert your actual SQL query here
```

**Result**

![Sales by Product Category](screenshots/01-sales-by-category.png)

**Insight:** Add the category with the highest sales value based on your results.
```SELECT PRODUCT, SUM(TOTAL_REVENUE) AS [TOTAL SALES FOR EACH PRODUCT] FROM [dbo].[LITA CAPSTONE CSV] GROUP BY PRODUCT

SELECT REGION, COUNT(QUANTITY) AS [NUMBER OF SALES TRANSACTION] FROM [dbo].[LITA CAPSTONE CSV] GROUP BY REGION

SELECT TOP 1 PRODUCT, SUM(TOTAL_REVENUE) AS [HIGHEST SELLING PRODUCT] FROM [dbo].[LITA CAPSTONE CSV] GROUP BY PRODUCT 
ORDER BY [HIGHEST SELLING PRODUCT] DESC

SELECT PRODUCT, SUM(TOTAL_REVENUE) AS [TOTAL REVENUE PER PRODUCT] FROM [dbo].[LITA CAPSTONE CSV] GROUP BY PRODUCT 

SELECT MONTH(ORDERDATE)AS [MONTH],SUM(TOTAL_REVENUE)AS [MONTHLY SALES]FROM [dbo].[LITA CAPSTONE CSV]
WHERE YEAR(ORDERDATE)= '2024' GROUP BY MONTH(ORDERDATE) ORDER BY MONTH

SELECT TOP 5 CUSTOMER_ID, SUM(TOTAL_REVENUE)AS [TOTAL PURCHASE AMOUNT] FROM [dbo].[LITA CAPSTONE CSV] GROUP BY CUSTOMER_ID 
ORDER BY [TOTAL PURCHASE AMOUNT] DESC

SELECT REGION, SUM(TOTAL_REVENUE) AS [REGION SALES], SUM (TOTAL_REVENUE)*100/SUM(SUM(TOTAL_REVENUE)) OVER()AS [PERCENTAGE OF TOTAL SALES]
FROM [dbo].[LITA CAPSTONE CSV] GROUP BY REGION 

SELECT DISTINCT PRODUCT FROM [dbo].[LITA CAPSTONE CSV] WHERE PRODUCT NOT IN(
SELECT DISTINCT PRODUCT FROM [dbo].[LITA CAPSTONE CSV]
WHERE ORDERDATE >=DATEADD(MONTH, -3,
(SELECT MAX(ORDERDATE) FROM [dbo].[LITA CAPSTONE CSV])
 )
```
);
