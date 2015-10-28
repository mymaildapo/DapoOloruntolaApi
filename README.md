# BookProject
** by Dapo Oloruntola **
Here are a few short sentences about my project.
In the next 4 weeks, by November 18th 2015. I will be building a d3 visualization website. My project is going to contain three data in JSON. The data is about how often people use the computer if they do and how often they use the internet.if they don't use either it is also included in the data.
I am going to create an API that provide a single interface through which the two datasets can be queried together, in a way that makes sense.
example I am going to query the API when last did someone use a Computer or used the Internet by Age Group, Frequency of Use, Year and Statistic from year 2007 to 2014) and are they connected to the internet or they are not.

My project is going to feature d3 visualization .The web pages is going to show pictures and when the user mouse over the picture it going to give the API query Result.

## Datasets 

When Persons last used a Computer or used the Internet by Age Group, Frequency of Use, Year and Statistic from year 2007 to 2014)
http://www.cso.ie/webserviceclient/DatasetDetails.aspx?id=ICA05

When Persons last used a Computer or used the Internet by Region, Frequency of Use, Year and Statistic from year 2007 to 2014
http://www.cso.ie/webserviceclient/DatasetDetails.aspx?id=ICA07

Households with Computer connected or not connected to the Internet by Type of Internet Connection, Year and Statistic from year 2007 to 2014
http://www.cso.ie/webserviceclient/DatasetDetails.aspx?id=ICA27

## How to Query the API
example:

var express = require('express');
var sqlite3 = require('sqlite3').verbose();
var fs = require('fs');

var diamond = JSON.parse(fs.readFileSync('DapoDataset.json','utf8'))

var db = new sqlite3.Database(':memory:');
db.serialize(function() {
  db.run('CREATE TABLE internetTb (id INTEGER PRIMARY KEY AUTOINCREMENT, male TEXT, female TEXT, total REAL)');
  var stmt = db.prepare('INSERT INTO internetTb (male,female, total) VALUES (?,?,?)');
  for (var i = 0; i < internetTb.length; i++) {
      stmt.run(diamond[i].male
               , internetTb[i].female
               , internetTb[i].total      
              );
  }
## Example use of the API
example:
var app = express();
app.get('/', function(req, res) {
  res.send("This is the Dapo API.");
});

var server = app.listen(8000);

## References
https://gist.github.com/ianmcloughlin/0c98c0869d4514b5283d