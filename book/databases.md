# Database Concepts

## Overview

In this Chapter, we aim to understand
several SQL and NoSQL Databases and how they are useful to developers.

They are two types of Databases:

- SQL
- NoSQL

SQL databases are popularly used to store data in a structured format in form of tables that have relationships and excellent querying capabilities.

NoSQL databases are ideally used to store **very, very large** amounts of data that are fast to access.

We will be learning about these databases, before starting, I want to clarify the terms which will be used:

1. **StartUp Scale Applications:** Applications having less than 10K daily active users
2. **Medium Scale Applications:** Applications having 10K to 100K daily active users
3. **Large Scale Applications:** Applications having more than 100K daily active users
4. **DAU:** DAU stands for Daily Active Users. Daily Active Users are those users who interact with your Application on a Daily Basis.

For First Definition I have used **StartUp** instead of **Small** as it feels better.

## SQL

SQL databases stores structured data in the format of tables. SQL databases form the core database for most applications.

Many SQL databases are there such as SQLite, PostgreSQL, MySQL, and MariaDB, functionality wise all SQL databases are similar. I consider SQLite and PostgreSQL to be 2 databases that will possibly handle use cases of Applications from Startup to Large Scale. All SQL Databases are vertically scalable meaning to scale them you need to rent bigger machines.

**SQLite**

SQLite is a lightweight, yet reliable database.

Due to its reliability, Google added SQLite in Android, so all Android App Developers can use SQLite to store data.

The biggest **selling factor** of SQLite is its **Simplicity**.

For all other databases such as PostgreSQL and MySQL, you will have to spin up a server on your machine, but because SQLite is just a file-based database there is no need for a server. Developing with SQLite will lead to a superior developer experience than PostgreSQL or MySQL.

Regarding SQLite, there is a huge misconception that because it is so simple, it is unsuitable for production.

The creators of SQLite  Database said that they are using SQLite database for their website to handle about 100K Page Hits per day ^1 and each page hit executes 200 statements^2. This translates to 231 SQL executions per second. (200* 100K/86400) which is really more than enough for a StartUp to Medium Scale Application.

In summary, whenever you are below the scale of Medium size Application (less than 100K daily active users), you should use SQLite as the database of choice for greater developer experience. Once you have reached the limits of SQLite, you can easily migrate to more suitable databases like PostgreSQL by following this StackOverflow answer that teaches you how to migrate from SQL to PostgreSQL.

