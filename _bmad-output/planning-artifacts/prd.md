---
stepsCompleted: [step-01-init, step-02-discovery, step-03-success, step-04-journeys, step-05-domain, step-06-innovation, step-07-project-type, step-08-scoping, step-09-functional, step-10-nonfunctional, step-11-polish]
inputDocuments:
  - product-brief-BMAD-TRAINING-2026-02-09.md
  - market-professional-decision-tools-research-2026-02-10.md
  - domain-decision-science-constrained-environments-research-2026-02-10.md
  - technical-5-move-judgement-circuit-architecture-research-2026-02-10.md
  - viability-assessment-5-move-judgement-circuit-2026-02-10.md
workflowType: 'prd'
documentCounts:
  briefs: 1
  research: 3
  brainstorming: 0
  projectDocs: 0
  viabilityAssessments: 1
classification:
  projectType: full_stack
  domain: education
  complexity: medium-high
  projectContext: greenfield
---

# Product Requirements Document - BMAD-TRAINING

**Author:** Tone
**Date:** 2026-02-10

## Executive Summary

**Product:** 5-Move Judgement Circuit — a paid, single-use decision structuring tool for professionals who have stopped deciding and started researching, hedging, or deferring.

**Differentiator:** Constraint as product. Value is in what the system refuses to let you do — hedge, over-research, outsource authority — not what it provides. The product creates a new category: constrained professional decision environments.

**Target users:** Agency leads, senior ICs, indie builders, and mid-career professionals facing consequential decisions where the cost of not deciding exceeds the risk of deciding wrong.

**Business model:** Pay-per-decision token model. Single price point at MVP (exact price determined during soft launch testing within £20–£50 range). No subscription at MVP. Growth through artefact sharing — the output is the marketing.

**Tech stack:** Next.js 16 + Supabase + Stripe + Vercel. Solo founder build. PWA, no native apps.

## Success Criteria

### User Success

**Primary success moment:** The user holds a defensible decision record — a professional artefact they produced through constrained action, not retrospective documentation. The artefact looks credible enough to share with a colleague or stakeholder.

**Secondary success moment (alongside):** The calibration capture surfaces something the user didn't know about how they decide. Not reflection — classification. "Did the circuit change what you would have done?" If the answer surprises them, calibration is working.

**Tertiary success:** The relief of having decided. The circuit ends analysis paralysis through constraint, not advice.

**Dignified exit criteria:** Eligibility failure is successful calibration, not rejection. "Not proceed" at any point is valid, not failure.

**User success metrics:**

| Metric | MVP Target | 6-Month Target |
|--------|-----------|---------------|
| Circuit completion rate (started → artefact) | >70% | >80% |
| Artefact share rate (is_public = true) | >20% | >30% |
| Completion-to-share ratio | >25% | >35% |
| Eligibility pass rate | >50% | Monitor for gaming |
| Repeat token purchase (within 6 months) | >10% | >20% |

**Decision stakes tracking:** The orientation move captures user self-reported decision stakes (career/financial/strategic/operational). Artefact share rate is tracked *by stakes level* to identify whether the product activates best on high-stakes or medium-stakes decisions.

### Business Success

**Revenue targets:**

| Metric | Month 1 | Month 6 | Month 12 |
|--------|---------|---------|----------|
| Monthly Gross Revenue | £500 | £5,000 | Sustainable growth |
| Token purchase conversion (visitors → buyers) | >5% | >10% | >10% |
| Infrastructure cost as % of revenue | <20% | <10% | <10% |

**Growth engine metrics:**

| Metric | Target | Why It Matters |
|--------|--------|---------------|
| Artefact share rate | >20% | Process-to-output value confirmation |
| Share-to-signup conversion | >5% of artefact link visitors | Artefact activates recipients, not just impresses them. Note: sharing is selective — users will share lower-stakes or professionally framed artefacts, not career-risk admissions. Share rate by stakes level is the diagnostic |
| Median days to second purchase | <90 days | If >90 days, token model alone cannot sustain the business — trigger subscription option |
| Activation-qualified subscribers | >30% of email list | Subscribers with a pending decision, not topic tourists |

