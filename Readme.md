## Project: Rupia

Rupia is a microservice-based e-wallet platform designed with scalability, security, and event-driven architecture in
mind.
Each microservice is maintained as an independent Git repository and aggregated under this parent project.

### Microservices & Shared Modules

| Name                                                                               | PORT | Remarks                                            |
|------------------------------------------------------------------------------------|------|----------------------------------------------------|
| [rupia-discovery-server](https://github.com/ronem123/rupia-discovery-server)       | 8762 | Microservice - Service  discovery (Eureka)         |
| [rupia-gateway](https://github.com/ronem123/rupia-gateway)                         | 8090 | Microservice - API Gateway                         |
| [rupia-admin-service](https://github.com/ronem123/rupia-admin-service)             | 8091 | Microservice - Super Admin and   Admin activities  |
| [rupia-auth-service](https://github.com/ronem123/rupia-auth-service)               | 8092 | Microservice - Authentication &     Authorization  |
| [rupia-customer-service](https://github.com/ronem123/rupia-customer-service)       | 8093 | Microservice - Customer profile &  eKYC management |
| [rupia-wallet-service](https://github.com/ronem123/rupia-wallet-service)           | 8094 | Microservice - Wallet & balance   management       |
| [rupia-transaction-service](https://github.com/ronem123/rupia-transaction-service) | 8095 | Microservice - Transactions &    ledger            |
| [rupia-consumer](https://github.com/ronem123/rupia-consumer)                       | 0    | Microservice - Kafka consumer / async processing   |
| [rupia-kafka-event](https://github.com/ronem123/rupia-kafka-event)                 | 0    | Shared module - (Kotlin,  events)                  |

# Architecture Overview

___

* Spring Boot–based microservices
* JWT-based authentication
* Kafka for event-driven communication
* PostgreSQL per service (database-per-service pattern)
* Service discovery & API gateway
* Loose coupling via events

# Prerequisites

___

* Java
* 21 Maven 3.9+
* Docker & Docker Compose (optional but recommended)
* PostgreSQL
* Apache Kafka

### Tools and technology used

| Tools             | Version | Purpose                            |
|-------------------|---------|------------------------------------|
| Spring boot       | 4.0.0   | Build spring web app               |
| Spring Web        | 4.0.0   | REST APIs                          |
| Spring Validation | 4.0.0   | Request validation                 |
| Spring Data JPA   | 4.0.0   | ORM & persistance                  |
| PostgresQL        | 15+     | Relational database                |
| JWT               | 0.12.6  | Authentication & authorization     |
| Apache Kafka      | 3.x/4.x | Event-driven messaging             |
| JAVA              | 21      | Runtime                            |
| Lombok            | latest  | Boilerplate code reduction         |
| MapStruct         | 1.6.3   | DTO <-> Entity mapping             |
| Jackson           | 0.12.6  | JSON Serialization/Deserialization |

## Clone and run the application

___

* Clone each microservice into single empty project folder
* Add each microservice as a maven module into the parent project

```
Note: Each microservice is included as a Git submodule.Due to known limitations with submodule pulls, it is recommended 
to clone each microservice repository separately and then include them in the parent project folder. This ensures a stable setup.
The submodule pull issues are expected to be resolved in future Git updates.`
```

## Environment configuration

___

* Create `.env` file and add these secrete name and link this `.env` file into the configuration file

```
  RUPIA_JWT_SECRET_ACCESS=aLYzytRNfvsP+OvcR3AsR2KwR6j9CsLci6L7AuRNv4k=
  RUPIA_JWT_SECRET_REFRESH=gUkSFY9rnwoNNd7ChEJcJN4KO4cJBnwFovVdIzHqc0k=
```

## Notes

___

* Each microservice is independently deployable
* No shared database between services
* Communication via REST + Kafka events
* Designed for fintech-grade scalability and security

# DOCKER NOTES
```
Docker setup and configuration
1. Build an app with
    1. mvn clean package -DskipTests
2. Create DockerFile
3. Create network where each microservice docker containers communicate
    1. docker network create rupia-network
    2. Check if all is fine: docker network ls
4. Build docker image
    1. docker build -t service_name: latest .
5. Create a container and run it on the created network
    1. docker run -d —name container_name —network rupia-network -p hostport:containerport image_name:latest
6. Check if docker container is up and running
    1. docker ps -a
    2. You will get the container id with the image running
7. Check the Docker logs
    1. docker logs container_id
8. Note: if the container is already present, you can remove it
    1. docker rm container_name
```