---
title: WSO2 Micro EI - Creating APIs
weight: 3
---

## Introduction

WSO2 is an opensource vendor that delivers a platform which counts with a component for integration (Enterprise Integrator), API Manager and Identity Server for IAM - Identity and Access Manager.

**Skalena**  counts with the WSO2 pioneers in Latin America, responsible for more than 30 sucessful deployments in Mexico, Argentina, Colombia, Ecuador and Brazil. 

In This page, you will be able to find informations specialy related to Integration and API Best practices.

## Pre-requirements 

Please, make sure you have the following components installed into your computer: 

* Visual Studio Code
* Docker 
* JDK 1.8 or 11
* Maven
{{% notice info %}}
If you are using Windows, and the version does not supports docker, we recommend you to use Vagrant to setup/run a VM Box into your machine, or to run a linux CentOs or Ubuntu into a VM in VirtualBox or VMWare. 
{{% /notice %}} 

## Audience

You have to know the basics about WSO2 EI. Skalena delivers a free and online training about WSO2 Integrator, unfortunately this is available just in Portuguese: https://skalena.thinkific.com/courses/wso2-integrator-fundamentals



## Configuring Visual Studio Code 

Please, make sure that your Visual Studio is properly configured to use Java, Maven and please, install the WSO2 Extension for Integration.

