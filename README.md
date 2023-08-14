**SUPPLY CHAIN ANALYTICS - JUST IN TIME COMPANY**
![1](https://github.com/hoshigan/Supply-Chain-Analytic---Just-In-Time-Company/assets/139525944/4641de54-2350-4a3a-a9f4-b490094328ce)

![2](https://github.com/hoshigan/Supply-Chain-Analytic---Just-In-Time-Company/assets/139525944/c1f801eb-da1f-408a-972e-6b8ffee3398c)

![3](https://github.com/hoshigan/Supply-Chain-Analytic---Just-In-Time-Company/assets/139525944/79d782c2-d00c-429d-9de5-9601710af2ce)

![4](https://github.com/hoshigan/Supply-Chain-Analytic---Just-In-Time-Company/assets/139525944/7d770135-d211-4c80-89d0-835ea0c585db)

**I) PROJECT DESCRIPTION**

The project provides a real-world dataset focusing on supply chain analytics. As the main data analyst for Just In Time, you will help solve key shipment and inventory management challenges, analyze supply chain inefficiencies, and create insightful dashboards to inform business stakeholders about potential problems and propose structural business improvements.

**II) METHODOLOGY**

**Business demand analysis**

**Requirements:** Create dashboard to analyze the business problem and improve the supply chain’s efficiency

**Method:** descriptive, exploratory and diagnostic analysis

**Tool used:** Python (Data preprocessing, data cleaning, EDA, inventory segmentation); Power BI (Dashboard)

**Sales Manager:** Overview and keep track of customer’s demand and product sales

=> Dashboard of overall business performance including sales, profit, orders, customers, best product,...

**Inventory Manager:** Control the inventory flow including order fulfillment, storing and distribution 

=> Dashboard of inventory management including warehouse inventory, number of orders from customer, storing cost,...

**Shipping Manager:** Overseeing daily shipping and distribution operations to customers

=> Dashboard of shipping management including orders, location, timing, delay shipping,...

**Overall target**
Create an interactive dashboard to summarize the research of the problem of the supply chain and suggest the solution

**III) DATA PREPROCESSING**

**Data overview**

The dataset provides three data tables including order_and_shipment, inventory and fulfillment. After examining the data fields, I noticed that the dataset generally represents the following key information

Customer:
General information about customers including identifiers and addresses

Order:
Information about the order including date of order, product and quantity ordered, order value

Shipment:
Shipping information including shipping date, shipping mode

Product:
Specific information about the ordered item including product name, product category, product department

Warehouse Inventory:
Information on inventory management for each product name including monthly inventory, warehouse location, storage costs, order fulfillment

**Data cleaning**

1. Drop unnecessary columns (Order Item ID, Order Time)

2. Fix the datatype of the columns

3. Remove special characters in Customer Country column

4. Check for missing value

5. Check for duplicate value

6. Inconsistency of Product Name between order and inventory table: There are 5 product names that appear in the _inventory_ table but not in the _order_ table. This means that these are items that are in the company's inventory but have not been ordered by the customer. So it's impossible to dêtrmine which product category and product department those product names belong to. After investigating carefully, I decided to keep these product names as they account for a considerable amount of storage cost
   
7. Negative and unusual large shipping time: The Shipping Time = Shipment Date - Order Date has some negative values. Thís is due to the error in recording since the Shipment Date < Order Date. There are also unusually large values. Normally, in the United States, standard shipping within the same country might take anywhere from 2 to 7 business days. International standard shipping can take longer, often ranging from 1 to 4 weeks. I decided to take this information as a reference and drop the shipping time values that < 0 and > 28

**Feature creation**

1. Create Date time feature from day, month, year feature
   
2. Create Shipment feature to show which order is late or on time

  Shipping Time = Shipment Date - Order Date

  Delay Shipment = Late if Shipment Day - Schedule < Shipping Time and vice versa

  Late Shipment Rate = Total of late order / Total number of order

3. Create Business performance feature

  Net Sales = Gross sales - Discount * Gross sales

  Unit Price = Gross sales / Order Quantity

  Profit margin = Total Profit / Total Net sales 

  Storage cost = Inventory cost per unit * Warehouse inventory 

**IV) EXPLORATORY DATA ANALYSIS**

In the EDA, I focus on analyzing the characteristics, behaviors, pattern and trends based on these criterions:

