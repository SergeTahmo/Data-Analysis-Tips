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