**Pre-launch demand signal:** Email list of 2,000+ subscribers via content marketing (long-form essays, social distribution, guest posts in professional communities). Acquisition channel is organic — no paid ads at pre-launch. This target is an assumption; kill criterion #1 (<500 after 3 months) is the reality check. If <30% of subscribers are activation-qualified, pivot content strategy from thought leadership toward decision-trigger content.

**Kill criteria:**
1. <500 email subscribers after 3 months of content marketing → pause
2. <5% soft launch conversion within 30 days → investigate
3. <50% circuit completion rate → investigate cold start
4. <10% artefact sharing after 3 months → redesign artefact
5. <10% repeat purchase within 6 months → reconsider model
6. Median repeat purchase >90 days → introduce subscription floor alongside tokens
7. <30% activation-qualified subscribers → pivot content strategy

### Technical Success

Performance and security targets are defined in Non-Functional Requirements. Key thresholds for kill/investigate decisions:

| Metric | Target |
|--------|--------|
| Error rate | <1% of sessions |
| RLS isolation | Zero cross-user data leaks |
| Webhook reliability | Zero lost credit additions |
| GDPR compliance | CASCADE delete verified, EU data residency |

### Sustainability Metrics

| Metric | Threshold | Trigger Action |
|--------|-----------|---------------|
| Founder hours per week | Tracked from launch | Baseline visibility |
| Sustainability ceiling (burnout + no payoff) | >50 hrs/week for 4+ consecutive weeks AND revenue <£8k/month | Forced scope reduction: pause content marketing, pause feature development, or raise prices |
| Sustainability ceiling (burnout regardless) | >60 hrs/week for 4+ consecutive weeks at any revenue | Review workload and delegate or cut scope — revenue does not justify unsustainable hours indefinitely |

### Measurable Outcomes

**Primary indicator:** Completion-to-share ratio. If users complete the circuit AND share the artefact, both process value and output value are confirmed. This single ratio captures more signal than any individual metric.

**Secondary indicator:** Share-to-signup conversion. If artefact recipients create accounts, the viral loop converts attention into activation — the growth engine is real, not performative.

## Product Scope

### MVP — Minimum Viable Product

- 5-move circuit workflow with enforced state machine (5 user-facing moves: Orientation, Declaration, Sufficiency, Artefact/Defence, Stop/Go — plus Eligibility gate and Calibration Capture = 7-state FSM)
- Token/credit purchase and consumption via Stripe
- Artefact generation (structured web view + PDF export)
- User authentication and data isolation (Supabase Auth + RLS)
- Basic dashboard (credit balance, circuit history)
- Shareable artefact URLs (public/private toggle)
- Calibration capture (three forced-choice prompts)
- Decision stakes classification in orientation move
- PWA installability
- Marketing/landing page
- GDPR compliance (privacy policy, data export, CASCADE delete)

**Explicitly excluded from MVP:**
- Native mobile apps
- Real-time collaboration
- AI-powered decision assistance
- Subscription pricing (credit/token system only at launch)
- Multi-language support
- Team/organisation accounts

### Growth Features (Post-MVP)

- Calibration trend analysis (decision patterns across multiple circuits)
- Volume pricing (buy 3 tokens for £50)
- Markdown export for knowledge management tools
- Public artefact gallery (opt-in showcase)
- Stakes-tiered pricing (standard £20–£30, high-stakes £75–£150)
- 30-day reflection trigger email ("How did that decision work out?")
- Decision portfolio view (after 3+ circuits)
- Low-cost subscription floor (£5–£10/month for 1 circuit/month) — triggered if median repeat >90 days

### Vision (Future)

- BMAD Training product (the ecosystem play)
- Team/organisation tokens with multi-stakeholder circuits
- API access for enterprise workflow integration
- Coaching partnership programme (between-sessions tool)
- Decision artefact format as de facto professional standard
- Cross-product calibration data bridge

## User Journeys

### Journey 1: Marcus — The Agency Lead Who Lost Narrative Control

**Persona:** Agency founder, 12-person digital agency. His team shipped a client redesign in three weeks using AI-assisted workflows. When the client's CTO asked "Why this architecture?", the lead developer said "It was the fastest approach." The client now demands a full review before approving the next phase. Marcus is on his laptop at 10pm looking for a way to never be in that room again.

**Discovery:** Quiet referral from another agency founder: "It won't teach you anything. It'll make you decide." Buys a token.

