# Code Style Guidelines

## General Principles
- Write clear, readable code that favors simplicity over cleverness.
- Follow the principle of least surprise — code should behave as readers expect.
- Keep functions and methods short and focused on a single responsibility.
- Prefer explicit over implicit behavior.

## Naming Conventions
- Use descriptive, meaningful names that convey intent.
- Variables and functions: `camelCase` (JS/TS) or `snake_case` (Python, Ruby, Rust).
- Classes and types: `PascalCase`.
- Constants: `UPPER_SNAKE_CASE`.
- Booleans: prefix with `is`, `has`, `should`, or `can` (e.g., `isValid`, `hasAccess`).
- Avoid abbreviations unless universally understood (e.g., `id`, `url`, `config`).

## Formatting
- Use consistent indentation (spaces preferred, width per language convention).
- Keep lines under 100 characters where practical.
- Use blank lines to separate logical sections within a file.
- Place opening braces on the same line (K&R style) for C-family languages.

## Functions and Methods
- Limit parameters to 3-4; use an options object or struct for more.
- Return early to reduce nesting — guard clauses over deeply nested if/else.
- Avoid side effects in functions that appear to be pure computations.

## Error Handling
- Handle errors at the appropriate level — don't swallow exceptions silently.
- Prefer specific error types over generic ones.
- Include context in error messages to aid debugging.

## Comments
- Write comments for *why*, not *what* — the code should explain the what.
- Remove commented-out code; use version control instead.
- Keep comments up to date when modifying the associated code.

## Imports and Dependencies
- Group and order imports: standard library, third-party, local modules.
- Avoid wildcard/star imports.
- Only import what is used.

## Testing
- Write tests alongside the code they verify.
- Test behavior and outcomes, not implementation details.
- Use descriptive test names that explain the scenario and expected result.
