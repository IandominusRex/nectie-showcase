<a name="readme-top"></a>

<div align="center">

# Nectie

### Show the work. Get booked.

**A two-sided marketplace connecting creative talent with the people who book them.**
Musicians, photographers, DJs, emcees, visual artists — and the venues, brands and organisers hiring them.

[![Live Demo](https://img.shields.io/badge/🔗_Live_Demo-nectie.co-FF6B4A?style=for-the-badge)](https://nectie.co)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Ian_Lim-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/ian-lim-1505a3205/)

![Status](https://img.shields.io/badge/status-live_in_production-brightgreen?style=flat-square)
![Built Solo](https://img.shields.io/badge/built_solo-8_months-orange?style=flat-square)
![Source](https://img.shields.io/badge/source-private-lightgrey?style=flat-square)

![Next.js](https://img.shields.io/badge/Next.js_16-000000?style=flat-square&logo=nextdotjs&logoColor=white)
![React](https://img.shields.io/badge/React-20232A?style=flat-square&logo=react&logoColor=61DAFB)
![React Native](https://img.shields.io/badge/React_Native-20232A?style=flat-square&logo=react&logoColor=61DAFB)
![Expo](https://img.shields.io/badge/Expo-000020?style=flat-square&logo=expo&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![Supabase](https://img.shields.io/badge/Supabase-3ECF8E?style=flat-square&logo=supabase&logoColor=white)
![Tailwind](https://img.shields.io/badge/Tailwind_CSS-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white)
![Stripe](https://img.shields.io/badge/Stripe-635BFF?style=flat-square&logo=stripe&logoColor=white)
![Vercel](https://img.shields.io/badge/Vercel-000000?style=flat-square&logo=vercel&logoColor=white)

<br>

![Nectie walkthrough](nectie-walkthrough.gif)

<sub>*The feed, map-based discovery, an event's organiser view, and the block-based portfolio builder — recorded live from [nectie.co](https://nectie.co).*</sub>

</div>

---

### Contents

- [The Problem](#the-problem)
- [The Solution](#the-solution)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Architecture](#architecture)
- [Engineering Deep-Dives](#engineering-deep-dives)
- [By the Numbers](#by-the-numbers)
- [About This Repo](#about-this-repo)
- [Contact](#contact)

## The Problem

**Booking a working musician in 2026 still runs on Instagram DMs.**

A venue finds an act through a friend or a tagged photo. They DM them. They ask if the band is free on the 14th, go quiet for a week, come back to negotiate a fee, then settle the real details — backline, set length, load-in time, who's covering parking — across forty messages nobody can find again. Payment happens by bank transfer, eventually, after two reminders.

Every part of that is a product gap:

- **A profile that can't carry the work.** LinkedIn gives a musician a headshot and a job title. The actual pitch is a recording, a live video, and photos from the last show — none of which a text-first professional network can hold.
- **Availability lives in one person's head.** "Are you free on the 14th?" is the single most repeated message in the industry, and answering it is unpaid admin.
- **Terms get agreed after the yes, not before.** Fee, deposit, cancellation, and technical requirements surface once someone is already committed — which is exactly when they're hardest to negotiate.
- **A band is not a person.** Every mainstream platform models one human per account. A four-piece has no identity of its own: no shared inbox, no collective track record, no way to be reviewed or booked *as the band*.
- **Booking and ticketing are separate businesses.** The venue books the act on one tool and sells tickets on another. Neither knows the other exists, so the lineup, the guest list, and the door count never reconcile.

The people absorbing that friction are the ones with the least leverage to fix it: freelance creatives who are paid per gig and spend hours a week on coordination they can't bill for.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## The Solution

Nectie collapses that whole pipeline into one product — discovery, booking, terms, payment, and the event itself.

| The friction | How Nectie handles it |
|---|---|
| A headshot can't show what you sound like | A block-based portfolio that carries **audio, video and photo** — 17 block types, live preview, custom theming |
| "Are you free on the 14th?" | Public **availability calendar** with recurring rules, per-date overrides, and an instant-booking toggle |
| Terms negotiated after the handshake | Gig listings carry **fee, payment terms, tech rider, backline and stage plot** on the posting itself |
| A band has no identity of its own | **Group accounts are first-class actors** — they post, apply, RSVP, message and collect reviews as themselves |
| Booking and ticketing are separate tools | **One event** holds its performer lineup, RSVP list, ticket tiers and QR check-in |
| Chasing an invoice after the show | **Stripe Connect** handles checkout, platform fees, payouts and refunds against the agreed terms |

The strategic bet underneath it: Nectie is the only platform that owns *both* sides of the same event — "who do I book?" **and** "how do I sell tickets to it?" A ticketing company can't answer the first question; a talent directory can't answer the second.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Features

- 🎭 **Two-sided marketplace** — creatives build a portfolio and publish availability; venues and organisers post gigs and hire directly, with no bidding race to the bottom.
- 👥 **Group accounts as first-class actors** — a band, ensemble or crew operates as a single account with its own profile, track record and reviews.
- 🎟️ **Full event lifecycle** — create, edit, cancel, RSVP, sell tickets via Stripe Connect, scan QR tickets at the door, publish a performer lineup, and post a photo album afterwards.
- 💼 **Structured gig postings** — tech riders, backline requirements, payment terms and stage plots are fields in the posting flow, not buried in a chat thread.
- 🧱 **Block-based portfolio builder** — 17 block types (hero, media gallery, audio/video embeds, stats, testimonials, résumé, hosted events, …), 5 presets, live preview, per-block theming.
- 🗺️ **Map-based discovery** — Leaflet + OpenStreetMap geolocation search across gigs, events, creatives, groups and venues.
- 💬 **Realtime messaging** — DMs and per-project chat threads with folder organisation and realtime delivery.
- 📅 **Availability & booking calendar** — recurring rules, per-date overrides, instant booking, and granular visibility controls.
- 📰 **Ranked social feed** — posts, comments, likes and follows, ranked by a tuned relevance score (host > performer > attendee > shared tag) rather than reverse-chronological order.
- 🔒 **Granular privacy** — per-profile visibility for profile, posts, portfolio, calendar, and who is allowed to message you.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Tech Stack

| Layer | Stack |
|---|---|
| **Web** | Next.js 16 (App Router) · React 18.3 · TypeScript · Tailwind CSS · Framer Motion |
| **Mobile** | React Native 0.86 (Expo SDK 57) · React 19 · NativeWind · Reanimated |
| **Data** | Supabase (Postgres, Auth, Storage) — 41 tables |
| **Payments** | Stripe Connect — destination charges, refunds, payouts |
| **Other** | Resend (transactional email) · Leaflet + OpenStreetMap (map discovery) |
| **Infra** | Vercel · npm workspaces monorepo |

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Architecture

One monorepo, two consumer apps, converging on a shared data layer instead of duplicating query logic:

```
nectie/
├── nectie-mvp/        → production Next.js web app
├── nectie-mobile/      → React Native (Expo) app — the primary target;
│                         web is the try-before-you-download surface
└── packages/
    ├── core/           → platform-neutral query functions, shared by both apps
    └── tokens/          → shared design tokens
```

`packages/core` holds pure functions that take a Supabase client as an argument instead of creating one — no `next/*` imports, no DOM globals, enforced by ESLint so the mobile bundler (Metro) can consume exactly the same code the web app runs.

The governing rule: **no query gets two implementations.** The moment mobile needs a query the web already has, the web's version is extracted into `core` and the web call site is migrated in the same change — never duplicated. A running log tracks every type mismatch that extraction has caught; each one was a latent bug already live on web before it was found.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Engineering Deep-Dives

Three problems worth telling, because "I used Next.js and Supabase" doesn't say much on its own.

<details>
<summary><strong>🔎 The audit that found a months-old silent failure</strong></summary>
<br>

A routine performance check noticed an idle, logged-out browser tab firing **334 Supabase requests in 25 seconds** — an infinite refetch loop caused by an unstable array reference in a `useEffect` dependency list.

Chasing that one bug backward led to something much bigger. A version mismatch between `@supabase/ssr` and `@supabase/supabase-js` had changed a generic type signature, and as a result **every Supabase query in the app was typed as returning `never[]`** — silently, for months. The compiler never complained. The workaround that appeared to fix it, `as any`, had been applied **381 times** across the codebase, and two queries were pointing at tables that didn't exist in production at all.

Fixing the root cause and removing all 381 casts restored real type safety app-wide — and incidentally surfaced a stored-XSS gap where the sanitisation library silently no-op'd during server-side rendering.

**Takeaway:** a type error you keep suppressing isn't an annoyance, it's a symptom. A dependency upgrade needs to be verified against the types it promises, not just against whether the build still passes.

</details>

<details>
<summary><strong>🎟️ The ticketing overhaul</strong></summary>
<br>

Before building the ticketing system, I worked through how Eventbrite, Peatix, Posh and Luma structure fees and payouts, and used that to pressure-test Nectie's own numbers. Two findings landed before a single ticket had sold:

- The fee schedule was **losing money on every order below a threshold price** — a plan that looked fine on paper broke at the cheap end, which is where most open-mic and small-venue tickets sit.
- Ticket prices were being stored and passed to Stripe **in the wrong unit** — a bug that, left uncaught, would have charged a customer roughly **100× the listed price** on the first live sale.

The rebuild ran to 10 phases: correct unit handling end to end, a refund flow that actually works (the original design cost the platform 100% of a refunded order because it never issued the Stripe transfer reversal), and the repositioning that became the product thesis above.

**Takeaway:** the dangerous bugs in a payments system aren't crashes — they're silent unit and logic errors that only surface as a wrong number on someone's card statement. Payment code needs adversarial review *before* launch.

</details>

<details>
<summary><strong>⚙️ A config-precedence trap across two toolchains</strong></summary>
<br>

Running the same monorepo across two different development toolchains surfaced a subtle precedence bug: one tool's instruction loader stops at the first `AGENTS.md` it finds walking up the directory tree and never evaluates the `CLAUDE.md` beside it. A three-line file written for an unrelated purpose therefore silently blanked out load-bearing build configuration — including Metro bundler resolution order — for an entire subproject.

Nothing errored. The configuration simply wasn't there, and the failure only showed up as a build behaving differently depending on which tool launched it. Fixed by declaring the instruction file list explicitly rather than relying on discovery order.

**Takeaway:** implicit "first match wins" resolution becomes a trap the moment more than one tool reads the same directory. Be explicit; don't inherit someone else's search order.

</details>

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## By the Numbers

<div align="center">

![Commits](https://img.shields.io/badge/commits-795-4A5568?style=flat-square)
![Tables](https://img.shields.io/badge/database_tables-41-4A5568?style=flat-square)
![Routes](https://img.shields.io/badge/page_routes-60+-4A5568?style=flat-square)
![Gotchas](https://img.shields.io/badge/documented_debugging_writeups-62-4A5568?style=flat-square)
![Casts](https://img.shields.io/badge/unsafe_casts_removed-381-4A5568?style=flat-square)
![Apps](https://img.shields.io/badge/apps_sharing_one_data_layer-2-4A5568?style=flat-square)

</div>

Built solo end to end — product decisions, schema design, UI, payments and infrastructure — from a blank repo in January 2026 to a live application taking real Stripe payments. A React Native (Expo) app is in active development alongside the web app, sharing one typed data layer rather than reimplementing it.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## About This Repo

> [!NOTE]
> **This repository intentionally contains no application code.** The implementation — 795 commits, 60+ routes and a 41-table schema — lives in a private repository.

What's here instead: a live, working product at [nectie.co](https://nectie.co), and a written account of what was built, how it's architected, and the specific problems solved along the way. That seemed more useful than a code dump with the interesting parts — auth, payment logic, business rules — stripped out to make it safe to publish.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Contact

<div align="center">

**Ian Lim Zhen Jun**

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Ian_Lim-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/ian-lim-1505a3205/)
[![Live Demo](https://img.shields.io/badge/🔗_nectie.co-FF6B4A?style=for-the-badge)](https://nectie.co)

</div>

<p align="right">(<a href="#readme-top">back to top</a>)</p>
