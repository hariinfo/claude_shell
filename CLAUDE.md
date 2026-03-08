# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Architecture

Monorepo with two modules:

```
frontend/   - React 19 + Vite + TypeScript (port 5173)
backend/    - Java 21 + Spring Boot 3.4 + Maven (port 8080)
```

Frontend calls the backend directly. In dev, Vite proxies `/api/*` requests to the backend on `:8080` (stripping the `/api` prefix).

## Dev Setup

1. Start the backend: `cd backend && ./mvnw spring-boot:run`
2. Start the frontend: `cd frontend && npm install && npm run dev`

Frontend proxies `/api/*` to the backend in dev. See each module's `CLAUDE.md` for detailed commands and conventions.
