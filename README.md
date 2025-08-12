# etl-customer-shopping-data

This project demonstrates a simple ETL (Extract, Transform, Load) pipeline using Python to process customer shopping data. The data is extracted from a public Kaggle dataset, loaded into a Google Sheet, and then transformed using Python(Pandas) and loaded into Google BigQuery for analysis.


## Project Overview
The goal of this project is to showcase a fundamental data engineering workflow. The pipeline performs the following steps:

- **Extract:** Reads data from a Google Sheet.
- **Transform:** Cleans columns in a pandas DataFrame.
- **Load:** Pushes the processed data into a BigQuery table.


## Dataset
The dataset used in this project is the **Customer Shopping Dataset** from Kaggle, available **[here](https://www.kaggle.com/datasets/mehmettahiraslan/customer-shopping-dataset)**


## Prerequisites
To run this project, you will need to set up the following:

1. **Google Cloud Project:**  
   A Google Cloud project with the Google Sheets API and BigQuery API enabled.

2. **Service Account:**  
   A service account with the necessary permissions to access Google Sheets and BigQuery. You'll need to create a JSON key file for this account.

3. **Google Sheet:**  
   A Google Sheet containing the customer shopping data. The service account's email must be shared with this sheet, granting it editor access.

4. **Python Environment:**  
   An environment with the following libraries installed:
   - `google-api-python-client`
   - `gspread`
   - `pandas`
   - `google-cloud-bigquery`
   - `pandas-gbq`

## ETL Pipeline Steps
The Python script automates the entire ETL process:

### **Step 1: Extraction (E)**
- Connects to the specified **Google Sheet** using the service account credentials.
- Accesses the `'data'` worksheet.
- Reads all records into a **pandas DataFrame**.

### **Step 2: Transformation (T)**
- Performs minor transformations, such as renaming DataFrame columns to more descriptive, `snake_case` names.
- Prepares the data so it is more suitable for use in database tables.

### **Step 3: Loading (L)**
- Loads the transformed DataFrame into a **BigQuery** table.
- Uses `pandas_gbq` to push the data, specifying:
  - Google Cloud **Project ID**
  - **Dataset** name
  - **Table** name
- Uses the parameter `if_exists='replace'` to ensure the table is overwritten with fresh data each run.

## Summary
This project demonstrates the core principles of building an ETL pipeline using Python, Google Sheets, and Google BigQuery.  
The process ensures that raw customer shopping data can be collected, cleaned, and made available for analysis in a structured and automated way.
