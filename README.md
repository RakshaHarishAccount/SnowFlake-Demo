# SnowFlake-Demo

This repository contains the data (CSV files) and SQL/Python code that will be used for ETL pipeline demo in snowflake.
1. Folder "Source CSVs" contains the input source files that can be stored locally or on Cloud storage like AWS S3, Azure ADLS, etc. In this demo, we are manually uploading the CSV source file to the internal stage in snowflake. This can ben done via the snowflake UI or by using the snowsql CLI terminal.
2. Folder "SQLs" contains the SQL codes in sequence to perform end-to-end ETL demo on snowflake.
3. Folder "Output Snowflake tables" contains the outputs of the SQL code.

## Steps for SQL Demo Implementation

1. In snowflake, create the data warehouse called "etl_wh" using the SQL "1. Warehouse & DB Creation.sql". In this warehouse create the "nyc_taxi_demo_db" database.
2. Create 3 schemas in the "nyc_taxi_demo_db" database - (a) raw_layer (b) staging_layer (c) serving_layer
3. Create an internal stage called "github_stage" in the default "public" schema of the "nyc_taxi_demo_db" database. Assign access controls and roles to different users by executing the SQL "2. Defining Access Controls & Roles.sql"
4. Manually upload the CSV source file in the "1.Source CSVs" folder to the "github_stage" via the snowflake UI or the snowsql CLI terminal. Use the CSV in the stage to load the initial source table in the raw_layer of the database. Execute the SQL "3. SnowPipe to Raw Layer.sql" to implement this step. (Optional - Place the CSVs in S3 or ADLS and create a SnowPipe in Snowflake to auto-ingest the cloud files). 
5. To perform transforms on the raw table and land it as a transformed data table in the staging_layer, execute the SQL "4. Staging Layer - Transformations.sql"
6. Finally, to build the serving_layer table from the staging_layer table, execute the SQL "5. Serving Layer.sql"
7. Optional - To check the account billing history incurred due to ETL implementation, execute  the SQL "6. Billing History Tracker.sql"; To implement the time travel scenario on Snowflake, execute the SQL "7. Time-travel Scenario.sql".

## Steps for Python-Snowpark Demo Implementation

1. Set the role as "Account Admin" for the snowflake warehouse "etl_wh"
2. Select the database as "nyc_taxi_demo_db" with the relevant schema
3. Instead of using a CSV file as a source of data in the internal stage "github_stage", a dataframe is created and used as source data in the Python implementation files.
4. Assumption : The schemas and the database are already created during the SQL demo execution
5. Run either of the 2 Python files to execute the ETL demo in snowflake using Python+SnowPark framework

