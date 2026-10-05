# Design

<!-- impeccable:design-schema 1 -->

## World

**Systems-diagram grammar.** The profile renders as the thing Ayush actually builds — a multi-agent system. The visual language is borrowed from the domain itself (node graphs, state machines, memory layers, flow edges) rather than from the GitHub-profile template genre.

The decisive move is that the two primary visuals are **hand-authored SVG committed to the repo**, not assembled from the badge/banner generator services every ML profile draws on. That is what separates this from a reskin.

## Palette

Committed dark. One ground, one identity accent, one signal accent.

| Role | Value | Use |
|:--|:--|:--|
| Ground | `#07070F` | obsidian base, both SVGs |
| Identity | `#60A5FA` / `#93C5FD` | agent nodes, edges, structure, headings |
| Signal | `#F59E0B` / `#FBBF24` | the critic node, the feedback loop, email CTA — reserved for *the thing that matters* |
| Text | `#F5F5F7` | wordmark, node labels |
| Muted | `#8B8BA7` / `#6E6E8E` | system text, secondary detail |

Amber is rationed deliberately: it marks the self-critique loop and nothing else structural, so the eye lands on the idea the profile is arguing for.

## Assets

Every visual is a hand-authored SVG in `assets/`, all 1280 wide so they share one grid and scale together.

| File | Size | What moves, and what it explains |
|:--|:--|:--|
| `hero.svg` | 1280×400 | Network boots outward from the center (mask wipe), nodes pop in by distance, wordmark tracks in from wide letter-spacing, HUD brackets draw on, a light sweep crosses the name, and a SMIL typewriter cycles four positioning lines |
| `section-0{1..4}.svg` | 1280×120 | Kinetic title cards: outlined index numeral draws on, title slides in, rule wipes across, an amber signal pulse travels the rule |
| `layers.svg` | 1280×300 | The three-layer thesis as motion: a packet circulating a five-node cycle with an amber retry chord; a query sonar-pinging a vector space and snapping to its 3 nearest neighbours; a prediction drawing with its conformal band and a check |
| `architecture.svg` | 1280×400 | The real topology, now *running*: a packet goes plan → search → read → critic, is rejected (`verdict: retry`), rides the amber arc back to search, passes on the second pass and streams out of write. Node boxes and their memory read/write lines light up in sync |
| `project-research.svg` | 1280×240 | Blocking vs. streamed lanes on a shared clock: one waits for a progress bar then dumps everything, the other emits tokens immediately. `87%` rolls in on an odometer |
| `project-legal.svg` | 1280×240 | Two documents, clause-alignment links draw across, one turns amber and flags `CONTRADICTION` with pulsing attention spans; the ALIGN → ENTAIL → ATTRIBUTE steps light in sequence |
| `project-atlas.svg` | 1280×240 | 19 points (one per lineage-specific TF) orbit tilted ellipses with depth faked by opacity; HNF1B, GATA3, NKX2-1 ride as labelled amber points. Expression matrix twinkles; `98.76%` and `19` roll in |
| `project-carbon.svg` | 1280×240 | Predictions pop in with their interval whiskers, SHAP bars grow from a shared baseline in both directions; `ŷ ± q̂` |
| `divider.svg` | 1280×36 | Between projects: a spinning amber diamond emitting particles outward |
| `stack.svg` | 1280×300 | Four marquee lanes (one per layer) at different speeds and alternating directions, edge-faded; the anchor tool of each layer is ringed amber |
| `footer.svg` | 1280×260 | Sign-off typed with `steps()` and a following caret over four slow waveforms |

Every number on a card (87%, 98.76%, 19) is one already stated in the project text. The SHAP features are labelled `φ₁…φ₅` and the clause/token/matrix shapes are abstract on purpose: they illustrate a mechanism and claim no data.

## Motion

**Two tiers.** *Entrances* are one-shot (boot, track-in, draw-on, wipe, pop, odometer) and run when the image first becomes visible: browsers pause animations in off-screen SVG images, so each card performs as it is scrolled into view. *Ambient loops* are slow and low-contrast (edge flow, breathing, orbits, marquee, waves) so the page never feels busy at rest.

