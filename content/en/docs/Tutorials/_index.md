
---
title: "Tutorials"
linkTitle: "Tutorials"
weight: 8
date: 2017-01-04
description: >
  Show your user how to work through some end to end examples.
---

{{% pageinfo %}}
API Tutorial
{{% /pageinfo %}}


​
In order to make your own API call, you need to first determine the authentication requirement and 
​
parameters of the specific API endpoint that you are calling. As a recap, there are five basic types of
 
API Endpoints:
​
* <span style="color:blue;">GET</span>: Retrieves a resource</p>
* <span style="color:green;">POST</span>: Creates a resource</p>
* <span style="color:orange;">PUT</span>: Updates or creates within an existing resource</p>
* <span style="color:cyan;">PATCH</span>: Partially modifies an existing resource</p>
* <span style="color:red;">DELETE</span>: Removes the resource</p>

## <span style="color:blue;">GET</span> Endpoints

Let's take a look at an example, a GET endpoint from the [Events Building Block development server](https://api-dev.rokwire.illinois.edu/docs/)  :

<span style="color:blue;">GET</span>/events/{event_id}search for events with given event_id </p>

Authentication requirement: a valid API key.
​
Parameters: event_id (string): ID of the event you are looking for.
​
When we access this endpoint, we need to first make sure we authenticate the endpoint properly. In this
 
case, the requirement for authentication is a valid API key that you should have gotten access to. 
​
Click on the "Authorize" button at the top right corner
​
and enter your API key and/or ID token.

Then, click on the "Try it out" button of the endpoint and we will be given a blank
 
to put in our parameter;

![](pic1.png)

Then search by typing in a specific event ID and hitting "Execute", for example, we want to look for the event corresponding to the event ID "5d9b8e953a4f03000be0ec45":

![](pic2.png)

## Error Handling

More likely than not, when you are trying to make your API call the first time, you will run into some unexpected. In order to understand and handle your error, you want to get yourself familiar with different types of error codes.

|Error code|Description|
|----------|-----------|
|200|searching results displayed (for GET, PATCH, PUT endpoints)|
|201|successful operation (for POST endpoints)|
|202|successful deletion (for DELETE endpoints)|
|400|invalid ID supplied (check your ID token)|
|401|unauthorized (check your API key)|
|404|not found (for GET endpoints)|
|405|invalid input| 
|500|internal error|