Questions:

**Business Performance**

1. What are the total net sales, profit and profit margin by the company?

2. What are the average net sales and profit per month?

3. How do the net sales and profit change over time?

4. How do the number of orders change over time?

5. How do the average order quantity and average unit price change over time?

6. Which product departments account for the majority of net sales and number of orders?

**Customer**

1. How was the distribution of customers by country and market?

2. How many customers does the company have over time?

3. Are there any patterns or trends of buying behavior over time?

**Product**

1. Which product categories and product names are most preferred?

2. Which product categories and product names are most profitable?

**Inventory**

1. Which product departments account for the majority of warehouse inventory and storage cost?

2. How is the inventory cost per unit distributed by the product department?

3. How do the warehouse inventory and storing costs change over time?

4. Which product names and product departments account for the majority of storing cost?

5. What is the average of the average fulfillment order?

6. What is the average order fulfillment of each product department?

**Shipment**

1. Which warehouses are orders shipped from?

2. Which shipment modes are preferred by customers?

3. What is the shipping time for each shipment mode?

4. What is the late shipment rate by product department and market?

5. How does the late shipment rate fluctuate over time?

**Summary of Finding**

1. The company has had an impressive business performance over the past 3 years with net sales of about 5.5 millions and profit of nearly 4 millions. As a result, the company has a very good profit margin, up to 72%

2. The number of orders decreased significantly leading to the sharp decline in net sales and profit. In addition, both net sales and profits decline at the same time by the relative same amount, indicating that costs are unlikely to change and the company is actually facing serious problems from the revenue side
Looking deeper into the product department, we can better gain insights into the decline of the business activities. The absence of the old leading - best selling items (Apparel, Fanshop, Footwear, Golf), which had been instrumental to the company’s success, was closely linked to this downturn.

3. Although over time, the buying behavior from key customer market has changed significantly, but the demand for ordering does not seem to have a strong fluctuation

4. Since both revenue and storage cost have dropped dramatically, there might be an incident resulting in the company being unable to continue selling those best-selling inventory. This can happen due to supply chain disruption. Also, the best selling products are always imported by the company a lot, while new products such as Technology have only been imported in a short time. Therefore, it is not excluded that the company intentionally changes its product offerings to test market demand

5. Interestingly, the best-selling parts have the longest replenishment times, in stark contrast to lesser-known products like Technology and Health and Beauty.

6. The company is having problems with the shipping time because there are quite a few orders that are selected for fast shipment mode such as same day and first class, but the items are shipped days later

7. The high late shipment rate of average 40% over a long time regardless the product departments or geography, which remains concerning and indicates inefficiencies in the supply chain system that need improvement

**Hypothesis Issues trees**

Based on the output of EDA, SCQ analysis was conducted to define the structure:

Situation: The company had relatively stable revenue and profit from 2015 to before September 2017 with revenue mainly coming from key products departments such as Apparel, Golf and Fan Shop.

Complication: The company's operation saw a sharp decline in Q4/2017 due to a supply chain incident resulting in no more revenue coming from key product departments.

Question: How can the company bounce back and re-establish business as before while also overcoming weaknesses in the supply chain?

To be able to solve the problem, it is first necessary to find out where the root cause comes from in the supply chain

Based on the output of EDA, a Hypothesis issue tree was developed

