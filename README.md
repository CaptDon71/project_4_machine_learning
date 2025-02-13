### project_4_machine_learning
# Machine Learning Models with Climate Change Data

## Project Overview
This project uses a dataset that records various climate change indicators for various countries since the beginning of the 20th century to develop a machine learning model that can be used to assess what indicators are best used to predict warming patterns. It assesses several factors within individual countries in a given year that record the state of the environment, such as temperature anomaly, forest area, sea level rise, artic ice extent, extreme weather events, average rainfall, air pollution, biodiversity, ocean acidification, and average temperature. It also uses several features related to human behavior, such as CO2 emissions, population, gdp, renewable energy usage, methane emissions, urbanization, deforestation rate, solar energy potential, waste management, per capita emissions, industrial activity, fossil fuel usage, energy consumption per capita, and an overall policy score. The models assess all these factors to attempt to make predictions for future warming trends.

## PostgreSQL Database Initialization and Extraction
The initial dataset is extracted from the following source: <br>
https://www.kaggle.com/datasets/ankushpanday1/global-warming-dataset-195-countries-1900-2023 <br>
<br>
It is then uploaded to a local postgres database with the notebook file 'database_initialization.ipynb' and extracted back to csv format with the same notebook. 
The notebook creates two new csvs: one that is a full extraction of the data using a "SELECT *" SQL statement and the another that averages every field in the dataset grouped by country and year.
<br>
<br>
To initialize the database with the aforementioned notebook, you MUST create a python file called 'postgres_info.py' with your local postgres username and password stored inside. The file should look like this:<br>
<img width="332" alt="Screenshot 2025-02-13 at 15 06 15" src="https://github.com/user-attachments/assets/bc8a7aa5-5d6f-4403-af25-16966dae9edd" /> <br>
You must manually add your username and password to this file and save it. The gitignore file will protect your information this way.
<br>
