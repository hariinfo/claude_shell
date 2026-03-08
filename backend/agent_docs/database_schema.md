# Database Schema

## Current Status

No database is configured yet. The application currently runs without persistence.

## Planned Setup

When adding a database:

- Use Spring Data JPA with Hibernate
- Prefer PostgreSQL for production, H2 for local dev/testing
- Manage schema migrations with Flyway (preferred) or Liquibase

## Configuration

Add to `application.yml`:

```yaml
spring:
  datasource:
    url: jdbc:postgresql://localhost:5432/claudeshell
    username: ${DB_USERNAME}
    password: ${DB_PASSWORD}
  jpa:
    hibernate:
      ddl-auto: validate    # Use Flyway for schema changes, not auto-DDL
    open-in-view: false      # Disable OSIV for predictable lazy loading
```

## Migration Conventions

- Migration files in `src/main/resources/db/migration/`
- Naming: `V001__create_users_table.sql`, `V002__add_orders_table.sql`
- Each migration is atomic and idempotent where possible
- Never modify an existing migration that has been applied — create a new one

## Entity Conventions

- Use `@Entity` with explicit `@Table(name = "...")`
- IDs: `Long` with `@GeneratedValue(strategy = GenerationType.IDENTITY)`
- Timestamps: `createdAt`, `updatedAt` with `@CreationTimestamp`, `@UpdateTimestamp`
- Use `@Column(nullable = false)` to match NOT NULL constraints