**The Circuit:**
- **Orientation:** Types: *"Do I freeze scope on the Meridian project now or keep iterating to satisfy the client's new requests?"*
- **Eligibility:** Disqualifies *"Which project management tool to migrate to"* — low consequence, reversible. Decision qualifies. Token consumed.
- **Declaration:** First attempt blocked — "We need to decide whether to freeze scope" lacks ownership. Rewrites: *"I am deciding to freeze scope on Meridian and present the current delivery as sufficient. If the client walks, I own that."* Consequence: *"We lose the account. That's £180k ARR."*
- **Sufficiency (crucible):** Wants to write three paragraphs. Forced to be specific: *Enough: "Current feature set covers 90% of user flows. Remaining 10% are edge cases the client hasn't specified." Excluded: "Performance optimisation — it's fast enough." Risk: "The client may see 'fast enough' as 'not finished.'"* This is where restraint is trained — Marcus has never written down what "enough" looks like.
- **Artefact:** One-page decision record. Defence prompt: *"Your rejected alternative was 'keep iterating.' Why isn't that actually better?"* — *"Because iterating without a boundary is how we got here."*
- **Stop/Go:** Commits. Downside: *"Client may escalate to our MD."* Reconsideration trigger: *"If the client identifies a genuine missed user flow, not an edge case."*

**Calibration Capture:** *Which behaviour stopped?* Selects: *"I was still changing what the decision was about."* He wasn't indecisive about scope — he was avoiding defining what the decision actually was.

**Resolution:** Shares artefact link with co-founder. Two weeks later, buys another token for a hiring decision.

---

### Journey 2: Priya — The Senior IC Under Increased Visibility

**Persona:** Staff engineer, mid-size fintech. Seven years of being "the one who does it right." AI adoption tripled team output. Her thoroughness — once a shield — is now friction. Her manager said: "We love the quality, but we need to talk about velocity." She heard: *your judgement is no longer enough to justify your pace.* She's trying to figure out whether she's obsolete or miscalibrated.

**Discovery:** Long-form essay — "The difference between being thorough and being right." Buys a token at midnight. Self-directed. Nobody told her to.

**The Circuit:**
- **Orientation:** Types: *"Do I adopt the team's AI-first workflow and reduce my review depth, or maintain my current standards and accept the velocity gap?"*
- **Eligibility:** Disqualifies *"Which linting rules to enforce"* — low stakes. Decision qualifies.
- **Declaration (crucible):** First attempt: "The team needs to decide how to balance quality and speed." Blocked — collective voice, not hers. Rewrites: *"I am deciding to reduce my review depth to match the team's AI-assisted pace. If something ships that I would have caught, I own that."* Consequence: *"A production incident traces back to a review I signed off on. My reputation takes the hit."* Declaration is Priya's crucible — she's spent her career making decisions sound like team decisions. Writing "I own that" is the hardest thing the circuit asks of her.
- **Sufficiency:** *Enough: "Reviewing architecture and security. Trusting AI-generated implementation patterns for standard CRUD." Excluded: "Line-by-line review of generated code that follows established patterns." Risk: "A style inconsistency ships. Nobody dies."* For Priya, naming what she's willing to let go is the relief — she's never had permission to say "this doesn't matter enough."
- **Artefact:** Defence prompt: *"Why isn't maintaining current standards actually better?"* — *"Because thoroughness without prioritisation is just anxiety with a process."*
- **Stop/Go:** Commits. Downside: *"I lose the identity of being the thorough one."* Reconsideration trigger: *"If a category of bug starts appearing that my old review depth would have caught."*

**Calibration Capture:** *Which behaviour stopped?* Selects: *"I was still gathering information."* She wasn't reviewing more carefully — she was reviewing more to feel safe.

**Resolution:** Doesn't share the artefact. Saves it. Reads it before sprint planning. Review turnaround drops 40%. Buys another token three weeks later for: *"Do I put myself forward for the platform architect role?"*

---

### Journey 3: Kai — The Indie Builder with Structure Whiplash

**Persona:** Solo founder building a SaaS tool for freelance photographers. In six months he's adopted and abandoned: agile boards, "just ship it", a Notion PM system, and raw AI prompting. He's stalled at 60% built. Opens the codebase every morning, stares at it, closes it. He's burned out on deciding *how* to work, not on the work itself.

