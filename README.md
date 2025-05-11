# 🇮🇳 Indian Cities AQI ETL Pipeline using Databricks and PySpark

This project is an end-to-end ETL (Extract, Transform, Load) pipeline that collects real-time Air Quality Index (AQI) data from [data.gov.in](https://data.gov.in/), processes and transforms it using PySpark on Databricks, and stores it in a Delta Lake format for efficient querying and analytics.

---

## 🚀 Project Objective

To build a scalable and modular data pipeline that:
- Ingests AQI data from an open API
- Cleans and transforms the data using PySpark
- Removes duplicates and null values
- Merges new data with previously stored records
- Stores it in a Delta Lake format for future analysis

---

## 🔗 Data Source

- **API Endpoint**: [https://api.data.gov.in/resource/3b01bcb8-0b14-4abf-b6f2-c1bfd384ba69](https://api.data.gov.in/resource/3b01bcb8-0b14-4abf-b6f2-c1bfd384ba69)
- **API Provider**: Government of India Open Data Platform
- **API Key**: Required (registered on data.gov.in)

---

## ⚙️ Technologies Used

| Component     | Technology     |
|---------------|----------------|
| API Ingestion | Python + `requests` |
| Processing    | PySpark on Databricks |
| Storage       | Delta Lake on DBFS (Databricks File System) |
| Versioning    | Git + GitHub |

---

## 🧱 ETL Pipeline Structure

1. **Extract**  
   - Calls the API to fetch AQI data (100 records per request)
   - Converts API response into a PySpark DataFrame
   - Saves raw data to DBFS as CSV/JSON

2. **Transform**  
   - Fixes schema types (timestamp, location, pollutant levels)
   - Removes duplicates and rows with null values
   - Cleans malformed data

3. **Load**  
   - Reads the previously processed Delta Lake table
   - Merges new records (update existing + insert new)
   - Saves final processed data back to the Delta Lake

---

## 📁 Folder Structure

```plaintext
/aqi-etl-pipeline/
│
├── aqi_etl_notebook.dbc         # Databricks Notebook with the ETL code
├── README.md                    # Project documentation

Sample Output:

| Timestamp           | Location | PM2.5 | PM10 | NO2 | NH3 | SO2 | CO  | O3 |
| ------------------- | -------- | ----- | ---- | --- | --- | --- | --- | -- |
| 2025-05-07 15:00:00 | Mumbai   | 74.5  | 91   | 25  | 18  | 12  | 0.9 | 26 |


**📊 Future Improvements**

Automate pipeline using AWS Glue or Lambda and store processed data on S3
Add Airflow or GitHub Actions for scheduling
Will think about to Build a dashboard with Power BI


**👤 Author**

Name: Saurabh
GitHub: Saurabh9565
Role: Aspiring Data Engineer | Skilled in SQL, PySpark, ETL, AWS, Databricks

**📎 License**

This project is open-source and free to use for educational purposes.
