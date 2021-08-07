---
title: "Getting Started"
linkTitle: "Getting Started"
weight: 2
description: >
  What does your user need to know to try your project?
---

{{% pageinfo %}}
Get your prerequisites and authentication ready.{{% /pageinfo %}}



# Prerequisites

Below mentioned authorization keys are required  to interact with the resources and visualize the events building block end-point operations.

## ApiKeyAuth  (apiKey)
 
1.Each client version has a unique API key (e.g., "c6befa22-50a6-4403-a8fc-378c9719743b") (FYI: This example only provides a general appearance of an API key) . 
 
2.For endpoints that do not require user authentication, the ROKWIRE-API-KEY header must contain an API key corresponding to a supported client.
​
## UserAuth  (http, Bearer)
 
The client must send a valid (i.e., signed, not expired) OpenID Connect id_token in the Authorization header when making requests to API endpoints that require user authentication. The id_token is valid only for 24hrs.
​

# Note

In the following list, endpoints with * specifically requires a valid id_token that indicates membership in at least one of the
 
following groups:
​
* urn:mace:uiuc.edu:urbana:authman:app-rokwire-service-policy-rokwire events manager
 
* urn:mace:uiuc.edu:urbana:authman:app-rokwire-service-policy-rokwire ems events uploader
 
* urn:mace:uiuc.edu:urbana:authman:app-rokwire-service-policy-rokwire events web app
 
* urn:mace:uiuc.edu:urbana:authman:app-rokwire-service-policy-rokwire event approvers
 
* urn:mace:uiuc.edu:urbana:authman:app-rokwire-service-policy-rokwire groups access
​
## Endpoint table

| Endpoint  | Description     | Authentication Requirement | Parameters  |
|-----------|-----------------|----------------------------|-------------|
| <p style="color:blue;">GET</p>/events| search for events with given information   |  a valid API key                         |    See Table 2         |
| <p style="color:green;">POST</p>/events*   | create a new event record into the system with all the information in the parameter provided        |      a valid ID token                      |   None          |
| <p style="color:blue;">GET</p>/events/{event_id}   | search for events with given event_id        |    a valid API key           |   event_id (string): ID of the event you are looking for |
| <p style="color:orange;">PUT</p>/events/{event_id}*|update information of events of a given event_id | a valid ID token|event_id (string): ID of the event that needs to be updated |
| <p style="color:red;">DELETE</p>/events/{event_id}*| delete information of events of a given event_id|a valid ID token |event_id (string): ID of the event that needs to be deleted |
| <p style="color:cyan;">PATCH</p>/events/{event_id}*|partially update the event record matching the event_id | valid ID token |event_id (string): ID of the event that needs to be updated |
| <p style="color:blue;">GET</p>/events/categories| get a list of event categories| a valid API key|None |
| <p style="color:blue;">GET</p>/events/tags|get a list of event tags |a valid API key | None|
| <p style="color:blue;">GET</p>/events/super-events/tags| get a list of Rokwire super event tags|a valid API key | None|
| <p style="color:blue;">GET</p>/events/{event_id}/images| get IDs of all images associated with the requested event|a valid API key | None|
| <p style="color:green;">POST</p>/events/{event_id}/images*| upload an image to with the requested event |a valid ID token |event_id: Event ID |
| <p style="color:blue;">GET</p>/events/{event_id}/images/{image_id}|download an event image by providing the IDs of the event and the image|a valid API key|event_id(string): Event ID; image_id(string): Requested image ID.
|
|<p style="color:orange;">PUT</p>/events/{event_id}/images/{image_id}*|update an image associated with the specified event|a valid ID Token|event_id(string): Event ID; image_id(string): Requested image ID.|
|<p style="color:red;">DELETE</p>/events/{event_id}/images/{image_id}*|delete an image associated with the specified event|a valid ID Token|event_id(string): Event ID; image_id(string): Requested image ID.
|


## Table 2:  Parameters of <span style="color:blue;">GET</span>/events endpoint </p>


|Parameter|Description|
|---------|-----------|
|title (string)|The parameter for searching events based on keywords in the title.|
|recurrenceId (integer)|The parameter to search events based on a specific recurrence ID.|
|tags (string)|Search events with the given tags, e.g., /events?tags=coffee&tags=music. This query will return all events whose tags contain coffee or music.|
|targetAudience (string)|The parameter for searching events based on given input target audience, e.g., /events?targetAudience=students&targetAudience=staff. This query will return all events whose target audience is either students or staff. This parameter is CURRENTLY IGNORED.|
|startDate (string)|The parameter for searching events based on a given start date, e.g., /events?startDate=2019-04-25T13:00:00. This query will return all events whose start date is equal or after the given input date.|
|startDate.lte (string)|The parameter for searching events based on a given start date, e.g., /events?startDate.lte=2019-04-25T13:00:00. This query will return all events whose start date is equal or before the given input date.|
|startDate.gte (string)|The parameter for searching events based on a given start date, e.g., /events?startDate.gte=2019-04-25T13:00:00. This query will return all events whose start date is equal or after the given input date.|
|startDateLimit (string)|Another parameter for searching events based on a given start date, e.g., /events?startDateLimit=2019-04-25T13:00:00. This query will return all events whose start date is less than or equal to the given input date.|
|endDate (string)|The parameter for searching events based on a given end date, e.g., /events?endDate=2019-04-25T13:00:00. This query will return all events whose start date is equal or before the given input date.|
|endDate.lte (string)|The parameter for searching events based on a given start date, e.g., /events?endDate.lte=2019-04-25T13:00:00. This query will return all events whose end date is equal or before the given input date.|
|endDate.gte (string)|The parameter for searching events based on a given start date, e.g., /events?endDate.gte=2019-04-25T13:00:00. This query will return all events whose end date is equal or after the given input date.|
|latitude (number)|The latitude of the center point for geolocation radius search.|
|longitude (number)|The longitude of the center point for geolocation radius search.|
|radius (integer)|The parameter to search events within a given radius of the provided location in meters, e.g., /events?latitude=40.1078955&longitude=-88.224036&radius=800. This query will return back all events whose geolocation is within 800 meter centered at given geolocation point.|
|skip (integer, $int32)|Number of records to skip for pagination.|
|limit (integer, $int32)|Maximum number of records to return.|
|id (string)|The parameter for searching multiple events based on their IDs.|
|superEventId (string)|The parameter for searching sub events based on the ID of a super event.|



