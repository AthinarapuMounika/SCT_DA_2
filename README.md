# SCT_DA_2
# Task 02 — Data Cleaning and Preparation

An end-to-end data cleaning and preprocessing workflow using Python and Pandas to prepare a Superstore dataset for analysis by handling missing values, removing duplicate records, converting data types, and exporting cleaned data.

# Objective

Prepare the dataset for further analysis by performing:

Identify and handle missing values
Remove duplicate rows
Convert string columns into appropriate data types
Clean and preprocess raw data
Export cleaned dataset into a new CSV file

# Dataset

Source: Sample Superstore Dataset

Property	Details
File	samplesuperstore.csv
Rows	Dataset records
Key columns	Order Date, Ship Date, Sales, Profit, Category, Region

Dataset was loaded into Google Colab using the Pandas library.

# Project Structure
SCT_DA_2.ipynb                     # Main notebook
samplesuperstore.csv              # Raw dataset
Cleaned_Global_Superstore.csv     # Cleaned dataset
README.md                         # Project documentation
Requirements

# Install dependencies:

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

# Analysis Steps
Step	Description
1	Import Pandas library
2	Load dataset
3	Display first 5 rows
4	Explore dataset information
5	Identify missing values
6	Handle missing values
7	Remove duplicate rows
8	Convert Order Date and Ship Date into datetime
9	Export cleaned dataset

# Code Used
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
No missing values were found in the dataset.
Duplicate records were handled successfully.
Date columns were converted into datetime format.
Dataset preprocessing completed successfully.
Cleaned data exported as Cleaned_Global_Superstore.csv.

# Result

The dataset was successfully cleaned and prepared for further analysis.

 # License

This project is for educational and internship purposes only.
