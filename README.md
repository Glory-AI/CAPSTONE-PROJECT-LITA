# CAPSTONE-PROJECT-LITA

## Project Overview

This is a capstone project to wrap up the data analysis bootcamp organized by Incubator Hub x LITA. It comprises two sub-projects namely:

1. **Sales Performance Analysis for a Retail Store** - which aims to uncover key insights such as top-selling products, regional
performance, and monthly sales trends.
2. **Customer Segmentation for a Subscription Service** - which aims to  understand customer behavior, track subscription types,
and identify key trends in cancellations and renewals.

## Tools

* **Microsoft Excel** : For initial exploration of data, data cleaning, and creation of pivot tables and charts.
* **SQL (Structured Query Language) Server** : For querying and gaining insights into data.
* **Microsoft Power BI** : For visualizing data, creating reports, and gaining more insights into data.

## Process

- Question definition 
- Data Sourcing
- Initial observation and cleaning of data
- Exploratory Data Analysis (Insights Derivation)
- Visualization generation

  ### Project 1: Sales Performance Analysis for a Retail Store
  ------
* *Question definition*
  
  This analysis will answer questions based on top-selling products, regional performance, monthly sales trends , and suggestions to improve on deficiency if any.

* *Data Source*

  The dataset used was provided by the learning organization behind this project. It comprises the following columns:
     - OrderID - A unique identifier of goods ordered for purchase by customers.
     - Customer Id - A unique identifier assigned to each customer that patronizes the retail store. 
     - Product - Goods purchased by customers
     - Region - Geographical area where the goods were purchased ( mainly; North, South, West, and East)
     - OrderDate - The date (DD/ MM/ YYYY) goods were purchased from the retail store.
     - Quantity - The amount of product purchased
     - UnitPrice - The price of individual product purchased by each customer.
       
