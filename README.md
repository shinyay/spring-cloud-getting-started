# Spring Cloud Getting Started

Spring Cloud provides various useful functions to solove the distributed architecture like Microservices.
This application uses the following services:
- Spring Cloud Gateway
- Spring Cloud Loadbalancer
- Spring Cloud Config Server
- Spring Cloud Eureka

|Spring Cloud|Functions|
|------------|---------|
|Spring Cloud Gateway|API Gateway|
|Spring Cloud Loadbalancer|Load Balancing|
|Spring Cloud Config Server|Configuration Management|
|Spring Cloud Eureka|Service Discovery|


## Description

![spring-cloud-diagram](images/spring-cloud.png)

### Related Repository

- https://github.com/shinyay/spring-cloud-gateway-gs
- https://github.com/shinyay/spring-cloud-loadbalancer-gs
- https://github.com/shinyay/spring-cloud-config-gs
- https://github.com/shinyay/spring-cloud-eureka-server-gs
- https://github.com/shinyay/spring-cloud-config-client-gs

### Role for each Services
#### 1. Spring Cloud Gateway
Spring Cloud Gateway provides APIs and coross cutting concerns to APIs such as security, metrics and resiliency.

- Features
  - Match routes on any request attribute
  - Predicates and filters are specific to routes
  - Request Rate Limiting
  - Path Rewriting
  - Spring Cloud DiscoveryClient integration

##### Implementation
Register routing configuration ro Loadbalancer service into Config Server

![gateway](images/spring-cloud-gateway.png)

```yaml
spring:
  cloud:
    gateway:
      discovery:
        locator:
          enabled: true
      routes:
        - id: loadbalancer
          uri: lb://loadbalancer
          predicates:
            - Path=/myapp/**
          filters:
            - RewritePath=/myapp/(?<path>.*), /$\{path}
```

## Demo

## Features

- feature:1
- feature:2

## Requirement

## Usage

## Installation

## Licence

Released under the [MIT license](https://gist.githubusercontent.com/shinyay/56e54ee4c0e22db8211e05e70a63247e/raw/34c6fdd50d54aa8e23560c296424aeb61599aa71/LICENSE)

## Author

[shinyay](https://github.com/shinyay)
