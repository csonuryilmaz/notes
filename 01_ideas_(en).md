## Ideas

Sometimes while watching a conference video, attending a meetup, listening a podcast, reading a book or talking with someone on a topic; I came up with new ideas. If I don't jot down them to somewhere, they will be forgotten.
Yes, this documentation contains those ideas.

##### SQL to MongoDB Translator

On 16.12.2016, I attended a MongoDB workshop. While we were doing tasks, I stuck at aggregations syntax. Although I was familiar with map/reduce functions and aggregations are one step forward of that, it was difficult for me to aggregations queries. Then I realized that when I try to solve the task with SQL syntax, it was very very easy.

So I came up with this idea. If there exists a tool which translates SQL queries to MongoDB query syntax, I think it will help people to warm-up MongoDB syntax and boost their learning curve. Reading documentation and trying was very slow and inefficient for me. But I can think in SQL syntax, do translation, study the output MongoDB query and examine results by running that query. By this way I can quickly map its syntax to mine known structures.

I have made a quick search. As far as I know, there are two free services:
* [QueryMongo](http://www.querymongo.com/)
* [SqlToMongo](http://klaus.dk/sqltomongodb/)

First one is old. Doesn't support aggregations syntax. Second one is incomplete. There are also commercial tools. But they are proprietary software. So out of my scope.

With quick search, I have found these web resources. It could be a good starting point.

* [SQL to MongoDB Mapping Chart](https://docs.mongodb.com/manual/reference/sql-comparison/)
* [MySQL to MongoDB Query Translator](https://blog.rjmetrics.com/2012/12/12/mysql-to-mongodb-query-tanslator/)
* [Is there a tool that lets me do sql-like queries on MongoDB?](https://www.quora.com/Is-there-a-tool-that-lets-me-do-sql-like-queries-on-MongoDB)
* [SQL to Mongo Query Translator (querymongo.com)](https://news.ycombinator.com/item?id=4909799)
* [SlamData](https://slamdata.com/get-slamdata/)
* [Teiid](http://teiid.jboss.org/)
