# ⚡ Power BI Performance Optimization Tips

This guide outlines key techniques for improving report performance, reducing load time, and ensuring efficient data models in Power BI.

---------------------------------------------------
🟢 1. Optimize the Data Model
---------------------------------------------------

- Remove unnecessary columns and tables
- Use only the required granularity of data
- Prefer numeric types over text where possible
- Avoid calculated columns when measures will suffice
- Hide columns not used in visuals

---------------------------------------------------
🟡 2. Use Star Schema Instead of Snowflake
---------------------------------------------------

- Flatten snowflake models to a star schema
- Create one-to-many relationships from dimension to fact tables
- Avoid circular and many-to-many relationships when possible

---------------------------------------------------
🔵 3. Reduce Data Volume
---------------------------------------------------

- Filter rows at the source (SQL, Power Query)
- Use parameters to limit imported data (e.g., last 12 months)
- Aggregate data before loading (e.g., monthly totals instead of daily)

---------------------------------------------------
🟣 4. Optimize DAX Measures
---------------------------------------------------

- Use variables to reduce repeated calculations
  VAR TotalSales = SUM(Sales[Amount])
  RETURN TotalSales * 0.1

- Avoid row-based iterators (SUMX, FILTER) on large tables
- Use IF instead of SWITCH where simpler
- Avoid CALCULATE inside IF/OR/AND logic unnecessarily

---------------------------------------------------
🟠 5. Limit Visuals & Complexity
---------------------------------------------------

- Reduce number of visuals per page (ideally under 12)
- Avoid overusing slicers, especially with large distinct values
- Turn off unnecessary interactions between visuals

---------------------------------------------------
🟤 6. Optimize Power Query (M)
---------------------------------------------------

- Keep transformations simple and step-by-step
- Avoid column-by-column transformations on large tables
- Remove columns early to reduce memory load
- Use native SQL queries if sourcing from databases

---------------------------------------------------
⚪ 7. Disable Auto Date/Time
---------------------------------------------------

- Go to: File → Options → Data Load
- Uncheck "Auto Date/Time" for new files
- Use your own date table instead

---------------------------------------------------
🟥 8. Enable Performance Analyzer
---------------------------------------------------

- View → Performance Analyzer → Start Recording
- Capture load time of each visual
- Use this to identify slow visuals or measures

---------------------------------------------------
🧠 9. Use Aggregations When Possible
---------------------------------------------------

- Pre-aggregate data in Power Query or SQL
- Load summarized data alongside detailed data
- Use aggregation tables with composite models

---------------------------------------------------
✅ Performance Checklist
---------------------------------------------------

- [ ] Model size minimized (only necessary columns/tables)
- [ ] No unnecessary relationships or bi-directional filters
- [ ] DAX measures use variables and optimized logic
- [ ] Auto Date/Time disabled and custom date table used
- [ ] Power Query transformations are efficient
- [ ] Performance Analyzer used to debug slow visuals
- [ ] Complex or high-cardinality visuals reduced
- [ ] Aggregations or data reduction techniques applied

---------------------------------------------------
Fast dashboards = Happy users.
Optimize early. Test often. Scale with confidence.
