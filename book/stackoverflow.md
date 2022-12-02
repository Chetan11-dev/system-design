<!-- 
 FOCUSED DESIGN FOR STARTUPS THAT GUIDES CORRECTLY FORGET TIME CONSTRAINTS. GIVE THEM COMPLETE SOLUTIONS.

 -->
## Create Stack Overflow for a StartUp
Now, is the time to create our beloved StackOverflow. StackOverflow is an application that saves the time of Developers by helping them find a trustful solution to their problems.
## 🎯 Create Stack Overflow for a StartUp
We will create a StackOverflow for a StartUp whose user base is less than 10,000.

Our Startup Application should allow users to take the following actions.

- Create Questions with Tags
- Upvote/Downvote Question
- Create Answers
- Upvote/Downvote Answer
- Comment on answers
- Search Questions by text or tags 
## Designing The API

**Create a Question**

This Endpoint will allow Users to Create Questions. The users need to specify the title, content, and at least one predefined tag for the question. 

```
create_question(user_id, title, content, tags)
```

Q: Should users to allowed to enter empty tags?

Well, even StackOverflow does not allow tags to be empty. Similarly, we should also not allow tags to be empty, as tags help us display unanswered questions to users based on their interests, and showing questions based on users’ interests helps drive engagement.

**Upvote/Downvote Question**

This Endpoint will allow other users to Upvote/Downvote a question. 

```python
vote_question(user_id, question_id, vote_type:  ‘UPVOTE’ |‘DOWNVOTE’)
```

**Create Answers**

This Endpoint will allow users to answer a question. 

```python
create_answer(user_id, question_id, content)
```

**Upvote/Downvote Answer**

This Endpoint will allow other users to Upvote/Downvote an answer. 

```python
vote_answer(user_id, answer_id, vote_type:  ‘UPVOTE’ |‘DOWNVOTE’)
```

**Comment on answers**

This Endpoint will allow users to comment on the answers.

```python
comment_on_answer(user_id, answer_id, content)
```

**Search Questions** 

This endpoint will allow users to search for questions by keywords or by tags.

search_questions(keywords?, tags?): Question[]

## Database Modeling
As we are creating an Application for Startups whose scale is below 10K DAU, we intuitively know SQL can support it. So, we use SQL Database.

Let us understand Database the models used in our Database.

**User Model**

The User model represents the Users of our System.

**Question Model**

The Question model represents questions asked by Users. 

A User can ask many questions but a question can only be asked by 1 user. So a Question has Many-to-One relations with Users.** 

**QuestionVote**

A QuestionVote represents a vote cast by a User on a question. QuestionVote contains the following properties:

user_id

question_id

vote_type

We want to allow a user to cast a maximum of 1 vote per question, we will enforce that by making the user_id and question_id unique together that way a user can cast a maximum of 1 vote per question.

Similar to StackOverflow we will also write logic to not allow the question’s author to upvote his own question.

**AnswerVote**

An AnswerVote represents a vote cast by a User on an answer. The rest of the logic is similar to the one you understood in previous QuestionModel.

**Comment**

A comment represents other users’ comments on an answer. 

An Answer can have many Comments but each Comment belongs to one Answer. So Comment has a Many-to-One Relation with Answers

Also, A User can have many Answers but each Answer belongs to one Answer. So Comments have a Many-to-One Relation with Users.

---

Based on these insights we can visualize our Database as follows:

<!-- Write Image  -->

## Design Decisions
Now, we will make Design Decisions in the context of StartUps whose user base is around 10,000. 

When designing for startups you should** aim** to keep things as simple and as easy to code as possible as this practice of opting for the simple solution will save Founders months of Developer Time, which can be invested by Founders in Marketing Efforts to increase Users. 

<!-- 
\# Due to the tribal nature of humans, developers often don’t agree regarding the choice of tools. For example, some Developers prefer React, and some developers prefer Svelte. We will also be making a similar choice and your preferred solution may be different from my preferred solution, which we respectfully accept.
-->


<!-- 
\# Lastly, there is no this is the only right way of doing things in system design. There are multiple ways of creating a system and every way is acceptable as long as it creates a System. 
-->



