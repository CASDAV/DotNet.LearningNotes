---
id: icxlg59f5qizidohx3lcgn0
title: Interview Q&A
desc: ''
updated: 1695574901354
created: 1693539983871
---

## What is HTTP?
HTTP (a.k.a. Hypertext Transfer Protocol) is an application protocol that is the foundation of most data exchange on the web, and it is the base to understand Client-Server applications.

Initially designed and developed by [Tim Berners-Lee](https://es.wikipedia.org/wiki/Tim_Berners-Lee) in the 90s, later standardized by [IETF (a.k.a. Internet Engineering Task Force)](https://www.ietf.org/) and [W3C (a.k.a. World Wide Web Consortium)](https://www.w3.org/).

The basics of functionality of HTTP are **the request** message and **the response** message, usually a request is made by the browser and send it to the server, then the server takes the request and executes some logic to generate a response, that response is sent to the browser and there the browser does something with that response.

## What is the format of a Request Message?

```text
METHOD | URL | PROTOCOL VERSION
-----------------------------------------
REQUEST HEADERS
-----------------------------------------
EMPTY LINE
-----------------------------------------
REQUEST BODY
```

## What are the important HTTP methods (or HTTP verbs) – (GET, POST, PUT, PATCH, HEAD, DELETE)?
The important HTTP methods are:

- GET: Request a representation of the specified resource.
- POST: Submits an entity to the specified resource, often causing a change in state or side effects on the server.
- PUT: Replaces all current representations of the target resource with the request payload.
- PATCH: The PATCH method applies partial modifications to a resource.
- HEAD: The HEAD method asks for a response identical to a GET request, but without the response body.
- DELETE: Deletes the specified resource.
## What are the important HTTP status codes?
These ae the important status codes:

- 101 Switching Protocols: This code is sent in response to an Upgrade request header from the client and indicates the protocol the server is switching to.

- 200 Ok: The request succeeded. The result meaning of "success" depends on the HTTP method:
    - GET: The resource has been fetched and transmitted in the message body.
    - HEAD: The representation headers are included in the response without any message body.
    - PUT or POST: The resource describing the result of the action is transmitted in the message body.
    - TRACE: The message body contains the request message as received by the server.

- 302 Found: This response code means that the URI of requested resource has been changed temporarily. Further changes in the URI might be made in the future. Therefore, this same URI should be used by the client in future requests.

- 304 Not Modified: This is used for caching purposes. It tells the client that the response has not been modified, so the client can continue to use the same cached version of the response.

- 400 Bad Request: The server cannot or will not process the request due to something that is perceived to be a client error (e.g., malformed request syntax, invalid request message framing, or deceptive request routing).

- 401 Unauthorized: Although the HTTP standard specifies "unauthorized", semantically this response means "unauthenticated". That is, the client must authenticate itself to get the requested response.

- 404 Not Found: The server cannot find the requested resource. In the browser, this means the URL is not recognized. In an API, this can also mean that the endpoint is valid but the resource itself does not exist. Servers may also send this response instead of 403 Forbidden to hide the existence of a resource from an unauthorized client. This response code is probably the most well known due to its frequent occurrence on the web.

- 500 Internal Server Error: The server has encountered a situation it does not know how to handle.

## What is Content Negotiation in HTTP?

## Explain how HTTP protocol works?

## What is a web server?