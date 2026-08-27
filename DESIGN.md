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

**`assets/hero.svg`** (1280×400) — animated agent-graph banner. Node clusters flank a center wordmark; edges flow via `stroke-dashoffset` animation, nodes breathe on staggered delays, embers drift. Center glow keeps the wordmark legible over the graph. Composition deliberately leaves the middle band quiet so type never competes with the network.

**`assets/architecture.svg`** (1280×400) — the real agent topology: `PLANNER → SEARCH → READ → CRITIC → WRITE` over a dual-layer ChromaDB memory bar, with the critic's amber feedback arc routing back to search. Content is drawn from the actual AI Research Assistant Pipeline description; nothing about the architecture is invented. This is the profile's proof-of-mastery asset — it demonstrates systems thinking before any project list does.

Both use CSS animation inside the SVG (works when GitHub serves them as images) and both **read completely without animation** — motion is a layer, never load-bearing. Both honor `prefers-reduced-motion`.

## Type

No web fonts are possible in an SVG rendered as an image, so faces resolve from system stacks: heavy tracked sans (`Segoe UI`/Roboto/Helvetica) for the wordmark, monospace (`SFMono-Regular`/Consolas/Menlo) for all system text — used for measurement and machine output, not as a "technical" costume.

## Structure

Hero → one positioning paragraph → **the problem I keep solving** (a thesis, before any project) → architecture diagram + the argument for the critic node → four projects with real technical decisions surfaced → stack → contact.

Depth leads. The sequencing is the "mastery" claim: an engineer's profile that opens with an argument and a diagram reads differently from one that opens with a badge wall.

## Verification

Both SVGs and the full rendered README were screenshotted in headless Chromium and inspected. Two defects were found and fixed: the architecture diagram's title block collided with the feedback arc (moved below the memory bar), and the Stack section's four lines collapsed into one paragraph (markdown single-newline; fixed with explicit `<br>`).

## Deliberate deviations

Emoji are retained as project-section markers. The craft floor treats emoji-as-icons as a tell, but the brief explicitly asked for a decorated profile, and in GitHub READMEs these read as a native affordance rather than a substitute icon system. The decorative weight is carried by the authored SVGs, not the emoji.

## Constraints

GitHub Markdown allows no CSS, JS, or web fonts. Every visual decision works within: committed SVG assets, allowed inline HTML (`<div align>`, `<img>`, `<br>`), tables, and shields.io badges. No project fact, metric, link, or credential was invented — all four project entries derive from the existing profile content.

## Removed: the stats cards

A "Signals" section originally carried two `github-readme-stats` cards from a self-hosted instance. It was cut after the instance began rendering *"Something went wrong! Downtime due to GitHub API rate limiting"* on the live profile.

The removal is a design improvement, not just a bug workaround. Those cards were the only third-party generators left in an otherwise fully authored page, and commit/streak/language counts are vanity metrics that say nothing about ML depth — the architecture diagram and the project write-ups carry that argument far better. A visibly broken error card on a profile arguing for engineering rigor is worse than no card at all.

To restore them, the self-hosted instance needs a GitHub personal access token set as `PAT_1` in its Vercel environment variables; unauthenticated it falls back to a shared rate limit and throttles quickly.
