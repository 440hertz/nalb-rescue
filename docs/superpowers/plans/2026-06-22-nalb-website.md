# NALB Website Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Build a single-page HTML/CSS website for No Animal Left Behind Search & Rescue at nalbrescue.com.

**Architecture:** One `index.html` and one `styles.css` file. No framework, no build step. CSS custom properties for the design system. Sections are built top-to-bottom in HTML order matching the scroll order. The animal face background pattern is an inline SVG data URI in CSS.

**Tech Stack:** HTML5, CSS3 (custom properties, flexbox, grid), Google Fonts (Lora + Inter), vanilla JS (hamburger menu only).

---

## File Structure

```
nalb-rescue/
├── index.html          # Single page — all markup
├── styles.css          # All styles — design system + layout + sections
├── assets/
│   ├── nalb-logo.png   # NALB logo (provided by client)
│   └── nalb-ert-logo.png  # NALB-ERT logo (provided by client)
└── docs/
    └── superpowers/
        ├── specs/2026-06-22-nalb-website-design.md
        └── plans/2026-06-22-nalb-website.md
```

---

## Task 1: Project scaffold and design system

**Files:**
- Create: `index.html`
- Create: `styles.css`

- [ ] **Step 1: Create `index.html` with base structure**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>No Animal Left Behind Search & Rescue</title>
  <meta name="description" content="Volunteer-run animal search & rescue and emergency response serving Gilpin County, CO and surrounding mountain communities.">
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Lora:wght@400;600;700&family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <!-- Nav -->
  <!-- Hero -->
  <!-- Donate Banner -->
  <!-- What We Do -->
  <!-- Our Story -->
  <!-- Areas We Serve -->
  <!-- Contact -->
  <!-- Footer -->
  <script src="main.js"></script>
</body>
</html>
```

- [ ] **Step 2: Create `styles.css` with the full design system**

```css
/* =====================
   DESIGN SYSTEM
   ===================== */
