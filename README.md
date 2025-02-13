### project_4_machine_learning
# Machine Learning Models with Climate Change Data

## Project Overview
This project uses a dataset that records various climate change indicators for various countries since the beginning of the 20th century to develop a machine learning model that can be used to assess what indicators are best used to predict warming patterns. It assesses several factors within individual countries in a given year that record the state of the environment, such as temperature anomaly, forest area, sea level rise, artic ice extent, extreme weather events, average rainfall, air pollution, biodiversity, ocean acidification, and average temperature. It also uses several features related to human behavior, such as CO2 emissions, population, gdp, renewable energy usage, methane emissions, urbanization, deforestation rate, solar energy potential, waste management, per capita emissions, industrial activity, fossil fuel usage, energy consumption per capita, and an overall policy score. The models assess all these factors to attempt to make predictions for future warming trends.
<br> <br> <br>

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
<br><br><br>

## Machine Learning Models
The notebook is broken into three distict predictive models which show the various steps taken to make a more optimal model for the data. The data is properly standardized, scaled, and cleaned from things like duplicate columns in every model iteration to ensure maximum possible accuracy. Each model is saved in the "h5_files" directory within the repository. The methodology for each model is as follows:<br>
<br>
### Model Iteration 1
The first model utilizes the entire dataset created by the "SELECT *" statement in the initialization notebook. It analyzes the label "average temperature" against all other features in the data. The model is built, complied, and fit as shown in this image:<br>
<br>
<img width="812" alt="Screenshot 2025-02-13 at 16 15 05" src="https://github.com/user-attachments/assets/82b0c323-e79a-4814-be78-ebe7253c095b" /> <br>
<br>
The model has an r2 score of -0.10753530069296424 and an accuracy of 0.8956294655799866. While the accuracy performs well, the r2 score is not. This is likely because there is too much data so it is accurately categorizing data, but the model can't explain the variance in the data very well. This is displayed well in the graphs below that seek to answer the following questions:
- What is the average temperature for every country overtime?
<img width="569" alt="Screenshot 2025-02-13 at 14 35 43" src="https://github.com/user-attachments/assets/0ffcbd07-5968-40a5-a5f3-f0f6b408a49a" /> <br>
- What is the relationship between a country's gross domestic product and CO2 emissions?
<img width="562" alt="Screenshot 2025-02-13 at 14 36 25" src="https://github.com/user-attachments/assets/fcf63d66-6cff-4009-87d6-40b3a9f2f559" /> <br>
- What is the relationship between the deforestation rate and temperature abnormalities?
<img width="573" alt="Screenshot 2025-02-13 at 14 36 51" src="https://github.com/user-attachments/assets/5decf396-9c5a-4f20-b56b-eab6307c23fb" /> <br>
<br>
There are so many data points at every point in the graphs that they are ineligible. The next model attempts to fix this by aggregating the rows in the fill dataset by country and year. <br>

### Model Iteration 2
The second model utilizes the second dataset created from the initialization file, which is an average of every field by country and year. This significantly reduced the ammount of fields and should address some of the variation problems in the first dataset. The model is built, complied, and fit with the same method as the first so we can see if this alone resolved the issues with the first. 
<br> <br>
Once completed, this model had an r2 score of -0.2992058611821107 and an accuracy of 0.858296275138855 which is much better than the first model but still isn't a very reliable model overall. Still, it shows much better data as shown in the graphs below:
- What is the relationship between CO2 emissions and renewable energy usage overtime?
<img width="782" alt="Screenshot 2025-02-13 at 14 39 34" src="https://github.com/user-attachments/assets/6195261a-3a1e-402f-a35e-78255925d396" /> <br>
- What factors in the model are most useful in predicting sea level rise?
<img width="985" alt="Screenshot 2025-02-13 at 14 40 03" src="https://github.com/user-attachments/assets/54e1da2a-2903-4acf-8fb1-de8884e4e5dc" /> <br>
- What is the relationship between renewable energy usage and a country's policy score?
<img width="851" alt="Screenshot 2025-02-13 at 14 40 24" src="https://github.com/user-attachments/assets/3aefcd04-7f03-46dd-bfab-296ce2c8995d" /> <br>
<br>
The general trend between CO2 emissions and renewable energy adoption shows that as renewable energy adoption increased, carbon dioxide emissions decreased. Inversely, as renewable energy adoption decreased, there was generally a rise in carbon dioxide emissions. The data indicates that the most important factor in predicting sea-level rise is CO2 emissions. Through clustering techniques countries with similar environmental policies can be grouped together.

### Model Iteration 3




