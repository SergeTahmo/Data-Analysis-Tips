### Power BI DAX & M Language Tips

This guide includes essential scripting tips for DAX (Data Analysis Expressions) and M (Power Query) used in Power BI.

---------------------------------------------------
 Part 1: DAX Tips & Best Practices
---------------------------------------------------

1. Create Measures, Not Calculated Columns
------------------------------------------
Total Sales = SUM(Sales[Revenue])
Profit Margin = DIVIDE([Profit], [Total Sales], 0)

2. Use Variables for Readability & Performance
----------------------------------------------
VAR totalCost = SUM(Sales[Cost])
VAR totalSales = SUM(Sales[Revenue])
RETURN DIVIDE(totalSales - totalCost, totalSales)

3. Avoid Iterators on Large Tables
----------------------------------
-- BAD:
SUMX(FILTER(Sales, Sales[Product] = "X"), Sales[Amount])
-- BETTER:
CALCULATE(SUM(Sales[Amount]), Sales[Product] = "X")

4. Use USERELATIONSHIP() for Inactive Relationships
---------------------------------------------------
Sales by Ship Date =
CALCULATE([Total Sales], USERELATIONSHIP(DimDate[Date], Sales[ShipDate]))

5. Time Intelligence Functions
------------------------------
YTD Sales = TOTALYTD([Total Sales], DimDate[Date])
MTD Sales = TOTALMTD([Total Sales], DimDate[Date])
Previous Month = CALCULATE([Total Sales], PREVIOUSMONTH(DimDate[Date]))

6. SELECTEDVALUE and HASONEVALUE
--------------------------------
Selected Region =
IF(HASONEVALUE(Regions[Region]), VALUES(Regions[Region]), "All")

Selected Year = SELECTEDVALUE(DimDate[Year], "Multiple")

7. CALCULATE with Filters
-------------------------
CALCULATE([Total Sales], Sales[Category] = "Furniture", Sales[Country] = "Canada")


---------------------------------------------------
🟦 Part 2: M Language (Power Query) Tips
---------------------------------------------------

1. Rename Columns Dynamically
-----------------------------
Table.RenameColumns(Source, {{"old_name", "new_name"}})

2. Remove Empty Rows
--------------------
Table.SelectRows(Source, each List.NonNullCount(Record.FieldValues(_)) > 0)

3. Change Column Types
----------------------
Table.TransformColumnTypes(Source, {{"Revenue", type number}, {"Date", type date}})

4. Trim and Clean Text
----------------------
Table.TransformColumns(Source, {{"CustomerName", Text.Trim, type text}})

5. Extract Date Parts
---------------------
Table.AddColumn(Source, "Year", each Date.Year([OrderDate]), Int64.Type)
Table.AddColumn(Source, "Month", each Date.Month([OrderDate]), Int64.Type)

6. Add Custom Columns
---------------------
Table.AddColumn(Source, "Profit Category", each
    if [Profit] > 1000 then "High"
    else if [Profit] > 0 then "Medium"
    else "Low")

7. Replace Errors
-----------------
Table.ReplaceErrorValues(Source, {{"Revenue", 0}})

8. Combine Files from Folder
----------------------------
let
    Source = Folder.Files("C:\\MyFolder"),
    Combine = Table.Combine(
        List.Transform(Source[Content], each Csv.Document(_, [Delimiter=",", Columns=5, Encoding=1252, QuoteStyle=QuoteStyle.None]))
    )
in
    Combine


---------------------------------------------------
🧠 Summary: When to Use DAX vs M
---------------------------------------------------

Feature               | DAX                        | M Language (Power Query)
----------------------|----------------------------|-----------------------------
Use Case              | Measures, KPIs             | Cleaning, shaping, merging
Executes              | At runtime                 | Before load (ETL)
Syntax Style          | Excel-like, row/contextual | Functional programming
Best For              | Metrics & logic            | Preprocessing & transformation

Keep your DAX clean |
Keep your M efficient |
Power BI rewards thoughtful modeling and scripting 
