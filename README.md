# Xetra ETL Pipeline Project

This project implements an ETL (Extract, Transform, Load) pipeline for processing financial trading data from the Deutsche Börse Xetra dataset. The processed data is stored in AWS S3 in Parquet format for further analysis and reporting.

## 📌 Project Overview

The pipeline performs the following tasks:

* **Extract**: Downloads daily CSV files from a public S3 bucket (`deutsche-boerse-xetra-pds`) using `boto3`.
* **Transform**:

  * Filters data based on a provided start date.
  * Calculates daily metrics such as opening and closing prices, daily high/low, traded volume, and percentage change from the previous closing price.
  * Cleans and rounds numerical data.
* **Load**: Writes the transformed data as a Parquet file into a target S3 bucket (`xetra-1234`).

## 🧰 Tools & Technologies

* **Python 3**
* **Pandas**: for data manipulation
* **Boto3**: for interacting with AWS S3
* **Jupyter Notebook**: for development and documentation

## 📁 Input & Output

* **Input**: CSV files from the `deutsche-boerse-xetra-pds` S3 bucket.
* **Output**: A single Parquet file uploaded to the `xetra-1234` S3 bucket, named using the pattern:

  ```
  xetra_daily_report_YYYYMMDD_HHMMSS.parquet
  ```

## 🧮 Key Data Transformations

* Extraction of opening and closing prices using grouping and sorting.
* Calculation of:

  * `opening_price`
  * `closing_price`
  * `change_prev_closing_%`
  * `daily_traded_volumn`
* Data cleansing using rounding and dropping NaN values.

## 🚀 How to Run

1. Ensure AWS credentials are configured with access to the appropriate buckets.
2. Set the `arg_date` parameter in the script to the desired start date.
3. Run the notebook to execute the ETL flow.
4. The result will be available in the target S3 bucket in Parquet format.

## 🔐 Notes

* Requires permissions to read from `deutsche-boerse-xetra-pds` and write to `xetra-1234`.
* Execution assumes a local or cloud environment configured with `boto3` access.

## 🧑‍💻 Author

* Kim Xiang

