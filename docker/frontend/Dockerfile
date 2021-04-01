# node:lts-buster-slim
FROM node:14.16.0-buster-slim as build-stage
WORKDIR /app
COPY ./src/package*.json ./
RUN npm install
ADD ./src ./
RUN npm run build

# nginx:stable-alpine
FROM nginx:1.18.0-alpine as prod-stage
COPY --from=build-stage /app/dist /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
