Every Asp.Net core project comes with a JSON file called "launchSettings", this file defines how the application will be launched.

## launchSettings.json example:

```JSON

{

  "iisSettings": {

    "windowsAuthentication": false,

    "anonymousAuthentication": true,

    "iisExpress": {

      "applicationUrl": "http://localhost:4539",

      "sslPort": 44303

    }

  },

  "profiles": {

    "http": {

      "commandName": "Project",

      "dotnetRunMessages": true,

      "launchBrowser": true,

      "applicationUrl": "http://localhost:5287",

      "environmentVariables": {

        "ASPNETCORE_ENVIRONMENT": "Development"

      }

    },

    "https": {

      "commandName": "Project",

      "dotnetRunMessages": true,

      "launchBrowser": true,

      "applicationUrl": "https://localhost:7146;http://localhost:5287",

      "environmentVariables": {

        "ASPNETCORE_ENVIRONMENT": "Development"

      }

    },

    "IIS Express": {

      "commandName": "IISExpress",

      "launchBrowser": true,

      "environmentVariables": {

        "ASPNETCORE_ENVIRONMENT": "Development"

      }

    }

  }

}

```

The previous example shows a default launchSettings.json, as you can see there are 2 sections, <code>"iisSetttings"</code> and <code>"profiles"</code>, first we are going to focus on the "profiles", and then in the "iisSettings".

### "profiles"

The profiles section as you can infer is in charge of defining the deployment profiles of the application, as you can see in the example by default there are 3 profiles, "http", "https", and "IIS Express".

As you noticed, those profiles have some common attributes: "commandName", "dotnetRunMessages", "launchBrowser", "applicationUrl", and "enviromentVariables", each of those attributes are in charge to specify important aspects of the deployment of the application.

Now let's understand each attribute, and what is in charge of:

- **commandName** this attribute will determine the internal and external web server that is going to use to host the application and handle the HTTP request. The values accepted for this attribute are:
	- **Project** this one means that your application will run only in a Kestrel server.
	- **IISExpress** this one means that your application will run Kestrel, but an IIS Express (IIS lightweight version) server will work as a reverse proxy server. (Only for Windows)
	- **IIS** this one means that your application will run Kestrel, but an IIS server will work as a reverse proxy server. (Only for Windows)
- **dotnetRunMessages** this attribute allows or deny the application to display messages in the terminal of the running server.
- **launchBrowser** this attribute determines if once the application is running, a browser window will be initialized to see/consume the application by opening the root URL or not.
- **applicationUrl** this attribute specifies the application base URL or URLs which you can access the application.

<p style="color:yellow">Note: a good practice is to set the port of the application between 1024 - 65536, because the other ports are reserved for the operating system. (Especially on Windows)</p>

- **enviromentVariables** this attribute allows us to set configuration values, by default, it comes with a configuration key called **"ASPNETCORE_ENVIRONMENT"** and the value of **"Development"**, you can change the value depending on your purpose, e.g. Production or Staging.

### "iisSettings"

As you can infer this section is in charge of the configuration when the IIS or IISExpress commandName is used in one profile, this configuration have it's own attributes, those attributes are:
- **windowsAuthentication** This attribute will specify whether Windows Authentication is enabled for your application or not. If true means Windows Authentication is enabled, and false means not enabled.
- **anonymousAuthentication** This attirbute will specify whether Anonymous Authentication is enabled for your application or not. If true means Anonymous Authentication is enabled, and false means not enabled.
- **iisExpress** This attribute has it's own sub attributes, those sub attributes are mainly focused on ports and security protocols.
- **sslPort** This attribute specifies the HTTPS Port number using which you can access the application in the case of an IIS Express Server. The value 0 means you cannot access the application using HTTPS protocol.