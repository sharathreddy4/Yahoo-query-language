#**YQL WEB SERVICES**
#**Yahoo Local Search WebServices**
- There are various ways you can construct a YQL statement, which uses local.search.

	Using zip code and query

select * from local.search where zip=”---“ andquery=”---“

- Example:
select * from local.search where zip='10598' andquery='pizza'



	Using location andquery

SELECT * FROM local.search WHERE location="---" andquery="---"

- Example:
SELECT * FROM local.search WHERE location="White Plains, NY" andquery="pizza"


	Using latitude, longitude andquery

SELECT * FROM local.search WHERE latitude="---" and longitude="---" andquery="---"

- Example:
SELECT * FROM local.search WHERE latitude="28.5383355" and longitude="-81.3792365" andquery="pizza"

	Using city, state andquery

SELECT * FROM local.search WHERE city="---" and state="--" andquery="---"

- Example:
SELECT * FROM local.search WHERE city="Yorktown" and state="NY" andquery="pizza"



##**Introduction to Yahoo! Social APIs**
- The Yahoo! Social APIs consist of YQL tables and REST APIs that enable you tocreate socially-enabledapplications.

	The Global User Identifier(GUID)

- The Global User Identifier (GUID) is a string that uniquely identifies a Yahoo! user. If you have a Yahoo mail account, you have a GUID. In YQL, the me keyword is the GUID valueof the user currently logged in to Yahoo!
How to retrieve your GUID using Yahoo mailid? The YQL statement (in YQLconsole):
select guid from yahoo.identity where yid =‘YahooEmailId’
Displays the GUID of the person whose Yahoo email id is specified.

- Example:

select guid from yahoo.identity where yid ='cscipresentation2@yahoo.com' 
This returns the GUID:SB6SGEUHFM6TGK6T5UF2TKFAAY


##**Yahoo GeoPlanet WebService**
- GeoPlanet is a set of Web Service tables accessed through YQL. They also provide APIs, but we will use YQL to access these services.



- Yahoo! GeoPlanet provides information for about six million named places globally. Coverage varies from country to country, but includes several hundred thousandunique administrative areas with half a million variant names; several thousand historical administrative areas; over two million unique settlements and suburbs, and millions of unique postal codes covering about 150 countries, plus a significant number of Points of Interest, Colloquial Regions, Airports, Area Codes, Time Zones, andIslands.

- Where On Earth ID(WOEID)
Yahoo identifies spatial entities by a 32-bit identifier called the Where On Earth ID (WOEID). WOEIDs are unique and non-repetitive, and are assigned to all entities within the system. A WOEID, once assigned, is never changed or recycled. 

- One way of finding WOEID is to use YQLstatement, select woeid from geo.places where text =‘place’
- Examples:
select woeid from geo.places where text ='JFK' returns12520380

select woeid from geo.places where text = 'taj mahal' returns23686018

select woeid from geo.places where text = 'Yosemite NationalPark' returns55813396


	The geo.placestables

- The geo.places table returns information about a place orplaces. There are two ways you can usegeo.places:

select * from geo.places where text = “place” select * from geo.places where WOEID =“woeid”

- Examples:
select * from geo.places where text = 'Yosemite National Park' select * from geo.places where text = 'tajmahal'
select * from geo.places where woeid='12520380'

 


	The geo.continentstable

- The geo.continents table returns information about places that arecontinents. select * fromgeo.continents

	The geo.oceanstable

- The geo.oceans table returns information about places that areoceans. select * fromgeo.oceans

	The geo.seastable

- The geo.seas table returns information about places that are seas. select * fromgeo.seas

	The geo.countriestable

- The geo.countries table returns information about places that are countries. select * fromgeo.countries

	The geo.statestable
- The geo.states table returns information about places that are states. select * from geo.states where place = “name of country or WOEID” 
- Examples:
select * from geo.states where place="US" select * from geo.states where place="UK" select * from geo.states whereplace="India"
select * from geo.states whereplace="23424824"

	The geo.countiestable

