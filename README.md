
<img width="661" height="258" alt="Screenshot 2026-01-22 092641" src="https://github.com/user-attachments/assets/9da60307-a7df-4d53-81a3-1c1872b9bca9" />

# Denmark-Residential-Housing-Market-Trends-1992-2024-DKK Currency-SQL--EXCEL--Tableau
The Danish residential housing market has experienced significant changes over the past three decades, influenced by economic conditions, interest rates, and regional development. In this case study, I analyze housing transaction data from 1992 to 2024 to uncover long-term pricing trends and key factors that impact home values.

To guide the analysis, I used AI to generate five practical questions that a stakeholder or decision-maker would realistically ask when evaluating the housing market. Using SQL and Excel for data preparation and Tableau for visualization, I translated these questions into clear, concise, and easy-to-understand visuals designed to make insights accessible to both technical and non-technical audiences.

This specific data was provided by Kaggle and can be viewed [here](https://www.kaggle.com/datasets/martinfrederiksen/danish-residential-housing-prices-1992-2024).

## Scope Of Analysis: Stakeholder Questions
* How have residential housing prices changed over time, and how do trends differ by region?
* Which house types have experienced the highest price growth over time?
* How do macroeconomic factors, such as nominal interest rates and inflation, relate to housing prices and sales trends in Denmark?
* Are newer homes priced at a premium compared to older homes, and does this vary by region or house type?
* How does the difference between offer price and final purchase price vary across regions, market conditions, and time periods?
* What insights can be drawn from average housing prices and percentage differences between offer and purchase prices across house age groups?

 ## SQL Methodology

SQL was used to aggregate, clean, and prepare Denmark residential housing data for analysis and visualization.

* **Data Aggregation:** Joined housing and pricing datasets using a LEFT JOIN on house_id, combining property attributes with purchase prices and economic indicators while filtering for complete records.

* **Data Quality Checks:** Performed conditional aggregation to identify missing values across key fields, revealing minor gaps in geographic data.

* **Data Cleaning:** Removed rows with missing location information and revalidated the dataset to ensure completeness.

* **Data Standardization:** Reformatted dates, normalized text fields, and rounded numeric and percentage values for consistency and reporting clarity.

* **Descriptive Statistics:** Calculated mean, median, and mode for key variables (rooms, square meters, price per square meter, and purchase price) using BigQuery-safe functions.

View the SQL scripts that document the full data preparation and calculation process for this case study [here](https://github.com/smouzakitis83/Denmark-Residential-Housing-Market-Trends-1992-2024-DKK-Currency-SQL--EXCEL--Tableau/blob/main/SQL%20QUERIES%20FOR%20DK_HOUSING.SQL).

## Tableau Visual Analysis

This Tableau visualization combines line and bar charts to illustrate changes in residential housing prices, house types, annual inflation, nominal interest rates, house age averages, and the percentage change between offer and purchase over time. Interactive filters for house type and region allow users to dynamically explore trends and compare market behavior across different segments. View and explore this interactive Tableau visualization [here](https://public.tableau.com/app/profile/stamatios.mouzakitis/viz/DenmarkResidentialHousingMarketTrends19922024DKKCurrency/Dashboard1).

<img width="1602" height="906" alt="Screenshot 2026-01-23 084014" src="https://github.com/user-attachments/assets/87221386-4ad9-49a2-85fa-8b3ac0b50403" />

## Excel Analysis & Quality Checks
A statistical Excel dashboard was developed with eight charts displaying average values for all integer columns. Additional summary statistics, including median and mode, were calculated for all numeric fields to support data validation and trend analysis.
The cleaned Excel dataset used for analysis and validation can be viewed [here](https://github.com/smouzakitis83/Denmark-Residential-Housing-Market-Trends-1992-2024-DKK-Currency-SQL--EXCEL--Tableau/blob/main/DK_Housing_C_C_Clean.xlsx).

<img width="1650" height="956" alt="Screenshot 2026-01-22 112439" src="https://github.com/user-attachments/assets/424afb14-ec48-42a3-a167-b154b4443343" />

<img width="1630" height="148" alt="Screenshot 2026-01-22 112411" src="https://github.com/user-attachments/assets/23d9a04f-57e4-438c-8b39-5a23847bc432" />

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
