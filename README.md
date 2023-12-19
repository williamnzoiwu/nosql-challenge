# nosql-challenge
## NoSQL Module 12 Challenge

First the data from the establishments.json file is imported from the Terminal. The database is named "uk_food" and the collection is named "establishments."

### Part 1: Setup
In the first notebook, first the necessary libraries are imported: PyMongo and Pretty Print (pprint). Then an instance of the Mongo Client is created. To confirm the database was created properly, the code then prints a list of all the databases in MongoDB to ensure "uk_food" is among the list. Then the collections in the database are printed to ensure that establishments is there. Then the first document in the collection is reviewed using a find_one, using find_one and the estabishments collection is  to a variable of the same name. 

### Part 2: Update Database
The database is then updated using a dictionary to add another document containing data for another restaurant. The new establishment is then added to the collection using an insert_one. Then a find one is used to insure the new establishment was added, searching by business name. Next the code finds the BusinessTypeID for "Restaurant/Cafe/Canteen" and returns only the BusinessTypeID and BusinessType fields. The new restaurant is then updated with the  found BusinessTypeID. The code then finds how many establishments have the common LocalAuthorityName of Dover using a count_documents, then deletes all those documents using a delete_many. After verifying those particular documents have been deleted, the code then changes the latitude and longitude field data types to decimals instead of strings. The code then sets rating values that are not numbers between 1 and 5 to null, and changes the RatingValue datatype to integer from string.

### Exploratory Analysis
The imports and the database are first uploaded to the new notebook, and then the following questions are answered:

Which establishments have a hygiene score equal to 20?

This is answered by simply creating a query for a hygiene score of 20 and then counting all the documents that match that query. The first document is then printed, and the results are then transferred to a DataFrame.

Which establishments in London have a RatingValue greater than or equal to 4? The first document is then printed, and the results are then transferred to a DataFrame.

This question is answered by creating a query using regular expression to find documents where 'LocalAuthorityName' contains the word London, and where the 'RatingValue' field is greater than or equal to 4.

What are the top 5 establishments with a RatingValue of 5, sorted by lowest hygiene score, nearest to the new restaurant added, "Penang Flavours"

This question is answered by first creating a variable for the desired degree away from the Penang restaurant(0.01), and then creating latitude and longitude variables equal to the latitude and longtitude of the Penang establishment. The query is then created by searching for a latitude and longitude greater than or equal to the latitude and longitude of Penang Flavors minus 0.01, in addition to a latitude and longitude less than or equal to the latitude and longitude of Penang Flavors plus 0.01. A Rating Value of 5 is added to the end of the query. Next the the results are sorted by hygiene score, and the top 5 documents are printed by using a limit of 5. The results are then transferred to a DataFrame.

How many establishments in each Local Authority area have a hygiene score of 0? Sort the results from highest to lowest, and print out the top ten local authority areas.

This question is answered by first creating a match query for establishments with a hygiene score of 0, then doing a group query to match the documents by Local Authority Name. A sort variable is then created to sort the mathces in descending order by count. Then a pipeline is created utilizing the match query, group query, and sort variable. The pipeline is then aggregated, and the top 10 results are printed. The results are then transferred to a DataFrame.