![image](https://github.com/hoshigan/Supply-Chain-Analytic---Just-In-Time-Company/assets/139525944/8bf8a194-2365-4276-b783-19cc9e68af50)

A supply chain will consist of three main components: suppliers - company - customers.

The supply chain starts with the suppliers who provide the products that the e-commerce company will sell. These could include manufacturers, distributors, or wholesalers. Supplier relationships, quality control, and timely deliveries are crucial in this supplier network. Here, we will be interested in average order fulfillment

Once the products are received from suppliers, they are stored in warehouses. Inventory management systems track stock levels, reorder points, and storage locations. Efficient warehousing and inventory management helps prevent stock outs while minimizing excess inventory. Here, we will learn more about storage cost, warehouse inventory and warehouse country

Once customers place orders, the e-commerce platform's order processing team verifies details, product availability, and shipping preferences before transmitting the information to the warehouse. There, staff pick and securely pack items from storage locations, ensuring accuracy and speed to meet customer expectations. The packed orders are then transferred to shipping partners, who may include couriers or carriers, with various options chosen to align with customer delivery expectations. So, in this section, we will need to focus on delayed shipment, delivery system as well as return and canceled order. However, the data set will only give us information about delayed shipment.

Overall, for the whole supply chain to work efficiently, demand forecasting plays a significant role in supply chain optimization. Historical sales data, customer trends, and market insights can help forecast demand accurately, reducing stockouts and excess inventory. We will also consider the demand and supply of the products

In this issue tree, I approach the problem in the most general way by dividing by internal and external factors based on the process of a supply chain. External factors here relate to customers and suppliers, which leads to two hypotheses for the supply chain problem. With internal factors directly related to the company, we will take care of product and shipment issues:

**(1) Customers changed their product preference:** Customers changed their buying behavior. Because the customer file is only about 8000 people and only about 3000 of them made a purchase before Q4/2017. Additionally, the number of customers increased sharply and changed with the market over time. Therefore, the possibility of all customers simultaneously changing their taste is possible

**(2) Supplier were not able to deliver product to the company:** Supply chain disruptions can occur on the supply network side, causing suppliers to be unable to deliver goods or deliver goods on time to the company's warehouse

**(3) The company changed their product offerings: **The company can actively change the items of its business. This can come from a company restructuring, or they test demand with new or changed items based on product life cycle analysis.

**(4) The delayed shipment affected their operation and customer’s loyalty:** This can happen because the company has a high late shipment rate. Customers therefore turn to rival companies with better delivery systems

Since we have over 50 product category and 118 product names, in order to analyze each branch of hypothesis efficiently, inventory segmentation is preferred

**V) INVENTORY SEGMENTATION**

ABC XYZ method is chosen for inventory segmentation.

ABC segments the inventory based on the value contribution of the product name (revenue). In this case, we will use Net Sales. The segmentation of ABC method is conducted as follows:

High value: Product names account for 80% of total net sales

Medium value: Product names account for 15% of the rest

Low value: Product names account for 5% of the rest

XYZ segments the inventory based on the demand volatility. The demand volatility is measured by the coefficient of variation, which equal the standard deviation divided by the mean value

Regular demand: Product names has CV < 0.25

Variable/ Seasonal/ Trendy demand: Product names has 0.25 <= CV <= 0.5

Irregular demand: Product names has CV > 0.5

There are 113 product names from customers' orders but there are 118 product names in the warehouse inventory. This ís due to 5 product names that have no demand as we have seen before. However, we can see that the inventory of these 5 products is not fixed but fluctuates over time. Thus, the company can still release these items from the warehouse. I exclude the possibility of the company donating or recycling these items as they are not the ones that can do so. I'm inclined to hypothesize that this is a systematic error in not recording orders for these items. Therefore, I decided to drop them. Dropping at this step will not affect the EDA analyzes above as these product names only affect the analyzes with the inventory table related to warehouse inventory, unit cost per unit and storage cost, not to analysis of data from the order table

**VI) EXPLORATORY DATA ANALYSIS 2**

**Summary of Finding**

1. There is a tendency to shift from old inventory segments to new ones. This trend can come from customers or from the company itself. Although XA and YA are the same old best selling products, they are different in nature. XA has a much higher value of products in each order, but the number of items in each order is less. Meanwhile, the opposite is true for YA. XB's characteristics are quite similar to XA's with high product value resulting in low order quantity per order. The phase inversion between these two factors holds true for the remaining segments. However, XC does not show an inverse trend between product value and product quantity. Although the product value falls in the middle and third highest, the quantity ordered is only 1 per order.

2. The company is frequently having excessive inventory or overstocked, even during periods of sharp declines. Often, it is necessary to overstock inventory for backup. But there are times when the company's inventory is up to 30% higher than actual demand. The company needs to improve the inventory management to prevent this situation.

3. The late shipments are not directly linked to the order fulfillment time but rather point to issues within the company's delivery system (shipping from warehouse to the customer). In the EDA, the late shipment rate in different markets is similar, showing that this situation seems to happen in general, regardless of geography. The company will need to improve its delivery system

**Testing the hypothesis**

(1) Supply usually has a drop before demand declines. But it is worth mentioning here that, as long as there is inventory, there will still be demand for orders from customers. This decline was not due to changing customer preferences, but rather a supply chain issue from supply side

