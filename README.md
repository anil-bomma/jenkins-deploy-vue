# Jenkins Deploy Vue
This project help in understanding to deploy any frontend application to deploy using Jenkins


## How to install docker on mac
- install homebrew `/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"`
- install docker using brew `brew install --cask docker`
- once you install try to check the version using `docker version`


## Vue Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```


## Setup Docker Image
```
FROM node:12.18.1-alpine AS build
WORKDIR /app
COPY ./package.json ./
RUN npm install
COPY . .
RUN npm run build

FROM nginx:1.19.0-alpine AS prod-stage
COPY --from=build /app/dist /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon --off;"]
```