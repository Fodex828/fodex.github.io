# SD Printings — Design System

## Brand & thesis

SD Printings is a five-person digital printing studio producing t-shirts, sarees,
and (soon) fully custom prints. The one thing a visitor should walk away with:
**quality good enough that they never look elsewhere again.**

**Thesis line:** "Quality prints, customers who never turn back."

Direction: **Filigree Ink** — built directly from the client's own logo, an
intricate hand-drawn scroll-and-flourish monogram. The page should feel like
that logo: deep, confident, and detailed where it counts, quiet everywhere else.

## Audience & the one job

Local customers browsing product categories (t-shirts, sarees, custom prints)
who decide, within the visit, to reach out by **phone call, WhatsApp, or
Facebook**. The page's one job is to build enough trust in the work shown that
the visitor picks up one of those three channels. There is no cart, no
checkout — contact is the conversion.

## Palette (OKLCH, named roles)

| Role | Value | Use |
|---|---|---|
| `--bg` | `oklch(20% 0.045 320)` | Page background — deep violet ink |
| `--surface` | `oklch(26% 0.05 320)` | Cards, product panels |
| `--surface-raised` | `oklch(30% 0.055 322)` | Hover / active surface state |
| `--ink` | `oklch(96% 0.01 320)` | Primary text |
| `--ink-muted` | `oklch(78% 0.03 320)` | Secondary text, captions |
| `--accent` | `oklch(65% 0.22 350)` | The one saturated colour — CTAs, links, active states, flourish strokes |
| `--violet-quiet` | `oklch(55% 0.09 300)` | Secondary decorative colour — dividers, icon lines, tags |
| `--border` | `oklch(100% 0 0 / 8%)` | Hairline borders on dark surfaces |

Rule: **one saturated accent only** (`--accent`). `--violet-quiet` never
competes with it in the same element — use one or the other, not both, on any
single component.

## Type (display / body / utility)

- **Display** — Cormorant Garamond, italic, weight 600. Used for the hero
  thesis line, section headlines, and product names only. Never body copy.
- **Body** — Manrope, weights 400/500/700. Used for paragraphs, nav, buttons,
  form labels.
- **Utility** — JetBrains Mono, weights 400/500. Used for category tags,
  prices, hours, phone/WhatsApp numbers, and any small structural label.

**Scale:**
- Hero display: `clamp(2.5rem, 6vw, 4.5rem)` / line-height 1.05
- Section display: `clamp(1.75rem, 3.5vw, 2.5rem)` / line-height 1.15
- Body: `1rem` / line-height 1.6
- Body large (lede): `1.125rem` / line-height 1.6
- Utility: `0.75rem`, letter-spacing `0.08em`, uppercase

**Do:** set display type in italic Cormorant with generous line-height so the
letterforms can breathe — that's where the logo's character lives.
**Don't:** use Cormorant below 18px, use more than two weights of Manrope on
one screen, or set utility type in anything but JetBrains Mono.

## Layout & spacing

8px base unit. Section vertical padding: 96px desktop / 56px mobile. Content
max-width 1180px, hero copy max-width 640px (centered, narrow — the thesis
should read like a headline, not a paragraph).

Product showcase uses an **asymmetric grid**: a featured product runs larger
(spans 2 columns) among standard single-column cards, so the grid doesn't read
as a uniform catalogue wall.

```
[ HERO — centered, narrow, generous top/bottom space ]

[ big product ][ card ]
[ card         ][ card ]
[ card ][ card ][ card ]

[ ABOUT / TEAM — short, one photo, one paragraph ]

[ CONTACT — call / whatsapp / facebook, equal weight ]
```

## Signature element

**The flourish rule.** A single hand-drawn line-art ornament (derived from the
logo's own scrollwork, redrawn as a thin SVG stroke in `--accent`) appears
under the hero thesis line and nowhere else on first load. It may reappear
once per section as a small corner accent on the featured product card. It
never appears twice in the same viewport, never as a repeating pattern, and
never as a background texture. This is the one piece of ornament the whole
site is allowed — everything else stays plain.

## Motion (structural + polish)

**Structural:** on page load, the hero thesis line and flourish fade up
together (250ms, ease-out, 80ms stagger) — a single orchestrated moment, not a
sequence of separate animations.

**Scroll behaviour (revised at client request):** the hero — logo, thesis,
flourish, lede, actions, and gallery — fades and lifts slightly as the
visitor scrolls past it, rather than staying static. This replaces the
original "no scroll-triggered motion" rule for the hero specifically; it
still doesn't apply anywhere else on the page (no scroll reveals on the
showcase, about, or contact sections).

