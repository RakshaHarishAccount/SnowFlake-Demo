# SnowFlake-Demo

This repository contains the data (CSV files) and SQL/Python code that will be used for ETL pipeline demo in snowflake.
1. Folder "Source CSVs" contains the input source files that can be stored locally or on Cloud storage like AWS S3, Azure ADLS, etc. In this demo, we are manually uploading the CSV source file to the internal stage in snowflake. This can ben done via the snowflake UI or by using the snowsql CLI terminal.
2. Folder "SQLs" contains the SQL codes in sequence to perform end-to-end ETL demo on snowflake.
3. Folder "Output Snowflake tables" contains the outputs of the SQL code.