:root {
  /* Colors */
  --color-blue-dark:    #1A3A5C;
  --color-blue-mid:     #2E6DA4;
  --color-blue-light:   #4A90C4;
  --color-blue-deeper:  #0F2438;
  --color-earth-dark:   #A0785A;
  --color-earth-light:  #C4924A;
  --color-cream:        #F8F4EF;
  --color-white:        #FFFFFF;
  --color-border:       #E0D8CF;
  --color-text:         #1D1D1F;
  --color-text-secondary: #555555;
  --color-text-on-blue: #FFFFFF;
  --color-text-muted-blue: rgba(255,255,255,0.75);
  --color-accent-badge: #EAF3FB;

  /* Gradients */
  --gradient-blue: linear-gradient(135deg, var(--color-blue-mid) 0%, var(--color-blue-light) 100%);
  --gradient-earth: linear-gradient(135deg, var(--color-earth-dark) 0%, var(--color-earth-light) 100%);
  --gradient-hero: linear-gradient(135deg, var(--color-blue-dark) 0%, var(--color-blue-mid) 60%, var(--color-blue-light) 100%);

  /* Animal face pattern — blue */
  --pattern-blue: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='400' height='400'%3E%3Cg fill='rgba(255,255,255,0.07)' transform='translate(10,5) rotate(-12,25,28) scale(0.9)'%3E%3Ccircle cx='25' cy='28' r='18'/%3E%3Cellipse cx='10' cy='20' rx='8' ry='13' transform='rotate(-18,10,20)'/%3E%3Cellipse cx='40' cy='20' rx='8' ry='13' transform='rotate(18,40,20)'/%3E%3Cellipse cx='25' cy='37' rx='11' ry='7'/%3E%3Cellipse cx='25' cy='31' rx='4' ry='3'/%3E%3C/g%3E%3Cg fill='rgba(255,255,255,0.06)' transform='translate(80,12) rotate(18,25,30) scale(0.7)'%3E%3Ccircle cx='25' cy='30' r='17'/%3E%3Cpolygon points='10,18 18,3 24,18'/%3E%3Cpolygon points='26,18 32,3 40,18'/%3E%3Cellipse cx='25' cy='36' rx='6' ry='4'/%3E%3Ccircle cx='25' cy='31' r='2.5'/%3E%3C/g%3E%3Cg fill='rgba(255,255,255,0.05)' transform='translate(155,0) rotate(-6,22,36) scale(0.65)'%3E%3Cellipse cx='22' cy='50' rx='11' ry='18'/%3E%3Ccircle cx='22' cy='28' r='14'/%3E%3Cellipse cx='14' cy='14' rx='4' ry='7' transform='rotate(-10,14,14)'/%3E%3Cellipse cx='30' cy='13' rx='4' ry='7' transform='rotate(10,30,13)'/%3E%3Ccircle cx='18' cy='57' r='3'/%3E%3Ccircle cx='26' cy='58' r='3'/%3E%3C/g%3E%3Cg fill='rgba(255,255,255,0.07)' transform='translate(230,8) rotate(25,25,28) scale(0.8)'%3E%3Ccircle cx='25' cy='28' r='18'/%3E%3Cellipse cx='10' cy='20' rx='8' ry='13' transform='rotate(-18,10,20)'/%3E%3Cellipse cx='40' cy='20' rx='8' ry='13' transform='rotate(18,40,20)'/%3E%3Cellipse cx='25' cy='37' rx='11' ry='7'/%3E%3Cellipse cx='25' cy='31' rx='4' ry='3'/%3E%3C/g%3E%3Cg fill='rgba(255,255,255,0.05)' transform='translate(315,5) rotate(-20,25,30) scale(0.6)'%3E%3Ccircle cx='25' cy='30' r='17'/%3E%3Cpolygon points='10,18 18,3 24,18'/%3E%3Cpolygon points='26,18 32,3 40,18'/%3E%3Cellipse cx='25' cy='36' rx='6' ry='4'/%3E%3C/g%3E%3Cg fill='rgba(255,255,255,0.06)' transform='translate(45,90) rotate(10,22,36) scale(0.75)'%3E%3Cellipse cx='22' cy='50' rx='11' ry='18'/%3E%3Ccircle cx='22' cy='28' r='14'/%3E%3Cellipse cx='14' cy='14' rx='4' ry='7' transform='rotate(-10,14,14)'/%3E%3Cellipse cx='30' cy='13' rx='4' ry='7' transform='rotate(10,30,13)'/%3E%3Ccircle cx='18' cy='57' r='3'/%3E%3Ccircle cx='26' cy='58' r='3'/%3E%3C/g%3E%3Cg fill='rgba(255,255,255,0.07)' transform='translate(130,95) rotate(-15,25,28) scale(1.0)'%3E%3Ccircle cx='25' cy='28' r='18'/%3E%3Cellipse cx='10' cy='20' rx='8' ry='13' transform='rotate(-18,10,20)'/%3E%3Cellipse cx='40' cy='20' rx='8' ry='13' transform='rotate(18,40,20)'/%3E%3Cellipse cx='25' cy='37' rx='11' ry='7'/%3E%3Cellipse cx='25' cy='31' rx='4' ry='3'/%3E%3C/g%3E%3Cg fill='rgba(255,255,255,0.05)' transform='translate(225,88) rotate(22,25,30) scale(0.65)'%3E%3Ccircle cx='25' cy='30' r='17'/%3E%3Cpolygon points='10,18 18,3 24,18'/%3E%3Cpolygon points='26,18 32,3 40,18'/%3E%3Cellipse cx='25' cy='36' rx='6' ry='4'/%3E%3Ccircle cx='25' cy='31' r='2.5'/%3E%3C/g%3E%3Cg fill='rgba(255,255,255,0.06)' transform='translate(320,92) rotate(-8,22,36) scale(0.8)'%3E%3Cellipse cx='22' cy='50' rx='11' ry='18'/%3E%3Ccircle cx='22' cy='28' r='14'/%3E%3Cellipse cx='14' cy='14' rx='4' ry='7' transform='rotate(-10,14,14)'/%3E%3Cellipse cx='30' cy='13' rx='4' ry='7' transform='rotate(10,30,13)'/%3E%3Ccircle cx='18' cy='57' r='3'/%3E%3C/g%3E%3Cg fill='rgba(255,255,255,0.05)' transform='translate(8,185) rotate(30,25,30) scale(0.65)'%3E%3Ccircle cx='25' cy='30' r='17'/%3E%3Cpolygon points='10,18 18,3 24,18'/%3E%3Cpolygon points='26,18 32,3 40,18'/%3E%3Cellipse cx='25' cy='36' rx='6' ry='4'/%3E%3C/g%3E%3Cg fill='rgba(255,255,255,0.07)' transform='translate(85,180) rotate(-5,22,36) scale(0.7)'%3E%3Cellipse cx='22' cy='50' rx='11' ry='18'/%3E%3Ccircle cx='22' cy='28' r='14'/%3E%3Cellipse cx='14' cy='14' rx='4' ry='7' transform='rotate(-10,14,14)'/%3E%3Cellipse cx='30' cy='13' rx='4' ry='7' transform='rotate(10,30,13)'/%3E%3Ccircle cx='18' cy='57' r='3'/%3E%3Ccircle cx='26' cy='58' r='3'/%3E%3C/g%3E%3Cg fill='rgba(255,255,255,0.06)' transform='translate(178,188) rotate(-28,25,28) scale(0.9)'%3E%3Ccircle cx='25' cy='28' r='18'/%3E%3Cellipse cx='10' cy='20' rx='8' ry='13' transform='rotate(-18,10,20)'/%3E%3Cellipse cx='40' cy='20' rx='8' ry='13' transform='rotate(18,40,20)'/%3E%3Cellipse cx='25' cy='37' rx='11' ry='7'/%3E%3Cellipse cx='25' cy='31' rx='4' ry='3'/%3E%3C/g%3E%3Cg fill='rgba(255,255,255,0.05)' transform='translate(280,182) rotate(14,25,30) scale(0.7)'%3E%3Ccircle cx='25' cy='30' r='17'/%3E%3Cpolygon points='10,18 18,3 24,18'/%3E%3Cpolygon points='26,18 32,3 40,18'/%3E%3Cellipse cx='25' cy='36' rx='6' ry='4'/%3E%3Ccircle cx='25' cy='31' r='2.5'/%3E%3C/g%3E%3Cg fill='rgba(255,255,255,0.06)' transform='translate(355,190) rotate(-18,25,28) scale(0.75)'%3E%3Ccircle cx='25' cy='28' r='18'/%3E%3Cellipse cx='10' cy='20' rx='8' ry='13' transform='rotate(-18,10,20)'/%3E%3Cellipse cx='40' cy='20' rx='8' ry='13' transform='rotate(18,40,20)'/%3E%3Cellipse cx='25' cy='37' rx='11' ry='7'/%3E%3C/g%3E%3Cg fill='rgba(255,255,255,0.06)' transform='translate(30,278) rotate(8,22,36) scale(0.85)'%3E%3Cellipse cx='22' cy='50' rx='11' ry='18'/%3E%3Ccircle cx='22' cy='28' r='14'/%3E%3Cellipse cx='14' cy='14' rx='4' ry='7' transform='rotate(-10,14,14)'/%3E%3Cellipse cx='30' cy='13' rx='4' ry='7' transform='rotate(10,30,13)'/%3E%3Ccircle cx='18' cy='57' r='3'/%3E%3Ccircle cx='26' cy='58' r='3'/%3E%3C/g%3E%3Cg fill='rgba(255,255,255,0.05)' transform='translate(115,285) rotate(-22,25,30) scale(0.6)'%3E%3Ccircle cx='25' cy='30' r='17'/%3E%3Cpolygon points='10,18 18,3 24,18'/%3E%3Cpolygon points='26,18 32,3 40,18'/%3E%3Cellipse cx='25' cy='36' rx='6' ry='4'/%3E%3C/g%3E%3Cg fill='rgba(255,255,255,0.07)' transform='translate(205,275) rotate(16,25,28) scale(0.95)'%3E%3Ccircle cx='25' cy='28' r='18'/%3E%3Cellipse cx='10' cy='20' rx='8' ry='13' transform='rotate(-18,10,20)'/%3E%3Cellipse cx='40' cy='20' rx='8' ry='13' transform='rotate(18,40,20)'/%3E%3Cellipse cx='25' cy='37' rx='11' ry='7'/%3E%3Cellipse cx='25' cy='31' rx='4' ry='3'/%3E%3C/g%3E%3Cg fill='rgba(255,255,255,0.05)' transform='translate(305,282) rotate(-10,22,36) scale(0.6)'%3E%3Cellipse cx='22' cy='50' rx='11' ry='18'/%3E%3Ccircle cx='22' cy='28' r='14'/%3E%3Cellipse cx='14' cy='14' rx='4' ry='7' transform='rotate(-10,14,14)'/%3E%3Cellipse cx='30' cy='13' rx='4' ry='7' transform='rotate(10,30,13)'/%3E%3C/g%3E%3C/svg%3E");

  /* Animal face pattern — cream */
  --pattern-cream: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='400' height='400'%3E%3Cg fill='rgba(26,58,92,0.07)' transform='translate(10,5) rotate(-12,25,28) scale(0.9)'%3E%3Ccircle cx='25' cy='28' r='18'/%3E%3Cellipse cx='10' cy='20' rx='8' ry='13' transform='rotate(-18,10,20)'/%3E%3Cellipse cx='40' cy='20' rx='8' ry='13' transform='rotate(18,40,20)'/%3E%3Cellipse cx='25' cy='37' rx='11' ry='7'/%3E%3Cellipse cx='25' cy='31' rx='4' ry='3'/%3E%3C/g%3E%3Cg fill='rgba(26,58,92,0.05)' transform='translate(80,12) rotate(18,25,30) scale(0.7)'%3E%3Ccircle cx='25' cy='30' r='17'/%3E%3Cpolygon points='10,18 18,3 24,18'/%3E%3Cpolygon points='26,18 32,3 40,18'/%3E%3Cellipse cx='25' cy='36' rx='6' ry='4'/%3E%3C/g%3E%3Cg fill='rgba(26,58,92,0.04)' transform='translate(155,0) rotate(-6,22,36) scale(0.65)'%3E%3Cellipse cx='22' cy='50' rx='11' ry='18'/%3E%3Ccircle cx='22' cy='28' r='14'/%3E%3Cellipse cx='14' cy='14' rx='4' ry='7'/%3E%3Cellipse cx='30' cy='13' rx='4' ry='7'/%3E%3C/g%3E%3Cg fill='rgba(26,58,92,0.07)' transform='translate(230,8) rotate(25,25,28) scale(0.8)'%3E%3Ccircle cx='25' cy='28' r='18'/%3E%3Cellipse cx='10' cy='20' rx='8' ry='13' transform='rotate(-18,10,20)'/%3E%3Cellipse cx='40' cy='20' rx='8' ry='13' transform='rotate(18,40,20)'/%3E%3Cellipse cx='25' cy='37' rx='11' ry='7'/%3E%3C/g%3E%3Cg fill='rgba(26,58,92,0.05)' transform='translate(315,5) rotate(-20,25,30) scale(0.6)'%3E%3Ccircle cx='25' cy='30' r='17'/%3E%3Cpolygon points='10,18 18,3 24,18'/%3E%3Cpolygon points='26,18 32,3 40,18'/%3E%3Cellipse cx='25' cy='36' rx='6' ry='4'/%3E%3C/g%3E%3Cg fill='rgba(26,58,92,0.06)' transform='translate(45,90) rotate(10,22,36) scale(0.75)'%3E%3Cellipse cx='22' cy='50' rx='11' ry='18'/%3E%3Ccircle cx='22' cy='28' r='14'/%3E%3Cellipse cx='14' cy='14' rx='4' ry='7' transform='rotate(-10,14,14)'/%3E%3Cellipse cx='30' cy='13' rx='4' ry='7' transform='rotate(10,30,13)'/%3E%3C/g%3E%3Cg fill='rgba(26,58,92,0.07)' transform='translate(130,95) rotate(-15,25,28) scale(1.0)'%3E%3Ccircle cx='25' cy='28' r='18'/%3E%3Cellipse cx='10' cy='20' rx='8' ry='13' transform='rotate(-18,10,20)'/%3E%3Cellipse cx='40' cy='20' rx='8' ry='13' transform='rotate(18,40,20)'/%3E%3Cellipse cx='25' cy='37' rx='11' ry='7'/%3E%3C/g%3E%3Cg fill='rgba(26,58,92,0.05)' transform='translate(225,88) rotate(22,25,30) scale(0.65)'%3E%3Ccircle cx='25' cy='30' r='17'/%3E%3Cpolygon points='10,18 18,3 24,18'/%3E%3Cpolygon points='26,18 32,3 40,18'/%3E%3Cellipse cx='25' cy='36' rx='6' ry='4'/%3E%3C/g%3E%3Cg fill='rgba(26,58,92,0.06)' transform='translate(320,92) rotate(-8,22,36) scale(0.8)'%3E%3Cellipse cx='22' cy='50' rx='11' ry='18'/%3E%3Ccircle cx='22' cy='28' r='14'/%3E%3Cellipse cx='14' cy='14' rx='4' ry='7' transform='rotate(-10,14,14)'/%3E%3Cellipse cx='30' cy='13' rx='4' ry='7' transform='rotate(10,30,13)'/%3E%3C/g%3E%3Cg fill='rgba(26,58,92,0.05)' transform='translate(8,185) rotate(30,25,30) scale(0.65)'%3E%3Ccircle cx='25' cy='30' r='17'/%3E%3Cpolygon points='10,18 18,3 24,18'/%3E%3Cpolygon points='26,18 32,3 40,18'/%3E%3Cellipse cx='25' cy='36' rx='6' ry='4'/%3E%3C/g%3E%3Cg fill='rgba(26,58,92,0.06)' transform='translate(85,180) rotate(-5,22,36) scale(0.7)'%3E%3Cellipse cx='22' cy='50' rx='11' ry='18'/%3E%3Ccircle cx='22' cy='28' r='14'/%3E%3Cellipse cx='14' cy='14' rx='4' ry='7' transform='rotate(-10,14,14)'/%3E%3Cellipse cx='30' cy='13' rx='4' ry='7' transform='rotate(10,30,13)'/%3E%3C/g%3E%3Cg fill='rgba(26,58,92,0.07)' transform='translate(178,188) rotate(-28,25,28) scale(0.9)'%3E%3Ccircle cx='25' cy='28' r='18'/%3E%3Cellipse cx='10' cy='20' rx='8' ry='13' transform='rotate(-18,10,20)'/%3E%3Cellipse cx='40' cy='20' rx='8' ry='13' transform='rotate(18,40,20)'/%3E%3Cellipse cx='25' cy='37' rx='11' ry='7'/%3E%3C/g%3E%3Cg fill='rgba(26,58,92,0.05)' transform='translate(280,182) rotate(14,25,30) scale(0.7)'%3E%3Ccircle cx='25' cy='30' r='17'/%3E%3Cpolygon points='10,18 18,3 24,18'/%3E%3Cpolygon points='26,18 32,3 40,18'/%3E%3Cellipse cx='25' cy='36' rx='6' ry='4'/%3E%3C/g%3E%3Cg fill='rgba(26,58,92,0.06)' transform='translate(355,190) rotate(-18,25,28) scale(0.75)'%3E%3Ccircle cx='25' cy='28' r='18'/%3E%3Cellipse cx='10' cy='20' rx='8' ry='13' transform='rotate(-18,10,20)'/%3E%3Cellipse cx='40' cy='20' rx='8' ry='13' transform='rotate(18,40,20)'/%3E%3Cellipse cx='25' cy='37' rx='11' ry='7'/%3E%3C/g%3E%3Cg fill='rgba(26,58,92,0.06)' transform='translate(30,278) rotate(8,22,36) scale(0.85)'%3E%3Cellipse cx='22' cy='50' rx='11' ry='18'/%3E%3Ccircle cx='22' cy='28' r='14'/%3E%3Cellipse cx='14' cy='14' rx='4' ry='7' transform='rotate(-10,14,14)'/%3E%3Cellipse cx='30' cy='13' rx='4' ry='7' transform='rotate(10,30,13)'/%3E%3C/g%3E%3Cg fill='rgba(26,58,92,0.05)' transform='translate(115,285) rotate(-22,25,30) scale(0.6)'%3E%3Ccircle cx='25' cy='30' r='17'/%3E%3Cpolygon points='10,18 18,3 24,18'/%3E%3Cpolygon points='26,18 32,3 40,18'/%3E%3Cellipse cx='25' cy='36' rx='6' ry='4'/%3E%3C/g%3E%3Cg fill='rgba(26,58,92,0.07)' transform='translate(205,275) rotate(16,25,28) scale(0.95)'%3E%3Ccircle cx='25' cy='28' r='18'/%3E%3Cellipse cx='10' cy='20' rx='8' ry='13' transform='rotate(-18,10,20)'/%3E%3Cellipse cx='40' cy='20' rx='8' ry='13' transform='rotate(18,40,20)'/%3E%3Cellipse cx='25' cy='37' rx='11' ry='7'/%3E%3C/g%3E%3Cg fill='rgba(26,58,92,0.05)' transform='translate(305,282) rotate(-10,22,36) scale(0.6)'%3E%3Cellipse cx='22' cy='50' rx='11' ry='18'/%3E%3Ccircle cx='22' cy='28' r='14'/%3E%3Cellipse cx='14' cy='14' rx='4' ry='7' transform='rotate(-10,14,14)'/%3E%3Cellipse cx='30' cy='13' rx='4' ry='7' transform='rotate(10,30,13)'/%3E%3C/g%3E%3C/svg%3E");

  /* Typography */
  --font-heading: 'Lora', Georgia, serif;
  --font-body: 'Inter', system-ui, sans-serif;

  /* Spacing */
  --section-padding: 5rem 1.5rem;
  --max-width: 900px;
  --card-radius: 10px;
  --btn-radius: 6px;
}

