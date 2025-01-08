# nosql-challenge

# Objective: The UK Food Standards Agency evaluates various establishments across the United Kingdom, and gives them a food hygiene rating. You've been contracted by the editors of a food magazine, Eat Safe, Love, to evaluate some of the ratings data in order to help their journalists and food critics decide where to focus future articles.

# NoSQL setup starter:

### Part 1: 

We start this section by importing the following dependencies:

* from pymongo import MongoClient

* from pprint import pprint

This sections purpose is to set up the Database and Jupyter Notbook by importing the establishments.json file and naming the database as "uk_food" as well as the collection as "establishments". 

### Part 2: 

This sections purpose is to update the Database with new restaurant data. We also check to make sure that new data was inserted correctly, updating the Database, and confirming that other documents still remained within the Database. We also changed some datatypes for the latitude & longitudes making sure that they are read in as numbers instead of their default being strings. We also applied the same method to the rating values and confirming those were changed into numbers as well.

# NoSQL analysis starter:

We start this section off by just setting up the notebook and importing all dependencies that are needed such as: 

* from pymongo import MongoClient
* import pandas as pd
* from pprint import pprint

### Part 3:

In this section we display the number of documents contained in the result by calling the "count_documents" function, we then display the first document in pretty print style, and then convert the result to a DataFrame & display the first 10 rows.

We also fetch the establishments that contain a hygiene score of 20 and use "count_documents" to displaya how many establishments match that score. Finally, we convert that result into a Pandas DataFrame.

Next, we fetch which establishments have a RatingValue of 4 or more and call the same function to display the other establishments with the same criteria. Again, that result is turned into a DataFrame.

Additionally, we then find the top 5 establishments with a `RatingValue` rating value of 5, sorted by lowest hygiene score, nearest to the new restaurant added, "Penang Flavours".

We end this sheet of code with finding How many establishments in each Local Authority area have a hygiene score of 0 and convert that into another DataFrame.

# I got/referenced the following lines of code from Xpert Learning Assistant/GitHub:

* establishments.update_many({}, [{'$set': {'geocode.longitude': {'$toDouble': '$geocode.longitude'}, 
                                         'geocode.latitude': {'$toDouble': '$geocode.latitude'}
                                         }
                                }
                               ]
                          )
  
* list(establishments.aggregate([{
    '$project': {'latitude': {'$isNumber': '$geocode.latitude'},
                 'longitude': {'$isNumber': '$geocode.longitude'}}
}]))

* result = list(establishments.find(query1))

* query2 = {"RatingValue": {"$eq": 5},
         "geocode.longitude": {"$lte": (longitude + degree_search), "$gte": (longitude - degree_search)},
         "geocode.latitude": {"$lte": (latitude + degree_search), "$gte": (latitude - degree_search)}}
sort = [("scores.Hygiene", 1)]

* pipeline = [query_match, query_group, sort]
result = list(establishments.aggregate(pipeline))
result




