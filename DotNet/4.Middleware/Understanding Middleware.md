## Introduction to Middleware

### What is Middleware?

When we talk about Middleware in .Net we talk about components whose objective is to handle requests and responses using specific logic or operations.

### Middleware Chain

Those components are assembled into the application pipeline. One of the most important things about middleware is the chaining, so it means that every middleware component must be chained one-after-another, with that said you can see that the middleware executes in the same sequence order they are added.

![Middleware chain](../assets/Middleware/MiddlewareChain.png)

>[!note]
>Each middleware should perform just a single operation (Should follow S.R.P.)

### Goals of Middleware

- Compose the sequence of middleware execution.
- Easily addition/removal of functionalities without affecting other middlewares in the pipeline.

### Ways to create Middleware

1. Middleware can be at the request delegate (anonymous method or lambda expression), mostly used in simple operations.
2. The middleware can be a class, mostly used when there is large functionality, operations or is too complex.

### Short-circuiting Middleware (A.K.A. Terminal Middleware)

When a middleware doesn't pass the request to the next middleware is called terminal middleware. Terminal middleware is often desirable because it avoids unnecessary work, this type of middleware can be used to prevent further middleware from processing the request.

## Run Method
 
As we said before the middleware is assembled into the application pipeline, this pipeline is located in the file called **"Program.cs"** by default,  just after calling the build method. Once the bullid method is executed you will get a application builder object usually called **"App"**, this **"App"** object is used to enable or create middleware.

>[!note]
>Don't forget that you have to create the middleware in the same order it is going to be executed.

As we said before there are two ways to create middleware, one of them is using the request delegate. To use the request delegate for create middleware there are some methods, one of them is the **"Run"** method, in this **"Run"** method you will define a lambda expression that you want to execute upon receiving the request.

Examples:

```cs
var builder = WebApplication.CreateBuilder(args);
var app = builder.Build();

app.Run(); //Run method without lambda expression
```

```cs
var builder = WebApplication.CreateBuilder(args);
var app = builder.Build();

app.Run((HttpContext context) => { //Run method with lambda expression
	//Some cool code
});

app.Run();
```

>[!note]
>If the code in your lambda expression invoques or uses some asynchronous methods, your expression must be declared as async.
>>[!example]
>>```cs
>>var builder = WebApplication.CreateBuilder(args);
>>var app = builder.Build();
>>
>>app.Run(async (HttpContext context) =>{
>>	//Some cool asynchronous code
>>});
>>
>>app.Run();
>>```



### Multiple Run() Methods?

Yes, you can add multiple **"Run"** methods into the application pipeline, but because of the nature of the **"Run"** method it will not work as expected, usually the **"Run"** method is used as the end of middleware pipeline, it means that the **"Run"** method doesn't pass forward the request to the subsequent middleware, or in other words the subsequent middleware isn't going to be executed after the **"Run"** method is called. 
 
## Use Method

Another method to create middleware is the **"Use"** method, this is the one that you use when you want to chain multiple request delegates together into your pipeline. This method can also be a short-circuit middleware by not calling the **"next"** parameter.  Unlike the **"Run"** method, the lambda  expression  in this method receives 2 parameters  instad of 1, those are HttpContext and RequestDelegate.

Example:

```cs
var builder = WebApplication.CreateBuilder(args);
var app = builder.Build();

//Middleware 1
app.Use( async (HttpContext context, RequestDelegate next) => {
	await context.Response.WriteAsync("Hello from Middleware 1");
	await next.Invoke(context); //Here the Use method passforward the request 
});

//Middleware 2
app.Run(async (HttpContext context) => {
	await context.Response.WriteAsync("Hello from Middleware 2");
});

app.Run();
```

>[!note]
>In every middleware you can perform actions before and after calling the next delegate (when its posible). 
>>[!example]
>>```cs
>>var builder = WebApplication.CreateBuilder(args);
>>var app = builder.Build();
>>
>>app.Use(async (context, next) =>
>>{
>>    // Work before calling the next request delegate.
>>    await next.Invoke();
>>   // Work after calling the next request delegate.
>>});
>>
>>app.Run(async context =>
>>{
>>   await context.Response.WriteAsync("Hello from 2nd delegate.");
>>});
>>
>>app.Run();
>>```

```cs
var builder = WebApplication.CreateBuilder(args);
var app = builder.Build();

app.Use(async (context, next) =>
{
    // Work before calling the next request delegate.
    await next.Invoke();
    // Work after calling the next request delegate.
});

app.Run(async context =>
{
    await context.Response.WriteAsync("Hello from 2nd delegate.");
});

app.Run();
```

## Middleware Lifecycle

The next image shows the middleware lifecycle, where you can see how the next middlewares in the pipelines are called, how all the middleware executions consolidate into a response, and also the subsequent execution of code and logic after calling the next request delegate.

![Middleware Lifecycle](../assets/Middleware/MiddlewareLifeCycle.svg)

## UseWhen Method

Another method used for adding custom middleware is the **"UseWhen"** method, the main difference with **"Use"** is that **"UseWhen"** executes a branch of middleware when a certain condition is true.

![UseWhen Diagram](../assets/Middleware/UseWhenMiddleware.svg)

Usually you can  use **"UseWhen"** to check if the request has a authorization token, has especial request headers, the request path starts with an specific route, and etc... 

The **"UseWhen()"** method receive 2 arguments (usually in the form of lambda expressions)
- First, the HttpContext that is used to validate the condition.
- Second, the lambda expression of IApplicationBuilder in Program.cs"app" doing something.

Example:

```cs
var builder = WebApplication.CreateBuilder(args);
var app = builder.Build();

//Middleware 1
app.Use( async (HttpContext context, RequestDelegate next) => {
	await context.Response.WriteAsync("Hello from Middleware 1 - Main chain");
	await next.Invoke(context);
});

//Middleware 2
app.UseWhen(HttpContext context => context.Request.Path.StartsWithSegments("api/"), WebApplication appBuilder => {

	appBuilder.Use(async (HttpContext context, RequestDelegate next) => {
		await context.Response.WriteAsync("Hello from Middleware 1 - Branch chain");
		await next.Invoke(context);
	});

	appBuilder.Use(async (HttpContext context, RequestDelegate next) => {
		await context.Response.WriteAsync("Hello from Middleware 2 - Branch chain");
		await next.Invoke(context);
	});
	
});

//Middleware 3
app.Run(async (HttpContext context) => {
	await context.Response.WriteAsync("Hello from Middleware 2 - Main chain");
});

app.Run();
```

## Next Steps

- [[Middleware Order]]