/* =====================
   RESET & BASE
   ===================== */
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
html { scroll-behavior: smooth; }
body {
  font-family: var(--font-body);
  color: var(--color-text);
  background: var(--color-cream);
  line-height: 1.6;
}
img { max-width: 100%; display: block; }
a { color: inherit; text-decoration: none; }

/* =====================
   UTILITY
   ===================== */
.container {
  max-width: var(--max-width);
  margin: 0 auto;
  padding: 0 1.5rem;
}
.section-label {
  font-family: var(--font-body);
  font-size: 0.7rem;
  font-weight: 700;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: var(--color-blue-light);
  margin-bottom: 0.75rem;
}
.section-label--white {
  color: rgba(255,255,255,0.65);
}

/* =====================
   BUTTONS
   ===================== */
.btn {
  display: inline-block;
  font-family: var(--font-body);
  font-weight: 700;
  font-size: 0.95rem;
  padding: 0.65rem 1.5rem;
  border-radius: var(--btn-radius);
  cursor: pointer;
  transition: opacity 0.2s ease, transform 0.1s ease;
  text-decoration: none;
}
.btn:hover { opacity: 0.9; transform: translateY(-1px); }
.btn:active { transform: translateY(0); }

.btn--primary {
  background: var(--gradient-blue);
  color: var(--color-white);
  box-shadow: 0 2px 8px rgba(26,58,92,0.3);
  border: none;
}
.btn--donate {
  background: var(--gradient-earth);
  color: var(--color-white);
  box-shadow: 0 2px 8px rgba(160,120,90,0.35);
  border: none;
}
.btn--secondary {
  background: transparent;
  color: var(--color-white);
  border: 2px solid rgba(255,255,255,0.7);
}
.btn--secondary-dark {
  background: transparent;
  color: var(--color-blue-dark);
  border: 2px solid var(--color-blue-dark);
}
.btn--text {
  color: var(--color-blue-light);
  text-decoration: underline;
  text-underline-offset: 3px;
  padding: 0;
  font-weight: 600;
}
.btn--text-white {
  color: rgba(255,255,255,0.85);
  text-decoration: underline;
  text-underline-offset: 3px;
  padding: 0;
  font-weight: 600;
}
```

- [ ] **Step 3: Commit the scaffold**

```bash
cd /Users/ezrashelton/Projects/nalb-rescue
git add index.html styles.css
git commit -m "feat: project scaffold and design system"
```

Expected output: `[main ...] feat: project scaffold and design system`

---

## Task 2: Navigation

**Files:**
- Modify: `index.html` — replace `<!-- Nav -->` comment
- Modify: `styles.css` — append nav styles
- Create: `main.js` — hamburger toggle

- [ ] **Step 1: Add nav markup to `index.html`**

Replace `<!-- Nav -->` with:

```html
<header class="nav" id="nav">
  <div class="nav__inner">
    <a href="#" class="nav__logo" aria-label="NALB Home">
      <img src="assets/nalb-logo.png" alt="No Animal Left Behind" class="nav__logo-img">
    </a>
    <button class="nav__hamburger" id="navToggle" aria-label="Open menu" aria-expanded="false">
      <span></span><span></span><span></span>
    </button>
    <nav class="nav__links" id="navLinks">
      <a href="#about" class="nav__link">About</a>
      <a href="#what-we-do" class="nav__link">What We Do</a>
      <a href="#areas" class="nav__link">Areas</a>
      <a href="#contact" class="nav__link">Contact</a>
    </nav>
    <a href="#donate" class="btn btn--primary nav__cta">Donate</a>
  </div>
