# github-archive-DE
ETL pipeline using PySpark in Databricks/Azure
using https://www.gharchive.org/ data

- `bronze_layer` loads in the raw data from the ADLS container and finds ideal amount of partitions for each day of data and saves as parquet files for each day
- `silver_layer` completely flattens the data, removes completely null columns, and seperates the data into 14 seperate and partitioned parquet files by day based on event type
- `gold_layer` uses PySparkSQL to create parquet files of aggregated data from the silver layer that would be useful for business visualizations/analysis
