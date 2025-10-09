# Power Data CSV to Database

This project walks through a simple, reproducible workflow for working with large-scale power system data from the Australian National Electricity Market (NEM). You will download raw dispatch SCADA data, convert it to a SQLite database, and be ready to analyse it with Python or SQL tools.

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

1. Download the raw CSV file from AEMO.
2. Use the notebook to load the CSV into a SQLite database (`dispatch_unit_scada.db`) so the raw data can be queried quickly.
3. Create a lighter-weight database (`dispatch_unit_scada_silver.db`) that keeps only the key columns (`SETTLEMENTDATE`, `DUID`, `SCADAVALUE`) for common analysis tasks.
4. Explore the database with SQL or Python—count rows, preview time periods, or filter for specific generating units.

## How to Run the Notebook

1. Place the downloaded CSV in the project root next to `prepareDB.ipynb`.
2. Start Jupyter Notebook or JupyterLab and open `prepareDB.ipynb`.
3. Update the `csv_file` variable in the first cell if your filename differs.
4. Run the cells in order to build the databases and inspect the results.
5. Open the resulting `.db` files with your favourite SQLite browser or query them directly from Python.

## Tools Used

- Python (pandas, sqlite3)  
- SQLite  
- Jupyter Notebook


## Purpose of This Project

This is a side project to demonstrate skills in:

- Handling large datasets (millions of rows)
- Using Python and SQL for efficient storage and querying
- Building a repeatable workflow for turning raw CSV files into a local database you can analyse


