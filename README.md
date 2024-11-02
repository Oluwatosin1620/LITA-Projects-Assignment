# LITA-Projects-Assignment

## Project Title: Sales Data

[Project Overview](project-overview)
[Key Features](ket-features)
[Data Tools](data-tools)
[Microsoft Excel](microsoft-excel)
[Exploratory Data Analysis ](exploratory-data-analysis)
[Insights Derived](insights-derived)
[SQL](SQL)
[POWER BI](power-bi)
 
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
  
**Insights Derived**:
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
    
In Summary, the business focuses on a particular product type and region each month. There was only a change in the product type in August when the business initially sold shoes in 2023 but later changed to selling Hats in 2024.  
  

## SQL (STANDARD QUERY LANGUAGE)
---
It is used for querying, storing and managing data in a database. The data that had already been cleaned up from Excel was imported.
The following queries were derived in the analysis:

**Insights Derived**:
1. Total sales for each Product Category:

~~~ SQL
SELECT Product, SUM(Quantity * UnitPrice) AS TotalSales
FROM [dbo].[LITA Capstone Dataset]
GROUP BY Product
order by TotalSales desc
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
A data Visualization and business intelligence tool for converting data from different sources to interactive dashboards. The following are required to be presented on the visualization tool:
1. Create a dashboard that visualises the Excel and SQL insights.
2. The dashboard should include a sales overview, top-performing products, and regional breakdowns.


![SalesData Dashboard](https://github.com/user-attachments/assets/65dc1381-99b4-43b4-a0c6-2c5f2cf85ab1)

![SalesData Dashboard 2](https://github.com/user-attachments/assets/ccd93d50-0671-4eb0-9e18-45d2be583782)


### INSIGHTS DRIVEN:

This analysis provides a comprehensive view of a business’s sales data over the past two years, focusing on 9,921 customers and tracking product sales across various regions. Initially, the dataset comprised 50,001 rows and 7 columns, covering customer details, product types, regions, order dates, quantity, and unit price. After removing duplicates, the data was refined to 9,921 unique records, with an additional column created to calculate total sales revenue.

From this data, we can see that the business achieved total revenue of 2,101,090, with shoes emerging as the highest-selling product category. Given its consistent demand across multiple regions, this product alone presents a significant growth opportunity. It would be strategically advantageous for the business to continue prioritizing shoes, as well as expanding their sales into the North region, where they are not currently available.

Breaking down product performance by region reveals that each area has distinct product preferences. In the North, the primary items sold were shirts, hats, and jackets. Meanwhile, the South region showed strong sales for gloves, shoes, and socks, and the East saw demand for jackets, hats, shirts, and shoes. In the West, socks, shoes, hats, and gloves were top sellers. Additionally, regional sales insights show that the combined sales value for shoes across the South, East, and West reached 613,380, making it a dominant product in these regions. Hats brought in 316,195 in the East, West, and North, while shirts reached 485,600 across the North and East. Socks totalled 180,785 in the West and South, and jackets earned 208,230 in the North and East. Gloves contributed 296,900 to the South and West.

An analysis of seasonal trends indicates that February was the peak sales month in both years, while April had the lowest sales volume in the previous year, and July in the current year saw a similar low. Year-over-year comparisons show that, although the business sold a greater quantity of products last year, sales revenue has increased in the present year. As of August 2024, the total revenue stands at 29,780, a promising figure compared to last year’s close at 38,681.

Visualizations were key to highlighting these findings: column charts effectively represented average and total revenue by product, bar charts illustrated monthly sales trends, and regional performance was presented using pie and doughnut charts for a clear view of revenue and sales distribution. A table outlined product quantities by region, multi-row cards highlighted the top-selling products, and cards summarized key figures, making the data accessible and actionable.

In conclusion, the South region and shoes represent strategic priorities for the business. Expanding shoe sales into the North could further drive growth, capitalizing on this high-performing product across all regions. Additionally, introducing socks to the East region, where shoes are already thriving, may uncover new sales opportunities.










## Project Title: Customer Data

[Project Overview](project-overview)
[Key Features](ket-features)
[Data Tools](data-tools)
[Microsoft Excel](microsoft-excel)
[Exploratory Data Analysis ](exploratory-data-analysis)
[Insights Derived](insights-derived)
[SQL](SQL)
[POWER BI](power-bi)
 
### Project Overview
This is an analysis and visualization of customer data using Excel, SQL, and Power BI, to uncover trends for strategic decision-making. This project, part of my GitHub portfolio, showcases my proficiency in data storytelling and highlights my ability to transform raw data into actionable insights with advanced tools confidently.

### Data Source
Our facilitator provided this dataset


### Dataset Description
This dataset contains various details of products sold in a store in a different geographical area. These types of datasets are studied to find patterns in the selling structure, profit earned from them, and order history. This data contains 9921 rows and 7 columns, while a missing key column was added in the cleaning process, making it a total of 8 columns.

---

### Key Features:
**CustomerID**: Each customer's unique ID
**CustomerName**: The name of each Customer
**Region**: The region in which the order was placed
**SubscriptionType**: The type of Subscription 
**SubscriptionStart**: The quantity of the product ordered
**SubscriptionEnd**: The unit price for each product
**Canceled**:
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
  
**Insights Derived**:
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

**Insights Derived**:
1. Retrieve the total number of customers from each region:

~~~ SQL
SELECT region, count(customerID) as TotalCustomers
from [dbo].[LITA Capstone Dataset11]
Group by region
order by TotalCustomers
~~~

2. Find the most popular subscription type by the number of customers:

~~~ SQL
SELECT SubscriptionType, count(customerid) as MostPopular
FROM [dbo].[LITA Capstone Dataset11]
GROUP BY SubscriptionType
ORDER BY MostPopular
~~~

3. Find customers who canceled their subscription within 6 months:
   
~~~ SQL
select *,
   DATEDIFF(month, SubscriptionStart, subscriptionend) as subscription_month
from [dbo].[LITA Capstone Dataset11]
where
    canceled = 1
    and DATEDIFF(month, subscriptionstart, subscriptionend) <= 6
order by 
    subscription_month;
~~~

4. Calculate the average subscription duration for all customers:

~~~ SQL
SELECT AVG(datediff(month, subscriptionstart, subscriptionend)) 
 as Averagesubscription
from [dbo].[LITA Capstone Dataset11]
~~~

5. Find customers with subscriptions longer than 12 months:

~~~ SQL
select *,
    DATEDIFF(month, SubscriptionStart, subscriptionend) as subscription_month
from [dbo].[LITA Capstone Dataset11]
where
    canceled = 1
    and DATEDIFF(month, subscriptionstart, subscriptionend) >12 
order by 
    subscription_month;
~~~

6. Calculate total revenue by subscription type:

~~~ SQL
SELECT SubscriptionType, sum(CAST(revenue AS INT)) as TotalRevenue
from [dbo].[LITA Capstone Dataset11]
group by subscriptiontype
order by TotalRevenue
~~~

7. Find the top 3 regions by subscription cancellations:

~~~ SQL
select top 3 region, count(*) as Total_cancel
from [dbo].[LITA Capstone Dataset11]
where canceled = 1
group by region
order by Total_Cancel desc
~~~

8. Find the total number of active and canceled subscriptions:

~~~ SQL
select case when canceled = 0 then 'Active_Sub'
	else 'Canceled_Sub' end as Subscription_Status, 
Canceled, count(*) as Total_cancel
from [dbo].[LITA Capstone Dataset11]
group by canceled
order by Total_Cancel desc
~~~


## POWER BI
A data Visualization and business intelligence tool for converting data from different sources to interactive dashboards.











