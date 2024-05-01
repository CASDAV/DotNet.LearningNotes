## Fedora

The next steps work on Fedora 38 and .Net versions 6,7

### Install .Net SDK

The first step is install the .Net SDK, for this you only need to execute the next command:

- For .Net 7

```bash

sudo dnf install dotnet-sdk-7.0

```

- For .Net 6

```bash

sudo dnf install dotnet-sdk-6.0

```

You can use the next command to list the .Net versions you have installed:

```bash

dotnet --list-sdks

```

### Install the runtime

This step is only if for some reason the previous command doesn't install on you machine the runtimes to execute your .Net applications

- For .Net 7

```bash

sudo dnf install aspnetcore-runtime-7.0

```

```bash

sudo dnf install dotnet-runtime-7.0

```

- For .Net 6

```bash

sudo dnf install aspnetcore-runtime-6.0

```


```bash

sudo dnf install dotnet-runtime-6.0

```

You can use the next command to list the runtimes you have installed:

```bash

dotnet --list-runtimes

```

### Install a code editor

We are going to use Visual Studio Code, to install it go to the next link: 
[Link VS code download page ](https://code.visualstudio.com/docs/?dv=linux64_rpm)

Accept the download, open a terminal and follow the next command:

```bash

sudo rpm -i {The-path-where-you-saved-the-file}/{the-name-of-the-file}.rpm

```

### Install .Net extensions

Install the 3 extension shown below

![VS code .Net extensions](assets/Environment_Setup/extensions.png)