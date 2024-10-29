# LITA-Projects-Assignment

### Project Title: Sales Data

### Project Overview
This is an analysis and visualization of sales data using Excel, SQL, and Power BI, to uncover trends for strategic decision-making. This project, part of my GitHub portfolio, showcases my proficiency in data storytelling and highlights my ability to transform raw data into actionable insights with advanced tools confidently.

### Data Source
Our facilitator provided this dataset

### Dataset Description
This dataset contains various details of products sold in a store in a different geographical area. These types of datasets are studied to find out the patterns in the selling structure, profit earned from them, and order history. This data contains 9921 rows and 7 columns, while a missing key column was added in the cleaning process, making it a total of 8 columns.

---

### Key Features:
**OrderID**: A unique identifier for each customer's order
**CustomerID**: Each customer's unique ID
**Product**: The name of the product ordered
**Region**: The region in which the order was placed
**OrderDate**: The date the product was ordered
**Quantity**: The quantity of the product ordered
**UnitPrice**: The unit price for each product
**Revenue**: The revenue derived from the product sold


### Data Tools
* Microsoft Excel, for:
  > Data cleaning;
  > Data Analysis and Summarization.
* SQL [Structured Query Language] for Querying data
* Power BI for Data Visualization
* GitHub for Portfolio building


## Microsoft Excel [VIEW PROJECT](https://us.docworkspace.com/d/sIJyeupNZi_f6uAY)
---
Microsoft Excel is a spreadsheet tool for data organization (cleaning and preparation), analysis, and visualization. It offers formulas, pivot tables, and charts, enabling users to manage and interpret data.

**Data Cleaning and Preparation**: Processing the raw data to ensure it is ready for analysis. Steps taken:
> Removing Duplicates: The initial rows of the data were 50001, but after removing duplicates, 9921 rows were left. No missing values were found; 
> Adding filters;
> Adding conditional formatting


### Exploratory Data Analysis
The following insights will be drawn:
* Which region has the highest sales?
* What product was sold the most?
* What month had the highest sales each year?
* What quantity of product was sold in each month of the year?
* What is the total number of products sold in the year?
* What is the total revenue of products sold in each region?
* Which region is best for business?
* Which product should the business focus more on?
* What is the total revenue derived from each product?
* What is the average sales for each product? And many more...


  ### Data Visualization
  **Pivot Table** a data summarization tool found in MS Excel was used for visualization.

1. **Region with the highest Sales**:	

![Total Sales by Region](https://github.com/user-attachments/assets/e21be676-1260-43d9-8733-0bd46bafbff7)
![image](https://github.com/user-attachments/assets/a2607c1f-ec43-4789-ae57-180d2d744781)


**key Finding**
Based on this analysis, the South Region has the highest sales, followed by the East Region, while the West Region has the lowest sales. Though the business is doing well in all regions, it should focus more on the South Region, which has a huge sales difference from others.

2. **Product that was sold the most**;

![Total Sales by Product](https://github.com/user-attachments/assets/c3d7def7-d6cb-442f-9b9f-6bed8c281312)
![image](https://github.com/user-attachments/assets/ae64607c-3a54-44a8-8888-442004daaf8e)


**Key Finding**
This analysis shows that shoes were the the most sold product with a total of 613,380 followed by shirts which had a total of 485,600 and socks coming as the least with totals of 180,785. 

3. **What month had the highest sales each year**;

![Total Sales by Month](https://github.com/user-attachments/assets/dc651dfe-c073-44af-ab93-6170d3a965b8)
![image](https://github.com/user-attachments/assets/04b218d5-72fd-4016-82c8-441da280d5f6)


**Key Finding**
It shows that in 2023 and 2024, February had the highest sales. July was the second-highest sales in 2023, but in 2024, Jul declined in sales, and Jan had the second-highest total sales.

4. **What are the average sales of products sold**;
   
![Average Sales by Product](https://github.com/user-attachments/assets/8de4825c-6816-484f-b2b4-a5a1645913c4)
![image](https://github.com/user-attachments/assets/14fab66c-0922-4257-bf9d-904574c40e2d)


5. **What is the total revenue of products sold in each region**?    
  
![Total Revenue by Region](https://github.com/user-attachments/assets/715259c0-4a91-4015-9ea2-5bdc5e827e79)
![image](https://github.com/user-attachments/assets/ce788d61-9f5a-4b31-b28b-8f0848ddf26e)


6. **What is the total No of products sold in a month at each region**;

![Total Product by Month and Region](https://github.com/user-attachments/assets/aaa55f49-39b6-4f95-bc80-ec2a4d9ae108)

**Key Findings**
In this analysis, lots of insights were generated. It answers the questions:

  * What is the total No of products sold in 2023? **5,952**
  * How many product types were sold in each month? **1**
  * How many products were sold in Jan? **496**
  * What is the total No of products sold in 2024? **3,969**
    
In Summary, the business focuses on a particular type of product and a specific region each month. There was only a change in the product type in August when the business initially sold shoes in 2023 but later changed to selling Hats in 2024.  
  

## SQL (STANDARD QUERY LANGUAGE)
---
It is used for querying, storing and managing data in a database. The following queries: were derived in the analysis:

1. Total sales for each Product Category:

~~~ SQL
SELECT Product, SUM(Quantity * UnitPrice) AS TotalSales
FROM [dbo].[LITA Capstone Dataset]
GROUP BY Product;
~~~

2. Find the number of sales transactions in each region:

~~~ SQL
SELECT Region, count(quantity * UnitPrice) AS SalesCount
from [dbo].[LITA Capstone Dataset]
group by region
~~~

3. Find the highest-selling product by total sales value:
   
~~~ SQL
SELECT Product, SUM(Quantity * UnitPrice) AS TotalSales
FROM [dbo].[LITA Capstone Dataset]
GROUP BY Product
order by 2 desc
~~~

4. Calculate total revenue per product:

~~~ SQL
SELECT Product, SUM(Quantity * UnitPrice) AS TotalRevenue
FROM [dbo].[LITA Capstone Dataset]
GROUP BY Product
~~~

5. calculate monthly sales totals for the current year:

~~~ SQL
SELECT 
    MONTH(OrderDate) AS Month, SUM(Quantity * UnitPrice) AS MonthlySales
FROM [dbo].[LITA Capstone Dataset]
WHERE YEAR(OrderDate) = YEAR(GETDATE())
GROUP BY  MONTH(OrderDate)
ORDER BY Month;
~~~

6. Find the top 5 customers by total purchase amount:

~~~ SQL
SELECT Top 5 Customer_Id, SUM(Quantity * UnitPrice) AS TotalPurchase
FROM [dbo].[LITA Capstone Dataset]
GROUP BY Customer_Id
ORDER BY TotalPurchase DESC
~~~

7. Calculate the percentage of total sales contributed by each region:

~~~ SQL
SELECT Region, sum(Quantity * UnitPrice) as TotalSales,
(SUM(Quantity * UnitPrice) * 100.00 / (SELECT SUM(Quantity * UnitPrice) 
from [dbo].[LITA Capstone Dataset] as PercentageOfTotalSales
WHERE  PercentageOfTotalSales
~~~

8. Identify products with no sales in the last quarter:

~~~ SQL
SELECT Product
FROM [dbo].[LITA Capstone Dataset]
WHERE Product NOT IN (
        SELECT DISTINCT Product
        FROM [dbo].[LITA Capstone Dataset]
        WHERE OrderDate >= DATEADD(QUARTER, -1, GETDATE())
    );
~~~


## POWER BI
A data Visualization and business intelligence tool for converting data from different sources to interactive dashboards.
