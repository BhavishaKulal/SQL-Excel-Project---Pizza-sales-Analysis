# SQL-Excel-Project-Pizza-sales-analysis

## Overview
In order to provide insights on revenue trends, sales performance by category and size, and customer behaviour based on time and order patterns, the Pizza Sales & Analysis project focusses on analysing sales data from a pizza chain. Using key performance metrics like total revenue, average order value, and total pizzas sold, the dashboard helps business stakeholders evaluate peak sales periods, best and worst-selling pizzas, and overall business health.

## Features
**1.Sales Insights by Time and Day**: Examines the busiest days and hours for pizza orders, emphasising the hours of highest sales and offering suggestions for improving operational effectiveness.

**2.Pizza Category and Size Breakdown**: Shows how sales are divided into categories (like Classic, Chicken, Supreme, and Veggie) and sizes (like Small, Medium, and Large).

**3.Best & Worst Sellers**: This feature helps with inventory management and marketing decisions by identifying the top 5 pizzas based on sales volume and the bottom 5 worst sellers.

**4.Daily and Hourly Trends**: Indicates when customers are most active by displaying hourly sales patterns throughout the day and order trends over the course of the week.

**5.Sales Performance Metrics**: Shows the total revenue, average order value, number of pizzas sold, and average number of pizzas per order, among other important business performance metrics.

**6.Dynamic Slicer for Date Filtering**: Offers an interactive slicer to filter the dashboard according to particular time intervals, enabling in-depth temporal analysis.

## Dataset

Dataset used for this task is Pizza sales excel file 

Dataset: [Pizza sales](https://github.com/BhavishaKulal/SQL-Excel-Project---Pizza-sales-Analysis/blob/main/pizza_sales.csv)

## SQL Queries Used
Sql Quries used for find out some KPI as below:

Document: [Sql Queries](https://github.com/BhavishaKulal/SQL-Excel-Project---Pizza-sales-Analysis/blob/main/pizza%20sql%20query.docx)

   - Total Revenue: select sum(total_price) as total_revenue from [pizza_sales excel file].
 
   -  Average Order Value: select sum(total_price) / COUNT(DISTINCT ORDER_ID) as average_order_value FROM [pizza_sales excel file].

   -  Total Pizza Sold: select sum(quantity) as total_pizza_sold from [pizza_sales excel file].

   - Total Orders: select count( distinct order_id) as total_orders from [pizza_sales excel file].

- Average Pizzas Per Order: select cast(cast(sum(quantity) as decimal(10,2)) / cast(COUNT(distinct order_id)as decimal(10,2)) as decimal(10,2)) as avg_piza_per_order from [pizza_sales excel file].

- Daily Trend of Total Orders: select DATENAME(dw, order_date)as order_date, count(distinct order_id) as total_order from [pizza_sales excel file] group by  DATENAME(dw, order_date).

- Hourly Trend of Total Orders: select DATEPART(hour, order_time) as order_hour,count(distinct order_id) as total_order from [pizza_sales excel file] group by DATEPART(hour, order_time) order by DATEPART(hour, order_time).

- Percentage of Sales by Pizza Category: select pizza_category, cast(sum(total_price)as decimal(10,2)) as total_sales,CAST(sum(total_price)*100/
 (select sum(total_price) from [pizza_sales excel file]) AS DECIMAL(10,2)) AS PCT
 from [pizza_sales excel file]  group by  pizza_category.

- Percentage of Sales by Pizza Size: select pizza_size, cast(sum(total_price)as decimal(10,2)) as total_sales, cast(sum(total_price)*100/(select sum(total_price) 
 from [pizza_sales excel file] where DATEPART(QUARTER, order_date)=1) as decimal(10,2)) as pct
from [pizza_sales excel file] where DATEPART(QUARTER, order_date)=1 group by  pizza_size 
order by pct desc.

- total pizza sold by pizza category: SELECT PIZZA_CATEGORY, SUM(quantity) AS TOTAL_SALES FROM [pizza_sales excel file] GROUP BY pizza_category ORDER BY SUM(quantity) DESC.

- top 5 best sellers by total pizzas sold: select top 5 pizza_name, sum(quantity) as total_sales from [pizza_sales excel file]
group by pizza_name order by sum(quantity) desc,

- bottom 5 sellers by total pizzas sold: select top 5 pizza_name, sum(quantity) as total_sales from [pizza_sales excel file]
group by pizza_name order by sum(quantity) asc.

## Data Preparation For the visualization 

Data Cleaning for the dataset was done in excel  as follows:
- created Total order coloum separately to ease the dashboard preparation( In order to find the distinct total order)
- Created order day coloumn
- Removed Unnecessary columns.
- Removed Unnecessary rows.
- Each of the columns in the table were validated to have the correct data type.

## Visualization
The following visualizations were created using Excel:

- KPI Cards - Displaying Total Revenue, Average Order Value, Total Pizza Sold, Total Orders, and Average Pizzas per Order.
- Bar Charts - Showing the daily and hourly trends of total orders.
- Pie Charts - Displaying the percentage of sales by pizza category and pizza size.
- Horizontal Bar Charts - Highlighting total pizza sold by category and the top 5 best-selling pizzas.

## Dasboard 
  Pizza sales Analysis

  View Dshboard - [Excel Pizza sales analysis](https://github.com/BhavishaKulal/SQL-Excel-Project---Pizza-sales-Analysis/blob/main/pizza_dashboard.xlsx)

  ![Screenshot 2024-09-15 224017](![sql-excel-pizzaproject](https://github.com/user-attachments/assets/34615dbb-96b2-47cb-8ce9-301f4db82b6f)
)
)