Here are the information about Visual Studio Code: [https://marketplace.visualstudio.com/items?itemName=WSO2.wso2ei](https://marketplace.visualstudio.com/items?itemName=WSO2.wso2ei). 

#### Requirements:

-   Java JDK 8 at least
-   The  `JAVA_HOME`  environment variable must be set
-   **Note:**  The path should end at the parent folder that contains the  `bin`folder.
    -   **Example Path:**  `/usr/lib/jvm/java-1.8.0`  if  `bin`  exists at  `/usr/lib/jvm/java-1.8.0/bin`
-   [Maven 3.5.0 or later](https://maven.apache.org/download.cgi)

#### Quick Start:

-   **Step 1.**  Install the Synapse extension for Visual Studio Code.
-   **Step 2.**  Open or create a Synapse Project and start integration!
    -   Extension is activated when you first access an xml file or via the command  `WSO2EI: Activate WSO2 EI Tooling`  through command palette

#### Useful Commands:

Open the Command Palette ( [Command] + [Shift] + [P] on macOS and [Ctrl] + [Shift] + [P] on Windows/Linux) and type in one of the following commands:

![enter image description here](https://raw.githubusercontent.com/wso2/ei-tooling-vscode/master/vscode-plugin/docs/AutoCompletion.gif)

### Recipe Code

Please, clone the recipe from here: https://github.com/skalena/recipes/tree/master/wso2-ei-micro-01/skalena-recipes

Here a little about the execution: 

## Skalena Recipes - WSO2 01

Target Recipes:
* Simple API
* Benchmarks
* API Façade Samples 

Please refer to this content in terms of pre-requirements: 

## Building

Clone the recipes repo:

    git clone https://github.com/skalena/recipes

Go to this folder sample: `wso2-ei-micro-01/skalena-recipes` and from there open the Visual Studio, you can type `code .` , if your Visual Studio is well-configured.

### Building the Project and Docker Image (EI Microintegrator)

Simple type: `./buildDockerImage.sh`  , done. 

### Running the Docker Image  (EI Microintegrator)

Simple type: `./runDockerImage.sh`  , done. 
The execution will show something like:

    ....... Running Docker image now ....
    f7d0daadb9d5f682699ae9850e68c0c0d6a35c3078ab65e99ad1ad7d391cda09

### Handling Docker

In order to know which containers are running, you can type: `docker ps` .  Then you will see a console output like similar to this:
docker ps

    CONTAINER ID  IMAGE  COMMAND  CREATED STATUS  PORTS  NAMES
    
    [here will be your id] skalena:recipe-ei-01 "/home/wso2carbon/do…" 41 seconds ago  Up 40 seconds 0.0.0.0:8290->8290/tcp, 8253/tcp, 0.0.0.0:9164->9164/tcp jovial_blackwell

In order to see the logs you have to execute `docker logs -f <your-container-id-execution>` 

And then you will see the logs pretty much like this: 

    $ docker logs -f f7d0daadb9d5
    
    [2020-07-03 05:10:02,204]  INFO {org.apache.synapse.deployers.SequenceDeployer} - Sequence named 'provider-acme' has been deployed from file : /home/wso2carbon/wso2mi-1.1.0/tmp/carbonapps/-1234/1593753002167skalena-recipes_1.0-SNAPSHOT.car/provider-acme.xml_1.0-SNAPSHOT/provider-acme.xml-1.0-SNAPSHOT.xml
    
    [2020-07-03 05:10:02,215]  INFO {org.apache.synapse.deployers.SequenceDeployer} - Sequence named 'provider-tabajara' has been deployed from file : /home/wso2carbon/wso2mi-1.1.0/tmp/carbonapps/-1234/1593753002167skalena-recipes_1.0-SNAPSHOT.car/provider-tabajara.xml_1.0-SNAPSHOT/provider-tabajara.xml-1.0-SNAPSHOT.xml
    
    [2020-07-03 05:10:02,221]  INFO {org.apache.synapse.deployers.SequenceDeployer} - Sequence named 'sequence-fault-facade' has been deployed from file : /home/wso2carbon/wso2mi-1.1.0/tmp/carbonapps/-1234/1593753002167skalena-recipes_1.0-SNAPSHOT.car/sequence-fault-facade.xml_1.0-SNAPSHOT/sequence-fault-facade.xml-1.0-SNAPSHOT.xml
    
    [2020-07-03 05:10:02,241]  INFO {org.apache.synapse.rest.API} - Initializing API: simple_api
    
    [2020-07-03 05:10:02,242]  INFO {API_LOGGER.simple_api} - Initializing API: simple_api
    
    [2020-07-03 05:10:02,247]  INFO {org.apache.synapse.deployers.APIDeployer} - API named 'simple_api' has been deployed from file : /home/wso2carbon/wso2mi-1.1.0/tmp/carbonapps/-1234/1593753002167skalena-recipes_1.0-SNAPSHOT.car/simple_api_1.0-SNAPSHOT/simple_api-1.0-SNAPSHOT.xml
    
    [2020-07-03 05:10:02,275]  INFO {org.apache.synapse.rest.API} - Initializing API: facade
    
    [2020-07-03 05:10:02,276]  INFO {API_LOGGER.facade} - Initializing API: facade
    
    [2020-07-03 05:10:02,277]  INFO {org.apache.synapse.core.axis2.Axis2SynapseEnvironment} - Continuation call is set to true
    
    [2020-07-03 05:10:02,278]  INFO {org.apache.synapse.deployers.APIDeployer} - API named 'facade' has been deployed from file : /home/wso2carbon/wso2mi-1.1.0/tmp/carbonapps/-1234/1593753002167skalena-recipes_1.0-SNAPSHOT.car/facade_1.0-SNAPSHOT/facade-1.0-SNAPSHOT.xml
    
    [2020-07-03 05:10:02,279]  INFO {org.wso2.micro.integrator.initializer.deployment.application.deployer.CAppDeploymentManager} - Successfully Deployed Carbon Application : skalena-recipesCompositeApplication_1.0-SNAPSHOT{super-tenant}
    
    [2020-07-03 05:10:02,339]  INFO {org.apache.synapse.transport.passthru.core.PassThroughListeningIOReactorManager} - Pass-through HTTP Listener started on 0.0.0.0:8290
    
    [2020-07-03 05:10:02,339]  INFO {org.apache.axis2.transport.mail.MailTransportListener} - MAILTO listener started
    
    [2020-07-03 05:10:02,343]  INFO {org.apache.synapse.transport.passthru.core.PassThroughListeningIOReactorManager} - Pass-through HTTPS Listener started on 0.0.0.0:8253
    
    [2020-07-03 05:10:02,345]  INFO {org.wso2.micro.integrator.initializer.StartupFinalizer} - WSO2 Micro Integrator started in 9 seconds
    
    [2020-07-03 05:10:02,415]  WARN {org.wso2.micro.integrator.management.apis.ManagementInternalApi} - Micro Integrator Management REST API is enabled
    
    [2020-07-03 05:10:02,487]  INFO {org.apache.synapse.transport.passthru.core.PassThroughListeningIOReactorManager} - Pass-through EI_INTERNAL_HTTPS_INBOUND_ENDPOINT Listener started on 0.0.0.0:9164

## Testing

Now let's test our stuff,  first, let's try the simple_api API call: 

    curl http://localhost:8290/simple_api -v 

Response:
    
    * Connected to localhost (::1) port 8290 (#0)
    
    > GET /simple_api HTTP/1.1
    
    > Host: localhost:8290
    
    > User-Agent: curl/7.64.1
    
    > Accept: */*
 
    < HTTP/1.1 200 OK
    
    < Accept: */*
    
    < Access-Control-Allow-Methods: GET
    
    < Host: localhost:8290
    
    < Access-Control-Allow-Headers:
    
    < Content-Type: application/json; charset=UTF-8
    
    < Date: Fri, 03 Jul 2020 05:16:03 GMT
    
    < Transfer-Encoding: chunked
    
    * Connection #0 to host localhost left intact
    
    {"message":{"msg":" That is the message back from WSO2 Micro EI at 2020-07-03T05:16:03 "}}* 

### API Façade

Now , let's execute the API Façade via API URI parameter (provider==acme): `curl http://localhost:8290/api-facade/provider/acme -v`

Reponse: 

    < HTTP/1.1 200 OK
    < Accept: */*   
    < Access-Control-Allow-Methods: GET   
    < Host: localhost:8290   
    < Access-Control-Allow-Headers    
    < Content-Type: application/json; charset=UTF-8   
    < Connection: Close   
    < Date: Fri, 03 Jul 2020 05:18:47 GMT  
    < Transfer-Encoding: chunked
    * Closing connection 0
    
    {"resultado":{"msg":"ACME"}}

Now, let's execute passing the provider via HTTP Header: 

    curl http://localhost:8290/api-facade/provider -v -H "X-Skalena-Provider:acme"

Response: 

    > X-Skalena-Provider:acme
    < HTTP/1.1 200 OK
    < Accept: */*
    < Access-Control-Allow-Methods: GET
    < X-Skalena-Provider: acme
    < Host: localhost:8290
    < Access-Control-Allow-Headers:
    < Content-Type: application/json; charset=UTF-8
    < Date: Fri, 03 Jul 2020 05:22:38 GMT
    < Transfer-Encoding: chunked
    {"resultado":{"msg":"ACME"}}

Now, let's simulate a call where the provider does not exists:

    curl http://localhost:8290/api-facade/provider -v -H "X-Skalena-Provider:mesbla"

Response: 

    > X-Skalena-Provider:mesbla
    < HTTP/1.1 404 Provider not found!
    < api-error-client: Provider not found, please refer to an existing one and see the logs
    < Accept: */*
    < Access-Control-Allow-Methods: GET
    < X-Skalena-Provider: mesbla
    < Host: localhost:8290
    < Access-Control-Allow-Headers:
    < Content-Type: application/json; charset=UTF-8
    < Date: Fri, 03 Jul 2020 05:24:08 GMT
    
    Connection #0 to host localhost left intact
    
    {"error":{"msg":"Sequence named Value {name ='null', expression =get-property('provider')} cannot be found","provider":"provider-mesbla"}}* 

### Benchmark 

Please, just call the shell script: ./benchmark.sh , and that's all, you will see 1000 calls with 100 concurrents clients, you will a result like that: 

    This is ApacheBench, Version 2.3 <$Revision: 1843412 $>
    
    Copyright 1996 Adam Twiss, Zeus Technology Ltd, http://www.zeustech.net/
    
    Licensed to The Apache Software Foundation, http://www.apache.org/

    Benchmarking localhost (be patient)

    Server Software:
    
    Server Hostname: localhost
    
    Server Port: 8290
 
    Document Path: /simple_api
    
    Document Length: 90 bytes
 
    Concurrency Level: 100
    
    Time taken for tests: 10.802 seconds
    
    Complete requests: 1000
    
    Failed requests: 0
    
    Total transferred: 314000 bytes
    
    HTML transferred: 90000 bytes
    
    Requests per second: 92.58 [#/sec] (mean)
    
    Time per request: 1080.181 [ms] (mean)
    
    Time per request: 10.802 [ms] (mean, across all concurrent requests)
    
    Transfer rate: 28.39 [Kbytes/sec] received
 
    Connection Times (ms)
    
    min mean[+/-sd] median max
    
    Connect: 0 1 1.4 0 6
    
    Processing: 7 1045 338.2 1175 1498
    
    Waiting: 7 1044 338.2 1173 1498
    
    Total: 7 1045 337.8 1175 1498

    Percentage of the requests served within a certain time (ms)
    
    50% 1175
    
    66% 1254
    
    75% 1269
    
    80% 1280
    
    90% 1338
    
    95% 1443
    
    98% 1480
    
    99% 1492
    
    100% 1498 (longest request)

## Recipe Overview

WSO2 Enterprise Integrator uses [Apache Synapse](https://synapse.apache.org/), which offers a way to create integrations and mediations using XML as the configuration language. 

Looking our example: 

    └── main
        ├── registry-resources
        │   └── artifact.xml
        └── synapse-config
            ├── api
            │   ├── facade.xml
            │   └── simple_api.xml
            ├── artifact.xml
            ├── endpoints
            ├── inbound-endpoints
            ├── local-entries
            ├── message-processors
            ├── message-stores
            ├── proxy-services
            ├── sequences
            │   ├── provider-acme.xml
            │   ├── provider-tabajara.xml
            │   └── sequence-fault-facade.xml
            ├── tasks
            └── templates
                └── send-http-code-and-message.xml

The most importante files are: 

* The `api` folder, which has 2 files: `simple-api.xml` and `facade.xml`. 
* The `sequence` folder, contains the extensions/components that we call sequences. 
* The `artifact.xml` is the file that manage which componentes will be installed in the run time.

### Let's check the code

Understanding the simple-api.xml , and the anatomy of the "small" program: 

{{<mermaid align="left">}}
graph LR;
    A[HTTP Invocation GET, POST, ...] -->|http transport| B(simple_api)
    B --> C[API URI]
    C -->|Payload| D[InSequence]
    C -->|Payload| E[OutSequence]
    C -->|Payload| F[Fault Sequence]
{{< /mermaid >}}

The source-code is the following one:

    <api context="/simple_api" name="simple_api" xmlns="http://ws.apache.org/ns/synapse">
        <resource methods="GET">
            <inSequence>
                <log level="custom">
                    <property name="status" value="API invocation received ...."/>
                </log>
                <property name="date" expression='get-property("SYSTEM_DATE", "yyyy-MM-dd&apos;T&apos;HH:mm:ss")' scope="default"/> 
                <payloadFactory media-type="xml">
                    <format>
                        <message xmlns="">
                            <msg> That is the message back from WSO2 Micro EI at $1 </msg>
                        </message>
                    </format>
                    <args>
                        <arg evaluator="xml" expression="get-property('date')"/>
                    </args>
    
                </payloadFactory>
                <property name="messageType" scope="axis2" type="STRING" value="application/json"/>
                <respond/>
            </inSequence>
            <outSequence/>
            <faultSequence/>
        </resource>
    </api>

The lonely portions invoked is the URI "/" when the GET HTTP is invoked, and just the the InSequence portion create a payload with a XML containing some data example, and convert it to a JSON format.

### API Façade + Command Pattern

#### API Facade
> The  **API Facade**  Design  **Pattern**  is a solution to a design
> problem that arises for  **API**  designers when back-end and internal
> systems of record are too complex to expose directly to application
> developers. The goal of an  **API Facade Pattern**  is to
> articulate internal systems and make them useful for the app
> developer.

Source: [https://pages.apigee.com/rs/apigee/images/api-facade-pattern-ebook-2012-06.pdf](https://pages.apigee.com/rs/apigee/images/api-facade-pattern-ebook-2012-06.pdf)

#### Command Pattern 
> In object-oriented programming, the command pattern is a behavioral
> design pattern in which an object is used to encapsulate all
> information needed to perform an action or trigger an event at a later
> time. This information includes the method name, the object that owns
> the method and values for the method parameters.

Source: [https://en.wikipedia.org/wiki/Command_pattern](https://en.wikipedia.org/wiki/Command_pattern)

We decided to implement these 2 patterns in order to help customer re-use components and pieces of code when they are creating the API mediations and/or orchestrations. 

Let's figure out the following scenario:

 - Just one API, receiving a common (the same) Payload
 - According to the `"driver"/"provider"`, this API dispatches this common payload to be treated by this `"driver"`. 
 - Let's recall the Database instructions execution: Whe have the common `payload` (the `sql)`, that can be dispatched to several different drivers, such as oracle, mysql, db2. etc. 

In our case, the have the following: 

- API receives the invocation
- API capture the "command" or which is the "driver" requested 
- API according to the name, injects the sequece that is responsible to handle the payload according to the driver/provider.
- If the things works well, client receives the HTTP 200
- If the provider is not found, a HTTP 404 is returned. 

See the code that implements the sceanarios above: 

    <?xml version="1.0" encoding="UTF-8"?>
    
    <api context="/api-facade" name="facade" xmlns="http://ws.apache.org/ns/synapse">
        <resource methods="GET" uri-template="/provider/{provider}">
        <inSequence>
            <log level="custom">          
                 <property name="provider" expression="fn:concat('provider-',get-property('uri.var.provider'))"/>
            </log>
    
            <property name="provider" expression="fn:concat('provider-',get-property('uri.var.provider'))" type="STRING"/>
    
           <sequence key="{get-property('provider')}"/> 
    
           <property name="NO_KEEPALIVE" value="true" scope="axis2"/>
    
           <property name="messageType" scope="axis2" type="STRING" value="application/json"/>
            
           <respond/>
    
            </inSequence>
            <outSequence>
                <!-- Define outflow mediation logic here -->
            </outSequence>
            <faultSequence>
               <log level="custom">
                  <property name="text" value="An unexpected error occured"/>
                  <property name="message" expression="get-property('ERROR_MESSAGE')"/>   
                  <property name="provider" expression="fn:concat('provider-',get-property('uri.var.provider'))" type="STRING"/>
       
               </log> 
               <payloadFactory media-type="xml">
                            <format>
                                <error xmlns="">
                                    <msg>$1</msg>
                                    <provider>$2</provider>
                                </error>
                            </format>
                            <args>
                                 <arg evaluator="xml" expression="get-property('ERROR_MESSAGE')"/>
                                  <arg evaluator="xml" expression="get-property('provider')"/>
                            </args>
               </payloadFactory>
               <property name="HTTP_SC_DESC" value="Provider not found! " scope="axis2"/>
               <header name="api-error-client" value="Provider not found, please refer to an existing one and see the logs" scope="transport"/>
               <property name="messageType" scope="axis2" type="STRING" value="application/json"/>
               <respond/>
            </faultSequence>
        </resource>
    
       <resource methods="GET" uri-template="/provider">
        <inSequence>
            <log level="custom">          
                 <property name="provider" expression="fn:concat('provider-',$trp:X-Skalena-Provider)"/>
            </log>
    
            <property name="provider" expression="fn:concat('provider-',$trp:X-Skalena-Provider)" type="STRING"/>
    
           <sequence key="{get-property('provider')}"/> 
    
           <property name="NO_KEEPALIVE" value="true" scope="axis2"/>
    
           <property name="messageType" scope="axis2" type="STRING" value="application/json"/>
            
           <respond/>
    
            </inSequence>
            <outSequence>
                <!-- Define outflow mediation logic here -->
            </outSequence>
            <faultSequence>
               <log level="custom">
                  <property name="text" value="An unexpected error occured"/>
                  <property name="message" expression="get-property('ERROR_MESSAGE')"/>   
                  <property name="provider" expression="fn:concat('provider-',get-property('uri.var.provider'))" type="STRING"/>
       
               </log> 
               <payloadFactory media-type="xml">
                            <format>
                                <error xmlns="">
                                    <msg>$1</msg>
                                    <provider>$2</provider>
                                </error>
                            </format>
                            <args>
                                 <arg evaluator="xml" expression="get-property('ERROR_MESSAGE')"/>
                                  <arg evaluator="xml" expression="get-property('provider')"/>
                            </args>
               </payloadFactory>
               <property name="HTTP_SC_DESC" value="Provider not found! " scope="axis2"/>
               <property name="HTTP_SC" value="404" scope="axis2"/>
               <header name="api-error-client" value="Provider not found, please refer to an existing one and see the logs" scope="transport"/>
               <property name="messageType" scope="axis2" type="STRING" value="application/json"/>
               <respond/>
            </faultSequence>
        </resource>
    
    
    </api>



