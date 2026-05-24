# SCT_DS_2  
# Task 02 — Data Cleaning and Preparation

An end-to-end data cleaning and preprocessing workflow using Python and Pandas to prepare a Superstore dataset for analysis by handling missing values, removing duplicate records, converting data types, and exporting cleaned data.

---

## Objective

Prepare the dataset for further analysis by performing:

- Identify and handle missing values  
- Remove duplicate rows  
- Convert string columns into appropriate data types  
- Clean and preprocess raw data  
- Export cleaned dataset into a new CSV file  

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

SCT_DS_2.ipynb  
samplesuperstore.csv  
Cleaned_Global_Superstore.csv  
README.md  

---

## Requirements

Install dependency:

```bash
pip install pandas

Library	Purpose
pandas	Data loading and preprocessing
# How to Run
Open Google Colab or Jupyter Notebook
Upload samplesuperstore.csv
Import required libraries
Run all notebook cells sequentially
Perform data cleaning operations
Export cleaned dataset
Analysis Steps
Step	Description
1	Import Pandas library
2	Load dataset
3	Display first 5 rows
4	Check missing values
5	Handle missing values
6	Remove duplicate rows
7	Convert Order Date and Ship Date into datetime
8	Export cleaned dataset
# Code
import pandas as pd

df = pd.read_csv("/content/samplesuperstore.csv")

print(df.head())

print(df.isnull().sum())

numeric_cols = df.select_dtypes(include=['int64','float64']).columns

for col in numeric_cols:
    df[col] = df[col].fillna(df[col].mean())

categorical_cols = df.select_dtypes(include=['object']).columns

for col in categorical_cols:
    df[col] = df[col].fillna(df[col].mode()[0])

df.drop_duplicates(inplace=True)

df['Order Date'] = pd.to_datetime(df['Order Date'], errors='coerce')

df['Ship Date'] = pd.to_datetime(df['Ship Date'], errors='coerce')

df.to_csv("Cleaned_Global_Superstore.csv", index=False)

print("Cleaning completed successfully")
# Key Findings
No missing values were found in the dataset
Duplicate rows were removed successfully
Date columns converted into datetime format
Dataset cleaned successfully
Cleaned file exported as Cleaned_Global_Superstore.csv
Result

The dataset was successfully cleaned and prepared for future analysis.

# License

This project is for educational and internship purposes only.


This is GitHub-ready and matches the style of your Task 04 README.
