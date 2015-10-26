#**USING YQL CONSOLE QUERY BUILDER**
- YQL console provides a screen which helps you build an YQL statement. If you don’t remember the options in an YQL statement for a table, the query builder helps to construct the statement.

- An example to illustrate the use of Query Builder

- Let us take the example of the local.search table. Start YQL console and click the table local.search.  You will see the result in the YQL console:

 ![alt text](https://github.com/pkdevaraj/Presentations/blob/gh-pages/IMAGES/YQL6.1.PNG "Query Builder 1")



- The example statement,
select * from local.search where zip='94085' and query='pizza' Has two parameters, zip and query.

- If you are wondering if there are other options we can use with local.search table, click local search button:

![alt text](https://github.com/pkdevaraj/Presentations/blob/gh-pages/IMAGES/YQL6.2.PNG "Query Builder 2")

![alt text](https://github.com/pkdevaraj/Presentations/blob/gh-pages/IMAGES/YQL6.3.PNG "Query Builder 3")

- When we click the local.search button, you will see the followingscreen:

- Notice that the lower part of the screen, shows five SELECTforms.

 
	Firstform:
- Open the first SELECT by clicking the first  (it may already be open). You will see the first format for SELECT:

![alt text](https://github.com/pkdevaraj/Presentations/blob/gh-pages/IMAGES/YQL6.4.PNG "Query Builder 4")
 
- There is textbox for listing_id. If you know the listing_id, type it and execute the statement by clicking the TEST button.  This is one form of using the SELECT on local.search table.

	Secondform
- Open the second SELECT by clicking the  . You will see the second format for SELECT:

![alt text](https://github.com/pkdevaraj/Presentations/blob/gh-pages/IMAGES/YQL6.5.PNG "Query Builder 5")

- This format is showing that you can use SELECT on local.search by inputting latitude, longitude, and query.

	Thirdform
- Open the second SELECT by clicking the play button . You will see the third format for SELECT:

![alt text](https://github.com/pkdevaraj/Presentations/blob/gh-pages/IMAGES/YQL6.6.PNG "Query Builder 6")
 

- This format is showing that you can use SELECT on local.search by inputting location and query.

	Fourthform
- Open the second SELECT by clicking the  . You will see the fourth format for SELECT:

![alt text](https://github.com/pkdevaraj/Presentations/blob/gh-pages/IMAGES/YQL6.7.PNG "Query Builder 7")

- This format is showing that you can use SELECT on local.search by inputting zip and query.


	Fifthform
- Open the second SELECT by clicking the  . You will see the fifth format for SELECT:
 
![alt text](https://github.com/pkdevaraj/Presentations/blob/gh-pages/IMAGES/YQL6.8.PNG "Query Builder 8")

- This format is showing that you can use SELECT on local.search by inputting city, state and query.


- Note: In all of them we can select how many results you like to see.



[**NEXT**](https://github.com/sharathvontari/Yahoo-query-language/blob/master/Application%20Using%20YQL.md)     

[**BACK TO CONTENTS**](https://github.com/sharathvontari/Yahoo-query-language/blob/master/README.md)