</header>
```

- [ ] **Step 2: Append nav styles to `styles.css`**

```css
/* =====================
   NAV
   ===================== */
.nav {
  position: sticky;
  top: 0;
  z-index: 100;
  background: var(--color-blue-dark);
  border-bottom: 1px solid rgba(255,255,255,0.08);
}
.nav__inner {
  max-width: var(--max-width);
  margin: 0 auto;
  padding: 0.85rem 1.5rem;
  display: flex;
  align-items: center;
  gap: 1.5rem;
}
.nav__logo-img {
  height: 36px;
  width: auto;
  filter: brightness(0) invert(1);
}
.nav__links {
  display: flex;
  gap: 1.5rem;
  flex: 1;
  justify-content: center;
}
.nav__link {
  font-family: var(--font-body);
  font-size: 0.875rem;
  font-weight: 500;
  color: rgba(255,255,255,0.85);
  transition: color 0.2s;
}
.nav__link:hover { color: var(--color-white); }
.nav__cta { font-size: 0.875rem; padding: 0.45rem 1.1rem; white-space: nowrap; }
.nav__hamburger {
  display: none;
  flex-direction: column;
  gap: 5px;
  background: none;
  border: none;
  cursor: pointer;
  padding: 4px;
  margin-left: auto;
}
.nav__hamburger span {
  display: block;
  width: 22px;
  height: 2px;
  background: white;
  border-radius: 2px;
  transition: transform 0.2s, opacity 0.2s;
}

