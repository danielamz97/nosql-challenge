# MongoDB Data Analysis for UK Food Establishments

## Overview

This project involves setting up a MongoDB database named `uk_food` and a collection named `establishments`. The data used for analysis is stored in the file `Resources/establishments.json`. The analysis is performed in two Jupyter notebook files: `NoSQL_setup_starter.ipynb` for database setup and `NoSQL_analysis_starter.ipynb` for exploratory analysis.

## Part 1: Database and Jupyter Notebook Set Up

1. The MongoDB database is set up using the `mongoimport` command in the `NoSQL_setup_starter.ipynb` notebook. The command drops any existing `establishments` collection and imports data from `establishments.json` into the MongoDB `uk_food` database.

2. The setup notebook correctly imports PyMongo and Pretty Print, creates a Mongo Client instance, lists databases, and lists collections in the `uk_food` database. Additionally, it uses `find_one()` and `pprint` to display one document in the `establishments` collection.

## Part 2: Update the Database

1. The notebook updates the database by inserting data for the "Penang Flavours" restaurant into the `establishments` collection.

2. Queries are performed to find and return the BusinessTypeID for "Restaurant/Cafe/Canteen" and update the "Penang Flavours" document with the correct BusinessTypeID.

3. Documents with "Dover Local Authority" as the value for LocalAuthorityName are deleted, and a count_documents() check ensures the documents were removed.

4. An update_many() query is performed to convert latitude and longitude fields from strings to decimal numbers and RatingValue to integers.

## Part 3: Exploratory Analysis

### Question 1: Establishments with a hygiene score equal to 20

- A query is correctly performed to find the establishments with a hygiene score of 20.
- `count_documents()` is used to list the correct number of documents (answer: 41).
- The first result is printed using `pprint`.
- The results are converted to a Pandas DataFrame and display the first 10 rows.

### Question 2: Establishments in London with a RatingValue greater than or equal to 4

- A query is correctly performed to find the establishments in London with a RatingValue greater than or equal to 4.
- The query uses the $regex operator to locate the London establishments.
- `count_documents()` is used to list the correct number of documents (answer: 33).
- The first result is printed using `pprint`.
- The results are converted to a Pandas DataFrame and display the first 10 rows.

### Question 3: Top 5 establishments with a RatingValue of 5, sorted by lowest hygiene score, nearest to "Penang Flavours"

- A query is correctly performed to find the establishments within 0.01 degree of the "Penang Flavours" restaurant.
- The query also limits the results to establishments with a RatingValue of 5.
- The query uses the `sort()` method in PyMongo to sort in ascending order on the hygiene score.
- The query uses the `limit()` method in PyMongo to limit the results to 5.
- All five results are printed using `pprint`.
- The results are converted to a Pandas DataFrame and displayed.

### Question 4: Establishments in each Local Authority area with a hygiene score of 0

- An aggregation pipeline is built to include a match query, group, and sort.
- The match query matches documents with a hygiene score of 0.
- The group step of the pipeline is grouped on LocalAuthorityName and counts the number of documents.
- The sort step of the pipeline sorts the count of the documents in descending order.
- The aggregation pipeline is correctly sent to the `aggregate()` method.
- The results from the aggregation query are cast as a list and then saved to a variable.
- The first ten results are printed using `pprint`.
- The results are converted to a Pandas DataFrame and display the first 10 rows.