* *Initial observation and cleaning of data*

 I performed observation of the sales dataset in ***Microsoft Excel***.

 I cleaned the data and also checked for duplicates: I was able to remove 40079 duplicate rows leaving 9921 rows for analysis.
  
  I found out that there was no column for the total sales made by each customer, so I created a new column:
     - Total Sales- The total amount of money paid by each customer on each day for specific goods ( Obtained by the Excel Formula [Quantity * UnitPrice] ).
  
  Next, I observed certain trends making use of MS Excel formulas and pivot tables:
  
  The total amount of revenue for the retail store is # 2,101,090.00

  ![image](https://github.com/user-attachments/assets/e33388f5-6040-4963-bcab-7d798c1f808b)

  ![image](https://github.com/user-attachments/assets/d38ba432-7e3d-4a09-afe1-c2ba55271687)

 * *Exploratory Data Analysis*

   For this purpose, I'll be making use of SQL Queries
   Table is created and data is imported as flat file(csv)
   
a. What is the total sales for each product category / the highest-selling product by total sales value?
   ``` SQL
   select [Product], sum(Total_Sales) as [PRODUCT SALES] 
   from  [dbo].[Capstone file]
   group by [Product]
   order by sum(total_sales) desc
   ```
   
   Inference: It can be seen that shoes sold best with a sum total of # 613,380 i.e it is the highest selling product.

b. What are sales trasanctions in each region?
   ``` SQL
   select [Region], sum(Total_Sales) as  [SALES BY REGION] 
   from  [dbo].[Capstone file]
   group by  [Region]
   order by sum(total_sales) desc
   ```
   Inference: The south produced the highest sales transaction with a total revenue of # 927,820

c. What is the monthly sales totals for the current year?
   ``` SQL
   select sum(total_sales) as MonthSales , MONTH(orderdate) as MonthInNumber
   from   [dbo].[Capstone file]
   where YEAR(orderdate) = '2024'
   group by MONTH(orderdate)
   order by MonthInNumber
   ```
   Inference: In the current year 2024, the month that yielded the highest sales totals is February and the month with the lowest is July.
   
d. Who are the top 5 customers by total purchase amount?
   ```SQL
   select distinct(Customer_Id),[Total_Sales]
   from [dbo].[Capstone file]
   order by  [Total_Sales] desc
   ```
   Inference: The top 5 customers made a total sales of #600 each.
  
e. What is the percentage of total sales contributed by each region?
   ```SQL
   select  count(total_sales) * 100 / sum(count(total_sales)) over() as 'Percentage',[Region]  
   from [dbo].[Capstone file]
   group by Region
   order by 2
   ```
   Inference: The south made the highest contribution of 44% to the total sales of the retail store.
   
f. What products contributed no sales to total revenue in the last quarter(within July and September)
   ```SQL
   SELECT [Product] , sum([Total_Sales]) as Sales  , DATEPART(QUARTER, [OrderDate] ) AS Quarter
   FROM [dbo].[Capstone file] 
   where YEAR(orderdate) = '2024'  
   group by [Product], DATEPART(QUARTER, [OrderDate])  
   order by DATEPART(QUARTER, [OrderDate])
   ```
   Inference: Only shoes and hats contributed to the total revenue in the last quarter with a sum of #211,500: shirts, jackets, gloves and socks had no contributions 

   **Conclusions**
   
  1. Sales reduced overall in 2023 and 2024 respectively which might be due to reduction in resources, staff, decline in economy or not able to keep up with technology, all these have to be considered and improved on if truly sales want to be maintained accross each year in the retail store.  

   2. It is seen that certain goods sold best in some regions. For example in the East, shirt sold better. Therefore to maximize sales, the retail store should channel more of specific goods to regions where more sales are made from those products.
    
   3. The South produced the greatest revenue ; which might be due to a larger store there, more workers, people living there, position of the store etc. To ensure this kind of effect on other regions too, the goods people patronize best in those regions should be produced more, there can be more workers or even discounts can be given in extremely low region stores like those in the West to encourage customers to purchase more. 
    
   4. The top selling product is 'shoes' ; therefore the retail store can invest more in the product to ensure increased sales.

   5. The number of customers considered in this dataset are 9921: in 2023 , 5952 customers patronized the retail store and in 2024 , 3969 customers has patronized the retail store from January to August. Efforts should be made to increase the number of customers.  

   * *Visualization Generation*
     ![image](https://github.com/user-attachments/assets/bd5b22f4-cbbf-449d-a3b6-317da857b7b4)


### Project 2: Customer Segmentation for a Subscription Service   
   ---

* *Question definition*
  
  This project aims to answer questions to understand customer behavior, track subscription types,and identify key trends in cancellations and renewals.
 
* *Data Source*
  
     The dataset used was provided by the learning organization behind this project. It comprises the following columns:
  
   - Customer Id - A unique identifier assigned to each customer that patronizes the subscription service.
   - Customer Name - The names of customers
   - Region - Geographical area where the subscription services was paid for.
   - Subscription type - type of subscription made by each customer( basic, premium, and standard)
   - Subscription Start - Period when each customer started a subscription type.
   - Subscription End - Period when each customer ended subscribing to a subscription type.
   - Canceled - A column indication whether or not a customer canceled their subscription.
   - Revenue - The total amount of money generated from subscription services.

* *Initial observation and cleaning of data*
  
  I performed observation of the sales dataset in ***Microsoft Excel***.
  
  I cleaned the data and also checked for duplicates. I also used pivot tables and formulas to obtain some insights.
 
 ![image](https://github.com/user-attachments/assets/d2352610-1d41-499a-bdfc-ca78af1b2d27)

 ![image](https://github.com/user-attachments/assets/8be0bc65-51d6-4d61-beb5-510d4aa31edc)

 The average subscription duration is 1 year(365 days)

 * *Exploratory Data Analysis*

a. What is the total number of customers from each region?
   ```SQL
   select COUNT(distinct([CustomerName]) as [Total Customers] , Region
   from [dbo].[customer data capstone]
   group by Region
   ```
   Inference: There are 5 customers in each region

b. What is the most popular subscription type by the number of customers?
   ```SQl
   select COUNT(distinct([CustomerName])) as [Customers], [SubscriptionType]
   from [dbo].[customer data capstone]
   group by [SubscriptionType]
   order by 1 desc
   ```
   Inference: The most popular subscription type is basic with a total of 10 out of 20 customers.

c. What customers who canceled their subscription within 6 months?
   ```SQL
   select count(distinct([CustomerID]))
   from [dbo].[customer data capstone]
   where DATEDIFF(YEAR, [SubscriptionStart], [SubscriptionEnd]) * 12 <= 6 and Canceled=1
   ```
   Inference: No customer canceled subscription within 6 months.

d. What is the average subscription duration for all customers?
   ```SQL
   select AVG(DATEDIFF(YEAR, [SubscriptionStart], [SubscriptionEnd]) * 12)
   as Average_Subcription_Duration_In_Months
   from [dbo].[customer data capstone]
   ```
   Inference: The average subscription duration for all customers is 12 months.

e.  What customers are with subscriptions longer than 12 months ?
   ```SQL
   select count([CustomerID]) as Number_Of_Customers_With_SubscriptionDuration_Greater_Than_TwelveMonths
   from [dbo].[customer data capstone]
   where DATEDIFF(YEAR, [SubscriptionStart], [SubscriptionEnd]) * 12 > 12
   ```
   Inference: No customer subscribed for a duration beyond 12 months.
   
 f. What is the total revenue by subscription type?
  ```SQL
    select sum(revenue) as Total_Revenue, [SubscriptionType]
    from [dbo].[customer data capstone]
    group by [SubscriptionType]
 ```
   Inference: The basic subscripiton type yielded the highest total revenue.

 g.  What are the top 3 regions by subscription cancellations?
   ```SQL
   select [Region] , count(*) as Region_by_Subscription_Cancellation  from [dbo].[customer data capstone]
   where [Canceled] = '1'
   group by region
   order by 2 desc
   ```
   Inference: The top 3 regions are North (with the highest subscription cancellations), South and West.

h. What is the total number of active and canceled subscriptions?
  ```SQL
   select count(*) as Canceled_Subscriptions
   from [dbo].[customer data capstone]
   where [Canceled]= '1'
   select count(*) as Active_Subscriptions
   from [dbo].[customer data capstone]
   where [Canceled]= '0'
  ```
   Inference: The number of active subscriptions(18612) is greater than the number of canceled subscription(15175) 

   
 **Conclusions**

 1. Each region has equal number of customers ; therefore efforts should be made to increase the number of customers accross all regions.
    
 2. It can be seen that people who canceled their subscription were less compared to people who did not. Despite this, the subscription service has to bridge the gap that is causing people to cancel subscription and ensure actions are taken.
 
 3. People who canceled their subscription for standard and premium types were more than those who did not. This might be because the standard and premium subscription types did not meet customers' expectation compared to the basic type. Therefore, efforts should be made to improve so well on those types that did not meet expectation.
 
 4. The East region did not experience canceled subscriptions at all, but the other regions experienced cancellations. Therefore, whatever strategies were applied for the East region should also be applied to the other region to minimize cancellations.

  * *Visualization Generation*
![image](https://github.com/user-attachments/assets/0aac7caf-c580-4e84-857c-703f84411954)

    