@media (max-width: 640px) {
  .nav__links {
    display: none;
    flex-direction: column;
    position: absolute;
    top: 100%;
    left: 0;
    right: 0;
    background: var(--color-blue-dark);
    padding: 1rem 1.5rem;
    gap: 1rem;
    border-bottom: 1px solid rgba(255,255,255,0.1);
  }
  .nav__links.is-open { display: flex; }
  .nav__hamburger { display: flex; }
  .nav__inner { flex-wrap: wrap; }
}
```

- [ ] **Step 3: Create `main.js` for hamburger toggle**

```javascript
const toggle = document.getElementById('navToggle');
const links = document.getElementById('navLinks');

toggle.addEventListener('click', () => {
  const open = links.classList.toggle('is-open');
  toggle.setAttribute('aria-expanded', open);
});

links.querySelectorAll('.nav__link').forEach(link => {
  link.addEventListener('click', () => {
    links.classList.remove('is-open');
    toggle.setAttribute('aria-expanded', false);
  });
});
```

- [ ] **Step 4: Open `index.html` in browser and verify**

```bash
open /Users/ezrashelton/Projects/nalb-rescue/index.html
```

Expected: Sticky dark blue nav bar with logo on left, links center, Donate button right. On narrow window hamburger appears, links collapse.

- [ ] **Step 5: Commit**

```bash
git add index.html styles.css main.js
git commit -m "feat: sticky navigation with mobile hamburger"
```

---

## Task 3: Hero section

**Files:**
- Modify: `index.html` — replace `<!-- Hero -->` comment
- Modify: `styles.css` — append hero styles

- [ ] **Step 1: Add hero markup**

Replace `<!-- Hero -->` with:

```html
<section class="hero" id="about">
  <div class="hero__inner container">
    <img src="assets/nalb-logo.png" alt="NALB" class="hero__logo">
    <h1 class="hero__title">No Animal Left Behind</h1>
    <p class="hero__sub">Search & Rescue &middot; Emergency Response &middot; Gilpin County, CO</p>
    <p class="hero__body">
      <!-- PLACEHOLDER: Replace with owner's voice. Suggested: -->
      When an animal is lost, stranded, or in danger in the Colorado mountains,
      we show up. Serving Gilpin County and the surrounding communities where
      no animal control exists.
    </p>
    <div class="hero__ctas">
      <a href="#donate" class="btn btn--donate">Donate</a>
      <a href="#contact" class="btn btn--secondary">Contact Us</a>
    </div>
  </div>
</section>
```

- [ ] **Step 2: Append hero styles to `styles.css`**

```css
/* =====================
   HERO
   ===================== */
