# Lab 21 - Create a Minimal WebAPI using .NET and a corresponding Docker image with GitHub Copilot



## Dockerfile

- Dockerfile.

  ```dockerfile
  # Use the official .NET SDK image as the base image
  FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
  
  # Set the working directory in the container
  WORKDIR /app
  
  # Copy the project file(s) to the container
  COPY *.csproj ./
  
  # Copy the remaining source code to the container
  COPY . ./
  
  # Build the application
  RUN dotnet build -c Release
  
  # Publish the application
  RUN dotnet publish -c Release --no-build -o out
  
  # Use the official .NET runtime image as the base image for the final stage
  FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS runtime
  
  # Set the working directory in the container
  WORKDIR /app
  
  # Copy the published output from the build stage to the final stage
  COPY --from=build /app/out ./
  
  # Espose the port that the application listens on
  EXPOSE 8080
  
  # Set the entry point for the container
  ENTRYPOINT ["dotnet", "/app/MinimalAPI.dll"]
  ```

- Creating an image with Dockerfile.
  
  ```bash
  docker build -t dotnetapp .
  ```

- Execute the below command to run the app on port 8080.

  ```bash
  # This binds port 8080 of the container to TCP port 8080 on 127.0.0.1 of the host (docker run -d -p [binds]:[host]).
  docker run -d -p 8080:8080 --name dotnetapp dotnetapp
  ```

- Test the application using curl.

  1.  Open command prompt terminal and type ``curl -v http://localhost:8080/randomeuropeancounty``

      ![Broken Image](https://github.com/user-attachments/assets/568975db-e659-4214-84f9-cb31a7adad6c)


- Test the application using Web browser.

  1. Open Web browser and type ``http://localhost:8080/tellmeajoke``.

      ![Broken Image](https://github.com/user-attachments/assets/9677fd86-1456-4bd0-9d0c-4d00ad45bb27)


- Test with the other endpoints for example ``/listfiles``.

