---
id: s0jhm0w44j3ijznlcf1zq3y
title: Understanding HTTP
desc: ''
updated: 1695358858393
created: 1693539953427
---

## Introduction to HTTP

HTTP (a.k.a. Hypertext Transfer Protocol) is an application protocol that is the foundation of most data exchange on the web, and it is the base to understand Client-Server applications.

Initially designed and developed by [Tim Berners-Lee](https://es.wikipedia.org/wiki/Tim_Berners-Lee) in the 90s, later standardized by [IETF (a.k.a. Internet Engineering Task Force)](https://www.ietf.org/) and [W3C (a.k.a. World Wide Web Consortium)](https://www.w3.org/).

The basics of functionality of HTTP are **the request** message and **the response** message, usually a request is made by the browser and send it to the server, then the server takes the request and executes some logic to generate a response, that response is sent to the browser and there the browser does something with that response.

![Example of request-response](assets/3_HTTP/HTTP_ClientServer_Ex.png)

Another way to understand this concepts is to see it as the abstraction of a conversation, i.e. subject *A* ask for something to subject *B*, *B* thinks what is he going to say, and then he answers to *A*.

## HTTP Request

Let's start from the begining or in this case from the request, as mentioned before the request is basically a message sent from the client to the server, where the client ask for some resources or actions to be preformed in the server.

![Request Exmaple](assets/3_HTTP/HTTP_Request.png)

### HTTP Request Fromat

The next is the basic structure of a HTTP request: 

```text
METHOD | URL | PROTOCOL VERSION
-----------------------------------------
REQUEST HEADERS
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
<p style="color:yellow">Note 2: As you can see, each method has its own purpose, however, those purposes are not mandatory is just a standard that all developers should follow as far as possible.</p>

#### URL

This section is refered to the relative path of the request, for example you are in a web page called `www.example.com`, and you click a button to see a list of the users, then the **Address Bar** of your browser changes from `www.exapmle.com` to `www.example.com/users` and the displayed page change and displays a list of the users, as you can see the address bar contains 2 main parts the **Base Path (a.k.a. Base URL)** in this example is `www,example.com`, and the **Relative Path (a.k.a. Realtive URL)** in this example is `/users`, as mentioned previously the URL section of a request message takes the relative path, so as you can imageno the value that is taked to make the request messages is `/users`.

#### PROTOCOL VERSION

This section determines the version of the HTTP protocol (a.k.a. HTTP specification) that its going to be used by the client and server to communicate, the most commonly used version is **HTTP/1.1**, the next list shows another commonly used or relevant versions of the protocol with a short description of the main characteristic of the version:

- HTTT/0.9 The one-line protocol
- HTTP/1.0 Buildinig extensibili
- HTTP/1.1 The standarized protocol
- HTTP/2 A protocol for greater performance
- HTTP/3 HTTP over QUIC

<p style="color:yellow">Note: For more information about HTTP protocol versions visit <a href="https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/Evolution_of_HTTP"> Mozilla Developer HTTP evolution</a></p> 

#### REQUEST HEADERS

This section contains Key-Value pairs that are sent by the browser to the server, those Key-Value pairs send inportant information that the server is used by the server for many purposes, here are some common examples of request headers:

- Accept: Represtent MIME type of response constent to be accepted by the client. i.e. text/html, text/plain, application/json, application/xml, etc...

- Accept-Language: Represents natural language of response content to be accepted by the client. i.e. en-US.

- Content-Type: MIME type of request body. i.e. text/x-www-form-uriencoded, application/json, application/xml, multipart/form-data, etc...

- Content-Lenght: Length (bytes) of request body. i.e. 100

- Date: Date and time of the request. i.e. Tue, 15 Nov 1994 08:12:31 GTM

- Host: Server domain name. i.e. www.example.com

- User-Agent: Browser (client) deatils. i.e. Mozilla/5.0 Firefox/12.0

- Cookie: Contains cookies to send to server. i.e. x=100

#### EMPTY LINE

The purpose of this section is to separate the Key-Value pairs from the request body.

#### REQUEST BODY

This section contains data relevant for the resources or logic business which the server is asked for.

Common request body formats:

- JSON
- XML

### Query string

Additionally to request body, other information can be sent to the server without using the request body, this can be achived by using query string sintax, this sintax allows you to send parameter values from the client to the server. Basically the query string is a text concatenated to the path of the request, here is a example of a query string:

```text
www.example.com/user?id=1
                    ^
        Here starts the query string
```

### Request message example

Here is an example of how looks an HTTP request message

```text
POST /user?id=1 HTTP/1.1
Host: www.example.com
Accept: application/json
Content-Type: application/json

{
    Some_Key_Value: "some data"
}
```