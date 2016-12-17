## MongoDB Workshop Notes

Speaker: ozlerhakan  (github & twitter)

Date:(2016-12-16 Saturday)

### Command-Line Tools

**mongodump:** Export data from mongodb instance.
*   -o: output folder
*   -c: specify collection
*   -q: find by query (json query) then dump output

**mongorestore:** Import dumped data into mongodb instance.

**mongoexport:** Export collection as json/csv format.

**mongoimport:** Import collections from json/csv format.

#### New Features In Version 3.4:

* Read-only Views
* Decimal Data Type
	Better for representation of currency like data.

#### Notes From "mongos" (console)

* show dbs
	List all databases.
* db
	Shows current database.
* use test
	Change current in use database to *test*.
* You can view implementation of methods. For example,
```
> db.student.insert
```
will verbose implementation of *insert* method. Result output is a javascript function.
* update()
	Atomic update. Partial.
* replaceOne()
	Change document completely.
* remove()
	Delete all matched documents.
* deleteOne()
	Delete at most one single documents from matched documents.
* MongoDB supports bulk operations. Bulk insert/update.
* **Aggregations** are like pipelines. $match > $group > $limit > $skip ... vs.
* **Indexes** They are like database indexes on RDBMS or couchbase views. Also indexed can defined compound. (Also supports unique indexes.)
* explain()
	See execution plan for supported methods. For example, find(), aggregate() ... vs.
* MongoDB supports horizontal data sharding. Abstracts shards by **mongos**. It seems like one mongo instance but manages shards internally.

###### Workshop Tasks

**1.** Insert some documents into **exam** collection:
```
db.exam.insert({_id:1,user:{name:"quincy",age:21},exam:54,quizzes:[85,45]})
db.exam.insert({_id:2,user:{name:"jessika",age:22},exam:90,quizzes:[90,90]})
db.exam.insert({_id:3,user:{name:"alix",age:19},exam:25,quizzes:[68,20]})
db.exam.insert({_id:4,user:{name:"tambra",age:21},exam:69,quizzes:[3,13]})
db.exam.insert({_id:5,user:{name:"sow",age:22},exam:82,quizzes:[45,63]})
db.exam.insert({_id:6,user:{name:"joe",age:21},exam:43,quizzes:[39,77]})
```

**2.** Find documents where exam is greater than 54
```
> db.exam.find({"exam":{$gt:54}})
{ "_id" : 2, "user" : { "name" : "jessika", "age" : 22 }, "exam" : 90, "quizzes" : [ 90, 90 ] }
{ "_id" : 4, "user" : { "name" : "tambra", "age" : 21 }, "exam" : 69, "quizzes" : [ 3, 13 ] }
{ "_id" : 5, "user" : { "name" : "sow", "age" : 22 }, "exam" : 82, "quizzes" : [ 45, 63 ] }
```

**3.** Find documents where at least one quiz is equal to or less than 80
```
> db.exam.find({quizzes:{$elemMatch:{$lt:80}}})
{ "_id" : 1, "user" : { "name" : "quincy", "age" : 21 }, "exam" : 54, "quizzes" : [ 85, 45 ] }
{ "_id" : 3, "user" : { "name" : "alix", "age" : 19 }, "exam" : 25, "quizzes" : [ 68, 20 ] }
{ "_id" : 4, "user" : { "name" : "tambra", "age" : 21 }, "exam" : 69, "quizzes" : [ 3, 13 ] }
{ "_id" : 5, "user" : { "name" : "sow", "age" : 22 }, "exam" : 82, "quizzes" : [ 45, 63 ] }
{ "_id" : 6, "user" : { "name" : "joe", "age" : 21 }, "exam" : 43, "quizzes" : [ 39, 77 ] }
```

**4.** Find documents where at least one quiz is equal to or less than 80 AND greater than 46
```
> db.exam.find({quizzes:{$elemMatch:{$lt:80,$gt:46}}})
{ "_id" : 3, "user" : { "name" : "alix", "age" : 19 }, "exam" : 25, "quizzes" : [ 68, 20 ] }
{ "_id" : 5, "user" : { "name" : "sow", "age" : 22 }, "exam" : 82, "quizzes" : [ 45, 63 ] }
{ "_id" : 6, "user" : { "name" : "joe", "age" : 21 }, "exam" : 43, "quizzes" : [ 39, 77 ] }
```

**5.** Find documents where all quizzes are 90 and exam is 90
```
> db.exam.find({exam:90,quizzes:{$all:[90,90]}})
{ "_id" : 2, "user" : { "name" : "jessika", "age" : 22 }, "exam" : 90, "quizzes" : [ 90, 90 ] }
```

**6.** How many documents will return after this query: db.exam.find({user:{age:21}})
```
> returns no result!
User is an embedded object. In order to filter it, we have to use dot notation.
> db.exam.find({"user.age":21})
{ "_id" : 1, "user" : { "name" : "quincy", "age" : 21 }, "exam" : 54, "quizzes" : [ 85, 45 ] }
{ "_id" : 4, "user" : { "name" : "tambra", "age" : 21 }, "exam" : 69, "quizzes" : [ 3, 13 ] }
{ "_id" : 6, "user" : { "name" : "joe", "age" : 21 }, "exam" : 43, "quizzes" : [ 39, 77 ] }
```

**7.**
```
{ "_id" : "Istanbul", "weather" : [ { "year" : 2015, "max" : 40, "min" : -10 }, { "year" : 2014, "max" : 41, "min" : -12 } ] }
{ "_id" : "Ankara", "weather" : [ { "year" : 2015, "max" : 39, "min" : -16 }, { "year" : 2014, "max" : 41, "min" : -19 } ] }
{ "_id" : "Izmir", "weather" : [ { "year" : 2015, "max" : 45, "min" : -1 }, { "year" : 2014, "max" : 48, "min" : -5 } ] }
```
Result:
```
{ "max" : 41, "min" : -19, "city" : "Ankara" }
{ "max" : 41, "min" : -12, "city" : "Istanbul" }
{ "max" : 48, "min" : -5, "city" : "Izmir" }
```
What is the aggregation query that outputs above result?
```
db.task2.aggregate([ {$unwind:"$weather"},
{$group:{_id:"$_id", max:{$max:"$weather.max"}, min:{$min:"$weather.min"}}},
{$project:{city:"$_id",_id:0,max:1,min:1}}, {$sort:{city:1}} ])
```
