# Denmark-Residential-Housing-Market-Trends-1992-2024-DKK-Currency-SQL--EXCEL--Tableau
The Danish residential housing market has experienced significant changes over the past three decades, influenced by economic conditions, interest rates, and regional development. In this case study, I analyze housing transaction data from 1992 to 2024 to uncover long-term pricing trends and key factors that impact home values.

To guide the analysis, I used AI to generate five practical questions that a stakeholder or decision-maker would realistically ask when evaluating the housing market. Using SQL and Excel for data preparation and Tableau for visualization, I translated these questions into clear, concise, and easy-to-understand visuals designed to make insights accessible to both technical and non-technical audiences.

This specific data was provided by Kaggle and can be viewed [here]([https://www.kaggle.com/datasets/roopacalistus/superstore](https://www.kaggle.com/datasets/martinfrederiksen/danish-residential-housing-prices-1992-2024)).

Insights and recommendations are provided on the following key areas:
* **Identifies top and low performing products** by analyzing profit and profit per unit sold to highlight true profitability beyond total sales.
* **Quantifies revenue lost due to discounts** and evaluates how discounting impacts final sale price and overall margins.
* **Calculates adjusted final sale prices** after discounts to provide a more accurate view of actual revenue earned.
* **Analyzes profit by quantity sold** to determine how much profit is generated per sub-catagory.
* **Evaluates revenue per sub-catagory** by dividing total sales by quantity sold, supporting data-driven pricing and inventory decisions.

View the SQL script containing all calculated columns used in this analysis [here](https://github.com/smouzakitis83/Retail-Superstore-Performance-Analysis-/blob/main/SuperStore_Calc.SQL)

# Visual Analysis and Key Findings

This visualization shows shipping cost differences by shipping class across all four regions, with Standard Class being the most costly.

<img width="674" height="484" alt="Screenshot 2025-12-19 120244" src="https://github.com/user-attachments/assets/468b37ea-e716-4bd7-8335-bd2bdd9a85a2" />

The inventory quantities for each category across all regions are shown below, clearly indicating that office supplies have the highest quantities among the three categories.

<img width="661" height="476" alt="Screenshot 2025-12-19 120309" src="https://github.com/user-attachments/assets/76236beb-c510-4d6d-9bf1-4afd5720cb1d" />

The following graph shows profit by subcategory, highlighting tables as the least profitable subcategory, with a negative profit.

<img width="636" height="331" alt="Screenshot 2025-12-19 120329" src="https://github.com/user-attachments/assets/8bf012da-c021-4e36-a95d-8c79678a9d7d" />

The visualization displays product quantities by state, showing California as the top state by quantity.

<img width="680" height="391" alt="Screenshot 2025-12-19 120356" src="https://github.com/user-attachments/assets/44071e95-2e8e-40ea-8c2f-5229c0470ece" />

# Executive Summary
This analysis breaks down shipping, sales, and profitability in a clear and easy-to-understand way. The Excel pivot charts compare shipping costs by shipping class and region, show how product quantities vary by region and category, highlight which subcategories generate the most profit, and display product quantities sold by state. These views make it easier to see where costs are higher, where demand is strongest, and which products perform best.

The Tableau dashboard brings everything together with interactive visuals and key performance indicators, including Sales, Profit, and Profit Margin %. Users can explore profit margins by subcategory, profit by category, revenue lost due to discounts, and a map showing sales and profit margin by state. Together, these insights help stakeholders quickly understand performance trends and identify opportunities to improve pricing, discount strategies, and shipping decisions.

Below is the overview page from the Tableau dashboard. The entire dashboard can be viewed and interacted with [here](https://public.tableau.com/app/profile/stamatios.mouzakitis/viz/SuperStore_Sales_Dashboard_17664161596300/Dashboard1)

<img width="680" height="391" alt="Screenshot 2025-12-22 123505" src="https://github.com/user-attachments/assets/fed03286-64d6-41aa-9880-7a9db99a9c75" />

## Sales Trends
* **Standard Class shipping** is the most expensive option across regions, while Same Day shipping consistently shows the lowest shipping costs.

* **Office Supplies** have the highest product quantities across all regions, indicating strong and consistent demand compared to Furniture and Technology.

* **Tables are the least profitable** subcategory, showing negative profit overall, with especially poor performance in the East Coast region.

* **California** leads all states in product quantity sold, making it the highest-volume state in the dataset.

## Recommendations
* **Take a closer look at Standard Class shipping** since it’s driving the highest costs. Shift orders to cheaper options or limit Standard Class to higher-margin products.

* **Lean into Office Supplies** which sell the most across all regions, by keeping strong inventory levels and avoiding heavy discounting that could effect their healthy performance.

* **Fix or rethink poorly performing products** like Tables, Bookcases, and Furnishings by reviewing pricing and discounts, and consider reducing or stopping promotions in regions where they consistently lose money.
