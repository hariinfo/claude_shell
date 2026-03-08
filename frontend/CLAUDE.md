# Frontend

React 19 + TypeScript + Vite application.

## Commands

```bash
npm install          # Install dependencies
npm run dev          # Vite dev server on :5173
npm run build        # tsc -b && vite build
npm run preview      # Preview production build
npm run test         # Run tests
npm run lint         # Run linter
npm run clean        # Remove dist/
```

## Project Structure

```
src/
  main.tsx           # Entry point (ReactDOM.createRoot)
  App.tsx            # Root component
```

## Conventions

- TypeScript config extends `../tsconfig.base.json`
- Source in `src/`, build output in `dist/`
- API calls use `/api/...` paths — Vite proxies these to the backend on `:8080` in dev (see `vite.config.ts`)
- In production, configure a reverse proxy (nginx, etc.) to route `/api/*` to the backend
