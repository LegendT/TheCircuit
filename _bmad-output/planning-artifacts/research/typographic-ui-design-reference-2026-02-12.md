# Typographic UI Design Reference — The Circuit

**Purpose:** Comprehensive design reference for outstanding typographic, minimal, and contemplative UI design. Compiled to inform the visual and interaction design of The Circuit — a constrained professional decision-making tool using near-monochrome typography (Source Serif 4, variable weight 200–900) on a warm off-white surface.

**Date:** 2026-02-12

---

## 1. Exemplary Minimal/Typographic Web Interfaces

### iA Writer — The Gold Standard for Typographic Austerity

**What they do:** iA Writer's website and application are the canonical reference for "the text is the product." The entire interface is a single typeface (iA Writer Duo/Quattro, their custom monospace and proportional families), a single column, and almost nothing else. No toolbar visible by default. No formatting options in the default view. No sidebar. The blank page is the interface.

**What makes it exceptional:**

- **Custom typeface as product identity.** iA commissioned their own type families (iA Writer Mono, Duo, Quattro) — the typeface IS the brand. Every character has been optimised for on-screen reading at the specific sizes the app uses. This is the most expensive and most effective way to achieve typographic distinction.
- **Disappearing chrome.** Menu bars, word counts, formatting — all hidden by default. The user sees their words and nothing else. Chrome appears on hover or through keyboard shortcuts and disappears again. The interface literally fades away.
- **Focus mode as spatial narrowing.** When activated, all text except the current sentence dims to near-invisible. The effect is a spatial density change within a single view — the cognitive field narrows without the content moving. This is directly analogous to The Circuit's density arc.
- **Typography as the only design element.** No colour. No icons (minimal). No imagery on the writing surface. Hierarchy is achieved through size, weight, and opacity — nothing else. The website carries this through: their marketing pages are heavily typographic with extreme whitespace.
- **The "Do" philosophy.** iA's content philosophy is "writing is not about looking at text, it's about looking *through* text." The interface must be transparent. Every pixel of chrome is a pixel between the writer and their thought. For The Circuit: every pixel of UI is a pixel between the user and their decision.

**Relevance to The Circuit:** iA Writer is the primary implementation reference for field design across all circuit states. The input fields should inherit this austerity: no formatting, no character count, no save button. The user's words are the only visual element that matters.

---

### Linear — Precision Through Restraint

**What they do:** Linear is a project management tool that achieved cult status through visual design quality. Their interface uses a dark, near-monochrome palette with Inter as the primary typeface, extreme information density managed through consistent spacing, and micro-interactions that feel engineered rather than designed.

**What makes it exceptional:**

- **Consistent spatial rhythm.** Every element in Linear sits on an implicit 4px grid. The padding inside cards, the gap between list items, the margin around sections — everything snaps to multiples of 4. This creates a subliminal sense of precision that users feel but cannot articulate. The result is an interface that feels "right" without any visible grid lines.
- **Monochrome hierarchy through opacity.** Linear achieves 4-5 levels of visual hierarchy using a single text colour at different opacity levels: primary text at 100%, secondary at 60-70%, tertiary at 40%, ghost/disabled at 20-25%. No additional colours are needed for hierarchy. The system achieves "information architecture through transparency."
- **Type scale discipline.** Linear uses approximately 5-6 font sizes across the entire application. The restraint is remarkable — most apps of similar complexity use 10+. Each size has a specific semantic purpose, and sizes never bleed between purposes.
- **Animation as communication.** Transitions in Linear are 120-200ms, ease-out. Fast enough to feel instant, slow enough to convey state change. Nothing bounces. Nothing overshoots. The animation vocabulary is "precise mechanical movement," not "organic delight."
- **Information density without clutter.** Linear shows more information per viewport than most competitors but feels emptier. The mechanism: consistent spacing, restrained type scale, and colour discipline create visual "air" even when content density is high.

**Relevance to The Circuit:** Linear's opacity-based hierarchy is directly applicable to the `--ink` / `--system` / `--recessive` token system. Their spatial rhythm discipline should inform the spacing token scale. Their animation philosophy (precise, fast, no bounce) aligns with the bell transition.

---

### Stripe's Documentation — The Standard for Technical Typography

**What they do:** Stripe's documentation is widely regarded as the best-designed technical documentation on the web. It uses a custom type system (built around a system font stack with custom display headings), generous margins, and a reading-optimised single-column layout with a persistent sidebar for navigation.

**What makes it exceptional:**

- **Measure control.** Body text in Stripe docs maxes out at approximately 680px / ~72 characters per line. This is textbook optimal measure for sustained reading. The content column does not expand to fill available width on large screens — it holds its measure with generous margins on either side.
- **Heading hierarchy through weight and spacing.** Stripe uses 3-4 heading levels, differentiated primarily through font-weight and margin-top. H2s get significantly more top margin than H3s, creating clear section boundaries without rules or dividers. The spacing IS the hierarchy.
- **Code/prose distinction.** Technical documentation has a unique challenge: mixing prose and code. Stripe differentiates these through background colour (subtle grey for code blocks), typeface (monospace for code, proportional for prose), and spatial treatment (code blocks get additional vertical padding). The distinction is immediate without being jarring.
- **Colour used structurally, never decoratively.** Links are a distinct colour. Code language labels use colour. Error states use colour. Nothing else does. The restraint prevents colour from competing with the text.
- **Performance typography.** Stripe docs load fast because they use system fonts for body text (eliminating font-loading latency) and reserve custom fonts for headings and marketing. This is a deliberate trade-off: maximum reading performance over maximum typographic distinction.

**Relevance to The Circuit:** Stripe's measure control (the max-width content column) should inform the `min(100% - 2 * var(--space-m), 42.5rem)` calculation. Their heading hierarchy through spacing-not-decoration validates the artefact's structural approach. The artefact section headings should follow Stripe's pattern: weight + generous margin-top = section boundary.

---

### Bear App — Warmth in Minimalism

**What they do:** Bear is a notes application for Apple platforms that achieves a warm, inviting writing environment through careful typography and colour treatment. It uses Avenir Next as the interface typeface and offers multiple editor typefaces, with a distinctive red accent colour against a warm white or cream surface.

**What makes it exceptional:**

- **Warm surface temperature.** Bear's default light theme uses a warm white (similar to The Circuit's `--surface`) rather than pure white. This seemingly minor choice dramatically affects the emotional register of the entire interface — it reads as "paper" rather than "screen," "calm" rather than "clinical."
- **Single accent colour.** Bear uses a single accent colour (a warm red-orange) for interactive elements, tags, and link text. Everything else is monochrome. The accent does double duty: it signals interactivity AND provides the brand's entire visual identity. One colour, maximum recognition.
- **Typography that encourages writing.** Bear's default editor uses generous line-height (approximately 1.6-1.7), comfortable font size (16-17px), and soft grey for markdown syntax characters. The effect: markdown formatting is visible but recessive, and the user's prose dominates. System syntax yields to user content.
- **Progressive disclosure of complexity.** Tags, export options, sync — all present but none visible in the writing view. The note surface is clean. Complexity exists in the sidebar and menu bar, never on the page.

**Relevance to The Circuit:** Bear's warm surface temperature validates the `oklch(0.98 0.005 80)` choice. Their single-accent-colour strategy maps to the `--accent` token. Their treatment of syntax characters (visible but recessive) is a direct reference for how system prompts and field labels should render — present but subordinate.

---

### Notion — Typography Under Load

**What they do:** Notion is a workspace tool that must handle everything from personal notes to company wikis. Its typographic system carries enormous load — supporting databases, Kanban boards, calendars, documents, and embedded content within a unified visual language.

**What makes it exceptional:**

