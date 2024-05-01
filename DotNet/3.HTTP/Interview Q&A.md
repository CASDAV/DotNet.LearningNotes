
## What is HTTP?
HTTP (a.k.a. Hypertext Transfer Protocol) is an application protocol that is the foundation of most data exchange on the web, and it is the base to understand Client-Server applications.

Initially designed and developed by [Tim Berners-Lee](https://es.wikipedia.org/wiki/Tim_Berners-Lee) in the 90s, later standardized by [IETF (a.k.a. Internet Engineering Task Force)](https://www.ietf.org/) and [W3C (a.k.a. World Wide Web Consortium)](https://www.w3.org/).

The basics of functionality of HTTP are **the request** message and **the response** message, usually a request is made by the browser and send it to the server, then the server takes the request and executes some logic to generate a response, that response is sent to the browser and there the browser does something with that response.

## What is the format of a Request Message?

HTTP Requests are messages which are sent by the client to initiate an action on the server.
It consists of various things:

1. Request Line: The Request-Line includes with HTTP method, URL, HTTP version.
2.  Request Headers: Contains request-header fields that allow the client to pass additional information to the server, logically equivalent to the parameters while method invocation in a programming language.
3. Request body: Contains actual content to send to server; such as query string, JSON, XML etc.

Format:
```text
METHOD | URL | PROTOCOL VERSION|
-----------------------------------------
REQUEST HEADERS
-----------------------------------------
EMPTY LINE
-----------------------------------------
REQUEST BODY
```

Example:

```text
POST /user?id=1 HTTP/1.1
Host: www.example.com
Accept: application/json
Content-Type: application/json
{
Some_Key_Value: "some data"
}
```

## What are the important HTTP methods (or HTTP verbs) – (GET, POST, PUT, PATCH, HEAD, DELETE)?
HTTP defines a set of request methods to indicate the desired action to be performed for a given resource.

The “GET” and “POST” are most used in HTML forms. The default request type in browsers while opening a page, is “GET”.

The “GET”, “POST”, “PUT”, “PATCH”, “HEAD” and “DELETE” are used in RESTful HTTP services, such as “Web API controllers”.

- GET: Request a representation of the specified resource.
- POST: Submits an entity to the specified resource, often causing a change in state or side effects on the server.
- PUT: Replaces all current representations of the target resource with the request payload.|
- PATCH: The PATCH method applies partial modifications to a resource.
- HEAD: The HEAD method asks for a response identical to a GET request, but without the response body.
- DELETE: Deletes the specified resource.
## What are the important HTTP status codes?
An HTTP status code is a server response to a browser’s request. It indicates status of completed action as a response to the request.

HTTP status code classes:

- 1xx – Informational
- 2xx – Success
- 3xx – Redirection
- 4xx – Client errors
- 5xx – Server errors

These are the important status codes:
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

In HTTP, content negotiation is the mechanism that is used for serving different representations of a resource to the same URI to help the user agent specify which representation is best suited for the user (for example, which document language, which image format, or which content encoding).

There are many approaches to archive the goal of this mechanism, but the most commonly used is Server-driven negotiation (a.k.a. proactive negotiation), the key of this mechanism is the request/response headers, where keys: Accept, Accept-Language, Accept-Encoding, Content-Type, etc... identify with the values the expected content (request) or the content offered (response).

Some examples of values used in those headers are: *text/x-www-form-uriencoded, application/json, application/xml, multipart/form-data, etc...*
## Explain how HTTP protocol works?

Hypertext Transfer Protocol (HTTP) is an application-layer protocol for transmitting hypermedia documents, such as HTML. It handles communication between web browsers and web servers. HTTP follows a classical client-server model. The basics of functionality of HTTP are **the request** message and **the response** message, usually a request is made by the browser and send it to the server, then the server takes the request and executes some logic to generate a response (usually a resource), that response is sent to the browser and there the browser does something with that response.

HTTP is a protocol that allows the fetching of resources, such as HTML documents. It is the foundation of any data exchange on the Web, and it is a client-server protocol, which means requests are initiated by the recipient, usually the Web browser.

Another way to understand this concept is to see it as the abstraction of a conversation, i.e. subject *"A"* ask for something to subject *"B"*, *"B"* thinks what is he going to say, and then he answers to *"A"*.

## What is a web server?

The strict definition of a web server says that a web server is a subset of an application server, but there is a slight difference between these type of severs, the difference is the purpose, opposite to application server the purpose of web server is to deliver static web content (HTML pages, files, images, video, etc...) in response to hypertext transfer protocol (HTTP) request from a web browser.

There are 2 relevant characteristics to use a web server, first, the support for other protocols (CGI, CGI variants, etc...), second, the ease of use of services like reverse proxy, load balancing, decompressing request, etc...