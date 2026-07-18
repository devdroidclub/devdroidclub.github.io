# Design — devdroid.club

Locked design system. Future Hallmark runs read this file first; pages defer
to it. Amend intentionally — the file is the rule.

## System
- Genre · modern-minimal
- Macrostructure · TBD (chosen at build time — this DNA covers surface / type / radius / motion, not page structure; the current prototype's frame+slide-deck shape is a separate decision, not superseded by this file)
- Theme · custom (vibe: "technical, calm, IDE-like, softly-rounded controls")
- Axes · light (paper ~94% L) / grotesk-sans (single-family, weight-differentiated) / cool (blue accent)

## Tokens (canonical · `tokens.css` is the source of truth once generated)
```css
:root {
  --color-paper:      oklch(94% 0.004 95);   /* base surface — barely-there neutral tint, not stark white */
  --color-paper-2:    oklch(90% 0.005 95);   /* recessed panels / sidebar-like surfaces, one notch darker */
  --color-ink:        oklch(18% 0.006 95);
  --color-ink-2:      oklch(45% 0.01 95);    /* muted / secondary text */
  --color-rule:       oklch(85% 0.006 95);   /* hairline borders */
  --color-accent:     oklch(55% 0.16 250);   /* cool blue — small footprint, not a flood */
  --color-accent-ink: oklch(98% 0.005 250);  /* text/icon on solid accent fill */
  --color-focus:      oklch(60% 0.18 250);

  --font-display: "Inter Tight", "General Sans", system-ui, sans-serif; /* candidate — role: heavy grotesque, single-family with body */
  --font-body:    "Inter", system-ui, sans-serif;                       /* candidate — role: neutral grotesque */
  --font-mono:    "JetBrains Mono", "IBM Plex Mono", ui-monospace, monospace; /* candidate — role: technical/meta labels */

  /* 4-pt spacing scale, named: --space-3xs … --space-4xl. Define in tokens.css. */
  /* Type scale, 1.25 (major-third) ratio: --text-xs … --text-display.          */

  --ease-out: cubic-bezier(0.16, 1, 0.3, 1);
  --dur-fast: 180ms;  --dur-base: 240ms;  --dur-slow: 320ms;

  --radius-card:  8px;   /* content surfaces: cards, panels, small icon tiles */
  --radius-pill:  999px; /* interactive controls: buttons, tags, active-tab chips */
  --radius-input: 6px;   /* form inputs, small controls */
  --radius-frame: 0px;   /* structural chrome: page frame, dividers, large photo/content blocks — deliberately sharp */
}
```

## Variants — Blog
Scoped divergence, not a system override. The base system stays
grotesk-sans/single-family (see Axes above); this variant applies only to
`/blog` — post titles, section marks, bylines, category tags. Everything
else (spacing scale, radius tiers, motion stance, CTA voice) is inherited
from the base system unchanged.

- Source · user's own `d.d.c.` wordmark (Figma), two weights of the same
  type family, confirmed by inspector panel — not screenshot-estimated.
- `--serif-blog-display`: **Shippori Mincho**, weight 800 (ExtraBold),
  letter-spacing -5%. Role: post titles, blog masthead mark. Free, Google
  Fonts.
- `--serif-blog-label`: **Shippori Mincho B1**, weight 700 (Bold), tracked
  out (positive letter-spacing). Role: bylines, dates, category/meta tags.
  Free, Google Fonts — B1 is a distinct rounded-terminal cut of the same
  family, not just a weight variant.
- Surface pairing observed alongside the type: a near-black card
  (`oklch(~8% 0 0)`) with off-white ink (`#FEFDFD`, not pure white) for
  masthead/stamp treatments; a light grey halftone/grain paper texture for
  section backgrounds. Grain is a background-only treatment — never place
  it under running body text (legibility/contrast).
- Live since 2026-07-18. `/blog` ships as two new slides in `index.html`'s
  existing hash-router deck: `slide-blog` (index — card grid) and
  `slide-blog-post` (a single reusable template, content injected by JS
  from a `BLOG_POSTS` data object keyed by slug — see `index.html`'s
  script section). Cards use `--serif-blog-display` for titles and
  `--serif-blog-label` for tag/date meta and the "Read →" link; body copy
  stays on the base `--mono`/`--sans` stack, per the grain-never-under-text
  rule below.
- Autopublish path: a future publishing agent only needs to append an
  entry to `BLOG_POSTS` (slug → `{ sourceUrl, en: {...}, ru: {...} }`) —
  no HTML/CSS edits required per post. Keep claims sourced (a
  `sourceLabel` + `sourceUrl` pair renders as a "Source:" line on the
  post) — this is the site's honest-copy discipline applied to editorial
  content, not just marketing copy.

## CTA voice
- Primary · solid `--color-accent` fill, `--radius-pill`, generous horizontal padding (echoes the "Get in Touch" / "Be Pro" pill buttons observed in references)
- Secondary · outline/ghost on `--color-ink`, same `--radius-pill`

## Motion stance
- Conservative — 1 reveal primitive at a time (fade or slide), no bounce/overshoot. No motion library was observed in any studied source (all static screenshots) — default to CSS-only transitions.
- Reduced-motion fallback · ≤150 ms opacity crossfade.

## Provenance
- Source mode: image (6 user-attached screenshots)
- Sources: Balenciaga.com (nav flyout + hero), Awwwards.com (Site of the Day template + jobs card grid), Cantor8.io (hero, ×3 near-duplicate captures)
- Date: 2026-07-18
- Attestation: image mode — emitted without asking, per protocol (user owns the screenshots)
- Confidence: tokens are a considered synthesis estimated from source-image colour bands and structural patterns, not extracted CSS (these are third-party sites, not project code). Fonts are role-based with named candidates from the Hallmark canon, not confirmed exact faces. Radius and structural rhythm observations are direct/accurate — they came from pixels, not markdown.

## Notes — anti-patterns flagged, do NOT carry over
- Don't apply one blanket border-radius everywhere. The whole point of this DNA is the two-tier system: `--radius-pill` only on genuine interactive controls, `--radius-card` on content surfaces, `--radius-frame: 0` on structural chrome (page frame, dividers, large content blocks). Collapsing this into a single radius value defeats the "VS Code" read this file is aiming for.
- Don't copy Cantor8's full-viewport saturated-blue flood as the base paper — that source's *hue* informed `--color-accent`, not `--color-paper`. The paper stays near-neutral/light.
- Don't copy Balenciaga's zero-radius-everywhere wholesale — it's a valid reference for how "sharp" the frame/structural layer can go, but the brief explicitly wants selective rounding, not austerity everywhere.

## Exports
`tokens.css` (in this project) is the source of truth once generated by a build.
For Tailwind v4 `@theme`, DTCG `tokens.json`, or shadcn/ui CSS variables, ask
*"extend design.md with Tailwind exports"* (or the format you want) — Hallmark
will append them per `export-formats.md`.
