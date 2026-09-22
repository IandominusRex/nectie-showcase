# Nectie

**A two-sided marketplace connecting creative talent with the people who book them — LinkedIn + Fiverr for musicians, artists, photographers, and event organisers.**

🔗 **Live demo:** [nectie.co](https://nectie.co)
📱 A native iOS/Android app (React Native/Expo) is also in progress — see [Architecture](#architecture).

> This is a **showcase repo** — a write-up of what I built and learned. The actual source lives in a private repository; this repo intentionally contains no application code.

---

## What it is

Nectie is a two-sided web (and soon mobile) platform built solo over ~8 months (Jan–Sep 2026): people discover and book **gigs** and **events**, organizations operate as first-class **group accounts**, and events carry their own **ticketing** system with Stripe-backed payments and payouts.

- **795 commits**, one person, from a blank repo to a production app with real users and real payments processing.
- **41 database tables**, 60+ routes, a documented cross-platform shared data layer.
- Everything below is described from the outside — architecture, decisions, and what went wrong along the way — without publishing the code itself.

## Tech stack

| Layer | Tech |
|---|---|
| Web | Next.js 16 (App Router), React 18.3, TypeScript, Tailwind, Framer Motion |
| Mobile | React Native 0.86 (Expo SDK 57), React 19, NativeWind, Reanimated |
| Data | Supabase (Postgres, Auth, Storage) |
| Payments | Stripe Connect (destination charges, refunds, payouts) |
| Other | Resend (email), Leaflet/OpenStreetMap (map discovery) |
| Infra | Vercel, npm workspaces monorepo |

## Architecture

Nectie is one monorepo with two consumer apps that converge on a shared data layer rather than duplicating query logic:

```
nectie/
├── nectie-mvp/       → production Next.js web app
├── nectie-mobile/     → React Native (Expo) app — the primary target;
│                        web is the try-before-you-download surface
└── packages/
    ├── core/          → platform-neutral query functions, shared by both apps
    └── tokens/         → shared design tokens
```

`packages/core` holds pure functions that take a Supabase client as an argument instead of creating one — no `next/*` imports, no DOM globals — enforced by ESLint so the mobile bundler (Metro) can consume the same code as the Next.js web app. The rule driving this: **no query may have two implementations.** When mobile needs a query the web already has, the web's version gets extracted into `core` and the web call site is migrated in the same change — not duplicated. A running log (`schema-findings.md`, in the private repo) tracks every type mismatch this extraction process has caught — each one was a latent bug already live on web.

## Engineering stories

A few specific problems worth telling, because "I use Next.js and Supabase" doesn't say much on its own.

### The audit that found a months-old silent failure

A routine performance check noticed an idle, logged-out browser tab firing **334 Supabase requests in 25 seconds** — an infinite refetch loop from an unstable array reference in a `useEffect` dependency list. Chasing that one bug backward led to something much bigger: a version mismatch between `@supabase/ssr` and `@supabase/supabase-js` had changed a generic type signature, and as a result **every Supabase query in the app had been typed as returning `never[]`** — silently, for months. The compiler never caught it. Developers (including past-me) had been "fixing" the resulting type errors the only way that seemed to work: `as any`. By the time this was found, the codebase had accumulated **381 of those casts**, and two queries were silently hitting tables that didn't exist in production. Fixing the root cause and removing all 381 casts restored real type safety across the app — and incidentally turned up a stored-XSS gap where the sanitization library silently no-op'd during server-side rendering.

**What this taught me:** a type error you keep suppressing isn't a UI annoyance, it's a symptom — and dependency upgrades need to be checked against the types they promise, not just whether the build passes.

### The ticketing overhaul

Before building a full ticketing system, I read through how Eventbrite, Peatix, Posh, and Luma structure fees and payouts, and used that to pressure-test Nectie's own numbers. Two things fell out of that review before a single ticket had sold in production:

- The fee schedule was **losing money on every order below a threshold price** — a pricing plan that looked fine on paper broke on the cheap end.
- Ticket prices were being stored and passed to Stripe in the wrong unit — a bug that, uncaught, would have charged a customer roughly **100x the listed price** on the very first live sale.

The resulting rebuild spanned 10 phases: correct unit handling, a working refund flow (the original design cost the platform 100% of a refunded order because it never issued the Stripe transfer reversal), and a repositioning of the product thesis — Nectie can offer something competitors can't by owning both the "who do I book" and "how do I sell tickets to it" sides of the same event.

**What this taught me:** the scariest bugs in a payments system aren't crashes, they're silent unit/logic errors that only show up as a wrong number on someone's card statement — which means payment code needs adversarial review before launch, not just after.

### Cross-tool configuration traps

Running the same repo across two different agent tools (Claude Code and opencode) surfaced a subtle config precedence bug: opencode's instruction loader stops at the first `AGENTS.md` it finds walking up the directory tree and never evaluates `CLAUDE.md` after that — even a three-line `AGENTS.md` meant for something unrelated silently blanked out load-bearing build configuration for an entire subproject. Fixed by making the instruction file list explicit rather than relying on discovery order.

**What this taught me:** implicit "first match wins" config resolution is a trap the moment you have more than one tool reading the same directory — be explicit, don't rely on discovery order.

## By the numbers

- **795** commits, Jan–Sep 2026
- **41** database tables
- **62** dated, evidence-based debugging write-ups kept alongside the code (root cause + fix, not just "fixed a bug")
- **381** unsafe type casts removed in a single audit after finding their root cause
- **10** phases in the ticketing system rebuild
- **2** apps (web + mobile) sharing one typed data layer

## Screenshots

_[Screenshots pending — to be added from a live walkthrough]_

---

Built by Ian Lim Zhen Jun · [LinkedIn](https://www.linkedin.com/in/ian-lim-1505a3205/)
