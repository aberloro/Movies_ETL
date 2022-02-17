# Movies_ETL Extract Transform Load

## Project Overview

Work was done in [Phase1](https://github.com/aberloro/Movies_ETL/tree/main/Phase1) to extract movie data from Wikipedia and Kaggle, clean and transform this data into useful DataFrames, and load the finished DataFrames into an SQL database.  The purpose of this project is to refactor that code into a few functions that automate the ETL pipeline and run it on a daily basis.

### Deliverables
  1. ETL function to read three data files.
  2. Extract and Transform Wikipedia Data
  3. Extract and Transform Kaggle Data.
  4. Create the Movie Database.

### Tools / Resources
  - Wikipedia / Kaggle
  - Jupyter Notebook
  - Python / Pandas / Regex
  - Postgress SQL / pgAdmin
 
## Code
  1. [ETL_function_test.ipynb](https://github.com/aberloro/Movies_ETL/blob/main/ETL_function_test.ipynb)
       - Read in CSVs as Pandas Dataframes
       - Open JSON file then read in as Pandas DataFrame
       - Set file paths
       - Return DataFrames
  2. [ETL_clean_wiki_movies.ipynb](https://github.com/aberloro/Movies_ETL/blob/main/ETL_clean_wiki_movies.ipynb)
       - Define function to clean up alternate titles and rename columns for each movie
       - Load files usind code from #1
       - Pass wiki movies through cleaning function
       - Use Try and Except block to remove duplicate rows based on IMDB ID
       - Drop columns with less than 90% of the data
       - clean Box Office, Budget, Relase Date, and Runnig Time columns with RegEX
       - Return DataFrames

  3. [ETL_clean_kaggle_data.ipynb](https://github.com/aberloro/Movies_ETL/blob/main/ETL_clean_kaggle_data.ipynb)
       - Remove adult movies
       - Convert kaggle metadata datatypes where needed
       - Merge wiki and Kaggle DataFrames and drop unnecessary columns
       - Add function to fill in missing Kaggle data with available wiki data
       - Filter and rename wanted columns
       - Convert Kaggle ratings data types where needed
       - Pivot data so ratings are grouped by movie ID and listed as counts in columns
       - Merge ratings data into movies_with_ratings_df
       - Return 3 DataFrames
       
  4. [ETL_create_database.ipynb](https://github.com/aberloro/Movies_ETL/blob/main/ETL_create_database.ipynb)
       - Create variable to hold Postgress URL as string
       - Create engine variable
       - Import movies_df using .to_sql() and replace if exists parameter
       - Import larger ratings file as chuncks using .to_sql() and append if exists parameter

## Databases
   1. Confirming [6052 rows](https://github.com/aberloro/Movies_ETL/blob/main/Resources/movies_query.png) in the movies database.
   2. Confirming [26,024,289 rows](https://github.com/aberloro/Movies_ETL/blob/main/Resources/ratings_query.png) in the ratings database. 


