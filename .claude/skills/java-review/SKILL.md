---
name: java-review
description: Review Java code for bugs, performance issues, security vulnerabilities, and adherence to best practices
disable-model-invocation: true
allowed-tools: Read, Grep, Glob, Agent, Bash(find *), Bash(git diff *)
argument-hint: [file-or-directory]
---

## Java Code Review

Review the Java code at `$ARGUMENTS`. If no argument is provided, review all staged changes (`git diff --cached`) or unstaged changes (`git diff`).

### Review Checklist

Analyze the code for issues in these categories:

**Correctness & Bugs**
- Null pointer risks and missing null checks
- Off-by-one errors, incorrect loop bounds
- Resource leaks (streams, connections, locks not closed in finally/try-with-resources)
- Concurrency issues: race conditions, missing synchronization, unsafe publication
- Incorrect equals/hashCode contracts
- Exception handling: swallowed exceptions, catching overly broad types

**Performance**
- Unnecessary object creation in hot paths
- String concatenation in loops (use StringBuilder)
- Inefficient collection usage (wrong data structure, missing initial capacity for large collections)
- N+1 query patterns in database access
- Missing use of streams/parallel streams where appropriate
- Unbounded collection growth or missing pagination

**Security**
- SQL injection (raw string concatenation in queries)
- Unvalidated user input reaching sensitive operations
- Hardcoded secrets or credentials
- Insecure deserialization
- Path traversal vulnerabilities
- Logging sensitive data

**Design & Maintainability**
- SOLID principle violations
- God classes or methods (excessive responsibility)
- Mutable state exposed via getters (returning internal collections directly)
- Missing or incorrect use of access modifiers
- Raw types instead of parameterized generics

**Java-Specific Best Practices**
- Use of Optional vs null returns for APIs
- Proper use of records, sealed classes (Java 17+)
- Preferring List.of/Map.of over mutable collections when immutability is intended
- Correct use of var (local variable type inference)
- Appropriate use of functional interfaces and lambdas

### Output Format

For each finding, report:

1. **File and line number** — `path/to/File.java:42`
2. **Severity** — CRITICAL / WARNING / INFO
3. **Category** — from the checklist above
4. **Issue** — brief description
5. **Suggestion** — concrete fix or improvement

Summarize findings at the end grouped by severity. If the code is clean, say so — don't invent issues.