**Discovery:** YouTube essay. The hook: "The problem isn't that you don't know enough. It's that you can't tell when you know enough." Buys a token impulsively on a Saturday afternoon.

**The Circuit:**
- **Orientation:** Almost closes the tab — he's been told to "just decide" before. But there's no content, no framework diagram. Just: type your decision. Types: *"Do I rebuild the upload flow for batch processing, or ship single-upload and add batch later?"*
- **Eligibility:** Disqualifies *"Which colour palette for the dashboard"* — low stakes. Decision qualifies. Token consumed.
- **Declaration:** *"I am deciding to ship single-upload now and defer batch processing. If users churn because it's too slow for professional workflows, I own that."* Consequence: *"I lose my first 20 beta users before I learn whether the core product works."* Ownership isn't Kai's problem. Scope is.
- **Sufficiency (crucible):** *Enough: "Single file upload with progress indicator, error handling for >50MB files, confirmation on success." Excluded: "Batch processing. Drag-and-drop. Resume on failure."* He's never written down what he's *not* building. Every framework he's tried told him to prioritise. None asked him to name what he's refusing. *Risk: "Power users find single-upload too slow and leave before I ship batch."* For Kai, the circuit gives **permission** — the exclusion is a required field, not an afterthought.
- **Artefact:** Defence prompt: *"Why isn't rebuilding for batch actually better?"* — *"Because I've rebuilt three things this month and shipped none of them."*
- **Stop/Go:** Commits. Downside: *"Beta users may hit the ceiling within two weeks."* Reconsideration trigger: *"If more than 3 of my first 10 users mention batch upload unprompted."*

**Calibration Capture:** *Which behaviour stopped?* Selects: *"I was still changing what the decision was about."* Same classification as Marcus, completely different underlying pattern — Marcus was avoiding definition, Kai was oscillating. The system doesn't need to know the difference. Kai does.

**Resolution:** Ships single-upload that evening — first thing he's shipped in five weeks. Screenshots the sufficiency field and pins it above his monitor. Buys another token ten days later for: *"Do I add a free tier or launch paid-only?"*

---

### Journey 4 (Edge Case): Dev — The Decision That Didn't Need Structure

**Persona:** Senior product manager at a Series B startup. Capable, under moderate pressure, heard about the circuit from a colleague. Not in crisis — curious. Has a nagging decision he's been circling for two weeks. Buys a token on a Tuesday lunchbreak.

**The Circuit — Eligibility Failure:**
- **Orientation:** Types: *"Should we use Postgres or MongoDB for our new analytics service?"*
- **Eligibility:** Disqualifies *"What to name the service"* — fine. Asked why his decision deserves structure, writes: *"Because it affects our whole data architecture."* But he can't articulate who sees the consequence if this goes wrong. The tech stack choice is reversible within a quarter. It affects performance, not careers. Nobody's reputation is on the line. **Eligibility fails.** The system says: *"Stopping here is correct."* No explanation. No rubric. No retry coaching.

**Post-Eligibility Classification (optional):**
> *Which property made this decision unsuitable for structure?*

Dev selects: *"The cost of structuring exceeded the risk."* As he selects it, he realises — he's spent two weeks on a decision that needed a 30-minute team discussion, not a structured judgement sequence.

**Resolution:** Token preserved. Dev closes the tab. Slightly annoyed, slightly relieved. Over the next week, the classification sticks — he starts noticing other decisions where structuring exceeds the risk. Three weeks later, he returns with: *"Do I recommend we kill the underperforming product line, knowing the CEO's reputation is attached to it?"* Eligibility passes. Token consumed.

---

### Journey Requirements Summary

**Capabilities revealed across all four journeys:**

