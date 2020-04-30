---
title: API First
weight: 5
pre: "<b>1. </b>"
chapter: true
---

### Chapter 1

1\. API First Concepts
======================

APIs? What are they? That is the million dollar question nowadays. We could come up with thousands of answers, but we prefer this simple analogy.

**A very easy analogy might be:** Your APIs are to your business what a panel and controls are to a car. Most people have no clue about how a car works under the hood but knows that if you push the accelerator, the car goes faster, and if you apply your brakes, the car will eventually stop (Figure 1). Similarly, things like climate control, blind spot detection, and adaptive cruise control provide a safer and more enjoyable driving experience without you having to worry about how those systems do what they do. Well, that is exactly how good APIs should work!

**In a very objective way:** APIs allow you to develop higher quality solutions more securely, quickly, and easily, and will allow your solutions to be created faster and with higher quality, since your developers don’t have to understand details of the business function in a wider and deeper way. For that reason, the market is increasingly creating applications composed of internal and external APIs, pretty much like Uber did (using Google Maps, PayPal, Social Logins, etc.). The outcome will be better applications and more competition among API providers.

<img class="s t u ga ai" src="https://miro.medium.com/max/1600/0\*kn7JKRC5r3n9WpK3.png" width="800" height="326" srcSet="https://miro.medium.com/max/552/0\*kn7JKRC5r3n9WpK3.png 276w, https://miro.medium.com/max/1104/0\*kn7JKRC5r3n9WpK3.png 552w, https://miro.medium.com/max/1280/0\*kn7JKRC5r3n9WpK3.png 640w, https://miro.medium.com/max/1400/0\*kn7JKRC5r3n9WpK3.png 700w" sizes="700px" role="presentation"/>

Figure 1 — The Car and its capabilities

API strategy or the API economy encompasses several aspects; these include adopting the right strategy to expose such internal capabilities in the organizations in a highly reusable fashion, ensuring they’re easy to consume internally and externally, and possibly being able to generate business and revenue.

Here’s another good way to look at this — in the 1990s, not having a website for a company was not good, but, today, a company with no plans of having at least one API might be unusual.

So what should companies be looking for in order to have a successful API strategy?

We understand that an API initiative must include the following phases (Figure 2):

*   Validate the impact in the core business
*   Qualify the key criteria (technology partner, success and even failure)
*   Define a short and agile sprint/delivery based on an MVP and MVA

<img class="s t u ga ai" src="https://miro.medium.com/max/1600/0\*elu5KIVOEMDBiSAJ.png" width="800" height="353" srcSet="https://miro.medium.com/max/552/0\*elu5KIVOEMDBiSAJ.png 276w, https://miro.medium.com/max/1104/0\*elu5KIVOEMDBiSAJ.png 552w, https://miro.medium.com/max/1280/0\*elu5KIVOEMDBiSAJ.png 640w, https://miro.medium.com/max/1400/0\*elu5KIVOEMDBiSAJ.png 700w" sizes="700px" role="presentation"/>

Figure 2 — A Process for validating your API initiative at early stages

This document intends to explain in a very vendor-agnostic way how it’s possible to achieve these points in an effective way, and also safely, protecting not only your time, but your team and investments. In the end, we would like to provide a set of guidelines to build credibility and trust with your company to execute a great API strategy and enable significant adoption.

2\. API: First
==============

As we have moved towards mobile-first development in the past, it is very common now that we face the API-first approach, which consists of representing your business functions as APIs. Therefore, let’s use a hypothetical travel business case example, a kind that many of us are familiar with how it works, as traveling, booking a flight or hotel, are common activities for most people. Let’s assume the name of this business is Hostelera (any similarity to an actual entity is purely coincidental).

Hostelera is a spinoff of a large and traditional tourism group that will share some resources with that new spinoff while maintaining their own development and business teams. The team supports a desktop application that runs in many travel agencies across the country. Hostelera realizes that they need to execute a digital transformation strategy, and for that reason, they decide to not only operate in B2B transactions (where companies do business with other companies) but to play into the B2C space (where companies can approach the end consumer in the chain). The Hostelera team decided that they will start their business developing their website in order to attract end customers; they start with some questions as follows:

