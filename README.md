# UK Food Standards Agency Establishments Analysis

This project analyzes food hygiene ratings data from the UK Food Standards Agency (FSA). The data is stored in a MongoDB database, and the analysis is performed using Python and the PyMongo library.

## Project Overview

The goal of this project is to assist the editors of "Eat Safe, Love" magazine in evaluating food hygiene ratings data. This involves:

1.  **Database Setup:** Importing data, verifying database and collection creation, and performing initial data checks.
2.  **Database Updates:** Modifying the database by adding a new restaurant, updating records, and removing unwanted data.
3.  **Exploratory Analysis:** Answering specific questions from the magazine editors using MongoDB queries and aggregation pipelines, and presenting the results in Pandas DataFrames.

## Project Structure

The project consists of the following files:

* **establishments.json:** The JSON file containing the food hygiene ratings data.
* **NoSQL\_setup\_starter.ipynb:** Jupyter Notebook for setting up the database and performing initial data checks.
* **NoSQL\_analysis\_starter.ipynb:** Jupyter Notebook for performing exploratory analysis and answering the magazine editors' questions.
* **README.md:** This file, providing an overview of the project.

## Setup 
**Import Data:**
    * In order to conduct the analysis, I imported the `establishments.json` data into MongoDB using the following command:

        ```bash
        mongoimport --type json -d uk_food -c establishments --drop --file establishments.json --jsonArray
        ```
## Project Steps

### Part 1: Database and Jupyter Notebook Set Up

1.  Import the `establishments.json` data into MongoDB.
2.  Verify the database and collection creation.
3.  Inspect a sample document.

### Part 2: Update the Database

1.  Add a new restaurant ("Penang Flavours").
2.  Update the new restaurant with the correct `BusinessTypeID`.
3.  Remove establishments in Dover.
4.  Convert string number values to actual numbers for `latitude`, `longitude`, and `RatingValue`.

### Part 3: Exploratory Analysis

**Question 1.** Find establishments with a hygiene score of 20.

**Answer:** There are 41 establishments with a hygiene score of 20. Below please find the sample of 5 establishments from the analysis (Note: some columns were removed for enhanced data vitualization purposes).
| _id                      |   FHRSID | LocalAuthorityBusinessID   | BusinessName        | BusinessType                      |   BusinessTypeID | LocalAuthorityName   | LocalAuthorityEmailAddress          | scores                                                          | 
|:-------------------------|---------:|:---------------------------|:--------------------|:----------------------------------|-----------------:|:---------------------|:------------------------------------|:----------------------------------------------------------------|
| 67d72572949f5057b0e8fa05 |   612039 | 1970/FOOD                  | Brenalwood          | Caring Premises                   |                5 |  Tendring            | fhsadmin@tendringdc.gov.uk          | {'Hygiene': 20, 'Structural': 15, 'ConfidenceInManagement': 30} |
| 67d72572949f5057b0e8fd0e |   730933 | 1698/FOOD                  | Melrose Hotel       | Hotel/bed & breakfast/guest house |             7842 |  Tendring            | fhsadmin@tendringdc.gov.uk          | {'Hygiene': 20, 'Structural': 20, 'ConfidenceInManagement': 20} |
| 67d72572949f5057b0e8fefa |   172735 | PI/000023858               | Seaford Pizza       | Takeaway/sandwich shop            |             7844 |  Lewes               | ehealth.ldc@lewes-eastbourne.gov.uk | {'Hygiene': 20, 'Structural': 10, 'ConfidenceInManagement': 20} |
| 67d72572949f5057b0e8ff0a |   172953 | PI/000024532               | Golden Palace       | Restaurant/Cafe/Canteen           |                1 |  Lewes               | ehealth.ldc@lewes-eastbourne.gov.uk | {'Hygiene': 20, 'Structural': 10, 'ConfidenceInManagement': 20} |

**Question 2.** Find establishments in London with a `RatingValue` greater than or equal to 4.