| Capability Area | Requirements | Revealed By |
|----------------|-------------|-------------|
| **State Machine** | Linear 7-state FSM with enforced progression; no backward navigation; field validation before state transition | All journeys |
| **Language Blocking** | Block passive/collective voice and AI attribution in Declaration; provide immediate, non-hostile redirection copy | Marcus, Priya |
| **Field Constraints** | Short text fields in Sufficiency; mandatory exclusion field; single-sentence risk field; 50-char cap on calibration free-text | Marcus, Kai |
| **Token Management** | Preserve token on eligibility failure with clear confirmation; consume on circuit entry; track balance on dashboard | Dev (critical) |
| **Artefact Generation** | Professional-quality decision record; structured web view; PDF export clean enough for client-facing use; public/private toggle | Marcus |
| **Artefact Storage** | Multiple artefacts per user; individual access from dashboard; no cross-decision analytics at MVP | Priya, Kai |
| **Eligibility UX** | Dignified failure state; no criteria revealed; no retry coaching; optional classification prompt; session ends cleanly | Dev |
| **Defence Prompt** | Structured challenge from user's own inputs (rejected alternative); write-in response, not yes/no | All happy paths |
| **Calibration Capture** | Three forced-choice prompts; all optional; no system response to selections; appears only after Stop/Go or eligibility exit | All journeys |
| **Return Flow** | Frictionless re-entry; land at orientation, not re-onboard; token balance visible immediately | Dev, Kai |
| **Performance** | Sub-20-minute session; <500ms server actions; works on mobile (PWA); Saturday afternoon on a laptop | Kai |
| **Privacy** | No social features; no sharing pressure; private-by-default artefacts; data isolation via RLS | Priya |
| **Analytics (Internal)** | Track: eligibility failure → return rate; commit/not-proceed ratio; completion-to-share ratio; stakes classification distribution | Dev, all |
| **Orientation Scaffolding** | Field hint or copy bridging problem-to-decision gap: enforce "Do I..." or "I am deciding whether to..." framing | Pre-mortem |
| **Purchase Readiness** | Track token-purchase-to-first-orientation latency as internal diagnostic; if median >7 days, purchase flow disconnected from decision readiness | Pre-mortem |
| **Session Re-entry** | On resume, re-present user's own declaration with "Are you still deciding this?" before continuing; re-anchor emotional contract | Pre-mortem |
| **Documentation User Diagnostic** | Track "The decision closed without resistance" selection rate in calibration capture; if >30%, investigate documenter vs decider ratio | Pre-mortem |
| **Progressive Language Guidance** | Declaration blocking escalates: 1st rejection → redirect copy; 2nd → structural scaffold; 3rd → convert to fillable structured fields | Pre-mortem |
| **Return Purchase Reason** | One optional post-purchase question: "What prompted this purchase?" (new decision / wanted to practise / recommended / other) | Pre-mortem |

### Pre-mortem Findings

| Blind Spot | Severity | Impact |
|-----------|----------|--------|
| Users arrive with problems, not decisions | High | Orientation UX gap — needs field scaffolding |
| Purchase-to-circuit gap | Medium | Missing analytics — track token-to-first-attempt latency |
| Session interruption kills emotional arc | Medium | Re-entry prompt needed — re-anchor, not just restore |
| "Already decided" users inflate metrics | Medium | Diagnostic — track "closed without resistance" rate |
| Language blocking rage-quit spiral | High | Progressive guidance escalation on repeated rejections |
| Return purchase is crisis-driven, not habit-driven | Medium | Post-purchase reason tracking (one optional question) |

## Innovation & Novel Patterns

### Detected Innovation Areas

This product creates a new category — **constrained professional decision environments** — rather than entering an existing one. Five distinct innovations underpin the product, each requiring specific validation.

1. **Category Creation** — "Constrained professional decision environments" don't exist as a product category. This product defines it.
2. **Constraint as Product** — Value is in what the system refuses to let you do (hedge, over-research, outsource authority), not what it provides.
3. **Cold Start Preservation** — No pre-circuit content. Immediate action IS the intervention. The shock of being asked to decide without preparation is load-bearing, not a UX oversight.
4. **Self-Punishing Economics** — Gaming is resolved through token economics, not fraud detection. Hollow decisions produce worthless artefacts at the user's expense. Risk: an insincere user who pays and gets no value is a refund request, not a self-correcting system. Mitigation: eligibility gate filters low-stakes decisions pre-payment; refund policy must be defined at launch (architecture scope).
5. **Classification, Not Reflection** — Calibration capture is post-mortem classification of behaviour, not introspection about feelings. "What changed" not "how did it feel."

### Validation Approach

Each innovation has a defined evidence path, earliest detectable signal, and fallback:

