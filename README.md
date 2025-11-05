# Stock-Price-Prediction-Analytics

### Introduction
This project focuses on building a Finance Data Analytics system utilizing the yfinance API
for extracting comprehensive historical stock market data including open, high, low, close
prices, and trading volumes. Leveraging this rich dataset enables conducting various financial
analyses such as stock price prediction, trend and volatility analysis, technical indicator
evaluation, and portfolio optimization. By integrating automated data collection through
yfinance with cloud-based storage and processing in Snowflake, the system provides an
efficient pipeline for storing, and analyzing stock market data.

### Problem Statement
The objective of this project is to develop a stock price prediction and analysis system
focused on forecasting the stock prices of key companies such as NVIDIA (NVDA) and
TESLA (TSLA) over the next seven or more days by leveraging historical stock price data.
Accurate forecasting of stock prices is invaluable to investors for informed decision-making,
effective risk management, and understanding market trends.
To support this goal, the system utilizes a Snowflake database to store large volumes of daily
stock price data across multiple companies. Data pipelines, orchestrated by Airflow, automate
the extraction, transformation, and loading (ETL) of this stock data. These pipelines ensure
the data remains fresh, consistent, and ready for downstream forecasting processes.

### Solution Requirements
#### Functional Requirements:
 Extract last 180 days of stock prices for selected companies using yfinance API.
 Load the data into Snowflake tables with proper schema.
 Automate data collection with Airflow DAGs running daily.
 Implement ML forecasting pipelines also as Airflow DAGs.
 Schedule forecasting after the loading pipeline completes.
#### Non-functional Requirements:
 Pipeline idempotency ensures data loads can be re-run safely.
 Secure management of credentials (Snowflake, yfinance API).
 Scalability to add more stock symbols.

#### Functional Analysis
The proposed system comprises several interconnected components, each serving a critical
role in achieving accurate stock price forecasting through automation and scalable processing.

### Component Overview
Data Extraction:
Python scripts leverage the yfinance API to fetch historical stock data, including open, high,
low, close, and volume metrics for multiple companies such as NVDA and TSLA.
Data Loading:
The Snowflake Python connector inserts the extracted data into structured database tables.
This process ensures data integrity through SQL transaction management, with error handling
to prevent inconsistencies.
Data Pipeline Automation:
Apache Airflow orchestrates daily workflows to automate the ETL (Extract, Transform, Load)
processes. Connections and credentials are securely managed via Airflow's connection
settings, ensuring seamless and reliable execution of data pipelines.
ML Forecasting Module:
A dedicated Airflow DAG triggers machine learning models which utilize the stored
historical data. The models, trained on the data, generate forecasts of the upcoming 7+ days,
storing predictions in a separate Snowflake table.

#### Union and Presentation:
A final SQL step unions actual historical data with forecasted prices to generate a
comprehensive, unified view. This enables efficient analysis and decision-making based on
combined historical and predictive insights.

#### Database and Data Pipeline Interaction
 Extracted data is transformed into a predefined schema with fields such as symbol, date,
open, close, high, low, and volume.
 The data pipeline sequences ensure that the forecasting models only run after successful
data loading, maintaining data consistency.
 SQL transactions with try/except error handling prevent data corruption and ensure
rollback on failures, maintaining system robustness.
This integrated architecture supports scalable, automated, and accurate stock market analysis,
providing a solid foundation for predictive analytics and strategic investment insights.

### Conclusion
This project developed an automated stock price prediction system using Snowflake and
Airflow to streamline financial data analytics. By leveraging the yfinance API, historical
stock data for selected companies was collected daily and stored in Snowflake through an
Airflow ETL pipeline. A separate forecasting pipeline predicted stock prices for the next
seven days, ensuring continuous data updates and insights. The integration of data ingestion,
transformation, and forecasting in a single automated workflow highlights the efficiency of
combining Snowflake’s data capabilities with Airflow’s orchestration power. Overall, this
system provides a scalable, reliable framework for real-time financial forecasting and
analysis.
----------------------------------
