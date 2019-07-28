# docker-ssl-webs
Simple way to deploy ssl websites.

- Using Docker to deply many ssl websites on your own server simply and quickly.
- This repository must uses the following docker images: [jwilder/nginx-proxy](https://hub.docker.com/r/jwilder/nginx-proxy) and [jrcs/letsencrypt-nginx-proxy-companion](https://hub.docker.com/r/jrcs/letsencrypt-nginx-proxy-companion)
- Use optionally just for the examples web-01 and web-02: [httpd](https://hub.docker.com/_/httpd)

## Dependencies
Install:
- [Docker](https://docs.docker.com/install/)
- [Docker Compose](https://docs.docker.com/compose/install/)

## Previous settings
- There are 2 folders with examples. Each one has a ".env" file, you need to modificate this with your website data:

- CONTAINER_NAME=< your-domain >
- VIRTUAL_HOST=< your-domain >.com, www.< your-domain >.com
- VIRTUAL_PORT=< your-custom-port > (OPTIONAL*)
- LETSENCRYPT_HOST=< your-domain >.com, www.< your-domain >.com
- LETSENCRYPT_EMAIL=< your-email >@example.com (OPTIONAL**)

 *If you don't set, delete. If your web use other port than 80, set it. And add in docker-compose.yml the follow: EXPOSE: - < your-custom-port >
 
 **If you don't set, delete.

## Run 1st WEB
1- First you need to create a network proxy:
```
$ sudo docker network create nginx-proxy
```
2- Then, run [docker-compose.yml](https://github.com/christian-quisbert/docker-ssl-webs/blob/master/docker-compose.yml) located on the root of the repository:
```
$ sudo docker-compose up -d --build
```
3- Finally, located in the web-0X folder, run:
```
$ sudo docker-compose up -d --build
```

At this point, you have deployed your first website on the server with Docker.
Now, you just need to repeat the 3rd step to start more webs.