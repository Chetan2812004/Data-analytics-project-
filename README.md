# Data-analytics-project-
📌 #Adani Enterprises Stock Analysis Using Python, Excel & Power BI  
🔹 1. Introduction

 #📍 Objective:

The goal of this project is to analyze the stock performance of Adani Enterprises using historical stock market data. The analysis is performed using:

Excel for data cleaning and preprocessing.

Power BI for interactive visualizations.

Python (Google Colab) for deeper data analysis.


The project provides insights into stock price trends, trading volumes, moving averages, and key financial patterns.


---

#🔹 2. Data Collection & Cleaning

📍 Data Source

The dataset used in this project consists of historical stock price data for Adani Enterprises, collected from:
✅ NSE (National Stock Exchange) - https://www.nseindia.com
✅ BSE (Bombay Stock Exchange) - https://www.bseindia.com
✅ Yahoo Finance - https://finance.yahoo.com

📍 Features in the Dataset

The dataset contains the following columns:
| Column Name | Description | |-------------|-------------| | Date | The trading date | | Open | Opening price of the stock | | High | Highest price of the stock on that day | | Low | Lowest price of the stock on that day | | Close | Closing price of the stock | | Adj Close | Adjusted closing price | | Volume | Number of shares traded |

📍 Data Cleaning in Excel

Before analysis, the dataset was cleaned using Excel, with the following steps:
✔ Handled missing values by filling or removing incomplete data.
✔ Removed duplicate records to avoid inconsistencies.
✔ Ensured correct date format for accurate time-series analysis.
✔ Checked for outliers using filtering techniques.
✔ Saved the cleaned dataset as an Excel file (cleaned_adani_stock.xlsx).



📍 Step 1: Mount Google Drive & Load Data

# Mount Google Drive
from google.colab import drive
drive.mount('/content/drive')

# Import necessary libraries
import pandas as pd
import matplotlib.pyplot as plt

# Load cleaned Excel file
file_path = "/content/drive/My Drive/cleaned_adani_stock.xlsx"  # Update with your actual file path
df = pd.read_excel(file_path)

# Display first few rows
df.head()


---


