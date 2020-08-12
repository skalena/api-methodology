---
date: 2016-04-09T16:50:16+02:00
title: APIs Design Best Practices
weight: 25
---

### **1) Terminologies**

The following are the most important terms related to REST APIs

-   **Resource**  is an object or representation of something, which has some associated data with it and there can be set of methods to operate on it. E.g. Animals, schools and employees are resources and  _delete, add, update_ are the operations to be performed on these resources.
-   **Collections**  are set of resources, e.g  _Companies_  is the collection of  _Company_  resource.
-   **URL**  (Uniform  **Resource**  Locator) is a path through which a  **resource** can be located and some actions can be performed on it.

Este é um exemplo:

Codigo:

    import java.*;
    
    public static void main(strain){
    
    }

### 2) API endpoint

Let’s write few APIs for  **Companies**  which has some  **Employees,**  to understand more.  
`/getAllEmployees`  is an API which will respond with the list of employees. Few more APIs around a  **Company**  will look like as follows:

-   `_/addNewEmployee_`
-   `_/updateEmployee_`
-   `_/deleteEmployee_`
-   `_/deleteAllEmployees_`
-   `_/promoteEmployee_`
-   `_/promoteAllEmployees_`

And there will be tons of other API endpoints like these for different operations. All of those will contain many redundant actions. Hence, all these API endpoints would be burdensome to maintain, when API count increases.

#### What is wrong?  

* The URL should only contain resources(nouns) not actions or verbs. The API path`/addNewEmployee`  contains the action  `addNew`  along with the resource name  `Employee`.

#### Then what is the correct way?  
* `/companies`  endpoint is a good example, which contains no action. But the question is how do we tell the server about the actions to be performed on  `companies`  resource viz. whether to add, delete or update?

