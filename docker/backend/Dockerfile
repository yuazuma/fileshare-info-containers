# sdk:latest
FROM mcr.microsoft.com/dotnet/sdk:5.0.201-buster-slim-amd64 AS build-stage
WORKDIR /app
ADD ./src ./
RUN dotnet restore
RUN dotnet publish -c Release -o out

# aspnet:latest
FROM mcr.microsoft.com/dotnet/aspnet:5.0.4-buster-slim-amd64 as prod-stage
WORKDIR /app
COPY --from=build-stage /app/out ./
RUN ls -la BackendApp.dll && sleep 50
EXPOSE 80
ENTRYPOINT [ "dotnet", "BackendApp.dll" ]
