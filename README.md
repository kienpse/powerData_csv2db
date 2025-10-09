
# Power Data CSV to Parquet

This project shows how to convert large-scale NEM power system SCADA data from CSV to Parquet for fast, efficient analysis in Python.

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
2. Use the notebook to load the CSV and save it as a Parquet file (`dispatch_unit_scada.parquet`) for fast, efficient analysis.
3. Optionally, create a filtered Parquet file with only the key columns (`SETTLEMENTDATE`, `DUID`, `SCADAVALUE`) for common analysis tasks.
4. Explore the Parquet data with Python (pandas, pyarrow)—count rows, preview time periods, or filter for specific generating units.


## How to Run the Notebook

1. Place the downloaded CSV in the project root next to `prepareDB.ipynb`.
2. Start Jupyter Notebook or JupyterLab and open `prepareDB.ipynb`.
3. Update the `csv_file` variable in the first cell if your filename differs.
4. Run the cells in order to convert the CSV to Parquet and inspect the results.
5. Analyse the resulting `.parquet` files directly in Python using pandas or pyarrow.



