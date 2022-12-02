# Concepts

## Overview

In this article, we will learn about some key features that are common to large-scale applications like StackOverflow, GitHub, etc.

These Key features are Scalability, Availability, Efficiency, and Maintainability

## Scalability

Scalability refers to the capability of the System to make itself grow when there is an increase in demand. For example, if on Diwali Festival the sale on an eCommerce site increases then the system should add more servers to handle the increase in load. This will lead to optimal performance for our users.

Distributes System Scales in Two Ways i.e. Horizontal Scaling and Vertical Scaling.

**Horizontal Scaling**

In Horizontal Scaling, more servers are added to handle the load.

Let us say you are serving your Start-up’s Website with help of **2** Django servers, Due to a surge in number of users, you add **4** more Django Servers which is called Horizontal Scaling. Horizontal Scaling means increases the number of servers to handle additional load.

Many NoSQL Databases such as Cassandra and Google Big Table scale horizontally by adding more nodes. Also, Backend webservers like Python’s Django, and NodeJS’s Nest.JS scale horizontally by adding more nodes.

![](https://raw.githubusercontent.com/Chetan11-dev/system-design/master/images/book/concepts/horizontal-scaling.png)

**Vertical Scaling**

In Vertical Scaling, you make your Server more Powerful.

Let’s say for your start-up’s website you are using a PostgreSQL Database as your Backend Database. Then due to the increase in several users your database queries are taking a long time and failing, to fix that you add more ram and cores to the Database server. This is called Vertical Scaling. In Vertical Scaling, you add more Ram and CPU to your server.

SQL Databases like PostgreSQL, and MySQL scale vertically. Also, Redis Database is scaled Vertically<sup>1</sup> by adding more Ram.

![](https://raw.githubusercontent.com/Chetan11-dev/system-design/master/images/book/concepts/vertical-scaling.png)

**Horizontal Scaling and Vertical Scaling**

Some Components in a Distributed System are scaled Horizontally and some are scaled Vertically.

As a general rule, Backend Web Servers (like Django) are scaled horizontally, while Databases (such as Redis, Big Table, and PostgreSQL) are first scaled Vertically, and if Vertical Scaling proves insufficient, then they are scaled Horizontally if the Database supports it. (Like Redis supports Horizontal Scaling by adding more servers)

When adding Vertical Scaling you should make sure that the application is capable of utilizing additional Ram/CPU. For example, applications like Python’s Django cannot utilize additional CPU/Ram so there is no benefit in adding additional Ram/CPU to a Django Server.

**Implementing Scaling**

Thankfully if you are using Kubernetes, it can easily make your system more horizontally scalable by automatically adding more nodes when there is an increase in demand and removing nodes when there is less demand. This feautre is called Auto Scaling.

If you want to Vertically Scale a component you will need to manually add more RAM/CPU through your Cloud Provider(GCP, Digital Ocean) website.

## Availability

Availability means how long a system is available to use. For example, a website that is available to use 99% is more available that a website that is available to use 96%.

**What causes a Server to become unavailable?**

The server may become unavailable because the node that the server is running on goes down.

Consider the case when we are searching for a question on StackOverflow and StackOverflow goes down. It is quite a frustrating experience, isn’t it?

![](https://raw.githubusercontent.com/Chetan11-dev/system-design/master/images/book/concepts/stackoverflow-offline.png)

**How to make my server not go down?**

Of course, you want your website to keep running all the time. Unfortunately, in the real world nodes do go down, hence inevitable at some point in time your website will go down. What you can do is reduce the % of the time the website is down.

**Increasing Availability**

The strategy to reduce the % of the time our website is down (or increase the % of the time it is available) we should detect that a server has gone down and spin up a new server in its place.

Thankfully if you are using Kubernetes, it can easily make your system more available for you, Kubernetes will automatically detect whenever your application dies, and bring back another application in isn’t place.

## Efficiency

There are 2 metrics to measure your System’s Efficiency i.e., Latency and RPS

**Latency**

Latency is a synonym for the delay. Latency in the context of System Design means how long a request takes to complete.

For example, a request to StackOverflow takes 832ms to complete so its latency is 832ms.

**How to reduce Latency?**

It is best to attempt to reduce the latency of pages that are most popularly visited on a website. These pages are

- Search Page and Product Page on amazon.com
- Question Page on StackOverflow
- Post Page on dev. to.

Once you identified your target pages you could reduce latency by:

- Adding Correct Caching Headers like Immutable Resources like “Cache-Control: public, max-age=31536000, immutable”
- Using CDN (like Cloudflare, Fastly, and Google Cloud CDN) for static assets
- Using Redis as Cache in Database Layer.
- Use DNS-based Balancing so that if an Indian User sends a Request it will be forwarded to a server located in India. If an American user sends a request, it will be sent to a server located in America.

**RPS**

RPS is a measure of how many requests a server can serve in a second. If a website can serve 2000 requests in a second. Its RPS is 2000.

Request per Second is also known by the following words:

Queries Per Second (QPS): Often used in Systems Design Articles

Throughput: Often used in Documentation of Cloud Providers like AWS.

I will use RPS, for sake of Simplicity :)

**How to increase RPS?**

You can increase your RPS as follows:

- Adding more Servers to your Load Balancer.
- Port the specific endpoint in a specific faster Programming Language.

For example, if you are writing a StackOverflow-like application in Django, and your “questions/“ endpoint is receiving high traffic then, you can tell your Load Balancer to route all requests to the “questions/” endpoint to an express.JS Server which is capable of serving more requests than Django Server.

With this solution, you will able to take advantage of the easy-to-use nature of Python and the Speed of JS at the same time 😊.

## Maintainability

Maintainability means how easy to maintain the system you have created is!

An easy to maintain system leads to lesser bugs, ease in adding new features, and most importantly peace of mind for Developers 😊

**How to make my system more maintainable?**

As follows:

- Use tools that are easy to use for Developers which means using Good Backend Framework, using Good Frontend Framework, and using a Good Cloud Provider. I will guide you later on that aspect.
- Hiring Good Engineers that name things well and write easy-to-understand functional code.

## Summary

You learned that

- Scalability is the feature by which a system grows to handle more demand.
- Availability is a feature by which a system remains available to use despite node failures by gracefully handling node failures
- Latency means how long a request take to complete
- RPS means how many requests a server can serve in a second.

**Notes** 
1. Redis can also be scaled Horizontally using Redis Clusters if vertical scaling is still not sufficient.