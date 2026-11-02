# Content Flow

React + Vite frontend, Hono API on Vercel Functions, Neon Postgres via Drizzle. See `Content Flow – Development Plan.md`.

## Run locally

1. Create a Neon project with a `dev` branch and copy its connection string.
2. `copy .env.example .env` and fill in `DATABASE_URL`, `TEMP_PASSWORD`, `CRON_SECRET`.
3. `npm run db:migrate` (applies `drizzle/`), then `npm run db:seed` (admin `mohammed@emqube.com`, starter task types).
4. `npm run dev` and open http://localhost:5173. Sign in as the admin with `TEMP_PASSWORD`; you'll be asked to change it.

## Deploy

Import the folder as one Vercel project. Set `DATABASE_URL` (production branch), `TEMP_PASSWORD` and `CRON_SECRET` as environment variables, run `npm run db:migrate` and `npm run db:seed` once against the production URL. The daily cron (`vercel.json`) calls `/api/cron/cleanup`.

## Checks

`npm run typecheck`, `npm test` (flow rules), `npm run build`.

## Excel import columns

Month, Client, Type, Title, Owner, Due Date, Media, Notes, Flow (names separated by commas). This is an assumed layout; adjust `src/views/Import.tsx` to match the real sheet.
