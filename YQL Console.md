#**THE YQL CONSOLE**
- The YQL console is the GUI provided by Yahoo to apply YQL statements. First, sign in to your Yahoo account and then to open the console, go to: http://developer.yahoo.com/yql/console/.
- If you don’t have a Yahoo account, sign up for one.
- When we click the link, we can see the following console screen:
 
 ![alt text](https://github.com/pkdevaraj/Presentations/blob/gh-pages/IMAGES/YQL2.1.PNG "Console Screen")

## Important components of the console:

- 1.	This is the box where we can type the YQLstatements.
- 2.	This is the box we can see the results of a query (in XML orJSON).
- 3.	Example Queries – This provides a huge number of Example predefined YQLstatements.
- 4.	Predefined data tables - again, predefined YQL services (Yahoo calls themTables).
- 5.	This is the resulting URL from the YQL statement executed.



##**Getting started with YQLconsole**
- Example 1:
- Step 1: Start YQL console in a browser:http://developer.yahoo.com/yql/console/.

By default the YQL statement show tables appears in the statement box.
- Step 2: As an example, click find sushi restaurants in san Francisco under Example Queries (box 3 above)

![alt text](https://github.com/pkdevaraj/Presentations/blob/gh-pages/IMAGES/YQL2.2.PNG "Console Screen 2")

 This will bring the following YQL statement in box1:

select * from local.search where query="sushi" and location="san francisco,ca"

- Step 3: Below Box 1, check XML button and click button.
- Step 4: You will see the result of the query in Box 2. Notice this is an XML document. Notice that the data in the XML document is the information about sushi restaurants in "san francisco, ca"area.
 
![alt text](https://github.com/pkdevaraj/Presentations/blob/gh-pages/IMAGES/YQL2.3.PNG "Console Screen 3")


- Step 5: The URL in Box 5 is the “REST query url” for the Web service. This is what we use when we need to develop applications with this Web service query. To call the YQL Web Service, an application would call an HTTP GET method on this URL. The q parameter in the URL matches the SELECT statement displayed under Your YQL Statement (except that characters such as spaces are URL encoded). 

- Step 6: Copy the URL in Box 5 and paste in a browser address bar.  See results in thebrowser.

![alt text](https://github.com/pkdevaraj/Presentations/blob/gh-pages/IMAGES/YQL2.4.PNG "Console Screen 4")

- These are the essential steps in using YQLconsole.

-  Example 2:

	Under Data Tables (Box 4), Click Weather. Click (as an example) weather.forecast. Notice result.
 
![alt text](https://github.com/pkdevaraj/Presentations/blob/gh-pages/IMAGES/YQL2.5.PNG "Console Screen 5")

- We can try more Data Tables from the console. As we notice there is a huge set of YQL statements readily available.

[**NEXT**](https://github.com/sharathvontari/Yahoo-query-language/blob/master/YQL%20Statements.md)     

[**BACK TO CONTENTS**](https://github.com/sharathvontari/Yahoo-query-language/blob/master/README.md)









 


 


