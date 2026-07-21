# Design — devdroid.club

Locked design system for the DDC commercial site. Amend intentionally; the
single-file build in `index.html` is the implementation source of truth.

## System

- Genre: modern-minimal with a terminal/editorial engineering voice.
- Macrostructure: Framed Product Narrative.
- Position: digital product studio; one responsible product
  partner assembling trusted specialists around the actual challenge.
- Navigation: sticky three-zone utility rail (brand, primary links, contacts /
  language / CTA) and a full-screen mobile menu with its own wordmark, two-column
  link grid on tablet, single-column links on phones and direct contact actions.
- Theme: achromatic warm paper, near-black ink, strict rules, no gradients,
  shadows, glass effects, or decorative rounding.
- Frame: one sharp outer frame around the full document. It must not consume
  useful mobile width.

## Tokens

```css
:root {
  --paper:  oklch(96% 0.004 95);
  --paper-2: oklch(91% 0.006 95);
  --ink:    oklch(16% 0.006 95);
  --muted:  oklch(44% 0.008 95);
  --rule:   oklch(72% 0.006 95);
  --focus:  oklch(34% 0.01 95);

  --sans: "Helvetica Neue", Arial, system-ui, sans-serif;
  --mono: "Hack", "DejaVu Sans Mono", ui-monospace, monospace;
}
```

Spacing follows a named 4/8-point scale. Components consume tokens; colour and
font values do not appear ad hoc outside the token block.

## Typography

- Display and body: Helvetica Neue / Arial / system sans-serif.
- Brand accent: the canonical `assets/ddc-wordmark.svg` contains the Mincho
  `d.d.c.` wordmark. Use this asset in the header and footer; do not recreate
  the mark as live page text or pair it with a second DDC title in the footer.
- Display and body remain Helvetica Neue / Arial in both languages so the
  hierarchy is consistent and Cyrillic never falls into an uncontrolled face.
- Technical metadata, navigation, section numbers, states and buttons: Hack.
- Body copy is at least 16px on mobile, with a 55–75-character reading measure.
- Major headings are tightly tracked, upright, left-aligned and allowed to wrap.
- Major headings wrap only at spaces; never split a word to satisfy a narrow
  editorial column. Reduce the responsive display size before breaking words.
- Hero and contact display scales are capped for 13-inch laptop viewports and
  have an additional short-viewport rule so each opening composition fits.
- Mono is never used for long paragraphs.

## Components

- Primary CTA: rectangular, solid ink, paper text, minimum 48px height.
- Secondary CTA: rectangular outline, transparent paper surface.
- Cards are content structures made from rules, not floating rounded surfaces.
- Section labels stack above their headings on mobile; no hanging eyebrow beside
  a heading at narrow widths.
- Selected work remains legible without imagery. Future approved screenshots
  are optional progressive enhancement, never required structure.
- Footer capability labels are navigation, not decoration: keep them as links
  to the capabilities section with visible hover and keyboard focus states.

## Motion

- One reveal primitive: short opacity + 16px vertical settling.
- No letter-by-letter typing, parallax, cursor replacement, or perpetual motion.
- `prefers-reduced-motion` disables reveal transforms and smooth scrolling.

## Content constraints

- No fabricated metrics, testimonials, clients, awards, team size or promises.
- No Team, pricing, vacancies, SEO/marketing service, or blog in this commercial
  site version.
- Arena and TLK may use their existing public links. Do not add outcomes or
  details without owner confirmation.
- Telegram bot stays generic until a verified public case is supplied.
- Preserve the established email, Telegram and GitHub contacts.
- Russian is the default language; an explicitly saved English preference is
  respected on later visits.

## Privacy and analytics

- The operator is shown as provided by the owner: Стасив С.В., Москва,
  `stas.stasiv@gmail.com`.
- The personal-data policy is available from the form and the footer in a
  square, native dialog that follows the site's paper-and-ink system.
- Keep the first-visit notice compact and service-like: a small label, one
  explanatory sentence and the decision controls. Do not use a display-sized
  consent headline.
- Keep the notice provider-neutral in its visible summary; provider details
  remain explicit inside the legal policy.
- Contact actions in the header and contact section use the same square email
  and Telegram icon language. Their accessible names and title text preserve
  the destination details without adding visual noise.
- In the desktop footer, the policy link belongs in the lower-right utility
  position; the brand statement and copyright remain lower-left.
- Form consent is a separate required checkbox. It must not be folded into the
  submit button label or treated as implied by submission.
- Yandex Metrika counter `110906380` is optional. Its script, Webvisor and
  clickmap must not load until the visitor explicitly allows analytics.
- Closing the first-visit notice means "necessary settings only". Store the
  decision locally and do not show the notice again unless site data is cleared.
- Necessary local storage is limited to the language and analytics choice.
- If the form delivery mechanism or analytics provider changes, update the
  policy and consent wording in the same release.

## Accessibility and responsive

- Semantic landmarks, one H1, logical H2/H3 structure, skip link.
- Visible focus states, keyboard-operable language switch and menu, Escape close.
- Mobile menu locks document scroll while open.
- Both `html` and `body` use `overflow-x: clip`.
- Test at 360, 390, 768, 1024, 1440 and 1920px.
- Hash aliases keep old service links from becoming dead ends on GitHub Pages.

## Provenance

- DDC terminal identity: existing project and owner-authored Figma prototype.
- Frost Ember: positioning principle only — integrated product partner instead
  of separate executors. No structure, visual assets, or copy were reproduced.
- Master brief received 2026-07-20 and treated as the current design direction.
