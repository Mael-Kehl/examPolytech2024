FROM node:10-alpine as node

WORKDIR /usr/src/app

COPY package*.json ./

RUN npm install 

COPY . .

RUN ng build

FROM nginx:1.13.12-alpine

LABEL maintainer "Maël KEHL"

COPY nginx/ /etc/nginx

COPY --from=node /usr/src/app/dist/angular /usr/share/nginx/html

COPY entrypoint.sh /docker-entrypoint.d/entrypoint.sh