---
id: s0jhm0w44j3ijznlcf1zq3y
title: Understanding HTTP
desc: ''
updated: 1693544740264
created: 1693539953427
---

## Introduction to HTTP

HTTP (a.k.a. Hypertext Transfer Protocol) is an application protocol that is the foundation of any data exchange on the Web, and it is the base to understand Client-Server applications.

Initially designed and developed by [Tim Berners-Lee](https://es.wikipedia.org/wiki/Tim_Berners-Lee) in the 90s, later standardized by [IETF (a.k.a. Internet Engineering Task Force)](https://www.ietf.org/) and [W3C (a.k.a. World Wide Web Consortium)](https://www.w3.org/).

The basics of functionality of HTTP are **the request** message and **the response** message, usually a request is made by the browser and send it to the server, then the server takes the request and executes some logic to generate a response, that response is sent to the browser and there the browser does something with that response.

![Example of request-response](assets/3_HTTP/HTTP_ClientServer_Ex.png)

Another way to understand this concepts is to see it as the abstraction of a conversation, i.e. subject *A* ask for something to subject *B*, *B* thinks what is he going to say, and then he answers to *A*.

## HTTP Request

Let's start from the begining or in this case from the request, as mentioned before the request is basically a message sent from the client to the server.

![Request Exmaple](assets/3_HTTP/HTTP_Request.png)

### HTTP Request Fromat

The next is an example of 

```text
GET URL HTTP/1.1
Key:Value
Key:Value

Request Body
```