- **Content-type-aware typography.** Notion adjusts its typographic treatment based on content type. A full-page document gets generous margins and large type. A database view gets compressed type and tight spacing. A Kanban board gets card-sized type. The same type system flexes across radically different densities — relevant because The Circuit needs this exact flex across the density arc.
- **Cover images and icons as emotional signals.** Notion pages can have cover images and page icons. These are cosmetic — they carry no information. But they transform the emotional register of a page from "document" to "place." The lesson: even in a minimal interface, one or two non-functional visual elements can establish an emotional environment. The Circuit's equivalent might be the spatial density itself.
- **Typographic conventions as UI patterns.** Notion uses type conventions instead of traditional UI elements. A `/` command replaces a toolbar. `@` mentions replace a people picker. `[[` links replace a file browser. Type IS the interface. Commands are typed, not clicked.
- **The "empty state" problem.** Notion handles the blank page with placeholder text: "Type '/' for commands." This transforms an intimidating void into an entry point. The Circuit's orientation scaffold ("Do I...") serves the same function — bridging the blank page without filling it.

**Relevance to The Circuit:** Notion's density-adaptive typography confirms that a single type system can serve radically different spatial environments — exactly what the density arc requires. Their placeholder-as-scaffold pattern validates the orientation approach.

---

### Medium — The Reading Experience as Product

**What they do:** Medium's primary product is the reading experience. Their entire design system is optimised for one activity: reading long-form prose on a screen. The writing interface mirrors this — what you write is what readers see.

**What makes it exceptional:**

- **Measure and line-height as first-class design.** Medium uses a content column of approximately 680-700px with 1.58 line-height (body text). These are not defaults — they are the result of extensive research and testing for optimal screen reading. The line-height is notably higher than print conventions (1.2-1.4) because screens require more leading for comfortable reading.
- **Typography progression on scroll.** The reading experience has subtle typographic modulation: the title is large, the subtitle is lighter, the byline is smaller, then the body settles into its reading rhythm. This "typographic invocation" — from large/attention to settled/reading — takes the reader through a state change in the first viewport. The Circuit could use a similar progression at state entry.
- **Estimated reading time as constraint signal.** Medium shows "5 min read" at the top of every article. This is a constraint — it sets expectations, creates a time boundary. The Circuit doesn't show time estimates, but the psychological mechanism is identical: the user knows this is bounded, not infinite.
- **Highlight and response as marginalia.** Medium's highlighting feature treats the reader's engagement as a typographic event — their marks appear as coloured underlines within the author's text. The reader's layer and the author's layer coexist typographically. In The Circuit, the user's text and the system's prompts occupy different typographic registers but share the same surface.
- **The "clap" as non-verbal response.** Medium's response mechanism is intentionally non-verbal — a clap, not a comment. This is relevant to The Circuit's exit silence: the appropriate response to testimony is not words. The system's silence at exit IS the response.

**Relevance to The Circuit:** Medium's line-height research (1.58 for screen reading) should inform body text line-height. Their content column width validates the 42.5rem target. Their typographic invocation (large→settled) suggests that each circuit state should have a brief typographic settling as the page renders.

---

### Arc Browser (The Browser Company) — Chrome That Disappears

**What they do:** Arc is a browser that radically reimagines browser chrome. The URL bar, tabs, and bookmarks are hidden by default. The content — the web page — fills the entire viewport. Chrome appears when needed (hover, keyboard shortcut) and vanishes again.

**What makes it exceptional:**

- **Full-viewport content as default.** Arc treats browser chrome the way iA Writer treats editor chrome: as interference. The default state is "you and the content." Everything else is an interruption to be minimised. This is philosophically identical to The Circuit's full-viewport states.
- **Spatial zones replace visual boundaries.** Instead of visible dividers between browser sections, Arc uses spatial zones — areas of the screen that respond differently to hover. The boundary is implicit, not drawn. For The Circuit: section boundaries in the artefact might use spatial separation (generous padding) rather than visible rules.
- **The "boost" customisation model.** Arc lets users customise how specific websites render — changing colours, hiding elements, adjusting type size. The mechanism: CSS injection. The principle: the user's reading preferences override the designer's intentions. The Circuit should never need this because its typography is already optimised for reading — but it validates the principle that reading comfort is paramount.

**Relevance to The Circuit:** Arc's full-viewport-content-as-default validates the separate-pages architecture. Their invisible boundaries through spatial zones inform the artefact section containment strategy.

---

### Readwise Reader — Reading as Environment

**What they do:** Reader is a read-it-later app that treats reading as an environment, not a feature. The reading view strips away navigation, adjusts typography to the content type, and provides annotation tools that feel like physical marginalia.

**What makes it exceptional:**

- **Content-type-aware rendering.** PDFs, articles, newsletters, and books all render differently. Each content type gets its own typographic treatment optimised for that format. The system adapts to the content, not the reverse. For The Circuit: different states might merit slightly different typographic weights within the same family.
- **Focus mode that compresses the visual field.** Reader's focus mode narrows the viewport, increases margins, and dims non-essential UI. The reading column becomes a vertical strip of text in a sea of emptiness. This is the most direct digital analogue to The Circuit's density arc — spatial compression as focus mechanism.
- **Highlighting as dialogue.** Reader treats highlights as a conversation between the reader and the text. Highlights are colour-coded, tagged, and exportable. The reader's engagement becomes a first-class typographic element layered over the source text.

**Relevance to The Circuit:** Reader's content-type-aware rendering validates the dual-token architecture (circuit fluid / artefact fixed). Their focus mode's spatial compression is a direct reference for the Sufficiency state's density.

---

### Substack — Document as Product

**What they do:** Substack is a publishing platform where the written document IS the product. The reading experience is intentionally simple: one column, generous margins, clean serif typography, minimal navigation. The newsletter format — a letter from one person to their subscribers — shapes every design decision.

**What makes it exceptional:**

- **Personal voice through typographic framing.** Substack uses serif typography for body text (typically Georgia or a custom serif), which carries cultural associations with personal writing, books, and letters. The serif choice signals "this is authored by a person" rather than "this is produced by a platform." For The Circuit: Source Serif 4 carries exactly this association — the user's words should feel authored, not entered.
- **The email as canonical format.** Substack newsletters land in the inbox first. The web view is secondary. This means the typography must work in the most constrained environment imaginable — email clients with limited CSS support. The lesson: constraints produce clarity. When you cannot use complex typography, you rely on measure, leading, and weight — the fundamentals. The Circuit's near-monochrome constraint forces the same reliance on fundamentals.
- **Minimal metadata.** A Substack post has a title, author, date, and body. Sometimes an image. That's the entire structure. No categories, no tags, no related posts widget, no comments section on the initial view. The metadata serves the document — it doesn't compete with it. The artefact should follow this pattern: name, date, decision, body. Minimal metadata, maximum document.

**Relevance to The Circuit:** Substack's serif-as-personal-voice validates Source Serif 4. Their minimal metadata model is a direct reference for artefact header design. Their constraint-forced-clarity principle mirrors the near-monochrome palette.

---

### Summary: Cross-Product Patterns

| Pattern | Products That Exhibit It | Circuit Application |
|---------|------------------------|-------------------|
| Text as the only visual element | iA Writer, Bear, Substack | All circuit states — user text dominates |
| Opacity-based hierarchy | Linear, Bear | `--ink` / `--system` / `--recessive` tokens |
| Warm surface temperature | Bear, Substack | `--surface: oklch(0.98 0.005 80)` |
| Measure-controlled content column | Stripe, Medium, Substack | `min(100% - 2 * var(--space-m), 42.5rem)` |
| Disappearing chrome | iA Writer, Arc | No persistent UI in circuit states |
| Spatial density as emotional signal | iA Writer (focus mode), Notion, Reader | The density arc |
| Single accent colour | Bear | `--accent` token |
| Content-type-aware typography | Notion, Reader | Dual token architecture |
| Placeholder as scaffold | Notion | "Do I..." orientation placeholder |
| Silence as response | Medium (clap as non-verbal) | Exit silence |

