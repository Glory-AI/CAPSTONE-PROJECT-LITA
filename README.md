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

  I performed observation of the sales dataset in MS Excel. I found out that there was no column for the total sales made by each customer, so I created a new column
     - Total Sales- The total amount of money paid by each customer on each day for specific goods ( Obtained by the Excel Formula [Quantity * UnitPrice] )

  
 
