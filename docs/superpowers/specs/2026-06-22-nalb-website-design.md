# NALB Website Design Spec
**No Animal Left Behind Search & Rescue**
Date: 2026-06-22
Domain: nalbrescue.com

---

## Overview

A simple, warm single-page website for No Animal Left Behind Search & Rescue — a volunteer-run nonprofit operating in Gilpin County, CO and surrounding mountain communities. The site serves four audiences: people with a lost/found animal, potential donors and supporters, community members, and partner agencies. Donate and Contact are priority CTAs throughout.

The site is built in plain HTML + CSS (no framework, no build step) for simplicity, speed, and easy handoff.

---

## Organization Context

- **Full name:** No Animal Left Behind Search & Rescue
- **Abbreviation:** NALB
- **Emergency arm:** NALB-ERT (No Animal Left Behind Emergency Response Team)
- **Type:** Nonprofit (umbrella organization)
- **Phone:** (303) 653-4799
- **Facebook:** https://www.facebook.com/NoAnimalLeftBehindSearchAndRescue
- **Service area:** Gilpin County, CO (Black Hawk, Central City), Boulder County, Unincorporated Jefferson County, Idaho Springs, Evergreen, Georgetown
- **Key credential:** MOU with the Gilpin County Sheriff's Office
- **Gap they fill:** No animal control exists in Gilpin County
- **Rating:** 100% recommend (7 Facebook reviews)

> **Content needed from owner:**
> - Founding year / how long established
> - Origin story (how NALB started)
> - Donate link / payment method (PayPal, Venmo, etc.)
> - Email address
> - Any specific rescue stories or photos approved for use
> - Donation banner copy (the urgency message)

---

## Tone & Voice

Warm, community-driven, approachable. Feels like neighbors helping neighbors in the mountains. The mission-forward copy leads with heart; credentials (MOU, ER team) are present but don't dominate. Copy pulled/adapted from Facebook where possible to preserve the owner's authentic voice.

---

## Visual Design

### Color Palette

| Role | Color | Hex |
|------|-------|-----|
| Primary / Hero bg | Deep sky blue | `#1A3A5C` |
| Primary gradient end | Mid blue | `#4A90C4` |
| Body bg | Cream | `#F8F4EF` |
| Card bg | White | `#ffffff` |
| Border / divider | Warm sand | `#E0D8CF` |
| CTA primary (blue) | Gradient `#2E6DA4` → `#4A90C4` | — |
| Accent / donate banner | Warm earth | `#A0785A` → `#C4924A` |
| Text primary | Near-black | `#1D1D1F` |
| Text secondary | Medium grey | `#555555` |
| Text on blue | White | `#FFFFFF` |
| Text muted on blue | 75% white | `rgba(255,255,255,0.75)` |

### Typography

| Role | Font | Weight |
|------|------|--------|
| Headings | Lora (Google Fonts, serif) | 700 |
| Subheadings / labels | Lora | 600 |
| Body copy | Inter (Google Fonts, sans-serif) | 400 |
| UI / buttons / nav | Inter | 500–700 |

### Buttons

| Tier | Style |
|------|-------|
| Primary | Blue gradient fill, white text, 6px radius, subtle drop shadow |
| Secondary | Outlined (2px border), no fill, 6px radius |
| Tertiary | Text link with underline, no border |

Donate uses the warm earth gradient (`#A0785A` → `#C4924A`) as an alternate primary to visually distinguish it from action CTAs.

### Background Pattern

Mixed animal face silhouettes (dog, cat, horse) at varied sizes and rotations, implemented as a tiled SVG CSS background. 400×400px tile, ~18 animals per repeat.

- **On blue (hero, contact section):** white fills at 5–7% opacity
- **On cream (body sections):** navy fills at 4–8% opacity

---

## Page Structure

Single scrolling page. Sticky top navigation. Seven sections in order:

```
[Nav]
[1] Hero
[2] Donate Urgency Banner
[3] What We Do
[4] Our Story
[5] Areas We Serve
[6] Contact
[Footer]
```

---

## Section Specs

