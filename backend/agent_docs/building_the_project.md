# Building the Project

## Prerequisites

- Java 21 (JDK)
- Maven 3.9+ (or use the included `./mvnw` wrapper)

## Build Commands

```bash
./mvnw clean package           # Clean build, produce JAR
./mvnw clean package -DskipTests  # Build without running tests
./mvnw spring-boot:run         # Run in dev mode on :8080
./mvnw clean                   # Remove target/ build artifacts
```

## Build Output

- JAR is produced at `target/backend-0.0.1-SNAPSHOT.jar`
- Run the JAR directly: `java -jar target/backend-0.0.1-SNAPSHOT.jar`

## Profiles

- Default profile runs on port 8080 (configured in `application.yml`)
- Override with: `./mvnw spring-boot:run -Dspring-boot.run.arguments=--server.port=9090`

## Dependency Management

- Dependencies are managed in `pom.xml`
- Spring Boot BOM (parent) manages version alignment for Spring ecosystem dependencies
- To add a new dependency, add it to the `<dependencies>` section in `pom.xml`
