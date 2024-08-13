# Layoffs Data Cleaning Project

## Overview

This project focuses on cleaning and standardizing a dataset of layoffs. The dataset contains information about companies, their locations, industries, the number of employees laid off, and other related data. The goal of this project is to remove duplicates, standardize the data, handle null values, and remove unnecessary columns, resulting in a clean and reliable dataset.

## Project Steps

### 1. **Remove Duplicates**
   - Created a `layoffs_staging` table by copying the structure and data from the original `layoffs` table.
   - Used a Common Table Expression (CTE) to identify and remove duplicate records based on key fields like `company`, `location`, `industry`, `total_laid_off`, `percentage_laid_off`, `date`, `stage`, `country`, and `funds_raised_millions`.
   - Created a `row_num` field to identify duplicates and removed any records where `row_num` > 1.

### 2. **Standardize the Data**
   - **Company Names**: Removed leading and trailing spaces from company names.
   - **Industry Names**: Standardized the industry names (e.g., consolidating all variations of "Crypto" into a single standard name).
   - **Country Names**: Removed trailing periods from country names and standardized entries like "United States".
   - **Dates**: Converted the date field from text to a proper `DATE` data type using the `str_to_date` function.

### 3. **Handle Null Values or Blank Values**
   - Set blank `industry` fields to `NULL`.
   - Filled in missing industry information by matching on `company` and `location` where possible.
   - Identified and reviewed records where both `total_laid_off` and `percentage_laid_off` were `NULL`.

### 4. **Remove Unnecessary Columns**
   - After all cleaning operations, removed the `row_num` column as it was only needed for duplicate detection.

## Database Schema

The cleaned data is stored in a `layoffs_staging2` table with the following columns:

- `company`: Name of the company
- `location`: Location of the company
- `industry`: Industry the company belongs to
- `total_laid_off`: Total number of employees laid off
- `percentage_laid_off`: Percentage of employees laid off
- `date`: Date of the layoff event (in `DATE` format)
- `stage`: Stage of the company (e.g., startup, established)
- `country`: Country where the company is based
- `funds_raised_millions`: Amount of funds raised by the company (in millions)

## Running the Project

### Prerequisites

- A MySQL or compatible database environment.

### Execution

1. **Create Staging Table**: Create a new table `layoffs_staging` with the same structure as the original `layoffs` table.
2. **Remove Duplicates**: Run the SQL queries provided to identify and remove duplicate records.
3. **Standardize Data**: Apply updates to standardize the company names, industry names, country names, and date formats.
4. **Handle Null Values**: Run the SQL queries to address `NULL` and blank values, filling in missing data where possible.
5. **Remove Unnecessary Columns**: Drop the `row_num` column once all cleaning tasks are completed.

### Final Output

The final cleaned data resides in the `layoffs_staging2` table, ready for further analysis or use.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgements

- **SQL Documentation**: For reference on SQL syntax and best practices.
- **MySQL Community**: For providing useful resources and support.


