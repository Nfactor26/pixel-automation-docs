---
title: "pixel-persistence"
linkTitle: "pixel-persistence"
weight: 2
description: >
  Installation and configuration of pixel-persistence
---

pixel-persistence is an asp.net core based web service used by pixel-designer and  pixel-runner to store and retrieve data. It also comes up with a blazor based UI for showing various reports for test execution results. pixel-persistence requires [mongodb](https://www.mongodb.com/try/download/community) to store automation process and test execution data.

> see docker-compose-*.* files in [project repository](https://github.com/Nfactor26/pixel-automation) if you are intrested in hosting on docker. An official docker image is planned for upcoming release.


- Make sure that an instance of mongodb is up and running
- Extract the files to any location after unblocking the zip file.
- Ensure that DOTNET_ENVIRONMENT OR ASPNETCORE_ENVIRONMENT variable is set to production. See [ENVIRONMENTS](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/environments?view=aspnetcore-7.0#environments) in asp.net 
- Edit the appsettings.json file to set the MongoDbSettings->ConnectionString. Example connectionString "mongodb://localhost:27017". This will vary based on your mongodb configuration.
- Launch pixel-persistence.exe
- Navigate to dashboard - https://localhost:5001/persistence and swagger ui - https://localhost:5001/swagger/index.html) to verify service is up and running. Base Url can be different depending on your setup.

> While the pixel-persistence service can be exposed directly (with Kestrel), it is recommended to use it behind a reverse proxy with SSL termination. See guidance on when to use Kestrel with a reverse proxy. **You will need to provide HTTPS certificate in either case**. Checkout [mkcert](https://github.com/FiloSottile/mkcert) if you are working locally to generate self-signed certificates.

> pixel-persistence doesn't support authentication and authorization out of the box. You would ideally want to host it behind a reverse proxy like [yarp](https://microsoft.github.io/reverse-proxy/) and authenticate and authorize requests before they are proxied. Please see [Authentication and Authorization](https://microsoft.github.io/reverse-proxy/articles/authn-authz.html) with yarp. You can use any reverse proxy of your choice.