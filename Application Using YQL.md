#**Developing Web applications using YQL and Web services**
- We have seen how to use YQL and pre-defined tables to obtain results from Yahoo! Web services in the YQL console (or even a Web browser by copying and pasting the REST URL in a browser address). This kind of use is restrictive – to use this the user needs the YQL console.

- We will see how to create a simple Web application that retrieves data from Web services and displays it in a browser – the user does not need YQL console. We need all we have learnt to develop the Web application. Once, it is developed and deployed, it is just a Web application. This kind of application can be incorporated into your Website.

- We will see an example of the steps involved in developing a Web application to retrieve data from Web service.

- Example of an application
- This application uses Flickr Web service. To use Flickr Web service, we needa Flickr API key.
  
- Step 1: In YQL console, give the YQLstatement,
SELECT * FROM flickr.photos.search WHERE api_key="64c914c0bdd6003c38a18bb6ceae5f38" andtext="Paris"
  
This retrieves Paris photos.  By default it retrieves 10photos.

- Step 2: Study the result in theconsole.
This gives a weird output.  The result looks likethis:

<photo farm="8" id="15907206802" isfamily="0" isfriend="0" ispublic="1" owner="127003880@N05"secret="fa408f39bb" server="7481" title="biserica goticaParis"/>
<photo farm="8" id="15907208142" isfamily="0"isfriend="0" ispublic="1" owner="127003880@N05"secret="555c3e3c1e" server="7542" title="Sacre-Coerparis"/>
<photo farm="8" id="15907102942" isfamily="0" isfriend="0" ispublic="1" owner="48011064@N08" secret="cb7cc925f6" server="7466" title="Paris by night - ChampsElysées"/>
<photo farm="8" id="15719966978" isfamily="0" isfriend="0" ispublic="1" owner="48011064@N08" secret="e8a43a111e" server="7524" title="Paris by night - ChampsElysées"/>
<photo farm="8" id="15905759901" isfamily="0" isfriend="0" ispublic="1" owner="48011064@N08" secret="3896de2782" server="7520" title="Paris by night - ChampsElysées"/>
<photo farm="9" id="15907804065" isfamily="0"isfriend="0" ispublic="1" owner="70599016@N00" secret="1698ace459" server="8607" title="Winged Victory ofSamothrace"/>
<photo farm="9" id="15288039593" isfamily="0" isfriend="0" ispublic="1" owner="48011064@N08" secret="b128dd54b4" server="8597" title="Paris by night - ChampsElysées"/>
<photo farm="8" id="15905441481" isfamily="0" isfriend="0" ispublic="1" owner="48011064@N08" secret="564eba8c2d" server="7550" title="Paris by night - Arc deTriomphe"/>
<photo farm="8" id="15907624725" isfamily="0" isfriend="0" ispublic="1" owner="48011064@N08" secret="cf6350899b" server="7478" title="Paris by night - ChampsElysées"/>
<photo farm="8" id="15288139483" isfamily="0"isfriend="0" ispublic="1" owner="48011064@N08" secret="c64b7ae3e9" server="7527" title="Paris by night - LaConcorde"/>


We need values of some of these attributes to actually retrieve the photos.

To construct the URL to the actual photo, we need the values of these attributes from the <photo> element: farm , id, server and secret.

- Example:
- Consider the following <photo> element:

<photo farm="8"
id="15907208142"
isfamily="0"
isfriend="0"
ispublic="1"
owner="127003880@N05"
secret="555c3e3c1e"
server="7542"
title="Sacre-Coerparis"/>

Notice the values of the attributes farm , id, server and secret: 
farm =8
id =15907208142
server =7542
secret=555c3e3c1e http://farm8.staticflickr.com/7542/15907208142_555c3e3c1e_m.jpg

The letter m specifies Small, 240 on longest side sizephoto.


- Step 3: Copy the REST Query URL.  Here itis:

