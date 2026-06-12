# Contributing to web-dashboard

## Local setup

```bash
cd web-dashboard
npm install
npm run dev
```

Point it at a locally running `core-api` by copying `.env.example` to
`.env` and adjusting `VITE_API_BASE_URL` if needed.

## Code style

We use ESLint + Prettier. Run `npm run lint` before opening a PR.

## Adding a new page

1. Add a component under `src/pages/`.
2. Wire it into the tab navigation in `src/App.tsx`.
3. If it needs data from `core-api`, add a typed fetch helper to
   `src/api/client.ts` rather than calling `fetch` directly in the
   component.