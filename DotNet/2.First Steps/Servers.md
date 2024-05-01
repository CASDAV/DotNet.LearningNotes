When we talk about servers we can separate them into 2 types, software servers and hardware servers, the first focused on applications and code/software execution and hosting, and the second focused on the physical machines that the software runs on (infrastructure).

For our purpose the ones that matter for us are the software servers, same as the pure concept of servers the software servers can also be separated into two main types, these are **Application Servers** and **Web Servers**.

## Application servers

An application server is software that host applications and enable interaction between end-user clients and server-side applications code, usually that code is known as business logic, and it's purpose is to generate and deliver dynamic content, such as transaction results, decision support, or real-time analytics. The client for an application server can be the application’s own end-user UI, a web browser, or a mobile app, and the client-server interaction can occur via any number of communication protocols. [IBM: Web server vs. application server: What is the difference?](https://www.ibm.com/topics/web-server-application-server)

### Examples of application servers

#### Java:

- [JBoss EAP](https://www.redhat.com/es/technologies/jboss-middleware/application-platform)

- [WebSphere Application Server](https://www.ibm.com/products/websphere-application-server)

- [WebLogic Application Server](https://www.oracle.com/java/weblogic/)

- [WildFly](https://www.wildfly.org/)

- [Apache Geronimo](https://geronimo.apache.org/)

- [GlassFish](https://www.oracle.com/middleware/technologies/glassfish-server.html)

- [Payara](https://www.payara.org/)

#### .Net:

- [Kestrel](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/servers/kestrel?view=aspnetcore-7.0)

## Web servers (a.k.a. reverse proxy servers)

The strict definition of a web server says that a web server is a subset of an application server, but there is a slight difference between these type of severs, the difference is the purpose, opposite to application server the purpose of web server is to deliver static web content (HTML pages, files, images, video, etc...) in response to hypertext transfer protocol (HTTP) request from a web browser.[IBM: Web server vs. application server: What is the difference?](https://www.ibm.com/topics/web-server-application-server)

There are 2 relevant characteristics to use a web server, first, the support for other protocols (CGI, CGI variants, etc...), second, the ease of use of services like reverse proxy, load balancing, decompressing request, etc...

### Examples of web servers

- [IIS (Intenet Information Services)](https://www.microsoft.com/en-us/download/details.aspx?id=48264)

- [NGINX](https://www.nginx.com/)

- [Apache HTTP](https://httpd.apache.org/)

- [Cherokee](http://cherokee-project.com/)

Now days the differences between application servers and web servers have become fuzzier, most of the popular servers (application servers and web servers) are hybrids of both.

## Asp.Net core hosting models

There are 2 main models of how is deployed an Asp.Net core, those models are the next ones.

### Application server model

![Application server model](ASP.NetCore_AppServerExec.png)

### Web server model

![Web server model](ASP.NetCore_WebServerExec.png)