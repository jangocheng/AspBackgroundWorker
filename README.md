# Titanosoft.AspBackgroundWorker

![Build Status](https://cdanielwaddell.visualstudio.com/_apis/public/build/definitions/991b95e6-1640-4127-b933-3b0aaddb919b/6/badge)

### What is AspBackgroundWorker?

AspBackgroundWorker is a dotnet Standard 2.0 library for scheduling a background job to periodically run inside of an ASP.NET core application.

### How do I get started?

1. install the nuget package:

```
PM> Install-Package Titanosoft.AspBackgroundWorker
```

2. Configure logging however you wish. Read more about logging here: [Logging in ASP.Net Core](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/logging?tabs=aspnetcore2x)

3. Configure your background job, by adding something like this to your confguration section (in Startup.cs):

```csharp
app.UseBackgroundTask(new RecurringBackgroundTask(
    "NewTask",  //A unique name
    new TimeSpan(0,1,0), //Run every minute, 
    (serviceProvider, cancellationToken) => {
        //Your code that uses the service proveder and cancels when the cancellationtoken is cancelled
    }}
)
{
    RunImmediately = true //Run now or wait until the first scheduled instance
})
```
