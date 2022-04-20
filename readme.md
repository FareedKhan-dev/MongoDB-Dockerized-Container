<!DOCTYPE html>
<!-- saved from url=(0027)https://pdf2md.morethan.io/ -->
<html><head><meta http-equiv="Content-Type" content="text/html; charset=UTF-8"><meta name="description" content="Converts PDF files to Markdown."><meta name="keywords" content="PDF, Markdown, converter, online"><link rel="shortcut icon" href="https://pdf2md.morethan.io/favicons/favicon.ico"><link rel="icon" href="https://pdf2md.morethan.io/favicons/favicon.ico">
<link rel="stylesheet" href="stylessheet.css">
</head><body><div id="main"><div data-reactroot=""><div class="container"><div><div></div><hr><div><h4>Assignment: Dockerized MongoDB</h4>
<h4>Name: Fareed Hassan Khan</h4>
<h4>Course: Big Data Analytics</h4>
<h4>Course Code: 60490</h4>
<h4>Project Description</h4>
<pre><code>This project is done on docker container creating a containerized Mongodb environment. Showing all the commands that are required for any naïve user to understand the basics of Mongodb.
</code></pre>
<pre><code>command 1 - 10 shows how to initialize the mongodb environment in docker container along with uploading the user data in the database.
</code></pre>
<pre><code>While the main commands section shows the basics of mongodb. A total of 59 commands has been
used in this assignment containing the topics such as (Aggregation, Replication, Counting,
Condition based search, regex search etc.)
</code></pre>
<hr>
<h4>Dataset Description</h4>
<h6>IMDB movies dataset is collected from Kaggle website. Following is the information about</h6>
<h6>the dataset.</h6>
<pre><code>Element Description
Dataset Filesize 405 Megabytes
Dataset Shape 600,000+ movies
Dataset (Movies Description) International Movies (USA, India, Russia, China etc.)
Dataset File Format Json
Dataset Source Kaggle
Dataset Drive Download Link drive.google...../view
Dataset Kaggle Download Link Kaggle.com/...-movies
</code></pre>
<h6>Each doc contains the following information.</h6>
<pre><code>Element Type Description
Id String (unique) Unique id for each movie
ImdbId String (unique) Unique ImdbId for each movie
Name String Name of the movie
Poster_url String Url of the poster of movie
Year String Released year of the movie
</code></pre>
<pre><code>Certificate String Certificate giving to movieEg. MA- 17 etc
</code></pre>
<pre><code>Runtime String Runtime of the movie^
Genre Array Comedy, Horror etc^
RatingValue String Rating of the movie^
Summary_text String Plot of the movie^
ratingCount Numeric Total number of people giving rating^
Director Object Name of the director along with director id^
Cast Array of Object Cast of the movie^
</code></pre>
<h6>1) docker-compose up -d</h6>
<pre><code>Creating network "mongodb_default" with the default driver
Pulling mongodb (mongo:)...
latest: Pulling from library/mongo
7c3b88808835: Pull complete
48a403577c28: Pull complete
76bbb7dc9013: Pull complete
e81b1e5a386b: Pull complete
7bdc1db49ec9: Pull complete
7b2f602f894c: Pull complete
627a84bea5f4: Pull complete
fc06fa2a9f52: Pull complete
0133c89ee92b: Pull complete
4e990167b745: Pull complete
Digest: sha256:03ef0031c1642df26d9d3efa9d57e24929672e1ae7aba5818227752089adde
Status: Downloaded newer image for mongo:latest
Creating mongodb ... done
</code></pre>
<pre><code>_____________________________________________________________________________________________________________________________
</code></pre>
<h6>2) docker ps</h6>
<pre><code>CONTAINER ID IMAGE COMMAND CREATED STATUS PORTS NAMES
a0f80020ef88 mongo "docker-entrypoint.s..." 27 minutes ago Up 27 minutes 0.0:27017-&gt;27017/tcp Mongodb
</code></pre>
<pre><code>_____________________________________________________________________________________________________________________________
</code></pre>
<h6>3 ) docker exec -it mongodb bash</h6>
<pre><code>root@a0f80020ef88:/#
</code></pre>
<hr>
<h6>4) root@a0f80020ef88:/# cd data/db</h6>
<hr>
<h6>6) mongoimport movies.json -d moviesdb -c moviescollection --jsonArray</h6>
<pre><code>2022 - 03 - 16T05:31:55.147+0000 connected to: mongodb://localhost/
2022 - 03 - 16T05:31:58.147+0000 [##......................] moviesdb.moviescollection 36.4MB/396MB (9.2%)
2022 - 03 - 16T05:32:01.147+0000 [####....................] moviesdb.moviescollection 73.3MB/396MB (18.5%)
2022 - 03 - 16T05:32:04.147+0000 [######..................] moviesdb.moviescollection 110MB/396MB (27.7%)
2022 - 03 - 16T05:32:07.147+0000 [########................] moviesdb.moviescollection 146MB/396MB (36.7%)
2022 - 03 - 16T05:32:10.147+0000 [##########..............] moviesdb.moviescollection 181MB/396MB (45.6%)
2022 - 03 - 16T05:32:16.147+0000 [###############.........] moviesdb.moviescollection 253MB/396MB (63.8%)
2022 - 03 - 16T05:32:19.147+0000 [#################.......] moviesdb.moviescollection 289MB/396MB (72.8%)
2022 - 03 - 16T05:32:22.147+0000 [###################.....] moviesdb.moviescollection 325MB/396MB (81.9%)
2022 - 03 - 16T05:32:25.147+0000 [#####################...] moviesdb.moviescollection 361MB/396MB (91.0%)
2022 - 03 - 16T05:32:28.049+0000 [########################] moviesdb.moviescollection 396MB/396MB (100.0%)
2022 - 03 - 16T05:32:28.049+0000 633719 document(s) imported successfully. 0 document(s) failed to import.
</code></pre>
<h6>7) mongo</h6>
<pre><code>Starting the mongodb inside docker container using “mongo” command.
</code></pre>
<hr>
<h6>8 ) show databases</h6>
<pre><code>admin 0.000GB
config 0.000GB
local 0.000GB
moviesdb 0.199GB
</code></pre>
<pre><code>Explanation: As you can see now our moviedb database has been imported
</code></pre>
<hr>
<h6>9 ) use moviesdb</h6>
<pre><code>switched to db moviesdb
</code></pre>
<hr>
<h6>10) show collections</h6>
<pre><code>moviescollection
</code></pre>
<h2>Main Commands</h2>
<h6>1) Following method retrieves all the documents in the collection.</h6>
<pre><code>db.moviescollection.find()
</code></pre>
<pre><code>{
"_id": "tt0142966",
"ImdbId": "tt0142966",
"name": "Voi juku - mikä lauantai",
"poster_url": "https://m.media-Samazon.com/images/M/MV5BODcWE1ZTEtZ....GdeQXVyMjI0MjMwMzQ@.",
"year": "1979",
...
}
...
</code></pre>
<pre><code>{
"_id": "tt0127981",
"ImdbId": "tt0127981",
"name": "Zdivocelá zeme",
"poster_url": "https://m.media-amazon.com/images/M/MV5BODQQxNSQ...jcxXkEyXkFqcGdeQXVyODYwMjAyNDE@.",
"year": "1997",
...
]
}
</code></pre>
<hr>
<h6>2) findOne() method, that returns only one document</h6>
<pre><code>db.moviescollection.findOne()
</code></pre>
<pre><code>{
"_id" : "tt0142966",
"ImdbId" : "tt0142966",
"name" : "Voi juku - mikä lauantai",
"poster_url" : "https://m.media-
amazon.com/images/M/MV5BODcxMzhkODktYWI5MC00YzE0LWE1ZTEtZjE2 ... MzQ@.",
"year" : "1979",
"certificate" : "",
"runtime" : "81 min",
"genre" : [
"Comedy"
],
"ratingValue" : "4.3",
},
"cast" : [
{
"name" : "Matti Pulliainen",
"name_id" : "nm0700432"
}
]
}
</code></pre>
<h6>3) The following operation counts the documents in a collection of moviesdb</h6>
<pre><code>db.moviescollection.aggregate( [{ $count: "total_number_of_movies" }])
</code></pre>
<pre><code>{ "total_number_of_movies" : 633719 }
</code></pre>
<hr>
<h6>4) Converting ratingValue field to float to make certain operations applicable on it.</h6>
<pre><code>db.moviescollection.find().forEach((d) =&gt; {
d["ratingValue"] = parseFloat(d["ratingValue"]);
db.moviescollection.save(d);
});
</code></pre>
<hr>
<h6>5) Counting movies having ratingValue greater than 9.</h6>
<pre><code>db.moviescollection.aggregate([
{ $match: { ratingValue: { $gt: 9.0 } } },
{ $count: "movies_rating_above_9" },
]);
</code></pre>
<pre><code>{ "movies_rating_above_9" : 2134 }
</code></pre>
<hr>
<h6>6) Counting movies having ratingValue lesser than 6.</h6>
<pre><code>db.moviescollection.aggregate([
{ $match: { ratingValue: { $lt: 6.0 } } },
{ $count: "movies_rating_below_6" },
]);
</code></pre>
<pre><code>{ "movies_rating_below_ 6 " : 116140 }
</code></pre>
<hr>
<h6>7 ) Finding highest rated movie name along with its released year.</h6>
<pre><code>db.moviescollection.find({}, {"name":1, “year”:1}).sort({ratingValue:-1}).limit(1).pretty()
</code></pre>
<pre><code>{ "_id" : "tt1219364", "name" : "Nachtfahrt", "year" : "1965 TV Movie", "ratingValue" : 10 }
</code></pre>
<h6>8 ) Finding lowest rated movie name along with its released year.</h6>
<pre><code>db.moviescollection
.find({ ratingValue: { $gt: 0.0 } }, { name: 1, year: 1, ratingValue: 1 })
.sort({ ratingValue: 1 })
.limit(1)
.pretty();
</code></pre>
<pre><code>{ "_id" : "tt3636012", "name" : "Te wu shuang xiong", "year" : "1991 TV Movie", "ratingValue" : 1 }
</code></pre>
<hr>
<h6>9 ) Finding Information of specific movie.</h6>
<pre><code>db.moviescollection.find(
{ name: "The Dark Knight" },
{ name: 1, ratingValue: 1, year: 1, runtime: 1 }
);
</code></pre>
<pre><code>{ "_id" : "tt0468569", "name" : "The Dark Knight", "year" : "2008", "runtime" : "152 min", "ratingValue" : 9 }
</code></pre>
<hr>
<h6>10 ) Converting year field to numeric to make certain operations applicable on it.</h6>
<pre><code>db.moviescollection.find().forEach((d) =&gt; {
d["year"] = parseFloat(d["year"]);
db.moviescollection.save(d);
});
</code></pre>
<hr>
<h6>11 ) Counting total movies released in year 2008.</h6>
<pre><code>db.moviescollection.aggregate([
{ $match: { year: 2008 } },
{ $count: "total_movies_released_in_2008" },
]);
</code></pre>
<pre><code>{ "total_movies_released_in_2008" : 10520 }
</code></pre>
<hr>
<h6>12 ) Finding the director of specific movie.</h6>
<pre><code>db.moviescollection.findOne(
{ name: "The Dark Knight" }, { director: { name: 1 } }
);
</code></pre>
<pre><code>{ "_id" : "tt0468569", "director" : { "name" : "Christopher Nolan" } }
</code></pre>
<h6>13 ) Finding latest directed movie of Christopher Nolan.</h6>
<pre><code>db.moviescollection.find(
{ "director.name": "Christopher Nolan" },
{ name: 1, year: 1 }.sort({year:-1}).limit(1)
);
</code></pre>
<pre><code>{ "_id" : "tt6723592", "name" : "Tenet", "year" : 2020 }
</code></pre>
<hr>
<h4>14 ) Finding each year total movies that are released or will going to be released.</h4>
<pre><code>db.moviescollection.aggregate([
{ $group: { _id: "$year", count: { $sum: 1 } } },
{ $sort: { _id: -1 } },
{ $limit: 20 },
]);
</code></pre>
<pre><code>{ "_id" : 2028 , "count" : 2 }
{ "_id" : 2027 , "count" : 2 }
{ "_id" : 2026 , "count" : 2 }
{ "_id" : 2025 , "count" : 7 }
{ "_id" : 2024 , "count" : 30 }
{ "_id" : 2023 , "count" : 170 }
{ "_id" : 2022 , "count" : 1498 }
{ "_id" : 2021 , "count" : 8620 }
{ "_id" : 2020 , "count" : 13253 }
{ "_id" : 2019 , "count" : 15073 }
{ "_id" : 2018 , "count" : 15554 }
{ "_id" : 2017 , "count" : 15673 }
{ "_id" : 2016 , "count" : 15724 }
{ "_id" : 2015 , "count" : 14632 }
{ "_id" : 2014 , "count" : 13806 }
{ "_id" : 2013 , "count" : 13346 }
{ "_id" : 2012 , "count" : 13103 }
{ "_id" : 2011 , "count" : 12434 }
{ "_id" : 2010 , "count" : 11364 }
{ "_id" : 2009 , "count" : 11322 }
</code></pre>
<h6>_____________________________________________________________________________________________________________________________</h6>
<h6>15 ) The first ever movie released in which year? (Based on dataset)</h6>
<pre><code>db.moviescollection.aggregate(
[
{ $match: { year: { $ne: NaN } } },
{ $group: { _id: {}, minYear: { $min: "$year" } } }
]
);
</code></pre>
<h6>{ "_id" : { }, "minYear" : 1903 }</h6>
<hr>  
<h6>16 ) Total movies directed by Christopher Nolan.</h6>
<pre>db.moviescollection<br>
.find({ "director.name": "Christopher Nolan" }, { name: 1, year: 1 })<br>
.count();</pre>
<h6>11</h6>

