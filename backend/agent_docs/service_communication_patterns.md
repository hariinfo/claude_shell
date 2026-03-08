# Service Communication Patterns

## Frontend ↔ Backend

- Frontend calls the backend via REST over HTTP
- In dev: Vite proxies `/api/*` to `http://localhost:8080` (stripping the `/api` prefix)
- In production: reverse proxy (nginx, etc.) routes `/api/*` to the backend

## API Design

- All endpoints are prefixed at the root level (e.g., `/health`, `/users`)
- Frontend calls `/api/health` → proxy rewrites to `/health` on backend
- Response format: JSON
- Error responses follow a consistent structure:

```json
{
  "status": 400,
  "error": "Bad Request",
  "message": "Validation failed",
  "details": ["field 'email' must not be blank"]
}
```

## HTTP Client (outbound calls)

When the backend needs to call external services:

- Use Spring's `RestClient` (preferred in Spring Boot 3.4+) or `WebClient` for reactive
- Define client beans in a `@Configuration` class
- Use timeouts: connect (5s), read (10s)
- Implement retry with exponential backoff for transient failures

## Async Communication

When async messaging is needed:

- Prefer Spring's `@Async` for simple background tasks
- Use a message broker (RabbitMQ, Kafka) for cross-service communication
- Define event DTOs in a shared package