---

## 2. Visual Hierarchy With Monochrome Palettes

### The Problem

Most digital interfaces rely on colour as the primary hierarchy signal: blue for links, red for errors, green for success, grey for disabled. Remove colour and the hierarchy collapses. The Circuit cannot use these conventions — it has no "success" state, no "error" state in the traditional sense. It has testimony, structure, and silence. The hierarchy must be built from typographic properties alone.

### The Seven Hierarchy Mechanisms (No Colour Required)

**1. Weight — The Primary Axis**

In a single-family variable font system (Source Serif 4, 200–900), weight is the most powerful hierarchy tool. The eye processes weight differences before size differences — a 600-weight heading at 18px reads as "more important" than a 300-weight heading at 20px. Weight communicates importance directly.

*Application to The Circuit:*
- User text (record mode): weight 500 — the dominant visual element
- User text (input mode): weight 400 — active, composing
- System prompts: weight 300 — subordinate, recessive
- Artefact headings: weight 600 — structural authority
- Redirect copy: weight 400 italic — distinct register, not subordinate

**Best practice:** The minimum perceptible weight difference is approximately 100 units on a standard variable font axis. A shift from 400 to 500 is subliminal (felt, not seen). A shift from 300 to 600 is supraliminal (immediately visible). The Circuit uses both: input→record is subliminal; system→user-text is supraliminal.

---

**2. Size — The Secondary Axis**

Size establishes structural hierarchy: headings vs. body vs. captions. But size alone, without weight differentiation, creates a monotonous hierarchy. The combination of size + weight produces compound hierarchy levels.

*Application to The Circuit:*
- Utopia fluid type scale with ~1.2 (minor third) ratio
- User body text: base size (clamp, 1rem–1.25rem)
- System prompts: one scale step below body
- Artefact headings: one scale step above body
- Artefact body: one additional step above circuit body (the quality jump)

**Best practice:** A typographic scale ratio of 1.2 (minor third) produces subtle, refined differences between levels. A ratio of 1.25 (major third) produces more dramatic jumps. For The Circuit's understated aesthetic, 1.2 is correct. Ratios above 1.333 (perfect fourth) feel editorial or magazine-like — wrong register for testimony.

---

**3. Opacity / Value — The Tertiary Axis**

Opacity controls the "volume" of text without changing its colour. In a monochrome palette, this is functionally equivalent to greyscale variation but with the advantage of maintaining the base colour's warmth.

*Application to The Circuit:*
- `--ink` at full opacity: user text, redirect copy
- `--system` (reduced lightness): system prompts, field labels
- `--recessive` (further reduced lightness): placeholder text, disabled states
- `--boundary` (near-surface): structural lines, section dividers

**Best practice from Linear's design system:** Limit opacity levels to 4-5 distinct values. More than 5 levels of typographic opacity creates ambiguity — the viewer cannot reliably distinguish adjacent levels. The Circuit uses exactly 4 text levels (ink, system, recessive, boundary) plus the surface.

---

**4. Spacing — The Structural Axis**

Spacing communicates grouping, separation, and importance without any visual mark. More space above a heading = stronger section break. Less space between items = tighter grouping. In a monochrome system, spacing does the work that colour-coded backgrounds and dividers do in polychromatic systems.

*Application to The Circuit:*
- Heading margin-top: the primary section break signal (more space = bigger break)
- Field padding: density arc signal (more padding = more spacious state)
- Content column margins: reading comfort signal (more margin = more premium feel)
- Gap between artefact sections: screenshot-ability signal (enough gap that a section, when cropped, has its own breathing room)

**Design principle (Gestalt proximity):** Elements that are closer together are perceived as belonging together. In the Sufficiency state, the three fields (enough, excluded, risk) should have tighter internal spacing (they're a group) and more generous external spacing (they're isolated from system chrome). The grouping IS the instruction — the layout says "these belong together" without the system needing to say it.

---

**5. Style — The Register Axis**

Italic, small caps, letterspacing — these create typographic register differences that signal "this is a different kind of text" without changing size, weight, or colour.

