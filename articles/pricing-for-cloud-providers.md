<!-- Title: Pricing for Cloud Providers -->
## Pricing for Cloud Providers
TLDR:

Here is the Pricing Table for all  4 major Cloud Providers.

|                | GCP  | AZURE | AWS  | DO   | UNIT    |
|----------------|------|-------|------|------|---------|
| CPU            | 16   | 14    | 14   | 24   | CPU     |
| RAM            | 2    | 2     | 2    | 2    | GB      |
| VM Bandwidth   | 0.12 | 0.09  | 0.09 | 0.01 | GB      |
| Object Storage | 0.02 | 0.18  | 0.02 | 0.01 | GB      |
| Disk Storage   | 0.04 | 0.19  | 0.08 | 0.10 | GB      |
| CDN Bandwidth  | 0.09 | 0.08  | 0.09 | 0.10 | GB      |
| Kubernetes     | 0    | 0     | 72   | 0    | CLUSTER |

You can use this table to calculate the cost of the Cloud Provider you are using.

Now let’s calculate Pricing for 4 Providers which are **Google Cloud, Microsoft Azure, AWS,** and **Digital Ocean** for these metrics

**- CPU**

**- RAM**

**- VM Bandwidth Server to User**

**- Object Storage**

**- Disk Storage**

**- CDN Bandwidth**

**- Kubernetes**

For some of these metrics, we will make some assumptions. Also, all pricing is based on a monthly basis for simplicity.
## CPU
The Pricing will be based on General Purpose CPU for on-demand Instances.

**GCP CPU Pricing**

**Cost: $16**

**Proof:**