- The geo.counties table returns information about places that are counties. Note that the term "county" refers to any administrative area that subdivides a first-level administrative area, such as counties, parishes, boroughs, departments, provinces,districts.


select * from geo.counties where place = “name of state orWOEID”

- Examples:
select * from geo.counties whereplace="NY"
select * from geo.counties where place="ShandongProvince"

	The geo.districtstable

- The geo.districts table returns information about places that are third-level administrative areas within acountry.

select * from geo.districts where place = “name of county orWOEID”

- Example:
select * from geo.districts where place="GreaterLondon"


##**Yahoo Flickr Webservice**
- Flickr is a Web site which is used to store, sort, search and share yourphotos online.

- Flickr provides several APIs using which you develop applications to retrieve photosfrom flickr site. We will not use the APIs directly, but use Flickr tables in YQLstatements.

- To use flickr APIs (or use them in YQL console), you need an API key from Flickr. It is easy to get one. Go to the Web site, http://www.flickr.com/services/apps/create/ and apply for an API key. When done, Flickr generates two keys for you. One is called API key and the other secret key. You need them when use flickr tables in YQLstatements.

- I have created an API key for cscipresentation2:
API key:64c914c0bdd6003c38a18bb6ceae5f38
Secret key:282635497b1d2628 User name:cscipresentation2
Screen name:csci Password:yahoo

- Flickr IDnumber
Every registered user on Flickr has user id number. To find your user id number, first create a Buddy icon.
  

- Once you have a Buddy icon, follow this link inFirefox:
https://www.flickr.com/import/people/yahoo/
 



- Right click on your Buddy icon and select “Save LinkAs”:


- Copy the user id and save it for futurereference. csci user id:92894228@N02
- Flicker users form groups according to their interest in photos. To find some groups, go to the site: http://www.flickr.com/groups. Select “Search Groups” from the drop down menu under the Groupstab:
 
- Next type the group you like to find. For example, you can type Paris, New York, Big Ben and so on. When you click Search, you will see a list of groups interested in that area. For example, when you search for a “New York” group, you will see a list like this (in the beta version of the “new groupsexperience”):
 


 




Click a group, for example, “New York Holiday” and you will see:
 



This is agroup.


