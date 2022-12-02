# Kubernetes

Kubernetes is an open-source container-orchestration tool made by Google. Google later donated Kubernetes to CNCF, for which we are thankful to Google.

Kubernetes originates from the Greek word helmsman, which means someone who steers a Ship.

If you do system design with Kubernetes it will be a much better Developer Experience. Now, I will give an Overview of the Capabilities of Kubernetes.

## What can Kubernetes do?
Kubernetes can do the following things.

**1.  Horizontal AutoScaling**

Kubernetes can horizontally scale your apps automatically,

Consider the example of Baidu, a Search App similar to Google whose user base consists of Chinese People only. There will be very less searching at Night in China, as Chinese users will be sleeping. Baidu can save money on computing if it can reduce the number of its Webservers at Night. 

Using Kubernetes Baidu can automatically reduce the number of Servers when there is less traffic and automatically increase servers when there is more. 

In other words with Kubernetes AutoScaling, you can get the ultimate **bang for the buck**.



**2.  Load balancing**

With Kubernetes, you can easily load balance your Application among a number of instances

**3.  Environment Variables Management**

In production, we need to inject certain environment variables into our application to make certain services work. With Kubernetes Secrets, Kubernetes can inject and manage environment variables easily.

**4. Self-Healing**

In case your application fails for some reason, Kubernetes will automatically restart the application and this helps increase the availability of your Apps.

**5.  Easy Storage Management**

In some applications, we need to persist data on disks. Before Kubernetes, we used to add disks to VM from the Cloud Provider’s Website. With Kubernetes, we can easily manage data storage in disks using Persistent Volumes. Persistent Volumes in Kubernetes help you manage data in Kubernetes.

**6. Resource Specification**

In some Applications, we need to specify that, we need X GB of Ram or X number of CPUs to run the Application. 

We can tell Kubernetes that our application needs X GB of RAM or X number of CPUs and Kubernetes will ensure that our Application only runs on a machine that meets the requirements.
**


## Benefits of using Kubernetes for Developers
**1. Saves Money 💰**

With features like Horizontal AutoScaling. You only use the resources you need. Thus giving you the ultimate Bang for the Buck.

**2. Increased Availability and Scalability**

With features like Horizontal AutoScaling and Self-Healing, you increase both the Availability and Scalability of your Application. Increased Availability prevents the Rage of the User.

**3. Developer Productivity**

Kubernetes is like Exercising. Exercising is tough to start with but it is good for you as it increases your lifespan.

Similarly, Kubernetes will be a learning curve for you but once you learn it, your Productivity will surely increase.
## Summary
In Conclusion, Kubernetes is a must-have tool for every Application. You should surely learn Kubernetes as it will be of immense help to you. 

In this course we are only focusing on system design, hence it is recommended you learn Kubernetes on your own through an online Course. 