| Innovation | Validated When | Earliest Signal | Measurement |
|-----------|---------------|----------------|-------------|
| Category creation | Users describe the product in constraint language unprompted, not "course" or "tool" language | User language in share messages and referral context | Referral message content + search console terms |
| Constraint as product | Users who hit language blocking report constraint as the valuable part; blocked users have higher share rates than unblocked | Declaration rewrite count correlated with share rate | Track declaration rejection count per session; correlate with downstream metrics |
| Cold start | Users type their first input within 60 seconds of orientation page load; completion rate ≥70% despite zero onboarding | Time-to-first-input at orientation | Page load → first keystroke latency as internal diagnostic |
| Self-punishing economics | Low-stakes decisions correlate with lower share and return rates; no eligibility hacking patterns emerge over time | Share rate segmented by decision stakes level | All metrics segmented by stakes classification from day one |
| Classification not reflection | Calibration capture option distribution is even (no option >40%); capture completers return at higher rates than skippers. Caveat: all responses are optional — completers self-select, so completion rate and completer-vs-skipper comparisons carry survivorship bias. Track completion rate alongside distribution | Distribution evenness across calibration options | Weekly option selection distribution + completion rate as diagnostic |

### Risk Mitigation

| Innovation | Fallback If Not Validated |
|-----------|--------------------------|
| Category creation | Product works as niche professional tool within BMAD ecosystem; two-product strategy still holds |
| Constraint as product | Soften language blocking to suggestions; move from hard constraints to progressive disclosure |
| Cold start | Add single pre-orientation sentence — context, not content. A/B test cold start vs one-sentence primer |
| Self-punishing economics | Tighten eligibility with second prompt: "Who will see the result of this decision?" — adds friction but preserves no-fraud-detection principle |
| Classification not reflection | Reduce from three calibration prompts to one (most diagnostic: "Which behaviour stopped?") — less data, crisper classification |

## Web Application Specific Requirements

### Project-Type Overview

The 5-Move Judgement Circuit is a full-stack web application classified closest to `web_app` in architecture pattern — a Next.js 16 App Router application with server-side rendering, server actions, and PWA capabilities. It is not a traditional SPA; it is a server-first application where the circuit state machine runs as a `useReducer` FSM on the client with server persistence via Supabase.

### Technical Architecture Considerations

- **Rendering Strategy:** Server Components (RSC) by default; client components only for the circuit state machine, Stripe checkout, and interactive form fields. No client-side routing between circuit steps — each state transition persists server-side before UI updates.
- **Browser Support:** Modern evergreen browsers (Chrome, Firefox, Safari, Edge — last 2 versions). No IE11. No polyfills for legacy.
- **Responsive Design:** Mobile-first PWA. Circuit must be fully usable on a phone screen — Kai on a Saturday afternoon on his laptop, but also Marcus at 10pm on his phone. Touch targets ≥44px.
- **SEO Strategy:** Marketing pages (landing, pricing) are SSR with full meta tags. Circuit pages are authenticated and not indexed. Artefact share pages are SSR with structured data for link previews.
- **Accessibility:** WCAG 2.1 AA. Keyboard navigable circuit. Screen reader compatible form fields. High contrast for text-heavy circuit steps (Declaration, Sufficiency).
- **PWA Capabilities:** Installable. Offline graceful degradation (display "reconnect to continue" rather than break mid-circuit). Service worker for static asset caching. Not offline-first — circuit requires server persistence.

### Implementation Considerations

- **Authentication:** Supabase Auth with magic link (primary) and OAuth (Google, GitHub). No password-based auth at MVP — reduces friction and support burden.
- **Real-time Requirements:** None at MVP. Circuit is single-user, synchronous. No WebSockets needed.
- **PDF Generation:** Artefact export as PDF — implementation approach (server-side vs client-side) deferred to architecture phase.
- **Session Interruption:** Circuit state persisted after each step transition. On return, re-anchor with user's own declaration before continuing (from pre-mortem findings).
- **Data Architecture:** PostgreSQL via Supabase. Row Level Security for data isolation. Immutable audit tables for circuit moves and calibration captures. Credit ledger pattern for token management.

## Project Scoping & Phased Development

### MVP Strategy & Philosophy

**MVP Approach:** Experience MVP — the minimum circuit that delivers the full emotional and professional arc. Unlike a feature MVP (ship the smallest useful thing) or a platform MVP (build for extensibility), this product's value is in the *completeness of the constrained experience*. A partial circuit is worthless. The MVP ships all 7 states or nothing.