*Application to The Circuit:*
- Italic: redirect copy — the system's procedural voice, distinct from both user text and system labels
- Small caps: timestamps in the artefact — factual metadata, distinct from body text
- Letterspacing: page headings or state names — if ever displayed (currently the system avoids naming states to the user, but this may apply to the artefact's section headings)

**Best practice:** Source Serif 4's italic forms are true italics (drawn separately, not slanted romans). True italics create a genuine register shift — the reader perceives a change of voice, not just a visual tweak. Slanted (oblique) forms lack this distinction. The Circuit's redirect copy relies on this register shift: "That describes a collective decision. What are *you* deciding?" is the system speaking in a different voice, not emphasising words within its normal voice.

---

**6. Position — The Spatial Axis**

Where text sits on the viewport communicates importance and role. Centred text reads as a heading or statement. Left-aligned text reads as body copy. Right-aligned text reads as metadata. In a full-viewport single-column layout, vertical position within the viewport is the primary positional signal.

*Application to The Circuit:*
- User text: positioned in the optical centre of the viewport (slightly above geometric centre — approximately 45% from top) — the most visually dominant position
- System prompts: above the input field — structurally preceding, visually subordinate
- Finality line: vertically centred — statement, not body copy
- Artefact export controls: below the artefact body — service, not content
- Timestamp: right-aligned or small caps below the commitment — metadata, not testimony

**Best practice (optical centre):** Geometric centre (50/50) feels visually low because the human eye weighs the top half of a surface more heavily. Optical centre sits at approximately 44-47% from the top edge. Place the most important element at the optical centre; less important elements above and below it.

---

**7. Contrast of Absence — The Silence Axis**

The most powerful hierarchy signal in a monochrome system is the contrast between content and its absence. Whitespace around an element elevates it. Isolation IS hierarchy. A single line in a vast viewport is the loudest thing in the interface — not because it's big or bold, but because everything else is absent.

*Application to The Circuit:*
- Exit silence: the finality line dominates because everything else is absent. Maximum contrast of absence.
- Orientation: the scaffold placeholder in generous whitespace — the input field's isolation signals "this is the only thing that matters right now."
- Sufficiency's exclusion field: visually elevated through isolation (more surrounding space than the "enough" field) — breathing room as emphasis.

**Design principle:** In a monochrome typographic system, the loudest design tool is not bold — it is empty space. The hierarchy goes: isolated element > bold element > large element > bright element. The Circuit's emotional peaks (exit silence, the exclusion field, the commitment moment) should all be moments of maximum isolation, not maximum visual weight.

---

### Hierarchy Stack for The Circuit

| Level | Mechanism | Token/Property | Usage |
|-------|-----------|---------------|-------|
| 1 (loudest) | Isolation + weight | `--ink`, weight 500, vast whitespace | Finality line, user Declaration |
| 2 | Weight + size | `--ink`, weight 600, heading size | Artefact section headings |
| 3 | Weight + normal spacing | `--ink`, weight 500, body size | User text (record mode) |
| 4 | Weight + comfort | `--ink`, weight 400, body size | User text (input mode) |
| 5 | Style change | `--ink`, weight 400, italic | Redirect copy |
| 6 | Reduced value | `--system`, weight 300 | System prompts, field labels |
| 7 | Further reduced value | `--recessive`, weight 300 | Placeholder text, scaffold |
| 8 (quietest) | Structural only | `--boundary` | Section dividers, artefact rules |

---

## 3. Density and Spacing as Emotional Design

### The Principle

Spatial density — the ratio of content to empty space within a viewport — is an emotional signal. Dense layouts feel urgent, constrained, close. Spacious layouts feel calm, open, expansive. This is not metaphorical — it is a physiological response. Dense visual environments activate higher cognitive load, trigger focused attention, and increase arousal. Spacious environments reduce cognitive load, enable diffuse attention, and lower arousal.

The Circuit uses this as a narrative arc: density that compresses through the circuit's crucible states and then opens into vast emptiness at exit. The user *feels* the decision becoming more serious through spatial compression, and *feels* the release through spatial expansion.

### Research and Precedent

**Architecture and Environmental Psychology**

The spatial density arc has direct parallels in architecture. Architects use ceiling height, corridor width, and room volume to create emotional journeys through buildings. Frank Lloyd Wright's compression-and-release technique — low ceilings in transitional corridors, soaring ceilings in living spaces — creates emotional transitions that visitors feel in their bodies, not just their eyes. The Japanese concept of *ma* (negative space as meaning-carrier) treats emptiness as an active design element, not a passive absence.

Alvar Aalto's courthouses use a deliberate spatial sequence: a generous entrance hall (orientation, grounding), a narrowing corridor (transition, focus), a compact courtroom (testimony, constraint), and a release space beyond (resolution, exit). The Circuit's density arc mirrors this almost exactly.

**Digital Precedents**

- **Typeform** uses generous whitespace around each question, with the ratio of question-to-whitespace communicating cognitive weight. A simple "What's your email?" sits in moderate whitespace. A complex "Describe your experience" sits in generous whitespace. The space says "take your time" without words.
- **Headspace** uses spatial progression within meditation sessions. The instruction screen is comfortably dense (guidance text, timer, controls). The meditation screen is sparse (a single visual element, maybe a timer). The completion screen is nearly empty. The spaciousness arc tracks the user's expected state: from needing guidance, to being in practice, to being in stillness.
- **Calm** (the meditation app) goes further: the timer screen during meditation shows only a single circle and the elapsed time. The overwhelming majority of the screen is a solid colour. The visual simplicity is itself a meditation instruction — "there is nothing to look at." This is The Circuit's exit silence: the visual emptiness IS the emotional communication.

### The Circuit's Density Arc — Technical Implementation

```
Orientation  ████░░░░░░░░░░░░░░░░  ~20% content density
Eligibility  ██████░░░░░░░░░░░░░░  ~30% content density
Declaration  █████████░░░░░░░░░░░  ~45% content density
Sufficiency  █████████████░░░░░░░  ~65% content density
Stop/Go      █████░░░░░░░░░░░░░░░  ~25% content density
Exit silence ██░░░░░░░░░░░░░░░░░░  ~10% content density
```

The density is achieved through three mechanisms:

1. **Padding tokens per state.** Each state's container uses different padding values from the spacing scale. Orientation uses `--space-xl` to `--space-3xl`. Sufficiency uses `--space-s` to `--space-m`. The tokens compress.

2. **Content volume.** Orientation has one field. Sufficiency has three fields plus structural labels. More content in the same viewport = higher density. The content count increases naturally with the circuit's demands.

3. **Peripheral emptiness.** The margins around the content column stay constant. What changes is the ratio of content to empty space within the column. At Orientation, one question floats in a sea of whitespace. At Sufficiency, three fields fill most of the vertical space. The column width doesn't change — the fill does.

### Emotional Mapping of Density

| Density Level | Emotional Register | Physiological Response | The Circuit's Application |
|---------------|-------------------|----------------------|--------------------------|
| Very sparse (~10%) | Solitude, vastness, stillness | Low arousal, diffuse attention, respiratory settling | Exit silence — the user is alone with their decision |
| Sparse (~20%) | Safety, invitation, openness | Low-moderate arousal, comfortable attention | Orientation — the room is wide open, the user is arriving |
| Moderate (~30%) | Focus, narrowing, purpose | Moderate arousal, directed attention | Eligibility — the room is narrowing, the system is assessing |
| Moderate-dense (~45%) | Constraint, pressure, exposure | Higher arousal, heightened attention | Declaration — the room has focus, the user is exposed |
| Dense (~65%) | Crucible, urgency, compression | High arousal, concentrated attention | Sufficiency — the user is in the narrowest part of the arc |
| Moderate-sparse (~25%) | Release, clarity, resolution | Arousal declining, attention broadening | Stop/Go — the room breathes again, the decision crystallises |

### Principles for Spacing as Emotional Design

1. **Density should change across states, not within them.** Each state has a fixed spatial character. The user should not see spacing animate or shift while they're in a state. The change happens at the bell transition — one state's density is replaced by the next. Animated density changes within a state would feel anxious, not purposeful.

2. **The compression-release arc should be asymmetric.** The compression happens gradually over three states (Orientation → Eligibility → Declaration → Sufficiency). The release happens in one jump (Sufficiency → Stop/Go). Asymmetric arcs feel more natural than symmetric ones — the build-up is slow, the release is sudden. Like a held breath.

3. **Content volume and padding should compound, not contradict.** At Sufficiency (densest), the padding compresses AND the content volume increases. Both mechanisms push toward density simultaneously. If the padding compressed but the content volume stayed low, the effect would be "cramped but empty" rather than "full and focused." The mechanisms must reinforce each other.

4. **The exit density should be lower than the entry density.** Orientation is spacious. Exit silence is *more* spacious. The user ends in a state that is emptier than where they started. This prevents the feeling of "returning to the beginning" — the exit is not a return, it is a release into something new. The arc is not circular; it's directional.

5. **Density is about vertical rhythm, not horizontal width.** The content column stays the same width throughout. What changes is how much vertical space surrounds each element. This is implemented through padding-block and gap values, not through padding-inline or width changes. Horizontal changes would feel like the layout is breaking. Vertical changes feel like breathing.

---

## 4. Document-Grade Typography in Web

### What "Document-Grade" Means

The Circuit generates a "decision record artefact" that should look like a professional legal, notarial, or executive document. "Document-grade" means the typography achieves the quality level of a well-typeset printed document — not a web page trying to look like a document, but a document that happens to be rendered in a browser and exported as PDF.

The distinction is in the details. Web typography defaults (system fonts, minimal line-height, no typographic refinements) produce output that reads as "web." Document-grade typography (considered typeface, deliberate line-height, proper measure, optical sizing, refinements like hanging punctuation) produces output that reads as "designed."

### Properties of Professional Document Typography

**1. Typeface Selection**

Professional documents overwhelmingly use serif typefaces. The cultural association is deep: serifs signal authority, tradition, credibility, permanence. The specific serif matters.

- **Old-style serifs** (Garamond, Caslon, Bembo): traditional, literary, personal. Best for: letters, personal essays, literary documents.
- **Transitional serifs** (Baskerville, Georgia, Source Serif): balanced authority and readability. Best for: professional documents, reports, records. **This is The Circuit's category.**
- **Modern serifs** (Didot, Bodoni): high contrast, editorial, dramatic. Best for: magazine headings, fashion, luxury. Wrong register for testimony.
- **Slab serifs** (Clarendon, Rockwell): mechanical, authoritative, sturdy. Best for: technical manuals, headings. Too utilitarian for testimony.

Source Serif 4 is a transitional serif designed explicitly for screen reading. It bridges print tradition and screen optimisation — exactly what a web-rendered professional document requires.

**2. Measure (Line Length)**

Professional print documents set body text at 45-75 characters per line. The optimum is approximately 66 characters (Robert Bringhurst, *The Elements of Typographic Style*). On screen, where reading is harder, the optimum narrows to approximately 55-70 characters.

*For The Circuit's artefact:*
- Content column: `min(100% - 2 * var(--space-m), 45rem)` — targeting approximately 60-65 characters per line at the artefact's fixed type size
- This is slightly wider than the circuit's content column (42.5rem) to accommodate the artefact's larger type size while maintaining optimal measure

**3. Line Height (Leading)**

Print documents use 120-145% leading (1.2-1.45 line-height). Screen documents need more: 140-170% (1.4-1.7). The reason: screen rendering is lower contrast than print, and vertical spacing compensates by giving the eye clearer "lanes" to follow.

*For The Circuit's artefact:*
- Body text: `line-height: 1.55` — within the sweet spot for screen reading of longer passages
- Headings: `line-height: 1.2` — tighter, because headings are short and benefit from compactness
- Metadata (date, timestamp): `line-height: 1.3` — compact, subordinate

**4. Margins**

Professional documents use generous margins — not because there's nothing to put there, but because the margins are functional. They frame the text block, give the eye a resting place at the end of each line, and create the "document object" feeling — the sense that this is a considered artefact, not content flowing to fill available space.

Traditional document margins: 1-1.5 inches on all sides. On screen, this translates to generous padding-inline on the content column.

*For The Circuit's artefact:*
- Margins should be noticeably wider than the circuit states' margins, contributing to the quality jump
- The margins say: "this is a document, not a form printout"

**5. Paragraph Treatment**

Professional documents use one of two paragraph separation methods:
- **First-line indent** (no paragraph spacing): traditional, book-like, continuous reading. Best for long-form prose.
- **Block paragraphs** (no indent, paragraph spacing): modern, business-like, scannable. Best for reports, memos, records.

*For The Circuit's artefact:*
- Block paragraphs with `margin-block-end` spacing — the artefact is a professional record, not a literary work. Block paragraphs are appropriate for the register.

**6. Heading Hierarchy in Documents**

Professional documents differentiate heading levels through a combination of:
- Size step (one scale step per heading level)
- Weight increase (600 for major headings, 500 for minor)
- Spacing above (more space = stronger section break)
- Optional rule or accent (a thin line below a heading signals structural division)

*For The Circuit's artefact:*
- Section headings: weight 600, `--accent` underline rule, generous margin-block-start
- No more than 2 heading levels — the artefact is structured by the circuit's states, not by sub-sections within them
- The heading treatment should use the `--accent` colour for the underline rule — this is the only non-monochrome element in the artefact and signals structural importance

**7. Typographic Details That Signal "Professional"**

| Detail | What It Does | CSS Property |
|--------|-------------|-------------|
| Hanging punctuation | Opening quotes and bullet points extend into the margin, keeping the text edge optically aligned | `hanging-punctuation: first last` |
| Proper quotation marks | Curly quotes instead of straight quotes — a hallmark of typeset text | Content processing (not CSS) |
| En/em dashes | Proper dash characters instead of hyphens | Content processing |
| Small caps for abbreviations | "PDF" rendered in small caps reads as refined typography | `font-variant-caps: small-caps` or `font-feature-settings: "smcp"` |
| Oldstyle figures in body text | Numerals that sit on the baseline with ascenders and descenders, integrating with body text | `font-variant-numeric: oldstyle-nums` |
| Lining figures in headings | Numerals that all sit on the baseline at cap height, appropriate for headings and tables | `font-variant-numeric: lining-nums` |
| Ligatures | Connected letter pairs (fi, fl) that smooth reading | `font-variant-ligatures: common-ligatures` |
| Optical sizing | The typeface adjusts its design details based on the rendered size — thinner strokes at large sizes, sturdier strokes at small sizes | `font-optical-sizing: auto` |

**8. The Quality Jump — From Input to Document**

The artefact must look visibly *better* than the input experience. This is achieved through three simultaneous signals:

1. **Type size step up.** The artefact body renders one Utopia scale step larger than the circuit body. The user's words are literally bigger in the document than they were in the input field.

2. **Wider margins.** The artefact column is wider than the circuit column, but the text block within it is proportionally narrower relative to the page. This creates more margin — the hallmark of document-grade typography.

3. **Structural accent work.** The `--accent` colour appears in section heading underlines, providing visual structure that does not exist in the circuit states. The circuit is monochrome. The artefact has one structural colour.

The quality jump should be visible and immediate. When the user scrolls from the exit silence to the artefact, the shift from "sparse interface" to "professional document" must be felt as an elevation — "my words look serious now."

---

## 5. Full-Viewport Typographic Layouts

### What "Text IS the Interface" Means

In a full-viewport typographic layout, text is not contained within interface elements — it IS the interface element. There are no sidebars, no persistent navigation, no header bars, no footers. The text sits directly on the surface. The only visual elements are the text, the surface, and the space between them.

This is the default state for every circuit page in The Circuit. Each state is a full-viewport environment where the user's text (or the system's prompt) occupies the centre, and everything else is either absent or invisible.

