---
date: 2016-04-09T16:50:16+02:00
title: Infrastrucutre
weight: 20
---

## Virtual Machines
There are still several organizations relying on VMs in order to leverage and optimize their infrastructure. We do believe that some traditional markets will still be using this technology for years ahead.  However there are a lot of technologies that can help you manage an environemnt like that: 

 - [Vagrant](https://www.vagrantup.com/): It provides the same, easy workflow regardless of your role as a developer, operator, or designer. It leverages a declarative configuration file which describes all your software requirements, packages, operating system configuration, users, and more.

## Containers (Docker)
Containers is not a new technology, we saw it first initially in mid of 2000's in Solaris, however Docker came to be established as a standard in the market. If you would like to see a Docker alternative, we do recommend you take a look at: [https://linuxcontainers.org/](https://linuxcontainers.org/).
Move towards containers as a factible strategy is a great step for a company that is modernizing their infrastructure. 
We have been using Docker as an intermediate point between VMs and Kubernetes, and in order to have a fully orquestrated environment even in Docker, we have been using Docker Swarm, and its way to organize a set/group of machines (containers) that can be scalable according to the business's needs. 

## Kubernetes 
Kubernetes is a container orchestrator solution, which aims to solve the managing, life-cycle, networking and other componentes when you have to run several containers at the same time. It was created and opensourced by Google.
The organizations can install and run Kubernetes AKA "k8s", on-premises, or to use one of the distributions from major public cloud providers, such as Google, Azure and AWS. 
To execute the whole microservices architecture using K8S requires to shift some paradigms and way to look the old-fashion or traditional infraestrucutre. 

## API Firewall
In front of API Gateways we can find out a new layer in market: API Firewalls. The actual markets considers that a regular WAF (Web Application Firewall), can be enough to protect their APIs, that is not so true. 

### OWASP API  - Security Top 10
As a result of the growing threat landscape and increasing usage of APIs, the OWASP API Security Top 10 Project was launched to help companies address security vulnerabilities specific to APIs: 
* API1 : Broken Object Level Access Control
* API2 : Broken Authentication
* API3 : Excessive Data Exposure
* API4 : Lack of Resources & Rate Limiting
* API5 : Missing Function Level Access Control
* API6 : Mass Assignment
* API7 : Security Misconfiguration
* API8 : Injection
* API9 : Improper Assets Management
* API10 : Insufficient Logging & Monitoring

![enter image description here](https://h3g3k7u7.stackpathcdn.com/wp-content/uploads/2020/02/logo_lighta-130x36.png)
We would like to present the 42Crunch solution, that aims to work as a dedicated solution just as an API Firewall. With 42Crunch, security can be easily defined in OpenAPI contracts, tested for bad behavior, and protected by a micro API firewall with the click of a button – ensuring continuous, unparalleled protection across the entire API lifecycle.