This is where the  [HTTP methods](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol#Request_methods)  (GET, POST, DELETE, PUT), also called as verbs, play the role.

The resource should always be  **plural**  in the API endpoint and if we want to access one instance of the resource, we can always pass the id in the URL.

-   method  `GET`  path  `/companies`  should get the list of all companies
-   method  `GET`  path  `/companies/34`  should get the detail of company 34
-   method  `DELETE`  path  `/companies/34`  should delete company 34

In few other use cases, if we have resources under a resource, e.g Employees of a Company, then few of the sample API endpoints would be:

-   `GET /companies/3/employees`  should get the list of all employees from company 3
-   `GET /companies/3/employees/45`  should get the details of employee 45, which belongs to company 3
-   `DELETE /companies/3/employees/45`  should delete employee 45, which belongs to company 3
-   `POST /companies`  should create a new company and return the details of the new company created

Isn’t the APIs are now more precise and consistent? 😎

**_Conclusion:_** _The paths should contain the plural form of resources and the HTTP method should define the kind of action to be performed on the resource._

### 3) HTTP methods (verbs)

HTTP has defined few sets of methods which indicates the type of action to be performed on the resources.

> The URL is a sentence, where resources are nouns and HTTP methods are verbs.

The important HTTP methods are as follows:

1.  `GET`  method requests data from the resource and should not produce any side effect.  
    E.g  `/companies/3/employees`  returns list of all employees from company 3.
2.  `POST`  method requests the server to  **create**  a resource in the database, mostly when a web form is submitted.  
    E.g  `/companies/3/employees`  creates a new Employee of company 3.  
    `POST`  is non-[idempotent](https://en.wikipedia.org/wiki/Idempotence#Computer_science_meaning)  which means multiple requests will have different effects.
3.  `PUT`  method requests the server to  **update**  resource or  **create**  the resource, if it doesn’t exist.  
    E.g.  `/companies/3/employees/john`  will request the server to update, or create if doesn’t exist, the  _john_  resource in  employees  collection under company 3.  
    `PUT`  is  [idempotent](https://en.wikipedia.org/wiki/Idempotence#Computer_science_meaning)  which means multiple requests will have the same effects.
4.  `DELETE`  method requests that the resources, or its instance, should be removed from the database.  
    E.g  `/companies/3/employees/john/`  will request the server to delete  _john_ resource from the employees collection under the company 3.

There are  [few other methods](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol#Request_methods)  which we will discuss in another post.

### 4) HTTP response status codes

When the client raises a request to the server through an API, the client should know the feedback, whether it failed, passed or the request was wrong. HTTP status codes are bunch of standardized codes which has various explanations in various scenarios. The server should always return the right status code.  
The following are the important categorization of HTTP codes:

#### **2xx (Success category)**

These status codes represent that the requested action was received and successfully processed by the server.

-   **200 Ok** The standard HTTP response representing success for GET, PUT or POST.
-   **201 Created** This status code should be returned whenever the new instance is created. E.g on creating a new instance, using POST method, should always return 201 status code.
-   **204 No Content** represents the request is successfully processed, but has not returned any content.  
    DELETE can be a good example of this.  
    The API  `DELETE /companies/43/employees/2`  will delete the employee 2 and in return we do not need any data in the response body of the API, as we explicitly asked the system to delete. If there is any error, like if  `employee 2`  does not exist in the database, then the response code would be not be of  `2xx Success Category`  but around  `4xx Client Error category`.

#### **3xx (Redirection Category)**

-   **304 Not Modified**  indicates that the client has the response already in its cache. And hence there is no need to transfer the same data again.

#### 4xx (Client Error Category)

These status codes represent that the client has raised a faulty request.

-   **400 Bad Request**  indicates that the request by the client was not processed, as the server could not understand what the client is asking for.
-   **401 Unauthorized**  indicates that the client is not allowed to access resources, and should re-request with the required credentials.
-   **403 Forbidden** indicates that the request is valid and the client is authenticated, but the client is not allowed access the page or resource for any reason. E.g sometimes the authorized client is not allowed to access the directory on the server.
-   **404 Not Found** indicates that the requested resource is not available now.
-   **410 Gone** indicates that the requested resource is no longer available which has been intentionally moved.

#### 5xx (Server Error Category)

-   **500 Internal Server Error**  indicates that the request is valid, but the server is totally confused and the server is asked to serve some unexpected condition.
-   **503 Service Unavailable** indicates that the server is down or unavailable to receive and process the request. Mostly if the server is undergoing maintenance.

### 5) Field name casing convention

You can follow any casing convention, but make sure it is consistent across the application. If the request body or response type is  [JSON](https://en.wikipedia.org/wiki/JSON)  then please follow camelCase to maintain the consistency.

### 6) Searching, sorting, filtering and pagination

All of these actions are simply the query on one dataset. There will be no new set of APIs to handle these actions. We need to append the query params with the GET method API.  
Let’s understand with few examples how to implement these actions.

-   **Sorting** In case, the client wants to get the sorted list of companies, the  `GET /companies`  endpoint should accept multiple sort params in the query.  
    E.g  `GET /companies?sort=rank_asc`  would sort the companies by its rank in ascending order.
-   **Filtering** For filtering the dataset, we can pass various options through query params.  
    E.g  `GET /companies?category=banking&location=india`  would filter the companies list data with the company category of Banking and where the location is India.
-   **Searching** When searching the company name in companies list the API endpoint should be  `GET /companies?search=Digital Mckinsey`
-   **Pagination** When the dataset is too large, we divide the data set into smaller chunks, which helps in improving the performance and is easier to handle the response. Eg.  `GET /companies?page=23`  means get the list of companies on 23rd page.

If adding many query params in GET methods makes the URI too long, the server may respond with  `414 URI Too long`  HTTP status, in those cases params can also be passed in the request body of the  `POST`  method.

### 7) Versioning

When your APIs are being consumed by the world, upgrading the APIs with some breaking change would also lead to breaking the existing products or services using your APIs.

`http://api.yourservice.com/v1/companies/34/employees`  is a good example, which has the version number of the API in the path. If there is any major breaking update, we can name the new set of APIs as  `v2`  or  `v1.x.x`

These guidelines are compiled on my experience of development. I would love to know your views on the pointers mentioned above. Please leave a comment, and let me know!

*Original Post* by ***Mahesh Haldar***  [@haldar.mahesh](https://hackernoon.com/u/haldar.mahesh): https://hackernoon.com/restful-api-designing-guidelines-the-best-practices-60e1d954e7c9?lipi=urn%3Ali%3Apage%3Ad_flagship3_profile_view_base_recent_activity_details_all%3Bodbdl3ujQ7CFgA21%2FhKW2A%3D%3D

## 10 API Best Practices (Design)

Original Post: https://medium.com/@mwaysolutions/10-best-practices-for-better-restful-api-cbe81b06f291

Web APIs has become an very important topic in the last year. We at M-Way Solutions are working every day with different backend systems and therefore we know about the importance of a clean API design.

Typically we use a RESTful design for our web APIs. The concept of REST is to separate the API structure into logical resources. There are used the HTTP methods GET, DELETE, POST and PUT to operate with the resources.

These are 10 best practices to design a clean RESTful API:

## 1. Use nouns but no verbs

For an easy understanding use this structure for every resource:

Resource GET  read - `/cars`
POST  create - `/cars`
PUT  update - `/cars`
DELETE remove/blocks-  `/cars` 

Do not use verbs:

    /getAllCars  
    /createNewCar  
    /deleteAllRedCars

## 2. GET method and query parameters should not alter the state

Use  **PUT, POST**  and  **DELETE**  methods instead of the **GET**  method to alter the state.  
Do not use  **GET**  for state changes:

    GET /users/711?activate or  
    GET /users/711/activate

## 3. Use plural nouns

Do not mix up singular and plural nouns. Keep it simple and use only plural nouns for all resources.

    /cars instead of /car  
    /users instead of /user  
    /products instead of /product  
    /settings instead of /setting

## **4. Use sub-resources for relations**

If a resource is related to another resource use subresources.

    GET /cars/711/drivers/ Returns a list of drivers for car 711  
    GET /cars/711/drivers/4 Returns driver #4 for car 711

## **5. Use HTTP headers for serialization formats**

Both, client and server, need to know which format is used for the communication. The format has to be specified in the HTTP-Header.

_Content-Type_  defines the request format.  
_Accept_  defines a list of acceptable response formats.

## **6. Use HATEOAS**

**H**ypermedia  **a**s  **t**he  **E**ngine  **o**f  **A**pplication  **S**tate is a principle that hypertext links should be used to create a better navigation through the API.

    {  
      "id": 711,  
      "manufacturer": "bmw",  
      "model": "X5",  
      "seats": 5,  
      "drivers": [  
       {  
        "id": "23",  
        "name": "Stefan Jauker",  
        "links": [  
         {  
         "rel": "self",  
         "href": "/api/v1/drivers/23"  
        }  
       ]  
      }  
     ]  
    }

## **7. Provide filtering, sorting, field selection and paging for collections**

**Filtering**:

Use a unique query parameter for all fields or a query language for filtering.

    GET /cars?color=red Returns a list of red cars  
    GET /cars?seats<=2 Returns a list of cars with a maximum of 2 seats

**Sorting**:

Allow ascending and descending sorting over multiple fields.

    GET /cars?sort=-manufactorer,+model

This returns a list of cars sorted by descending manufacturers and ascending models.

**Field selection**

Mobile clients display just a few attributes in a list. They don’t need all attributes of a resource. Give the API consumer the ability to choose returned fields. This will also reduce the network traffic and speed up the usage of the API.

    GET /cars?fields=manufacturer,model,id,color

**Paging**

Use limit and offset. It is flexible for the user and common in leading databases. The default should be limit=20 and offset=0

    GET /cars?offset=10&limit=5

To send the total entries back to the user use the custom HTTP header: X-Total-Count.

Links to the next or previous page should be provided in the HTTP header link as well. It is important to follow this link header values instead of constructing your own URLs.

Link: <https://blog.mwaysolutions.com/sample/api/v1/cars?offset=15&limit=5>; rel="next",  
<https://blog.mwaysolutions.com/sample/api/v1/cars?offset=50&limit=3>; rel="last",  
<https://blog.mwaysolutions.com/sample/api/v1/cars?offset=0&limit=5>; rel="first",  
<https://blog.mwaysolutions.com/sample/api/v1/cars?offset=5&limit=5>; rel="prev",

## **8. Version your API**

Make the API Version mandatory and do not release an unversioned API. Use a simple ordinal number and avoid dot notation such as 2.5.

We are using the url for the API versioning starting with the letter „v“

    /blog/api/v1

## **9. Handle Errors with HTTP status codes**

It is hard to work with an API that ignores error handling. Pure returning of a HTTP 500 with a stacktrace is not very helpful.

**Use HTTP status codes**

The HTTP standard provides over 70 status codes to describe the return values. We don’t need them all, but there should be used at least a mount of 10.

200 — OK — Eyerything is working  
201 — OK — New resource has been created  
204 — OK — The resource was successfully deleted

304 — Not Modified — The client can use cached data

400 — Bad Request — The request was invalid or cannot be served. The exact error should be explained in the error payload. E.g. „The JSON is not valid“  
401 — Unauthorized — The request requires an user authentication  
403 — Forbidden — The server understood the request, but is refusing it or the access is not allowed.  
404 — Not found — There is no resource behind the URI.  
422 — Unprocessable Entity — Should be used if the server cannot process the enitity, e.g. if an image cannot be formatted or mandatory fields are missing in the payload.

500 — Internal Server Error — API developers should avoid this error. If an error occurs in the global catch blog, the stracktrace should be logged and not returned as response.

**Use error payloads**

All exceptions should be mapped in an error payload. Here is an example how a JSON payload should look like.

    {  
      "errors": [  
       {  
        "userMessage": "Sorry, the requested resource does not exist",  
        "internalMessage": "No car found in the database",  
        "code": 34,  
        "more info": "http://dev.mwaysolutions.com/blog/api/v1/errors/12345"  
       }  
      ]  
    }

## **10. Allow overriding HTTP method**

Some proxies support only  **POST**  and  **GET**  methods. To support a RESTful API with these limitations, the API needs a way to override the HTTP method.

Use the custom HTTP Header  **X-HTTP-Method-Override**  to overrider the POST Method.


## Other interesting references

https://cloud.google.com/apis/design/

