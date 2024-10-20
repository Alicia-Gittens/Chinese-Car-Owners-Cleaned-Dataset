# Data Cleaning and Validation Script for Car Owners Dataset
Overview
This Python script is designed to process a large dataset of car owners, specifically targeting data from China. The script performs several operations to clean and validate the data, ensuring its quality and usability for further analysis. The key functionalities include:

# Column Translation: Translates column headers from Chinese to English.
# Data Cleaning: Cleans and validates critical data fields like emails, mobile numbers, VINs, and ID numbers.
# Address Merging: Combines multiple address-related columns into a single full_address field.
# Duplicate Detection: Identifies and handles duplicate records based on VIN and ID numbers.
# Data Separation: Segregates the dataset into clean and garbage (invalid or duplicate) data.
# Chunk Processing: Processes the data in chunks to efficiently handle large files.
# Prerequisites
Python 3.x
# Required Python Libraries:
pandas
re (Regular Expressions)
logging
os
# You can install the required libraries using the following command:
pip install pandas
# Script Structure
Configurations
translated_headers: A dictionary that maps Chinese column names to their English equivalents.
columns_to_remove_in_clean: A list of columns to remove from the clean dataset (but keep in the garbage dataset).
chunk_size: The number of rows to process per chunk (default is 250000).
columns_to_clean: Columns that require cleaning using regular expressions.
pattern: A regular expression pattern used for cleaning data.
# Functions
is_valid_email(email): Validates the format of an email address.
is_valid_mobile(mobile): Checks if the mobile number is numeric and has a reasonable length (7 to 15 digits).
is_alphanumeric(value): Checks if a value contains only alphanumeric characters.
safe_process(func, *args, **kwargs): Wraps a function in a try-except block for error handling.
process_data(file_path, clean_file_prefix, garbage_file_prefix): The main function that processes the dataset.
# Usage
1. Set Input and Output Paths
At the end of the script, specify the paths for your input file and the prefixes for the output files:
# Example usage
input_file = r"path_to_your_input_file.csv"
clean_file_prefix = r"path_to_your_clean_data_output_prefix"
garbage_file_prefix = r"path_to_your_garbage_data_output_prefix"

# Process the data and save chunks
process_data(input_file, clean_file_prefix, garbage_file_prefix)
Replace the placeholders with your actual file paths:

input_file: The path to your input CSV file containing the car owners dataset.
clean_file_prefix: The prefix for your clean data output files.
garbage_file_prefix: The prefix for your garbage data output files.
2. Run the Script
Execute the script using the command line:
python your_script_name.py
Ensure that you have navigated to the directory containing the script or provide the full path to the script.

# Output
Clean Data Files: CSV files containing cleaned and validated data. The files are named with the specified clean_file_prefix, including chunk numbers and a final consolidated file.
Garbage Data Files: CSV files containing invalid or duplicate data. The files are named with the specified garbage_file_prefix, including chunk numbers and a final consolidated file.
Logs: The script generates log messages detailing the processing steps, any errors encountered, and statistics like the number of garbage rows per chunk.
# Detailed Process
1. Data Loading and Chunking
The script reads the input CSV file in chunks, as defined by chunk_size, to handle large datasets without exhausting memory resources.
2. Column Translation
Column headers are translated from Chinese to English using the translated_headers dictionary.
All column names are converted to lowercase and spaces are replaced with underscores for consistency.
3. Data Cleaning and Validation
Duplicate Detection: Identifies duplicates based on VIN and ID Number from the original data.
# Email Cleaning:
Converts email addresses to lowercase.
Replaces invalid entries like 'no email' with NaN.
Validates email format using regular expressions.
# Address Merging:
Merges address, city, province, and postal_code into a single full_address field.
Drops the original address columns from the clean data but retains them in the garbage data.
# Alphanumeric Validation:
Checks if VIN and ID Number contain only alphanumeric characters.
Mobile Number Validation:
Ensures that mobile_phone contains only digits and is of a reasonable length.
# Date of Birth Validation:
Validates that date_of_birth is a valid date.
Formats valid dates as mm/dd/yyyy in the clean data.
# Data Separation
Valid Rows: Rows that pass all validation checks are included in the clean dataset.
# Invalid Rows:
Rows failing any validation check.
Duplicate rows based on VIN and ID Number.
These rows are included in the garbage dataset.
# Saving Results
The script saves each processed chunk to separate CSV files for both clean and garbage data.
After processing all chunks, it concatenates the chunk files into final consolidated datasets for both clean and garbage data.
Duplicate entries in the final clean dataset are further identified and separated.
Customization
# Adjusting Chunk Size
Modify the chunk_size variable to change the number of rows processed per chunk, which can help optimize performance based on your system's capabilities.
# Modifying Validation Rules
The validation functions (is_valid_email, is_valid_mobile, etc.) can be customized to fit different data formats or validation requirements.
# Updating Column Translations
If your dataset contains additional columns or uses different Chinese column names, update the translated_headers dictionary accordingly.
# Changing Columns to Remove
Adjust the columns_to_remove_in_clean list to specify which columns should be excluded from the clean dataset.
# Error Handling
The script uses Python's logging module to record errors and important information.
The safe_process function ensures that errors in individual operations do not halt the entire script.
# Notes
Data Integrity: Always back up your data before processing to prevent accidental data loss.
Input File Format: Ensure that the input CSV file uses the correct delimiter (default is a comma).
Dependencies: All required libraries must be installed for the script to run successfully.
Logging: Check the logs for detailed information about the data processing and any issues encountered.
# License
This project is open-source and available under the MIT License.

Contact
For questions or feedback, please contact the script author or maintainers.

This README was generated to provide a comprehensive guide on how to use and understand the data cleaning and validation script. It covers all aspects from setup to execution, aiming to assist users in effectively utilizing the script for their data processing needs.






