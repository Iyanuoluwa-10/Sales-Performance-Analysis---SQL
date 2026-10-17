# SQL Project

## Project Title: Sales Performance Analysis

### Project Overview
This project uses SQL Server Management Studio to explore, analyze sales dataset, and answer relevant business questions.

### Tools Used
- SQL Server Management Studio for Importing data, accessing database tables, writing and executing SQL queries, and viewing query results
- GitHub for portfolio building

### Data Loading and Preparation
The data was imported into SQL Server Management Studio, the database table, column names and data types were inspected, and the data was prepared for querying and analysis.

### Exploratory Data Analysis
EDA involved the exploring of the data to answer some questions such as:
- What is total sales for each product category?
- What is the number of sales transactions in each region?
- What is the the highest-selling product by total sales value?
- What is the monthly sales for each product?

### Data Analysis
The following SQL queries were used to analyse the sales data

 Total Sales by Product Category
 ```sql
SELECT PRODUCT, SUM(TOTAL_REVENUE) AS [TOTAL SALES FOR EACH PRODUCT] FROM [dbo].[LITA CAPSTONE CSV] GROUP BY PRODUCT
```
<img width="1084" height="479" alt="Total sales for each product" src="https://github.com/user-attachments/assets/59810b7c-7d2b-4bd4-bf15-63af450a9c2d" />

Number of Sales Transactions per Region
```sql
SELECT REGION, COUNT(QUANTITY) AS [NUMBER OF SALES TRANSACTION] FROM [dbo].[LITA CAPSTONE CSV] GROUP BY REGION
```
<img width="1071" height="470" alt="Number of sales transaction per region" src="https://github.com/user-attachments/assets/88a0d48d-2621-4d71-850b-c4a4fb9b38f6" />

Highest Selling Product
```sql
SELECT TOP 1 PRODUCT, SUM(TOTAL_REVENUE) AS [HIGHEST SELLING PRODUCT] FROM [dbo].[LITA CAPSTONE CSV] GROUP BY PRODUCT 
ORDER BY [HIGHEST SELLING PRODUCT] DESC
```
<img width="1066" height="379" alt="Highest selling product" src="https://github.com/user-attachments/assets/e875e0da-bae9-4352-93c8-7649a0f3c345" />

Total Revenue per product
```sql
SELECT PRODUCT, SUM(TOTAL_REVENUE) AS [TOTAL REVENUE PER PRODUCT] FROM [dbo].[LITA CAPSTONE CSV] GROUP BY PRODUCT 
```
<img width="1072" height="517" alt="Total revenue per product" src="https://github.com/user-attachments/assets/0a46f1e8-9515-48b6-881b-aa5eb34902a9" />

Monthly Sales Total for the Current Year
```sql
SELECT MONTH(ORDERDATE)AS [MONTH],SUM(TOTAL_REVENUE)AS [MONTHLY SALES]FROM [dbo].[LITA CAPSTONE CSV]
WHERE YEAR(ORDERDATE)= '2024' GROUP BY MONTH(ORDERDATE) ORDER BY MONTH
```
<img width="1072" height="523" alt="Monthly sales" src="https://github.com/user-attachments/assets/88d9d7c8-ee7c-45f2-bb43-c7c5175b6e65" />

Top 5 Customers
```sql
SELECT TOP 5 CUSTOMER_ID, SUM(TOTAL_REVENUE)AS [TOTAL PURCHASE AMOUNT] FROM [dbo].[LITA CAPSTONE CSV] GROUP BY CUSTOMER_ID 
ORDER BY [TOTAL PURCHASE AMOUNT] DESC
```
<img width="1071" height="508" alt="Top 5 customers" src="https://github.com/user-attachments/assets/e68ad591-e556-4613-84e2-d92bebd8135a" />

Percentage of Total Sales by each Region
```sql
SELECT REGION, SUM(TOTAL_REVENUE) AS [REGION SALES], SUM (TOTAL_REVENUE)*100/SUM(SUM(TOTAL_REVENUE)) OVER()AS [PERCENTAGE OF TOTAL SALES]
FROM [dbo].[LITA CAPSTONE CSV] GROUP BY REGION 
```
<img width="1077" height="419" alt="Percentage of total sales" src="https://github.com/user-attachments/assets/ddb679bf-01fa-4df9-8967-328212eb3993" />

Products with no sales in the last quarter
```sql
SELECT DISTINCT PRODUCT FROM [dbo].[LITA CAPSTONE CSV] WHERE PRODUCT NOT IN(
SELECT DISTINCT PRODUCT FROM [dbo].[LITA CAPSTONE CSV]
WHERE ORDERDATE >=DATEADD(MONTH, -3,
(SELECT MAX(ORDERDATE) FROM [dbo].[LITA CAPSTONE CSV])
 )
```
<img width="1068" height="497" alt="Products with no sales in the last quarter" src="https://github.com/user-attachments/assets/e724b905-f82f-4a2e-a934-183758eb77ac" />


