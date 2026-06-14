-- ============================================
-- Sales Budget Analytics Project
-- Author: Altin Salihi
-- Description: SQL analysis queries for business insights
-- ============================================

-- Use database
USE sales_budget_project;

-- ============================================
-- 1. Preview Data
-- ============================================
SELECT *
FROM sales_data
LIMIT 10;

-- ============================================
-- 2. Totalzpo Revenue, Cost, Profit, Budget, Variance
-- ============================================
SELECT
SUM(Revenue) AS Total_Revenue,
SUM(Cost_Total) AS Total_Cost,
SUM(Profit) AS Total_Profit,
SUM(Budget_Value) AS Total_Budget,
SUM(Variance) AS Total_Variance
FROM sales_data;

-- ============================================
-- 3. Revenue by Location
-- ============================================
SELECT
Location,
SUM(Revenue) AS Total_Revenue
FROM sales_data
GROUP BY Location
ORDER BY Total_Revenue DESC;

-- ============================================
-- 4. Profit by Category
-- ============================================
SELECT
Category,
SUM(Profit) AS Total_Profit
FROM sales_data
GROUP BY Category
ORDER BY Total_Profit DESC;

-- ============================================
-- 5. Budget vs Actual by Month
-- ============================================
SELECT
Month,
SUM(Revenue) AS Revenue,
SUM(Budget_Value) AS Budget
FROM sales_data
GROUP BY Month
ORDER BY Month;

-- ============================================
-- 6. Top 5 Products by Revenue
-- ============================================
SELECT
Material_Description AS Product,
SUM(Revenue) AS Total_Revenue
FROM sales_data
GROUP BY Material_Description
ORDER BY Total_Revenue DESC
LIMIT 5;

-- ============================================
-- 7. Variance by Location
-- ============================================
SELECT
Location,
SUM(Variance) AS Total_Variance
FROM sales_data
GROUP BY Location
ORDER BY Total_Variance DESC;

-- ============================================
-- 8. Monthly Profit Trend
-- ============================================
SELECT
Month,
SUM(Profit) AS Total_Profit
FROM sales_data
GROUP BY Month
ORDER BY Month;

-- ============================================
-- 9. Category Performance (Revenue & Profit)
-- ============================================
SELECT
Category,
SUM(Revenue) AS Total_Revenue,
SUM(Profit) AS Total_Profit
FROM sales_data
GROUP BY Category
ORDER BY Total_Revenue DESC;

-- ============================================
-- 10. Detailed Product Performance
-- ============================================
SELECT
Material_Description AS Product,
SUM(Revenue) AS Revenue,
SUM(Profit) AS Profit,
SUM(Variance) AS Variance
FROM sales_data
GROUP BY Material_Description
ORDER BY Revenue DESC;