**Answer:** There are 33 establishments in London with a rating value greater than or equal to 4. Below please find the sample of 5 establishments from the analysis (Note: some columns were removed for enhanced data vitualization purposes).
| _id                      |   FHRSID |  LocalAuthorityBusinessID   | BusinessName                         | BusinessType            |   BusinessTypeID |  RatingValue |    LocalAuthorityCode | LocalAuthorityName         | 
|:-------------------------|---------:| :---------------------------|:-------------------------------------|:------------------------|-----------------:| ------------:| ---------------------:|:---------------------------|
| 67d72572949f5057b0e9109c |   621707 |  PI/000025307               | Charlie's                            | Other catering premises |             7841 |            4 |                   508 | City of London Corporation | 
| 67d72572949f5057b0e913be |  1130836 |  PI/000034075               | Mv City Cruises Erasmus              | Other catering premises |             7841 |            5 |                   508 | City of London Corporation |
| 67d72572949f5057b0e91f0e |   293783 |  PI/000002614               | Benfleet Motor Yacht Club            | Other catering premises |             7841 |            4 |                   508 | City of London Corporation | 
| 67d72573949f5057b0e92d0e |  1315095 |  PI/000036464               | Coombs Catering t/a The Lock and Key | Restaurant/Cafe/Canteen |                1 |            5 |                   508 | City of London Corporation |
| 67d72573949f5057b0e92d0f |   294474 |  PI/000014647               | Tilbury Seafarers Centre             | Restaurant/Cafe/Canteen |                1 |            5 |                   508 | City of London Corporation | 

**Question 3.**  Find the top 5 establishments near "Penang Flavours" with a `RatingValue` of 5, sorted by hygiene score.

**Answer:** Below are the top 5 establishments near "Penang Flavours with a rating value of 5 and sorted by lowest hygiene score
| _id                      |   FHRSID | LocalAuthorityBusinessID   | BusinessName                        | BusinessType                          |   BusinessTypeID | RatingValue | RatingKey    | RatingDate          | scores                                                       |
|:-------------------------|---------:|:---------------------------|:------------------------------------|:--------------------------------------|-----------------:|------------:|:-------------|:--------------------|:-------------------------------------------------------------|
| 67d72573949f5057b0e94ee5 |   694609 | PI/000116619               | Volunteer                           | Pub/bar/nightclub                     |             7843 |           5 | fhrs_5_en-gb | 2019-08-05T00:00:00 | {'Hygiene': 0, 'Structural': 0, 'ConfidenceInManagement': 0} | 
| 67d72573949f5057b0e94ef6 |   695241 | PI/000179088               | Plumstead Manor Nursery             | Caring Premises                       |                5 |           5 | fhrs_5_en-gb | 2021-06-16T00:00:00 | {'Hygiene': 0, 'Structural': 0, 'ConfidenceInManagement': 5} | 
| 67d72573949f5057b0e94efb |   694478 | PI/000086506               | Atlantic Fish Bar                   | Takeaway/sandwich shop                |             7844 |           5 | fhrs_5_en-gb | 2021-06-16T00:00:00 | {'Hygiene': 0, 'Structural': 0, 'ConfidenceInManagement': 5} |
| 67d72573949f5057b0e94eb3 |   695223 | PI/000178842               | Iceland                             | Retailers - supermarkets/hypermarkets |             7840 |           5 | fhrs_5_en-gb | 2019-11-13T00:00:00 | {'Hygiene': 0, 'Structural': 5, 'ConfidenceInManagement': 5} | 
| 67d72573949f5057b0e94ec6 |  1380578 | 14425                      | Howe and Co Fish and Chips - Van 17 | Mobile caterer                        |             7846 |           5 | fhrs_5_en-gb | 2021-11-11T00:00:00 | {'Hygiene': 0, 'Structural': 0, 'ConfidenceInManagement': 0} |

**Question 4.**  Find the number of establishments in each Local Authority area with a hygiene score of 0.

**Answer:** tThere are 55 different Local Authority names present in the results of the grouping operation. Each of those 55 local authorities contains at least one establishment that has a hygiene score of 0.  Below is the sample of 10 results.

<img width="169" alt="image" src="https://github.com/user-attachments/assets/842c6a6f-e18c-4820-8b31-f45bca5ff40a" />


**References**
* UK Food Standards AgencyLinks to an external site. (2022). UK food hygiene rating data API.
* https://ratings.food.gov.uk/open-data/en-GBLinks to an external site.. Contains public sector information licensed under the Open Government Licence v3.0Links to an external site.
Accessed Sept 9, 2022 and Sept 12, 2022 with the establishment settings as follows: longitude=51.5072, latitude=-0.1276, maxdistancelimit=4567, pagesize=10000, sortoptionkey=distance, pagenumber=(1,2,3,4,5,6,7,8).
* Acknowledgement: Code research and debugging assistance provided by Google and Stackoverflow.