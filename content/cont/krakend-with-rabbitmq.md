---
title: KrakenD API Gateway with RabbitMQ
weight: 4
---

## Objective

We will be let KrakenD to be able to publish and consume messages from RabbitMQ. 

```mermaid
sequenceDiagram
Client ->> API-KrakenD: Send a POST
API-KrakenD-->>RabbitMQ: Publishing the Payload

```
In the above case, KrakenD will provide an out-of-the-box backend to publish a message into the specified exchange in RabbitMQ.

###  Components that we will use

* Docker - in order to easily run RabbitMQ 
* KrakenD binary (but you can use the Docker distro as well)

## Getting Started

### Running RabbitMQ server and management console

Please, run the following docker command:

    docker run -it --rm --name rabbitmq -p 5672:5672 -p 15672:15672 rabbitmq:3-management

The following result, will the a console log screen as the following ones:



    Configuring logger redirection
    
    2020-11-17 20:52:35.100 [debug] <0.287.0> Lager installed handler error_logger_lager_h into error_logger
    
    2020-11-17 20:52:35.487 [info] <0.272.0>
    
    Starting RabbitMQ 3.8.9 on Erlang 23.1.2
    
    Copyright (c) 2007-2020 VMware, Inc. or its affiliates.
    
    Licensed under the MPL 2.0. Website: https://rabbitmq.com
    ##  ##  RabbitMQ 3.8.9
    ##########  Copyright (c) 2007-2020 VMware, Inc. or its affiliates.
    ######  ##
    ##########  Licensed under the MPL 2.0. Website: https://rabbitmq.com
    
    Doc guides: https://rabbitmq.com/documentation.html
    
    Support:  https://rabbitmq.com/contact.html
    
    Tutorials:  https://rabbitmq.com/getstarted.html
    
    Monitoring: https://rabbitmq.com/monitoring.html
    
    Logs: <stdout>
    Config file(s): /etc/rabbitmq/rabbitmq.conf
    Starting broker...2020-11-17 20:52:35.491 [info] <0.272.0> 
    node : rabbit@1d1aeaabfa13
    home dir : /var/lib/rabbitmq
    config file(s) : /etc/rabbitmq/rabbitmq.conf
    cookie hash  : dSjJ44QW4pEza/vazmLqQQ==
    log(s) : <stdout>
    database dir : /var/lib/rabbitmq/mnesia/rabbit@1d1aeaabfa13

The next screeshot is the RabbitMQ Management Console URL:

![enter image description here](../images/rabbitMQ.png)

