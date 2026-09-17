# Run ModelWise in one environment

The selected environment is **Local + Docker** because it gives ModelWise a real PostgreSQL database, repeatable setup and a clean path to Vercel without tying the application to a proprietary workspace.

## Fastest start

Install Docker Desktop, open a terminal in this folder, and run:

```bash
docker compose up --build
```

The first start installs the schema, seeds all four learning tracks, and opens ModelWise at `http://localhost:3000`. The database is retained in the `modelwise_data` Docker volume between restarts.

Use:

- Learner: `test@example.com` / `password`
- Administrator: `admin@example.com` / `password`

Stop the services with `docker compose down`. This preserves the database. Use Docker Desktop’s volume controls if you intentionally need a completely fresh database.

## Optional integrations

The learning platform works without Stripe or Resend keys. Without Stripe, enrollment uses a safe preview checkout path. Without Resend, email events are recorded in server output.

To exercise those integrations, create a local `.env` beside `compose.yaml`:

```env
STRIPE_SECRET_KEY=sk_test_your_key
STRIPE_WEBHOOK_SECRET=whsec_your_secret
STRIPE_PRICE_ID_FOUNDATIONS=price_your_foundations_price
RESEND_API_KEY=re_your_key
RESEND_FROM_EMAIL=ModelWise <learning@your-verified-domain.com>
OPENAI_API_KEY=sk-proj-your-key
OPENAI_MODEL=gpt-5.2
```

For local Stripe webhook testing, run Stripe CLI forwarding to `http://localhost:3000/api/webhooks/stripe` and use the signing secret it prints.

## Smoke test

1. Open `/` and select **Explore courses**.
2. Open **ModelWise Certified — Foundations** and continue to sign in.
3. Sign in as the learner and open `/dashboard`.
4. Continue Foundations, open its quiz, submit answers, and open the applied lab.
5. Sign out, sign in as the administrator, and open `/admin`.
6. Review users, edit a course, inspect certificates, and open analytics.
7. Open `/verify/not-a-real-credential` to confirm the public invalid-credential state.

## Run without Docker

Provide a PostgreSQL URL in `.env.local`, then run:

```bash
npm install
npm run setup
npm run dev
```

## Later: migrate to production

1. Create a managed PostgreSQL database through Neon, Supabase, or another Vercel-compatible provider.
2. Set `DATABASE_URL`, `NEXTAUTH_SECRET`, `NEXTAUTH_URL`, Stripe and Resend values in Vercel.
3. Run the Prisma schema and seed against the managed database once.
4. Import the repository into Vercel and deploy it as a Next.js project.
5. Register `https://YOUR_DOMAIN/api/webhooks/stripe` for `checkout.session.completed`.
6. Replace the prepared credentials provider with hashed passwords or a production identity provider before opening public registration.
