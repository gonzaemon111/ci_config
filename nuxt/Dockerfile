FROM node:10-alpine
ENV LANG C.UTF-8
WORKDIR /app
COPY . .
RUN npm install -g vue-cli
ENV HOST 0.0.0.0
EXPOSE 3333