The url access is: [http://127.0.0.1:15672](http://127.0.0.1:15672/#/) , where "***guest***" works for both *user/password*.


#### RabbitMQ: **OK** 

![KrakenD logo](https://raw.githubusercontent.com/devopsfaith/krakend/master/docs/images/krakend.png)
## Creating KrakenD's Configuration

This post is based on the following documenation's page: https://www.krakend.io/docs/backends/pubsub/, in that case we will use KrakenD to automatically define a Backend to publish a payload as a message, and we can get able to read it back (consuming).

{{% notice note %}}
If you backend that interact with you messaging layer demands too much complexity, business rules,etc, we do recommend you create a Backend to treat it in a better fashion, with no limitations and able to do whatever you need.  
{{% /notice %}} 

#### KrakenD Configuration File

For this example, we will use the following krakend.json config file:

    {
       "version":2,
       "port":8080,
       "endpoints":[
          {
             "endpoint":"/produce/{key}",
             "method":"POST",
             "backend":[
                {
                   "extra_config":{
                      "github.com/devopsfaith/krakend-amqp/produce":{
                         "exchange":"testdiuscoa",
                         "durable":true,
                         "delete":false,
                         "exclusive":false,
                         "no_wait":true,
                         "mandatory":true,
                         "immediate":false,
                         "name":"radiuscoa",
                         "routing_key":"Key"
                      }
                   },
                   "host":[
                      "amqp://guest:guest@localhost:5672"
                   ],
                   "disable_host_sanitize":true
                }
             ]
          },
          {
             "endpoint":"/consume",
             "backend":[
                {
                   "extra_config":{
                      "github.com/devopsfaith/krakend-amqp/consume":{
                         "name":"queue-1",
                         "exchange":"testdiuscoa",
                         "durable":true,
                         "delete":false,
                         "exclusive":false,
                         "no_wait":true,
                         "no_local":false,
                         "routing_key":[
                            "#"
                         ],
                         "prefetch_count":10
                      }
                   },
                   "host":[
                      "amqp://guest:guest@localhost:5672"
                   ],
                   "disable_host_sanitize":true
                }
             ]
          }
       ]
    }


### Executing the KrakenD API Gateway consuming the config file

Once you have KrakenD installed into your machine, we will use the krakend binary program, that can be installed from many different plataforms(https://www.krakend.io/docs/overview/installing/)

Please, create a folder named krakend-rabbit into your machine,  copy and create a file called *krakend.json* into that created folder and type the following command:

    krakend run -c krakend.json

The KrakenD API Gateway runtime will boot in over miliseconds, with the logs and informations, as the following ones:

    krakend run -c krakend.json 
    Parsing configuration file: krakend.json
    2020/11/18 03:05:59  ERROR: unable to create the gologging logger: getting the extra config for the krakend-gologging module
    2020/11/18 03:05:59  ERROR: unable to create the GELF writer: getting the extra config for the krakend-gelf module
    2020/11/18 03:05:59  INFO: Listening on port: 8080
    2020/11/18 03:05:59  DEBUG: creating a new influxdb client
    2020/11/18 03:05:59  DEBUG: no config for the influxdb client. Aborting
    2020/11/18 03:05:59  WARNING: influxdb: unable to load custom config
    2020/11/18 03:05:59  WARNING: opencensus: no extra config defined for the opencensus module
    2020/11/18 03:05:59  WARNING: building the etcd client: unable to create the etcd client: no config
    2020/11/18 03:05:59  DEBUG: no config for the bloomfilter
    2020/11/18 03:05:59  WARNING: bloomFilter: no config for the bloomfilter
    2020/11/18 03:05:59  WARNING: no config present for the httpsecure module
    2020/11/18 03:05:59  INFO: registering usage stats for cluster ID 'F8ai6U9zv0qNuwRJrbglzP0A7to7xFVpOn9ujfccbfM='
    2020/11/18 03:05:59  DEBUG: lua: no extra config
    2020/11/18 03:05:59  DEBUG: botdetector middleware:  no config defined for the module
    2020/11/18 03:05:59  DEBUG: AMQP: amqp://guest:guest@localhost:5672: no amqp consumer defined
    2020/11/18 03:05:59  DEBUG: CEL: no extra config detected for backend /
    2020/11/18 03:05:59  DEBUG: lua: no extra config
    2020/11/18 03:05:59  DEBUG: CEL: no extra config detected for pipe /produce/:key
    2020/11/18 03:05:59  DEBUG: lua: no extra config
    2020/11/18 03:05:59  INFO: JOSE: singer disabled for the endpoint /produce/:key
    2020/11/18 03:05:59  DEBUG: lua: no extra config
    2020/11/18 03:05:59  INFO: JOSE: validator disabled for the endpoint /produce/:key
    2020/11/18 03:05:59  DEBUG: botdetector:  no config defined for the module
    2020/11/18 03:06:00  DEBUG: CEL: no extra config detected for backend /
    2020/11/18 03:06:00  DEBUG: lua: no extra config
    2020/11/18 03:06:00  DEBUG: CEL: no extra config detected for pipe /consume
    2020/11/18 03:06:00  DEBUG: lua: no extra config
    2020/11/18 03:06:00  INFO: JOSE: singer disabled for the endpoint /consume
    2020/11/18 03:06:00  DEBUG: lua: no extra config
    2020/11/18 03:06:00  INFO: JOSE: validator disabled for the endpoint /consume
    2020/11/18 03:06:00  DEBUG: botdetector:  no config defined for the module
    2020/11/18 03:06:00  DEBUG: http-server-handler: no extra config

    ![Homer Happy](https://media1.giphy.com/media/xT5LMHxhOfscxPfIfm/200.gif)

    
### Ready!

Now we can test the endpoints exposed by KrakenD that can *publish* the messages:

    curl -i --location --request POST 'http://localhost:8080/produce/foo' --data-raw '{"foo":"bar"}'
    
    HTTP/1.1 200 OK
    **Content-Type**: application/json; charset=utf-8
    **X-Krakend**: Version 1.1.1
    **X-Krakend-Completed**: false
    **Date**: Wed, 18 Nov 2020 06:12:28 GMT
    **Content-Length**: 5
    
    null

In that resource, there is no message back. 

Now let's consume the message from RabbitMQ:

    curl -i --location --request GET 'http://localhost:8080/consume'
    
    HTTP/1.1 200 OK
    
    **Content-Type**: application/json; charset=utf-8
    **X-Krakend**: Version 1.1.1
    **X-Krakend-Completed**: true
    **Date**: Wed, 18 Nov 2020 06:15:53 GMT
    **Content-Length**: 14
    
    
    {"foo":"bar"}

{{% notice note %}}

If you get any error or not working as demonstrated, please, add the following Environment variable: `export RABBIT_SERVER_URL='guest:guest@localhost:5672'`

{{% /notice %}}

### Conclusion 

This document demonstrates how you can integrate KrakenD with RabbitMQ. For more information, please reach us at: hello@skalena.com 