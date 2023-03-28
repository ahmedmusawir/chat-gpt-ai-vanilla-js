# Step 1: Build Stage
FROM node:16.17.1-alpine AS build-stage

WORKDIR /app

COPY package*.json ./

RUN npm config set legacy-peer-deps true

RUN npm install

COPY . .

RUN npm run build

# Step 2: Production Deployment
FROM nginx:1.13.9-alpine

COPY --from=build-stage /app/dist /usr/share/nginx/html

EXPOSE 8001
