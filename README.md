# The Circuit

A constrained professional decision environment. Pay-per-decision. No subscriptions, no dashboards, no advice.

The Circuit exists for professionals who have stopped deciding and started researching, hedging, or deferring. It provides a structured, witnessed proceeding — five moves from orientation to commitment — that produces an immutable decision artefact. The system enforces constraint: language blocking prevents hedging, designed emptiness prevents distraction, and the forward-only flow prevents retreat.

**This is not a productivity tool.** It is closer to a notarised deposition than a form. The user's words become the record. The system witnesses. That's all.

## What We've Done

All planning work follows the [BMAD Method](https://github.com/bmad-code-org/bmad-method) (v6) — a structured agent-driven workflow for product development.

### Phase 1 — Analysis
- Product brief defining the constrained decision environment concept
- Market research and domain analysis

### Phase 2 — Planning
- **Product Requirements Document (PRD)** — four user personas (Marcus, Priya, Kai, Dev), circuit mechanics, eligibility/exit logic, token economics, and MVP scope
- **PRD Validation Report** — independent review confirming PRD completeness
- **UX Design Specification** (14 collaborative steps, complete) covering:
  - Core experience mechanics and emotional response architecture
  - Design system: cu.css (CUBE CSS + Utopia fluid responsive), Source Serif 4 variable font, near-monochrome oklch palette
  - "Considered" design direction — centred alignment, 42.5rem content column, maximum spatial generosity
  - 5 user journey flows with Mermaid diagrams
  - 21 custom component specifications
  - 10 Circuit-specific UX consistency patterns (including Designed Absence as a codified pattern)
  - No-breakpoint responsive architecture (Utopia clamp, no @media width queries)
  - WCAG 2.2 AA + selective AAA accessibility strategy
- **Design direction mockups** (HTML) and **colour theme visualiser** (HTML)

### Phase 3 — Solutioning (next)
- Solution architecture
- Epics and stories
- Implementation readiness check

### Phase 4 — Implementation (planned)
- Sprint planning and story development
- Next.js 16 + Supabase + Stripe + Vercel
- PWA with service worker caching

## Tech Stack (Planned)

| Layer | Technology |
|-------|-----------|
| Framework | Next.js 16 (App Router) |
| Database | Supabase (Postgres + Auth + Realtime) |
| Payments | Stripe (token-based, pay-per-decision) |
| Hosting | Vercel |
| Design System | cu.css (custom CUBE CSS + Utopia) |
| Typography | Source Serif 4 (variable, weight 200–900) |
| Colour | oklch colour space, near-monochrome with ink opacity hierarchy |
| Delivery | PWA (installable, offline-capable static assets) |

## Project Structure

```
_bmad/                    # BMAD v6 framework
_bmad-output/
  planning-artifacts/
    prd.md                # Product Requirements Document
    prd-validation-report-*.md
    ux-design-specification.md   # Complete UX spec (14 steps)
    ux-color-themes.html         # Colour theme visualiser
    ux-design-directions.html    # Design direction mockups
Project Brief/            # Original project brief and research documents
```

## The Five Moves

1. **Orientation** — The system introduces itself. Maximum emptiness, minimum information
2. **Eligibility** — Clinical triage. Not everyone should proceed. Some are redirected out
3. **Declaration** — The user states what they're deciding, owns it, acknowledges consequences
4. **Sufficiency** — Three constrained fields: what's enough, what's excluded, what's risked
5. **Stop/Go** — The stamp falls. Defence prompt, downside acknowledgement, final commitment or abandonment

After commitment: **Exit Silence** (the system goes quiet), **Artefact** (immutable transcript), **Calibration Coda** (optional reflection prompts).
