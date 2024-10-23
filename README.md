# Car Owners Data Cleaning Script

This Python script is designed to clean, validate, and process a large dataset of car owners, specifically for a dataset containing foreign language headers. It translates the headers into English, processes the data in chunks for efficiency, and separates the records into clean and garbage datasets based on various validation rules.

## Imports
pandas
re
logging
os

## Setup and Configuration:
	○ Logging Configuration: Logs messages with timestamps to track the processing progress and errors.
	○ Translation of Headers: Translates foreign language headers into English for consistency.
	○ Configuration:
		§ Columns to remove from clean data but keep in garbage data.
		§ Expected columns list for easier reference.
		§ Chunk size set to 250,000 rows for optimized processing.

## Validation Functions:
	○ is_valid_email: Checks if an email address has a valid format.
	○ is_valid_mobile: Validates that the mobile number is numeric and of a reasonable length (7-15 digits).
	○ is_alphanumeric: Checks if a given value contains only alphanumeric characters (used for VIN and ID validation).
	○ safe_process: Wraps functions in a try-except block for safe execution, logging errors without stopping the process.

## Data Processing:
	○ Reads Data in Chunks: Processes data in chunks for memory efficiency.
	○ Translates Column Names: Converts Chinese headers to English and then converts them to lowercase with underscores.
	○ Removes Specified Columns: Drops specified columns from the clean data while retaining them in the garbage data.

## Data Cleaning and Validation:
	○ Check for Duplicates: Identifies duplicates using VIN and ID number from the original data.
	○ Email Cleaning: Converts emails to lowercase and replaces variations of "no email" with NaN.
	○ Email Validation: Adds a flag to indicate if an email is valid.
	○ Merge Address Fields: Merges 'address', 'city', 'province', and 'postal_code' into a single 'full_address' column.
	○ VIN and ID Validation: Checks if VIN and ID numbers are alphanumeric.
	○ Mobile and Date Validation: Checks if mobile numbers are valid and verifies that the date of birth is correctly formatted.
	○ Separates Clean and Garbage Data: Creates a clean dataset with valid rows and a garbage dataset with invalid rows or duplicates.

## Data Formatting and Saving:
	○ Date of Birth Formatting: Ensures 'date_of_birth' is formatted as mm/dd/yyyy in the clean data.
	○ Saves Clean and Garbage Data: Saves each processed chunk into separate clean and garbage CSV files.
	○ Logs Information: Logs details such as the number of garbage rows per chunk.

## Final Data Concatenation and Saving:
	○ Merges Cleaned Chunks: Concatenates all clean data chunks into a single DataFrame.
	○ Performs Final Duplicates Check: Identifies duplicates in the combined clean data.
	○ Saves Final Clean Data: Excludes duplicates and saves the final clean dataset to a CSV file.
	○ Saves Duplicates Separately: If any duplicates remain, saves them to a separate CSV file.
	○ Merges and Saves All Garbage Data: Combines all garbage chunks and saves them to a final garbage dataset.

## Example Usage:
	○ Defines input file path and prefixes for output clean and garbage files.
Calls process_data() function to start the ETL process with specified file paths and configurations





 
