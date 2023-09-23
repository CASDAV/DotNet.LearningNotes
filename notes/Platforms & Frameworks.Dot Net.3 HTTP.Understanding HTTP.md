---
id: s0jhm0w44j3ijznlcf1zq3y
title: Understanding HTTP
desc: ''
updated: 1695512652503
created: 1693539953427
---

## Introduction to HTTP

HTTP (a.k.a. Hypertext Transfer Protocol) is an application protocol that is the foundation of most data exchange on the web, and it is the base to understand Client-Server applications.

Initially designed and developed by [Tim Berners-Lee](https://es.wikipedia.org/wiki/Tim_Berners-Lee) in the 90s, later standardized by [IETF (a.k.a. Internet Engineering Task Force)](https://www.ietf.org/) and [W3C (a.k.a. World Wide Web Consortium)](https://www.w3.org/).

The basics of functionality of HTTP are **the request** message and **the response** message, usually a request is made by the browser and send it to the server, then the server takes the request and executes some logic to generate a response, that response is sent to the browser and there the browser does something with that response.

![Example of request-response](assets/3_HTTP/HTTP_ClientServer_Ex.png)

Another way to understand this concept is to see it as the abstraction of a conversation, i.e. subject *"A"* ask for something to subject *"B"*, *"B"* thinks what is he going to say, and then he answers to *"A"*.

## HTTP Request

Let's start from the beginning or in this case from the request, as mentioned before the request basically is a message sent from the client to the server, where the client ask for some resources or actions to be preformed in the server.

![Request Example](assets/3_HTTP/HTTP_Request.png)

### HTTP Request Format

The next is the basic structure of an HTTP request: 

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
- GET: Request a representation of the specified resource.
- POST: Submits an entity to the specified resource, often causing a change in state or side effects on the server.
- PUT: Replaces all current representations of the target resource with the request payload.
- DELETE: Deletes the specified resource.

<p style="color:yellow">Note: There are more HTTP methods, but these 4 are the most used.</p>
<p style="color:yellow">Note 2: As you can see, each method has its own purpose, however, those purposes are not mandatory is just a standard that all developers should follow as far as possible.</p>

#### URL

This section is referred to the relative path of the request, for example you are in a web page called `www.example.com`, and you click a button to see a list of the users, then the **Address Bar** of your browser changes from `www.exapmle.com` to `www.example.com/users` and the displayed page change and displays a list of the users, as you can see the address bar contains 2 main parts the **Base Path (a.k.a. Base URL)** in this example is `www.example.com`, and the **Relative Path (a.k.a. Relative URL)** in this example is `/users`, as mentioned previously the URL section of a request message takes the relative path, so as you can imagine the value that is taken to make the request messages is `/users`.

#### PROTOCOL VERSION

This section determines the version of the HTTP protocol (a.k.a. HTTP specification) that it's going to be used by the client and server to communicate, the most commonly used version is **HTTP/1.1**, the next list shows another commonly used or relevant versions of the protocol with a short description of the main characteristic of the version:

- HTTT/0.9 The one-line protocol
- HTTP/1.0 Building extensibility
- HTTP/1.1 The standardized protocol
- HTTP/2 A protocol for greater performance
- HTTP/3 HTTP over QUIC

<p style="color:yellow">Note: For more information about HTTP protocol versions, visit <a href="https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/Evolution_of_HTTP"> Mozilla Developer HTTP evolution</a>.</p> 

#### REQUEST HEADERS

This section contains Key-Value pairs that are sent by the browser to the server, those Key-Value pairs send important information that is used by the server for many purposes, here are some common examples of request headers:

- Accept: Represent MIME type of response content to be accepted by the client. i.e. text/html, text/plain, application/json, application/xml, etc...

- Accept-Language: Represents natural language of response content to be accepted by the client. i.e. en-US.

- Content-Type: MIME type of request body. i.e. text/x-www-form-uriencoded, application/json, application/xml, multipart/form-data, etc...

- Content-Lenght: Length (bytes) of request body. i.e. 100

- Date: Date and time of the request. i.e. Tue, 15 Nov 1994 08:12:31 GTM

- Host: Server domain name. i.e. www.example.com

- User-Agent: Browser (client) details. i.e. Mozilla/5.0 Firefox/12.0

- Cookie: Contains cookies to send to server. i.e. x: 100

<p style="color:yellow">Note: Usually these aren't visible to the end-user, this info is intended to the exchange of info between the server and the client</p>

#### EMPTY LINE

The purpose of this section is to separate the Key-Value pairs from the request body.

#### REQUEST BODY

This section contains data relevant for the resources or logic business which the server is asked for.

Common request body formats:

- JSON
- XML

### Query string

Additionally, to request body, other information can be sent to the server without using the request body, this can be achieved by using query string syntax, this syntax allows you to send parameter values from the client to the server. Basically the query string is a text concatenated to the path of the request, here is an example of a query string:

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

## HTTP Response

As mentioned previously when a request is made to a server this one catches the request, performs some logic, and then sends back a response to the browser.

![Response example](assets/3_HTTP/HTTP_Response.png)

### HTTP Response Format

As the request the response also have its own format, this format is similar to the response format, but there are some differences, the next is the basic structure of a response message:

```text
PROTOCOL VERSION | STATUS CODE | STATUS DESCRIPTION
-----------------------------------------
RESPONSE HEADERS
-----------------------------------------
EMPTY LINE
-----------------------------------------
RESPONSE BODY
```

As you can see the mayor difference of this format is its first line, just as we did with the request format below we will see in detail each item.

#### PROTOCOL VERSION

This one doesn't change, it's just the same as it was in the request format.

#### STATUS CODE & STATUS DESCRIPTION

HTTP response status codes indicate whether a specific HTTP request has been successfully completed. Responses are grouped in five classes:

- Informational responses (1XX)
- Successful responses (2XX)
- Redirection messages (3XX)
- Client error responses (4XX)
- Server error responses (5XX)

Additionally, each response code comes with a description of the code, next we will see the most common response status codes with its status descriptions, and detailed info about the response:

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

<p style="color:yellow">Note: For more information about status codes click the next link: <a href="https://developer.mozilla.org/en-US/docs/Web/HTTP/Status">Mozilla Developer: HTTP response status codes
</a>.</p>

#### RESPONSE HEADERS

This one doesn't change, it's just the same as it was in the request format.

Some common response headers are:

- Date: Date and time of the request. i.e. Tue, 15 Nov 1994 08:12:31 GTM.

- Server: Name of the server, i.e. Server = Kestrel.

- Content-Type: MIME type of the response body. i.e. text-plain/text.

- Content-Length: Length (bytes) of the response body, i.e. 100.

- Cache-Control: Indicates the seconds that the response can be cached at the browser, i.e. max-age: 60.

- Set-Cookie: Contains cookies for the browser, i.e. x: 10.

- Access-Control-Allow-Origin: Used to enable CORS (a.k.a. Cross-Origin Resource Sharing), i.e. `x: http://www.example.com`.

- Location: contains a URL to redirect.

#### RESPONSE BODY

This one doesn't change, it's just the same as it was in the request format.
