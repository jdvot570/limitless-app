# CLAUDE.md — Project Memory (Limitless MVP0)

## Mission
- Product: Limitless — MVP0 (subscriptions: ONE / EVOLVE / ULTIMATE)
- Scope: Next.js (Vercel), Supabase (EU), Stripe Checkout, Odoo, Brevo
- Locales: **fr**, **nl**, **en**
- GDPR: **no card data**, minimal PII, logs without PII

## Engineering Rules
- TypeScript strict, ESLint, Prettier
- UI: **shadcn/ui**, Tailwind
- API: Next.js **/api** routes (server‑only secrets)
- DB: Supabase Postgres with **RLS enabled**
- Payments: **Stripe Checkout** (no Elements for MVP0)

## Security Defaults
- Never expose **STRIPE_SECRET_KEY** or any server secret client‑side
- Prefer **RLS policies** over ad‑hoc checks; no public access to sensitive tables
- Use server SDKs for Odoo/Brevo (never from the browser)

## MVP0 Success Criteria (short)
- Pages: `/pricing`, `/checkout/success`, `/auth` (login/reset), `/account`, `/merci`
- Stripe Checkout live (3 plans, VAT automatic, coupons in P0)
- Stripe webhook → Supabase (user+plan), Odoo (invoice), Brevo (emails)
- Intercom enabled, Analytics (GTM/GA4 + Hotjar), SEO basics (meta/sitemap/robots)
- Runbook go‑live, QA for payments & i18n, uptime monitoring

## Definition of Done (DoD)
- Payment works for 3 plans with auto‑VAT + tested coupons
- Stripe webhook → Supabase + Odoo + Brevo validated end‑to‑end
- Account creation after payment + login/reset operational
- Merci page reachable after payment via login
- Invoice auto‑generated in Odoo + email via Brevo
- Intercom active; tracking complete (GTM/GA4 + Hotjar + dashboard)
- Legal pages + cookie banner live; monitoring & runbook ticked
- SEO active (multilingual metadata, sitemap, robots.txt)

## PR Review — What I care about
- 1) Security/PII & secrets  2) i18n/a11y  3) Perf  4) Tests  5) DoD alignment
- Prefer **minimal & safe diffs**; add targeted unit/integration tests

## How to use me (Claude Code)
- Summon: *“Review this PR using CLAUDE.md and agents/reviewer.md; check DoD.”*
- For DB changes: *“Draft SQL migration w/ RLS policies + rollback as per agents/migrations.md.”*
- For incidents: *“Generate runbook steps and checks for payment/i18n failures.”*

---

## Recipes — Next.js
- **Scaffold page**: "Create a `/pricing` RSC page with shadcn/ui Cards, responsive grid, and SSR meta. Keep styles via Tailwind, no inline CSS."
- **API route**: "Draft `/api/checkout` with schema validation (zod), safe env access (server‑only), error mapping, and unit tests."
- **Bundle check**: "Show me biggest client bundles and suggest code‑splitting for shadcn/ui imports."

## Recipes — Supabase (Postgres + RLS)
- **Migration**: "Write a transactional SQL migration for table `subscriptions` with RLS: owner‑only SELECT/INSERT. Provide `-- down`."
- **Policy audit**: "List exposed tables and propose minimal policies based on routes we have."
- **Seed**: "Create a tiny synthetic seed for plans (ONE/EVOLVE/ULTIMATE)."

## Recipes — Tailwind + shadcn/ui
- **Add component**: "Use `npx shadcn@latest add [component-name]` to add shadcn/ui components."
- **UI spec**: "Generate a Card/Badge/Button layout matching our typography scale and spacing (Tailwind), accessible, focus states visible."
- **A11y pass**: "Audit components for color contrast and keyboard nav; propose minimal fixes."

## Recipes — Stripe Checkout
- **Config**: "Prepare server code to create Checkout Sessions with `automatic_tax`, `tax_id_collection`, coupons; return URL to `/checkout/success`."
- **Webhook**: "Generate verified webhook handler (HMAC) that writes to Supabase and enqueues Odoo/Brevo calls. Include tests and replay notes."

## Recipes — i18n/SEO/Analytics
- **i18n sweep**: "Scan diff for hard‑coded FR; convert to fr/nl/en resource files with keys."
- **SEO basics**: "Add multilingual metadata, sitemap, robots, canonical urls."
- **GTM plan**: "List events (checkout_start, payment_success, error) with payload shapes."
