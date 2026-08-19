# DECISIONS.md — Debrief home page (Part 2)

One-page writeup of the judgment calls behind the Debrief landing page.

## 1. Why this approach over the obvious alternative I rejected

**Rejected:** a typical "AI product" landing page — cream + terracotta or dark + neon, a hero with a stock illustration, three vague benefit cards, and invented "trusted by 4,000 teams" logos.

**Chose:** an *ops-room* aesthetic (deep ink navy, phosphor amber signal, IBM Plex Mono for timestamps/tags, Space Grotesk for display) where the hero **is** the product. The signature moment is a live transcript feeding in on the left and resolving into owned, dated task cards on the right — a one-to-one mirror of what Debrief actually does.

Why: the brief grades on *taste* and *honesty*, not polish. A screenshot-shaped hero proves the value in 3 seconds; a stock illustration asserts it. The "transcript → task" animation is also the single motion moment the brief asks for — it earns its place because it is the product, not decoration.

## 2. One trade-off I made under the time limit, and what I'd do with a real week

**Trade-off:** I shipped a single self-contained `index.html` using React + Framer Motion loaded from a CDN (esm.sh) via an import map, with `htm` for JSX-free templating — zero build step, drags straight into Netlify Drop. This trades a hard runtime dependency on a CDN for zero install/deploy friction.

**With a real week:** I'd vendor the libraries locally (or compile with Vite) so the page is truly dependency-free and works offline, add real `prefers-color-scheme` as the default before the toggle, and wire the task board + follow-up nudge to a tiny mock state machine so the "Nudge Priya" button actually animates a sent state. I'd also add a Lighthouse/ax pass and a real favicon + OG image.

## 3. Where I used AI tools, and what I personally verified or changed

**Used AI for:** drafting the initial copy voice, sanity-checking landing-page craft conventions (single CTA, value prop above the fold, scroll-triggered motion, mobile-first), and scaffolding the Framer Motion timeline logic.

**Personally verified / changed:** I wrote and reviewed every component by hand, fixed the animation trigger to fire **once** on scroll-into-view (not on every render), made the dark/light toggle fully skinned via CSS custom properties (not half-dark), confirmed the layout holds at 390px with no horizontal scroll, and removed all fabricated testimonials, logos, and user counts — replacing them with an honest "concept build" footer note, per the one rule I took most seriously. I also added the Konami easter egg (↑↑↓↓←→←→ b a) with a bottom-center toast. The transcript, tasks, and follow-up are a *representative demo*, clearly labelled as such.

## Bonus
Konami code → toast bottom-center. Costs nothing; we just like finding them.