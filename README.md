# Spring Project Template — How to Use

This repository is a minimal Kotlin + Spring Boot + Vaadin template using Gradle.
Use it to bootstrap a new application quickly and consistently.

## Prerequisites

- JDK 21 (or a compatible distribution such as Temurin 21)
- Gradle Wrapper (included) — no need to install Gradle
- Docker (optional, for Docker/Compose based workflows)

## Project Stack

- Kotlin with Spring Boot 3
- Vaadin 24 for UI
- Actuator, Validation, Web
- Micrometer (OTLP/Prometheus registries included but optional)

See `HELP.md` for curated framework links that Spring Boot generated.

## Getting Started

### 1) Clone and run

```bash
./gradlew bootRun     # macOS/Linux
gradlew.bat bootRun   # Windows
```

The app will start on `http://localhost:8080` by default.

### 2) Run tests

```bash
./gradlew test        # macOS/Linux
gradlew.bat test      # Windows
```

### 3) Build a JAR

```bash
./gradlew build
```

The packaged artifact will be at `build/libs/`.

## Using This as a Template for a New Project

1) Create a new repository from this template (or clone and re‑init Git).
2) Update metadata in `build.gradle.kts`:
   - `group`, `version`, and `description`.
3) Rename the base package and directories:
   - Current package: `software.robsoncassiano.template.springproject`
   - Files to update:
     - `src/main/kotlin/.../SpringProjectApplication.kt`
     - `src/test/kotlin/.../SpringProjectApplicationTests.kt`
   - Use your IDE’s “Refactor → Rename Package” to safely rename packages and move folders.
4) Search and replace references to the old name in the repository (README, compose files, etc.).
5) Update application configuration in `src/main/resources/application.properties` as needed.

## Docker and Compose

- A `compose.yaml` file exists, but it’s intentionally empty to let you define services your app needs (databases, message brokers, etc.).
- Add services and networks according to your needs. Example services you might add:
  - Postgres, Redis, RabbitMQ, Keycloak, etc.
- When services are defined, start your dev environment with:

```bash
docker compose up -d
```

Then run the app locally against those services using `bootRun`.

## Observability (Optional)

Micrometer registries for OTLP and Prometheus are on the classpath as runtime dependencies. To use them:

- Prometheus: expose `/actuator/prometheus` and scrape via Prometheus server.
- OTLP: set the required `management.otlp.metrics.export.*` properties.

Refer to Spring Boot and Micrometer docs linked in `HELP.md`.

## Common Gradle Tasks

- `bootRun` — run the application
- `test` — run tests
- `build` — assemble JAR and run tests
- `bootJar` — build only the executable JAR

## Project Layout

```
src/
  main/
    kotlin/…/SpringProjectApplication.kt  # Application entry point
    resources/application.properties      # App configuration
  test/
    kotlin/…/SpringProjectApplicationTests.kt
build.gradle.kts                          # Build configuration
compose.yaml                              # Define dev services (optional)
```

## Tips

- Keep the Vaadin version aligned with the BOM in `build.gradle.kts` (`vaadinVersion`).
- Enable live reload with Spring Boot DevTools (included as `developmentOnly`).
- When changing the Java/Kotlin version, also update your IDE SDK settings.

## License

Add your project’s license here.
