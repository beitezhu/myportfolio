---
layout: post
title:  Tableau visualization showcasing the pizza sales trend
date:   2024-1-15 22:15:20 +0800
tags:   SQL;Tableau
---
![image](../assets/image/pizza_tableau_home_icon.png) 

> - SQL Tool: Snowflake,
- Visualization Tool: Tableau
- My role: Write the SQL query to find the data insight and do the visualization of the pizza sales product. 

![image](../assets/image/pizza_tableau_2nd_icon.png)  
<br/>

#### Summary
In this project, I wrote SQL queries on Snowflake to summarize the data, and then used Tableau for visualization. My aim was to assist pizza sales owners in identifying selling trends and the best-selling products. I also created an interactive dashboard that allows users to adjust metrics for a deeper understanding of the business.

<br/>
##### Here are the details of how I did that

Step 1: I cleaned the data and imported the datasheet into Snowflake. 

![image](../assets/image/Snowflake_database.png)
<br/>

Step 2: I wrote queries in Snowflake to understand the KPIs of pizza sales, including total revenue, average order price, etc. 

```
----Total_revenue
    SELECT SUM(total_price) as total_revenue
    FROM realdata128;
----Total_revenue is 827327


----Average order price
    SELECT SUM(total_price)/count(distinct order_id) as Avg_Order_value
    FROM realdata128;
----Average order price is 38.75


----Total_pizza_sold
    SELECT sum(quantity) as Total_pizza_sold
    FROM realdata128;
----Total_pizza_sold is 49574


----Total_order_number
    SELECT COUNT(distinct order_id) as total_order_numb
    FROM realdata128;
----Total_order_number is 21350


----Avg_pizza_per_order
    SELECT sum(quantity)/COUNT(distinct order_id) AS avg_pizza_per_order
    FROM realdata128;
----Avg_pizza_per_order is 2.32196

```
<br/>
Step 3: I wrote queries in Snowflake to analyze the trends in pizza sales metrics, including the weekly trend for total pizzas sold and the breakdown of sales by pizza size and category, among others.

```
--Hourly trend for total pizzas sold
    SELECT 
        date_part(hour,order_time)as order_hour, 
        SUM(quantity) as Total_pizzas_sold
    FROM realdata128
    GROUP BY date_part(hour,order_time)
    ORDER BY order_hour;


---Weekly trend for totally orders
    SELECT 
        DATE_PART(WEEKISO,order_date) as week_number, 
        YEAR(order_date) as YEAR, 
        COUNT(DISTINCT order_id) as Total_orders
    FROM realdata128
    GROUP BY DATE_PART(WEEKISO,order_date),YEAR(order_date)
    ORDER BY DATE_PART(WEEKISO,order_date),YEAR(order_date);


---Percentage of sales by pizza category
    SELECT 
        pizza_category, 
        sum(total_price)*100/(SELECT sum(total_price) from realdata128) AS percentage
    FROM realdata128
    GROUP BY pizza_category;


---Size of sales by pizza category
    SELECT 
        pizza_size, 
        sum(total_price) as Total_sales,
        sum(total_price)*100/(SELECT sum(total_price) from realdata128 WHERE date_part(quarter,order_date) = 1) AS percentage
    FROM realdata128
    WHERE date_part(quarter,order_date) = 1
    GROUP BY pizza_size
    ORDER BY percentage DESC;


--Best seller by revenue, total quantity and total order
    SELECT 
        pizza_name, 
        sum(quantity) as total_quan
    FROM realdata128
    GROUP by pizza_name
    ORDER by total_quan ASC;

    SELECT 
        pizza_name, 
        sum(total_price) as total_revenue
    FROM realdata128
    GROUP by pizza_name
    ORDER by total_revenue DESC
    LIMIT 5;

    SELECT 
        pizza_name, 
        COUNT(distinct order_id) as total_orders
    FROM realdata128
    GROUP by pizza_name
    ORDER by total_orders ASC;
```
<br/>
Step 4: I connected the Snowflake server to the Tableau server to perform visualizations. Please click the 'Home' and 'Best/Worst Seller' buttons at the top left to switch between tables.



<div class='tableauPlaceholder' id='viz1706640276658' style='position: relative'><noscript><a href='#'><img alt='Home ' src='https:&#47;&#47;public.tableau.com&#47;static&#47;images&#47;pi&#47;pizzatablaue&#47;Home&#47;1_rss.png' style='border: none' /></a></noscript><object class='tableauViz'  style='display:none;'><param name='host_url' value='https%3A%2F%2Fpublic.tableau.com%2F' /> <param name='embed_code_version' value='3' /> <param name='site_root' value='' /><param name='name' value='pizzatablaue&#47;Home' /><param name='tabs' value='no' /><param name='toolbar' value='yes' /><param name='static_image' value='https:&#47;&#47;public.tableau.com&#47;static&#47;images&#47;pi&#47;pizzatablaue&#47;Home&#47;1.png' /> <param name='animate_transition' value='yes' /><param name='display_static_image' value='yes' /><param name='display_spinner' value='yes' /><param name='display_overlay' value='yes' /><param name='display_count' value='yes' /><param name='language' value='en-US' /></object></div>                

<script type='text/javascript'>                    var divElement = document.getElementById('viz1706640276658');                    var vizElement = divElement.getElementsByTagName('object')[0];                    if ( divElement.offsetWidth > 800 ) { vizElement.style.width='1100px';vizElement.style.height='950px';} else if ( divElement.offsetWidth > 500 ) { vizElement.style.width='1100px';vizElement.style.height='950px';} else { vizElement.style.width='100%';vizElement.style.height='2877px';}                     var scriptElement = document.createElement('script');                    scriptElement.src = 'https://public.tableau.com/javascripts/api/viz_v1.js';                    vizElement.parentNode.insertBefore(scriptElement, vizElement);                </script>


<br/>
Step 5: I cross-checked the numbers in Tableau with the queries I executed in Snowflake to ensure the data is correct on both sides.

![image](../assets/image/pizza_tableau_best.png)