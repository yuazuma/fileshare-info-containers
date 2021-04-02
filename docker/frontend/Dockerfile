# sdk:latest
FROM mcr.microsoft.com/dotnet/sdk:5.0.201-buster-slim-amd64 AS build-stage
WORKDIR /app
ADD ./src ./
RUN dotnet restore
RUN dotnet publish -c Release -o out

# nginx:stable-alpine
FROM nginx:1.18.0-alpine as prod-stage
COPY --from=build-stage /app/out/wwwroot /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
