# Formula 1 Race Data Analysis

## Project Overview
This project focuses on analyzing Formula 1 race data using Azure Cloud Services. The primary goal was to optimize ETL pipelines for efficient data processing and develop interactive dashboards to gain insights into race metrics. We also implemented Unity Catalog for robust data governance, ensuring secure and well-managed access to the datasets.

## Technologies Used
- **Azure Data Factory (ADF):** Used for orchestration of ETL pipelines.
- **Azure Databricks:** Leveraged for data transformation using PySpark and Delta Lake.
- **Azure Data Lake Gen 2:** Managed and processed race data efficiently.
- **Power BI:** Created interactive dashboards for data visualization.
- **Azure Key Vault:** Ensured secure storage of connection secrets.
- **Unity Catalog:** Implemented for data governance, managing access and ensuring data security.

## Project Structure

### Set-Up
- **set-up/mount_adls_storage.py:** Script to mount Azure Data Lake Storage (ADLS) for seamless access to data during the ingestion and processing phases.

### Raw Data Ingestion
- **raw/1.create_raw_tables.sql:** SQL script to create raw tables in the database, serving as the initial staging area for ingested data before processing.

### Data Ingestion
- **ingestion/0.ingest_all_files.py:** Script to ingest all necessary data files into the Azure Data Lake.
- **ingestion/1.ingest_circuits_file.py:** Script for ingesting the circuits data file.
- **ingestion/2.ingest_races_file.py:** Script for ingesting the races data file.
- **ingestion/3.ingest_constructors_file.py:** Script for ingesting the constructors data file.
- **ingestion/4.ingest_drivers_file.py:** Script for ingesting the drivers data file.
- **ingestion/5.ingest_results_file.py:** Script for ingesting the race results data file.
- **ingestion/6.ingest_pit_stops_file.py:** Script for ingesting the pit stops data file.
- **ingestion/7.ingest_lap_times_file.py:** Script for ingesting the lap times data file.
- **ingestion/8.ingest_qualifying_file.py:** Script for ingesting the qualifying data file.
- **ingestion/9.create_processed_database.sql:** SQL script to create the processed database for further analysis.

### Data Transformation
- **trans/0.create_presentation_database.sql:** SQL script to create the presentation layer database, where processed data is stored for final analysis and visualization.
- **trans/2.driver_standings.py:** Script to calculate and process driver standings based on race results.
- **trans/3.constructor_standings.py:** Script to calculate and process constructor standings.
- **trans/4.calculated_race_results.py:** Script to compute and finalize race results for further analysis.

### Data Analysis
- **analysis/1.find_dominant_drivers.sql:** SQL script to identify the most dominant drivers based on race results.
- **analysis/2.find_dominant_teams.sql:** SQL script to determine the most dominant teams in Formula 1.
- **analysis/3.viz_dominant_drivers.sql:** SQL script to create visualizations for the dominant drivers.
- **analysis/4.viz_dominant_teams.sql:** SQL script to create visualizations for the dominant teams.

### Utility Scripts
- **utils/1.prepare_for_incremental_load.sql:** SQL script to prepare the database for incremental data loads, ensuring that only new or updated data is processed in subsequent runs.

### Common Functions and Configuration
- **includes/common_functions.py:** Contains utility functions that are commonly used across various scripts in the project.
- **includes/configuration.py:** Configuration settings for environment variables and other project-specific parameters.

## How to Run

1. **Set Up Azure Environment:**
   - Clone the repository.
   - Run the `mount_adls_storage.py` script in the `set-up` folder to mount Azure Data Lake Storage (ADLS).

2. **Raw Data Ingestion:**
   - Execute the SQL script in the `raw` folder to create raw tables in the database.

3. **Data Ingestion:**
   - Use the scripts in the `ingestion` folder to load all relevant data files into the Azure Data Lake.

4. **Data Transformation:**
   - Execute the SQL and Python scripts in the `trans` folder to process the data and generate the necessary standings and race results.

5. **Data Analysis:**
   - Run the SQL scripts in the `analysis` folder to analyze dominant drivers and teams.
   - Use the visualization scripts to create insightful dashboards.

6. **Utility Scripts:**
   - If you plan to update the data periodically, run the `prepare_for_incremental_load.sql` script in the `utils` folder.

7. **Visualization:**
   - Use Power BI to create interactive dashboards using the processed data for race metrics and insights.

## Conclusion
This project demonstrates the use of Azure Cloud Services for managing and analyzing large datasets efficiently. By optimizing ETL pipelines, implementing Unity Catalog for data governance, and creating insightful visualizations, the project provides a comprehensive approach to Formula 1 race data analysis.
