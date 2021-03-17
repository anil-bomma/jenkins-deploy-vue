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


## Setup Docker File
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
CMD ["nginx", "-g", "daemon off;"]
```

## Build docker image
- to build docker image execute in docker file directory `docker build -t docker-vue .`
- it will create docker image in local.
- we can check using images using `docker images`

## Run Docker container
- To run the docker container we need to map the expose port
- To run use `docker run -p 5000:80 -it --name docker-container docker-vue`

## Remove container and images
- To remove conatiner use `docker rm -f container_id`
- To remove image use `docker rmi image image_id`