**Resource Requirements:** Solo founder build. Next.js 16 + Supabase + Stripe + Vercel. No dedicated design resource — the product is deliberately text-heavy with minimal UI complexity. No backend team — Supabase handles auth, database, and RLS. No DevOps — Vercel handles deployment and scaling.

**MVP Boundary Principle:** If removing a feature breaks the circuit's emotional arc or makes the artefact unprofessional, it's MVP. If removing it only reduces analytics precision or operational convenience, it's post-MVP.

### Analytics Tiering

**Tier 1 — Instrument and monitor at MVP** (act on within 90 days):

- Circuit completion rate, artefact share rate, token purchase conversion, repeat purchase rate
- Eligibility pass rate, commit vs not-proceed ratio
- Token-to-first-orientation latency (purchase flow health)
- Server action response times, error rate, webhook delivery success
- Return purchase reason (one optional post-purchase question)
- MRR and infrastructure cost % (via Stripe/Vercel dashboards)

**Tier 2 — Log events at MVP, analyse post-MVP** (store raw data, no dashboards):

- Declaration rejection count per session, time-to-first-input at orientation
- Calibration option distribution, share rate by stakes level, referral message content
- Share-to-signup conversion, median days to second purchase
- Eligibility failure → return rate, "closed without resistance" rate
- Activation-qualified subscriber %, founder hours per week

**Implementation principle:** Tier 1 gets a weekly query or dashboard. Tier 2 gets `analytics_events` table inserts — the data exists when volume justifies analysis.

### Scope Risk Assessment

**Technical risk:** Low. The stack is proven (Next.js + Supabase + Stripe). The state machine is the most complex component — mitigated by `useReducer` FSM pattern with server persistence. Language blocking in Declaration is regex-based at MVP, not NLP.

**Market risk:** Medium. Category creation means no proven demand. Mitigated by: pre-launch email list (2,000+ target), content marketing that names the pain, soft launch conversion as earliest signal. Kill criteria are defined.

**Resource risk:** Low for build, medium for sustain. Solo founder can build MVP. Risk is post-launch: content marketing + support + iteration as a single person. Sustainability ceiling metric (>50 hrs/week for 4+ weeks at <£8k/month) triggers forced scope reduction.

**Scope creep risk:** Low. The product philosophy is self-disciplining — "constraint as product" applies to its own development. The circuit is 7 states. Adding features contradicts the value proposition.

### Phase Dependencies

- **Phase 1 → Phase 2:** Growth features (calibration trends, volume pricing, stakes-tiered pricing) require Tier 2 analytics data accumulated during Phase 1. Minimum 3 months of Phase 1 data before Phase 2 decisions.
- **Phase 2 → Phase 3:** Vision features (team tokens, API access, coaching partnerships) require validated product-market fit from Phase 1 kill criteria AND growth metrics from Phase 2. No Phase 3 planning until repeat purchase rate >20%.

## Functional Requirements

### Circuit Execution

- **FR1:** User can enter a decision as free text in the orientation step
- **FR2:** System provides field scaffolding that guides "Do I..." or "I am deciding whether to..." framing in orientation
- **FR3:** User can test a low-stakes decision for eligibility disqualification before committing their token
- **FR4:** System evaluates eligibility based on user-provided justification without revealing evaluation criteria
- **FR5:** System preserves the user's token when eligibility fails
- **FR6:** System presents a clean, non-judgemental exit with optional post-eligibility behaviour classification when eligibility fails
- **FR7:** System consumes exactly one token per circuit at the moment of eligibility pass (see FR25)
- **FR8:** User can write a declaration of ownership with stated consequences
- **FR9:** System blocks passive voice, collective voice, and AI attribution in declarations
- **FR10:** System provides progressive language guidance on repeated declaration rejections (redirect copy → structural scaffold → fillable structured fields)
- **FR11:** User can define sufficiency boundaries with mandatory "enough", "excluded", and "risk" fields
- **FR12:** System enforces field constraints in sufficiency (short text, mandatory exclusion, single-sentence risk)
- **FR13:** System generates a defence prompt derived from the user's own rejected alternative
- **FR14:** User can respond to the defence prompt in free text
- **FR15:** User can commit or not-proceed at Stop/Go with stated downside and reconsideration trigger
- **FR16:** System presents calibration capture with three forced-choice prompts after circuit completion or eligibility exit
- **FR17:** Calibration capture responses are optional with no system feedback on selections
- **FR18:** User can classify their decision stakes level during orientation
- **FR19:** System enforces linear state progression with no backward navigation
- **FR20:** System validates all required fields before allowing state transition
- **FR21:** User can resume an interrupted circuit with re-anchoring prompt showing their own declaration

