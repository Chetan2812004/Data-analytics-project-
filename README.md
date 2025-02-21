📌 Project Title: Adani Enterprises Stock Analysis Using Excel, Power BI & Python

🔹 1. Introduction

📍 Objective:

The goal of this project is to analyze the stock performance of Adani Enterprises using historical stock market data. The analysis is performed using:

Excel for data cleaning and preprocessing.

Power BI for interactive visualizations.

Python (Google Colab) for deeper data analysis.


The project provides insights into stock price trends, trading volumes, moving averages, and key financial patterns.


---

🔹 2. Data Collection & Cleaning

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


---


#Import necessary libraries
import pandas as pd
import matplotlib.pyplot as plt

#Load Data from Google Drive
file_path = "/content/sample_data/cpproject.xlsx"  # Update with your actual file path

#Read the Excel file
df = pd.read_excel(file_path)

#Show the first few rows of data
df.head()

#Print actual column names to check for issues
print("Column Names:", df.columns)

#Trim spaces and rename the 'Date' column if necessary
df.rename(columns=lambda x: x.strip(), inplace=True)

#If the column is named differently (e.g., ' date '), rename it explicitly
possible_date_columns = [col for col in df.columns if 'date' in col.lower()]
if possible_date_columns:
    df.rename(columns={possible_date_columns[0]: 'Date'}, inplace=True)

#Convert 'Date' column to proper datetime format
df['Date'] = pd.to_datetime(df['Date'], errors='coerce')

#Sort data by Date
df = df.sort_values(by='Date')

#Display the first few rows to verify
df.head()

#Print actual column names to check for issues
print("Column Names:", df.columns)

#Trim spaces and rename the 'Date' column if necessary
df.rename(columns=lambda x: x.strip(), inplace=True)

#If the column is named differently (e.g., ' date '), rename it explicitly
possible_date_columns = [col for col in df.columns if 'date' in col.lower()]
if possible_date_columns:
    df.rename(columns={possible_date_columns[0]: 'Date'}, inplace=True)

#Convert 'Date' column to proper datetime format
df['Date'] = pd.to_datetime(df['Date'], errors='coerce')

#Sort data by Date
df = df.sort_values(by='Date')

#Display the first few rows to verify
df.head()

#Check if 'Close' column exists. If not, find the correct column name
if 'Close' not in df.columns:
    # Assuming closing price is in a column containing 'close' (case-insensitive)
    close_column = next((col for col in df.columns if 'close' in col.lower()), None)
    if close_column:
        # Rename the column to 'Close'
        df.rename(columns={close_column: 'Close'}, inplace=True)
    else:
        raise KeyError("Could not find a column representing closing price. Please check your data.")

🔹 4. Exploratory Data Analysis (EDA)

EDA helps to understand trends, patterns, and relationships in the dataset.

📍 1. Stock Price Trend Over Time

#Plot the stock closing price trend

plt.figure(figsize=(12, 6))
plt.plot(df['Date'], df['Close'], label='Closing Price', color='blue')
plt.xlabel('Date')
plt.ylabel('Stock Price (INR)')
plt.title('Adani Enterprises Stock Closing Price Trend')
plt.legend()
plt.grid()
plt.show()


#Check for volume column name (case-insensitive)

volume_column = next((col for col in df.columns if 'volume' in col.lower()), None)

#If the volume column is found, rename it to 'Volume'
if volume_column:

    df.rename(columns={volume_column: 'Volume'}, inplace=True)
else:
    raise KeyError("Could not find a column representing volume. Please check your data.")

📍 2. Trading Volume Analysis

plt.figure(figsize=(12, 6))
plt.bar(df['Date'], df['Volume'], color='purple', label='Trading Volume')  # Now use 'Volume'
plt.xlabel('Date')
plt.ylabel('Volume')
plt.title('Adani Enterprises Trading Volume')
plt.legend()
plt.show()

📍 3. Moving Averages (SMA & EMA)

#Calculate 20-day and 50-day moving averages
df['SMA_20'] = df['Close'].rolling(window=20).mean() # Now uses 'Close' if it exists or the renamed column
df['SMA_50'] = df['Close'].rolling(window=50).mean() # Now uses 'Close' if it exists or the renamed column

#Plot Moving Averages
plt.figure(figsize=(12, 6))
plt.plot(df['Date'], df['Close'], label="Closing Price", color='blue') #Now uses 'Close' if it exists or the renamed column
plt.plot(df['Date'], df['SMA_20'], label="SMA 20-day", color='green')
plt.plot(df['Date'], df['SMA_50'], label="SMA 50-day", color='red')
plt.xlabel('Date')
plt.ylabel('Stock Price (INR)')
plt.title('Moving Averages Analysis')
plt.legend()
plt.grid()
plt.show()

---

🔹 5. Power BI Dashboard (Visualization)

Key Reports & Charts Created in Power BI:
✅ Stock Price Trends - Interactive line charts.
✅ Trading Volume Trends - Bar charts for daily volumes.
✅ Moving Averages Analysis - SMA & EMA plotted for trend analysis.
✅ High-Low Price Volatility - Candlestick charts.
✅ Market Sentiment Analysis - Integration with news data.

Power BI allows users to interact with the data and make better investment decisions.


---

🔹 6. Conclusion & Key Findings

📈 Final Insights from the Analysis:
✅ Stock Performance: The stock showed both upward and downward trends.
✅ Trading Volume Trends: Sudden volume spikes were noticed, indicating market reactions to news or events.
✅ Moving Averages: The SMA 20-day & SMA 50-day crossovers indicate potential buy/sell opportunities.
✅ Power BI Dashboard: Provides quick & interactive insights into stock performance.

📌 Investment Recommendation: Investors should consider technical indicators & market conditions before making trading decisions.


---

🔹 7. Future Scope

🚀 Next Steps for Advanced Analysis:
🔹 Sentiment Analysis - Using news headlines & tweets to measure investor sentiment.
🔹 Machine Learning Prediction - Forecasting future stock prices using ML models.
🔹 Comparative Analysis - Comparing Adani Enterprises with other market leaders.


---

📌 Final Project Summary

✔ Data Cleaning: Done in Excel.
✔ Data Analysis: Performed using Python in Google Colab.
✔ Visualization: Created using Power BI.
✔ Findings: Identified trends, trading volume spikes, and moving average signals.
✔ Outcome: The analysis helps in market behavior understanding & investment strategies.


---








