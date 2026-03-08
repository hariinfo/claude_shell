# Backend

Java 21 + Spring Boot 3.4 application.

## Quick Reference

```bash
./mvnw spring-boot:run    # Dev server on :8080
./mvnw package             # Build JAR
./mvnw test                # Run tests
```

## Agent Docs

Detailed documentation lives in `agent_docs/`. Before starting any task, review the list below and decide which files are relevant to your work. Read only what you need — do not read all files for every task.

| File | Description | Read when... |
|------|-------------|--------------|
| `agent_docs/building_the_project.md` | Build commands, prerequisites, dependency management | Building, adding dependencies, or troubleshooting build issues |
| `agent_docs/running_tests.md` | Test commands, conventions, and test structure | Writing or running tests |
| `agent_docs/code_conventions.md` | Package structure, naming, style rules, API design | Writing or reviewing any code |
| `agent_docs/service_architecture.md` | Layered architecture, responsibilities per layer | Adding new features, understanding the codebase structure |
| `agent_docs/database_schema.md` | Database setup, migrations, entity conventions | Working with persistence, entities, or schema changes |
| `agent_docs/service_communication_patterns.md` | Frontend-backend communication, HTTP clients, async patterns | Working on API endpoints, external integrations, or async features |

**Instruction**: Before you begin work, tell the user which `agent_docs/` files you plan to read and why. Wait for approval before reading them.
