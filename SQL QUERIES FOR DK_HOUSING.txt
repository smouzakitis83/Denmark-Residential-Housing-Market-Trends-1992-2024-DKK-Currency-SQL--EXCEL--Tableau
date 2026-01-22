SQL QUERIES FOR DK_HOUSING


----DATA AGGREGATION----

/* This query uses a LEFT JOIN to combine housing records with pricing data based on a shared house_id. 
It then filters the results to include only rows where both tables contain matching, non-null records,
ensuring the dataset contains complete housing and pricing information.*/

SELECT
  h.*,
  p.purchase_price,
  `%_change_between_offer_and_purchase`,
  p.`nom_interest_rate%`,
  `dk_ann_infl_rate%`,
  `yield_on_mortgage_credit_bonds%`
FROM `steve-m.DK_Housing.dk_housing` AS h
LEFT JOIN `steve-m.DK_Housing.dk_housing_Prices` AS p
  ON h.house_id = p.house_id
WHERE
  p IS NOT NULL
  AND h IS NOT NULL;



----DATA CLEANING----

/* This query uses a subquery to join housing and pricing data, then checks each column for missing values using conditional aggregation.
The results identified 11 missing values in the city column, indicating areas requiring additional data cleaning prior to analysis.
This step ensures data completeness and reliability before proceeding with further transformations and insights. */

SELECT
  COUNT(*) AS total_rows,
  SUM(CASE WHEN date IS NULL THEN 1 ELSE 0 END) AS missing_date,
  SUM(CASE WHEN quarter IS NULL THEN 1 ELSE 0 END) AS missing_quarter,
  SUM(CASE WHEN house_type IS NULL THEN 1 ELSE 0 END) AS missing_house_type,
  SUM(CASE WHEN sales_type IS NULL THEN 1 ELSE 0 END) AS missing_sales_type,
  SUM(CASE WHEN year_build IS NULL THEN 1 ELSE 0 END) AS missing_year_build,
  SUM(CASE WHEN no_rooms IS NULL THEN 1 ELSE 0 END) AS missing_no_rooms,
  SUM(CASE WHEN sqm IS NULL THEN 1 ELSE 0 END) AS missing_sqm,
  SUM(CASE WHEN sqm_price IS NULL THEN 1 ELSE 0 END) AS missing_sqm_price,
  SUM(CASE WHEN address IS NULL THEN 1 ELSE 0 END) AS missing_address,
  SUM(CASE WHEN zip_code IS NULL THEN 1 ELSE 0 END) AS missing_zip_code,
  SUM(CASE WHEN city IS NULL THEN 1 ELSE 0 END) AS missing_city,
  SUM(CASE WHEN area IS NULL THEN 1 ELSE 0 END) AS missing_area,
  SUM(CASE WHEN region IS NULL THEN 1 ELSE 0 END) AS missing_region,
  SUM(CASE WHEN purchase_price IS NULL THEN 1 ELSE 0 END)
    AS missing_purchase_price,
  SUM(CASE WHEN '%_change_between_offer_and_purchase' IS NULL THEN 1 ELSE 0 END)
    AS missing_change_between_offer_and_purchase,
  SUM(CASE WHEN 'dk_ann_infl_rate%' IS NULL THEN 1 ELSE 0 END)
    AS missing_dk_ann_infl_rate,
  SUM(CASE WHEN 'nom_interest_rate%' IS NULL THEN 1 ELSE 0 END)
    AS missing_nom_interest_rate,
  SUM(CASE WHEN 'yield_on_mortgage_credit_bonds%' IS NULL THEN 1 ELSE 0 END)
    AS missing_yield_on_mortgage_credit_bonds,
FROM
  (
    SELECT
      h.*,
      p.purchase_price,
      `%_change_between_offer_and_purchase`,
      p.`nom_interest_rate%`,
      `dk_ann_infl_rate%`,
      `yield_on_mortgage_credit_bonds%`
    FROM `steve-m.DK_Housing.dk_housing` AS h
    LEFT JOIN `steve-m.DK_Housing.dk_housing_Prices` AS p
      ON h.house_id = p.house_id
    WHERE
      p IS NOT NULL
      AND h IS NOT NULL
  )





/* This query pulls all housing and pricing data while removing any rows where the city value is missing. 
By filtering out nulls in the city column, the dataset is cleaner and ready for analysis without incomplete location information.*/

