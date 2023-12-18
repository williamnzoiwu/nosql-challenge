# nosql-challenge
NoSQL Module 12 Challenge

### NoSQL Setup
First the data from the establishments.json file is imported from the Terminal. The database is named "uk_food" and the collection is named "establishments."

In the first notebook, first the necessary libraries are imported: PyMongo and Pretty Print (pprint). Then an instance of the Mongo Client is created. To confirm the database was created properly, the code then prints a list of all the databases in MongoDB to ensure "uk_food" is among the list. Then the collections in the database are printed to ensure that establishments is there. Then the first document in the collection is reviewed using a find_one, using find_one and the estabishments collection is  to a variable of the same name. 

The database is then updated using a dictionary to add another document containing data for another restaurant. The new establishment is then added to the collection using an insert_one. Then a find one is used to insure the new establishment was added, searching by business name.

Part 2: Update the Database
Use NoSQL_setup_starter.ipynb for this section of the challenge.

The magazine editors have some requested modifications for the database before you can perform any queries or analysis for them. Make the following changes to the establishments collection:

An exciting new halal restaurant just opened in Greenwich, but hasn't been rated yet. The magazine has asked you to include it in your analysis. Add the following information to the database:
