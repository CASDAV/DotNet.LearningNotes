---
id: s0jhm0w44j3ijznlcf1zq3y
title: Understanding HTTP
desc: ''
updated: 1695150053688
created: 1693539953427
---

## Introduction to HTTP

HTTP (a.k.a. Hypertext Transfer Protocol) is an application protocol that is the foundation of most data exchange on the web, and it is the base to understand Client-Server applications.

Initially designed and developed by [Tim Berners-Lee](https://es.wikipedia.org/wiki/Tim_Berners-Lee) in the 90s, later standardized by [IETF (a.k.a. Internet Engineering Task Force)](https://www.ietf.org/) and [W3C (a.k.a. World Wide Web Consortium)](https://www.w3.org/).

The basics of functionality of HTTP are **the request** message and **the response** message, usually a request is made by the browser and send it to the server, then the server takes the request and executes some logic to generate a response, that response is sent to the browser and there the browser does something with that response.

![Example of request-response](assets/3_HTTP/HTTP_ClientServer_Ex.png)

Another way to understand this concepts is to see it as the abstraction of a conversation, i.e. subject *A* ask for something to subject *B*, *B* thinks what is he going to say, and then he answers to *A*.

## HTTP Request

Let's start from the begining or in this case from the request, as mentioned before the request is basically a message sent from the client to the server.

![Request Exmaple](assets/3_HTTP/HTTP_Request.png)

### HTTP Request Fromat

The next is the basic structure of a HTTP request: 

```HTTP
METHOD | URL | PROTOCOL VERSION
-----------------------------------------
REQUEST HEADERS
(KEY:VALUE)
-----------------------------------------
EMPTY LINE
-----------------------------------------
REQUEST BODY
```

As you can see above, you can say that an HTTP request message is just a plain text with a format, and that is pretty much what that is. However, there are some standardized rules that you must follow to create a request message, as you can see above all the parts of a request message are reserved for a specific item, each specific item contains information that's necessary, below we will see in detail the items that make up the request:

#### Method

This section indicates the desired action to be performed with the request, although they can also be nouns, these request methods are sometimes referred to as HTTP verbs.

Some HTTP methods are:
- GET: Request a reperesntation of the especified resource, 
- POST: Submits an entity to the specified resource, often causing a change in state or side effects on the server.
- PUT: Replaces all current representations of the target resource with the request payload.
- DELETE: Deletes the specified resource.

<p style="color:yellow">Note: There are more HTTP methods, but this 4 are the most used.</p>
<p style="color:yellow">Note 2: As you can see each method has its own purpose, however, those purposes are not mandatory is just a standard that all developers should follow as far as possible.</p>

#### URL

This section indicates where are you making the request, for example you just open your favorite browser (Chrome, Safari, Friefox, etc...) you want to make a search in Google, you type in the **Address Bar** `google.com`, and then you press enter, in that moment you are making a request to Google, that is indicated thanks to the address that you type before in the address bar the URL should look like in you request message like this `https://www.google.com/`


#### PROTOCOL VERSION





