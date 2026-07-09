# CookGraph

Plataforma de recetas colaborativa. Los usuarios crean recetas, las versionan, y la
comunidad comenta y valora. Proyecto de portfolio centrado en **arquitectura hexagonal**,
**MongoDB**, **GraphQL** y **Angular**.

> 🚧 En construcción.

## Stack

| Capa | Tecnología |
|---|---|
| Backend | Java 21 · Spring Boot 4.1 · Spring for GraphQL |
| Persistencia | MongoDB 8 |
| API | GraphQL (schema-first) |
| Auth | JWT propio (BCrypt) |
| Frontend | Angular 22 · Apollo Angular · Signals |
| Infra local | Docker Compose |
| Testing | JUnit 5 · Mockito · Testcontainers · GraphQlTester |
| CI | GitHub Actions |

## Arquitectura

Monolito modular partido en **bounded contexts** (`recipes`, `social`, `users`,
`collections`), cada uno con estructura hexagonal (dominio sin framework, puertos
segregados, adaptadores in/out). Sin dependencias directas entre contextos: se comunican
por puertos y eventos. Diseñado para extraerse a subgrafos GraphQL federados sin reescribir
el dominio.

## Puesta en marcha

Requisitos: Docker, JDK 21, Node 24.

```bash
# 1. Base de datos
docker compose up -d mongo

# 2. Backend
cd backend
./mvnw spring-boot:run
```

- API GraphQL: http://localhost:8080/graphql
- GraphiQL (IDE): http://localhost:8080/graphiql
- Health: http://localhost:8080/actuator/health

## Estructura

```
cookgraph/
├── backend/            # Spring Boot · com.cookgraph
├── frontend/           # Angular 22
├── docker-compose.yml  # MongoDB (dev local)
└── LICENSE             # MIT
```

## Roadmap

- Federación GraphQL (extraer contextos a subgrafos + gateway Apollo Federation)
- Búsqueda avanzada con Elasticsearch
- Follow de usuarios + feed de actividad
- i18n ES/EN en el frontend

## Licencia

[MIT](LICENSE) · Diego Pastor Hernández