![](https://raw.githubusercontent.com/Chetan11-dev/system-design/master/images/articles/pricing-for-cloud-providers/https://raw.githubusercontent.com/Chetan11-dev/system-design/master/images/articles/pricing-for-cloud-providers/gcp-cpu.png)

**Estimation:**

As shown in the picture

**Azure CPU Pricing**

**Cost: $14**

**Proof:**

![](https://raw.githubusercontent.com/Chetan11-dev/system-design/master/images/articles/pricing-for-cloud-providers/azure-cpu.png)

**Estimation:**

The pricing is based on the B1ms instance which gives 2GB RAM and 1 CPU for $18 because Azure does not provide Pricing based on per unit CPU. I assumed the price of RAM to be $2/GB (The per  Ram Price of GCP)

Based on this Assumption the CPU Price is calculated as follows:

B1MS Cost: $18

(Assumed Ram Cost): 2 \* $2

Estimated CPU Cost: $14

**AWS CPU Pricing**

**Cost: $14**

**Proof:**

![](https://raw.githubusercontent.com/Chetan11-dev/system-design/master/images/articles/pricing-for-cloud-providers/aws-cpu.png)

**Estimation:**

The pricing is based on the a1.medium instance which gives 2GB RAM and 1 CPU for $18($0.0255 \* 720 hours)

Assuming the price of RAM to be $2/GB (The per Ram Price of GCP)

a1.medium Cost: $18

(Assumed Ram Cost): 2 \* $2

Estimated CPU Cost: $14

**Digital Ocean** **CPU Pricing**

**Cost: $24**

**Proof:**

![](https://raw.githubusercontent.com/Chetan11-dev/system-design/master/images/articles/pricing-for-cloud-providers/do-cpu.png)

**Estimation:**

The pricing is based on a General Purpose instance that gives 8GB RAM and 2 CPUs for $63. Digital Ocean also provides a Basic Instance which is cheaper but we are using a General Purpose instance instead for an Apple to Apple Comparison with other providers.

Assuming the price of RAM to be $2/GB (The Ram Price of GCP)

Instance Cost: $63

(Assumed Ram Cost): 8 \* $2

Estimated CPU Cost for 2 CPUs: $47

Estimated CPU Cost for 1 CPU: $23.5

## RAM
**GCP RAM Pricing**

**Cost: $2**

**Proof:** 

![](https://raw.githubusercontent.com/Chetan11-dev/system-design/master/images/articles/pricing-for-cloud-providers/gcp-mem.png)

**Estimation:**

As shown in the picture

**Azure RAM Pricing**

**Cost: $2**

**Proof:** 

![](https://raw.githubusercontent.com/Chetan11-dev/system-design/master/images/articles/pricing-for-cloud-providers/azure-cpu.png)

**Estimation:**

Based on Assumptions made while calculating the CPU Cost.

**AWS RAM Pricing**

**Cost: $2**

**Proof:**

![](https://raw.githubusercontent.com/Chetan11-dev/system-design/master/images/articles/pricing-for-cloud-providers/aws-cpu.png)

**Estimation:**

Based on Assumptions made while calculating the CPU Cost.

**Digital Ocean** **RAM Pricing**

**Cost: $2**

**Proof:**

![](https://raw.githubusercontent.com/Chetan11-dev/system-design/master/images/articles/pricing-for-cloud-providers/do-cpu.png)

**Estimation:**

Based on Assumptions made while calculating the CPU Cost.

## Bandwidth
**GCP Bandwidth Pricing**

**Cost: $0.12**

**Proof:**

![](https://raw.githubusercontent.com/Chetan11-dev/system-design/master/images/articles/pricing-for-cloud-providers/gcp-bw.png)

**Estimation:**

Hers, we have used pricing which excludes China and Australia which turns out to be $0.12

**Azure Bandwidth Pricing**

**Cost: $0.09**

**Proof:**

![](https://raw.githubusercontent.com/Chetan11-dev/system-design/master/images/articles/pricing-for-cloud-providers/azure-bw.png)

**Estimation:**

Hers, we have used Network Egress in which we assumed your Servers are located either in America or Europe.

**AWS Bandwidth Pricing**

**Cost: $0.09**

**Proof:**

![](https://raw.githubusercontent.com/Chetan11-dev/system-design/master/images/articles/pricing-for-cloud-providers/aws-bw.png)

**Estimation:**

Hers, we have used pricing for traffic below 10TB.

**Digital Ocean** **Bandwidth Pricing**

**Cost: $0.01**

**Proof:**

![](https://raw.githubusercontent.com/Chetan11-dev/system-design/master/images/articles/pricing-for-cloud-providers/do-bw.png)

**Estimation:**

Hers, we have used pricing for excess data transfer from Server to User which costs $0.01.

Object Storage 

**GCP Object Storage Pricing**

**Cost: $0.02**

**Proof:**

![](https://raw.githubusercontent.com/Chetan11-dev/system-design/master/images/articles/pricing-for-cloud-providers/gcp-st.png)

**Estimation:**

Pricing is as shown in the image.

**Azure Object Storage Pricing**

**Cost: $0.18**

**Proof:**

![](https://raw.githubusercontent.com/Chetan11-dev/system-design/master/images/articles/pricing-for-cloud-providers/azure-st.png)

**Estimation:**

Pricing is as shown in the image

**AWS Object Storage Pricing**

**Cost: $0.02**

**Proof:**

![](https://raw.githubusercontent.com/Chetan11-dev/system-design/master/images/articles/pricing-for-cloud-providers/aws-st.png)

**Estimation:**

Pricing is as shown in the image

**Digital Ocean** **Object Storage Pricing**

**Cost: $0.01**

**Proof
:**
![](https://raw.githubusercontent.com/Chetan11-dev/system-design/master/images/articles/pricing-for-cloud-providers/do-st.png)

**Estimation:**

Pricing is as shown in the image

Disk Storage Pricing

**GCP Disk Storage Pricing**

**Cost: $0.04**

**Proof:**

![](https://raw.githubusercontent.com/Chetan11-dev/system-design/master/images/articles/pricing-for-cloud-providers/gcp-dsk.png)

**Estimation:**

Pricing is as shown in the image

**Azure Disk Storage Pricing**

**Cost: $0.19**

**Proof:**

![](https://raw.githubusercontent.com/Chetan11-dev/system-design/master/images/articles/pricing-for-cloud-providers/az-dsk.png)

**Estimation:**

Pricing is calculated as $0.74/4GB which is $0.19

**AWS Disk Storage Pricing**

**Cost: $0.08**

**Proof:**

![](https://raw.githubusercontent.com/Chetan11-dev/system-design/master/images/articles/pricing-for-cloud-providers/aws-dsk.png)

**Estimation:**

Pricing is as shown in the image

**Digital Ocean** **Disk Storage Pricing**

**Cost: $0.01**

**Proof:**

![](https://raw.githubusercontent.com/Chetan11-dev/system-design/master/images/articles/pricing-for-cloud-providers/do-dsk.png)

**Estimation:**

Pricing is calculated as  100GB/$10 which is  0.10

CDN Bandwidth 

**GCP CDN Bandwidth Pricing**

**Cost: $0.09**

**Proof:**

![](https://raw.githubusercontent.com/Chetan11-dev/system-design/master/images/articles/pricing-for-cloud-providers/gcp-cdn.png)

**Estimation:**

Pricing is as shown in the image

**Azure CDN Bandwidth Pricing**

**Cost: $0.08**

**Proof:**

![](https://raw.githubusercontent.com/Chetan11-dev/system-design/master/images/articles/pricing-for-cloud-providers/azure-cdn.png)

**Estimation:**

Pricing is as shown in the image

**AWS CDN Bandwidth Pricing**


**Cost: $0.09**

**Proof:**

![](https://raw.githubusercontent.com/Chetan11-dev/system-design/master/images/articles/pricing-for-cloud-providers/aws-cdn.png)

**Estimation:**

Pricing is as shown in the image

**Digital Ocean** **CDN Bandwidth Pricing**

**Cost: $0.01**

**Proof:**

![](https://raw.githubusercontent.com/Chetan11-dev/system-design/master/images/articles/pricing-for-cloud-providers/do-cdn.png)

Kubernetes 

**GCP Kubernetes Pricing**

**Cost: $0.00**

**Proof:**

![](https://raw.githubusercontent.com/Chetan11-dev/system-design/master/images/articles/pricing-for-cloud-providers/gcp-ke.png)

**Estimation:**

In GCP the first Cluster is Free, for any additional Cluster you are charged $72 per month.

**Azure Kubernetes Pricing**

**Cost: $0.00**

**Proof:**

![](https://raw.githubusercontent.com/Chetan11-dev/system-design/master/images/articles/pricing-for-cloud-providers/azure-ke.png)

**Estimation:**

Pricing is as shown in the image

**AWS Kubernetes Pricing**

**Cost: $72**

**Proof:**

![](https://raw.githubusercontent.com/Chetan11-dev/system-design/master/images/articles/pricing-for-cloud-providers/aws-ke.png)

**Estimation:**

Amazon Kubernetes cost $0.10 per hour. For a month of usage, it cost 72$($0.10 \* 720)

**Digital Ocean** **Kubernetes Pricing**

**Cost: $0.00**

**Proof:**

![](https://raw.githubusercontent.com/Chetan11-dev/system-design/master/images/articles/pricing-for-cloud-providers/do-ke.png)

**Estimation:**

The $12 charge on the page is the cheapest VM Node on Digital Ocean. Kubernetes is free as Digital Ocean gives free Control Pane.