*   Are we about to use PHP, Python, Django?
*   Are we fine to use HTML5 with bootstrap or material?
*   Can we check some themes in Themeforest?

Well, all those questions above are valuable, but they are far away from **impacting the business** in a very effective manner. Now we will discover what we can do slightly differently.

3\. API: First Applied
======================

In order to support Hostelera in their digital transformation initiative, we were invited to help them, but initially just talking about business and nothing else. Now, let’s take a look at our initial questions:

*   **Question:** Tell us what you sell the most? And how?
*   **Business:** We do have a great contract with some hotel brands and at some destinations and during some seasons our prices are by far the best! As a result, many agencies can book our offers into our desktop system and we take care of the logistics.

**Note:** If you wish to learn more about the technical aspects, such as API verbs, nouns, etc, please refer to relevant material in the WSO2 Library.

*   **Question:** Describe the most important information you need at the point of booking a hotel room.
*   **Business:** The key things we need to know about the reservation are destination, period, type of room and if double bed/twin beds, and how the payment will be made. Sometimes when we allow direct payments, we may face some issues with recovering our commission, which isn’t very favorable for us.

After we evaluate what was important for Hostelera, the tech people had uncovered what capabilities exist in the organization (as is), and after brainstorming with the business and technology teams, we came up with the following APIs to get started (Figure 3).

<img class="s t u ga ai" src="https://miro.medium.com/max/1600/0\*zM8j5TqtMjspjjnm.png" width="800" height="315" srcSet="https://miro.medium.com/max/552/0\*zM8j5TqtMjspjjnm.png 276w, https://miro.medium.com/max/1104/0\*zM8j5TqtMjspjjnm.png 552w, https://miro.medium.com/max/1280/0\*zM8j5TqtMjspjjnm.png 640w, https://miro.medium.com/max/1400/0\*zM8j5TqtMjspjjnm.png 700w" sizes="700px" role="presentation"/>

Figure 3 — The Initial proposed API Catalog

With the information provided, we can now design the APIs in a very easy manner using an industry standard called Swagger.

