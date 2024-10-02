# Supply-Chain-Analysis-Dashboard
Supply Chain Analysis

Problem- AtliQ Mart is a growing FMCG manufacturer headquartered in Gujarat, India. It is currently operational in three cities Surat, Ahmedabad and Vadodara. They want to expand to other metros/Tier 1 cities in the next 2 years.

AtliQ Mart is currently facing a problem where a few key customers did not extend their annual contracts due to service issues. It is speculated that some of the essential products were either not delivered on time or not delivered in full over a continued period, which could have resulted in bad customer service. Management wants to fix this issue before expanding to other cities and requested their supply chain analytics team to track the ’On time’ and ‘In Full’ delivery service level for all the customers daily basis so that they can respond swiftly to these issues.

The Supply Chain team decided to use a standard approach to measure the service level in which they will measure ‘On-time delivery (OT) %’, ‘In-full delivery (IF) %’, and OnTime in full (OTIF) %’ of the customer orders daily basis against the target service level set for each customer.

Task:  
Peter Pandey is the data analyst in the supply chain team who joined AtliQ Mart recently. He has been briefed about the the task in the stakeholder business review meeting. Now imagine yourself as Peter Pandey and play the role of the new data analyst who is excited to build this dashboard and perform the following task:
1.	Create the metrics according to the metrics list.
2.	Create a dashboard according to the requirements provided by stakeholders in the business review meeting. You will be provided with the transcript of this business review meeting in comic form.
3.	Create relevant insights not provided in the metric list/stakeholder meeting.
Solutions:
This Power BI dashboard provides insights into key supply chain performance metrics. It tracks delivery performance, order fulfillment rates, and trends in on-time delivery. It is designed to help stakeholders monitor the efficiency of the supply chain and identify opportunities for improvement.
Dashboard Features
1. Key Metrics
The following custom measures were created to monitor supply chain performance:
•	In-Full Delivery: Measures the percentage of orders delivered in full.
DAX
Copy code
In-Full Delivery = DIVIDE(COUNTROWS(FILTER(fact_orders_aggregate, fact_orders_aggregate[in_full] = 1)), COUNTROWS(fact_orders_aggregate), 0)
•	Line Fill Rate %: Measures the percentage of order lines delivered in full.
DAX
Copy code
Line Fill Rate % = DIVIDE(COUNTROWS(FILTER(fact_order_lines, fact_order_lines[In Full] = 1)), COUNTROWS(fact_order_lines), 0)
•	On-Time Delivery %: Measures the percentage of orders delivered on time.
DAX
Copy code
On Time Delivery % = DIVIDE(COUNTROWS(FILTER(fact_orders_aggregate, fact_orders_aggregate[on_time] = 1)), COUNTROWS(fact_orders_aggregate), 0)
•	On-Time In-Full (OTIF): Measures the percentage of orders delivered both on time and in full.
DAX
Copy code
On Time In Full = DIVIDE(COUNTROWS(FILTER(fact_orders_aggregate, fact_orders_aggregate[on_time] = 1 && fact_orders_aggregate[in_full] = 1)), COUNTROWS(fact_orders_aggregate), 0)
•	Volume Fill Rate: Measures the percentage of order quantity that was successfully delivered.
DAX
Copy code
Volume Fill Rate = DIVIDE(SUM(fact_order_lines[delivery_qty]), SUM(fact_order_lines[order_qty]), 0)
2. Visualizations
•	Clustered Bar Chart: Displays comparisons of key performance metrics against their targets:
o	On-Time Delivery vs Target
o	On-Time In-Full (OTIF) vs Target
o	In-Full Delivery vs Target
o	These visualizations are connected via bookmarks for interactive navigation.
•	Line Chart: Depicts the performance trends of On-Time In-Full (OTIF) delivery percentage over time, allowing for an understanding of the overall trend and performance improvements.
3. Bookmarks
The dashboard includes bookmarks to toggle between different views for easier analysis of:
•	On-Time Delivery vs Target
•	OTIF vs Target
•	In-Full Delivery vs Target
4. Interactivity
The dashboard includes slicers for different time periods and filters for better analysis based on regions, order types, and product categories.
________________________________________
Data Sources
The data is pulled from:
•	Fact Orders Aggregate: Aggregate data for orders, containing fields like in_full, on_time, etc.
•	Fact Order Lines: Detailed data for each order line, including delivery_qty and order_qty.

