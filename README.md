# spring-redis-websocket
[![Heroku Status](https://github.com/RawSanj/spring-redis-websocket/workflows/Deploy%20to%20Heroku/badge.svg)](https://github.com/RawSanj/spring-redis-websocket/actions?query=workflow%3A%22Deploy+to+Heroku%22) [![DockerHub Status](https://github.com/RawSanj/spring-redis-websocket/workflows/DockerHub/badge.svg)](https://github.com/RawSanj/spring-redis-websocket/actions?query=workflow%3ADockerHub) [![License](https://img.shields.io/badge/license-Apache%202-blue?style=flat-square&logo=appveyor)](https://github.com/RawSanj/spring-redis-websocket/blob/master/LICENSE)

## Multi-instance Reactive Chat App using Spring Boot WebFlux and Redis Pub/Sub

Scalable Java 11 Spring Boot WebFlux Chat Application to demonstrate use of Reactive Redis [Pub/Sub] using Reactive [WebSocket Handler], without using any external Message Broker like RabbitMQ to sync messages between different instances. 

[![Deploy to Heroku](https://www.herokucdn.com/deploy/button.png)](https://heroku.com/deploy)

> The older non-reactive servlet based spring-redis-websocket application can be found in below links:
>1. [Spring-Boot 2.3: Java-11 version](https://github.com/RawSanj/spring-redis-websocket/tree/spring-boot-web-2.3)
>2. [Spring-Boot 1.5: Java-8 version](https://github.com/RawSanj/spring-redis-websocket/tree/spring-boot-1.5.x)

### Deploy to Play-with-Docker

Ctrl + Click this button to deploy multiple instances of the spring-redis-websocket load balanced by NGINX:

[![Deploy to PWD](deploy-to-pwd.png)](https://labs.play-with-docker.com/?stack=https://raw.githubusercontent.com/RawSanj/spring-redis-websocket/master/src/main/docker/docker-compose.yml#)

### Installation and Configuration

##### Pre-requisite:
Install and run [Redis] locally or on Docker.

To run Redis in Docker:
```sh
$ docker run -d -p 6379:6379 -e REDIS_PASSWORD=SuperSecretRedisPassword bitnami/redis:4.0.11-r6
```
 
##### Clone repo:
```sh
$ git clone https://github.com/RawSanj/spring-redis-websocket.git
```

#### Build and Run the applications:

Build and run the **spring-redis-websocket** application:
```sh
$ cd spring-redis-websocket

$ mvn clean package

$ mvn spring-boot:run
```

### Run in Docker

#### Build and run the *spring-redis-websocket* locally in Docker:

Build the JAR file:
```sh
$ mvn clean package
```

Build docker image:
```sh
$ mvn spring-boot:build-image
```

Run docker image:
```sh
$ docker run -d -p 8080:8080 \
$ rawsanj/spring-redis-websocket
```

#### Run multiple instance using docker-compose locally
 
Run multiple instances of *spring-redis-websocket* locally load balanced via Ngnix connected to redis container in Docker:
```sh
$ cd src/main/docker
$ docker-compose up
```

#### Or try [Play with Docker] to quickly setup Docker and run in browser:
1. Click Create Instance to quickly setup Docker host.
2. Install git by running: 
```sh
$ apk add git --no-cache
```
3. Clone the repository:
```sh
$ git clone https://github.com/RawSanj/spring-redis-websocket.git
```
4. Run multiple instances of *spring-redis-websocket*:     
```sh
$ cd spring-redis-websocket/src/main/docker
$ docker-compose up
```

### Run in Kubernetes

#### Assuming you have a Kubernetes Cluster up and running locally:

```sh
$ kubectl apply -f src/main/k8s
```

#### Or try [Play with Kubernetes] to quickly setup a K8S cluster:
1. Follow the instructions to create Kuberenetes cluster.
2. Install git by running: 
```sh
$ yum install git -y
```
3. Clone the repository:
```sh
$ git clone https://github.com/RawSanj/spring-redis-websocket.git
```
4. Run multiple instances of *spring-redis-websocket* load balanced by native Kubernetes Service. All instances connected to a single [Redis] pod.     
```sh
$ cd spring-redis-websocket
$ kubectl apply -f src/main/k8s
```


### Tech

**spring-redis-websocket** uses a number of open source projects:

* [Spring Boot] - An opinionated framework for building production-ready Spring applications. It favors convention over configuration and is designed to get you up and running as quickly as possible.
* [Spring Data Redis] - Spring Data Redis provides easy configuration and access to Redis from Spring applications.
* [Redis] - Redis is an open source (BSD licensed), in-memory data structure store, used as a database, cache and message broker.
* [Bootstrap] - Bootstrap is an open source toolkit for developing with HTML, CSS, and JS. Custom Bootstrap theme - [Bootswatch Sketch]. 
* [Docker] - Docker is an open platform for developers and sysadmins to build, ship, and run distributed applications.
* [NGINX] - NGINX is High Performance Load Balancer, Web Server, & Reverse Proxy.
* [Kubernetes] - Kubernetes is an open-source system for automating deployment, scaling, and management of containerized applications.


License
----

Apache License 2.0

Copyright (c) 2020 Sanjay Rawat

[//]: #

   [Spring Boot]:<https://projects.spring.io/spring-boot/>
   [Redis]: <https://redis.io>
   [Runtime]: <https://github.com/kubeless/kubeless/blob/master/docs/runtimes.md#custom-runtime-alpha>
   [Spring Data Redis]: <https://projects.spring.io/spring-data-redis/>
   [Bootstrap]: <https://getbootstrap.com>
   [Bootswatch Sketch]: <https://bootswatch.com/sketchy/>
   [Docker]: <https://www.docker.com>
   [NGINX]: <https://www.nginx.com>
   [Kubernetes]: <https://kubernetes.io>
   [Pub/Sub]: <https://redis.io/topics/pubsub>
   [WebSocket Handler]: <https://docs.spring.io/spring/docs/current/spring-framework-reference/web-reactive.html#webflux-websockethandler>
   [Play with Kubernetes]: <https://labs.play-with-k8s.com>
   [Play with Docker]: <https://labs.play-with-docker.com>
