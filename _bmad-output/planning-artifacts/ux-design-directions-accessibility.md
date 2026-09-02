# Accessibility findings: ux-design-directions.html

Audited 2 September 2026 against WCAG 2.2 AA. This file records what was
measured and why. The outstanding work is tracked as a ToneBan task under
`the-circuit`, not here.

## How it was run

axe-core 4.13.0 through `@axe-core/cli`, tags `wcag2a,wcag2aa,wcag21a,wcag21aa,wcag22aa`,
against the page served locally, with `--load-delay 1500` so nothing was sampled
mid-animation. Results read from the saved JSON rather than the console, because
the console reporter prints violations only and never mentions the `incomplete`
bucket.

axe reported 2 violations, 22 passes and 1 incomplete group of 6 nodes. The six
were resolved by measuring the rendered pixels, which is what the rest of this
note is about.

## Failures

Eight nodes, all contrast, all against the 4.5:1 threshold for text under
18.66px bold / 24px regular.

| Element | Measured | Needs | Cause |
|---|---|---|---|
| `.privacy-note` | 3.13:1 | 4.5:1 | `#8e8d8b` on `#faf8f5` |
| `.artefact-peek` | 1.83:1 | 4.5:1 | `#bbbab7` on `#faf8f5` |
| `.dir-nav__num` x3 | 2.87 to 3.13:1 | 4.5:1 | `rgba(26, 26, 24, 0.48)` |
| `.dir-nav__label` x3 | 2.91:1 | 4.5:1 | `rgba(26, 26, 24, 0.48)` |

The six nav nodes came back as `incomplete` rather than as violations because
axe cannot see through the alpha to a ratio. Three independent methods agree on
what it composites to: pixel measurement of the render gave 2.87:1 and 3.06:1,
and the arithmetic `fg * a + bg * (1 - a)` gives `rgb(142, 141, 139)` at 3.13:1.
The same measurement returns `rgb(26, 26, 24)` exactly for the active item,
which is the full-opacity sibling used to calibrate it.

## What would fix them

- **The two greys.** The lightest neutral grey that clears 4.5:1 on `#faf8f5` is
  about `rgb(115, 114, 112)`. Both current values are lighter than that.
- **The inactive nav treatment.** One cause behind all six nodes: 48% alpha as
  the "inactive" state. At `rgba(26, 26, 24, 0.61)` it composites to
  `rgb(113, 113, 110)` and clears at 4.62:1, while still reading as visibly
  dimmer than the active item. Anything above 0.61 also works.

## Not failures, but worth knowing

- No `<h1>` among 30 headings.
- No `<main>` landmark. The page has three `<header>` elements and a `<nav>`.

Neither is a tagged WCAG A or AA failure, so neither appears above.

## Re-running it

Serve this directory and run the command in the "How it was run" section. Read
`incomplete` from the saved JSON, not the console summary. A run that reports
zero violations without saying what happened to the incompletes verifies less
than it appears to.