**Hero gallery:** an auto-advancing slideshow sits under the hero actions,
crossfading between photos of finished work every 4 seconds. It pauses on
hover and stops advancing entirely under `prefers-reduced-motion` (first
slide stays visible, static).

**Polish:** product cards lift 4px with a soft shadow on hover; the flourish
under the hero thesis very slightly redraws (stroke-dashoffset) on load only.
Product detail pages use a click-to-swap thumbnail gallery — no auto-advance
there, since the visitor is already choosing what to look at.

**Restraint rule:** beyond the hero fade and gallery, motion happens once (on
load) or in direct response to a hover — never ambient, never elsewhere on
scroll. `prefers-reduced-motion` disables the load fade, the hero scroll-fade,
the stroke-draw, and the gallery auto-advance; content simply appears in
place and the first gallery slide stays put.

## Components

- **Nav** — logo mark (left), category anchors (center, optional on scroll),
  a single filled `--accent` "WhatsApp" button (right). Sticky, background
  fades from transparent to `--surface` after scroll.
- **Hero** — logo mark, thesis line (display), one-sentence lede (body,
  `--ink-muted`), flourish divider, auto-advancing photo gallery. Fades on
  scroll (see Motion).
- **Product card** — image, product name (display, small), category tag
  (utility, `--violet-quiet`), one-line description. Links to a full detail
  page rather than scrolling to contact. Manual content — see Assets plan.
- **Product detail page** (`/products/<slug>.html`) — click-to-swap photo
  gallery (main image + up to 4 thumbnails), product name, tag, description,
  WhatsApp/Call actions, and a "More from SD Printings" strip of the other
  products using the same product-card component.
- **Contact block** — three equal-weight actions: Call, WhatsApp, Facebook.
  Each shows the actual number/handle in utility type, not just an icon.
- **Footer** — logo mark, hours (utility: "Open daily · 7am–9pm"), contact
  repeat, categories.

## Copy rules

- Active voice, plain verbs, sentence case. No "Welcome to" openers, no
  "we are passionate about" filler.
- Say what the shop actually does before saying how good it is: category
  first, quality claim second, never quality claim alone.
- Every CTA names the channel, not a generic verb: "Call SD Printings",
  "Message on WhatsApp", not "Get in touch."
- Hours and contact info are never hidden behind a click — they're visible in
  nav or footer at all times.

## Assets plan

| Asset | Look | Source |
|---|---|---|
| Logo mark | As supplied — line-art filigree monogram, used on `--bg` at full contrast | Client-supplied (`assets/logo.png`) |
| Hero background/photo | Optional — team at work or a single finished garment, lit warm against the violet ground | Client to add later — **marked with `//` comment in index.html** |
| Product images (t-shirt, saree, custom) | Product-on-plain-background or in-use shots, consistent crop ratio | Client uploads manually — **marked with `//` comment placeholders** |
| Team/about photo | Candid, one shot, not posed stock | Client to add later |

## Conversion essentials

- Call, WhatsApp, and Facebook are always equal-weight — no single channel is
  pushed over another, since the client uses all three.
- Hours ("Open daily · 7am–9pm") shown in both nav-adjacent area and footer.
- Phone number and WhatsApp number rendered as real `tel:` / `wa.me` links,
  not images.
- No form, no email capture — contact is direct and immediate, matching how
  the client actually operates.

## Anti-patterns

- No cream background, no terracotta accent, no broadsheet hairline grid —
  the three AI-default looks this brief deliberately avoids.
- No gradient text, no glassmorphism, no Inter as body face.
- No stock-photo people in blazers. No numbered "01 / 02 / 03" process
  markers — nothing here is a sequence.
- No more than one flourish visible at a time.

## References

Primary and only visual reference: the client's own logo (hand-drawn filigree
"SD" monogram). No external sites were supplied; the direction is derived
entirely from the mark and the client's described scene (rich violet, slight
pink, five-person print studio).
