## Car Owners Data Cleaning and Validation Script
Overview
This script processes a large dataset of car owners from China, focusing on cleaning, validating, and splitting the data into clean and garbage datasets. It uses chunk processing to handle large files efficiently, ensuring that only valid data is kept while any invalid or duplicate entries are separated into a garbage dataset.

## Purpose
Clean and validate a dataset of car owners.
Handle translations of column headers from Chinese to English.
Process the data in manageable chunks to optimize memory usage.
Output clean data and garbage data separately for further analysis.

## Libraries Used
pandas: For data manipulation and processing.
re: For regular expression operations, mainly used in data validation.
logging: To log the progress and errors during data processing.
os: To handle file paths and check for the existence of files.

## Features
Chunk Processing: 
Reads the data in chunks of 250,000 rows, allowing efficient processing of large datasets without memory overload.
Validation Functions:

## Email Validation: 
Checks for valid email formats and sets any variations of "no email" as NaN.

## Mobile Number Validation: 
Validates that mobile numbers are numeric and have a reasonable length (7-15 digits).

## VIN and ID Validation: 
Checks if Vehicle Identification Numbers (VIN) and ID numbers are alphanumeric.

## Data Cleaning:
Translates Chinese column headers into English.
Converts column names to lowercase and replaces spaces with underscores for consistency.
Removes specified columns from clean data but retains them in garbage data.
Merges address-related fields into a single full_address column.
Checks for duplicates using VIN and ID numbers.
Separates valid data into clean datasets and invalid data or duplicates into garbage datasets.

## Final Data Concatenation:
Merges all clean data chunks into a final cleaned dataset.
Performs a final duplicate check on the entire cleaned dataset.
Saves duplicates into a separate file.
Combines all garbage data chunks into a final garbage dataset.

## Configuration
Chunk Size: 250,000 rows per chunk.
Columns Removed from Clean Data: 
Includes fields like gender, industry, monthly_salary, marital_status, education, brand, car_series, car_model, configuration, engine_number, unnamed:_21, and color.





 
