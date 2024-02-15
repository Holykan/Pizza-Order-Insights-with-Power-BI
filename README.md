# Pizza-Order-Insights-with-Power-BI
 
About the dataset
* This dataset contains 4 tables in CSV format
* The Orders table contains the date & time that all table orders were placed
* The Order Details table contains the different pizzas served with each order in the Orders table, and their quantities
* The Pizzas table contains the size and price for each distinct pizza in the Order Details table, as well as its broader pizza type
* The Pizza Types table contains details on the pizza types in the Pizzas table, including their name as it appears on the menu, the category it falls under, and its list of ingredients
  Procedure
1. The dataset was almost clean.. after loading into Power Bi, had to use the “Use first row as Headers” feature in the power query editor on the pizza types table. I also had to define the data types for date and time in the orders table.
2. I created 4 more columns in the orders table. Below are the column names and DAX formulas I used to create them:
- [ ] day_name = FORMAT(orders[date], “dddd”) - This displays the full name of the day of the week corresponding to the date values in the “date” column. 
- [ ] hour_of_day = HOUR(orders[time]) - This displays the hour of the day corresponding to the time values in the “time” column.
- [ ] time_of_day = IF(orders[hour_of_day] < 12, “Morning”, IF(orders[hour_of_day] < 17, “Afternoon”, “Evening”)) - This aggregates the column into morning, afternoon and evening based on the conditions specified in the function. 
- [ ]  month_of_the_year = FORMAT(orders[date], “MMMM”) - This displays the full name of the month corresponding to the date values in the “date” column.
- [ ] purchase_amount = order_details[quantity] * RELATED(pizzas[price])
3. Measures created;
- [ ] Total_pizza_made = SUM(order_details[quantity])
- [ ] total_sales = SUM(order_details[purchase_amount])

Insights
1. In this dashboard, we can see that the Pizza restaurant generated $817.9K in 2015. This was as a result producing 49.6K pizzas by honouring 21.4K orders placed by customers.
2. The top 5 best selling pizzas in descending order are; The Big Meat Small size with 1914 orders, The Thai Chicken Large size with 1410 orders, The Five Cheese Large size with 1409 orders, The Four Cheese Large size with 1316 order and the Classic Deluxe Medium size with 1181 orders. This influences the buying of the ingredients for making these pizzas.
3. The top 5 income generating pizzas are in the order; Thai Chicken Large, Five Cheese Large, Four Cheese Large, Spicy Italian Large and Big Meat Small.
4. The heat map tells us that the busy times in the day are Tuesday @ 12, Wednesday @ 12, Thursday @ 12 and 1pm and Fridays @ 12 and 1pm.
5. The donut chart shows that people people do not like the Extra Large and the Extra Extra Large Pizzas as they occupy only 1.2% and 0.06% respectively.
6. By using the month slicer, we can infer that October is the lease busiest month with 1.6K orders and May and July were the busiest month with 1.9K orders in both months.
