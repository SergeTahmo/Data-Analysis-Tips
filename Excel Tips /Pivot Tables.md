# 📊 Excel Pivot Table Tips & Tricks

Excel PivotTables are powerful tools for summarizing, analyzing, and exploring data without writing formulas. This guide covers practical tips to master PivotTables and unlock dynamic, insightful reporting.

---

##  1. Getting Started with PivotTables

- Select your dataset (including headers).
- Go to: `Insert` → `PivotTable`.
- Choose location (new worksheet or existing).
- Drag fields into: 
  - **Rows** (categories)
  - **Columns** (subcategories)
  - **Values** (numeric summaries)
  - **Filters** (slicers)

---

##  2. Refresh Data Automatically

When the source data changes:
- Right-click inside the PivotTable → `Refresh`.
- OR use the shortcut: `Alt + F5`.
- You can also check: `PivotTable Options` → `Data` → Enable *"Refresh data when opening the file"*.

---

##  3. Change Summary Calculations

By default, numbers are summed:
- Click a value → `Value Field Settings`.
- Choose from:
  - **Sum, Count, Average**
  - **Max, Min, StdDev**
  - **% of Total**, **Running Total**, etc.

---

##  4. Grouping Data

###  Group Dates:
- Right-click a date → `Group`.
- Choose: `Years`, `Quarters`, `Months`, etc.

### Group Numbers:
- Right-click number values (e.g., ages) → `Group`.
- Specify range intervals (e.g., 0–10, 10–20…).

---

##  5. Filtering with Slicers & Timelines

### Slicers:
- Select PivotTable → `Insert` → `Slicer`.
- Great for filtering by category (e.g., Product, Region).

### Timelines:
- Use for Date filters.
- Select PivotTable → `Insert` → `Timeline`.

---

##  6. Calculated Fields

Create custom formulas:
- Click anywhere inside the PivotTable.
- Go to `PivotTable Analyze` → `Fields, Items & Sets` → `Calculated Field`.
- Example:
  ```excel
  = Revenue - Cost
