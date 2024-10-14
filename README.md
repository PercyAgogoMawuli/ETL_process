**Project Overview:**
This project implements an Extract, Transform, Load (ETL) pipeline for scraping, processing, and storing data about the largest banks in the world based on market capitalization. The pipeline is written in Python and leverages web scraping, data transformation, and database storage to automate data engineering tasks.

**Components:**

*Data Extraction:*

Scrapes data from the Wikipedia page listing the largest banks by market capitalization.
Extracted data includes the bank name and market capitalization in USD, which is then stored in a pandas DataFrame.
Data Transformation:

Converts the extracted market capitalization values from USD to other currencies (GBP, EUR, INR) using exchange rates from a CSV file.
The transformed values are added as new columns to the DataFrame and rounded to 2 decimal places.
Data Loading:

Saves the transformed data to both a CSV file and an SQLite database.
Executes SQL queries on the database to demonstrate basic data analysis and querying.

*File Overview:*

code_log.txt: Log file used to record the progress of various steps in the ETL pipeline.
Largest_banks_data.csv: CSV file containing the final processed and transformed data.
Banks.db: SQLite database storing the transformed data in a table called Largest_banks.
exchange_rate.csv: CSV file providing exchange rates for converting USD to other currencies (GBP, EUR, INR).

**Code Structure:**

*Libraries Imported:*

requests: To fetch the web page content.
pandas: To handle data in DataFrame format and for reading/writing CSV files.
sqlite3: To manage database storage and SQL queries.
BeautifulSoup: To parse the HTML content from the Wikipedia page.
numpy: To assist in numerical operations, particularly for rounding off values.
datetime: To record timestamps for logging.
Functions:

log_progress(message): Logs progress messages with timestamps to code_log.txt.

extract(url, table_attribs): Scrapes bank names and market capitalization data from the Wikipedia page, then stores this data in a pandas DataFrame.

transform(df, csv_path): Adds columns for market capitalization in GBP, EUR, and INR by converting from USD values using exchange rates provided in exchange_rate.csv.

load_to_csv(df, output_path): Saves the transformed DataFrame to a CSV file.

load_to_db(df, sql_connection, table_name): Loads the DataFrame into an SQLite database table.

run_query(query_statement, sql_connection): Runs SQL queries on the database and prints the results.

*Running the ETL Process:*

The ETL pipeline is executed in the following sequence:

Extract: Data is scraped from the Wikipedia page and stored in a pandas DataFrame.
Transform: The USD market capitalization is converted into GBP, EUR, and INR using exchange rates from exchange_rate.csv.
Load:
The transformed data is saved to a CSV file.
The data is also loaded into an SQLite database, and queries are run to analyze the data.
Querying: SQL queries demonstrate basic data retrieval and analysis, such as selecting all rows, calculating the average market capitalization in GBP, and retrieving the names of the top 5 banks.
SQL Queries Executed:
Retrieve all data from the Largest_banks table.
Calculate the average market capitalization in GBP for the largest banks.
Select the names of the top 5 largest banks.
Prerequisites:
Python 3.x

Libraries: requests, pandas, sqlite3, numpy, datetime, beautifulsoup4

**How to Use:**

Clone or download the repository.
Ensure that the exchange_rate.csv file contains the correct currency exchange rates.
Run the script to initiate the ETL process. It will:
Scrape the data from the Wikipedia page.
Perform currency conversion.
Save the results in both a CSV file and an SQLite database.
Review the log file (code_log.txt) to track the progress of the ETL operations.
