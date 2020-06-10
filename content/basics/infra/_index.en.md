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

```mermaid
gantt  dateFormat
YYYY-MM-DD  title  Adding GANTT diagram functionality to mermaid  section  A section  Completed  task :done, des1, 2014-01-06,2014-01-08  Active  task :active, des2, 2014-01-09, 3d  Future  task : des3, after des2, 5d  Future  task2 : des4, after des3, 5d  section  Critical tasks  Completed  task in the critical line :crit, done, 2014-01-06,24h  Implement  parser and jison :crit, done, after des1, 2d  Create  tests for parser :crit, active, 3d  Future  task in critical line :crit, 5d  Create  tests for renderer :2d  Add  to mermaid :1d
```


