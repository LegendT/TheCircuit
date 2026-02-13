---
stepsCompleted: [1, 2, 3, 4]
inputDocuments: []
workflowType: 'research'
lastStep: 1
research_type: 'technical'
research_topic: '5-Move Judgement Circuit — Technical Architecture and Implementation'
research_goals: 'Full-stack architecture evaluation, payment/token infrastructure for pay-per-decision model, calibration engine data layer design, artefact generation and export system, authentication and user data management, tech stack selection for MVP, broad survey across all technical areas with deep dives where warranted'
user_name: 'Tone'
date: '2026-02-10'
web_research_enabled: true
source_verification: true
---

# Research Report: Technical

**Date:** 2026-02-10
**Author:** Tone
**Research Type:** Technical

---

## Research Overview

### Technical Research Scope Confirmation

**Research Topic:** 5-Move Judgement Circuit — Technical Architecture and Implementation

**Research Goals:** Full-stack architecture evaluation, payment/token infrastructure for pay-per-decision model, calibration engine data layer design, artefact generation and export system, authentication and user data management, tech stack selection for MVP, broad survey across all technical areas with deep dives where warranted

**Technical Research Areas:**

- **Platform Architecture** — Web app vs PWA vs native mobile, hosting approach, monolith vs services for MVP, rendering strategy
- **Tech Stack Selection** — Frontend framework, backend language/framework, database choices, fastest path to quality MVP
- **Payment & Token Infrastructure** — Pay-per-decision at £20–£50, payment providers, token/credit systems, pricing flexibility
- **Calibration Engine Data Layer** — Storing Calibration Capture data across sessions, schema design for feedback loop, querying patterns for calibration trends
- **Artefact Generation & Export** — Professional shareable decision records, PDF/markdown/structured output, artefact-as-marketing technical requirements
- **Auth, Privacy & Data** — User accounts, decision history, GDPR compliance, calibration data persistence vs privacy minimisation

**Research Methodology:**

- Current web data with rigorous source verification
- Multi-source validation for critical technical claims
- Confidence level framework for uncertain information
- Comprehensive technical coverage with architecture-specific insights

**Scope Confirmed:** 2026-02-10

---

## Technology Stack Analysis

### Platform Architecture Decision: Web App with PWA Enhancement

The circuit's core experience — a sequential 5-move decision process with text input, forced declarations, and artefact output — is fundamentally a **web application**. There is no technical requirement for native mobile capabilities (camera, GPS, accelerometer, local file system). The entire interaction is structured text input and structured document output.

**Recommended platform: Progressive Web App (PWA) built on Next.js.**

A PWA provides the critical advantages without the cost of native development:

- **Installable on home screen** — users can add the circuit to their phone or desktop, creating a dedicated app-like experience without app store distribution
- **Offline capability** — with service workers (via Serwist, the maintained successor to next-pwa), completed artefacts can be cached locally. The circuit itself requires server interaction (token validation, data persistence), but artefact review can work offline
- **No app store gatekeeping** — Apple and Google take 15–30% of in-app purchases. A PWA with Stripe payment bypasses this entirely, preserving the full £20–£50 token price
- **Single codebase** — one Next.js application serves desktop, tablet, and mobile. No separate iOS/Android development

Next.js 16 (current as of 2026) has built-in PWA manifest support through the App Router, and Serwist provides modern service worker tooling based on Google's Workbox. The combination is production-ready and well-documented.

**Confidence: Very High** — PWA is the correct architecture for this product class. Native mobile would add cost without adding capability.

