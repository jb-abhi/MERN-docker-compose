# Use base image to build
FROM node:18.19.1-alpine AS build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# Use Nginx to serve the build
FROM nginx:latest
WORKDIR /app
COPY --from=build /app/dist /usr/share/nginx/html
EXPOSE 80
