# SpringBoot best practice
[![Build Status](http://www.concourse.developer-tm.com:8080/api/v1/teams/main/pipelines/springboot-bestpractice-pipeline/jobs/unit-test/badge)](https://www.concourse.developer-tm.com/teams/main/pipelines/springboot-bestpractice-pipeline)
[![MIT License](http://img.shields.io/badge/license-MIT-blue.svg?style=flat)](https://github.com/tomoyane/springboot-bestpractice/blob/master/LICENSE.txt)

About Spring Boot best practice architecture.

## Environment

```bash
$ SPRING_PROFILES_ACTIVE=""

$ MYSQL_DB_HOST=""
$ MYSQL_DB_NAME=""
$ MYSQL_DB_USER=""
$ MYSQL_DB_PASS=""

$ REDIS_DB_HOST=""
$ REDIS_DB_PORT=""
$ REDIS_DB_PASS=""
```

### Local environment

Local development property file is application-loc.yml.

```bash
$ SPRING_PROFILES_ACTIVE="local"
```

Working on docker container.
 * Docker Image
   * MySQL
   * Redis
   * OpenJDK

Cassandra cluster.
 * CentOS7 virtual machine 
 * 3 nodes

#### MySQL
Sample query is sql/mysql_sample.sql file.

Sample Class
 * UserEntity.java
 * UserService.java
 * UserRepository.java
 * InfoEntity.java
 * InfoService.java
 * InfoRepository.java
   
#### Redis
Sample Class
 * UserService

### Develop environment
Develop development property file is application-dev.yml.

```bash
$ SPRING_PROFILES_ACTIVE="dev"
```

## Build
Git clone
```bash
$ git clone https://github.com/tomoyane/springboot-bestpractice.git
```

Run test
```bash
./gradlew test
```

### Using docker container
Docker image build
 * Build SpringBoot best practice application.
 * Use docker for local development.
   * MySQL
   * Redis
   * OpenJDK 

```bash
$ docker-compose -f docker-compose-local.yml build
```

Run container
```bash
$ docker-compose -f docker-compose-local.yml up -d
```

## Authentication and Authorization
Spring security.

JWT.

## Architecture
```
spring-boot-bestpracite
├── main
│   ├── java
│   │    └── com
│   │        └── bestpractice
│   │           └── api
│   │               ├── App.java
│   │               ├── common
│   │               │   ├── config
│   │               │   ├── property
│   │               │   └── util
│   │               │
│   │               ├── controller
│   │               │   ├── Advice.java
│   │               │   ├── v1
│   │               │   └── v2
│   │               │
│   │               ├── domain
│   │               │   ├── entity
│   │               │   ├── model
│   │               │   ├── repository
│   │               │   └── service
│   │               │
│   │               ├── exception
│   │               │
│   │               └── security
│   │                   ├── filter
│   │                   └── role
│   │ 
│   └── resources
│       ├── application-dev.yml
│       └── application-local.yml
└── test
    ├── java
    │   └── com
    │       └── bestpractice
    │           └── api
    │               ├── AppTests.java
    │               │
    │               ├── common
    │               │
    │               ├── controller
    │               │
    │               ├── repository
    │               │
    │               └── service
    │
    └── resources
        └── application-test.yml
```

## License
[MIT](https://github.com/tomoyane/springboot-bestpractice/blob/master/LICENSE)
