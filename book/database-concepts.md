We will about some important database concepts such as Sharding and CAP Theorem

**What is Sharding in Databases?**

In Database Sharding you divide your databases into smaller parts and spread these small parts across multiple servers. 

The reason to shard your Database is that after certain Terabytes of Data the Database becomes unscalable and slower in returning queries. So, to restore performance, we shared it. 

Many NoSQL Databases such as Redis, Elasticsearch, Cassandra, and BigTable are shared across multiple machines for scalability.  These Databases handle Sharding automatically for you, so you do not need to write any additional code to shard things.

SQL Databases like PostgreSQL can also be shared, but you need to write additional code in your backend framework. Understand that, if you are sharding PostgreSQL, it is advisable to consider the question that should you move tables related to a specific feature to a Big Data Solution like Cassandra.

## Methods of Sharding

NoSQL Databases automatically shard data for you, so here we will only discuss sharding in the context of SQL Databases.

**Hash-Based Sharding**

In hash-based sharding. we use a key such as a user id as input to the hash function. Based on this hash value we find the shard number where you have to store data. 

The shard number may be calculated as follows: 

```python
shard_number = hash(key) % number_of_shards
```

Now, based on this shard\_number you will connect to that database and store data there. 

Here, the drawback is if we want to increase the number of shards, we have to remap keys.

Understand that, Hash-based sharding is quite popular due to its simplicity. NoSQL databases like ElasticSearch internally implement Hash-based sharding.

**Horizontal Sharding**

With this approach, the data is sharded based on rows. 

For example, you have a database with the names of your users. Now if you say that all users starting with name A-M will go to shard 1 and N-Z will go to shard 2. Then that is called Horizontal Sharding.

Here, the drawback is if we want to increase the number of shards, we have to change the range.

**Vertical Sharding**

With this approach, the data is sharded based on columns.

Take the example of a web crawler that stores webpages with their URL and the HTML in a table like so. ⬇️

![](https://raw.githubusercontent.com/Chetan11-dev/system-design/master/images/book/database-concepts/pages.png)

Now if you store the data in 2 shards where, 

shard 1 contains the URL

shard 2 contains the HTML of the page, then it will be called Vertical Sharding ⬇️

![](https://raw.githubusercontent.com/Chetan11-dev/system-design/master/images/book/database-concepts/pages-html.png)

The drawback here is that in your backend you will need to combine data by yourself in your backend which means more complexity and additional latency.

**Directory-Based Sharding**

In Directory-Based Sharding, we map the primary key of a table to a shard\_number, and whenever we want to know where a specific row is stored we query the shard map. 

![](https://raw.githubusercontent.com/Chetan11-dev/system-design/master/images/book/database-concepts/directory-based-sharding.png)

The drawback here is you need to make make an additional query to know the shard data is located which increases the latency. 

In Conclusion, for most use cases where you want to spread your data across multiple servers, you should use hash-based sharding as It is quite easy to implement.

## Cap Theorem
Now, we look at the CAP theorem and how it is useful when designing distributed applications and choosing a SQL or NoSQL Database.

**What is CAP Theorem?**

CAP Theorem is used to make system Developers aware of the trade-offs while designing distributed databases. So developers do not waste time trying to create a solution that just cannot be created.

Just like your life, you have many dreams but can choose only to focus your efforts on fulfilling a few of your dreams. 

Similarly, in a distributed system you can choose **2** attributes out of **3** attributes which are **C**onsistency, **A**vailability, **P**artition Tolerance.

**“CAP” Explained**

Let’s understand 3 attributes of a distributed system.

**Consistency**

Consistency means when data is written to one node, every node in the cluster must give the same data that was written.

**Availability**

Availability means that in event of one or more nodes going down, the other working nodes must continue serving both reads and writes.

**Partition Tolerance**

Partition Tolerance that in event of network disconnection between two nodes (the nodes are up but not connected), the disconnected nodes along with the other working nodes must continue serving both reads and writes. 

Consider an example, let’s say you have a cluster and a network disconnection (or partition) occurs between two nodes so they can’t sync with each other. You have choices:

🔘 make disconnected nodes available to serve reads and writes. If you choose this you give up consistency as disconnected nodes can’t sync with each other.

🔘 consider disconnected nodes shut. If you choose this option you give up availability as disconnected nodes become unavailable.

**Types of Database based on CAP.** 

Based on what attributes a distributed database supports we can classify them into 3 groups:

**CP Databases**

CP databases support only Consistency and Partition Tolerance. Whenever there is a network disconnection in a CP Database, it will make the disconnected nodes unavailable, thereby sacrificing availability. An example of a CP Database is **BigTable**.

In Big Table when network disconnection occurs between two nodes, those two nodes will be considered down.

**AP Databases**

AP databases support only Availability and Partition Tolerance. Whenever there is a network disconnection in an AP Database, the disconnected node will continue serving reads and writes, thereby getting out of sync and giving up consistency. Example of AP Database is **Cassandra** and **ElasticSearch,** 

In Cassandra, if you write data it will become consistent after some seconds. So in Cassandra, you may get an inconsistent response if read data just after writing it to Cassandra

Yet because of lack of consistency, you should not discount Cassandra as Cassandra is a great database because it can support a high volume of writes (millions per second) which is a requirement for large-scale messaging apps like Discord and IoT Device Log Systems.

**CA Databases**

CA databases support only Consistency and Availability.** CA can **never** exist in a **distributed** system because network disconnection will always occur in a system, and when network disconnection occurs you have to either make disconnected nodes unavailable (thereby giving up **Availability**) or make them available (thereby giving up **Consistency** as disconnected nodes can’t sync).


**Summary**

CAP Theorem humbles developers by making them understand that in a distributed system when network disconnection occurs, they can either have Availability or Consistency.

This helps them is making them choose the correct database for their needs.

Also, understand that the CAP theorem is only applicable to distributed databases such as Cassandra, but not to SQL Databases.