Some [API management](https://wso2.com/api-management/) solutions have the Swagger Editor built into their solution, and with this, you can define your entire API “contract” and plug in the final implementation later. As a result, you can combine both technology and business to define what’s really important to be delivered as the initial APIs. The goal here is to be already connecting with our MVP and MVA that will be proposed later on in this paper.

Figure 4 is an example of the Swagger Editor where you can see the result of the meeting and efforts applied by both the business as well as technology.

<img class="s t u ga ai" src="https://miro.medium.com/max/1600/0\*z777mXxRInVdVeBV.png" width="800" height="454" srcSet="https://miro.medium.com/max/552/0\*z777mXxRInVdVeBV.png 276w, https://miro.medium.com/max/1104/0\*z777mXxRInVdVeBV.png 552w, https://miro.medium.com/max/1280/0\*z777mXxRInVdVeBV.png 640w, https://miro.medium.com/max/1400/0\*z777mXxRInVdVeBV.png 700w" sizes="700px" role="presentation"/>

Figure 4 — The API Contract (Swagger)

As a matter of fact, once the APIs are well designed, we can now even mock them; in other words, before you spend a lot of energy, time, and money to build the complete system, you can test it out with some canned JSON (payloads) using a basic JavaScript implementation. Simple fixed data will be good enough for testing some of your assumptions on how to make the API easy to connect to.

_Given that the APIs are ready for initial usage, what about the website?_

Simple answer: With the APIs ready, to build a site, web app, mobile app, bots, integrating with partners, etc., connecting to your API (and thus with your core business) is extremely easy.

The following section describes some important phases when creating your APIs.

3.1 Validating impacts in core business
=======================================

If you don’t know the exact benefits an API strategy can bring to your organization, and if you consider this a tough task at least in the short term, it may help to do some interactions/sprints following the principles of API: First.

The direct impacts of an API strategy into an organization include

*   Capacity to expand the way to communicate and connect with new business channels and generate new potential revenue streams.
*   Monetizing these new revenue streams (why not)
*   Delivery of new applications faster and with more agility given that most of the hard work will be encapsulated by APIs
*   Service reusability and governance, helping find what assets exist and sharing them more broadly across the organization, including integrations, microservices, legacy databases, stored procedures, etc.
*   For the organization, it will represent starting jobs with proper tools, and not having to create the tools over and over again from scratch.

However, there is a tricky part in all of this. You have to make sure that you have the proper **organization engagement** with your API initiative. The sad truth is that if your company doesn’t embrace exposing and reusing APIs as a key component of transforming and impacting the business, based on some of our experiences, there is a higher risk of failure. For this reason, sometimes interns to C-levels must know that you are investing time, money, and company efforts to accomplish something that will have a valuable outcome and it also directly helps to improve the business. For this reason, it’s important you involve as many people as possible in your API initiative. Some ways to do that might be

*   API First Hackathons: Just drafting potential APIs
*   Consuming APIs Hackathons: Just checking how the existing applications or partners can consuming your “drafted” APIs

These types of initiatives can bring you real KPIs that can make your company “buy in” to your initiative (idea). That is one of the most fundamental things in very successful API initiatives.

Let’s consider the Hostelera example again; they were losing market share and revenue and they noticed that a direct B2C interaction could capture more market share, increase commissions, generate new sales channels, or further expand opportunities. After all, they have significant experience in the market. After evaluating all the risks and investments, the company founder and CEO, a “baby boomer”[1](https://wso2.com/whitepapers/a-pragmatic-approach-to-rock-your-api-strategy/#tag1), starts spreading the word that the company was “investing in that thing called APIs. And that API will save our ship!”

3.2 Defining your criteria for selecting some solution/partner
==============================================================

It’s important you define some criteria when you have many solutions and partners available out there. For instance, Hostelera used the following criteria:

*   Some solution where it’s possible to design the APIs as drafting/mocking before any implementation (**_API: First in the veins_**)
*   _A cloud-based solution_ to get the initial project delivered quickly, but according to the traditional IT “owner” of Hostelera, eventually to be hosted in their data center in the future, and using the same solution from a cloud provider or on-premises or hybrid.
*   Expand a third-party ecosystem to reach new consumers by defining a very cool marketplace (an **API Store/API Portal**), with many social resources, an API rating, and user comments(engagement), to be able to generate a pleasant **developer community**, integrating _Hostelera booking_ functionalities directly into their mobile and other applications.
*   A **solid API Gateway** that’s able to connect API callers to the backend legacy systems in Hostelera, which still uses a very old database based on Informix, and have a bunch of libraries written in C and C++ for a set of features and calculations. Modernizing this system can now be considered, as long as the new system can be accessed using the new APIs; putting the new system in place will be transparent to the API users).
*   Able to get their **team up and running** with a **minimal** solution in a few days or if possible in a few hours. This agility is important to test ideas and quickly refine them to achieve maximum business impact.

Defining the right path forward is very important. For this reason, with the organization’s support, try to evaluate what’s really important to your business and try looking for a platform that is able to accomplish your goals within your budgets and expectations. Moreover, it’s important to measure the quality and good reference cases as well. Define your criteria and go to market.

3.3 Adoption Strategy
=====================

It’s crucial to involve your technology partner in your adoption process. Usually, we recommend an agile approach, based on quick sprints, where the most important goal is to have something ready in a short time. The ideal timeframe would be 1 month (no more than this, but might be even less); once you extend that deadline you can miss your focus and overwhelm your team. It’s important to achieve a quick win or to discover what’s preventing a win quickly so you can adjust your plans and try again. That is the most important point at this moment: to reach a **quick win**!

The organization might be waiting for fast results, but think that everything must be incremental and iterative in order to have a pragmatic and objective adoption.

As a proposal for timelines, we suggest the following:

<img class="s t u ga ai" src="https://miro.medium.com/max/3516/1\*bBus5qLIVXSmkUIdJSvd3g.png" width="1758" height="1340" srcSet="https://miro.medium.com/max/552/1\*bBus5qLIVXSmkUIdJSvd3g.png 276w, https://miro.medium.com/max/1104/1\*bBus5qLIVXSmkUIdJSvd3g.png 552w, https://miro.medium.com/max/1280/1\*bBus5qLIVXSmkUIdJSvd3g.png 640w, https://miro.medium.com/max/1400/1\*bBus5qLIVXSmkUIdJSvd3g.png 700w" sizes="700px" role="presentation"/>

Proposal of a Very Agile Sprint for an MVA of an API Initiative

3.3.1 What are MVP and MVA?
---------------------------

A **minimum viable product, or MVP** (or minimum delivery possible in a certain time period), is the minimum of a minimum for your product/idea works. Note that an MVP launch might be totally incremental and versionable, where you can evolve with every new interaction. The main idea of your MVP is that in a single month (or less) you could have something like [https://api.mycompany.com,](https://api.mycompany.com,) bootstrapping your API initiative, making it real, and anything else that event might mean for your organization:

*   You had solved the initial issues and/or opportunities to execute your first APIs, and now you can prove that your initiative is able to **attract** **investments** and _get boosted_.
*   You shall be happy because you launched something that you will not regret, and you will be helping your organization with a new way to look at how things can be easily consumable and programmable; you now have the way to connect the dots and make the business connect even remote dots more easily.

Again, your MVP/initiative shall be incremental and continuous, always adding new capabilities and reusing what you already did as illustrated in Figure 5 below.

<img class="s t u ga ai" src="https://miro.medium.com/max/1600/0\*Ks6lpHJSJ9idZ0Kx.png" width="800" height="507" srcSet="https://miro.medium.com/max/552/0\*Ks6lpHJSJ9idZ0Kx.png 276w, https://miro.medium.com/max/1104/0\*Ks6lpHJSJ9idZ0Kx.png 552w, https://miro.medium.com/max/1280/0\*Ks6lpHJSJ9idZ0Kx.png 640w, https://miro.medium.com/max/1400/0\*Ks6lpHJSJ9idZ0Kx.png 700w" sizes="700px" role="presentation"/>

Figure 5: How a MVP must evolve — [https://blog.engineyard.com/2015/actually-mvp](https://blog.engineyard.com/2015/actually-mvp)

A **minimum viable architecture, or MVA**, is the minimum architecture that you will use to build your services that will be exposed as APIs. There are companies that are able to reuse their legacy integrations, actual integrations, database schemas, or even the database’s components, such as Stored Procedures; it can also include those that contain a bunch of business logic inside. Note that your MVA is also incremental and continuous, and eventually you might change that database vendor dependency and replace those stored procedures for cool and fancy microservices deployed in a very fashion orchestrated docker cluster. However, other companies will start from scratch and rewrite some of their new services using Java, Go,.Net, Python, Elixir, etc. but this is not relevant to your API layer. Hence, such important decisions might be taken during this period. They key is to keep the architecture resilient enough in order to accommodate any scenario you might face from now on.

_Some common questions during that period might be_

*   Could I reuse my stored procedures, packages as services exposed via REST/SOAP? How hard and productive will it be?
*   Can I still use my existing messaging queues transactions connected to my new services and APIs?
*   That file integrations that results in inserts in some of those tables in the database are ready and good enough to be exposed via my new services and consequently as my new APIs?

The answers for that and a long list of potential other questions will be in the result of the alignment of your MVA with your MVP. In other words, what can you do to accelerate your MVP? Keep in mind that once the MVP is ready, never forget about the basics regarding **agile methods** because at any moment you evaluate your architecture and promote/expose services in the most convenient way for you. However, keep in mind that you have to align the expectations, timing, the MVP, and the MVA as everything is sort of connected.

Some organizations, for instance, already have [their enterprise service bus (ESBs)](https://martinfowler.com/articles/microservices.html), which might be already exposing many services. There is no issue getting started with this as you don’t have to ‘change the team that’s winning the game.’ We too have seen many customers using different flavors of ESBs, like exposing SOAP services and for powerful API Gateway, the task of converting SOAP to REST is _something incredibly easy_. Although [ESBs are still prevalent](https://martinfowler.com/articles/microservices.html), some organizations simply don’t like such technology for many different reasons, and they prefer microservices, micro-integrations, or related approaches. It’s alright to follow the same model unless the API gateway in your [API Manager](https://wso2.com/api-management/features/) Suite is not capable of supporting such challenges and you’re faced with a very agile environment for architecture decisions.

4\. Look: Evaluate: Repeat
==========================

<img class="s t u ga ai" src="https://miro.medium.com/max/1600/0\*OOYHBOuAvN2pR6Qy.png" width="800" height="226" srcSet="https://miro.medium.com/max/552/0\*OOYHBOuAvN2pR6Qy.png 276w, https://miro.medium.com/max/1104/0\*OOYHBOuAvN2pR6Qy.png 552w, https://miro.medium.com/max/1280/0\*OOYHBOuAvN2pR6Qy.png 640w, https://miro.medium.com/max/1400/0\*OOYHBOuAvN2pR6Qy.png 700w" sizes="700px" role="presentation"/>

Figure 6 — Look, Evaluate, Repeat Proces (LER)

It’s crucial to check at the end of each phase what worked and what didn’t and adjust the airplane’s wings while it’s in flight, in keeping with the realities of today’s connected world. There is no magic recipe or any phenomenal book that might be able to help organizations **transform and reach the digital era**. To **transform**, it’s necessary to gain as much insights, information, and indicators as you can, evaluate them, and based on facts and definitely with a pinch of creativity and courage make things happens.

5\. Conclusion
==============

This post was not intended to be a blockbuster, but to give you a sharp orientation on how to conduct an API strategy adoption. It demonstrates the most pragmatic way with some insights, and by sharing real experiences from some of our consultants on the field, the ones that had looked at some eyes that found happiness in had delivered a good value, and others that are still looking to solve their issues. At the end of the day, most theories get tossed when an initiative does not succeed. Therefore, we described some primordial phases in adopting APIs. There are a bunch of other topics that were not covered in this paper, such as

*   How are you planning your integration architecture? Microservices or lightweight integrations platforms?
*   How will your continuous delivery work? How will it be aligned with your DevOps?
*   How are you thinking about securing your organization in that digital world?
*   How are you treating your analytics? Does real-time analytics impacts your business?

Many of those points, will vary according to your existing or chosen technological partners, while some of those will allow you to use what you have at home; others can bring you new practices that will let you start from scratch, what can be good or not, but in the end, it will drive us to one of the points in that whitepaper: “What is important for you and your company?” Can you recall the criterias topic that we mentioned before? That is the mental trigger that we would like to take with you.

6\. References
==============

*   \[1\] Baby boomers:  
    [https://en.wikipedia.org/wiki/Baby\_boomers](https://en.wikipedia.org/wiki/Baby_boomers)
*   [https://martinfowler.com/articles/microservices.html](https://martinfowler.com/articles/microservices.html)
*   [https://www.gartner.com/doc/3217617/api-economy-turning-business-platform](https://www.gartner.com/doc/3217617/api-economy-turning-business-platform)
*   [https://www.forrester.com/report/A+Developers+Guide+To+Forresters+Strategies+For+API+Success/-/E-RES122957](https://www.forrester.com/report/A+Developers+Guide+To+Forresters+Strategies+For+API+Success/-/E-RES122957)