.hero {
  background-color: var(--color-blue-dark);
  background-image: var(--pattern-blue);
  background-size: 400px 400px;
  padding: 6rem 1.5rem 5rem;
  text-align: center;
}
.hero__inner { display: flex; flex-direction: column; align-items: center; gap: 1rem; }
.hero__logo { height: 100px; width: auto; filter: brightness(0) invert(1); margin-bottom: 0.5rem; }
.hero__title {
  font-family: var(--font-heading);
  font-size: clamp(2rem, 5vw, 3rem);
  font-weight: 700;
  color: var(--color-white);
  line-height: 1.2;
}
.hero__sub {
  font-family: var(--font-body);
  font-size: 0.8rem;
  font-weight: 600;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--color-text-muted-blue);
}
.hero__body {
  font-size: 1.05rem;
  color: rgba(255,255,255,0.88);
  max-width: 540px;
  line-height: 1.7;
}
.hero__ctas { display: flex; gap: 1rem; flex-wrap: wrap; justify-content: center; margin-top: 0.5rem; }
```

- [ ] **Step 3: Verify in browser**

Reload `index.html`. Expected: Full-width blue hero with animal face pattern, centered logo, headline in Lora, subline, body copy, and two buttons.

- [ ] **Step 4: Commit**

```bash
git add index.html styles.css
git commit -m "feat: hero section"
```

---

## Task 4: Donate urgency banner

**Files:**
- Modify: `index.html` — replace `<!-- Donate Banner -->` comment
- Modify: `styles.css` — append banner styles

- [ ] **Step 1: Add banner markup**

Replace `<!-- Donate Banner -->` with:

```html
<section class="donate-banner" id="donate">
  <div class="donate-banner__inner container">
    <p class="donate-banner__text">
      <!-- PLACEHOLDER: Replace with owner's copy -->
      Volunteer-run. No public funding. Every dollar goes directly to the animals.
    </p>
    <a href="#" class="btn donate-banner__btn">
      <!-- PLACEHOLDER: Replace href with actual donate link (PayPal/Venmo/etc.) -->
      Support NALB &rarr;
    </a>
  </div>
</section>
```

- [ ] **Step 2: Append banner styles to `styles.css`**

```css
/* =====================
   DONATE BANNER
   ===================== */
.donate-banner {
  background: var(--gradient-earth);
  padding: 1.5rem;
  text-align: center;
}
.donate-banner__inner {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1rem;
}
.donate-banner__text {
  font-family: var(--font-body);
  font-size: 1rem;
  font-weight: 600;
  color: var(--color-white);
}
.donate-banner__btn {
  background: var(--color-white);
  color: var(--color-earth-dark);
  font-weight: 700;
  padding: 0.5rem 1.4rem;
  border-radius: var(--btn-radius);
  transition: opacity 0.2s;
}
.donate-banner__btn:hover { opacity: 0.9; }

@media (min-width: 640px) {
  .donate-banner__inner { flex-direction: row; justify-content: center; gap: 2rem; }
}
```

- [ ] **Step 3: Verify in browser**

Expected: Warm earth gradient strip below hero with urgency text and white button.

- [ ] **Step 4: Commit**

```bash
git add index.html styles.css
git commit -m "feat: donate urgency banner"
```

---

## Task 5: What We Do section

**Files:**
- Modify: `index.html` — replace `<!-- What We Do -->` comment
- Modify: `styles.css` — append section styles

- [ ] **Step 1: Add What We Do markup**

Replace `<!-- What We Do -->` with:

```html
<section class="what-we-do section--cream" id="what-we-do">
  <div class="container section__inner">
    <p class="section-label">What We Do</p>
    <h2 class="section-heading">When an animal needs help, we show up.</h2>
    <p class="section-subtext">
      There is no animal control in Gilpin County. NALB fills that gap —
      for lost pets, unknown animals, and large-scale emergencies alike.
    </p>
    <div class="cards">
      <div class="card">
        <img src="assets/nalb-logo.png" alt="NALB Search & Rescue" class="card__logo">
        <h3 class="card__title">Search & Rescue</h3>
        <p class="card__body">
          When an animal shows up and no one knows where it came from, we respond.
          From lost pets to unknown animals in the mountains — if no one else can help,
          NALB is the call.
        </p>
      </div>
      <div class="card">
        <img src="assets/nalb-ert-logo.png" alt="NALB Emergency Response Team" class="card__logo">
        <h3 class="card__title">NALB-ERT</h3>
        <p class="card__body">
          The No Animal Left Behind Emergency Response Team deploys during disasters,
          wildfires, and large-scale emergencies across the Front Range.
        </p>
        <span class="card__badge">MOU &middot; Gilpin County Sheriff's Office</span>
      </div>
    </div>
  </div>
</section>
```

- [ ] **Step 2: Append What We Do + shared section styles to `styles.css`**

```css
/* =====================
   SHARED SECTION STYLES
   ===================== */
.section--cream {
  background-color: var(--color-cream);
  background-image: var(--pattern-cream);
  background-size: 400px 400px;
}
.section--white { background: var(--color-white); }
.section--blue {
  background-color: var(--color-blue-dark);
  background-image: var(--pattern-blue);
  background-size: 400px 400px;
}
.section__inner {
  padding: var(--section-padding);
  text-align: center;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1rem;
}
.section-heading {
  font-family: var(--font-heading);
  font-size: clamp(1.4rem, 3vw, 2rem);
  font-weight: 700;
  color: var(--color-blue-dark);
  line-height: 1.25;
  max-width: 600px;
}
.section-heading--white { color: var(--color-white); }
.section-subtext {
  font-size: 1rem;
  color: var(--color-text-secondary);
  max-width: 560px;
  line-height: 1.7;
}
.section-subtext--white { color: rgba(255,255,255,0.82); }

/* =====================
   CARDS
   ===================== */
.cards {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1.5rem;
  width: 100%;
  max-width: 720px;
  margin-top: 1rem;
}
.card {
  background: var(--color-white);
  border-radius: var(--card-radius);
  border: 1px solid var(--color-border);
  padding: 2rem 1.5rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.75rem;
  text-align: center;
}
.card__logo { height: 64px; width: auto; object-fit: contain; }
.card__title {
  font-family: var(--font-heading);
  font-size: 1.1rem;
  font-weight: 700;
  color: var(--color-blue-dark);
}
.card__body {
  font-size: 0.9rem;
  color: var(--color-text-secondary);
  line-height: 1.65;
}
.card__badge {
  display: inline-block;
  font-size: 0.65rem;
  font-weight: 700;
  letter-spacing: 0.06em;
  text-transform: uppercase;
  background: var(--color-accent-badge);
  color: var(--color-blue-dark);
  padding: 0.25rem 0.6rem;
  border-radius: 4px;
  margin-top: 0.25rem;
}

