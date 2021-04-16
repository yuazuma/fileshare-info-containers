# sdk:latest
FROM mcr.microsoft.com/dotnet/sdk:5.0.201-buster-slim-amd64 AS build-stage
WORKDIR /app
RUN git clone https://github.com/yuazuma/fileshare-info-ui-backend .
RUN dotnet restore
RUN dotnet publish -c Release -o out

# aspnet:latest
FROM mcr.microsoft.com/dotnet/aspnet:5.0.4-buster-slim-amd64 as prod-stage
WORKDIR /app
COPY --from=build-stage /app/out ./
COPY --from=build-stage /app/app.db ./
RUN ls -la FileShareInfoApp.dll && sleep 5
EXPOSE 80
ENTRYPOINT [ "dotnet", "FileShareInfoApp.dll" ]
