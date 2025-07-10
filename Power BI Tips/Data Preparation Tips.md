#  Data Preparation Tips for Analysis & Modeling

Data preparation (also called data wrangling) is the foundation of any reliable analysis or machine learning pipeline. These tips help you transform raw data into clean, structured, and analysis-ready formats.

---------------------------------------------------
 1. Understand Your Raw Data
---------------------------------------------------

- Start by profiling the dataset:
  - Check row and column counts
  - Understand data types
  - Identify key columns (ID, timestamps, targets)

- Use tools like:
  - df.info(), df.describe() in pandas
  - Power Query's Column Quality & Distribution
  - Data profiling in Power BI

---------------------------------------------------
 2. Clean Missing Values
---------------------------------------------------

- Check for missing data in each column
- Strategies:
  - Drop rows/columns (if few or irrelevant)
  - Fill with mean, median, mode, or constants
  - Forward-fill/backward-fill (for time series)
  - Add flags for missing indicators

- Tools:
  - Python: df.fillna(), df.dropna()
  - Excel: IFERROR(), ISBLANK()
  - Power Query: Replace Errors, Fill Down/Up

---------------------------------------------------
 3. Handle Duplicates
---------------------------------------------------

- Remove exact duplicate rows
- Check for duplicate IDs or combinations
- Python: df.duplicated(), df.drop_duplicates()
- Power Query: Remove Duplicates on columns

---------------------------------------------------
 4. Standardize Formats & Units
---------------------------------------------------

- Dates: Use consistent formats (ISO 8601 preferred: YYYY-MM-DD)
- Text: Remove extra spaces, fix casing (UPPER/lower/Proper)
- Units: Standardize currencies, distance, weight, time, etc.

- Python: str.lower(), str.strip(), pd.to_datetime()
- Power Query: Transform → Format

---------------------------------------------------
 5. Correct Data Types
---------------------------------------------------

- Ensure dates are `datetime`, numbers are numeric
- Convert categorical variables where needed
- Power BI: Set data types in Model view
- Python: df.astype(), pd.to_numeric()

---------------------------------------------------
 6. Engineer Useful Features
---------------------------------------------------

- Extract:
  - Year, Month, Day, Weekday from dates
  - Text length, word count, sentiment from text
  - Ratios, percent changes, rolling averages

- Create flags (e.g. is_active, is_high_value)
- Use binning/bucketing for continuous values

---------------------------------------------------
 7. Flatten or Normalize Data
---------------------------------------------------

- For ML or reporting:
  - Convert nested structures to flat tables
  - Normalize or reshape pivoted tables
  - Merge/split columns where appropriate

---------------------------------------------------
 8. Join and Merge Datasets
---------------------------------------------------

- Define primary and foreign keys
- Use correct join types (inner, left, anti, etc.)
- Match on clean, standardized keys

- SQL: JOINs
- Python: pd.merge()
- Power BI: Relationships + Merge Queries

---------------------------------------------------
 9. Validate with Business Logic
---------------------------------------------------

- Revenue should not be negative
- Age should be between 0 and 120
- Order date should be before delivery date
- Create assertions or rule checks

---------------------------------------------------
 10. Save Clean Versions of Data
---------------------------------------------------

- Always back up the raw data
- Save cleaned version with date/time stamp
- Consider version control (e.g., Git or DVC)
- Common formats: CSV, Parquet, Excel, database

---------------------------------------------------
 Data Preparation Checklist
---------------------------------------------------

- [ ] All missing values handled or flagged?
- [ ] All duplicates removed?
- [ ] Correct data types for all columns?
- [ ] Consistent formatting (dates, text, numbers)?
- [ ] Features engineered and added?
- [ ] Columns renamed clearly and consistently?
- [ ] Final dataset saved and documented?

---------------------------------------------------
Clean data = Better analysis = Smarter decisions.
Invest in your data preparation and your results will follow.
