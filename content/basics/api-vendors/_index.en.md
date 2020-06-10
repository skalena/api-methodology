---
title: API Vendors
weight: 15
---

This section will cover some interesting API's solutions vendors and some summary about them. In addition, we will classify the kind/stereotype of available solutions.

## Definitions

Here are definitions of terms that will be referred to repeatedly during this article for your reference. 

-   **[Proxy](https://en.wikipedia.org/wiki/Proxy_server)  –**  A server that acts as an intermediary for requests from clients seeking resources from servers that provide those resources.
-   **Reverse Proxy –**  Type of proxy that retrieves resources on behalf of a [client](https://en.wikipedia.org/wiki/Client_(computing) "Client (computing)") from one or more [servers](https://en.wikipedia.org/wiki/Server_(computing) "Server (computing)")  and then returns these resources to the client, appearing as from the proxy.
-   **API Gateway** – A system to that receives API requests, performs traffic routing and management to the backend services and returns a response to the client / end user requester.
-   **Ingress –**  Incoming traffic (north/south) to a cluster running your application services. When referred to in  [Kubernetes](https://www.solo.io/solutions/solutions-kubernetes-ingress/)  environments, an Ingress Controller object exists to specifically fulfill this function.
-   **North/South –**  This direction of traffic is defined as the client to server traffic, between the clients or end users outside of the datacenter to the network inside the datacenter.
-   **East/West –** The service to service communication that occurs within the cluster and does not leave your network.
-   **Service Mesh**  – An example of east/west traffic using an architecture where a proxy sidecar is deployed alongside each service to manage the traffic.
*Source: https://solo.io* 

## Commercial Vendors
There are several solutions very interesting in the market, we will mention the following ones:

 - **[**Sensedia**](https://sensedia.com/en/)** - A Brazilian company that counts with very strong consulting services and a very complete solution. They have so many interesting customers in financial industry, as well very emblematic success cases. Actually they are expanding to other territories, such as Europe and some countries in Latin America. Both Forrester and Gartner shares very good comments and analyisis about them. 
 - **[Apigee](https://cloud.google.com/apigee)** - One of the pioneers in API Market, they were acquired by Google and have been dominant in many Gartner and Forrester reports. 
 - **[IBM API Connect](https://www.ibm.com/cloud/api-connect)** -  Original StrongLoop, acquired by IBM. Interesting solution provided by IBM. 
 - [**Axway**](https://www.axway.com/en/products/api-management) - Together with Apigee they are one of the pioneers in the market. 
 - [**CA API Gateway**](https://www.broadcom.com/products/software/api-management/layer7-api-gateways) - Originally Layer7 API Gateway, acquired by CA and later one acquired by Broadcom. 
 - **[**OpenLegacy**](https://www.openlegacy.com/)** - A very interesting solution, with so many accelerators, code generators and enablers for API inititives. 
 - [**AWS API Gateway**](https://aws.amazon.com/api-gateway/) - Proprietary API Gateway running only in AWS Environment and very dependent from AWS Ecosystem. 
  - [**MuleSoft**](https://www.mulesoft.com/platform/enterprise-integration) - Proprietary API solution acquired by Salesforce.

 

## Enterprise OpenSource
The following solutions are Opensource with Enterprise Subscriptions (SLA and Support). The solutions listed bellow have what they call "Community versions", as well as "Enterprise Versions" with exclusive features.  

 - [**Kong**](https://konghq.com/) - They are by far one of the most known API Gateways in the market. Kong runs on top of ***NGINX***, and it uses Lua(*a programming language created in Rio de Janeiro in Brazil*), to extend and create its plugins. Kong can be classified as an API Proxy. Actually KongHQ, the company behind Kong Community is actually delivering very interesting components, such as Kubernetes Ingress Controller and other very interesting components.  
 - [**Tyk**](https://tyk.io/) - A very performatic API Gateway, API Proxy, API Analytics and Developer Portal solution, which according to our evaluation is a great solution for customers looking for a Cloud based solution. According to their Github sources, they are using **GoLang** to build their solutions. 
 - [**WSO2**](https://www.wso2.com) - One of the most complete plataforms in API Management industry. They have several components out-of-the-box, such as a Key Manager for generating and validating tokens, as well powerful real-time analytics engine. 
 - **Skalena** - We are working in to have our own API Gateway, this is a working in progress, that we would be announcing soon. 

 ## Did not found your preferred Solution here? 
Please, if you would like to see or improve the references about the products here, please, reach us at api-methodology (a) skalena.com. 