*Sources: [Next.js PWA Guide](https://nextjs.org/docs/app/guides/progressive-web-apps), [LogRocket (Next.js 16 PWA with offline support)](https://blog.logrocket.com/nextjs-16-pwa-offline-support/), [Medium (PWA in Next.js App Router 2026)](https://medium.com/@amirjld/how-to-implement-pwa-progressive-web-app-in-next-js-app-router-2026-f25a6797d5e6)*

---

### Frontend Framework: Next.js (React)

**Recommendation: Next.js with the App Router and React Server Components.**

The 2026 framework landscape offers three credible options for a paid web app MVP:

| Framework | Strengths | Weaknesses for Circuit |
|-----------|-----------|----------------------|
| **Next.js** | Largest ecosystem, extensive hiring pool, Vercel-optimised deployment, mature Server Components, built-in API routes | Heavier bundle than alternatives, Vercel lock-in risk |
| **Remix (React Router v7)** | Excellent for form-heavy apps, web standards focus, predictable SSR | Smaller ecosystem, merged into React Router (identity confusion), fewer starter kits |
| **SvelteKit** | Smallest bundles (~50% smaller), 90/100 Lighthouse scores out of the box, fastest DX for small apps | Smallest hiring pool, fewest third-party integrations, less mature ecosystem |

**Why Next.js wins for the circuit:**

1. **Ecosystem density** — The Next.js + Supabase + Stripe combination has multiple production-grade starter kits (MakerKit, Supastarter, Nextbase, Vercel's own SaaS starter). This dramatically reduces MVP development time by providing pre-built auth flows, payment integration, and database connectivity
2. **The circuit is a form-heavy sequential experience** — while Remix excels here too, Next.js's App Router with Server Actions provides equivalent capability with a larger ecosystem
3. **Server Components** — the circuit's moves can be rendered server-side, reducing client JavaScript and improving performance on mobile devices
4. **PWA support** — built-in manifest generation and service worker integration via Serwist
5. **Hiring and maintainability** — if the product succeeds, finding developers who know Next.js is straightforward

**The multi-step wizard pattern** — the circuit's 5-move sequence maps directly to the well-established multi-step form wizard pattern in React. Current best practice (2026) uses React Hook Form for state management, Zod schemas for per-step validation, and React context to share form state across step components. The linear stepper UX pattern (users must complete each step sequentially before proceeding) maps perfectly to the circuit's constraint design.

**Confidence: High** — Next.js is the pragmatic choice for MVP speed. SvelteKit would produce a technically superior product but at the cost of ecosystem support and hiring flexibility.

*Sources: [NxCode (Framework Comparison 2026)](https://www.nxcode.io/resources/news/nextjs-vs-remix-vs-sveltekit-2025-comparison), [Nucamp (Top 10 Full Stack Frameworks 2026)](https://www.nucamp.co/blog/top-10-full-stack-frameworks-in-2026-next.js-remix-nuxt-sveltekit-and-more), [Cabot Solutions (MVP Tools 2026)](https://www.cabotsolutions.com/blog/mvp-development-tools-and-tech-stack-every-founder-should-know-in-2026), [MakerKit (Multi-Step Forms React)](https://makerkit.dev/blog/tutorials/multi-step-forms-reactjs)*

---

### Backend and Database: Supabase (PostgreSQL)

**Recommendation: Supabase as the unified backend — database, authentication, real-time, and storage in one platform.**

Supabase is an open-source Backend-as-a-Service built on PostgreSQL that provides:

- **PostgreSQL database** with full SQL flexibility, Row Level Security (RLS), and 30+ years of reliability
- **Built-in authentication** via GoTrue — email/password, OAuth (Google, GitHub, etc.), magic links, and SSO. No separate auth service needed
- **Row Level Security** — database-level access control that ensures users can only access their own data. This is critical for the circuit: a user's decision history, calibration data, and artefacts must be isolated from other users at the database level, not just the application level
- **Real-time subscriptions** — while not critical for the circuit MVP, this enables future features like live collaboration or real-time calibration dashboards
- **Edge Functions** — serverless functions for business logic that can't run client-side (token validation, webhook processing)
- **Visual schema designer** — rapid schema iteration during MVP development

**Why Supabase over raw PostgreSQL or Firebase:**

| Option | Advantage | Disadvantage for Circuit |
|--------|-----------|------------------------|
| **Raw PostgreSQL** (e.g., Neon, Railway) | Maximum flexibility, no abstraction layer | Requires building auth, RLS policies, and API layer from scratch |
| **Firebase** | Excellent real-time, mobile-first | NoSQL (poor for relational data like decision history), Google lock-in, weaker SQL querying for calibration analytics |
| **Supabase** | PostgreSQL foundation + auth + RLS + real-time, all pre-integrated | Slightly less flexible than raw Postgres for edge cases, analytics querying not optimised for large-scale aggregation |

**Calibration data schema consideration:** Supabase projects include TimescaleDB (Apache 2 Edition), a PostgreSQL extension designed for time-series data. The Calibration Capture data — three forced-choice responses per circuit completion, timestamped and linked to user accounts — is inherently time-series. TimescaleDB's hypertables (virtual tables partitioned into chunks based on time intervals) provide efficient storage and querying for calibration trend analysis without requiring a separate analytics database.

**GDPR compliance:** Supabase is GDPR compliant with EU data centre regions available (Frankfurt). It provides SOC 2 certification, encryption at rest and in transit, and audit logs. Critically, RLS ensures data isolation at the database level — even if application code has a bug, PostgreSQL policies prevent cross-user data access. However, GDPR compliance requires application-level implementation too: user consent flows, data deletion workflows (right to erasure), and data export capability.

**Confidence: High** — Supabase is the strongest option for an MVP that needs auth, relational data, and time-series calibration tracking in a single platform.

*Sources: [MakerKit (Best Database for Startups 2026)](https://makerkit.dev/blog/tutorials/best-database-software-startups), [Hackceleration (Supabase Review 2026)](https://hackceleration.com/supabase-review/), [Supabase (Row Level Security)](https://supabase.com/features/row-level-security), [Supabase (GDPR Compliance)](https://supabase.store/pages/gdpr-compliance), [Supabase (Security)](https://supabase.com/security), [Supabase (TimescaleDB)](https://supabase.com/docs/guides/database/extensions/timescaledb), [Bootstrapped (User Activity Tracking)](https://bootstrapped.app/guide/how-to-implement-user-activity-tracking-in-supabase)*

---

### Payment Infrastructure: Stripe with Credit/Token System

**Recommendation: Stripe Checkout Sessions with a server-side credit system.**

The circuit's pricing model — pay per consequential decision at £20–£50 — maps to an established pattern in web applications: the **credit/token purchase system**. The user buys credits (tokens) via Stripe, and each circuit completion consumes one credit.

**Implementation architecture:**

1. **Credit purchase flow:**
   - User clicks "Buy Token" (or "Buy 3 Tokens", "Buy 5 Tokens" for volume pricing)
   - Server creates a Stripe Checkout Session with the `userId` stored in `client_reference_id` and credit quantity in metadata
   - User is redirected to Stripe's hosted checkout page (PCI compliance handled by Stripe — no card data touches our servers)
   - On successful payment, Stripe fires a `checkout.session.completed` webhook
   - Webhook handler adds credits to the user's account in Supabase

2. **Credit consumption flow:**
   - User initiates a circuit → server checks credit balance → deducts one credit → circuit begins
   - If credit balance is zero → user is prompted to purchase
   - Eligibility failures (the free gate) do not consume credits — this is application logic, not payment logic

3. **Why Stripe over alternatives:**

| Provider | Advantage | Disadvantage for Circuit |
|----------|-----------|------------------------|
| **Stripe** | Best developer experience, hosted checkout (PCI compliant), excellent webhook system, global coverage, well-documented credit system patterns | 2.9% + 30p per transaction (significant on a £20 token) |
| **PayPal** | Better micropayment rates (under $10) | Worse developer experience, less reliable webhooks, unprofessional checkout flow |
| **Paddle/Lemon Squeezy** | Handle VAT/tax as Merchant of Record | Less flexibility for credit systems, smaller ecosystem |

**Fee consideration:** At £20 per token, Stripe's fee is approximately £0.88 (4.4%). At £50, it's approximately £1.75 (3.5%). Volume pricing (buy 3 tokens for £50) improves the effective fee rate. This is acceptable for MVP — optimisation can come later via Stripe's volume discounting or alternative providers.

**The credit system pattern is well-documented** in the Next.js + Stripe ecosystem, with multiple tutorials and starter kits providing reference implementations. MakerKit 1.1.0 (released February 2026) includes multi-line item checkout and tiered pricing out of the box.

**Confidence: Very High** — Stripe + credit system is the established pattern for this pricing model. No reason to deviate.

*Sources: [Stripe (Checkout Sessions API)](https://docs.stripe.com/payments/quickstart-checkout-sessions), [Stripe (Micropayments Guide)](https://stripe.com/resources/more/micropayments-101-a-guide-to-get-businesses-started), [Medium (NextJS Stripe Credit System)](https://medium.com/@jsteinb/nextjs-using-stripe-to-build-a-credit-system-for-your-saas-app-3562e1608c25), [Tiger Abrodi (Credits System with Stripe)](https://tigerabrodi.blog/implement-a-credits-system-with-stripe-my-messy-notes), [Stripe (Payment Links)](https://docs.stripe.com/payment-links)*

---

### Artefact Generation: React-PDF with Markdown Export

**Recommendation: Dual-format artefact output — structured web view (default) with PDF and Markdown export options.**

The artefact is the circuit's most visible output and its primary marketing vehicle ("artefact as marketing"). It must be:

- **Professional in appearance** — clean, structured, immediately credible
- **Shareable** — exportable as PDF for email/Slack/print, and as Markdown for technical users
- **Consistent** — every artefact follows the same structure regardless of the decision content
- **Lightweight to generate** — no server-side rendering bottleneck

**Technical approach:**

1. **Primary view: Structured web page** — the artefact is stored as structured data (JSON) in Supabase and rendered as a React component. This is the default view within the app — fast, responsive, and styled with the circuit's design language

2. **PDF export: React-PDF** — React-PDF is an open-source library built on PDFKit that allows PDF creation using React's declarative syntax. The artefact's structured data maps directly to React-PDF components. PDF generation happens client-side, avoiding server load

3. **Markdown export** — a simple transformation from structured JSON to Markdown text. Useful for users who want to paste decisions into Notion, Obsidian, or other knowledge management tools

4. **Share link** — each artefact gets a unique URL (with optional public/private toggle). This enables the "artefact as marketing" strategy: users share their decision records, recipients see a professional output with circuit branding

**Artefact structure (data model):**
```
{
  id: uuid,
  user_id: uuid,
  created_at: timestamp,
  orientation: { statement: string, context: string },
  eligibility: { criteria: string[], passed: boolean },
  declaration: { decision: string, alternatives: string[] },
  sufficiency: { evidence: string, threshold_met: boolean },
  artefact_summary: string,
  calibration_capture: {
    behavioural_interruption: enum,
    sufficiency_boundary: enum,
    cost_acceptance: enum
  }
}
```

**Confidence: High** — React-PDF is mature and well-maintained. The dual-format approach (web + PDF + Markdown) covers all sharing scenarios without over-engineering.

*Sources: [React-PDF](https://react-pdf.org/), [LogRocket (Generating PDFs in React)](https://blog.logrocket.com/generating-pdfs-react/), [GitHub (React-PDF)](https://github.com/diegomura/react-pdf), [PDForge (React-PDF Reports)](https://pdforge.com/blog/how-to-generate-pdf-reports-from-html-with-react-pdf)*

---

### Hosting and Deployment: Vercel (Primary) with Supabase Cloud

**Recommendation: Vercel for the Next.js application, Supabase Cloud for the database and backend services.**

| Component | Platform | Cost (MVP) | Rationale |
|-----------|----------|-----------|-----------|
| **Next.js app** | Vercel Pro | ~£20/month | Native Next.js deployment, edge functions, automatic preview deployments, excellent DX |
| **Database + Auth** | Supabase Pro | ~£25/month | PostgreSQL, auth, RLS, edge functions, EU data centre |
| **Payments** | Stripe | 2.9% + 30p per transaction | Checkout sessions, webhooks, credit system |
| **Domain + DNS** | Cloudflare (free) | £0 | DNS, DDoS protection, SSL |
| **Email** | Resend or Supabase built-in | £0–£20/month | Transactional emails (purchase confirmation, artefact sharing) |

**Total MVP infrastructure cost: ~£45–£65/month** plus Stripe transaction fees.

This is deliberately lean. The circuit's traffic pattern at launch will be low-volume, high-value (each user completes a circuit infrequently but pays £20–£50 per use). Vercel's Pro plan handles this comfortably. If the product scales beyond Vercel's pricing comfort zone, the Next.js application can be migrated to Cloudflare Pages (unlimited free bandwidth) or Railway (container-based, more predictable scaling costs) without rewriting.

**Confidence: High** — Vercel + Supabase is the most common production deployment pattern for Next.js SaaS applications in 2026. Well-documented, well-supported, and cost-effective at MVP scale.

*Sources: [Nucamp (Deploying Full Stack Apps 2026)](https://www.nucamp.co/blog/deploying-full-stack-apps-in-2026-vercel-netlify-railway-and-cloud-options), [MakerKit (Best Next.js Hosting 2026)](https://makerkit.dev/blog/tutorials/best-hosting-nextjs), [Codegiant (Cloudflare vs Vercel)](https://blog.codegiant.io/p/cloudflare-vs-vercel), [DigitalOcean (Vercel Alternatives 2026)](https://www.digitalocean.com/resources/articles/vercel-alternatives)*

---

### SaaS Starter Kit: Accelerating MVP Development

**Key finding: The Next.js + Supabase + Stripe stack has multiple production-grade starter kits that can reduce MVP development time by weeks.**

| Starter Kit | Features | Pricing | Best For |
|-------------|----------|---------|----------|
| **MakerKit** | Auth, Stripe billing (multi-line item, tiered pricing as of Feb 2026), Supabase integration, admin dashboard | From $199 one-time | Most actively maintained, best Stripe integration |
| **Supastarter** | Auth, payments, i18n, email, admin panel, Prisma ORM | From $299 one-time | Production-grade, extensive documentation |
| **Nextbase** | Auth, Stripe, Supabase, shadcn/ui | From $149 one-time | Clean starting point, lower cost |
| **Vercel SaaS Starter** | Auth, PostgreSQL with Drizzle ORM, Stripe, landing page | Free (open-source) | Zero cost, official Vercel template |

**Recommendation for the circuit:** Start with **MakerKit** or the **Vercel SaaS Starter** as the foundation, then build the circuit-specific features (5-move sequence, calibration capture, artefact generation) on top. The starter kit provides the "undifferentiated heavy lifting" — auth flows, payment integration, account management, email — so development effort can focus entirely on the circuit experience itself.

**Confidence: High** — Using a starter kit is standard practice for SaaS MVPs in 2026. The risk of "framework debt" is low because the underlying technologies (Next.js, Supabase, Stripe) are the same regardless of starter kit choice.

*Sources: [GitHub (Next-Supabase-Stripe Starter)](https://github.com/KolbySisk/next-supabase-stripe-starter), [Vercel (SaaS Starter Kit)](https://vercel.com/templates/next.js/stripe-supabase-saas-starter-kit), [MakerKit (Next.js Supabase Boilerplate)](https://makerkit.dev/next-supabase), [Supastarter](https://supastarter.dev/nextjs-supabase-boilerplate), [SaaS Starters (All Next.js Boilerplates)](https://saasstarters.com/stack/next/all/)*

---

### Technology Stack Summary

| Layer | Choice | Rationale |
|-------|--------|-----------|
| **Platform** | PWA (Progressive Web App) | No native requirements, avoids app store fees, single codebase |
| **Frontend** | Next.js (App Router, React Server Components) | Largest ecosystem, best starter kit support, PWA-ready |
| **UI** | shadcn/ui + Tailwind CSS | Consistent with starter kits, accessible, customisable |
| **Backend** | Supabase Edge Functions + Next.js API Routes | Serverless, scales to zero, no infrastructure management |
| **Database** | Supabase (PostgreSQL) with TimescaleDB extension | Relational data + time-series calibration tracking in one database |
| **Auth** | Supabase Auth (GoTrue) | Built-in, RLS-integrated, OAuth + email/password |
| **Payments** | Stripe (Checkout Sessions + webhooks) | Credit/token system, PCI compliant, best DX |
| **Artefact Export** | React-PDF (client-side) + Markdown | Professional PDF output, lightweight, no server dependency |
| **Hosting** | Vercel (app) + Supabase Cloud (backend) | Native Next.js deployment, EU data centre option |
| **DNS/CDN** | Cloudflare (free tier) | DDoS protection, SSL, global CDN |
| **Email** | Resend or Supabase built-in | Transactional emails for purchases and sharing |
| **Starter Kit** | MakerKit or Vercel SaaS Starter | Pre-built auth, payments, account management |

**Estimated MVP infrastructure cost:** £45–£65/month + Stripe transaction fees
**Estimated development acceleration from starter kit:** 2–4 weeks saved on auth, payments, and account management

---

## Integration Patterns Analysis

The circuit has six distinct integration boundaries — points where different systems must communicate reliably. Each integration has specific patterns, failure modes, and security requirements.

### Integration 1: Next.js ↔ Supabase (Data Layer)

**Pattern: Server Actions with Supabase client, RLS-enforced queries.**

The primary data flow in the circuit is between the Next.js frontend and Supabase's PostgreSQL database. Current best practice (2026) uses **Next.js Server Actions** — server-side functions called directly from React components — to handle all database mutations.

**Key implementation patterns:**

1. **Separate client utilities** — Supabase runs in two contexts (browser and server), requiring separate client instances. The standard pattern is a `/utils/supabase/` folder with `client.ts` (browser) and `server.ts` (server) modules. Server Actions use the server client; client-side reads use the browser client

2. **RLS for reads, Server Actions for writes** — a production-proven pattern separates concerns: client-side queries use the browser Supabase client with RLS enforcing data isolation, while all write operations (creating circuits, saving moves, recording calibration captures) route through Server Actions using the server client. This prevents direct database mutations from the browser

3. **Cookie-based session management** — when calling Supabase from Server Actions, `cookies()` must be called before any Supabase calls to opt fetch calls out of Next.js's caching. This ensures authenticated data fetches return the correct user's data

4. **Serialisation constraint** — Server Action arguments and return values must be serialisable (no functions, classes, or circular references). The circuit's data model (structured JSON for each move) is naturally serialisable, so this is not a concern

**Critical security consideration:** Always use `supabase.auth.getUser()` rather than `supabase.auth.getSession()` on the server, because session data comes from cookies which can be spoofed. `getUser()` makes a round-trip to Supabase's auth server to verify the JWT.

**Confidence: Very High** — This is the standard integration pattern for all Next.js + Supabase applications. Extensively documented and battle-tested.

*Sources: [Supabase (Next.js Tutorial)](https://supabase.com/docs/guides/getting-started/tutorials/with-nextjs), [Supabase (Server-Side Auth for Next.js)](https://supabase.com/docs/guides/auth/server-side/nextjs), [MakerKit (Next.js Server Actions Guide 2026)](https://makerkit.dev/blog/tutorials/nextjs-server-actions), [CatJam (Next.js + Supabase in Production)](https://catjam.fi/articles/next-supabase-what-do-differently)*

---

### Integration 2: Stripe ↔ Supabase (Payment Processing)

**Pattern: Stripe Checkout Sessions → Webhooks → Supabase credit ledger.**

The payment integration is the circuit's most critical system-to-system boundary. Failure here means either lost revenue (payment captured but credits not granted) or unearned access (credits granted but payment not captured).

**Implementation architecture:**

```
User clicks "Buy Token"
    → Next.js API route creates Stripe Checkout Session
    → User redirected to Stripe hosted checkout
    → User pays
    → Stripe fires checkout.session.completed webhook
    → Next.js webhook handler:
        1. Verifies Stripe signature (within 5-minute window)
        2. Checks idempotency (has this event.id been processed?)
        3. Extracts userId and credit quantity from session metadata
        4. Adds credits to user's account in Supabase
        5. Stores event.id to prevent duplicate processing
    → User redirected to success page with updated credit balance
```

**Critical webhook best practices:**

- **Idempotency is non-negotiable** — Stripe may send the same event multiple times. The webhook handler MUST check if `event.id` has already been processed before adding credits. Store processed event IDs in a Supabase table, not in memory (memory is lost on serverless function cold starts)
- **Signature verification within 5 minutes** — Stripe timestamps webhook payloads and rejects verification attempts after 5 minutes. The webhook handler must verify immediately, then process
- **Retry schedule** — Stripe retries failed deliveries: immediately, 5 min, 30 min, 2 hours, 5 hours, 10 hours, then every 12 hours for up to 3 days. The handler must be resilient to receiving events out of order
- **Background processing** — for complex post-payment logic (sending confirmation emails, updating analytics), move processing to background jobs after acknowledging the webhook with a 200 response

**Credit consumption atomicity:** When a user starts a circuit, the credit deduction must be atomic — check balance and deduct in a single database transaction to prevent race conditions (e.g., user opening two browser tabs simultaneously).

**Confidence: Very High** — Stripe webhook integration is the most documented payment pattern in web development. The credit system pattern specifically has multiple reference implementations in the Next.js ecosystem.

*Sources: [Stripe (Webhooks)](https://docs.stripe.com/webhooks), [Stigg (Stripe Webhook Best Practices)](https://www.stigg.io/blog-posts/best-practices-i-wish-we-knew-when-integrating-stripe-webhooks), [Medium (Handling Payment Webhooks Reliably)](https://medium.com/@sohail_saifii/handling-payment-webhooks-reliably-idempotency-retries-validation-69b762720bf5), [Stripe (Idempotent Requests)](https://docs.stripe.com/api/idempotent_requests), [MagicBell (Stripe Webhooks Guide)](https://www.magicbell.com/blog/stripe-webhooks-guide)*

---

### Integration 3: Row Level Security (Data Isolation)

**Pattern: PostgreSQL RLS policies enforcing per-user data boundaries at the database level.**

Data isolation is architecturally critical for the circuit. A user's decision history, calibration captures, and artefacts are deeply personal professional data. Leaking one user's decisions to another would be a trust-destroying event.

**RLS policy design for the circuit:**

| Table | SELECT Policy | INSERT Policy | UPDATE Policy | DELETE Policy |
|-------|--------------|---------------|---------------|---------------|
| `circuits` | `auth.uid() = user_id` | `auth.uid() = user_id` | `auth.uid() = user_id` | `auth.uid() = user_id` |
| `circuit_moves` | `auth.uid() = user_id` | `auth.uid() = user_id` | `auth.uid() = user_id` | None (moves are immutable) |
| `calibration_captures` | `auth.uid() = user_id` | `auth.uid() = user_id` | None (captures are immutable) | None (captures are immutable) |
| `artefacts` | `auth.uid() = user_id OR is_public = true` | `auth.uid() = user_id` | `auth.uid() = user_id` | `auth.uid() = user_id` |
| `credits` | `auth.uid() = user_id` | Service role only (webhook) | Service role only (webhook + circuit start) | None |
| `webhook_events` | None | Service role only | None | None |

**Key design decisions:**

1. **Immutable moves and calibration captures** — once a circuit move is recorded or a calibration capture is submitted, it cannot be edited or deleted. This preserves the integrity of the calibration dataset. RLS enforces this by having no UPDATE or DELETE policies on these tables

2. **Public artefact sharing** — artefacts have a dual access pattern: the owner can always access them, AND anyone can access artefacts where `is_public = true`. This enables the shareable URL feature without requiring anonymous authentication

3. **Credit ledger is service-role only for writes** — credits are added only by the Stripe webhook handler (using the service role key, which bypasses RLS) and deducted only by the circuit initiation Server Action (also service role). Users can read their own credit balance but never modify it directly

4. **January 2026 cautionary tale** — the Moltbook data breach demonstrated what happens when RLS is disabled: 1.5 million API keys and 35,000+ email addresses exposed. RLS must be enabled on ALL tables from day one, with explicit policies for every access pattern

**Confidence: Very High** — RLS is a mature PostgreSQL feature with extensive Supabase documentation and real-world production patterns.

*Sources: [Supabase (Row Level Security)](https://supabase.com/docs/guides/database/postgres/row-level-security), [VibeAppScanner (RLS Complete Guide 2026)](https://vibeappscanner.com/supabase-row-level-security), [SupaExplorer (10 Real-World RLS Patterns)](https://supaexplorer.com/dev-notes/10-real-world-rls-patterns-for-supabase-with-policy-snippets.html), [Bastion (Moltbook Security Lessons)](https://bastion.tech/blog/moltbook-security-lessons-ai-agents), [Supabase (Securing Your API)](https://supabase.com/docs/guides/api/securing-your-api)*

---

### Integration 4: Circuit State Machine (Workflow Orchestration)

**Pattern: Finite state machine using useReducer for the 5-move sequential workflow.**

The circuit's 5-move sequence is a classic finite state machine: it has defined states, defined transitions between states, and rules preventing invalid transitions (you cannot skip to Move 4 without completing Move 3).

**State machine design:**

```
States: idle → orientation → eligibility → declaration → sufficiency → artefact → calibration → complete

Transitions:
  idle → orientation:    [START_CIRCUIT] (requires credit > 0)
  orientation → eligibility:  [SUBMIT_ORIENTATION] (requires valid input)
  eligibility → declaration:  [PASS_ELIGIBILITY] (requires criteria met)
  eligibility → idle:         [FAIL_ELIGIBILITY] (free exit, no credit consumed)
  declaration → sufficiency:  [SUBMIT_DECLARATION] (requires decision + alternatives)
  sufficiency → artefact:     [DECLARE_SUFFICIENT] (requires explicit declaration)
  artefact → calibration:     [GENERATE_ARTEFACT] (requires summary written)
  calibration → complete:     [SUBMIT_CALIBRATION] (requires all 3 forced-choice answers)
```

**Implementation approach: `useReducer` over XState.**

| Option | Advantage | Disadvantage for Circuit |
|--------|-----------|------------------------|
| **`useReducer`** | Built into React, zero dependencies, simple for linear flows, easy to understand and debug | No built-in side effect management, no visual state chart tooling |
| **XState** | Full state machine library with side effects, guards, parallel states, visual debugger | Significant learning curve, overkill for a linear 7-state machine, adds dependency |

The circuit's state machine is **linear** — there are no parallel states, no complex branching (the only branch is eligibility pass/fail), and no re-entry to previous states. `useReducer` handles this cleanly without the overhead of XState. The reducer function enforces valid transitions and prevents impossible states.

**Server-side state persistence:** Each move's completion is saved to Supabase via Server Action before the state transitions to the next move. If the user closes their browser mid-circuit, the state can be restored from the database on their next visit. The reducer's initial state is hydrated from the database, not from a default.

**Confidence: High** — Linear multi-step workflows are the canonical use case for `useReducer` as a finite state machine. XState would be warranted if the circuit added complex branching or parallel workflows in the future.

*Sources: [Kyle Shevlin (useReducer as FSM)](https://kyleshevlin.com/how-to-use-usereducer-as-a-finite-state-machine/), [Medium (State Machines in React)](https://medium.com/@ignatovich.dm/state-machines-in-react-advanced-state-management-beyond-redux-33ea20e59b62), [First AML (Multi-Step Forms with State Machines)](https://firstaml.dev/blog/2ldc7qgkjwbg7h2bm3xryc3so6eqb1), [GitHub (XState)](https://github.com/statelyai/xstate)*

---

### Integration 5: Artefact Sharing (Public URLs)

**Pattern: UUID-based public URLs with RLS-controlled anonymous access.**

The "artefact as marketing" strategy requires that completed decision records can be shared via a unique URL that anyone can view — without requiring the recipient to create an account.

**Implementation approach:**

1. Each artefact has a UUID (`id`) and a boolean `is_public` field (default: `false`)
2. When the user toggles "Share this artefact," `is_public` is set to `true`
3. The share URL is: `https://circuit.app/artefact/{uuid}`
4. The artefact page uses the Supabase anon key (public client) to query the `artefacts` table
5. The RLS policy on `artefacts` allows SELECT where `auth.uid() = user_id OR is_public = true`
6. No authentication required to view a public artefact — the anon key combined with the RLS policy handles access control

**Security considerations:**

- UUIDs are unguessable (128-bit random), so a public URL does not create an enumeration risk
- The artefact page displays read-only content — no mutations are possible via the public view
- The owner can revoke sharing at any time by setting `is_public = false`
- No user data beyond the artefact content is exposed (no email, no calibration data, no credit balance)

**Confidence: High** — This is a standard pattern for shareable content in Supabase applications. The RLS policy is simple and well-understood.

*Sources: [Supabase (Row Level Security)](https://supabase.com/docs/guides/database/postgres/row-level-security), [Supabase (Anonymous Sign-Ins)](https://supabase.com/docs/guides/auth/auth-anonymous), [Supabase (Securing Your API)](https://supabase.com/docs/guides/api/securing-your-api)*

---

### Integration 6: Transactional Email (Resend)

**Pattern: Resend API with React Email templates, triggered by Supabase Edge Functions or Server Actions.**

The circuit needs transactional emails for three scenarios:

1. **Purchase confirmation** — "Your token has been added. You have X credits remaining."
2. **Artefact sharing notification** — "Tone shared a decision record with you: [link]"
3. **Auth emails** — password reset, email verification (handled by Supabase Auth + Resend SMTP)

**Why Resend:**

- First-class Supabase integration — connect Resend to Supabase to automatically configure custom SMTP for auth emails
- React Email — compose email templates using React components instead of raw HTML. The artefact sharing email can reuse the same React components that render the artefact in the app
- Simple API — a single `resend.emails.send()` call with React Email templates
- Generous free tier (100 emails/day) — more than sufficient for MVP
- All major SaaS starter kits (MakerKit, Supastarter, Nextbase) include Resend integration

**Confidence: High** — Resend is the default transactional email choice for Supabase applications in 2026. The integration is well-documented and pre-built in starter kits.

*Sources: [Supabase (Resend Integration)](https://supabase.com/partners/integrations/resend), [Resend (Supabase Integration)](https://resend.com/supabase), [Supabase (Custom Auth Emails with React Email)](https://supabase.com/docs/guides/functions/examples/auth-send-email-hook-react-email-resend), [MakerKit (Email Configuration)](https://makerkit.dev/docs/next-supabase-turbo/emails/email-configuration)*

---

### Integration Architecture Summary

```
┌─────────────────────────────────────────────────────┐
│                    USER (Browser)                     │
│  ┌─────────────┐  ┌──────────┐  ┌────────────────┐  │
│  │ Circuit UI   │  │ Auth UI  │  │ Payment UI     │  │
│  │ (5-move FSM) │  │          │  │ (Buy Tokens)   │  │
│  └──────┬───────┘  └────┬─────┘  └───────┬────────┘  │
└─────────┼───────────────┼────────────────┼───────────┘
          │               │                │
    Server Actions   Supabase Auth    Stripe Checkout
          │               │                │
┌─────────┼───────────────┼────────────────┼───────────┐
│         ▼               ▼                ▼           │
│  ┌─────────────────────────────────────────────┐     │
│  │              Next.js Server                  │     │
│  │  ┌──────────┐  ┌──────────┐  ┌───────────┐ │     │
│  │  │ Server   │  │ API      │  │ Webhook   │ │     │
│  │  │ Actions  │  │ Routes   │  │ Handler   │ │     │
│  │  └────┬─────┘  └────┬─────┘  └─────┬─────┘ │     │
│  └───────┼──────────────┼──────────────┼───────┘     │
│          │              │              │             │
│          ▼              ▼              ▼             │
│  ┌─────────────────────────────────────────────┐     │
│  │           Supabase (PostgreSQL)              │     │
│  │  ┌──────┐ ┌────────┐ ┌──────┐ ┌─────────┐  │     │
│  │  │Circuits│ │Artefacts│ │Credits│ │Calibration│ │     │
│  │  └──────┘ └────────┘ └──────┘ └─────────┘  │     │
│  │         Row Level Security (all tables)      │     │
│  └─────────────────────────────────────────────┘     │
│                                                      │
│  ┌────────────┐  ┌────────────┐                      │
│  │   Resend    │  │ Cloudflare  │                     │
│  │ (Email)     │  │ (DNS/CDN)   │                     │
│  └────────────┘  └────────────┘                      │
│                                                      │
│              VERCEL + SUPABASE CLOUD                 │
└──────────────────────────────────────────────────────┘
```

| Integration | Pattern | Complexity | Risk Level |
|-------------|---------|-----------|------------|
| Next.js ↔ Supabase | Server Actions + RLS | Low | Low — well-documented standard pattern |
| Stripe ↔ Supabase | Webhooks + idempotency | Medium | Medium — webhook reliability requires careful implementation |
| Data Isolation (RLS) | Per-table PostgreSQL policies | Low | Low — but must be enabled on ALL tables from day one |
| Circuit State Machine | `useReducer` FSM + server persistence | Medium | Low — linear state machine, well-understood pattern |
| Artefact Sharing | UUID URLs + RLS public flag | Low | Low — simple read-only pattern |
| Transactional Email | Resend API + React Email | Low | Low — pre-built in starter kits |

**The circuit's integration architecture is deliberately simple.** There are no microservices, no message queues, no event buses, no service mesh. Every integration is a direct connection between two well-documented systems. This is appropriate for an MVP — complexity can be added when scale demands it, not before.

---

## Architectural Patterns and Design

The circuit's architecture must serve a specific product shape: a sequential, high-stakes workflow that captures structured data, enforces behavioural constraints, and produces professional artefacts. Every architectural decision below is evaluated against this product reality — not against abstract "best practices" that assume different traffic patterns or user behaviour.

### System Architecture Pattern: Modular Monolith on Serverless

**Pattern: Next.js App Router as a modular monolith deployed to Vercel's serverless infrastructure.**

The circuit does not need microservices. It has a single domain (decision-making), a single user type (the decision-maker), and a single core workflow (the 5-move sequence). Splitting this into separate services would add network latency, deployment complexity, and operational overhead with zero architectural benefit.

**Why modular monolith over microservices for the circuit:**

| Consideration | Modular Monolith | Microservices |
|---------------|------------------|---------------|
| **Development speed** | Single codebase, single deployment, single debugging context | Multiple repos, independent deploys, distributed tracing required |
| **Latency** | Function calls between modules (nanoseconds) | Network calls between services (milliseconds) |
| **Consistency** | Single database transaction for credit deduction + circuit creation | Distributed transaction coordination (sagas, eventual consistency) |
| **Team size** | Ideal for 1–3 developers | Justified when teams exceed 8–10 developers working on independent features |
| **Operational cost** | One Vercel project, one Supabase instance | Multiple compute instances, service discovery, API gateway |

**Module boundaries within the monolith:**

The Next.js App Router's directory structure naturally enforces module boundaries:

```
app/
  (auth)/          → Authentication flows (login, signup, password reset)
  (dashboard)/     → User dashboard (credit balance, circuit history, settings)
  (circuit)/       → The 5-move workflow (orientation → calibration)
  (artefact)/      → Artefact viewing, sharing, and export
  api/
    webhooks/      → Stripe webhook handler
```

Each route group `(group)` acts as a module with its own layouts, loading states, and error boundaries. Shared logic lives in `/lib` (Supabase client utilities, Stripe helpers, Zod schemas) and `/components` (UI components). This achieves the separation-of-concerns benefits of microservices without the operational overhead.

**Vercel's Fluid Compute model** (2025–2026) further validates this approach. Unlike traditional serverless where each function invocation is isolated, Fluid Compute keeps function instances warm between requests, reduces cold starts through bytecode caching (27% faster cold starts), and allows concurrent request handling within a single instance. For the circuit's traffic pattern — low-volume, high-value, with bursty usage — this means near-instant response times without paying for always-on compute.

**Confidence: Very High** — A modular monolith is the correct architecture for a single-product MVP with a small team. Microservices would be premature optimisation.

*Sources: [Vercel (Fluid Compute)](https://vercel.com/blog/introducing-fluid-compute), [Vercel (Serverless Functions)](https://vercel.com/docs/functions), [Next.js (App Router Project Structure)](https://nextjs.org/docs/getting-started/project-structure)*

---

### Database Architecture: PostgreSQL Schema Design

**Pattern: Normalised relational schema with GENERATED AS IDENTITY keys, immutable audit tables, and CASCADE delete chains for GDPR compliance.**

The circuit's data model is inherently relational: users have credits, credits enable circuits, circuits contain moves, circuits produce artefacts, and artefacts have calibration captures. Each entity has clear foreign key relationships.

**Schema design principles for the circuit:**

1. **GENERATED AS IDENTITY over SERIAL** — PostgreSQL's modern identity columns (`GENERATED ALWAYS AS IDENTITY`) replace the legacy `SERIAL` type. Identity columns prevent accidental manual ID insertion, support sequence management at the column level, and are SQL-standard compliant. All circuit tables should use this pattern

2. **Immutable workflow tables** — `circuit_moves` and `calibration_captures` are append-only. Once a move is recorded, it is never updated or deleted (except via GDPR right-to-erasure CASCADE). This preserves the integrity of the calibration dataset and creates a reliable audit trail

3. **Timestamped everything** — every table includes `created_at` (defaulting to `now()`) and, where applicable, `updated_at` (via trigger). Time-series queries for calibration trend analysis depend on accurate timestamps

4. **Enum types for constrained values** — the calibration capture's three forced-choice responses use PostgreSQL enum types, preventing invalid data at the database level rather than relying on application validation alone

**Proposed schema structure:**

```sql
-- Users (managed by Supabase Auth, extended with profile)
CREATE TABLE public.profiles (
  id UUID REFERENCES auth.users PRIMARY KEY,
  display_name TEXT,
  created_at TIMESTAMPTZ DEFAULT now()
);

-- Credit ledger (service-role writes only)
CREATE TABLE public.credits (
  id BIGINT GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
  user_id UUID REFERENCES auth.users NOT NULL,
  amount INTEGER NOT NULL,  -- positive = purchase, negative = consumption
  reason TEXT NOT NULL,      -- 'purchase', 'circuit_start', 'refund'
  stripe_session_id TEXT,    -- null for consumption entries
  created_at TIMESTAMPTZ DEFAULT now()
);

-- Circuits (the 5-move workflow instance)
CREATE TABLE public.circuits (
  id UUID DEFAULT gen_random_uuid() PRIMARY KEY,
  user_id UUID REFERENCES auth.users NOT NULL,
  status TEXT NOT NULL DEFAULT 'orientation',
  started_at TIMESTAMPTZ DEFAULT now(),
  completed_at TIMESTAMPTZ,
  current_step INTEGER DEFAULT 1
);

-- Individual moves within a circuit (immutable)
CREATE TABLE public.circuit_moves (
  id BIGINT GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
  circuit_id UUID REFERENCES public.circuits ON DELETE CASCADE NOT NULL,
  user_id UUID REFERENCES auth.users NOT NULL,
  move_type TEXT NOT NULL,  -- 'orientation', 'eligibility', etc.
  move_data JSONB NOT NULL, -- structured data for each move type
  created_at TIMESTAMPTZ DEFAULT now()
);

-- Calibration captures (immutable)
CREATE TABLE public.calibration_captures (
  id BIGINT GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
  circuit_id UUID REFERENCES public.circuits ON DELETE CASCADE UNIQUE NOT NULL,
  user_id UUID REFERENCES auth.users NOT NULL,
  behavioural_interruption TEXT NOT NULL,
  sufficiency_boundary TEXT NOT NULL,
  cost_acceptance TEXT NOT NULL,
  created_at TIMESTAMPTZ DEFAULT now()
);

-- Artefacts (shareable decision records)
CREATE TABLE public.artefacts (
  id UUID DEFAULT gen_random_uuid() PRIMARY KEY,
  circuit_id UUID REFERENCES public.circuits ON DELETE CASCADE UNIQUE NOT NULL,
  user_id UUID REFERENCES auth.users NOT NULL,
  summary TEXT NOT NULL,
  is_public BOOLEAN DEFAULT false,
  created_at TIMESTAMPTZ DEFAULT now()
);

-- Webhook event deduplication
CREATE TABLE public.webhook_events (
  id TEXT PRIMARY KEY,  -- Stripe event ID
  processed_at TIMESTAMPTZ DEFAULT now()
);
```

**Key design decisions:**

- **Credit ledger pattern** — credits are stored as a ledger (debit/credit entries), not a running balance. The current balance is `SUM(amount) WHERE user_id = ?`. This provides a complete audit trail and makes reconciliation with Stripe straightforward
- **JSONB for move data** — each move type has different data fields (orientation has statement + context, eligibility has criteria + passed, etc.). JSONB stores this flexibly without requiring a separate table per move type, whilst still being indexable and queryable
- **CASCADE deletes** — when a user exercises their GDPR right to erasure, deleting from `auth.users` cascades through `profiles → circuits → circuit_moves → calibration_captures → artefacts`. One DELETE operation removes all user data
- **UNIQUE constraints** — each circuit has exactly one calibration capture and one artefact (`UNIQUE` on `circuit_id`). This enforces the one-circuit-one-artefact invariant at the database level

**Zero-downtime migrations:** For schema changes after launch, pgroll (open-source, backed by Xata) provides expand-and-contract migrations that allow the old and new schema versions to coexist during deployment. This prevents downtime during schema updates — critical once real users have paid credits at stake.

**Confidence: High** — The schema follows established PostgreSQL patterns for workflow tracking applications. The ledger pattern for credits is used by every major credit/token system.

*Sources: [PostgreSQL (GENERATED AS IDENTITY)](https://www.postgresql.org/docs/current/sql-createtable.html), [Supabase (Database Schema)](https://supabase.com/docs/guides/database/tables), [GitHub (pgroll)](https://github.com/xataio/pgroll), [Supabase (Migrations)](https://supabase.com/docs/guides/deployment/database-migrations)*

---

### Scalability and Performance Patterns

**Pattern: Serverless-native architecture optimised for low-volume, high-value traffic with graceful scaling.**

The circuit's traffic pattern is unusual and favourable: each user makes a consequential decision infrequently (perhaps weekly or monthly), pays £20–£50 per use, and spends 10–30 minutes completing the circuit. This is the opposite of a social media feed (high-volume, low-value, millisecond attention spans).

**What this means for architecture:**

1. **No scaling bottleneck at MVP** — even 1,000 active users completing one circuit per week generates only ~143 requests/day for circuit completions (plus page loads, auth checks, etc.). Vercel's free tier handles 100,000 function invocations per month; the Pro tier handles millions

2. **Cold starts are acceptable** — the circuit's 10–30 minute session means a 200ms cold start on the first request is imperceptible. Vercel's bytecode caching (introduced 2025) reduces subsequent cold starts by 27%, and Fluid Compute keeps instances warm during active sessions

3. **Database connection pooling is essential** — serverless functions create a new database connection per invocation. Without connection pooling, 50 concurrent users could exhaust PostgreSQL's default 100-connection limit. Supabase includes PgBouncer (connection pooler) by default, configured for transaction-level pooling. Use the pooled connection string in Server Actions and API routes

4. **Static generation where possible** — the circuit's marketing pages, pricing page, and documentation can be statically generated at build time (ISR — Incremental Static Regeneration). Only the circuit workflow itself, the dashboard, and artefact viewing require server-side rendering

**Performance budget for the circuit:**

| Metric | Target | Rationale |
|--------|--------|-----------|
| **First Contentful Paint** | < 1.5s | Users arrive from marketing — first impression matters |
| **Time to Interactive** | < 3s | Circuit must feel responsive before user begins typing |
| **Server Action response** | < 500ms | Move submission must feel instant — no loading spinners between moves |
| **PDF generation** | < 3s | Client-side React-PDF — acceptable for a one-time export |
| **Lighthouse Performance** | > 90 | PWA installability and credibility |

**Caching strategy:**

- **Static pages**: CDN-cached at Vercel's edge (marketing, docs, pricing)
- **User dashboard**: Server-rendered with short revalidation (60s) — credit balance should be near-real-time
- **Circuit workflow**: No caching — each move is a unique server mutation
- **Public artefacts**: CDN-cached with on-demand revalidation when `is_public` toggle changes

**Confidence: High** — The circuit's traffic pattern is ideally suited to serverless. Scaling concerns are a success problem, not a launch problem.

*Sources: [Vercel (Fluid Compute)](https://vercel.com/blog/introducing-fluid-compute), [Supabase (Connection Pooling)](https://supabase.com/docs/guides/database/connecting-to-postgres#connection-pooler), [Next.js (Caching)](https://nextjs.org/docs/app/building-your-application/caching), [Web.dev (Performance Metrics)](https://web.dev/metrics/)*

---

### Security Architecture

**Pattern: Defence in depth — multiple independent security layers, each sufficient to prevent the most critical attack vectors.**

The circuit handles sensitive professional data and financial transactions. A security breach would destroy trust irreversibly. The architecture must assume that any single layer can fail and still prevent data exposure.

**Security layers for the circuit:**

**Layer 1: Authentication (Supabase Auth + JWT)**

- Supabase Auth handles user registration, login, password reset, and session management
- JWTs are issued by Supabase and verified on every server-side request
- Critical: always use `supabase.auth.getUser()` on the server (makes a round-trip to verify the JWT) rather than `supabase.auth.getSession()` (trusts the cookie, which can be spoofed)
- Session tokens stored in httpOnly cookies — not accessible to client-side JavaScript

**Layer 2: Row Level Security (database-level isolation)**

- Every table has explicit RLS policies (defined in Integration 3 above)
- Even if application code has a bug, PostgreSQL prevents cross-user data access
- RLS is the last line of defence — it must be enabled on ALL tables, with no exceptions

**Layer 3: Input Validation (Zod schemas)**

- All user input validated server-side using Zod schemas before database insertion
- The circuit's move data is structured — each move type has a defined shape that Zod enforces
- Prevents SQL injection, XSS payloads in stored data, and malformed input

**Layer 4: API Security**

- Server Actions and API routes are server-side only — no API keys exposed to the browser
- Stripe webhook signature verification prevents forged payment events
- Rate limiting via Vercel's built-in edge middleware prevents abuse

**OWASP Top 10 (2025 update) relevance to the circuit:**

| OWASP Category | Circuit Risk | Mitigation |
|----------------|-------------|------------|
| **Broken Access Control** | High — users must not see each other's decisions | RLS policies + `getUser()` verification |
| **Cryptographic Failures** | Medium — payment data, personal decisions | Stripe handles PCI; Supabase encrypts at rest and in transit |
| **Injection** | Medium — user text input in every move | Zod validation + parameterised queries (Supabase client) |
| **Insecure Design** | Low — the circuit's sequential constraint IS the design | State machine prevents skipping moves |
| **Security Misconfiguration** | Medium — RLS disabled, exposed env vars | RLS mandatory on all tables; Vercel env var management |
| **Vulnerable Components** | Medium — supply chain risk in npm ecosystem | Dependabot alerts, lockfile integrity, minimal dependencies |
| **Authentication Failures** | Medium — account takeover | Supabase Auth with rate limiting, optional MFA |
| **Data Integrity Failures** | High — calibration data must be immutable | No UPDATE/DELETE RLS policies on moves and calibrations |
| **Logging and Monitoring** | Medium — detecting abuse | Vercel analytics, Supabase logs, Stripe event logs |
| **SSRF** | Low — no user-controlled URL fetching | Not applicable to the circuit's feature set |

**New in OWASP 2025: Exceptional Condition Handling** — the updated top 10 includes a new category for applications that fail silently or insecurely when encountering unexpected conditions. For the circuit, this means: if a Server Action fails mid-circuit (database timeout, Stripe error), the error must be surfaced to the user, not swallowed. The credit deduction must be atomic — if the circuit cannot start, the credit must not be consumed.

**Confidence: High** — The security architecture follows established patterns for SaaS applications handling sensitive data. No exotic threats require exotic mitigations.

*Sources: [OWASP (Top 10 2025)](https://owasp.org/Top10/), [Supabase (Security)](https://supabase.com/security), [Next.js (Security Headers)](https://nextjs.org/docs/app/api-reference/config/next-config-js/headers), [Vercel (Firewall)](https://vercel.com/docs/security/vercel-firewall)*

---

### GDPR and Data Privacy Architecture

**Pattern: Privacy by design with CASCADE deletes, EU data residency, and minimal data collection.**

The circuit operates under UK/EU GDPR regulations. The architecture must support data subject rights without requiring custom tooling for each request.

**GDPR requirements and architectural implementation:**

| GDPR Right | Implementation |
|------------|---------------|
| **Right to Access** | API endpoint exports all user data as JSON (profile, circuits, moves, artefacts, calibrations). Supabase query: join all user tables by `user_id` |
| **Right to Erasure** | DELETE from `auth.users` → CASCADE deletes all related data across all tables. One SQL statement removes everything |
| **Right to Rectification** | Profile data (display name) is editable. Circuit moves and calibration captures are immutable by design — this is documented in terms of service as part of the product's integrity guarantee |
| **Right to Data Portability** | JSON export of all user data (same as Right to Access). Additionally, artefact PDF/Markdown export provides a portable decision record |
| **Data Minimisation** | The circuit collects only what is needed: decision text, structured responses, and calibration choices. No tracking pixels, no analytics beyond basic usage counts |

**EU data residency:**

- Supabase project deployed to **Frankfurt (eu-central-1)** region — all PostgreSQL data, auth data, and edge function execution within the EU
- Vercel deployment to EU region (London or Frankfurt) for the Next.js application
- Stripe is GDPR compliant with EU data processing agreements

**CASCADE delete chain:**

```
DELETE FROM auth.users WHERE id = {user_id}
  → CASCADE to public.profiles
  → CASCADE to public.credits
  → CASCADE to public.circuits
    → CASCADE to public.circuit_moves
    → CASCADE to public.calibration_captures
    → CASCADE to public.artefacts
  → CASCADE to (any other user-linked tables)
```

**Important caveat: backups.** Supabase Pro plan includes daily backups retained for 7 days. A GDPR deletion removes data from the live database but not from backups. Supabase's backup retention period means truly purged data takes up to 7 days to cycle out. This is standard practice and legally acceptable under GDPR (documented retention schedule), but it should be disclosed in the privacy policy.

**Confidence: High** — The CASCADE delete pattern is the standard approach for GDPR right-to-erasure in PostgreSQL applications. EU data residency is a configuration choice in both Supabase and Vercel.

*Sources: [Supabase (GDPR)](https://supabase.store/pages/gdpr-compliance), [Supabase (Data Processing Agreement)](https://supabase.com/legal/dpa), [PostgreSQL (CASCADE Foreign Keys)](https://www.postgresql.org/docs/current/ddl-constraints.html), [ICO (Right to Erasure)](https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/individual-rights/right-to-erasure/)*

---

### Deployment and Operations Architecture

**Pattern: Git-driven CI/CD with preview deployments, database migrations, and zero-downtime releases.**

The circuit's deployment pipeline should be simple, automated, and safe. Every code change must be reviewable before reaching production.

**Deployment workflow:**

```
Developer pushes to feature branch
  → Vercel creates Preview Deployment (unique URL)
  → Preview connects to Supabase staging project (separate from production)
  → Developer tests on preview URL
  → Pull request reviewed and merged to main
  → Vercel deploys to Production automatically
  → Supabase migrations run via CLI (supabase db push)
```

**Key operational patterns:**

1. **Separate Supabase projects for staging and production** — never test against the production database. Supabase's free tier allows a second project for staging at no cost. Schema migrations are developed against staging, then applied to production via the Supabase CLI

2. **Environment variable management** — Vercel's environment variable system separates Development, Preview, and Production secrets. The Stripe webhook secret, Supabase service role key, and Resend API key are never committed to the repository

3. **Database migrations via Supabase CLI** — `supabase migration new` creates timestamped SQL migration files, `supabase db push` applies them. For zero-downtime schema changes on the live system, use expand-and-contract patterns (add new column → backfill data → update application code → remove old column)

4. **Monitoring and observability:**
   - **Vercel Analytics** — Web Vitals, function execution times, error rates
   - **Supabase Dashboard** — Database performance, query analytics, auth usage
   - **Stripe Dashboard** — Payment success rates, webhook delivery status, revenue metrics
   - **Sentry or LogRocket** (optional at MVP) — Error tracking and session replay for debugging user-reported issues

5. **Rollback strategy** — Vercel supports instant rollback to any previous deployment. If a production release introduces a bug, rollback is a single click in the dashboard. Database rollbacks are more complex (require reverse migrations), which is why schema changes should be non-destructive (additive changes only, remove later)

**Confidence: High** — Git-driven CI/CD with preview deployments is the standard for Vercel-hosted applications. The deployment pipeline requires no custom infrastructure.

*Sources: [Vercel (Preview Deployments)](https://vercel.com/docs/deployments/preview-deployments), [Supabase (Local Development)](https://supabase.com/docs/guides/local-development), [Supabase (Database Migrations)](https://supabase.com/docs/guides/deployment/database-migrations), [Vercel (Environment Variables)](https://vercel.com/docs/environment-variables)*

---

## Implementation Approaches and Technology Adoption

This section translates the architectural decisions above into a practical implementation plan — what to build first, how to build it, how to test it, and what to watch out for.

### Implementation Roadmap: Phased MVP Development

**Strategy: Starter kit foundation → circuit core → payment integration → polish and launch.**

The circuit is not a general-purpose SaaS. It has one workflow, one user type, and one monetisation model. The implementation roadmap reflects this focus — every phase delivers a testable increment of the core product.

**Phase 1: Foundation (Week 1–2)**

- Set up the development environment: Node.js, Supabase CLI, Docker (for local Supabase), Stripe CLI
- Initialise the project using MakerKit or Vercel SaaS Starter as the base
- Configure Supabase project (local + remote staging) with the schema from the Database Architecture section
- Configure Supabase Auth (email/password + Google OAuth)
- Seed the local database with test data (`supabase/seed.sql`)
- Verify: user can sign up, log in, see an empty dashboard

**Phase 2: Circuit Core (Week 3–5)**

- Build the 5-move circuit workflow using the `useReducer` state machine
- Implement each move as a React component with Zod validation
- Create Server Actions for persisting each move to Supabase
- Implement the eligibility gate (pass/fail branching)
- Build the calibration capture form (three forced-choice prompts)
- Implement server-side state persistence and session recovery (resume mid-circuit)
- Verify: user can complete an entire circuit from orientation to calibration (credits bypassed for now)

**Phase 3: Payment and Credits (Week 5–6)**

- Integrate Stripe Checkout Sessions (test mode)
- Build the webhook handler with idempotency checks
- Implement the credit ledger (purchase adds credits, circuit start deducts)
- Build the "Buy Token" flow and credit balance display
- Test the full purchase → circuit → artefact flow end-to-end in Stripe test mode
- Verify: user can buy a token, start a circuit, and see credit balance update correctly

**Phase 4: Artefact and Sharing (Week 6–7)**

- Build the artefact web view (structured React component)
- Implement React-PDF export
- Implement Markdown export
- Build the shareable URL feature (`is_public` toggle + public artefact page)
- Configure Resend for transactional emails (purchase confirmation, share notification)
- Verify: user can view, export, and share their completed artefact

**Phase 5: Polish and Launch (Week 7–8)**

- Build the marketing/landing page (statically generated)
- Implement PWA manifest and service worker (Serwist)
- Security hardening: confirm RLS on all tables, Zod validation on all inputs, security headers
- Performance testing: Lighthouse audit, Core Web Vitals check
- GDPR compliance: privacy policy, cookie consent, data export endpoint, CASCADE delete verification
- Switch Stripe to live mode
- Deploy to production (Vercel + Supabase Cloud Frankfurt)
- Verify: full end-to-end test on production with a real £20 payment

**Total estimated timeline: 6–8 weeks** for a solo developer working full-time with a starter kit foundation. This is aggressive but realistic because the starter kit eliminates 2–4 weeks of authentication, payment, and account management boilerplate.

**Confidence: Medium-High** — Timeline depends heavily on developer familiarity with Next.js and Supabase. A developer new to these tools should add 2–3 weeks for learning.

*Sources: [MakerKit (Next.js Supabase Boilerplate)](https://makerkit.dev/next-supabase), [Supastarter](https://supastarter.dev/), [WeArePresta (MVP Roadmap Guide 2026)](https://wearepresta.com/the-complete-mvp-roadmap-guide-for-2026/), [Nexiby (SaaS MVP Blueprint 2026)](https://nexiby.com/saas-mvp-development/)*

---

### Development Workflow and Tooling

**Pattern: Local-first development with Supabase CLI, hot reload, and separate staging/production environments.**

The development workflow must be fast, reproducible, and safe. A developer should be able to clone the repository, run one command, and have a fully functional local environment — including database, auth, and edge functions.

**Local development stack:**

```
supabase start          → Starts local PostgreSQL, Auth, Storage, Edge Functions (Docker)
npm run dev             → Starts Next.js dev server with hot reload
stripe listen --forward-to localhost:3000/api/webhooks/stripe
                        → Forwards Stripe test events to local webhook handler
```

Three terminal windows. That's the entire local development environment.

**Key workflow practices:**

1. **Supabase CLI manages the database lifecycle** — `supabase init` creates the project structure, `supabase migration new` creates migration files, `supabase db reset` rebuilds the local database from migrations + seed data. Every schema change is versioned in SQL migration files, not made through the Supabase dashboard

2. **Seed data for reproducible testing** — `supabase/seed.sql` populates the local database with test users, sample circuits, and sample artefacts. Running `supabase db reset` returns the database to a known state — essential for debugging and for onboarding new developers

3. **Environment variable discipline** — `.env.local` for development (local Supabase URLs, Stripe test keys), `.env.test` for automated tests (local Supabase URLs), Vercel environment variables for staging/production. The `.env.local` file is gitignored; environment variables are never committed

4. **TypeScript throughout** — TypeScript catches a class of bugs at compile time that would otherwise surface in production. The Supabase CLI generates TypeScript types from the database schema (`supabase gen types typescript`), ensuring type safety between the database and application code

5. **Code formatting and linting** — Biome (the Rust-based successor to ESLint + Prettier, now standard in 2026) for consistent formatting and lint rules. Configured once, enforced via pre-commit hook

**Confidence: Very High** — This is the documented standard workflow for Supabase local development. No custom tooling required.

*Sources: [Supabase (CLI Getting Started)](https://supabase.com/docs/guides/local-development/cli/getting-started), [Supabase (Local Development)](https://supabase.com/docs/guides/local-development), [Supabase (Database Seeding)](https://supabase.com/docs/guides/local-development/seeding-your-database), [Supabase (Database Migrations)](https://supabase.com/docs/guides/deployment/database-migrations)*

---

### Testing Strategy

**Pattern: Three-layer testing — Vitest for unit/integration, Playwright for end-to-end, Stripe CLI for payment flow verification.**

The circuit's testing strategy must cover three distinct concerns: component logic (does the state machine transition correctly?), integration logic (does the Server Action persist data to Supabase?), and end-to-end flows (can a user buy a token and complete a circuit?).

**Layer 1: Unit and Integration Tests (Vitest + React Testing Library)**

- **Circuit state machine**: test every valid transition and every invalid transition attempt. The `useReducer` function is pure — given a state and action, it returns a new state. This is trivially testable with Vitest
- **Zod schemas**: test that valid move data passes validation and invalid data is rejected
- **Server Actions**: test with mocked Supabase client (using `vi.mock`) to verify data transformation and error handling without hitting the database
- **Credit balance calculation**: test the ledger aggregation logic (`SUM(amount) WHERE user_id = ?`)

**Layer 2: End-to-End Tests (Playwright)**

- **Authentication flow**: user signs up → verifies email → logs in → sees dashboard
- **Circuit completion flow**: user starts circuit → completes all 5 moves → submits calibration → sees artefact
- **Payment flow**: user buys token (Stripe test card `4242424242424242`) → credit balance updates → circuit starts
- **Artefact sharing**: user toggles `is_public` → copies share URL → opens in incognito window → artefact is visible
- **RLS isolation**: user A creates a circuit → user B cannot see it (verified via Playwright multi-context)

Playwright runs against the local development stack (Next.js dev server + local Supabase). Authentication state is stored using Playwright's `storageState` feature, so tests don't need to log in on every test run.

**Layer 3: Stripe Payment Testing**

- **Stripe test mode** provides a complete simulation environment. Test card numbers (`4242...` for success, `4000000000000002` for decline) simulate real payment scenarios without moving real money
- **Stripe CLI** forwards webhook events to the local webhook handler: `stripe listen --forward-to localhost:3000/api/webhooks/stripe`
- **Stripe test clocks** simulate time-based events (subscription renewals, delayed payments) — not needed for the credit system but useful if subscription pricing is added later
- **Webhook replay** — if a webhook handler has a bug, Stripe allows re-sending past events from the dashboard. The handler's idempotency check prevents duplicate credit additions

**Testing priority for MVP:**

| Test Type | Priority | Rationale |
|-----------|----------|-----------|
| State machine transitions | Critical | A bug here breaks the core product |
| Credit deduction atomicity | Critical | A bug here means revenue loss or free access |
| Webhook idempotency | Critical | A bug here means duplicate credits |
| End-to-end circuit flow | High | Validates the user experience |
| RLS isolation | High | A bug here is a data breach |
| Artefact PDF generation | Medium | Client-side, user can retry |
| Email sending | Low | MVP can function without email |

**Confidence: High** — Vitest + Playwright is the officially recommended testing stack for Next.js in 2026. Stripe's test mode is comprehensive and well-documented.

*Sources: [Next.js (Testing Guide)](https://nextjs.org/docs/app/guides/testing), [Michele Ong (Testing Next.js 15 + Playwright + MSW + Supabase)](https://micheleong.com/blog/testing-with-nextjs-15-and-playwright-msw-and-supabase), [Stripe (Test Mode)](https://docs.stripe.com/test-mode), [Stripe (Build and Test)](https://docs.stripe.com/get-started/test-developer-integration), [Strapi (Unit and E2E Tests with Vitest & Playwright)](https://strapi.io/blog/nextjs-testing-guide-unit-and-e2e-tests-with-vitest-and-playwright)*

---

### Team Organisation and Skills

**Context: Solo developer or small team (1–2 developers) building the MVP.**

The circuit is a focused product with a narrow feature set. It does not require a large team. The bottleneck is not headcount — it's decision-making speed and product clarity.

**Required skills for the MVP developer:**

| Skill | Level Needed | Notes |
|-------|-------------|-------|
| **React/Next.js** | Strong | App Router, Server Components, Server Actions — the core of the application |
| **TypeScript** | Intermediate | Type safety is important but advanced generics are not needed |
| **PostgreSQL/SQL** | Intermediate | Schema design, RLS policies, basic query optimisation |
| **Supabase** | Intermediate | Auth, RLS, Edge Functions, CLI workflow — well-documented, learnable in days |
| **Stripe API** | Basic | Checkout Sessions + webhooks — a focused subset of Stripe's API |
| **Tailwind CSS** | Basic | UI styling — shadcn/ui provides pre-built components |
| **Git** | Basic | Branching, PRs, merge workflow |

**What the starter kit handles (no skill required):**

- Auth UI flows (login, signup, password reset, OAuth)
- Stripe billing integration scaffolding
- Admin dashboard
- Email configuration
- Account/team management
- Basic landing page template

**Hiring considerations if the product scales:**

The Next.js + Supabase + Stripe stack is the most common SaaS stack in 2026. Finding developers with this skill set is straightforward. The circuit's codebase — a modular monolith with clear route groups — is easy to onboard new developers into. There are no exotic technologies, no custom frameworks, and no proprietary abstractions.

**Confidence: High** — The skill requirements are mainstream and the starter kit reduces the effective skill barrier significantly.

---

### Cost Optimisation and Resource Management

**Pattern: Start lean, optimise only when costs become material relative to revenue.**

The circuit's cost structure is unusually favourable for an MVP: low fixed costs (serverless infrastructure), variable costs that scale with revenue (Stripe fees), and no per-user infrastructure costs until scale.

**MVP cost breakdown (monthly):**

| Component | Cost | Scales With |
|-----------|------|-------------|
| **Vercel Pro** | ~£20/month | Bandwidth and function invocations |
| **Supabase Pro** | ~£25/month | Database size and auth users |
| **Stripe fees** | 2.9% + 30p per transaction | Revenue (a good problem) |
| **Cloudflare DNS** | £0 | N/A (free tier) |
| **Resend** | £0 (free tier: 100 emails/day) | Email volume |
| **Domain name** | ~£10/year | N/A |
| **Sentry** (optional) | £0 (free tier: 5K events/month) | Error volume |
| **Total fixed** | **~£45–50/month** | |

**Revenue breakeven analysis:**

At £20 per token (after Stripe fees of ~£0.88): net revenue per token ≈ £19.12. Monthly fixed costs of £50 require approximately **3 token sales per month** to break even on infrastructure. At £50 per token: approximately **1 token sale per month**.

This is a remarkably low breakeven point. The circuit can sustain itself with a tiny user base whilst product-market fit is being validated.

**Cost optimisation triggers (only pursue when relevant):**

| Trigger | Optimisation | When |
|---------|-------------|------|
| Vercel bandwidth exceeds £100/month | Migrate static assets to Cloudflare Pages | > 1,000 daily visitors |
| Supabase database exceeds 8GB | Archive old circuit data to cold storage | > 50,000 completed circuits |
| Stripe fees exceed £500/month | Negotiate volume discount with Stripe | > £17,000/month revenue |
| Email volume exceeds 100/day | Upgrade Resend to paid tier (~£20/month) | > 100 daily transactions |
| Error volume exceeds 5K/month | Upgrade Sentry or switch to self-hosted option | Indicates a quality problem, not a scaling problem |

**The golden rule for MVP cost management:** Do not optimise costs until they represent more than 10% of monthly revenue. Until then, developer time spent on cost optimisation is more expensive than the costs being optimised.

**Confidence: Very High** — The cost structure is straightforward and the breakeven point is extremely low.

---

### Risk Assessment and Mitigation

**Technical risks specific to the circuit, ranked by impact and likelihood.**

| Risk | Impact | Likelihood | Mitigation |
|------|--------|-----------|------------|
| **Stripe webhook failure** (credits not granted after payment) | Critical — user pays but gets nothing | Low (Stripe retries for 3 days) | Idempotent webhook handler + manual reconciliation admin endpoint + credit balance check on dashboard load |
| **RLS misconfiguration** (user data exposed) | Critical — trust-destroying, potential legal liability | Low (RLS is explicitly defined per table) | Playwright tests verify RLS isolation; enable RLS on ALL tables from day one; no `SECURITY DEFINER` functions without audit |
| **Credit race condition** (two circuits started simultaneously) | High — revenue loss or free access | Medium (technically possible with multiple browser tabs) | Atomic credit deduction via PostgreSQL transaction (`SELECT ... FOR UPDATE` + deduct in single transaction) |
| **State machine bypass** (user skips a move) | High — undermines the entire product concept | Low (state transitions enforced server-side) | Server Actions verify current state before accepting move submission; state stored in database, not client |
| **Starter kit lock-in** (kit's patterns conflict with circuit needs) | Medium — refactoring cost | Medium (starter kits make assumptions about app structure) | Evaluate starter kit structure before committing; prefer kits with minimal opinions (Vercel SaaS Starter) over heavily opinionated ones |
| **Cold start latency spike** (serverless function takes > 3s) | Medium — poor UX on first interaction | Low (Vercel Fluid Compute mitigates this) | Monitor function execution times via Vercel Analytics; if persistent, consider Vercel Pro's warm function feature |
| **Supabase service outage** | High — entire app unavailable | Very Low (99.9% SLA on Pro plan) | Vercel cached static pages remain available; display maintenance message for dynamic features |
| **GDPR subject access request volume** | Low — administrative burden | Very Low at MVP scale | Automated data export endpoint (Phase 5); manual processing acceptable for < 10 requests/month |

**The highest-risk integration is the Stripe webhook handler.** If it fails, real money is involved. The mitigation strategy is threefold:
1. Idempotent processing with event ID deduplication
2. Stripe's automatic retry schedule (up to 3 days)
3. An admin endpoint that can manually reconcile a Stripe session ID to credit addition

**Confidence: High** — These risks are well-understood in the SaaS ecosystem. No novel or unmitigated risks identified.

---

## Technical Research Recommendations

### Recommended Technology Stack (Final)

| Layer | Recommendation | Confidence |
|-------|---------------|------------|
| **Platform** | Progressive Web App (PWA) | Very High |
| **Framework** | Next.js 16 (App Router, React Server Components) | High |
| **UI Library** | shadcn/ui + Tailwind CSS | High |
| **Backend** | Supabase (PostgreSQL, Auth, RLS, Edge Functions) | High |
| **Payments** | Stripe (Checkout Sessions, webhooks, credit system) | Very High |
| **Artefact Export** | React-PDF (client-side) + Markdown | High |
| **Hosting** | Vercel Pro (app) + Supabase Cloud Frankfurt (backend) | High |
| **DNS/CDN** | Cloudflare (free tier) | High |
| **Email** | Resend (free tier) | High |
| **Starter Kit** | MakerKit or Vercel SaaS Starter | High |
| **Testing** | Vitest + Playwright + Stripe CLI | High |
| **Monitoring** | Vercel Analytics + Sentry (free tier) | Medium |

### Implementation Priority Matrix

**Must have for launch (MVP):**
- 5-move circuit workflow with state machine
- Credit purchase and consumption (Stripe)
- Artefact generation (web view + PDF export)
- User authentication and data isolation (Supabase Auth + RLS)
- Basic dashboard (credit balance, circuit history)

**Should have for launch (improves product quality):**
- Shareable artefact URLs
- Calibration capture (three forced-choice prompts)
- PWA installability
- Transactional emails (purchase confirmation)
- Marketing/landing page

**Could have post-launch (enhances growth):**
- Calibration trend analysis (user's decision patterns over time)
- Volume pricing (buy 3 tokens for £50)
- Public artefact gallery (opt-in showcase of anonymised decisions)
- Team/organisation accounts
- API access for enterprise integration

**Won't have at MVP (explicitly excluded):**
- Native mobile apps
- Real-time collaboration
- AI-powered decision assistance
- Subscription pricing (credit system only at launch)
- Multi-language support

### Success Metrics and KPIs

| Metric | Target (Month 1) | Target (Month 6) | Measurement |
|--------|------------------|-------------------|-------------|
| **Circuit completion rate** | > 70% of started circuits | > 80% | Supabase query: completed / started |
| **Eligibility pass rate** | > 50% | Monitor for gaming patterns | Supabase query: passed / attempted |
| **Token purchase conversion** | > 5% of visitors | > 10% | Stripe + Vercel Analytics |
| **Artefact share rate** | > 20% of completed circuits | > 30% | Supabase query: is_public = true |
| **Monthly recurring revenue** | £500 | £5,000 | Stripe Dashboard |
| **Lighthouse Performance** | > 90 | > 95 | Automated CI check |
| **Error rate** | < 1% of sessions | < 0.5% | Sentry |
| **Infrastructure cost ratio** | < 20% of revenue | < 10% of revenue | Manual calculation |

### Skill Development Recommendations

For a developer new to this stack, prioritised learning path:

1. **Next.js App Router fundamentals** (1–2 days) — Server Components, Server Actions, route groups, layouts
2. **Supabase quickstart** (1 day) — CLI setup, local development, Auth, RLS basics
3. **Stripe Checkout integration** (1 day) — Checkout Sessions, webhook handler, test mode
4. **React Hook Form + Zod** (half day) — multi-step form validation pattern
5. **Playwright basics** (half day) — writing and running end-to-end tests
6. **React-PDF** (half day) — creating PDF documents from React components

**Total ramp-up time for an experienced web developer new to this specific stack: ~5 days.** The stack is deliberately composed of well-documented, widely-adopted technologies with extensive tutorial ecosystems.

*Sources: [Stripe (Test Mode)](https://docs.stripe.com/test-mode), [MakerKit (Deploy to Vercel)](https://makerkit.dev/docs/next-supabase-turbo/going-to-production/vercel), [Vercel (Expanding Observability)](https://vercel.com/blog/expanding-observability-on-vercel), [SigNoz (Sentry Alternatives 2026)](https://signoz.io/comparisons/sentry-alternatives/), [Sentry (Log Drains for Vercel and Supabase)](https://sentry.io/changelog/log-drains-for-cloudflare-vercel-heroku-and-supabase/), [PayProGlobal (SaaS MVP Guide)](https://payproglobal.com/how-to/build-mvp-for-saas/), [SaaS Fractional CPO (MVP Development Guide 2026)](https://saasfractionalcpo.com/blog/saas-mvp-development-guide/)*

---

### Multi-Product Forward Planning Notes

The two-product strategy (Circuit MVP → BMAD Training) introduces two architectural constraints that should be carried into the architecture phase. No MVP code changes are required — these are design intent notes to prevent future decisions from closing off the expansion path.

**1. Credit System Product Scope**

The `credits` table is currently designed for circuit tokens only. When BMAD Training launches (likely subscription-based rather than pay-per-use), the system will need to distinguish between product-specific entitlements. The ledger pattern already supports this — adding a `product TEXT NOT NULL DEFAULT 'circuit'` column to the credits table enables per-product balance queries (`SUM(amount) WHERE user_id = ? AND product = 'circuit'`) without restructuring. This column should be added at MVP if the cost is trivial (one column, one default value), or deferred as a migration when Product 2 enters development.

**Architectural constraint:** The credit ledger must not assume single-product usage. Design the balance query interface to accept a product parameter from the start, even if only one product exists.

**2. Single Supabase Project Principle**

Both products must share one Supabase project, one PostgreSQL database, and one auth user pool. This enables:

- **Shared identity** — a Circuit user can later access BMAD Training without creating a new account
- **Cross-product calibration data** — calibration captures from Circuit completions can inform BMAD Training personalisation ("based on your 12 circuits, your calibration trend suggests X")
- **Unified billing** — one Stripe customer ID per user across both products

If the products are split into separate Supabase projects, the calibration data bridge breaks and users need separate accounts. This would undermine the ecosystem strategy.

**Architectural constraint:** One Supabase project, one user pool, one database. Multiple products coexist as schema namespaces (table prefixes or PostgreSQL schemas), not separate infrastructure.