**How to search by text?**

We have 2 Options,

- Use SQL’s contains function to search across the Title field of the Question.
- Use ElasticSearch to do a full-text search across titles and content.

Using the ElasticSearch-based solution will give the best developer experience and using the SQL-based solution will give the best Developer Experience as it is easy to implement. 

As we are creating for a StartUp we will opt for the best Developer Experience and use an SQL-based Solution. We will also add the ElasticSearch-based Solution to our backlog to be implemented later as it gives the best Developer Experience.

**Q**: Which SQL Database to use?

As we are creating for StartUp we should use SQLite as working with SQLite gives superior Developer Experience because we don’t need to start a Server. A more Scalable Database like PostgreSQL can be used later if we outgrow SQLite.

## Cost Estimation
We will estimate costs assuming we are running on the Google Cloud Platform.

For our Startup application, we will be running the following components in GCP.

1 Kubernetes Cluster

1 Django Server serving Backend Application

1 Svelte Kit Server serving Frontend

In GCP the first Cluster is free to every user, so we skip the cost of Kubernetes.

![](https://raw.githubusercontent.com/Chetan11-dev/system-design/master/images/book/stackoverflow/gke-free.png)

**Bandwidth**

Now we will calculate the Bandwidth used in 1 month.

We assumed that,

We have 10K Daily Active Users.

Each User creates 12 Questions per month

It is a Read Heavy Application with Read to Write Ration of 100:1.

The size of the Q/A Page after compression is 100KB.

**Calculation**

Total Question Created per Month = Questions Created by Each User \* Number of Users 

=  12 \* 10K = 120K

Reads per Month = Total Question Created per Month  \* Reads per Question = 120K \* 100 = 1.2M

Reads per Second = Reads per Month/Seconds in Month = 1.2M/2.5M = 0.48 

Bandwidth = Reads per Month \*  Page Size = 1.2M \* 100KB = 120GB

Bandwidth per Second = Reads per Second \*  Page Size = 0.48 \* 100KB = 48KB or 0.048MB

So **Cost of Bandwidth** is,

= Bandwidth Used \* Cost of 1 GB Bandwidth 

= 120GB \* $0.12 = $14.4

---

**VM Cost** 

Our Read Per Second stands very low at 0.48. so we will run 1 Svelte Kit Server and 1 Django Server. 

For Django Server, we allocate 0.25 CPU and 1GB Ram.

For Svelte Kit Server, we allocate 0.25 CPU and 1GB Ram. 

So **VM Cost** is,

= Django Server Cost + Svelte Kit Server Cost

= 0. 25 \* CPU Cost + 1 \* Ram Cost + 0.25 \* CPU Cost + 1 \* Ram Cost

= 0.25 \* $16 + 1 \* $2 + 0.25 \* $16 + 1 \* $2

= $6

**Q:** How can we find the amount of CPU or RAM which will be used?

Well, you should monitor your Kubernetes Cluster to learn how much RAM and CPU your application is using based on that you should decide how much CPU and Ram to allocate.

You can use tools like Metrics API and Kubernetes Dashboard these tools will display the RAM and CPU in graph format like so,

IMAGE

**Disk Storage Cost**

Some Instructors do estimate the Storage used by Database.

Understand that, estimating Database Storage is Hard to do, and a database takes tiny amounts of Space to store lots of Data. So to keep things easy we will just skip it.

Lastly, I want to give you instructions on how to allocate storage for the Database in Production.

Let’s the day you are using SQLite to store data for your StartUp. SQLite stores data in a single file. So, we will start with 1 GB of  Storage and we will monitor it so that whenever storage becomes around 70% full we will double it. 

Also, GCP gives you 30 GB of free disk storage. So you can keep doubling storage for free till you reach the 30GB mark. ⬇️

![](https://raw.githubusercontent.com/Chetan11-dev/system-design/master/images/book/stackoverflow/cmp-engine.png)

**Total Cost**

VM Cost = $6

Bandwidth Cost = $14.2

**Total Cost = $7.2**

**Accounting for Discounts**

Every User on the Google Cloud Platform is offered e2-micro instances for **free**. the e2-micro instance has **0.5 CPU** and **2 GB Ram**. This negates our VM Cost.

![](https://raw.githubusercontent.com/Chetan11-dev/system-design/master/images/book/stackoverflow/cmp-engine.png)

So Total Cost after Discounts is

**Total Cost = $7.2**

Less e2-micro discount = -$6

**Final Cost = $1**

So, you have to pay $1 to run your Startup Application for 10K Users which is a bargain for Startups.

**Note:**

To avail of discounts, make sure to add only 1 node for an e2-micro instance in your Kubernetes Cluster. Also, ensure you run your Kubernetes Cluster created in a region like us-central1 (lowa).
## Beyond System Design

**Q:** Should I add more features to it?

Understand this **bitter truth** that, there is a very **high** **chance** that **no one will use your product**. So if you add more features and no one used your product, that means all months spent in implementing those features are wasted. 

So, what I will suggest is **first** you create** a **usable product**, then **focus** your efforts on **getting users**. Once users start coming, your **morale** will **increase**, and then you can **write code** to add **more features**. 

**Q:** How can I make a Startup like StackOverflow succeed?

**A:** First, understand **why** people **come to StackOverflow**? 

The reason they come to StackOverflow is that they **want a trustful solution** to their problem

So, to compete with StackOverflow all you need is **trustful solutions to people’s problems**.

Trustful answers are always in high demand **Biology Students** want trustful answers, **Lawyers** want trustful answers, **Accountants** want trustful answers and **High School** Students want lots of trustful answers.

So, the recipe to making your startup succeed is simple, you just get lots of trustful answers for a target audience say **High School Students.**

**Q:** How can I get lots of trustful answers for the target audience say **High School Students**?

**A:** If I have to do it, here is how I will do it.

1. Use Python to scrape 100’s Popular Questions from existing Q/A Sites like brainly.com, toppr.com, and byju.com
1. Write good answers in my own words using tools like quillbot.com and publish them on our startup website.
1. Analyze traffic generated using Google Analytics and Repeat it many times

**Q:** How can I money from it?

**A:**

0. Resist the temptation of monetizing by asking people to pay to see answers like quora.com does by asking $5 to see answers because it gives a terrible user experience when you can’t see an answer just because you are broke.
0. Focus on reaching the 100K DAU mark by 
   - increasing the number of questions 
   - Creating additional Q/A websites focused on 1 specific niche like LawExchange for Lawyers, and AccountExchange for Accountants. 
0. Then create an ecosystem of Paid Products similar to how Google has created and monetized your customers. You can create a supplementary Paid Product like a Course Selling Platform (like Udemy) and sell courses to make money. 

<!-- 
0. # Lastly if you are profitable, I would recommend you make a difference in people’s life by donating 1/10 of your Net Profits as Dasvandh. 

Dasvandh is a practice in which we make a difference in people’s life by donating which was pioneered by Guru Nanak Dev Ji.

It is **best** to donate Dasvandh by yourself because by that you can be assured that your money has made a difference in people’s life.

Some of the most effective ways to make a difference in people’s lives are

- Give changing books like **Rich Dad and Poor Dad, The Wellness Sense** to College Students. These books will change the life of a few college students.
- Rent a place and create a Study Room for Students where they can study away from the distractions of home in a quiet place free of Cost. Make sure to advertise your library by visiting all Schools and Colleges in your City.
-->

## Outgrowing StackOverflow
Now we will scale our StartUp Architecture to support up to 1000K users.

TODO:

Changes 

Use PostgreSQL

Use Redis Database

Use CDN
## Final Thoughts
We are fortunate to be developers, whatever problems we have other developer helps us by giving solution. The best way to repay this help is to help others.

We want someone to create a StackOverflow for Lawyers, Accountants, and High School Students to help them. 

It is definitely a good StartUp Idea and just remember, it will take time to monetize the website, so be steady.

Finally here is the fruit of our hard work. Thankfully, It is quite simple which should be for a StartUp.

## Summary
2-3 lines

Give Examples, Research on SO. Find on Google

Notes:

\1.

\2.

\3.

\4.

\5.

\6.
