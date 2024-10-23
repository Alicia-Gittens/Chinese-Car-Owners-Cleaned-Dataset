# Car Owners Data Cleaning Script

This Python script is designed to clean, validate, and process a large dataset of car owners, specifically for a dataset containing foreign language headers. It translates the headers into English, processes the data in chunks for efficiency, and separates the records into clean and garbage datasets based on various validation rules.

## Table of Contents
- [Overview]
- [Features]
- [Prerequisites]
- [Installation]
- [Usage]
- [Configuration]
- [File Structure]
- [Output]
- [Contributing]
- [License]

## Overview
The script processes a large dataset of car owners in chunks of 250,000 rows to manage memory efficiently. It cleans and validates the data, saving the results in separate files for further analysis. The script translates Chinese headers into English, removes unnecessary columns, and validates fields such as email, mobile phone, and IDs.

## Features
- **Data Translation:** Translates foreign language headers into English for easier processing.
- **Data Cleaning:** Validates email addresses, phone numbers, VINs, and ID numbers.
- **Data Validation:** Checks for alphanumeric values, duplicates, and properly formatted dates.
- **Data Transformation:** Merges address components into a single 'full_address' field.
- **Chunk Processing:** Processes the data in chunks of 250,000 rows for better memory management.
- **Logging:** Logs the progress and any errors encountered during data processing.
- **Customizable:** Easily adaptable for different datasets by changing configuration parameters.

## Prerequisites
- Python 3.12 or higher
- Required Python libraries:
  - `pandas`
  - `re`
  - `logging`
  - `os`

## Install the required dependencies:
pip install pandas
Ensure that your dataset file is accessible on your local machine.

## Usage
Update the file paths in the script:

input_file = 'Input file path'
clean_file_prefix = 'Input file path'
garbage_file_prefix = 'Input file path'

## Run the script:
python car_owners_data_cleaning.py

The script will process the dataset, saving cleaned and garbage records into separate files.

## Configuration
translated_headers: Translates Chinese headers into English. Adjust if different translations are needed.
columns_to_remove_in_clean: Specifies which columns to drop from the clean data but keep in the garbage data.
chunk_size: Defines the size of data chunks to process at a time (default is 250,000 rows).

## translated_headers: Translates Chinese headers into English. Adjust if different translations are needed.
columns_to_remove_in_clean: Specifies which columns to drop from the clean data but keep in the garbage data.
chunk_size: Defines the size of data chunks to process at a time (default is 250,000 rows).
## File Structure
car_owners_data_cleaning.py: The main script for data cleaning and validation.
Cleaned Data Files: Processed data saved as Clean_China_chunk_X.csv for each chunk.
Garbage Data Files: Invalid data saved as Garbage_China_chunk_X.csv for each chunk.
Final Output Files: Merged final cleaned and garbage datasets saved as Clean_China_final.csv and Garbage_China_final.csv.
Output

## The script generates the following outputs:
Clean Data: Records with valid fields, saved in multiple chunk files and a final merged file.
Garbage Data: Records with invalid fields or duplicates, saved in chunk files and a final merged file.
Duplicates Report: Duplicates are identified in the final cleaned dataset and saved separately if any exist.
Contributing
Feel free to open issues or submit pull requests for improvements or bug fixes. Contributions are welcome!

## License
This project is licensed under the MIT License. See the LICENSE file for more details.

## This `README.md` explains the script’s functionality, setup instructions, and configuration options while giving an overview of its features and outputs. It’s structured to help users understand how to use and adapt the script for their needs.



