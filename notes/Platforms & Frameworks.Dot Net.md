---
id: rkq4b6v3g5gtttnqsqxmql3
title: Dot Net
desc: Introduction to .Net
updated: 1695504434945
created: 1689994015219
---

## Introduction to .Net

### What is .Net?

.Net is a cross-platform, high-performace, and open source web application development platform.

### What you can do with .Net?

You can create web applications of any scale, also you can create REST API services, and more!

### Cross-platform?

After you developed your .Net application you will need to host it, that means you're required to install it on a server, once it is done your aplication will recive request from clients and porviding the response, the question at this point is: **Can your application run on the server regardless of its operating system?**, the answer to this question is: **yes!** (for the most relevant, FreeBSD isn't supported natively). Usualy this applications are developed on Windows/Mac machines, and deployed on Linux servers

### Which servers support .Net?

.Net supports Krestel by default as application server, and IIS, NGINX, Doker, Apache, and many more as reverse proxies.

### Is open-source

.Net code is available on GitHub for free, this usaualy means that you will get updates of .Net frequently.

[.Net repository on GitHub](https://github.com/dotnet)

### Is cloud supported?
Microsfot Azure cloud is supported out of the box.

## Parts of .Net Developing

.Net has many tools and frameworks for developing, and also can be used for many projects (web app's, web API's, mobile app's, desktop app's, and many more), but for now we will focus on the most important four for web development, these four are: Asp.Net core MVC, Asp.Net core Web API, Asp.Net core Razor Pages, and Asp.Net core Blazor.

### Asp.Net core MVC

Used in development of medium to complex applications.

### Asp.Net core Web API

Used for creating RESTful services, SOAP services, and more for all types of client aplications.

### Asp.Net core Razor Pages

Used for creating simple and page focused web aplications.

### Asp.Net core Blazor

Used for creating client-side and server side web appplications.

## Short history of .Net

.Net is a platform/framework developed and supported mainly by Microsoft, the history of .Net starts around the 2000s with the first release of **".Net Framework"** this one was mainly supported on Windows operating systems, some of the most popular applications at that time were Asp.Net web forms, Asp.Net MVC, Microsoft WPF, Microsoft Silverligth, Xamarin, PCL, etc... Then in 2012 Microsoft decided to standardize how every thing should be done in the different versions of .Net, that standard was called **".Net Standard"**, later in 2016 the first release of **".Net Core"** was freed, this one was based on the previously mentioned .Net Standard, at that time .Net Framework and .Net Core were 2 separated branches for developing applications, but that changed in 2020 when these 2 branches merged in one platform/framework that's only called **".Net"**, the first version of this unified platform/framework was .Net 5.

### Asp.Net Web Forms vs Asp.Net MVC vs Asp.Net Core

#### Asp.Net web Forms
- Launched on 2002
- Performance issues due to server events and view-state (the web applications were statefull instead of stateless, which means every page has to store its state, and that state will be stored in form of view state, and that view state object has to be transferred from the client to server and viceversa for each request)
- Windows only
- Not cloud-friendly
- Not open-source
- Event-driven development model

#### Asp.Net MVC
- Launched on 2009
- Performance issues due to some dependencies with Asp.Net (.Net framework)
- Windows only
- Sligthly cloud-friendly
- Open-source
- Model-view-controller (MVC patern)

#### Asp.Net Core
- Launched on 2016
- Faster performance
- Cross-platform
- Cloud-friendly
- Open-source
- Model-view-controller (MVC patern)

## Interview questions

### What is Asp.Net Core?

Asp.Net Core is a platform/framework for web development, it's characterized for being cross-platform, cloud-friendly, open-source, and high-performance.

### What are the features of Asp.Net Core?

1. Can create applications at any scale and complexity.

2. Can create REST API, and more.

3. It is cross-platform, you can develop an Asp.Net Core application on Windows, macOS or Linux, and that code will behave in the same way on those operating systems.

4. It is supported by many servers, Asp.Net core can run on Krestel, IIS, NGINIX, Doker, and Apache. 

5. Is open-source.

6. Is cloud supported right out of the box.

### What are the advantages of ASP.NET Core over ASP.NET (.NET Framework)?

- Has a faster performance. 

- Is cross-platform. 

- Is cloud-friendly right out of the box.

### What is Asp.Net Core meta package?

Asp.Net Core meta packages are sets of dependencies that are necessary for each .Net project, they are added automatically to the project from the very beginning of a .Net project. 

Some packages for web development with .Net are:

- Microsoft.AspNetCore.Diagnostics
- Microsoft.AspNetCore.Hosting
- Microsoft.AspNetCore.Routing
- Microsoft.AspNetCore.Server.IISIntegration
- Microsoft.AspNetCore.Server.Kestrel
- Microsoft.Extensions.Configuration.EnvironmentVariables
- Microsoft.Extensions.Configuration.FileExtensions
- Microsoft.Extensions.Configuration.Json
- Microsoft.Extensions.Logging
- Microsoft.Extensions.Logging.Console
- Microsoft.Extensions.Options.ConfigurationExtensions
- NETStandard.Library 

### When do you choose classic ASP.NET MVC over ASP.NET Core?

When you don't need cross-platform support for your web app.


### What is a web application framework, and what are its benefits?

A web application framework is a framework designed to support the development of web applications, these web applications include web services, web resources, and web API's. Web application frameworks usually provide a standard way to build and deploy web applications.

Benefits:

- Saves a lot of time, you don't have to start a project from the scratch.

- Ease of development process.

- Improves the data proficiency.

- Increase security.

- Debugging and testing are easier.

- Makes systems more reliable.

- Create more fault-tolerant systems
