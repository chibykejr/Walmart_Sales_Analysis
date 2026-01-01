# Walmart Sales Data Analysis

## Project Overview
This project involves a comprehensive analysis of Walmart sales data across various branches and cities. The goal is to explore historical sales patterns, evaluate the performance of different product lines, and understand customer behavior to optimize business strategies. 

The project utilizes SQL for extensive Data Engineering (Feature Engineering) and Exploratory Data Analysis (EDA) to answer critical business questions regarding revenue, taxation, and customer satisfaction.

## Project Structure
The repository consists of the following primary components:

* **Data Asset**
    * `WalmartSalesData.csv`: A dataset containing 1,000 transactions from three different branches (A, B, C) located in Yangon, Naypyitaw, and Mandalay.
* **Database Engineering & Analysis**
    * `Walmart_SQL_queries.sql`: A comprehensive SQL script that handles table creation, data cleaning, feature engineering, and high-level analytical queries.

## Data Engineering & Feature Engineering
To provide more granular insights, the raw data was enhanced through feature engineering in SQL:

1.  **Time of Day**: Categorizes transactions into *Morning*, *Afternoon*, and *Evening* to identify peak shopping hours.
2.  **Day Name**: Extracts the day of the week (Mon, Tue, etc.) to determine the busiest days for each branch.
3.  **Month Name**: Extracts the month to help determine sales and profit trends throughout the year.



## Key Analytical Questions Addressed
The SQL analysis is divided into three main categories:

### 1. Product Analysis
* Which product lines are the top performers by revenue and quantity?
* Which product line has the largest Value Added Tax (VAT)?
* Identifying product lines that are performing above or below the average sales threshold.

### 2. Sales Analysis
* Number of sales made in each time of the day per weekday.
* Which customer types (Member vs. Normal) bring the most revenue?
* Which city has the largest tax percent/VAT?

### 3. Customer Analysis
* Which customer type pays the most in VAT?
* Distribution of gender per branch.
* Which time of the day and day of the week receive the best average customer ratings?

## SQL Logic Examples
The following snippet demonstrates how the project categorizes sales by time of day:

```sql
-- Categorizing time into periods
SELECT
    time,
    (CASE
        WHEN `time` BETWEEN "00:00:00" AND "12:00:00" THEN "Morning"
        WHEN `time` BETWEEN "12:01:00" AND "16:00:00" THEN "Afternoon"
        ELSE "Evening"
    END) AS time_of_day
FROM sales;

-- Updating the table with the new feature
ALTER TABLE sales ADD COLUMN time_of_day VARCHAR(20);
UPDATE sales SET time_of_day = (/* CASE logic above */);
