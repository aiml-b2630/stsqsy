# StudySquad Sync — v6.1.0

StudySquad Sync is a student study platform for campus room occupancy, timed room holds, and study squad matching.

## Architecture
- React 18 + Vite frontend.
- Express REST API with SQLite persistence through `better-sqlite3`.
- WebSocket room updates at `/ws`; clients receive an initial `rooms:snapshot` and subsequent `rooms:updated` messages.
- Swagger UI at `/api/docs` and the OpenAPI 3.0 document at `/api/openapi.json`.
- Background worker releases expired room holds and broadcasts the updated room inventory.

## Setup
1. Install Node.js 18+.
2. Install dependencies: `npm install`.
3. Copy `.env.example` to `.env` and set a cryptographically random `JWT_SECRET` (at least 32 characters). Generate one with:
   `node -e "console.log(require('node:crypto').randomBytes(48).toString('hex'))"`
4. Set `DB_FILE` to a writable SQLite file path. Its parent directory is created automatically.
5. Start the API with `npm run server` and the frontend with `npm run dev` in a second terminal.

## API documentation
Open `http://localhost:5000/api/docs` while the API is running. Protected endpoints accept `Authorization: Bearer <JWT>`.

## WebSocket protocol
Connect to `ws://localhost:5000/ws` (or `wss://` behind HTTPS). The server sends:
- `rooms:snapshot` on connection.
- `rooms:updated` after successful reservations and expired-hold cleanup.

Each message contains `type`, `rooms`, and `emitted_at` (for updates). The frontend subscribes automatically and refreshes the occupancy grid.

## Scripts
- `npm run dev` — Vite development server.
- `npm run server` — Express + WebSocket API server.
- `npm run build` — production frontend build.
- `npm test` — Vitest suite.

## Security notes
No JWT signing secret is shipped in the repository. Authentication refuses to issue or verify tokens if `JWT_SECRET` is missing, uses the documented placeholder, or is shorter than 32 characters. Do not commit `.env` files or production secrets.
