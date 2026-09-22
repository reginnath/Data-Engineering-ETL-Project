# Data-Engineering-ETL-Project
An ETL project using Pentaho to transform, validate, model, and prepare data for analytical and machine learning use.

## 1. Overview
- The pipeline uses local storage for the raw data, transformed data, star schema, and logging stages.
- The data consumption stage uses a MySQL database (via XAMPP).
- Pentaho transformations (`.ktr`) and jobs (`.kjb`) use absolute file paths (e.g., `C:\Users\...`). If the project is run on another computer, these paths must be updated accordingly.

## 2. How to Run
- Download the project input file, `GoogleAds_DataAnalytics_Sales_Uncleaned_pentaho.csv`, from the Google Drive link provided in the Expected Output section below.
- Place the downloaded CSV file inside the /raw_data folder.
- Make sure the following folder structure is available on your computer:
```text
├── raw_data
│   └── GoogleAds_DataAnalytics_Sales_Uncleaned_pentaho.csv
├── transformed_data
├── star_schema
├── logs
└── consumption_data
```
- Run the Pentaho job. The pipeline will automatically generate the required outputs, including transformed data, star schema tables, log files, and the consumption dataset.
- Note: Only the `/raw_data` folder needs to contain an input file. The other folders will be populated automatically when the Pentaho pipeline is executed.

## 3. Expected Output
- The Google Drive folder contains the input CSV file, example outputs from a completed pipeline run, including transformed CSV files, star schema tables, log files, and the ML-ready dataset.
- The ML-ready dataset is also provided in both CSV and SQL dump formats to demonstrate database integration.
- Google Drive: https://drive.google.com/drive/folders/1sz2VWS_r9UqumfBeuBvN4pW7P543XaAm?usp=sharing

## 4. Notes
- The absolute paths configured in Pentaho can be updated to match the folder location on the local computer.
- To inspect the results without running the pipeline, the output folders available on Google Drive can be used.

## 5. Data Consumption Stage (load to MySQL via XAMPP)
- Create a new MySQL database named ml_ready_dataset.
- Make sure the Pentaho database connection named `connectionOLAP` is configured to connect to this database:
   - Host: `localhost`
   - Port: `3306`
   - User: `root`
   - Password: empty or according to the local configuration
   - Database: `ml_ready_dataset`
- Run the Pentaho job. The `regression_dataset` table will be automatically created and populated with the processed data.
