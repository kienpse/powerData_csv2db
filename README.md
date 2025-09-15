# Power Data CSV to Database

This project demonstrates how to work with large-scale power system data from the Australian National Electricity Market (NEM). It shows how to download raw dispatch SCADA data, convert it to a database format, and prepare it for efficient querying with Python and SQL.

## About the Data

- Source: [AEMO Data Archive](https://nemweb.com.au/Data_Archive/Wholesale_Electricity/MMSDM/2025/MMSDM_2025_07/MMSDM_Historical_Data_SQLLoader/DATA/)  
- Dataset: DISPATCH_UNIT_SCADA (SCADA telemetry of generating units and loads)  
- Time resolution: 5 minutes  
- Coverage: Every scheduled power unit/plant in the NEM  
- Size: A single month contains ~4 million rows of data, which is too large to handle efficiently as CSV

Because the data is so large, the raw CSV files are not included in this repository. You can download them directly from AEMO. Example (July 2025):  
https://nemweb.com.au/Data_Archive/Wholesale_Electricity/MMSDM/2025/MMSDM_2025_07/MMSDM_Historical_Data_SQLLoader/DATA/PUBLIC_ARCHIVE#DISPATCH_UNIT_SCADA#FILE01#202507010000.zip  

Alternatively, similar datasets can be found at [NEMweb](https://www.aemo.com.au/energy-systems/electricity/national-electricity-market-nem/data-nem/market-data-nemweb).

## Project Workflow

1. Download the raw CSV file from AEMO  
2. Bronze layer: Save the CSV into a SQLite database (`dispatch_unit_scada.db`) to preserve raw data in a structured form  
3. Silver layer: Extract key columns (`SETTLEMENTDATE`, `DUID`, `SCADAVALUE`) into a smaller database (`dispatch_unit_scada_silver.db`)  
4. (Planned) Data scrubbing and further SQL transformations to prepare a gold layer dataset suitable for analysis and visualisation

## Tools Used

- Python (pandas, sqlite3)  
- SQLite  
- Jupyter Notebook


## Purpose of This Project

This is a side project to demonstrate skills in:

- Handling large datasets (millions of rows)  
- Using Python and SQL for efficient storage and querying  
- Applying the bronze → silver → gold data engineering pattern