SELECT *
FROM
  (
    SELECT
      h.*,
      p.purchase_price,
      `%_change_between_offer_and_purchase`,
      p.`nom_interest_rate%`,
      `dk_ann_infl_rate%`,
      `yield_on_mortgage_credit_bonds%`
    FROM `steve-m.DK_Housing.dk_housing` AS h
    LEFT JOIN `steve-m.DK_Housing.dk_housing_Prices` AS p
      ON h.house_id = p.house_id
    WHERE
      p IS NOT NULL
      AND h IS NOT NULL
  )
WHERE city IS NOT NULL




/* This query rechecks all key columns in the joined housing and pricing dataset, including the city column that previously had 11 nulls. 
The results confirm that those nulls are now removed, making the dataset complete and ready for analysis.*/

SELECT
  COUNT(*) AS total_rows,
  SUM(CASE WHEN date IS NULL THEN 1 ELSE 0 END) AS missing_date,
  SUM(CASE WHEN quarter IS NULL THEN 1 ELSE 0 END) AS missing_quarter,
  SUM(CASE WHEN house_type IS NULL THEN 1 ELSE 0 END) AS missing_house_type,
  SUM(CASE WHEN sales_type IS NULL THEN 1 ELSE 0 END) AS missing_sales_type,
  SUM(CASE WHEN year_build IS NULL THEN 1 ELSE 0 END) AS missing_year_build,
  SUM(CASE WHEN no_rooms IS NULL THEN 1 ELSE 0 END) AS missing_no_rooms,
  SUM(CASE WHEN sqm IS NULL THEN 1 ELSE 0 END) AS missing_sqm,
  SUM(CASE WHEN sqm_price IS NULL THEN 1 ELSE 0 END) AS missing_sqm_price,
  SUM(CASE WHEN address IS NULL THEN 1 ELSE 0 END) AS missing_address,
  SUM(CASE WHEN zip_code IS NULL THEN 1 ELSE 0 END) AS missing_zip_code,
  SUM(CASE WHEN city IS NULL THEN 1 ELSE 0 END) AS missing_city,
  SUM(CASE WHEN area IS NULL THEN 1 ELSE 0 END) AS missing_area,
  SUM(CASE WHEN region IS NULL THEN 1 ELSE 0 END) AS missing_region,
  SUM(CASE WHEN purchase_price IS NULL THEN 1 ELSE 0 END)
    AS missing_purchase_price,
  SUM(CASE WHEN '%_change_between_offer_and_purchase' IS NULL THEN 1 ELSE 0 END)
    AS missing_change_between_offer_and_purchase,
  SUM(CASE WHEN 'dk_ann_infl_rate%' IS NULL THEN 1 ELSE 0 END)
    AS missing_dk_ann_infl_rate,
  SUM(CASE WHEN 'nom_interest_rate%' IS NULL THEN 1 ELSE 0 END)
    AS missing_nom_interest_rate,
  SUM(CASE WHEN 'yield_on_mortgage_credit_bonds%' IS NULL THEN 1 ELSE 0 END)
    AS missing_yield_on_mortgage_credit_bonds,
FROM
(SELECT *
FROM
  (
    SELECT
      h.*,
      p.purchase_price,
      `%_change_between_offer_and_purchase`,
      p.`nom_interest_rate%`,
      `dk_ann_infl_rate%`,
      `yield_on_mortgage_credit_bonds%`
    FROM `steve-m.DK_Housing.dk_housing` AS h
    LEFT JOIN `steve-m.DK_Housing.dk_housing_Prices` AS p
      ON h.house_id = p.house_id
    WHERE
      p IS NOT NULL
      AND h IS NOT NULL
  )
WHERE city IS NOT NULL)





/* This query cleans and prepares the dataset by formatting the date into U.S. month/day/year format and normalizing all
 text fields using TRIM, UPPER, and LOWER to ensure consistent capitalization. 
Floating-point columns were rounded to two decimal places for improved readability and reporting accuracy. 
These transformations prepare the dataset for reliable analysis and seamless export to Excel or visualization tools.*/

