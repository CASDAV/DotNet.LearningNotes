---
id: 09ipn68alnqawuqcuxdv7n6
title: Interview Q&A
desc: ''
updated: 1692765207818
created: 1691033430769
---

## What is Kestrel and what are advantages of Kestrel in Asp.Net Core?

Kestrel is the default cross-platform application server for .Net web applications, it works as development server and also as real application server, this server is able to receive the request from the real internet and send responses back.

Features of Kestrel are:

- Lightweight and fast.

- Cross-platform and supports all versions of .NET Core.

- Supports HTTP & HTTPS.

- Easy configuration

- Multiple apps on the same port is not supported

- Windows authentication is not supported

## What is the difference between IIS and Kestrel? Why do we need two web servers?

The main difference between IIS and Kestrel is that Kestrel is a cross-platform server. It runs on Windows, Linux, and Mac, whereas IIS only runs on Windows.

IIS (Internet Information Services) is a web server (a.k.a. reverse proxy server) developed and supported by Microsoft (not open-source), the principal differences between this server and Kestrel are the purpose and additional services of each of them, IIS seeks to deliver static web content (as most of the web servers), and manage/provide some services for the web applications (load balancing, authentication, decryption of SSL certificates, etc...), in the other hand Kestrel seeks to interact with the end-user client by delivering dynamic content and hosting the code of the application (business logic).

With that said, it's easy to see that IIS and Kestrel are in charge of different aspects of a real world web application, it's very common that an application in a production environment uses both serves one for hosting/handling the execution of the business logic, and the other one to act as a reverse proxy with features like load balancing, caching, URL rewriting, decompressing request, authentication, decryption of SSL certificates, and etc...   

## What is the purpose of launchSettings.json in asp.net core?

Basically, the launchSettings.json file is a configuration file that describes how the .Net application can be launched, usually this file contains run time profiles, these profiles have attributes that describe the ports that will be use the application to receive the clients request, the environment of execution, and etc...

The file is usually used only during the development of the application using Visual Studio. It contains only those settings that required to run the application.

launchSettings.json is only used by Visual Studio and auto-generated projects from the `dotnet` templates.

You don't need launchSettings.json for publishing an app (on production server).

## What is generic host or HostBuilder in .NET Core?

This type of host are objects that encapsulates application resources and lifetime functionality, such as:

- Dependency Injection (DI)
- Logging
- Configuration
- App startup
- App shutdown
- `IHostedService` implementations

The main reason for including all the app's independent resources in one object is lifetime management: control over the app startup and the app shutdown.

The generic host was previously present as ‘Web Host’, in .NET Core for web applications. Later, the ‘Web Host’ was deprecated and a generic host was introduced to cater to the web, Windows, Linux, and console applications.

## What is the purpose of the .csproj file?

The .csproj file is one of the most important files in our .Net application, essentially it tells the compiler how to build the project.

One of the responsibilities of a .csproj is to list the dependencies of the project, similar to dependency management with maven or Gradle and exactly like package.json in JavaScript frameworks (with the difference .csproj is in XML format instead of JSON).

The .csproj file also contains information about the tooling needed to build the project, such as:
- Type of project (web, console, desktop, etc.)
- The target platform/framework (net5.0, net6.0, net7.0, etc.)
- Dependencies on other projects and 3rd party libraries (versions included) 

## What is IIS?

IIS (Internet Information Services) is a web server (a.k.a. reverse proxy server) developed and supported by Microsoft, IIS seeks to deliver static web content (as most of the web servers), and manage/provide some services for the web applications (load balancing, authentication, decryption of SSL certificates, etc...).

A limitation of IIS is that it only runs on Windows. However, it is very configurable. You can configure it to suit your application’s specific needs.

## What is the “Startup” class in ASP.NET core prior to Asp.Net Core 6?

The startup class is the entry point of the ASP.NET Core application. Every Asp.NET Core (Asp.Net Core 5 and earlier) application must have this class. It contains the necessary code to bootstrap the application. This class contains two methods Configure() and ConfigureServices().

- Configure(): The Configure() method is used to essential middleware(s) to the application request pipeline.

- ConfigureServices(): The ConfigureServices() method is used to add services to the IoC container.

To summarize, the Startup class is where:

1. Services required by the app are configured via ConfiguringServices method, and consumed across the app via dependency injection (DI) or application services.

2. The app's request handling pipeline is defined, as a series of middleware components, via the Configure method.

This class was used until .net 5 came out, for further versions .net 6, 7, etc... the class in charge of these functionalities is the "Program" class.

## What does WebApplication.CreateBuilder() do?

`WebApplication.CreateBuilde()` initialize a new instance of the WebApplicationBuilder class with preconfigured defaults.

That instance basically loads the configuration and default services, some examples of the configuration that is loaded in that builder are environment variables, settings like API URLs or server names and connection strings, also set services, application services, etc...

To summarize this method does the following things:

- Configure the app to use Kestrel as web server.

- Specify to use the current project directory as root directory for the application.

- Setup the configuration sub-system to read setting from appsettings.json and appsettings.{env}.json to environment specific configuration.

- Set Local user secrets storage only for the development environment.

- Configure environment variables to allow for server-specific settings.

- Configure command line arguments (if any).

- Configure logging to read from the Logging section of the appsettings.json file and log to the Console and Debug window.

- Configure integration with IIS

- Configure the default service provider.

