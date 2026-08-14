# Fixt

Booking system for service businesses — set your hours, share a link, let people book without the back-and-forth.

## Tech stack

- Next.js (App Router) + TypeScript + Tailwind CSS
- Prisma ORM + PostgreSQL (Neon)
- Clerk (auth)
- Resend (email notifications)
- Deployed on Vercel

## Getting started

1. **Clone the repo**
   ```bash
   git clone https://github.com/<your-username>/fixt.git
   cd fixt
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Set up environment variables**
   ```bash
   cp .env.example .env
   ```
   Fill in `.env` with real values:
   - `DATABASE_URL` — ask your teammate for the shared Neon connection string (or grab it from the Neon dashboard if you're already a project member)
   - Clerk keys — from the [Clerk dashboard](https://dashboard.clerk.com) API Keys page
   - Resend key — from the [Resend dashboard](https://resend.com) (only needed once you hit the email notifications task)

4. **Sync the database schema**
   ```bash
   npx prisma generate
   npx prisma db push
   ```
   This applies `prisma/schema.prisma` to the shared dev database. If a teammate changed the schema, pull the latest code first, then run this again.

5. **Run the dev server**
   ```bash
   npm run dev
   ```
   Open [http://localhost:3000](http://localhost:3000).

## Working with the shared database

Both devs point at the **same** Neon dev database — not separate local instances. This means:

- Schema changes made by one dev are visible to the other after they pull and run `npx prisma db push`
- **Sync before you change the schema.** If you're about to add/edit a model, message your teammate first to avoid conflicting migrations.
- Never commit `.env` — it's gitignored. Only `.env.example` (placeholders) goes in the repo.

## Branch naming

`BOOK-<ticket-number>-short-description`
e.g. `BOOK-12-availability-engine`

## Project status

🚧 In active development — see the project board for current sprint tasks.
