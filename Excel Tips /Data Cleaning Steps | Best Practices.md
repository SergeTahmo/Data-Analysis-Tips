#  Data Cleaning: Step-by-Step Guide & Best Practices

Cleaning data is one of the most crucial and time-consuming steps in any data analysis or machine learning workflow. This guide outlines a structured approach to ensure your data is accurate, consistent, and analysis-ready.

---

##  Why Data Cleaning Matters

Bad data leads to:
- Misleading insights
- Broken visualizations
- Poor model performance

Clean data enables:
- Accurate analysis
- Trustworthy dashboards
- Better business decisions

---

## Step-by-Step Data Cleaning Process

### 1. Understand the Data

- Know your columns, units, expected ranges
- Read documentation or metadata if available
- Use `df.info()` and `df.describe()` in Python

---

### 2. Handle Missing Values

- Identify with `isnull().sum()` or visual tools (e.g., missingno)
- Strategies:
  - Drop rows/columns if impact is minimal
  - Fill (`mean`, `median`, `mode`, `forward fill`, `backward fill`)
  - Use domain-specific defaults
  - Flag missing values for later analysis

---

### 3. Fix Data Types

- Convert `object` to `datetime`, `int`, `float`, or `category`
- Avoid mixed types in the same column
- Example (Python):
  ```python
  df['date'] = pd.to_datetime(df['date'], errors='coerce')
  df['price'] = df['price'].astype(float)


### Excel Data Cleaning Tips — Code Format

<pre lang="excel"> ' ========================== ' 1. Remove Duplicates ' ========================== ' Excel Menu: Data → Remove Duplicates ' Shortcut: Alt + A + M ' ========================== ' 2. Trim Extra Spaces ' ========================== =TRIM(A2) ' Removes leading/trailing and extra spaces ' ========================== ' 3. Remove Non-Printable Characters ' ========================== =CLEAN(A2) ' Removes line breaks, tabs, etc. ' ========================== ' 4. Convert Text to Proper Case ' ========================== =PROPER(A2) ' John Doe =UPPER(A2) ' JOHN DOE =LOWER(A2) ' john doe ' ========================== ' 5. Find and Replace ' ========================== ' Ctrl + H → Replace "N/A" or "-" with blank ' ========================== ' 6. Split Data into Columns ' ========================== ' Data → Text to Columns → Delimited (e.g. comma, space) ' ========================== ' 7. Convert Text to Numbers ' ========================== =VALUE(A2) ' Or use the ⚠️ "Convert to Number" smart tag ' ========================== ' 8. Remove Blank Rows ' ========================== ' Ctrl + G → Special → Blanks → Right-click → Delete Rows ' ========================== ' 9. Highlight Duplicates ' ========================== ' Home → Conditional Formatting → Highlight Cells Rules → Duplicate Values ' ========================== '10. Combine Data from Columns ' ========================== =CONCATENATE(A2, " ", B2) =TEXTJOIN(" ", TRUE, A2, B2, C2) ' ========================== '11. Flag Outliers (Simple Z-Score Logic) ' ========================== =IF(ABS(A2 - AVERAGE($A$2:$A$100)) > 3 * STDEV.P($A$2:$A$100), "Outlier", "OK") ' ========================== '12. Fix Dates Stored as Text ' ========================== =DATEVALUE(A2) ' Then format cell as Date ' ========================== '13. Standardize Headers ' ========================== ' Rename to lowercase, underscore_separated: e.g., first_name, order_date ' ========================== '14. Use Filters ' ========================== ' Ctrl + Shift + L → Apply AutoFilter ' Filter by blanks, text in numeric fields, errors, etc. </pre>