<hr>

<h6>17) Total number of comedy genre movies are?</h6>
<pre>db.moviescollection.find( { genre: { $in: [ 'Comedy' ] } } ).count()</pre>
<h6>108751</h6>
<hr>
<h6>18 ) Highest rated horror movie.</h6>
<p>db.moviescollection.find( { genre: { $in: [ 'Horror' ] } } ).sort({ratingValue:-1}).limit(1).pretty()</p>
<p>{<br>
"_id" : "tt2084851",<br>
"name" : "HorrorscapeS",<br>
"year" : 2010 ,<br>
"ratingValue" : 9.<br>
}</p>
<hr>
<h6>19 ) Converting ratingCount field to numeric to make certain operations applicable on it.</h6>
<p>db.moviescollection.find().forEach((d) =&gt; {<br>
d["ratingCount"] = parseFloat(d["ratingCount"]);<br>
db.moviescollection.save(d);<br>
});</p>
<hr>
<h6>20 ) Finding movie name based on highest number of rating count.</h6>
<p>db.moviescollection.find({}, { name: 1, ratingCount: 1, year: 1 }).sort({ ratingCount: -1 }).limit(1).pretty();</p>
<p>{<br>
"_id" : "tt7671414",<br>
"name" : "Thriller",<br>
"year" : 2018 ,<br>
"ratingCount" : 999<br>
}</p>
<h6>21 ) Finding some certificates assigned to movies.</h6>
<p>db.moviescollection.aggregate([<br>
{ $group: { _id: "$certificate", count: { $sum: 1 } } },<br>
{ $sort: { _id: -1 } },<br>
{ $limit: 20 },<br>
]);</p>
<p>{ "_id" : "X", "count" : 3064 }<br>
{ "_id" : "Unrated", "count" : 3343 }<br>
{ "_id" : "TV-Y7-FV", "count" : 19 }<br>
{ "_id" : "TV-Y7", "count" : 140 }<br>
{ "_id" : "TV-Y", "count" : 107 }<br>
{ "_id" : "TV-PG", "count" : 2674 }<br>
{ "_id" : "TV-MA", "count" : 2597 }</p>
<h5>...</h5>
<p>{ "_id" : "PG", "count" : 5527 }<br>
{ "_id" : "Open", "count" : 12 }<br>
{ "_id" : "Not Rated", "count" : 29279 }<br>
{ "_id" : "NC-17", "count" : 65 }<br>
{ "_id" : "MA-17", "count" : 3 }<br>
{ "_id" : "MA-13", "count" : 1 }</p>
<hr>
<h6>22 ) Counting missing data in ratingValue field.</h6>
<p>db.moviescollection.find({ratingValue:NaN}).count()</p>
<h6>352710</h6>
<hr>
<h6>23 ) Counting missing data in year field.</h6>
<p>db.moviescollection.find({year:NaN}).count()</p>
<h6>82707</h6>
<hr>
<h6>24 ) Counting movies containing no plot on IMDB website.</h6>
<p>db.moviescollection.find({summary_text:"Add a Plot"}).count()</p>
<h6>286046</h6>
<h6>25 ) Finding top 10 movies based on longest runtime.</h6>
<p>db.moviescollection<br>
.find({}, { _id: 0, runtime: 1, name: 1, year: 1 })<br>
.sort({ runtime: -1 });</p>
<p>{ "name" : "Mystrio (Uno... dos... tres pilyos!)", "year" : 1998 , "runtime" : "999 min" }</p>
<p>{ "name" : "His Last Stand", "year" : NaN, "runtime" : "990 min" }<br>
{ "name" : "The Viking Who Became a Bigamist", "year" : 1969 , "runtime" : "99 min" }</p>
<p>{ "name" : "Schloß Gripsholm", "year" : 1963 , "runtime" : "99 min" }</p>
<p>{ "name" : "Lemak Kampung Santan", "year" : 2013 , "runtime" : "99 min" }</p>
<p>{ "name" : "Death Is No Escape", "year" : 2012 , "runtime" : "99 min" }</p>
<p>{ "name" : "Elvira's Movie Macabre: The Devil's Wedding Night", "year" : 1981 , "runtime" : "99 min" }<br>
{ "name" : "Window of Opportunity", "year" : 2015 , "runtime" : "99 min" }</p>
<p>{ "name" : "Social Norm", "year" : 2016 , "runtime" : "99 min" }</p>
<hr>
<h6>26 ) Finding top 10 movies based on shortest runtime.</h6>
<p>db.moviescollection.aggregate([<br>
{ $unwind: "$name" },<br>
{ $match: { runtime: { $ne: "" } } },<br>
{ $group: { _id: "$name", runtime: { $min: "$runtime" } } },<br>
{ $project: { _id: 0, name: "$_id", runtime: 1 } },<br>
{ $sort: { runtime: 1 } },<br>
{ $limit: 10 },<br>
]);</p>
<p>{ "runtime" : "1 min", "name" : "Arnold Palmer's Restaurant - The Experience Continues" }</p>
<p>{ "runtime" : "1 min", "name" : "My Little Pony: Happy Birthday to You!" }</p>
<p>{ "runtime" : "1 min", "name" : "Sofia the First- Dear Sofia" }</p>
<p>{ "runtime" : "1 min", "name" : "OneDex Commercial" }</p>
<p>{ "runtime" : "1 min", "name" : "Car Thief Allstate Mayhem" }</p>
<p>{ "runtime" : "1 min", "name" : "The International La Quinta Arts Festival" }</p>
<p>{ "runtime" : "1 min", "name" : "Beauty Service Commercial for SRIS Home Expert Services" }</p>
<p>{ "runtime" : "1 min", "name" : "ATA Martial Arts Fitness Kickboxing Commercial 2020" }</p>
<p>{ "runtime" : "1 min", "name" : "Friends for Change - Nature-Environment" }</p>
<p>{ "runtime" : "1 min", "name" : "Apple: Here's to the Crazy Ones" }</p>
<h6>27 ) Inserting a new data (i.e., movie) in moviescollection.</h6>
<p>db.moviescollection.insertOne( { name: "My First Movie", year: 2022 } );</p>
<p>{<br>
"acknowledged" : true,<br>
"insertedId" : ObjectId("62346717da0bb7fd47496dcb"<br>
}</p>
<hr>
<h6>28 ) Finding the newly inserted movie.</h6>
<p>db.moviescollection.find({name:"My First Movie", year:2022})</p>
<p>{ "_id" : ObjectId(" 6 2346717da0bb7fd47496dcb"), "name" : "My First Movie", "year" : 2022 }</p>
<hr>
<h6>29 ) Updating the year from 2022 to 2021 of newly inserted movie.</h6>
<p>db.moviescollection.updateOne({name: "My First Movie", year:2022}, {$set:{year: 2021 }})</p>
<p>{ "acknowledged" : true, "matchedCount" : 1 , "modifiedCount" : 1 }</p>
<hr>
<h6>30 ) Finding the updated data of newly inserted movie.</h6>
<p>db.moviescollection.find({name:"My First Movie", year:2022})</p>
<p>{ "_id" : ObjectId(" 6 2346717da0bb7fd47496dcb"), "name" : "My First Movie", "year" : 2021 }</p>
<hr>
<h6>31 ) Replacing the name of the newly inserted movie.</h6>
<p>db.moviescollection.replaceOne(<br>
{ name: "My First Movie", year: 2022 },<br>
{ name: "My Movie new", year: 2022 }<br>
);</p>
<p>{<br>
"acknowledged" : true,<br>
"matchedCount" : 1 ,<br>
"modifiedCount" : 1<br>
}</p>
<h6>32 ) Finding the updated data of newly inserted movie.</h6>
<p>db.moviescollection.find({name:"My Movie new", year:202 1 })</p>
<p>{</p>
<p>"_id" : ObjectId(" 6 2346717da0bb7fd47496dcb"),<br>
"name" : "My Movie new",<br>
"year" : 2021<br>
}</p>
<hr>
<h6>33 ) Deleting the newly inserted movie.</h6>
<p>db.moviescollection.deleteOne({name:"My Movie new", year:202 1 })</p>
<p>{</p>
<p>"acknowledged" : true,</p>
<p>"deletedCount" : 1</p>
<p>}</p>
<hr>
<h6>34 ) Checking if deleted data exist or not?</h6>
<p>db.moviescollection.findOne({name:"My Movie new", year:202 1 })</p>
<p>null</p>
<hr>
<h6>35 ) Inserting many movies with single command (insertMany).</h6>
<p>db.moviescollection.insertMany( [{ name: "movie 1"}, { name: "movie 2"}, { name: "movie 3"}]);</p>
<p>{</p>
<p>"acknowledged" : true,</p>
<p>"insertedIds" : [</p>
<p>ObjectId(" 6 2347f1bda0bb7fd47496dcc"),</p>
<p>ObjectId("62347f1bda0bb7fd47496dcd"),<br>
ObjectId("62347f1bda0bb7fd47496dce")</p>
<p>]</p>
<p>}</p>
<h6>36 ) updating all movies years from 2021 to 2022 with name of “fareed movies”.</h6>
<p>db.moviescollection.updateMany( [{ name: "fareed movies"}, {$set: {year: 2022 }]);</p>
<p>{ "acknowledged" : true, "matchedCount" : 1 , "modifiedCount" : 1 }</p>
<hr>
<h6>37 ) Deleting all movies with name of “fareed movies”.</h6>
<p>db.moviescollection.deleteMany( [{ name: "movies_of_fareed"}]);</p>
<p>{<br>
"acknowledged" : true,<br>
"deleteCount" : 3<br>
}</p>
<hr>
<h6>38 ) Let’s view all the indexes in the moviescollection using the following command.</h6>
<p>db.moviescollection.getIndexes()</p>
<p>[ { "v" : 2 , "key" : { "_id" : 1 }, "name" : "<em>id</em>" } ]</p>
<hr>
<h6>39 ) Making ImdbId as an index to retrieve data faster.</h6>
<p>db.moviescollection.ensureIndex({ImdbId:1})</p>
<p>{<br>
"createCollection": false,</p>
<p>"numIndexesbefore": 1 ,</p>
<p>"numIndexesafter": 1 ,</p>
<p>"ok": 1</p>
<p>}</p>
<h6>41 ) dropping the index (ImdbId).</h6>
<p>db.moviescollection.dropIndex({ImdbId:1})</p>
<p>{<br>
"nIndexesWas": 2 ,<br>
"ok": 1<br>
}</p>
<hr>
<h6>42 ) Displaying only the second doc skipping the first doc.</h6>
<p>db.moviescollection.find().limit(1).skip(1)</p>
<p>{<br>
"_id": "tt0142887",<br>
"ImdbId": "tt0142887",<br>
"name": "Syöksykierre",<br>
"poster_url": "https://m.media-<br>
amazon.com/images/M/MV5BMTA3YTQ3N2ItMGQ4NS00MjFjLTgxNjEtMTYxN2Q4ZWEzZjdlXkEyXkFqcGdeQXV<br>
yMzU0NzkwMDg@.",</p>
<h2>...</h2>
<p>"ratingValue": 5.2,<br>
"summary_text": "Add a Plot",<br>
"ratingCount": 66 ,<br>
"director": { "name": "Tapio Suominen", "name_id": "nm0839412" },<br>
"cast": [<br>
{ "name": "Kimmo Liukkonen", "name_id": "nm0515070" },<br>
{ "name": "Markku Toikka", "name_id": "nm0865647" },<br>
{ "name": "Kai Honkanen", "name_id": "nm0393337" },<br>
{ "name": "Albert Liukkonen", "name_id": "nm0515069" }<br>
]<br>
}</p>
<hr>
<h6>43 ) Displaying all the docs but skipping the first one.</h6>
<p>db.moviescollection.find({}, {name:1}).skip(1)</p>
<p>{ "_id" : "tt0142887", "name" : "Syöksykierre" }<br>
{ "_id" : "tt0142383", "name" : "Le huitième jour" }<br>
{ "_id" : "tt0144999", "name" : "Isaia, horeve" }<br>
{ "_id" : "tt0142346", "name" : "Half Way to Hell" }</p>
<h1>...</h1>
<p>{ "_id" : "tt0127981", "name" : "Zdivocelá zeme" }<br>
{ "_id" : "tt0128557", "name" : "Society Affairs" }</p>
<h6>44 ) Counting movies based on ratingValue.</h6>
<p>db.moviescollection.aggregate([<br>
{ $group: { _id: "$ratingValue", count: { $sum: 1 } } },<br>
{ $sort: { _id: -1 } },<br>
{ $limit: 20 }<br>
]);</p>
<p>{ "_id" : 10 , "count" : 151 }</p>
<p>{ "_id" : 9.9, "count" : 37 }</p>
<p>{ "_id" : 9.8, "count" : 88 }</p>
<p>{ "_id" : 9.7, "count" : 85 }<br>
{ "_id" : 9.6, "count" : 129 }</p>
<h4>...</h4>
<p>{ "_id" : 8.5, "count" : 1410 }<br>
{ "_id" : 8.4, "count" : 1659 }</p>
<p>{ "_id" : 8.3, "count" : 1699 }</p>
<p>{ "_id" : 8.2, "count" : 2414 }</p>
<p>{ "_id" : 8.1, "count" : 2234 }</p>
<hr>
<h6>45 ) Output all movies posters URLs in an array grouped by ratingValue.</h6>
<p>db.moviescollection.aggregate([<br>
{ $group: { _id: "$ratingValue", count: { $push: “$poster_url” } } },<br>
{ $sort: { _id: -1 } },<br>
{ $limit: 20 }<br>
]);</p>
<p>{</p>
<p>"_id": 10 ,</p>
<p>"count": [</p>
<p>"https://m.media-amazon.com/images/S/sash/NapCxx-VwSOJtCZ.",</p>
<p>"https://m.media-amazon.com/images/S/sash/NapCxx-VwSOJtCZ.",</p>
<p>"https://m.media-amazon.com/images/S/sash/NapCxx-VwSOJtCZ.",<br>
"https://m.media-amazon.com/images/S/sash/NapCxx-VwSOJtCZ.",</p>
<h3>...</h3>
<p>"https://m.media-amazon.com/images/M/MV5...MTc2XkEyXkFqcGdeQXVyNjk3ODkyODQ@.",</p>
<p>"https://m.media-amazon.com/images/S/sash/...wSOJtCZ.",</p>
<p>"https://m.media-amazon.com/images/M/MV... 00YmY0LWE4NDUtOjY1ODk@.",</p>
<p>"https://m.media-amazon.com/images/S/sash/NapCxx-VwSOJtCZ.",</p>
<p>"https://m.media-amazon.com/images/S/sash/NapCxx-VwSOJtCZ."<br>
]</p>
<p>}</p>
<h6>46 ) Replicating the movies database in a separate mongo container.</h6>
<p>My mongodb instance name is f05e306624ac and it is running on port 27017. To add this instance to<br>
replica set, I used the command rs.add() in Mongo client. Replacing the host name and port number.</p>
<blockquote>
<p>rs.add(HOST_NAME:PORT)</p>
</blockquote>
<blockquote>
<p>rs.add(f05e306624ac : 27017)</p>
</blockquote>
<hr>
<h6>47 ) Finding all the movies name having director name contains “Ch”.</h6>
<blockquote>
<p>db.moviescollection.find({"director.name":{$regex:"Ch"}}).limit( 2 )</p>
</blockquote>
<p>{<br>
"_id": "tt0117414",<br>
"ImdbId": "tt0117414",<br>
"name": "Qi yi lu cheng: Zhen xin ai sheng ming",<br>
"poster_url": "https://m.media-amazon.com/images/M/MV5BMjExNjUxNDc3OV5BMl5BanBnXkFtZTgwMDUwMzgwMzE@.",</p>
<h5>...</h5>
<p>"director": { "name": "Leung Chun 'Samson' Chiu", "name_id": "nm0158409" },<br>
"cast": [<br>
{ "name": "Andy Lau", "name_id": "nm0490489" },</p>
<h6>...</h6>
<p>]<br>
}</p>
<h4>...</h4>
<p>{<br>
"_id": "tt0112821",<br>
"ImdbId": "tt0112821",<br>
"name": "Deadline for Murder: From the Files of Edna Buchanan",</p>
<h6>...</h6>
<p>"director": { "name": "Joyce Chopra", "name_id": "nm0159154" },<br>
"cast": [<br>
{ "name": "Elizabeth Montgomery", "name_id": "nm0000548" },<br>
{ "name": "Yaphet Kotto", "name_id": "nm0001433" },<br>
{ "name": "Audra Lindley", "name_id": "nm0511964" },<br>
{ "name": "Joe Flanigan", "name_id": "nm0281167" }<br>
]<br>
}</p>
<h6>48 ) Finding all the movies having names containing “Dark” in it.</h6>
<blockquote>
<p>db.moviescollection.find({"name":{$regex:"Dark"}}).limit(2)</p>
</blockquote>
<p>{<br>
"_id": "tt2473732",<br>
"ImdbId": "tt2473732",<br>
"name": "It's Dark Here"</p>
<h4>...</h4>
<p>"director": { "name": "Adam Coplan", "name_id": "nm3641195" },<br>
"cast": [<br>
{ "name": "Bubba Lewis", "name_id": "nm0506991" },<br>
]<br>
}</p>
<h4>...</h4>
<p>{<br>
"_id": "tt2081299",<br>
"ImdbId": "tt2081299",<br>
"name": "Level 26: Dark Revelations",<br>
"poster_url": "https://m.media-amazon.com/images/M/MV5BODA4ODk0NDgzMV5BMl5BanBnXkFtZTcwNzAyNzIyNw@@.",</p>
<h5>...</h5>
<p>"cast": [<br>
{ "name": "Dave Baez", "name_id": "nm0651104" },<br>
]<br>
}</p>
<hr>
<h6>49 ) Finding all the movies having names starting with “Dark”.</h6>
<blockquote>
<p>db.moviescollection.find({"name":{$regex:"^Dark"}}).limit(2)</p>
</blockquote>
<p>{<br>
"_id": "tt2473732",<br>
"ImdbId": "tt2473732",<br>
"name": "Dark Satanic Magick"</p>
<h4>...</h4>
<p>"director": { "name": "Adam Coplan", "name_id": "nm3641195" },<br>
"cast": [<br>
{ "name": "Bubba Lewis", "name_id": "nm0506991" },<br>
]<br>
}</p>
<h4>...</h4>
<p>{<br>
"_id": "tt2081299",<br>
"poster_url": "https://m.media-amazon.com/images/M/MV5BODA4ODk0NDgzMV5BMl5BanBnXkFtZTcwNzAyNzIyNw@@.",</p>
<h5>...</h5>
<p>"cast": [<br>
{ "name": "Dave Baez", "name_id": "nm0651104" },<br>
] }</p>
</div></div></div></div><nav class="navbar navbar-default"><div class="container"><div class="navbar-header"><p class="navbar-text">This is a offline tool, your data stays locally and is not send to any server!</p></div><div class="navbar-collapse collapse"><p class="navbar-text navbar-right"><a href="https://github.com/jzillmann/pdf-to-markdown/issues" target="_blank">Feedback &amp; Bug Reports</a></p></div></div></nav></div></div></body></html>