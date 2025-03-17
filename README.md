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

**Answer:** There are 41 establishments with a hygiene score of 20.
 C:\Users\Bim\Desktop\Module-12_nosql-challenge\Analysis