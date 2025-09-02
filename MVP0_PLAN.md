# MVP0 – Feature Plan (extract)

## Success Criteria
- Pages: /pricing, /checkout/success, /auth (login/reset), /account, /merci
- Stripe Checkout live (3 plans, auto VAT, coupons)
- Webhooks → Supabase (user+plan), Odoo (invoice), Brevo (emails)
- Intercom active; Analytics (GTM/GA4 + Hotjar + tag plan + dashboard)
- Runbook go‑live; QA payments & i18n; uptime monitoring
- SEO basics: multilingual metadata, sitemap, robots.txt

## 4‑Week Plan
**S1 – Foundation**
- Create projects (Vercel, Supabase, Stripe, GitHub) + DPA + 2FA + env vars
- Setup Next.js 15 + shadcn/ui + minimal i18n
- `/pricing` + buttons → `/api/checkout`
- Configure Checkout: `automatic_tax`, `tax_id_collection`, `custom_fields`, coupons

**S2 – Payments & Webhooks**
- Implement `/api/checkout` and `/api/stripe/webhook`
- Detect B2C vs B2B (tax_ids, company)
- Webhooks → Supabase, Odoo, Brevo
- `/checkout/success` (read `session_id`)

**S3 – Auth & Account**
- Supabase Auth (signup post‑payment, login/reset)
- `/account` (plan + invoices)
- `/merci` (waiting list + next steps)
- GTM/GA4 + Hotjar + tag plan + dashboard
- Functional QA for payments + errors

**S4 – GDPR & Go‑live**
- Cookie banner + legal pages (CGU, Privacy)
- Intercom (support/chat)
- Finalize i18n FR/NL/EN (pricing, success, emails)
- SEO publish (metadata, sitemap, robots)
- Go‑live runbook (secrets/idempotency checklist)
- Uptime monitoring + final tests

## Required Access
- GitHub Admin (org, private repo, branch protection), Vercel Admin (team, env),
- Stripe Admin (API, webhooks), Supabase Maintainer (EU), Odoo Admin, Brevo Admin,
- GTM/GA4 IDs, DNS registrar, **Claude Code PR reviews enabled**

## DoD (see CLAUDE.md for the short checklist)
- Payments OK (3 plans + VAT + coupons) · Webhooks OK · Auth OK · Merci OK · Invoicing OK · Intercom OK · Analytics OK · Legal + cookies OK · SEO OK · Runbook OK · Monitoring OK
