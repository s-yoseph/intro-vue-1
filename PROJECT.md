# Project Map

> **Navigation rule:** When a prompt targets a specific area, go directly to
> the mapped path. Do not scan unrelated directories or read files outside
> the relevant path unless the task explicitly requires cross-cutting changes.

---

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend framework | Nuxt.js 3 |
| Backend / DB | Supabase |
| Auth | Supabase Auth |
| Styling | <!-- e.g. Tailwind CSS, UnoCSS --> |
| State management | <!-- e.g. Pinia --> |
| Deployment | <!-- e.g. Vercel, Netlify --> |

---

## Project Structure

| Path | Purpose |
|---|---|
| `nuxt.config.ts` | Nuxt configuration, modules, runtime config |
| `app.vue` | Root app component |
| `pages/` | File-based routes — one file per page |
| `components/` | Reusable UI components |
| `layouts/` | Page layout wrappers |
| `composables/` | Shared logic / Vue composables |
| `middleware/` | Route middleware (auth guards, redirects) |
| `server/api/` | Nuxt server routes (API endpoints) |
| `server/utils/` | Server-side utilities and helpers |
| `lib/supabase.ts` | Supabase client initialization |
| `lib/` | Shared utilities, types, constants |
| `stores/` | Pinia stores (if used) |
| `assets/` | Static assets (images, fonts, global CSS) |
| `public/` | Files served as-is (favicon, robots.txt) |
| `.env` | Local environment variables (gitignored) |
| `.env.example` | Env variable template with placeholders |
| `supabase/migrations/` | Database migration files |
| `supabase/seed.sql` | Seed data for local development |
| `plans/` | Agent-managed plan files — do not edit manually |

---

## Environment Variables

| Variable | Purpose |
|---|---|
| `SUPABASE_URL` | Supabase project URL |
| `SUPABASE_ANON_KEY` | Supabase anon/public key |
| `SUPABASE_SERVICE_ROLE_KEY` | Service role key — server-side only, never expose to client |

---

## Key Conventions

- All Supabase calls go through `lib/supabase.ts` — never initialize the client inline.
- Auth state is managed via `composables/useAuth.ts` (or equivalent) — don't read the session directly in pages.
- Server routes in `server/api/` handle any operation that requires the service role key.
- Environment variables prefixed `NUXT_PUBLIC_` are exposed to the client — all others are server-only.

---

## Notes

<!-- Add project-specific notes, gotchas, or decisions here as the project grows -->