@media (max-width: 540px) {
  .cards { grid-template-columns: 1fr; }
}
```

- [ ] **Step 3: Verify in browser**

Expected: Cream section with pattern, two white cards side by side — NALB logo + S&R description, NALB-ERT logo + ERT description with MOU badge.

- [ ] **Step 4: Commit**

```bash
git add index.html styles.css
git commit -m "feat: what we do section with S&R and NALB-ERT cards"
```

---

## Task 6: Our Story section

**Files:**
- Modify: `index.html` — replace `<!-- Our Story -->` comment
- Modify: `styles.css` — append story styles

- [ ] **Step 1: Add Our Story markup**

Replace `<!-- Our Story -->` with:

```html
<section class="our-story section--white" id="about-story">
  <div class="container section__inner">
    <p class="section-label">Our Story</p>
    <h2 class="section-heading">Born from a love for animals and community.</h2>
    <div class="story__body">
      <p>
        <!-- PLACEHOLDER: Replace with owner's founding story -->
        No Animal Left Behind started when we realized there was a gap that no one
        else was filling — animals in Gilpin County had nowhere to turn when they
        were lost, injured, or in danger. So we showed up.
      </p>
      <p>
        <!-- PLACEHOLDER: Replace with additional story content from owner -->
        What started as a small group of volunteers has grown into a fully organized
        search and rescue operation with an emergency response arm, serving not just
        Gilpin County but the broader mountain communities of Colorado's Front Range.
      </p>
    </div>
    <div class="story__callout">
      <!-- PLACEHOLDER: Replace X with actual founding year -->
      Proudly serving our mountain community since <strong>[YEAR]</strong>.
    </div>
  </div>
</section>
```

- [ ] **Step 2: Append story styles to `styles.css`**

```css
/* =====================
   OUR STORY
   ===================== */
.story__body {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  max-width: 620px;
  text-align: left;
  font-size: 1rem;
  color: var(--color-text-secondary);
  line-height: 1.75;
}
.story__callout {
  margin-top: 0.5rem;
  background: var(--color-accent-badge);
  border-left: 4px solid var(--color-blue-mid);
  padding: 1rem 1.5rem;
  border-radius: 0 var(--btn-radius) var(--btn-radius) 0;
  font-family: var(--font-body);
  font-size: 0.95rem;
  color: var(--color-blue-dark);
  max-width: 480px;
  text-align: left;
}
```

- [ ] **Step 3: Verify in browser**

Expected: White section, centered heading, left-aligned body paragraphs, blue accent callout block with founding year placeholder.

- [ ] **Step 4: Commit**

```bash
git add index.html styles.css
git commit -m "feat: our story section with placeholder copy"
```

---

## Task 7: Areas We Serve section

**Files:**
- Modify: `index.html` — replace `<!-- Areas We Serve -->` comment
- Modify: `styles.css` — append areas styles

- [ ] **Step 1: Add Areas We Serve markup**

Replace `<!-- Areas We Serve -->` with:

```html
<section class="areas section--cream" id="areas">
  <div class="container section__inner">
    <p class="section-label">Where We Work</p>
    <h2 class="section-heading">Serving Colorado's mountain communities.</h2>
    <div class="areas__tags">
      <span class="area-tag">Gilpin County</span>
      <span class="area-tag area-tag--sub">Black Hawk &middot; Central City</span>
      <span class="area-tag">Boulder County</span>
      <span class="area-tag">Unincorporated Jefferson County</span>
      <span class="area-tag">Idaho Springs</span>
      <span class="area-tag">Evergreen</span>
      <span class="area-tag">Georgetown</span>
    </div>
    <p class="areas__tagline">If there's no one else to call, we're the call.</p>
  </div>
</section>
```

- [ ] **Step 2: Append areas styles to `styles.css`**

```css
/* =====================
   AREAS WE SERVE
   ===================== */
.areas__tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.6rem;
  justify-content: center;
  max-width: 600px;
  margin-top: 0.5rem;
}
.area-tag {
  background: var(--color-white);
  border: 1.5px solid var(--color-border);
  border-radius: 999px;
  padding: 0.35rem 1rem;
  font-family: var(--font-body);
  font-size: 0.85rem;
  font-weight: 600;
  color: var(--color-blue-dark);
}
.area-tag--sub {
  background: var(--color-accent-badge);
  border-color: var(--color-blue-light);
  font-size: 0.78rem;
  font-weight: 500;
  color: var(--color-blue-mid);
}
.areas__tagline {
  font-family: var(--font-heading);
  font-size: 1.05rem;
  font-style: italic;
  color: var(--color-blue-mid);
  margin-top: 0.5rem;
}
```

- [ ] **Step 3: Verify in browser**

Expected: Cream + pattern section, pill-shaped location tags, italic tagline below.

- [ ] **Step 4: Commit**

```bash
git add index.html styles.css
git commit -m "feat: areas we serve section"
```

---

## Task 8: Contact section

**Files:**
- Modify: `index.html` — replace `<!-- Contact -->` comment
- Modify: `styles.css` — append contact styles

- [ ] **Step 1: Add Contact markup**

Replace `<!-- Contact -->` with:

```html
<section class="contact section--blue" id="contact">
  <div class="container section__inner">
    <p class="section-label section-label--white">Get In Touch</p>
    <h2 class="section-heading section-heading--white">We're here when you need us.</h2>
    <p class="section-subtext section-subtext--white">
      <!-- PLACEHOLDER: Add owner's note about response time / when to call -->
      Have a lost animal or need to report one? Reach out — we respond as fast as we can.
    </p>
    <div class="contact__details">
      <a href="tel:3036534799" class="contact__item">
        <span class="contact__icon">📞</span>
        <span>(303) 653-4799</span>
      </a>
      <!-- PLACEHOLDER: Replace href with actual email when provided -->
      <a href="mailto:info@nalbrescue.com" class="contact__item">
        <span class="contact__icon">✉️</span>
        <span>info@nalbrescue.com</span>
      </a>
      <a href="https://www.facebook.com/NoAnimalLeftBehindSearchAndRescue" target="_blank" rel="noopener" class="contact__item">
        <span class="contact__icon">👥</span>
        <span>Follow us on Facebook</span>
      </a>
    </div>
    <a href="#donate" class="btn btn--donate" style="margin-top:1rem;">Support Our Work</a>
  </div>