### Navigation (sticky)
- **Left:** NALB logo SVG (white version for dark nav bg)
- **Center:** Anchor links — About · What We Do · Areas · Contact
- **Right:** Donate button (primary blue gradient)
- **Mobile:** Center links collapse to hamburger; Donate stays visible
- **Background:** `#1A3A5C` (matches hero, seamless transition)

### 1. Hero
- **Background:** Blue + animal face pattern
- **Content (centered):**
  - NALB logo (large, white)
  - Headline: *"No Animal Left Behind"* — Lora 700, white
  - Subline: *"Search & Rescue · Emergency Response · Gilpin County, CO"* — Inter, small caps, muted white
  - Body copy: 2 sentences, warm/mission-forward — **[CONTENT NEEDED FROM OWNER]**
  - CTAs: **Donate** (earth gradient primary) + **Contact Us** (outlined secondary)

### 2. Donate Urgency Banner
- **Background:** Warm earth gradient (`#A0785A` → `#C4924A`)
- **Content (centered):**
  - Short urgency line — **[COPY NEEDED: e.g. "Volunteer-run. No public funding. Every dollar goes directly to the animals."]**
  - CTA: **Support NALB →** (white button, earth text)
- **Note:** Copy to be refined with owner in v1 review

### 3. What We Do
- **Background:** Cream + subtle animal face pattern
- **Content (centered):**
  - Section label: "What We Do" — Inter, small caps, blue accent
  - Heading: Lora 700, `#1A3A5C`
  - Subtext: 1–2 sentences about the gap NALB fills
  - Two cards side by side:
    - **Search & Rescue** — NALB logo, description, Gilpin County gap callout
    - **NALB-ERT** — NALB-ERT logo, description, MOU with Sheriff's Office badge

### 4. Our Story
- **Background:** White
- **Content (centered, single column):**
  - Section label + Lora heading
  - Origin story paragraphs — **[CONTENT NEEDED FROM OWNER]**
  - Callout block (blue accent): Founding year / "Established X years" stat
  - Optional: pull quote from owner
- **Note:** Content to be pulled from Facebook posts or provided directly by owner

### 5. Areas We Serve
- **Background:** Cream + animal face pattern
- **Content (centered):**
  - Section label + heading
  - Badge/tag layout listing communities:
    - Gilpin County (Black Hawk · Central City)
    - Boulder County
    - Unincorporated Jefferson County
    - Idaho Springs
    - Evergreen · Georgetown
  - Tagline: *"If there's no one else to call, we're the call."*

### 6. Contact
- **Background:** Blue + animal face pattern
- **Content (centered):**
  - Heading: *"Get In Touch"*
  - Phone: (303) 653-4799
  - Facebook link (tertiary CTA)
  - Email — **[NEEDED FROM OWNER]**
  - Short note about response and when/how to reach them — **[NEEDED FROM OWNER]**
  - CTA: **Donate** (earth gradient)

### Footer
- **Background:** `#0F2438` (darker navy)
- **Content:** © NALB · nalbrescue.com · Facebook link
- **Font:** Inter, small, muted white

---

## Content Placeholders (Owner Input Required)

- [ ] Founding year and origin story
- [ ] Hero body copy (2 sentences in owner's voice)
- [ ] Donate urgency banner copy
- [ ] Donate link / payment platform
- [ ] Email address
- [ ] Any approved rescue photos or videos
- [ ] Contact section response-time note

---

## Tech Stack

- **HTML:** Single `index.html` file
- **CSS:** Single `styles.css` file (no framework)
- **Fonts:** Google Fonts — Lora + Inter (single `<link>` tag)
- **Images:** NALB and NALB-ERT logos (provided as PNG/SVG)
- **Hosting:** TBD — GitHub Pages or Netlify recommended (free tier)
- **Domain:** nalbrescue.com (already owned)

---

## Out of Scope for v1

- Photos/videos gallery (deferred to post-owner sync)
- Online donation form (link out to external platform)
- CMS or editable backend
- Multi-page structure
- Map embed

---

## Reference

- Logo files: NALB (infinity + paw + heart), NALB-ERT (infinity + horse/dog/cat + flame)
- Anti-pattern reference: Summit County Lost Pets Rescue site (information overload, inconsistent IA and fonts — avoid)
- Facebook: https://www.facebook.com/NoAnimalLeftBehindSearchAndRescue