- Each group has an ID. To find the group id, copy the URL for the group from the Web browser (in our example, it is https://www.flickr.com/groups/nyholiday/ ). Next, go to http://idgettr.com/ , paste in the link as shown below and select“Find”:



- Notice the group id for this “New York Holiday” group:74919583@N00.


- Getting started with flickr tables

   In YQL console, on the left panel, under Data Tables, see the entryflickr:


- Click flickr to expand, you will see a list of all flickr tables available to you:
 



 


- Forcscipresentation2:
API key:64c914c0bdd6003c38a18bb6ceae5f38 Secret key:282635497b1d2628
User name:cscipresentation2
 Screen name: csci
User id:92894228@N02


	The flickr.photos.searchtable

- This is a very important and usefultable.
SELECT * FROM flickr.photos.search WHERE api_key="---" and text="---" Example:
SELECT * FROM flickr.photos.search WHERE api_key="64c914c0bdd6003c38a18bb6ceae5f38" and text="tajmahal"

- Note: This gives a weird output.  The output will contain lines likethis:
<photo farm="9" id="8453030675" isfamily="0" isfriend="0" ispublic="1" owner="88755760@N06" secret="a6f2c58d48" server="8243" title="Around theWorld"/>
 




	The flickr.groups.infotable

- This retrieves information about thegroup.

SELECT * FROM flickr.groups.info WHERE api_key="---" andgroup_id="---"

- Example:
SELECT * FROM flickr.groups.info WHERE api_key="64c914c0bdd6003c38a18bb6ceae5f38" andgroup_id="74919583@N00"

This retrieves the information about the group “New YorkHoliday”.

	The flickr.groups.pools.photostable

- Returns a list of pool photos for a given group.

SELECT * FROM flickr.groups.pools.photos WHERE api_key="---" andgroup_id="---"


- Example:
SELECT * FROM flickr.groups.pools.photos WHERE api_key="64c914c0bdd6003c38a18bb6ceae5f38" andgroup_id="74919583@N00"

	The flickr.people.findbyusernametable

- Returns a user's flicker id, given theirusername.

SELECT * FROM flickr.people.findbyusername WHERE api_key="---" andusername="---"

- Example:
SELECT * FROM flickr.people.findbyusername WHERE api_key="64c914c0bdd6003c38a18bb6ceae5f38" and username="Peppersalt"


	The flickr.people.info2table

- Gets information about auser.

SELECT * FROM flickr.people.info2 WHERE api_key="---" anduser_id="---"




 
- Example:

SELECT * FROM flickr.people.info2 WHERE api_key="64c914c0bdd6003c38a18bb6ceae5f38" anduser_id="42101521@N06"

	The flickr.people.publicphotostable
- This retrieves a list of public photos for the given user.

SELECT * FROM flickr.people.publicphotos WHERE api_key="---" anduser_id="---"

SELECT * FROM flickr.people.publicphotos WHERE api_key="64c914c0bdd6003c38a18bb6ceae5f38" anduser_id="92894228@N02"

	The flickr.photos.exiftable

- This retrieves a list of EXIF/TIFF/GPS tags for a given photo.


SELECT * FROM flickr.photos.exif WHERE photo_id=”---“ andapi_key=”---“

- Example:
SELECT * FROM flickr.photos.exif WHERE photo_id=”92894228@N02/8444283079” and api_key=”64c914c0bdd6003c38a18bb6ceae5f38”
	The flickr.photos.interestingnesstable
This returns the list of interesting photos for the most recent day. SELECT * FROM flickr.photos.interestingness WHEREapi_key="---"

- Example:
SELECT * FROM flickr.photos.interestingnessWHERE api_key="64c914c0bdd6003c38a18bb6ceae5f38"

	The flickr.photos.recenttable
- This returns a list of the latest public photos uploaded toflickr. SELECT * FROM flickr.photos.recent WHEREapi_key="---"

- Example:
SELECT * FROM flickr.photos.recent WHERE api_key="64c914c0bdd6003c38a18bb6ceae5f38"





	The flickr.placestable
- This return a list of place IDs, latitude and longitude for the querystring.


SELECT * FROM flickr.places WHERE query="---" andapi_key="---"

- Example:
SELECT * FROM flickr.places WHERE query="New York, NY"and api_key="64c914c0bdd6003c38a18bb6ceae5f38"


##**Weathertable**
- YQL provides only one weather table.

	The weather.forecast table

select * from weather.forecast wherelocation=---
select * from weather.forecast where location=--- AND u=”-“ select * from weather.forecast wherewoeid=---
select * from weather.forecast where woeid=--- ANDu=”-“

- Note: The optional u (units) parameter indicates the degree units for the weather forecast. By default, Yahoo! Weather returns temperature information in degrees Fahrenheit. Usethe u parameter to explicitly specify the degree units in Fahrenheit (f) or Celsius(c).

- Examples:
select * from weather.forecast wherewoeid=2524915
select * from weather.forecast where woeid=2524915 ANDu="c" select * from weather.forecast wherelocation=10598
select * from weather.forecast where location=10598 ANDu="c"


- OtherTables
There are plenty of tables available within Yahoo YQL console which we haven’t presented here.
 

[**NEXT**](https://github.com/sharathvontari/Yahoo-query-language/blob/master/YQL%20Console%20Query%20Builder.md)     

[**BACK TO CONTENTS**](https://github.com/sharathvontari/Yahoo-query-language/blob/master/README.md)