https://query.yahooapis.com/v1/public/yql?q=select%20*%20from%20flickr.photos.search
%20where%20api_key%3D%2264c914c0bdd6003c38a18bb6ceae5f38%22%20and%20text
%3D%22Paris%22&diagnostics=true


- Just to see the output, we can open this link in a browser.


 


- Step 4: The output is an XML document. Let us process this using DOM techniques in JavaScript. 
And then we have processed nodes using the xmlDocobject.

The important part of code is passing the REST query as a parameter to the xhttp.open() function.

<scripttype="text/javascript"> functionloadXMLDoc()
{
xhttp=new XMLHttpRequest();
xhttp.open("GET","https://query.yahooapis.com/v1/public/yql?q=SELECT%20*%20FROM%20flickr.photos.search%20WHERE%20api_key%3D%2264c914c0bdd6003c38a18bb6 ceae5f38%22%20and%20text%3D%22Paris%22&diagnostics=true",false);
xhttp.send();
returnxhttp.responseXML;
}
</script>

- The call to the function now is just,xmlDoc=loadXMLDoc(); 
- In our JavaScript program, let us access the <photo> element and its attribute values.We
need these values to construct the actual photo URL.(Study the output in the YQLconsole). Here is the JavaScript code which accesses the <photo> element and its attribute values.

photoNodes=xmlDoc.getElementsByTagName("photo"); for (var i = 0; i < photoNodes.length;i++)
{
var farm = photoNodes[i].getAttribute("farm");
var server =photoNodes[i].getAttribute("server");
var id =photoNodes[i].getAttribute("id");
var secret =photoNodes[i].getAttribute("secret");
}









- Step 5: After retrieving the values of the farm, server, id and secret attribute valuesfor each photo, we will construct the actual URL for the photo .

- The following code adds the photo to the Webpage :


var img = newImage();
img.src ='https://farm'+farm+'.static.flickr.com/'+server+'/'+id+'_'+secret+'.jpg'; document.body.appendChild(img);

Step 6: As before, we like to make the program flexible – not fixed for photos of Paris. We will create a text box to input the photo category.
Completeprogram:

<html>
<head>
<script type="text/javascript"> functionloadXMLDoc(inp)
{
xhttp=newXMLHttpRequest(); 
var URL1="https://query.yahooapis.com/v1/public/yql?q=SELECT%20*%20FROM%20flickr. photos.search%20WHERE%20api_key%3D%2264c914c0bdd6003c38a18bb6ceae5f38%2 2%20and%20text%3D%22";
var URL2=escape(inp);
var URL3 ="%22&diagnostics=true"; varURL=URL1+URL2+URL3;
xhttp.open("GET",URL,false); xhttp.send();
returnxhttp.responseXML;
}
</script>

</head>
<body>
<FORM Name="one" METHOD="GET"ACTION="">
What kind of pictures: <INPUT TYPE="text"Name="kindof"><P>
<INPUT TYPE="button" VALUE="Submit"onClick="invoke()">
</FORM>
<scripttype="text/javascript"> functioninvoke()
{
var kind = document.one.kindof.value; xmlDoc=loadXMLDoc(kind); photoNodes=xmlDoc.getElementsByTagName("photo"); document.write("<p>Number of photos",photoNodes.length); for (var i = 0; i < photoNodes.length;i++)
{
var farm = photoNodes[i].getAttribute("farm"); var server =photoNodes[i].getAttribute("server"); var id =photoNodes[i].getAttribute("id");
 var secret =photoNodes[i].getAttribute("secret");             
 var img = newImage();
img.src ='http://farm'+farm+'.static.flickr.com/'+server+'/'+id+'_'+secret+'.jpg'; document.body.appendChild(img);
}
}
</script>
</body>
</html>


 [**NEXT**](https://github.com/sharathvontari/Yahoo-query-language/blob/master/Conclusion.md)     

[**BACK TO CONTENTS**](https://github.com/sharathvontari/Yahoo-query-language/blob/master/README.md)



 


 


 


