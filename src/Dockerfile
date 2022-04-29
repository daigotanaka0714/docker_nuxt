FROM node:latest

WORKDIR /src

COPY package.json yarn.lock ./

RUN yarn install

ENV HOST 0.0.0.0
EXPOSE 3000