### Where This Works — Successful Examples

**Poetry Websites and Literary Journals**

Sites like *Poetry Foundation*, *The Paris Review* (reading view), and individual poet websites frequently use full-viewport typographic layouts. A poem on a screen: centred text, generous whitespace, nothing else. These work because:

- The content is short enough to fit in a single viewport (or close to it)
- The reader expects to spend time with the text, not to scan it
- The whitespace is itself meaningful — it signals "this text deserves contemplation"
- There is no competing content — no sidebar, no "related poems," no ads

**Reading Mode in Browsers**

Safari's Reader Mode, Firefox's Reader View, and Arc's "Boost" presets all do the same thing: strip a web page down to its text and serve it in a clean, single-column, full-viewport layout. The universal pattern:

- Remove all navigation, headers, footers, and sidebars
- Set a readable measure (typically 38-42rem / 600-680px)
- Use a comfortable type size (16-20px)
- Set generous line-height (1.5-1.7)
- Warm or neutral background (not pure white)
- No interactive elements except scroll

The fact that every major browser has built a reading mode that strips interfaces down to "text on a surface" validates the core premise: for focused reading and writing, the best interface is no interface.

**Writing Tools in Focus/Zen Mode**

iA Writer, Ulysses, Typora, Obsidian (when configured), and VS Code's Zen Mode all offer a full-viewport writing environment. The patterns:

- Content centred in the viewport with generous margins
- Typing cursor as the primary interactive element
- Word count and metadata hidden or minimally displayed
- Keyboard shortcuts for everything — no need to reach for UI controls
- Exit from focus mode via Escape key

**Digital Art Galleries**

Sites for photographers, artists, and type foundries frequently use full-viewport layouts for individual works. Each piece fills the screen. Navigation is at the edges or hidden. The work is the interface.

### What Makes Full-Viewport Typography Succeed

**1. The Text Must Be Worth the Space**

A full-viewport layout makes a promise: "what you're reading is important enough to deserve your entire screen." If the text doesn't deliver on that promise — if it's generic, trivial, or could be a sidebar note — the empty space reads as waste, not intention. The Circuit's text earns the space: every prompt is consequential, every user response is testimony.

**2. Measure Must Be Precisely Controlled**

Without sidebars or other elements to constrain the text block, the content column must set its own width. If the text runs to the full width of a large screen (160+ characters per line), readability collapses. If the text is pinched too narrow on a small screen, the column feels fragile. The measure must be:

- Capped: `max-width: 42.5rem` (approximately 65 characters)
- Floored: the text never gets narrower than the mobile viewport minus comfortable margins
- Expressed as `min()`: `min(100% - 2 * var(--space-m), 42.5rem)` — fluid down, capped up

