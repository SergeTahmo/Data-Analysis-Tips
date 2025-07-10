' =======================================
'  Power BI Data Modeling Tips & Tricks
' =======================================

' ========== 1. Naming Conventions ==========
-- Use PascalCase or snake_case for table and column names
-- Prefix lookup tables with "Dim_" and fact tables with "Fact_"
-- Example:
-- Dim_Customer, Fact_Sales, Dim_Date

' ========== 2. Relationships ==========
-- Always use a star schema (one-to-many from Dim to Fact)
-- Disable bidirectional filtering unless required
-- Cardinality: Use Single → Many when possible

' ========== 3. Create a Calendar Table ==========
-- Use DAX to create a Date Table:
Calendar = CALENDAR(DATE(2015,1,1), DATE(2030,12,31))

-- Mark it as the official date table in the Model view
-- Add columns: Year, Month, Quarter, DayOfWeek, etc.

' Example:
Year = YEAR('Calendar'[Date])
Month = FORMAT('Calendar'[Date], "MMMM")
MonthNum = MONTH('Calendar'[Date])
Quarter = "Q" & FORMAT('Calendar'[Date], "Q")

' ========== 4. Create Measures (Not Calculated Columns) ==========
-- Use Measures for performance and scalability
-- Example:
Total Sales = SUM(Fact_Sales[Revenue])
Profit Margin % = DIVIDE([Profit], [Total Sales], 0)

' ========== 5. Use Measures over Implicit Aggregations ==========
-- Always write your own DAX measures instead of dragging fields into visuals

' ========== 6. Avoid Auto Date/Time ==========
-- Turn it off in Options → Data Load → Time Intelligence → Uncheck
-- Use your custom Date table instead

' ========== 7. Organize Your Fields ==========
-- Use Display Folders to group related measures
-- Example: Measures Folder → KPIs, Totals, Ratios

' ========== 8. Use Relationships Over LOOKUPVALUE ==========
-- Use physical/model relationships instead of LOOKUPVALUE or RELATED wherever possible

' ========== 9. Hide Unused Columns ==========
-- Hide keys and helper columns from report view
-- Only expose business-readable fields

' ========== 10. Performance Tips ==========
-- Avoid using DAX iterator functions in large datasets: SUMX, AVERAGEX
-- Use variables to optimize repeated calculations
-- Example:
VAR TotalRevenue = SUM(Fact_Sales[Revenue])
RETURN TotalRevenue * 0.1

' ========== 11. Use Role-Playing Dimensions Carefully ==========
-- Create separate inactive relationships (e.g., Order Date, Ship Date)
-- Use USERELATIONSHIP in measures:
Total Sales by Ship Date =
CALCULATE([Total Sales], USERELATIONSHIP(Dim_Date[Date], Fact_Sales[ShipDate]))

' ========== 12. Create a “Disconnected Table” for What-If Analysis ==========
-- Create a parameter table for slicers or simulations
-- No relationship required; use in CALCULATE + FILTER

' =========================================
'  Best Practices Summary:
-- Use a star schema, not snowflake
-- Use measures not calculated columns
-- Leverage display folders for clean models
-- Always use a Date table and mark it
-- Keep your model lean: remove/hide unused data
' =========================================
