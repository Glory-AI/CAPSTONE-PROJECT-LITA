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

  The dataset used was provided by the learning organization behind this project. It comprises the following data points:
     - OrderID - A unique identifier of goods ordered for purchase by customers.
     - Customer Id - A unique identifier assigned to each customer tat patronizes the retail store. 
     - Product - Goods purchased by customers
     - Region - Geographical area where the goods were purchased ( mainly; North, South, West, and East)
     - OrderDate - The date (DD/ MM/ YYYY) goods were purchased from the retail store.
     - Quantity - The amount of product purchased
     - UnitPrice - The price of individual product purchased by each customer.
* *Initial observation and cleaning of data*

  I performed observation of the sales dataset in ***Microsoft Excel***. I found out that there was no column for the total sales made by each customer, so I created a new column:
     - Total Sales- The total amount of money paid by each customer on each day for specific goods ( Obtained by the Excel Formula [Quantity * UnitPrice] )
  Next, I observed certain trends making use of formulas and pivot tables
  ![image](https://github.com/user-attachments/assets/9568bf4c-706e-4ed0-9f15-bb3413489322)
  ![image](https://github.com/user-attachments/assets/2308aa54-c705-41d5-9e78-a6cbf5d95820)
I was able to obtain total sales by product, region and month ad I was able to detect that

 * Sales reduced overall in 2023 and 2024 respectively which might e due to reduction in resources, staff, decline in economy or not able to keep up with technology, all these have to be considered and improved on if truly sales want to be mainntained accross each year in the retail store.

 * Likewise, it is seen that certain goods sold best in some regions. For example in the East, shirt sold better. Thhereore to maximize sales, the retail store sould channel more of specific ggoods to regions where more sales are made from those products.

 * The South produced the greatest revenue ; which might be due to a larger store there, more workers, people living there, position of the store etc. To ennsure this kind of effect on other regions too, the goods people patroize est in those regions should be produced more, there can be more workers or even discounts can be given in extremely low region stores like those in the West to encourage customers to purchase more. 

 The top selling product is 'shoes' ; therefore the retail store can invest more in the product to ensure increased sales.

 The number of customers considered in this dataset are 50,000
 In 2023
 In 2024
 


  
 
