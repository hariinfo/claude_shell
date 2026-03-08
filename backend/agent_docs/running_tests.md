# Running Tests

## Commands

```bash
./mvnw test                    # Run all tests
./mvnw test -Dtest=ClassName   # Run a specific test class
./mvnw test -Dtest=ClassName#methodName  # Run a specific test method
./mvnw verify                  # Run all tests including integration tests
```

## Test Structure

```
src/test/java/com/claudeshell/backend/
  BackendApplicationTests.java         # Spring context load test
```

## Conventions

- Unit tests: `*Test.java` — no Spring context, use mocks
- Integration tests: `*IntegrationTest.java` — use `@SpringBootTest`
- Controller tests: use `@WebMvcTest(ControllerName.class)` with `MockMvc`
- Service tests: plain JUnit 5 + Mockito, no Spring context needed
- Test files mirror the main source package structure
- Use `@DisplayName` for readable test descriptions

## Test Dependencies

- JUnit 5 (via `spring-boot-starter-test`)
- Mockito (included with starter)
- AssertJ (included with starter)
- MockMvc for controller layer testing
