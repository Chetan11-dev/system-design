# Load Balancing

## What is Load Balancing?

Load balancing is the process by which we distribute requests over several servers, so that no single server gets overloaded, and starts failing requests due to a lack of resources.

Modern high-traffic Websites such as StackOverflow must quickly respond to millions of HTTP requests. A Single Server may not be able to handle the load of these requests.

So we add a load balancer whose only job is to distribute requests over a pool of servers.
For example, as you can see in this picture several users are sending requests to the load balancer which is then distributing these requests over a pool of application servers.

![](https://raw.githubusercontent.com/Chetan11-dev/system-design/master/images/book/load-balancing/load-balancing.png)

You can load balance requests in several different ways. Popular Load Balancing methods are given below.
There are different methods of loading balancing such as

Round Robin:
Round Robin is the most popular method of loading balancing. Here we distribute requests sequentially.
As an example, if we have 3 Servers and we receive 6 HTTP requests this is how they will be distributed.

HTTP Request 1  -> Server 1
HTTP Request 2  -> Server 2
HTTP Request 3  -> Server 3
HTTP Request 4  -> Server 1
HTTP Request 5  -> Server 2
HTTP Request 6  -> Server 3

and so on

IP Hashing

This method routes traffic to servers based on a hashing algorithm that takes the user's IP into account. This ensures that traffic from the same source IP address is always routed to the same server. For example,
if user 1 sends a request it will always be routed to the same server say Server 1. if user 2 sends a request it will always be routed to the same server say Server 3.

So question is, Which load balancing method to use?
It depends on your use case. For most applications, a round-robin is ideal. It is also the most popular method used.

## Load Balancing in different Product Stages:

The question is how will you determine how many nodes to load balance between?

Well, It depends on your product stage as follows:

Startup: In startup keep it simple and load-balance with just 1 Server.

Growth: When you start receiving a decent amount of traffic you should use horizontal autoscaling and load balance traffic using round robin. In horizontal autoscaling, new app instances will automatically spine up as traffic increases and will be automatically removed when traffic reduces to save money. This feature is available in Kubernetes which I will talk about later.

## Tools

Nginx and Apache Web Server are the 2 most popular load balancers. Nginx is more developer friendly than Apache Web Server.

Also if you are using Kubernetes, the Kubernetes team has created a product through which you can integrate Nginx into Kubernetes as your load balancer.

The product has 13K+ Starts in Github which is Great. Here is the GitHub link for it
Link: [ingress-nginx](https://github.com/kubernetes/ingress-nginx)