**Settled frame is the design.** Every entrance uses `animation-fill-mode: backwards` and keyframes that only define the `from` state, so the element's own attributes are the end state. With motion off, or mid-load, nothing is ever stuck invisible.

**Motion carries meaning.** Amber movement always means the critique/correction idea (retry arc, contradiction, interval, signal pulse); blue is structure and flow. Nothing moves that could not be explained in a sentence.

**Mechanics.** CSS keyframes for transforms/opacity; SMIL (`animate`, `animateMotion` with `keyPoints`) where timing must be exact or an element follows a path: the typewriter, the topology packet and its synced highlights, orbiting TFs. Mono text uses `textLength` so typewriter clips and carets line up whatever monospace font the viewer has. Easing is one family: `cubic-bezier(.16,1,.3,1)` for settles, a slight overshoot for pops.

**Reduced motion.** Every SVG has a `prefers-reduced-motion` block that stops CSS animation, hides SMIL-driven layers (`.smil`) and shows static stand-ins (`.rm-show`), e.g. the hero's typewriter becomes the full positioning line.

## Type

No web fonts are possible in an SVG rendered as an image, so faces resolve from system stacks: heavy tracked sans (`Segoe UI`/Roboto/Helvetica) for the wordmark, monospace (`SFMono-Regular`/Consolas/Menlo) for all system text — used for measurement and machine output, not as a "technical" costume.

## Structure

Hero → one positioning paragraph → **01 the problem** (thesis + layers triptych) → **02 topology** (the running architecture + the argument for the critic node) → **03 selected work** (four animated project cards, each followed by its write-up) → **04 stack** (marquee + plain-text summary) → typed sign-off → contact.

Depth leads. The sequencing is the "mastery" claim: an engineer's profile that opens with an argument and a diagram reads differently from one that opens with a badge wall.

## Verification

Every SVG is validated with `xmllint` and frame-sampled in headless Chromium loaded as an `<img>` (GitHub's context: no scripts), then the full README is rendered on light and dark page backgrounds at desktop and phone widths. Motion-pass defects found and fixed: a duplicated `style` attribute (invalid XML) on wipe elements, the divider diamond's rotate attribute being overridden by its CSS spin, atlas orbits overflowing the card, and streamed tokens all reappearing at once on loop restart (moved to per-token SMIL key times). Earlier pass: the architecture diagram's title block collided with the feedback arc (moved below the memory bar), and the Stack section's four lines collapsed into one paragraph (markdown single-newline; fixed with explicit `<br>`).

## Deliberate deviations

The project emoji were removed in the motion pass: each project now opens with its own animated card (coded `P.01`–`P.04`), which does the marker job with real content. Section `##` headings became SVG title cards, which costs GitHub's heading outline; the alt text on each card carries the heading for screen readers.

## Constraints

GitHub Markdown allows no CSS, JS, or web fonts. Every visual decision works within: committed SVG assets, allowed inline HTML (`<div align>`, `<img>`, `<br>`), tables, and shields.io badges. No project fact, metric, link, or credential was invented — all four project entries derive from the existing profile content.

## Removed: the stats cards

A "Signals" section originally carried two `github-readme-stats` cards from a self-hosted instance. It was cut after the instance began rendering *"Something went wrong! Downtime due to GitHub API rate limiting"* on the live profile.

The removal is a design improvement, not just a bug workaround. Those cards were the only third-party generators left in an otherwise fully authored page, and commit/streak/language counts are vanity metrics that say nothing about ML depth — the architecture diagram and the project write-ups carry that argument far better. A visibly broken error card on a profile arguing for engineering rigor is worse than no card at all.

To restore them, the self-hosted instance needs a GitHub personal access token set as `PAT_1` in its Vercel environment variables; unauthenticated it falls back to a shared rate limit and throttles quickly.
