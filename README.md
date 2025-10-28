# Aegis Workboard

Aegis Workboard is a secure, role-driven task platform built as a modern Nx monorepo. It demonstrates clean separation of concerns, RBAC at the API layer, and a responsive web UI with sensible defaults for production readiness.

## Why this structure?
- **Monorepo (Nx)** for shared types, consistent tooling, and faster dev loops.
- **API-first** design with route guards and service-level checks.
- **Web app** focused on clarity and speed, with room for NgRx/React Query/state libs.

## Quick Start (Docker)
```bash
docker compose up --build
```
- Web: http://localhost:4200 (or the port your app prints)
- API: http://localhost:3000/api

## Manual Dev
```bash
# API
cd apps/api
npm install
npm run start:dev

# Web
cd apps/web
npm install
npm start
```

## Security Notes
- JWT auth with expiry
- Role-based access at controller and service layers
- Input validation (DTOs) recommended with class-validator
- Helmet/CORS configured at the edge

## Testing
- Add unit tests under `*-spec.ts`
- API e2e can be run from `api-e2e` (see project.json)

## Credits & License
This distribution was refactored and rethemed for originality. Third‑party licenses remain intact.


### Drag-to-status (NgRx)
- UI dispatches `moveTask({id,status})` on drop
- Effects call API `PATCH /tasks/:id` with new status
- Reducer updates list immutably