Link: [https://stackoverflow.com/questions/4581727/convert-sqlite-sql-dump-file-to-postgresql](https://stackoverflow.com/questions/4581727/convert-sqlite-sql-dump-file-to-postgresql)


**PostgreSQL**

PostgreSQL is a popular SQL database.

It is ideally used in large-scale applications (more than 100K active users).

It can easily handle Tables having **Billions** of Rows. ^3.

As a Real-World example,

[adyen.com](http://adyen.com/) (a payments platform similar to PayPal) uses Postgres for storing more than 10,000 GB of Data and doing more than 5000 Transactions per second on it. ^4

So, I can conservatively say PostgreSQL can handle databases up to 10,000 GB as proven by [ayden.com](http://ayden.com/).

In Summary, if you have a large-scale app (100K+ users) then PostgreSQL is a great choice for you.

**Important Tools for SQL Development**

**SQLite browser**

If you’re using SQLite a very very important tool you should definitely use is the **SQLite browser,** it helps you visually browse and edit your tables. Pete Morgan and SQLite Browser Team give it away to the community for free. To use it just download it and open a SQL file with it.

Also, A picture is worth 1000 words. Here is the interface of SQLite Browser on my PC :)

![https://raw.githubusercontent.com/Chetan11-dev/system-design/master/images/book/databases/sqlite-screenshot.png](https://raw.githubusercontent.com/Chetan11-dev/system-design/master/images/book/databases/sqlite-screenshot.png)

**CloudSQL**

For Large Scale Applications(>100K Daily Active Users) it is preferable to use a managed SQL Service like Google’s **CloudSQL** for PostgreSQL, it is quite reliable due to Google’s experience in running SQL for several Developers.

CloudSQL is priced at 30$/CPU, 5$/GB Ram. It is double the pricing of a bare VM node, which is fair enough.

![https://raw.githubusercontent.com/Chetan11-dev/system-design/master/images/book/databases/cost-comparision-sql.png](https://raw.githubusercontent.com/Chetan11-dev/system-design/master/images/book/databases/cost-comparision-sql.png)

## NoSQL

NoSQL databases have become popular among developers nowadays.

SQL databases are different from NoSQL as SQL Databases stores data in form of tables, while NoSQL stores data in form of Documents, Key-Value Pairs, Graph Databases, and Wide Column Databases.

Let us learn about the use cases of popular databases. All these popular Databases are horizontally scalable meaning to scale them you need to add more machines.

**ElasticSearch**

ElasticSearch stores data in form of Documents. Elasticsearch is popularly used for text searching. (Think Google)

Searching is an important feature, All Large Applications like StackOverflow, GitHub, Google, Amazon, and Airbnb allow you to search data. Most probably in your StartUp, you need to add a search functionality that will allow users to search for things.

You can easily implement this with Elasticsearch. Elasticsearch is specifically designed for searching data similar to Google Search. Elasticsearch is capable of searching through Billions of Documents in consumer-facing Applications (like GitHub, and Stackoverflow).

Real World Examples of ElasticSearch are as follows,

**GitHub** uses Elasticsearch to implement its Code/Repository search functionality. ^5

**Stack Overflow** uses Elasticsearch for question searching. ^6

**Udemy** uses Elasticsearch for implementing the Course Search Functionality  ^7

**Instacart (an app similar to Amazon)** uses Elasticsearch for implementing the Product Search Functionality. ^8

In summary, whenever you need to search for something use ElasticSearch.

**Redis**

Redis can store data in form of Key-Value Pairs, Sets, Maps of Items, etc. Although it is most popularly used to cache things, The things to be cached are stored in Key Value Pairs.

Redis can also be used for implementing PubSub.

Let’s discuss Caching and PubSub use cases.

Redis has 2 use cases:

- Caching

**Caching**

In Redis, you can store Key Value Pairs which could be used to implement User Session if using Stateful Authentication and creating Page Based Cache like Caching a StackOverflow Question Page.

You can also use Sorted Set, Sorted Set helps create Leader Boards in Games like retrieving the top 10 highest-scoring gamers.

**PubSub**

You can use Redis to implement PubSub use cases like triggering scripts to run based on events.

**Neo4j**

Neo4j stores data in form of a Graph. The syntax of Neo4j is like SQL which is nice as you can use your existing knowledge of SQL.

Neo4j is a database that has very specific use cases like **E-commerce** and **Fraud Detection**.

![https://raw.githubusercontent.com/Chetan11-dev/system-design/master/images/book/databases/neo-4j.jpg](https://raw.githubusercontent.com/Chetan11-dev/system-design/master/images/book/databases/neo-4j.jpg)

**Ecommerce**

The most popular use case of Neo4j in eCommerce is Product Recommendation, In Product Recommendation, you analyze the behavior of previous buyers of a Product to estimate what else the customer will like to buy with the current product.

Walmart uses Neo4j for its Product Recommendation.

With Neo4j you can create Product Recommendation Engines similar to how amazon recommends your Products. ⬇️

**Fraud Detection**

In our world, we have a few people which are awesome (Open Source Contributors, Sikhs who help feed people in need) and a few people who are tough to deal with (Bad Politicians, Bad Companies, Parasitic Schools)

![https://raw.githubusercontent.com/Chetan11-dev/system-design/master/images/book/databases/bought-together.png](https://raw.githubusercontent.com/Chetan11-dev/system-design/master/images/book/databases/bought-together.png)

**Robber Politicians**

Some Robber Politicians, but not all create Shell Companies through their Relatives, and these Politician-owned Companies are given contracts by the Politicians. Using Neo4j you can detect if the Politician's Blood Relation (like any Politician’s Wife’s Uncle) owns the Company being given a Contract.

**Income Tax Evasion**

Some Companies, but not all use Complex Tax Laws which only Lawyers can understand to distribute Companies’ Profits and get them back to the company’s Owner. The Income Tax department can analyze the Bank Statements of these Companies and figure out if the Company’s money getting into Shareholder’s Pockets.

**India’s Parasitic** **School**

In India, some Private School owners force Children to buy Specific Clothing, Books, etc which are owned by the School owners. We can detect these things with Neo4j

Also, this brave Youtuber highlights this problem in detail in the Hindi Language which must watch by all Indians: [https://www.youtube.com/watch?v=az_zvD06DFU](https://www.youtube.com/watch?v=az_zvD06DFU)

**Note for entrepreneurs who want to start a Fraud Detection Company.**

Problems caused by Robber Politicians and Parasitic Schools ultimately harm millions of people all over countries.

Due to the hard work of our Open-Source Brothers, we Developers are sitting on top of these solutions and you have the power to solve this problem.

You may want to help your brother citizens, by solving these problems. To help you in your endeavor here is some advice:

Coding the System is Easy a month of Coding is enough, the most time-consuming part will be to convince Politicians to give Birth certificates, ID cards, Marriage certificates, Company Details, etc, as these will be needed to create the Fraud Detection System. To successfully do that it is best to show the Politicians how Fraud Detection System can prevent fraud practically on a small scale say a city. Once they are convinced, you can roll it Nationwide.

Politicians are most probably not giving so sensitive data to a StartUp. So, I strongly recommend that only medium-scale established companies do this. So, this idea of fraud detection can be best done by a Medium Scale Software Company but is mostly doomed to fail for a StartUp.

**Big Table**

Big Table is a database made by Google to solve its Big Data needs.

Big Table is a wide-column Database. A wide Column has Columns within Columns. Here is a visualization of the Big Table.

Big Table gives you low latency read and writes while handling up to Petabytes (1000TB) of Data. So, it is a very Scalable Database. It is used for massive amounts of Data.

Use cases of BigTable are

**Financial data**, such as transaction histories, stock prices, and currency exchange rates.

**Internet of Things data**, such as usage reports from energy meters and home appliances.

**Time-series data**, such as CPU and memory usage over time for multiple servers.

**Analytics data** such as data collected by apps like Google Analytics.

Google BigTable is an invention of Google, there also exists HBase which is an Open Source alternative to BigTable designed to clone the behavior of BigTable.

Some of the Notable Companies using BigTable are:

**Twitter** uses Bigtable to process 400 Billion Events per Day.^9

**Google** uses BigTable to store data from Google Analytics. Google also stores the web pages it crawls in BigTable. This Data set reacts up to Petabytes ^10

**Cassandra**

Cassandra is a database made by Avinash Lakshman and Prashant Malik from Facebook and Facebook donated it to Apache Foundation. We are grateful to Facebook. Similar to BigTable it is a wide-column Database capable of supporting Petabytes of Data^11.

It can also do 1 Million writes per second^12 which makes it the preferred choice for

- Messaging systems of large-scale applications (>100K Daily Active Users)
- IoT Device that generates lots of data.

Also, **Discord** uses Cassandra to store its user’s messages.

Again, when you are creating a Messaging System for Large Cassandra Applications (>100K DAU) similar to **Discord,** Cassandra is ideal for it.

Still, I will strongly emphasize using PostgreSQL for the messaging system if your app is below the 100K Users mark as PostgreSQL is simpler to implement than Cassandra.

**MongoDB**

MongoDB stores data in form of Documents. It is very popular among JS Developers and is also very easy to start with. It is a multipurpose database owned by 10gen.

MongoDB can scale to up to 10TB of Data^13, similar to PostgreSQL but not more than that.

It is certainly not for Big Data use cases and you should prefer Cassandra or BigTable for that.

Also, **DDiscord**in its initial stages used MongoDB but later moved on to Cassandra as Discord notices that MongoDB was not Scaling^14.

When creating things in MongoDB you will need to learn complex NoSQL paradigms which you don’t need to learn if you simply used SQL.

Also, Scaling SQL is easy, you just need to use CloudSQL and Google will scale it for you, while on the other hand, MongoDB is Complex to Scale.

Some Developers make the argument that MongoDB is easier than SQL.

That is correct only in the case of JavaScript. If you are using Django the easiest framework to make the backend, then Django ORM will make SQL extremely easy for you.

Also, many Instructors on YouTube out of ignorance of other Databases will suggest you use MongoDB. This is the case when you have a Hammer everything looks like a Nail.

In summary, PostgreSQL is a simpler and more developer-friendly alternative to MongoDB, so I recommend PostgreSQL over MongoDB.

## Consumer Advice

You should stay away from Pay per Priced NoSQL Databases like Firestore and DynamoDB.

Databases like Firestore by Google are priced pay-per-read or write. This is because it makes cloud providers more money, rather than if they have been given as pay per node.

For example, below you can see pricing for Firestore.

As per the table, for 1$ you get 100,000 Writes(approx.). The Computer you are reading on now, can do 100,000 SQLite writes in just 2 seconds^15. So why would you pay 1$ for something that can be done in 2 seconds by your PC?

Also, Firestore Forces you to optimize based on reads to save money, while you should be optimizing on creating a simpler architecture.

Also, do not get into the words of google when they say Firestore is very scalable and all of that, as it may be but it is also very expensive.

Coding in a pay-per-read database will cause you to write schema in a way that minimizes cost at expense of complex architecture.

Whatever schema you have in Firestore can be modeled into SQL

Compared to Firestore, open-source options like PostgreSQL are not only more intuitive and easier but also you can run them on pay per node basis, making them quite cheap in long run.

## Summary

Here is the summary,

- **SQLite**: Use it for StartUp and Medium Scale Applications (< 100K Daily Active Users)
- **PostgreSQL**: Use it for Large Scale Applications (less than 100K Daily Active Users) and when SQLite starts underperforming.
- **Redis:** Use it for Caching or PubSub.
- **Elasticsearch:** Use it to implement search functionality
- **MongoDB:** Use PostgreSQL instead of MongoDB as it scales just as well as MongoDB and is way easier to manage for Large Applications than MongoDB
- **BigTable/Cassandra**: Use it for Big Data (Terabytes to Petabytes) of Data
- **Firestore:** Use SQL databases instead of Firestore, they are easier and cost way less.

Lastly, with PostgreSQL, Redis, ElasticSearch, Bigtable, and Cassandra, you can make almost all applications at the scale of StackOverflow, Google, Netflix, etc.

1. [https://www.sqlite.org/whentouse.html](https://www.sqlite.org/whentouse.html)
2. [https://www.sqlite.org/np1queryprob.html](https://www.sqlite.org/np1queryprob.html)
3. [https://pgconf.ru/en/2017/94495F](https://pgconf.ru/en/2017/94495F)
4. [https://www.adyen.com/blog/updating-a-50-terabyte-postgresql-database](https://www.adyen.com/blog/updating-a-50-terabyte-postgresql-database)
5. [https://www.elastic.co/customers/github](https://www.elastic.co/customers/github)
6. [https://meta.stackexchange.com/questions/187431/how-does-stack-overflow-implement-its-search-indexing](https://meta.stackexchange.com/questions/187431/how-does-stack-overflow-implement-its-search-indexing)
7. [https://stackshare.io/udemy/udemy/](https://stackshare.io/udemy/udemy/)
8. [https://stackshare.io/instacart/instacart](https://stackshare.io/instacart/instacart)
9. [https://blog.twitter.com/engineering/en_us/topics/infrastructure/2021/processing-billions-of-events-in-real-time-at-twitter-](https://blog.twitter.com/engineering/en_us/topics/infrastructure/2021/processing-billions-of-events-in-real-time-at-twitter-)
10. [https://static.googleusercontent.com/media/research.google.com/en//archive/bigtable-osdi06.pdf](https://static.googleusercontent.com/media/research.google.com/en//archive/bigtable-osdi06.pdf)
11. [https://www.threatstack.com/blog/scaling-cassandra-lessons-learned](https://www.threatstack.com/blog/scaling-cassandra-lessons-learned)
12. [https://cloudplatform.googleblog.com/2014/03/cassandra-hits-one-million-writes-per-second-on-google-compute-engine.html](https://cloudplatform.googleblog.com/2014/03/cassandra-hits-one-million-writes-per-second-on-google-compute-engine.html)
13. [https://stackoverflow.com/questions/12980389/can-mongodb-handle-tbs-of-data](https://stackoverflow.com/questions/12980389/can-mongodb-handle-tbs-of-data)
14. [https://discord.com/blog/how-discord-stores-billions-of-messages](https://discord.com/blog/how-discord-stores-billions-of-messages)
15. [https://www.sqlite.org/faq.html#:~:text=Actually%2C SQLite will easily do,speed of your disk drive](https://www.sqlite.org/faq.html#:~:text=Actually%2C%20SQLite%20will%20easily%20do,speed%20of%20your%20disk%20drive).