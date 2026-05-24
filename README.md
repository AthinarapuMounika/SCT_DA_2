# SCT_DA_2
# Task 02 — Data Cleaning and Preparation

An end-to-end data cleaning and preprocessing workflow using Python and Pandas to prepare a Superstore dataset for analysis by handling missing values, removing duplicate records, converting data types, and exporting cleaned data.

---

## Objective

Load a dataset into Google Colab using Pandas and perform:

- Identify and handle missing values
- Remove duplicate rows
- Convert string columns into date format
- Clean and preprocess raw data
- Export cleaned data into a new CSV file

---

## Dataset

**Source:** Sample Superstore Dataset

| Property | Details |
|---|---|
| File | `samplesuperstore.csv` |
| Key columns | `Order Date`, `Ship Date`, `Sales`, `Profit`, `Category`, `Region` |

> Dataset loaded into Google Colab using the Pandas library.

---

## Project Structure

```text
SCT_DA_2.ipynb
samplesuperstore.csv
Cleaned_Global_Superstore.csv
README.md
```

---

## Requirements

Install dependencies with:

```bash
pip install pandas
```

| Library | Purpose |
|---|---|
| pandas | Data loading and preprocessing |

---

## How to Run

1. Open Google Colab or Jupyter Notebook  
2. Upload `samplesuperstore.csv`  
3. Run all notebook cells step-by-step  
4. Perform cleaning operations  
5. Export cleaned dataset  

---

## Analysis Steps

| Step | Description |
|---|---|
| 1 | Import Pandas library |
| 2 | Load dataset |
| 3 | Display first 5 rows |
| 4 | Check missing values |
| 5 | Fill numerical missing values |
| 6 | Fill categorical missing values |
| 7 | Remove duplicate rows |
| 8 | Convert date columns |
| 9 | Export cleaned dataset |

---

## Code Used

```python
import pandas as pd

# Load dataset
df = pd.read_csv("/content/samplesuperstore.csv")

# Display first rows
print("First 5 rows:")
print(df.head())

# Check missing values
print("\nMissing values:")
print(df.isnull().sum())

# Fill numerical missing values
numeric_cols = df.select_dtypes(include=['int64','float64']).columns

for col in numeric_cols:
    df[col] = df[col].fillna(df[col].mean())

# Fill text missing values
categorical_cols = df.select_dtypes(include=['object']).columns

for col in categorical_cols:
    df[col] = df[col].fillna(df[col].mode()[0])

# Remove duplicates
df.drop_duplicates(inplace=True)

# Convert date columns
df['Order Date'] = pd.to_datetime(df['Order Date'], errors='coerce')
df['Ship Date'] = pd.to_datetime(df['Ship Date'], errors='coerce')

# Save cleaned data
df.to_csv("Cleaned_Global_Superstore.csv", index=False)

print("Cleaning completed successfully")
```

---

## Key Findings

- Missing values were checked successfully
- No missing values were found in the dataset
- Duplicate rows were removed
- Order Date and Ship Date converted into datetime format
- Dataset cleaned successfully
- Cleaned dataset exported as `Cleaned_Global_Superstore.csv`

---

## Result

The dataset was successfully cleaned and prepared for further analysis.

---

## License

This project is for educational and internship purposes only.
