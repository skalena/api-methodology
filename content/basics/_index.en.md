---
title: API First
weight: 5
pre: "<b>1. </b>"
chapter: true
---

### Chapter 1

1\. API First Concepts
======================

**APIs are the glue of the digital world.** They are embeddable components like legos, in which the edges are connectable via HTTP Protocol. 

API First ideates about to draft the ideas starting by the APIs, in common sense, it means that if you have good APIs, you will have great applications. 

Everything starts at the level of the contract, which is the definition of the API's capabilities, in other words: What the API does and how. 

These definitions are defined under industry standards, which are Open API Specifications (OAS). The definition/contract represented through a JSON or YAML file, and it is commonly called the "Swagger file".

## Designing the API Contracts

To create great APIs, always starts on to clear and concise contracts ([OAS/Swagger](https://www.openapis.org)), although, to create those contracts is not an easy task, many misconceptions and learning curve can damage your API contract. 

## Tooling

One of the most known tool for creating API contracts is no doubt: [Swagger Editor](http://editor.swagger.io/?_ga=2.118868105.1682952795.1588217501-359518690.1588217501) by SmartBear, in fact if you go to [https://swagger.io](https://swagger.io) you will discover very interesting solutions.  They also have solutions to render your [API Contract](https://petstore.swagger.io/?_ga=2.89613339.1682952795.1588217501-359518690.1588217501), and also a very interesting way to use [Code Generators](https://github.com/swagger-api/swagger-codegen), either for your API server side and also client side. 

## Skalena Tooling for API Contract

After several projects and consulting engagements, we decided to use a free solution called Stop Light:

![StopLight Editor](https://skalena.net/blog/wp-content/uploads/2020/04/image-1-1024x568.png)

We decided to use this tool, simply because we can promote very collaborative sessions with our customers and then define together how we will define the API, exactly which kind of data it will expose, as well as which methods, parameters and in the end, we can check the generated Swagger/OAS file in a very two-way effective manner. 
