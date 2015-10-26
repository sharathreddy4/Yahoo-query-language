#**YQL STATEMENTS**
- The following table lists all YQL statements.

##**The SELECT statement in detail**

- SELECT is the most important YQL statement.The SELECT statement of YQL retrieves data from YQL tables. The YQL Web Servicefetches data from a back-end data source (often a Web service), transforms the data, and returns the data in either XML or JSON format. Table rows are represented as repeating XML elements or JSONobjects.

- Syntax of SELECT

- The YQL SELECT statement has the following syntax:

- SELECT what FROM table WHERE filter [|function]

- The what clause contains the fields (columns) to retrieve. The fields correspond to theXML elements or JSON objects in the data returned by the SELECT. An asterisk (the "*" character) in the what clause means all fields.

- The table is either the YQL pre-defined or Open Data Table that represents a data source. (Unlike in SQL, in YQL only one table can bespecified.)

- The filter is a comparison expression that limits the rows returned. The results ofthe SELECT can be piped to an optional function, such assort.

- In YQL, statement keywords such as SELECT and WHERE are case-insensitive. Table and field names are case sensitive. In string comparisons, the values are case sensitive. String literals must be enclosed in quotes; either double or single quotes are allowed.

- Note:
- When you copy a YQL statement from my notes and paste it the console, the quotes maybe of wrong kind.  Remember to retype quotes if you see anerror.

- Some services (such as flickr) require an API key to use their services.

- As we saw, the console provides a huge set of pre-defined tables. In addition there are community open data tables. When you execute a YQL statement and you see an error such as, “No definition found for …..”, it is likely that it is a community open data table. To use such a table, you check “Show Community Tables” link under Data Tables on the left side of theconsole:






- Examples
	Using the tablegoogle.search

select * from google.search whereq='Obama'

This will search Google for the wordObama.

- Note: The YQL console might display an error: “No definition found for Table google.search.” If you see this error message, check the box to the left of “Show Community Tables”.  It will nowwork.

Here is the result (shownpartially):


	Selecting certain fields only

- In the previous result, observe that <results> contains several tags. We can select to receive only selected tags only. The following example selects only title andcontent:

select  title,content  from  google.search  whereq='Obama'













- Here is theresult:

 


	Using AND and OR infilters
The filter expressions can be combined with the boolean AND and OR operators. The AND operator has precedence over the OR operator. To change precedence, encloseexpressions inparentheses.

- Example:
select * from google.search where q='Obama' ORq='Clinton'


	Using IN infilters
We can use IN in the filter expressions if the choices to select are many. Items are separated bycommas.

- Example:
select * from google.search where q in ('Obama','Clinton','Carter')

	Limiting number of itemsreturned

- The maximum number of items returned by a SELECT is 5000. The maximumprocessing time for a YQL statement is 30 seconds. For most tables, the default number of items returned is 10. (That is, the default is 10 if we do not specify a limit in the SELECT statement.) We can change the limit by using limit infilter.

- Example:
select * from google.search where q in ('Obama', 'Clinton','Carter') limit5


- Note: When the limit is large number, it may still give you smaller number ofresults.

	Sortingresults

- We can sort the results on a field, using the keyword sort. To sort, add the following at the end of the YQLstatement:

|sort(field=”fieldname”)

The symbol | is called the pipe symbol (fromUnix).

- Example:

select * from google.search where q in ('Obama', 'Clinton','Carter') |sort(field="title")




	Using reverse() infilter

- This reverses the original list ofresults


- Example:
select title from google.search where q in ('Obama', 'Clinton','Carter') |reverse()

- Example:
select title from google.search where q in ('Obama', 'Clinton','Carter')| sort(field="title")|reverse()

	Using unique infilter
- Removes items (rows) with duplicate values in the specifiedfield.

- Example:
selecttitlefromgoogle.searchwhereqin('Obama','Clinton','Carter')|unique(field="title")

	Using truncate infilter
- Displays the first specified number ofitems.
- Syntax:|truncate(count=number)

- Example:
select title from google.search where q in ('Obama', 'Clinton','Carter') |truncate(count=3)


	Using tail infilter
- Displays the last specified number ofitems.
- Syntax:|tail(count=number)

- Example:
select title from google.search where q in ('Obama', 'Clinton','Carter') |tail(count=3)

 



 



