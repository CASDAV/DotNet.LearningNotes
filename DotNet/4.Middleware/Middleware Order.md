As we said in the previous chapter the middleware is executed sequentially, this means that middleware should follow an order, this is especially important when we have to handle exceptions, authentication, authorization, and etc...

With that in mind here we will explain the right order recommended by Microsoft.

## The right order of middleware

![Recommended order for middleware](../assets/Middleware/MiddlewareOrder.svg)

As you can see in the previous image, this is the recommended order when using the built-in middleware (even Microsoft recommend this order, for more info visit this link: [Microsoft Documentation: Middleware Order ](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/middleware/?view=aspnetcore-8.0#middleware-order)), another thing that you can see there, is the specific place to put the custom middleware in the recommended order,.

<p style="color:yellow">
Note: This order isn't mandatory, so it means that you can remove (sometimes you can remove middleware without problems, read the documentation for more info) or change the order if you want (we do not recommend changing the order of the built-in middleware), but that could lead to some problems, also there are another built-in middlewares that you can use that aren't shown in the image, for more info of this middlewares, and its order visit the next link: <a href="https://learn.microsoft.com/en-us/aspnet/core/fundamentals/middleware/?view=aspnetcore-8.0#built-in-middleware">Microsoft Documentation: Built-in Middleware</a>. 
</p>

Now we will make a short explanation of each of the middleware shown in the image, so you can understand what is going on in the middleware pipeline.

### Exception Handler

There are 2 built-in middlewares to handle exceptions, this time we will only talk about the one used in production environments, for more information of the one used in development environments visit : [Microsoft Documentation: Developer Exception Middleware](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/error-handling?view=aspnetcore-8.0#developer-exception-page).

The function of the exception handler are:
- Catch and log unhandled exceptions.
- Re-execute the request in alternate pipeline using an indicated path, if the response is already started the request isn't re-executed.

<p style="color:yellow">
Note: If the alternate pipeline throws an exception of its own, the middleware will throw the original exception.
</p>

To use this middleware in your app you need to add the next line to the pipeline:
```cs
app.UseExceptionHandler();
```

<p style="color:yellow">
Note: This middleware isn't recommended for development environments, use instead the middleware <code>app.UseDeveloperExceptionPage</code>, an example of how you can implement this 
</p>

For more info of this middleware and error handling visit: [Microsoft Documentation: Error Handling in ASP.Net core](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/error-handling?view=aspnetcore-8.0).

### HTTP Strict Transport Security Protocol (A.K.A. HSTS)

The HSTS is a security enhancement that when is used/mandatory to consume a web app is specified through a response heder, when a browser supports the HSTS it receives the header and stores the configuration for the domain in the browser, this configuration prevents sending any communication through HTTP, forcing the browser to only use HTTPS to communicate with the domain.

As you can see this middleware prevents the user from using invalid, untrusted or insecure certificates, with this option enabled the browser also disable prompts that allow the users to trust temporally those certificates (HSTS basically prevents man-in-the-middle attacks).

Since HSTS is enforced by the client it has some limitations:
- The client must support HSTS (usually only supported by browsers)
- HSTS needs at least one successful HTTPS request to establish the HSTS policy into the browser configuration.
- The application must check every HTTP request and redirect or reject the HTTP request.

To use this middleware in your app you need to add the next line to the pipeline:
```cs
app.UseHSTS();
```

<p style="color:yellow">
Note: This middleware isn't recommended for development environments, that's because HSTS settings are easily cached by browsers (this is specially inconvenient while doing test). By default HSTS excludes the loopback address (local host).
<br/>
<br/>
Here an example of how to use HSTS in development environments:
</p>

```cs
var builder = WebApplication.CreateBuilder(args);

builder.Services.AddRazorPages();

var app = builder.Build();

if (!app.Environment.IsDevelopment())
{
    app.UseExceptionHandler("/Error");
    app.UseHsts();
}

//More middleware...

app.Run();
```

### Https Redirection

As the name of this middleware indicates, the function of this one is to redirect the HTTP requests to HTTPS, this with the purpose to encrypt all the communications between the client and the server to ensure the security of the data.

To use this middleware in your app you need to add the next line to the pipeline:
```cs
app.UseHttpsRedirection();
```

<p style="color:yellow">
Note: If you are deploying your app with a reverse proxy server that can handle by its own the HTTPS redirection, and also writing HSTS headers, the HTTPS redirection and the HSTS middleware isn't required in your app pipeline.
</p>

### Static Files

This middleware allows your web application to serve static files like HTML, CSS, JavaScript, images, and etc.. direct to the clients.

When you create an app you will see a web root directory called **wwwroot**, by default the static files middleware will take this directory as the static files storage for the application.

<p style="color:yellow">
Note: Its posible to change the default directory for more info visit: <a href="https://learn.microsoft.com/en-us/aspnet/core/fundamentals/?view=aspnetcore-8.0&tabs=windows#content-root">Microsoft Documentation: Content root/Web root</a >.
</p>

To use this middleware in your app you need to add the next line to the pipeline:
```cs
app.UseStaticFiles();
```

If for some reason your app need to serve files outside of the wwwroot folder you can explicitly indicate the middleware the directory, here an example:

```cs
using Microsoft.Extensions.FileProviders;

var builder = WebApplication.CreateBuilder(args);

builder.Services.AddRazorPages();
builder.Services.AddControllersWithViews();

var app = builder.Build();

if (!app.Environment.IsDevelopment())
{
    app.UseExceptionHandler("/Error");
    app.UseHsts();
}

app.UseHttpsRedirection();

app.UseStaticFiles(new StaticFileOptions
{
    FileProvider = new PhysicalFileProvider(
           Path.Combine(builder.Environment.ContentRootPath, "MyStaticFiles")), //Here you indicate the directory name (remeber that the file directory should be in the same directory as wwwroot is located)
    RequestPath = "/StaticFiles" //Here you indicate the root of the requets path used to access the files 
});

app.UseAuthorization();

app.MapDefaultControllerRoute();
app.MapRazorPages();

app.Run();
``` 

 You can also have more than one static files middleware for different file directories.

  There is a lot more info about this middleware an its features, to see more visit: [Microsoft Documentation: Static Files Middleware](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/static-files?view=aspnetcore-8.0).

<p style="color:yellow">
Note: For security is recommended to don't serve sensitive files or files that are not going to be shown to the final users. 
</p>

### Routing

### CORS

### Authentication

### Authorization

### Next Steps
- [[Custom Middleware]]