SELECT
  FORMAT_DATE('%m/%d/%Y', date) AS datesqm_price,
  quarter,
  house_id,
  CONCAT(
    UPPER(SUBSTR(TRIM(house_type), 1, 1)),
    LOWER(SUBSTR(TRIM(house_type), 2))) AS house_type,
  CONCAT(
    UPPER(SUBSTR(TRIM(sales_type), 1, 1)),
    LOWER(SUBSTR(TRIM(sales_type), 2))) AS sales_type,
  year_build,
  no_rooms,
  sqm,
  Round(sqm_price, 2) AS sqm_price,
  CONCAT(
    UPPER(SUBSTR(TRIM(address), 1, 1)),
    LOWER(SUBSTR(TRIM(address), 2))) AS address,
  zip_code,
  CONCAT(
    UPPER(SUBSTR(TRIM(city), 1, 1)),
    LOWER(SUBSTR(TRIM(city), 2))) AS city,
  CONCAT(
    UPPER(SUBSTR(TRIM(area), 1, 1)),
    LOWER(SUBSTR(TRIM(area), 2))) AS area,
  CONCAT(
    UPPER(SUBSTR(TRIM(region), 1, 1)),
    LOWER(SUBSTR(TRIM(region), 2))) AS region,
  purchase_price,
  `%_change_between_offer_and_purchase`,
  round(`nom_interest_rate%`, 2) AS `nom_interest_rate%`,
  round(`dk_ann_infl_rate%`, 2) AS `dk_ann_infl_rate%`,
  round(`yield_on_mortgage_credit_bonds%`, 2)
    AS `yield_on_mortgage_credit_bonds%`
FROM `steve-m.DK_Housing.DK_Housing_Combined`




----CALCULATED COLUMNS----


-- This query calculates the mean, median, and mode for the number of rooms
-- to summarize the central tendency of housing size in the dataset.


SELECT
  -- Mean
  Round(AVG(no_rooms),2) AS mean_no_rooms,

  -- Median (BigQuery-safe)
  APPROX_QUANTILES(no_rooms, 2)[OFFSET(1)] AS median_no_rooms,

  -- Mode
  (
    SELECT no_rooms
    FROM `steve-m.DK_Housing.DK_Housing_C_C`
    WHERE no_rooms IS NOT NULL
    GROUP BY no_rooms
    ORDER BY COUNT(*) DESC
    LIMIT 1
  ) AS mode_no_rooms

FROM `steve-m.DK_Housing.DK_Housing_C_C`
WHERE no_rooms IS NOT NULL;





-- This query calculates the mean, median, and mode for the square meters (sqm)
-- to summarize the central tendency of property size in the dataset.

SELECT
  -- Mean (rounded to 2 decimals)
  ROUND(AVG(sqm), 2) AS mean_sqm,

  -- Median
  APPROX_QUANTILES(sqm, 2)[OFFSET(1)] AS median_sqm,

  -- Mode
  (
    SELECT sqm
    FROM `steve-m.DK_Housing.DK_Housing_C_C`
    WHERE sqm IS NOT NULL
    GROUP BY sqm
    ORDER BY COUNT(*) DESC
    LIMIT 1
  ) AS mode_sqm

FROM `steve-m.DK_Housing.DK_Housing_C_C`
WHERE sqm IS NOT NULL;




-- This query calculates the mean, median, and mode for the square meter price (sqm_price)
-- to summarize the central tendency of property pricing per square meter in the dataset.

SELECT
  -- Mean (rounded to 2 decimals)
  ROUND(AVG(sqm_price), 2) AS mean_sqm_price,

  -- Median
  APPROX_QUANTILES(sqm_price, 2)[OFFSET(1)] AS median_sqm_price,

  -- Mode
  (
    SELECT sqm_price
    FROM `steve-m.DK_Housing.DK_Housing_C_C`
    WHERE sqm_price IS NOT NULL
    GROUP BY sqm_price
    ORDER BY COUNT(*) DESC
    LIMIT 1
  ) AS mode_sqm_price

FROM `steve-m.DK_Housing.DK_Housing_C_C`
WHERE sqm_price IS NOT NULL;




-- This query calculates the mean, median, and mode for the purchase price
-- to summarize the central tendency of property purchase values in the dataset.

SELECT
  -- Mean (rounded to 2 decimals)
  ROUND(AVG(purchase_price), 2) AS mean_purchase_price,

  -- Median
  APPROX_QUANTILES(purchase_price, 2)[OFFSET(1)] AS median_purchase_price,

  -- Mode
  (
    SELECT purchase_price
    FROM `steve-m.DK_Housing.DK_Housing_C_C`