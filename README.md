## Uber Data Engineering Project
This project processes Uber data using the Mage.ai framework, transforming the raw data from an API, applying transformations, and then exporting the data to BigQuery for analysis and further processing.

# Project Structure
extract.py: This script loads Uber data from a provided API endpoint and returns it as a pandas DataFrame.

transform.py: This script performs the necessary transformations on the raw data, including datetime manipulations, creation of various dimension tables (e.g., datetime, passenger count, trip distance), and the fact table.

load.py: This script exports the transformed data to BigQuery, following the configuration specified in the io_config.yaml file.

# Requirements
To run this project, you will need to install the following dependencies:

Mage.ai - Framework for data transformation and pipeline management.

Pandas - Library for data manipulation.

Requests - For making HTTP requests to fetch the Uber data from the API.

BigQuery - For exporting data to Google BigQuery.

pip install mage-ai pandas requests google-cloud-bigquery
# Setup and Configuration
Clone the Repository:

Clone the repository to your local machine.

git clone <repository_url>
cd <project_directory>
BigQuery Configuration:

Ensure that you have a io_config.yaml file in the project root that contains the configuration for BigQuery. This file should look like the following:

bigquery:
  project_id: "<your_project_id>"
  credentials: "<path_to_your_credentials_file>"
The io_config.yaml file will be used in the load.py script to export the data to BigQuery.

API Endpoint for Uber Data:

The raw Uber data is loaded from the following API endpoint:

https://storage.googleapis.com/uber-data-engineering-project-darshil/uber_data.csv
# Workflow
The project follows the ETL (Extract, Transform, Load) pipeline:

Extract Data (extract.py):

Fetches raw Uber data from the provided API endpoint.

Loads the data into a pandas DataFrame.

Transform Data (transform.py):

Performs various transformations, including:

Converting datetime columns to proper pandas datetime objects.

Creating dimension tables like datetime_dim, passenger_count_dim, rate_code_dim, etc.

Creating a fact table by merging the dimension tables with the original data.

Load Data (load.py):

Exports the transformed data into BigQuery.

Each table (datetime_dim, passenger_count_dim, rate_code_dim, etc.) is exported as a separate BigQuery table.

The fact table is also exported to BigQuery for further analysis.

# How to Run the Project
Clone the repository and install the necessary dependencies.

Set up your BigQuery credentials and ensure your io_config.yaml is configured correctly.

# Run the project through Mage.ai or execute each script individually.

# Run the pipeline using Mage.ai
mage run
Alternatively, you can execute the scripts in sequence:

python extract.py
python transform.py
python load.py
