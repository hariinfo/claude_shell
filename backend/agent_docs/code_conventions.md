# Code Conventions

## Package Structure

```
com.claudeshell.backend
  ├── controller/       # REST controllers (@RestController)
  ├── service/          # Business logic (@Service)
  ├── repository/       # Data access (@Repository)
  ├── model/            # Entity and domain classes (@Entity)
  ├── dto/              # Request/response DTOs (records preferred)
  ├── config/           # Spring configuration (@Configuration)
  └── exception/        # Custom exceptions and error handlers
```

## Naming

- Controllers: `XxxController` (e.g., `UserController`)
- Services: `XxxService` (e.g., `UserService`)
- Repositories: `XxxRepository` (e.g., `UserRepository`)
- DTOs: `XxxRequest`, `XxxResponse` (e.g., `CreateUserRequest`)
- Entities: singular nouns (e.g., `User`, `Order`)

## Style

- Use Java records for DTOs and value objects
- Prefer constructor injection (no `@Autowired` on fields)
- Use `final` fields for injected dependencies
- Return `ResponseEntity` from controllers for explicit status codes
- Use `Optional` for nullable return values, never for parameters
- Config in `application.yml`, not `.properties`

## API Design

- RESTful endpoints: `GET /users`, `POST /users`, `GET /users/{id}`
- Use plural nouns for resource paths
- Return appropriate HTTP status codes (201 for creation, 204 for no content, etc.)
- Validate request bodies with `@Valid` and Jakarta Bean Validation annotations
