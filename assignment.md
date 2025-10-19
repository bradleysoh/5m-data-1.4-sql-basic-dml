# Assignment

## Brief

Write the SQL DML statements for the following questions.

## Instructions

Paste the answer as SQL in the answer code section below each question.

### Question 1

Select the minimum and maximum price per sqm of all the flats.

```sql
SELECT 
  ROUND(MAX(rpf.resale_price/rpf.floor_area_sqm),2) AS Maximum_price_per_sqm, 
	ROUND(MIN(rpf.resale_price/rpf.floor_area_sqm),2) AS Minimum_price_per_sqm,
FROM resale_flat_prices_2017 rpf;
```

### Question 2

Select the average price per sqm for flats in each town.

```sql
SELECT 
  rpf.town, ROUND(AVG(rpf.resale_price/rpf.floor_area_sqm),2) AS Average_price_per_sqm
FROM resale_flat_prices_2017 rpf
GROUP BY rpf.town
ORDER BY rpf.town;
```

### Question 3

Categorize flats into price ranges and count how many flats fall into each category:

- Under $400,000: 'Budget'
- $400,000 to $700,000: 'Mid-Range'
- Above $700,000: 'Premium'
  Show the counts in descending order.

```sql
SELECT 
	COUNT(*) AS Number_of_Flats,
	CASE
		WHEN rpf.resale_price < 400000 THEN 'Budget'
		WHEN rpf.resale_price BETWEEN 400000 AND 700000 THEN 'Mid-Range'
		WHEN rpf.resale_price > 700000 THEN 'Premium' 
		ELSE 'Unclassified'
	END AS Price_Category
FROM resale_flat_prices_2017 rpf
GROUP BY Price_Category
ORDER BY Number_of_Flats DESC;
```

### Question 4

Count the number of flats sold in each town during the first quarter of 2017 (January to March).

```sql
SELECT 
	rpf.town, COUNT(*) AS Number_of_Flats_Sold
FROM resale_flat_prices_2017 rpf
WHERE rpf.month IN ('2017-01', '2017-02', '2017-03')
GROUP BY rpf.town
ORDER BY rpf.town;
```

## Submission

- Submit the URL of the GitHub Repository that contains your work to NTU black board.
- Should you reference the work of your classmate(s) or online resources, give them credit by adding either the name of your classmate or URL.
