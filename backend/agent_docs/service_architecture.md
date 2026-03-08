# Service Architecture

## Overview

The backend is a Spring Boot 3.4 application following a layered architecture pattern.

## Layers

```
HTTP Request
  → Controller (input validation, HTTP concerns)
    → Service (business logic, orchestration)
      → Repository (data access)
        → Database
```

### Controller Layer
- Handles HTTP request/response mapping
- Input validation via `@Valid`
- Delegates to service layer — no business logic here
- Returns DTOs, never entities

### Service Layer
- Contains all business logic
- Orchestrates between repositories
- Transaction boundaries (`@Transactional`) are defined here
- Throws domain-specific exceptions

### Repository Layer
- Data access via Spring Data JPA
- Extend `JpaRepository` or `CrudRepository`
- Custom queries via `@Query` or derived method names
- No business logic — only data operations

## Cross-Cutting Concerns

- **Error handling**: Global `@RestControllerAdvice` for consistent error responses
- **Logging**: SLF4J via Lombok's `@Slf4j` or manual `LoggerFactory`
- **Security**: Spring Security (when added) at the filter chain level
- **Validation**: Jakarta Bean Validation at the controller layer

## Entry Point

- `BackendApplication.java` — `@SpringBootApplication` main class
- Config in `src/main/resources/application.yml`