(2) Suppliers were not able to deliver products to the company, I think this is most likely the root cause. This cause may explain the sudden severance of the XA and YA segments. The company likely tried to find an alternative supplier and in the meantime opted to test-sell the XB and XC segment.

(3) The company changed their product offerings, let's take a look at the graph of warehouse inventory by inventory segmentations again. There were no apparent reductions in storage costs and warehouse inventory for two XA and YA segments in previous years. The decline in these segments was abrupt, almost to the point of disappearance. Also, it is not really reasonable and rational for the company to actively remove best - selling items (80% of total net sales) from their business immediately without testing. Such abrupt removal is very risky! It might not an intentional strategic move by the company to alter its product offerings. However, the dataset only provides information for a period of 3 years. The behavior of changing categories can take place in a longer cycle due to the product life cycle. Therefore, it’s need more investigation

(4) The delay shipment affected their operation and customer’s loyalty. The late shipment rate has maintained ranging from 30% to 50% for a prolonged period. But the number of customers only witnessed a sudden fall during Q4/2017, not to mention it's cyclical. Net sales also remained stable even though LSR fluctuated and only dropped sharply at that time. Late shipments may not be the primary root cause of the overall decline in business performance during that period

**VII) SUGGESTION**

Based on all the analysis I would like to make some recommendations as follows

**Restore revenue and profit (recommended for each inventory segmentation):**

**XA, YA:**

The historical data shows that both segments are in high demand from customers and are also the main source of revenue for the company. Bringing these segments back will be one of the top goals. The company can find new suppliers and redesign the supply chain so that the incident of Q4/2017 won’t happen again.
This includes further investigation to identify where supply chain disruptions are occurring and filtering out suitable alternative suppliers. For example, items such as clothing, footwear and apparel are often imported from Southeast Asia, West Asia and Central America. Meanwhile, Electronics and Technology products are manufactured in both North America and East Asia. Therefore, we are not sure where the disruption occurred.

**XB, XC:**

These segments show a certain growth potential that cannot be ignored. XB and XC had surged and shouldered all of the company's revenue by the time the disruption occurred. So the first thing to do is conducting market research to understand current consumption trends and market's demands for the emerging products.
Analyzing both local and global markets to identify gaps and opportunities is also necessary. Furthermore, monitoring the evolution of this segment and forecast customer demand (if possible) to optimize inventory management is recommended.

**YB, YC, ZB, ZC:**

These segments do not contribute significantly to the company's revenue. They also have low or no demand. I recommend dropping these segments or reducing inventory to optimize storage cost.

****Overstock and Understock:

If it is available, demand forecasting is crucial. By analyzing historical sales data, tracking market trends, and employing predictive analytics, the company can anticipate future demand, allowing it to maintain an optimal inventory level. Additionally, setting up reorder points for each product is essential. These points serve as indicators for reordering, factoring in lead time, sales velocity, and desired safety stock levels, ensuring the company replenishes stock in a timely manner without risking overstocking. Speaking of safety stock, maintaining this buffer inventory is vital. It acts as a safeguard against unexpected demand fluctuations or supply delays, mitigating the chances of stockouts and the associated revenue loss while also minimizing the risk of excessive stock accumulation.

Recalling again that customers by each market have a strong increase at a certain time. In Q4/2017, it had customers from the Asia Pacific market, previously Europe. Based on this cycle, I expect customers from Asia Pacific to make up the majority in Q1/2018, followed by North America in the following quarters. The company can rely on this information to calculate the appropriate amount of inventory and consider predicting the product life cycle for each region.

**High late shipment rate:**

In order to effectively curb the issue of high late shipment rates, the company should consider implementing a multifaceted approach.

Firstly, the optimization of the delivery system through a redesigned transportation route, such as adopting a cross-docking strategy, can significantly enhance the efficiency of shipments.

Furthermore, collaboration with local logistics companies to leverage their existing resources and expertise is not a bad idea, especially with markets far away from the USA and Puerto Rico.

Additionally, to bolster the overall delivery system and expand the company's global reach, establishing a warehouse in a strategic logistics hub like Singapore in Asia would be beneficial. This move would not only improve the delivery process but also facilitate smoother operations across various international markets.