**3. Vertical Position Matters More Than Horizontal**

In a full-viewport layout, where the text sits vertically determines its emotional register:

- **Top third:** header, subordinate. Text here feels like a label or title — introductory, not the main event.
- **Optical centre (42-47% from top):** dominant, important. This is where the primary content should sit — the user's input field, the finality line, the commitment prompt.
- **Lower third:** metadata, service. Text here feels like a footnote — supporting, not central.
- **Evenly distributed (centred with equal top/bottom space):** statement, declaration. This is appropriate for the finality line: "There is nothing else. This decision is yours now."

**4. Entry and Exit Must Be Managed**

A full-viewport layout has no visible navigation. The user needs to know:
- How they arrived (bell transition — the previous state faded, this state appeared)
- What to do (the content itself — a prompt, a field, a statement)
- How to leave (submit the text, make the choice, scroll to continue)

Without these signals, a full-viewport text page is a dead end. The Circuit manages this through:
- Bell transition as arrival signal
- Content as instruction (the prompt tells the user what to do)
- Submit button / scroll affordance as exit signal

**5. The Background Must Be Considered**

In a full-viewport layout, the background is the largest visual element. A jarring white (#FFFFFF) background creates eye strain. A coloured background competes with the text. The ideal: a warm, slightly tinted neutral that reads as "paper" or "surface." This is why `--surface: oklch(0.98 0.005 80)` is warm off-white — it's the background for a layout where the background IS the majority of the visual experience.

### What Makes Full-Viewport Typography Fail

**1. Empty Space That Reads as "Missing"**

If the layout's emptiness looks like the designer forgot to add content rather than choosing to remove it, the design fails. The mitigation: visual polish. The typeface must be beautiful. The spacing must be precise. The alignment must be pixel-perfect. Users read "sparse but rough" as unfinished and "sparse but polished" as intentional.

**2. No Affordance for Continuation**

A full-viewport layout with no visible next step traps the user. The exit silence addresses this by making the artefact's top edge barely visible at the bottom of the viewport — a scroll affordance that does not break the silence.

**3. Text That's Too Small for the Space**

Putting small text in a large viewport creates the wrong kind of isolation — the text looks lost, not elevated. The text size must be proportional to the viewport such that the text occupies a meaningful portion of the reader's visual field. For body text: minimum 1rem, ideally 1.125-1.25rem in a full-viewport context.

**4. Inconsistent Spacing**

In a layout with no visible structure, spacing IS the structure. If the spacing between elements is inconsistent — if the gap above a heading differs from the gap above another heading of the same level — the user perceives disorder. There are no grid lines, borders, or background colours to mask inconsistency. Every spacing decision is exposed.

**5. Failure to Differentiate States**

If every full-viewport page looks the same, the user loses the sense of progression. The density arc prevents this: each state has a visibly different spatial character. Orientation is spacious. Sufficiency is dense. Exit is vast. The user can feel the difference even if they can't name it.

---

## 6. CSS Techniques for Premium Feel

### Font Loading and Rendering

**Variable Font Loading**

```css
@font-face {
  font-family: 'Source Serif 4';
  src: url('/fonts/SourceSerif4-Variable.woff2') format('woff2');
  font-weight: 200 900;
  font-display: swap;
  font-optical-sizing: auto;
  size-adjust: 100%;          /* Fine-tune against fallback */
  ascent-override: 90%;       /* Reduce layout shift during swap */
  descent-override: 10%;
  line-gap-override: 0%;
}
```

*Key decisions:*
- `font-display: swap` shows fallback text immediately, swaps when the font loads. For a text-first product, invisible text (FOIT) is worse than a layout shift (FOUT).
- `size-adjust`, `ascent-override`, `descent-override`, `line-gap-override`: these metric override descriptors match the fallback font's metrics to the custom font, minimising the visual shift when the swap occurs. For a product where text position IS the design, minimising layout shift is critical.
- `font-optical-sizing: auto`: lets Source Serif 4 adjust its design details based on rendered size. At small sizes (system prompts), strokes thicken slightly for legibility. At large sizes (artefact headings), strokes thin for elegance. This is built into the font; the CSS activates it.

**Fallback Font Stack**

```css
--font-family: 'Source Serif 4', Georgia, 'Times New Roman', serif;
```

Georgia is the best screen serif fallback — it was designed for screen rendering and has similar proportions to Source Serif 4. The stack ensures readable text even if the custom font fails to load.

**Font Size Adjust for Fallback Matching**

```css
font-size-adjust: 0.52;  /* Match x-height ratio between Source Serif 4 and Georgia */
```

This normalises the x-height between the primary and fallback fonts, so the text occupies approximately the same vertical space during the font swap. In a layout where text position is the primary design element, this prevents jarring shifts.

---

### Typographic Refinements

**Ligatures and OpenType Features**

```css
/* Production settings for Source Serif 4 */
body {
  font-variant-ligatures: common-ligatures contextual;
  font-variant-numeric: oldstyle-nums proportional-nums;
  font-kerning: normal;
  font-optical-sizing: auto;
}

/* Artefact headings — different numeric style */
.artefact-heading {
  font-variant-numeric: lining-nums tabular-nums;
}

/* Equivalent shorthand via font-feature-settings (if needed for specificity) */
body {
  font-feature-settings: "kern" 1, "liga" 1, "clig" 1, "calt" 1, "onum" 1, "pnum" 1;
}
```

*What each does:*
- `common-ligatures`: activates fi, fl, ff ligatures — smoother reading
- `contextual`: activates context-dependent alternates — letter forms that adapt to their neighbours
- `oldstyle-nums`: numerals with ascenders and descenders (3, 4, 5 drop below baseline). Integrates numbers into body text naturally. Use in body text.
- `proportional-nums`: numerals with varying widths (1 is narrower than 0). Natural spacing in body text. Use in body text.
- `lining-nums`: uniform-height numerals at cap height. Use in headings, timestamps, metadata.
- `tabular-nums`: uniform-width numerals (all digits same width). Use in tables, aligned numbers.
- `kern`: enables the font's built-in kerning tables — letter pair spacing adjustments

**Hanging Punctuation**

```css
.artefact-body,
.circuit-input {
  hanging-punctuation: first last;
}
```

This extends opening quotation marks and punctuation into the left margin, keeping the text edge optically aligned. The effect is subtle but the perception is "professionally typeset" vs. "default." Browser support: Safari has had this for years; Chrome/Firefox support is improving. Progressive enhancement — where unsupported, punctuation stays inline (visually fine, just not elevated).

**Text Wrapping**

```css
h1, h2, h3 {
  text-wrap: balance;
}

p {
  text-wrap: pretty;
}
```

- `text-wrap: balance`: distributes text evenly across lines in headings, preventing orphaned short last lines. A heading that reads "Making Professional / Decisions" instead of "Making / Professional Decisions" is the difference between composed and careless.
- `text-wrap: pretty`: prevents orphaned single words on the last line of paragraphs. Less aggressive than balance — appropriate for body text where perfect balance would be too rigid.

**Hyphenation**

```css
.artefact-body {
  hyphens: auto;
  hyphenate-limit-chars: 6 3 2;  /* min word length, min before break, min after break */
  hyphenate-limit-lines: 2;      /* max consecutive hyphenated lines */
  hyphenate-limit-zone: 8%;      /* only hyphenate if line end falls in this zone */
}
```

Proper hyphenation produces more even line lengths, which creates a calmer text block. The limits prevent aggressive hyphenation (breaking short words, stacking hyphens on consecutive lines) that would feel mechanical.

*Note:* Use hyphenation in the artefact (document-grade output) but NOT in the circuit input fields. Input text should not be hyphenated — the user should see their words exactly as they typed them.

---

### Text Rendering

```css
body {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-rendering: optimizeLegibility;
}
```

*What each does:*
- `-webkit-font-smoothing: antialiased`: on macOS, this switches from subpixel rendering (which can look blurry at certain sizes) to greyscale antialiasing (crisper, thinner, more refined). This is the standard for premium web typography.
- `-moz-osx-font-smoothing: grayscale`: the Firefox equivalent.
- `text-rendering: optimizeLegibility`: activates kerning and ligatures. Can cause performance issues with very large text blocks — but The Circuit's text blocks are short (testimony, not novels), so this is safe.

*Caution:* `text-rendering: optimizeLegibility` can cause slowdowns on pages with extremely long text. For The Circuit, where individual text blocks are short (a few sentences to a few paragraphs), this is not a concern. Do NOT use `text-rendering: optimizeSpeed` — it disables ligatures and kerning, which are essential for document-grade output.

---

### Letter Spacing at Different Sizes

Letter spacing (tracking) should vary by size. Large text (headings) benefits from tighter tracking — the default spacing looks loose at large sizes. Small text (captions, metadata) benefits from looser tracking — the default spacing can feel cramped at small sizes.

```css
/* Heading sizes: tighten tracking */
.artefact-heading {
  letter-spacing: -0.015em;
}

/* Body text: default tracking (no adjustment) */
.artefact-body {
  letter-spacing: normal;
}

/* Small text: loosen tracking slightly */
.system-text {
  letter-spacing: 0.01em;
}

/* All-caps text (if ever used): significant loosening */
.label-caps {
  letter-spacing: 0.08em;
  text-transform: uppercase;
}
```

*Principle:* The relationship between letter spacing and size is inverse. As size increases, reduce tracking. As size decreases, increase tracking. The perceptual effect: text at all sizes feels equally "spaced."

---

### Line Height Ratios

Line height should vary by text purpose:

```css
:root {
  --lh-tight: 1.1;        /* Large display text, single-line headings */
  --lh-heading: 1.2;      /* Multi-line headings */
  --lh-compact: 1.35;     /* UI text, labels, metadata */
  --lh-body: 1.55;        /* Body text — screen reading optimised */
  --lh-generous: 1.7;     /* Spacious reading — the artefact at contemplative pace */
}
```

*Research basis:*
- Print optimal: 1.2–1.45 (Bringhurst)
- Screen optimal: 1.4–1.7 (various studies, Medium's 1.58 is well-documented)
- The sweet spot for professional screen reading: 1.5–1.6
- Going above 1.7 starts to disconnect lines from each other — the eye loses the thread

---

### Proper Measure Implementation

```css
.circuit-content {
  /* Fluid with a readable maximum */
  max-inline-size: min(100% - 2 * var(--space-m), 42.5rem);
  margin-inline: auto;
}

.artefact-content {
  /* Slightly wider for document-grade reading */
  max-inline-size: min(100% - 2 * var(--space-m), 45rem);
  margin-inline: auto;
}
```

*Why `rem` not `ch`:* The `ch` unit (0-character width) seems ideal for setting measure by character count, but it varies with the font and can produce unexpected results with variable fonts. Using `rem` with a known type size gives predictable character counts: at 1.125rem Source Serif 4, 45rem produces approximately 60-65 characters per line — within the optimal range.

---

### The Subliminal Weight Transition

The input-to-record mode weight shift (400 → 500) should be CSS-only, using registered custom properties:

```css
@property --text-weight {
  syntax: "<number>";
  inherits: true;
  initial-value: 400;
}

.circuit-field {
  font-variation-settings: "wght" var(--text-weight);
  transition: --text-weight 600ms ease-out;
}

.circuit-field[data-mode="record"] {
  --text-weight: 500;
}
```

*Why this works:*
- `@property` registration makes the custom property animatable (unregistered custom properties cannot be transitioned)
- `font-variation-settings` with a variable font produces a smooth, continuous weight change — not a jump between static font files
- 600ms ease-out: slow enough to be subliminal (the user feels gravitas, doesn't see a font change), fast enough to complete before the user's attention shifts
- The transition happens during the bell pause — the text settles into its record weight as the new state renders

---

### Viewport and Scroll Management

```css
/* Full-viewport states */
.circuit-state {
  min-block-size: 100dvh;
  display: grid;
  place-content: center;
  padding-block: var(--state-padding-block);
  padding-inline: var(--space-m);
}

/* Exit silence — contained scroll environment */
.exit-silence {
  min-block-size: 100dvh;
  overscroll-behavior: contain;
}

/* Scroll snap for post-completion sections */
.post-completion {
  scroll-snap-type: y proximity;
}

.post-completion > section {
  scroll-snap-align: start;
  scroll-padding-block-start: var(--space-l);
}
```

*Key decisions:*
- `100dvh` not `100vh`: accounts for mobile browser chrome (address bar, navigation bar). Marcus on his phone sees the full state, not content hidden behind browser UI.
- `overscroll-behavior: contain` on exit silence: prevents scroll chaining — the user cannot accidentally scroll "past" the silence back to the circuit. The silence is a contained environment.
- `scroll-snap-type: y proximity`: the scroll will gently snap to section boundaries (silence → artefact → calibration) but only when close. Not mandatory snap, which feels rigid.

---

### The Bell Transition (CSS-Only)

```css
@property --bell-opacity {
  syntax: "<number>";
  inherits: false;
  initial-value: 1;
}

.circuit-state {
  opacity: var(--bell-opacity);
  transition: --bell-opacity 300ms ease-in;
}

.circuit-state[data-transitioning="out"] {
  --bell-opacity: 0;
}

/* The incoming state */
.circuit-state[data-transitioning="in"] {
  --bell-opacity: 0;
  animation: bell-in 400ms ease-out 200ms forwards;
}

@keyframes bell-in {
  to { --bell-opacity: 1; }
}
```

*Timing:*
- Fade out: 300ms ease-in (accelerating exit)
- Designed pause: 200ms delay (the "bell" — the moment between states)
- Fade in: 400ms ease-out (decelerating arrival)
- Total: ~900ms for the complete transition
- On slow connections: the pause extends naturally (the server response fills the gap)

*Reduced motion:*
```css
@media (prefers-reduced-motion: reduce) {
  .circuit-state {
    transition: none;
    animation: none;
  }
}
```

---

### Colour and Surface

```css
:root {
  --surface: oklch(0.98 0.005 80);
  --ink: oklch(0.15 0.01 80);
  --system: oklch(0.55 0.005 80);
  --accent: oklch(0.55 0.06 55);
  --boundary: oklch(0.82 0.005 80);
  --recessive: oklch(0.72 0.005 80);
}

/* Derived variants */
:root {
  --ink-subtle: color-mix(in oklch, var(--ink) 60%, transparent);
  --accent-hover: color-mix(in oklch, var(--accent) 85%, black);
  --surface-raised: color-mix(in oklch, var(--surface) 95%, var(--ink));
}

/* High contrast preference */
@media (prefers-contrast: more) {
  :root {
    --system: oklch(0.35 0.005 80);
    --recessive: oklch(0.50 0.005 80);
    --boundary: oklch(0.60 0.005 80);
  }
}

/* Forced colours */
@media (forced-colors: active) {
  :root {
    --ink: CanvasText;
    --surface: Canvas;
    --accent: Highlight;
    --system: CanvasText;
    --boundary: CanvasText;
  }
}
```

*Why `oklch`:*
- Perceptually uniform: equal numeric changes = equal perceived changes. This matters when computing derived colours — `color-mix()` in oklch produces clean, predictable midpoints
- Hue angle control: the `80` hue keeps the entire palette in the warm yellow-amber family. Consistent hue prevents the palette from feeling random
- Low chroma (0.005-0.06): keeps the palette near-monochrome. The accent's 0.06 chroma is enough to register as "warm brown" without reading as "colourful"

---

### Focus and Interaction States

```css
/* Focus ring — meets WCAG 2.4.13 AAA */
:focus-visible {
  outline: 2px solid var(--ink);
  outline-offset: 2px;
}

/* Remove default focus for mouse users */
:focus:not(:focus-visible) {
  outline: none;
}

/* Interactive elements — minimal styling */
button, [role="button"] {
  font-family: inherit;
  font-size: inherit;
  font-weight: inherit;
  color: var(--ink);
  background: transparent;
  border: 1px solid var(--ink);
  padding: 0.75em 1.5em;
  cursor: pointer;
  transition: background-color 150ms ease;
}

button:hover {
  background: var(--surface-raised);
}

/* The commit button — the only button that deserves weight */
.commit-action {
  font-weight: 500;
  background: var(--ink);
  color: var(--surface);
}
```

---

### Selection Styling

```css
::selection {
  background: color-mix(in oklch, var(--accent) 30%, transparent);
  color: var(--ink);
}
```

A subtle, warm selection colour that maintains readability. The selection should feel like a highlighter on paper, not a system highlight.

---

### Print Stylesheet (for PDF Parity)

```css
@media print {
  :root {
    --surface: white;
    --ink: black;
    --system: #555;
    --accent: #666;
    --boundary: #ccc;
  }

  body {
    font-size: 11pt;  /* Standard document size */
    line-height: 1.45; /* Print-optimised leading */
  }

  .circuit-state,
  .exit-silence,
  .calibration-coda {
    display: none;  /* Only print the artefact */
  }

  .artefact {
    margin: 0;
    padding: 0;
    max-width: none;
  }

  .artefact-heading {
    page-break-after: avoid;
  }

  .artefact-section {
    page-break-inside: avoid;
  }
}
```

---

### Complete CSS Custom Properties Reference

```css
:root {
  /* ═══════ COLOUR ═══════ */
  --surface: oklch(0.98 0.005 80);
  --ink: oklch(0.15 0.01 80);
  --system: oklch(0.55 0.005 80);
  --accent: oklch(0.55 0.06 55);
  --boundary: oklch(0.82 0.005 80);
  --recessive: oklch(0.72 0.005 80);

  /* ═══════ TYPOGRAPHY ═══════ */
  --font-family: 'Source Serif 4', Georgia, 'Times New Roman', serif;
  --font-weight-light: 300;      /* system text */
  --font-weight-regular: 400;    /* input mode, redirect */
  --font-weight-medium: 500;     /* record mode, artefact body */
  --font-weight-semibold: 600;   /* artefact headings */

  --lh-tight: 1.1;
  --lh-heading: 1.2;
  --lh-compact: 1.35;
  --lh-body: 1.55;
  --lh-generous: 1.7;

  /* ═══════ SPACING (via Utopia/cu.css, representative values) ═══════ */
  /* These would be generated by Utopia — shown here for reference */
  --space-3xs: clamp(0.25rem, ...);
  --space-2xs: clamp(0.375rem, ...);
  --space-xs:  clamp(0.5rem, ...);
  --space-s:   clamp(0.75rem, ...);
  --space-m:   clamp(1rem, ...);
  --space-l:   clamp(1.5rem, ...);
  --space-xl:  clamp(2rem, ...);
  --space-2xl: clamp(3rem, ...);
  --space-3xl: clamp(4rem, ...);

  /* ═══════ TRANSITIONS ═══════ */
  --bell-fade-out: 300ms ease-in;
  --bell-pause: 200ms;
  --bell-fade-in: 400ms ease-out;
  --weight-transition: 600ms ease-out;

  /* ═══════ LAYOUT ═══════ */
  --measure-circuit: min(100% - 2 * var(--space-m), 42.5rem);
  --measure-artefact: min(100% - 2 * var(--space-m), 45rem);
  --touch-target-min: 2.75rem;    /* 44px at default root — WCAG AAA */
}
```

---

## 7. Synthesis — How These Principles Apply to The Circuit

### The Design Stack

Reading from bottom (foundational) to top (experiential):

1. **CSS foundation:** `@layer`, `@property`, `oklch`, modern layout (Grid, Flexbox, `gap`), `dvh`, variable fonts
2. **Typography system:** Source Serif 4 variable, Utopia fluid scale, optical sizing, OpenType features, fallback metric matching
3. **Spatial system:** Utopia fluid spacing, density arc per state, measure-controlled columns, `overscroll-behavior` containment
4. **Hierarchy system:** Weight + size + opacity + spacing + style + position + absence — seven axes, no colour dependency
5. **Emotional arc:** Density compression through the crucible, release at Stop/Go, vast silence at exit
6. **Document-grade output:** Quality jump through size step + wider margins + structural accent, dual token architecture
7. **The experience:** Text IS the interface. The user's words are the only thing that matters. Everything else — every pixel, every property, every transition — exists to make the user's words feel serious, permanent, and owned.

### Key Design Decisions This Research Supports

| Decision | Supporting Evidence |
|----------|-------------------|
| Source Serif 4 as sole typeface | Transitional serif = authority + readability. Variable = smooth weight transitions. Single family = unified identity. Confirmed by: iA Writer (single family), Substack (serif = personal voice) |
| Near-monochrome palette | Hierarchy through weight/size/opacity, not colour. Confirmed by: Linear (opacity hierarchy), iA Writer (no colour), Bear (single accent) |
| Warm off-white surface | Reads as "paper" not "screen." Reduces eye strain. Confirmed by: Bear (warm surfaces), Medium (warm background option), every reading app |
| Density arc across states | Spatial compression as emotional signal. Confirmed by: architecture (Wright, Aalto), meditation apps (Headspace, Calm), Typeform (space = cognitive weight) |
| Full-viewport states | Text as interface, no chrome. Confirmed by: iA Writer, Arc, poetry websites, every browser reading mode |
| Measure at 42.5-45rem | 60-65 characters optimal for screen reading. Confirmed by: Bringhurst (45-75 chars), Medium (680px), Stripe docs (680px) |
| Document-grade artefact | Quality jump from input to document. Confirmed by: Day One (quality jump on export), Substack (document as product), legal/notarial typography conventions |
| Bell transition (CSS-only) | Precise, fast, no bounce. Confirmed by: Linear (120-200ms, ease-out), architectural transitions (threshold moments), meditation apps (state changes without animation) |
| `@property` for weight animation | CSS-only animatable custom properties. The weight transition is the mechanism for the subliminal input→record shift. No JavaScript animation library needed |
| Hanging punctuation, ligatures, optical sizing | Document-grade typographic refinements. The difference between "web page" and "professional document" lives in these details |

### What Must Be Invented (No Existing Reference)

This research confirms that the following Circuit interactions have no existing digital precedent and require original design:

1. **Language blocking as trust-building** — No product blocks user text and makes it feel like respect
2. **Eligibility rejection as calibration** — No product tells users "no" and makes it feel like a useful finding
3. **Session re-entry as confrontation** — No product shows users their own words and asks "do you still mean this?"
4. **Dual-format artefact** — No product produces output that works as both a complete document and as screenshot-able fragments

These are the design problems that research cannot solve. They require prototyping, testing, and iteration with real users in real decision moments.

---

*This reference document was compiled from deep analysis of the products, principles, and techniques described. For the real-time implementation phase, the CSS techniques in Section 6 can be directly adopted. The design principles in Sections 2-5 should inform design decisions but not constrain them — The Circuit is creating a new category, and category-creating products often need to break the very principles they studied.*
