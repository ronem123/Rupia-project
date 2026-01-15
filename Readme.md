## Project: Rupia

Rupia is a microservice-based e-wallet platform designed with scalability, security, and event-driven architecture in
mind.
Each microservice is maintained as an independent Git repository and aggregated under this parent project.

### Microservices & Shared Modules

| Name                                                                               | Remarks                                           |
|------------------------------------------------------------------------------------|---------------------------------------------------|
| [rupia-kafka-event](https://github.com/ronem123/rupia-kafka-event)                 | Shared module - (Kotlin, events)                  |
| [rupia-auth-service](https://github.com/ronem123/rupia-auth-service)               | Microservice - Authentication & Authorization     |
| [rupia-wallet-service](https://github.com/ronem123/rupia-wallet-service)           | Microservice - Wallet & balance management        |
| [rupia-transaction-service](https://github.com/ronem123/rupia-transaction-service) | Microservice - Transactions & ledger              |
| [rupia-customer-service](https://github.com/ronem123/rupia-customer-service)       | Microservice - Customer profile & eKYC management |
| [rupia-discovery-server](https://github.com/ronem123/rupia-discovery-server)       | Microservice - Service discovery (Eureka)         |
| [rupia-gateway](https://github.com/ronem123/rupia-gateway)                         | Microservice - API Gateway                        |
| [rupia-consumer](https://github.com/ronem123/rupia-consumer)                       | Microservice - Kafka consumer / async processing  |

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

## Environment configuration

___

* Create .env file and add these secrete name and link this .env file into the configuration file

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
