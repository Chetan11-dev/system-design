Cloud Providers

**TLDR**

For the most bang for the buck,

- Use GCP Kubernetes and GCP Compute Engine because your Users will be interacting with your VMs in Real Time. You want these services to be the best of the best and Google has a great experience in delivering Complex Great Products like Google Maps and Google Translate, hence use GCP Kubernetes and GCP Compute Engine.
- Use Digital Ocean Object Storage as many applications will possibly have to store large amounts of data for that we can reduce our costs by using Digital Ocean Object Storage which happens to be 0.01$/GB.
- Use Cloudflare’s CDN as it is free for Unlimited amounts of Data, so any rational person will use them over any Cloud Provider.


**Detailed Version**

We will be discussing 4 Cloud Providers which are **Google Cloud, Microsoft Azure, AWS, and Digital Ocean** on 2 important metrics which are **Developer Experience** and **Pricing**. Let’s start.

## Developer Experience
I have used all 4 Providers and based on my experience,

**Digital Ocean** gives Great Developer Experience. Its UI is **the** best among all cloud providers

**GCP** gives Good enough Developer Experience, its strongest point is its good documentation which covers all the common use cases for developers which is a great time saver. Also, Google has a track record of creating Complex Consumer Products like Maps and Google Translate which is a Plus.

**Azure** gives Good enough Developer Experience. 

**AWS** gives a very Bad Developer Experience. The Documentation of AWS is full of Marketing, telling how awesome AWS is. In GCP and Digital Ocean, you will get good defaults but in AWS you will have to figure out what good defaults are by Google Searching. So, think twice before using AWS.
## Pricing
## Here is the pricing for the most important metrics for Different Cloud Providers in Dollars.

|                | GCP  | AZURE | AWS  | DO   | UNIT    |
|----------------|------|-------|------|------|---------|
| CPU            | 16   | 14    | 14   | 24   | CPU     |
| RAM            | 2    | 2     | 2    | 2    | GB      |
| VM Bandwidth   | 0.12 | 0.09  | 0.09 | 0.01 | GB      |
| Object Storage | 0.02 | 0.18  | 0.02 | 0.01 | GB      |
| Disk Storage   | 0.04 | 0.19  | 0.08 | 0.10 | GB      |
| CDN Bandwidth  | 0.09 | 0.08  | 0.09 | 0.10 | GB      |
| Kubernetes     | 0    | 0     | 72   | 0    | CLUSTER |

Here are some notes on pricing,

For CPU and RAM, there are similarly priced for all 4 Providers.

Bandwidth from User to VM is not charged by any 4 Providers.

Bandwidth from VM to User is similar for the 3 Big Clouds, but Digital Ocean offers it extremely Cheap at $0.01. The price of GCP and Microsoft can be justified as both these providers use their own Private Subnet to route traffic to the user, which is faster than the public Internet used by Digital Ocean.

Object Storage is the cheapest for Digital Ocean at $0.01 and $0.02 for GCP.

GCP is the cheapest in Disk Storage at $0.04 but Digital Ocean is expensive at $0.10 because if you need additional storage in Digital Ocean your only option is to use Digital Ocean’s Network based Volumes which cost $0.10 which happens to be slower also as they use the network to transfer data. 


Kubernetes cost $0 in all 3 cloud providers except AWS which Cloud Providers provide for free, as they can make money from VMs, used by Kubernetes. In GCP only the first cluster is free, any additional cluster will be charged $72 per month.

The pricing of CDN is just for information purposes, and I expect you to **not** use any 4 Cloud provider’s CDN as Cloudflare provides **Unlimited CDN** at a $**0.00** cost to you. So, any rational consumer will choose Cloudflare over all 4 cloud providers. 

The burning question is why Cloudflare gives CDN for free when others are charging for it? 

The answer is they believe that by giving it for free they can attract more customers and monetize them. Also, a free product makes it harder for new entrants and competitors to take their market share. 

A person asked this question the same question on webmasters.stackexchange.com and this was answered by the CEO of Cloudflare which I suggest you read now, 

Link: <https://webmasters.stackexchange.com/questions/88659/how-can-cloudflare-offer-a-free-cdn-with-unlimited-bandwidth>


**Note on Pricing**

Understand that, if you go to the Cloud Provider’s Website you will not see the Pricing, I have shown you because I have made certain assumptions like CPU and RAM for Providers such as AWS, Digital Ocean, and Azure as they don’t give information in that format. 

Also, many providers like Azure, AWS, and Digital Ocean give you at least 100GB of free bandwidth with the VM, which is good for startups the pricing I told is when you use more than the free limit.

You may be interested in reading this article where I describe from where I got Pricing for each Provider.

Link:

Also, In all 4 Cloud Providers, all resources are priced on an hourly basis. For example, in GCP the CPU cost is $15 per CPU. If your use the CPU only for 6 hours, you will be charged for 6 hours price which is **$0.25** ($15/720 hours \* 12 hours)


## Free Offers 
The good news for startups is that all these providers give free trials for some time. 

Also, some people when their trial period ends, create another account with another Card to avail credit for more time which you possibly want to do if you are broke, which is ok as everyone is broke at some point in time. Let’s see what these offers are

**GCP** gives **$300** Credit for **3 months** but you will need a Card.

Get Started Link: <https://cloud.google.com/free>

**Azure** gives **$100** Credit to GitHub students for **1 year** but you will need a Card.

Get Started Link: https://education.github.com/pack

**AWS** gives **$100** Credit for **1** year and there is **no need** for a Card but you will need to verify that you are a student either by verifying your college email address (like <ram@iitkanpur.edu>) or if you don’t have a school email you will have to tell them your school or college did not give you an email, along with your School ID after which they will give you the **$100** Credit.

Get Started Link: <https://www.awseducate.com/registration/s/registration-detail?language=en_US>

**Digital Ocean** gives **$200** Credit for GitHub students for **1 year** but you will need a Card.

Get Started Link: https://education.github.com/pack

**ATTENTION**

Even though you have free credit, please make sure that you shut down the resources after you use them otherwise you will keep incurring charges.

I made the mistake of postponing to shut down resources in GCP because I had free credit of **$300**, which resulted in an overdue bill of $61. 

So, please don’t repeat my mistake and make sure to shut down the resources even if you have free credit as all 4 Cloud Providers except **Microsoft Azure** follow the bad practice of **automatically** charging your Card without asking you if you exceed the free limit


## Conclusion
The burning question is which provider should I use for which service and Why?

For Optimal Developer Experience and Saving. Here is my Recommendation

Use GCP Kubernetes and GCP Compute Engine because your Users will be interacting with your VMs in Real Time. You want these services to be the best of the best and Google has a great experience in delivering Complex Great Products like Google Maps and Google Translate, so use GCP Kubernetes and GCP Compute Engine.

Use Digital Ocean Object Storage as many applications will possibly have to store large amounts of data for that we can reduce our costs by using Digital Ocean Object Storage which happens to be 0.01$/GB.

Use Cloudflare’s CDN as it is free for Unlimited amounts of Data, any rational person will use them over any Cloud Provider’s Website.