### Token & Payment

- **FR22:** User can purchase decision tokens via credit card payment
- **FR23:** User can view their current token balance on the dashboard
- **FR24:** System presents one optional post-purchase question about purchase reason
- **FR25:** System consumes a token at eligibility pass, not at circuit entry

### Decision Artefacts

- **FR26:** System generates a structured decision record (decision, declaration, sufficiency boundaries, defence response, commitment, calibration) as web view upon circuit completion
- **FR27:** User can export their decision artefact as PDF
- **FR28:** User can toggle artefact visibility between public and private
- **FR29:** User can share a public artefact via URL
- **FR30:** User can add an optional message when sharing an artefact link
- **FR31:** User can access all their artefacts individually from the dashboard
- **FR32:** Shared artefact pages render with structured data for link previews

### User Account & Data

- **FR33:** User can create an account via passwordless authentication or third-party identity provider
- **FR34:** User can view their circuit history on the dashboard
- **FR35:** User can request export of all their personal data
- **FR36:** User can request deletion of their account and all associated data
- **FR37:** System isolates user data so no user can access another user's circuits or artefacts

### Marketing & Conversion

- **FR38:** Visitor can view the product landing page with product positioning
- **FR39:** Visitor can view pricing information
- **FR40:** Visitor can sign up for the pre-launch email list
- **FR41:** Artefact link recipients can view shared artefacts without an account
- **FR42:** Artefact link recipients can create an account from the shared artefact page

### Analytics & Diagnostics

- **FR43:** System tracks Tier 1 metrics with dashboard or weekly query access (circuit completion, share rate, conversion, eligibility pass rate, commit ratio, response times, errors, webhook success)
- **FR44:** System logs Tier 2 analytics events for future analysis (declaration rejections, orientation timing, calibration distribution, stakes segmentation, referral content)
- **FR45:** System tracks token-purchase-to-first-orientation latency as internal diagnostic

## Non-Functional Requirements

### Performance

- Server action response time: <500ms (p95)
- First Contentful Paint: <1.5s
- Time to Interactive: <3s
- Lighthouse Performance Score: >90
- Circuit session duration: sub-20 minutes end-to-end (design target, not hard limit)
- State transition persistence: each circuit step persists server-side before client UI updates

### Security

- All data encrypted at rest (Supabase default) and in transit (TLS)
- Row Level Security enforces zero cross-user data access
- Payment processing handled entirely by Stripe (no card data touches our servers)
- Credit ledger writes restricted to service role only (no client-side credit manipulation)
- Immutable audit tables for circuit moves and calibration captures (append-only, no UPDATE/DELETE)
- Authentication via Supabase Auth (magic link + OAuth) — no password storage
- GDPR: CASCADE delete on account deletion, data export on request, EU data residency, privacy policy

### Accessibility

- WCAG 2.1 AA compliance
- Full keyboard navigation through circuit workflow
- Screen reader compatible form fields and state transitions
- Contrast ratio ≥ 4.5:1 for normal text, ≥ 3:1 for large text (WCAG AA) — particularly for Declaration and Sufficiency steps (text-heavy, high-stakes input)
- Touch targets ≥44px for mobile PWA usage

### Integration

- Stripe webhook delivery: zero lost credit additions (retry and reconciliation strategy required)
- Supabase Auth: magic link delivery reliability (Resend as email provider)
- Stripe checkout: payment failure handling with retry option, clear error messaging, and no silent failure (user always informed of outcome)
- Artefact share links: Open Graph and structured data for social/messaging link previews

### Scalability

- Architecture supports horizontal scaling via Vercel serverless and Supabase connection pooling
- No architectural decisions at MVP that would require rewrite at 10x users
- Database schema supports future multi-tenancy without migration (user_id foreign keys on all tables)

### Reliability

- Error rate: <1% of sessions
- Circuit state survives browser close, device switch, and network interruption
- Interrupted circuits resumable with re-anchoring prompt
- Webhook processing idempotent (duplicate delivery doesn't double-credit)
