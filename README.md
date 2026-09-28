# nimbusdesk-discovery-server

Service registry (Netflix Eureka, standalone mode) for the [NimbusDesk](https://github.com/eliangilsierra/nimbusdesk-infra) system — see that repo for the overall architecture, ADRs and roadmap.

Every other NimbusDesk backend service registers itself here on startup, and the API Gateway resolves routes against this registry instead of hardcoded hosts/ports (see [ADR-0001](https://github.com/eliangilsierra/nimbusdesk-infra/blob/develop/adr/0001-service-discovery-con-eureka.md)).

## Stack

- Java 17
- Spring Boot 3.2.4
- Spring Cloud 2023.0.1 (`spring-cloud-starter-netflix-eureka-server`)
- Maven

## Run locally

With Maven installed:

```bash
mvn spring-boot:run
```

With Docker:

```bash
docker build -t nimbusdesk-discovery-server .
docker run -p 8761:8761 nimbusdesk-discovery-server
```

Dashboard: http://localhost:8761

## How it fits in

Part of the NimbusDesk v1 system. See [`nimbusdesk-infra`](https://github.com/eliangilsierra/nimbusdesk-infra)'s `docker-compose.yml` to run it together with the rest of the services.