</section>
```

- [ ] **Step 2: Append contact styles to `styles.css`**

```css
/* =====================
   CONTACT
   ===================== */
.contact__details {
  display: flex;
  flex-direction: column;
  gap: 0.85rem;
  align-items: center;
  margin-top: 0.5rem;
}
.contact__item {
  display: flex;
  align-items: center;
  gap: 0.6rem;
  font-family: var(--font-body);
  font-size: 1rem;
  font-weight: 500;
  color: rgba(255,255,255,0.9);
  text-decoration: none;
  transition: color 0.2s;
}
.contact__item:hover { color: var(--color-white); }
.contact__icon { font-size: 1.1rem; }
```

- [ ] **Step 3: Verify in browser**

Expected: Blue + pattern section, white text, phone/email/Facebook links, Donate button at bottom.

- [ ] **Step 4: Commit**

```bash
git add index.html styles.css
git commit -m "feat: contact section"
```

---

## Task 9: Footer

**Files:**
- Modify: `index.html` — replace `<!-- Footer -->` comment
- Modify: `styles.css` — append footer styles

- [ ] **Step 1: Add footer markup**

Replace `<!-- Footer -->` with:

```html
<footer class="footer">
  <div class="container footer__inner">
    <p class="footer__copy">&copy; <span id="year"></span> No Animal Left Behind Search & Rescue &middot; nalbrescue.com</p>
    <a href="https://www.facebook.com/NoAnimalLeftBehindSearchAndRescue" target="_blank" rel="noopener" class="footer__link">Facebook</a>
  </div>
  <script>document.getElementById('year').textContent = new Date().getFullYear();</script>
</footer>
```

- [ ] **Step 2: Append footer styles to `styles.css`**

```css
/* =====================
   FOOTER
   ===================== */
.footer {
  background: var(--color-blue-deeper);
  padding: 1.25rem 1.5rem;
}
.footer__inner {
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  gap: 0.5rem;
}
.footer__copy {
  font-family: var(--font-body);
  font-size: 0.78rem;
  color: rgba(255,255,255,0.45);
}
.footer__link {
  font-family: var(--font-body);
  font-size: 0.78rem;
  color: rgba(255,255,255,0.55);
  text-decoration: underline;
  text-underline-offset: 2px;
  transition: color 0.2s;
}
.footer__link:hover { color: rgba(255,255,255,0.85); }
```

- [ ] **Step 3: Verify full page in browser**

Scroll from top to bottom. Verify:
- Nav sticks at top
- All 6 sections render in correct order
- No layout breaks at narrow widths (resize to 375px)
- Fonts load (Lora for headings, Inter for body)
- All placeholder notes visible for owner content

- [ ] **Step 4: Commit**

```bash
git add index.html styles.css
git commit -m "feat: footer and complete page structure"
```

---

## Task 10: Assets placeholder and final polish

**Files:**
- Create: `assets/` directory with placeholder logo files
- Modify: `styles.css` — mobile final pass

- [ ] **Step 1: Create assets directory and add logo placeholders**

```bash
mkdir -p /Users/ezrashelton/Projects/nalb-rescue/assets
```

Until the actual logo PNGs are provided, create a CSS fallback so the page doesn't break. Add to `styles.css`:

```css
/* Logo fallback if image not yet provided */
.nav__logo-img:not([src]),
.nav__logo-img[src="assets/nalb-logo.png"]:not([naturalWidth]) {
  display: none;
}
.hero__logo[src="assets/nalb-logo.png"]:not([naturalWidth]) {
  display: none;
}
```

- [ ] **Step 2: Final mobile pass — append to `styles.css`**

```css
/* =====================
   MOBILE FINAL PASS
   ===================== */
@media (max-width: 480px) {
  .hero { padding: 4rem 1.25rem 3.5rem; }
  .hero__logo { height: 72px; }
  .section__inner { padding: 3.5rem 1.25rem; }
  .hero__ctas { flex-direction: column; align-items: center; }
  .hero__ctas .btn { width: 100%; text-align: center; }
  .donate-banner__inner { flex-direction: column; }
  .footer__inner { flex-direction: column; align-items: center; text-align: center; }
}
```

- [ ] **Step 3: Verify at 375px width**

Resize browser to 375px. Verify:
- Nav hamburger works, links open/close
- Hero text doesn't overflow
- Cards stack vertically
- Donate banner stacks vertically
- All text is readable (no overflow, no clipping)

- [ ] **Step 4: Final commit**

```bash
git add .
git commit -m "feat: assets structure, mobile polish, complete v1 build"
```

---

## Content Swap Checklist (post-owner sync)

When the owner provides content, update these locations:

| Item | File | Location |
|------|------|----------|
| Hero body copy | `index.html` | `<!-- PLACEHOLDER -->` in `.hero__body` |
| Donate link | `index.html` | `href="#"` on `.donate-banner__btn` |
| Donate banner copy | `index.html` | `<!-- PLACEHOLDER -->` in `.donate-banner__text` |
| Founding year | `index.html` | `[YEAR]` in `.story__callout` |
| Origin story | `index.html` | `<!-- PLACEHOLDER -->` paragraphs in `.story__body` |
| Email address | `index.html` | `mailto:` href + display text in `.contact__details` |
| Contact response note | `index.html` | `<!-- PLACEHOLDER -->` in `.section-subtext` in contact |
| NALB logo | `assets/` | Replace `nalb-logo.png` |
| NALB-ERT logo | `assets/` | Replace `nalb-ert-logo.png` |
