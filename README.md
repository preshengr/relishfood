# Relish Food — Website

A single-page website built for **Relish Food**, a bakery, breakfast spot, and cold-pressed juice bar located in Garki II, Abuja, FCT, Nigeria.

This is a self-contained, static HTML file — no build tools, frameworks, or installation required. Open it in a browser and it works.

---

## 1. Project Overview

| | |
|---|---|
| **Business** | Relish Food |
| **Category** | Bakery · Restaurant · Breakfast Restaurant · Juice Shop |
| **Address** | Opp. Housing Estate, 1st Gate, 1 Misau Crescent, Off Birnin Kebbi Crescent, Garki II, Garki 900103, Abuja, FCT, Nigeria |
| **Phone** | +234 909 761 9343 |
| **Purpose of site** | Give the business a fast, mobile-first web presence so customers can find their location, check if they're open, call/WhatsApp to order, and browse what's on offer — all from a single page. |
| **File type** | Single HTML file (`relish-food.html`) with embedded CSS and JavaScript |

---

## 2. File Structure

```
relish-food.html      → The entire website (HTML + CSS + JS in one file)
README.md             → This document
```

There are no external assets (no image files, no separate stylesheets/scripts). All icons are inline SVG, and fonts load from Google Fonts via CDN. This makes the site extremely portable — it can be emailed, hosted anywhere, or opened directly from a USB drive.

---

## 3. How to View / Run the Site

**Option A — Open locally**
Double-click `relish-food.html`, or right-click → Open With → any web browser. No server or installation needed.

**Option B — Local server (optional, for development)**
```bash
# From the folder containing the file
python3 -m http.server 8000
# then visit http://localhost:8000/relish-food.html
```

**Option C — Deploy live** (see [Section 8](#8-deployment-options))

---

## 4. Technology Used

| Layer | Technology |
|---|---|
| Structure | HTML5 |
| Styling | Plain CSS3 (CSS custom properties / variables, Grid, Flexbox) — no CSS framework |
| Interactivity | Vanilla JavaScript (no libraries, no jQuery, no React) |
| Fonts | Google Fonts: **Unbounded** (display), **Inter** (body text), **IBM Plex Mono** (labels, hours, data) |
| Icons | Hand-coded inline SVG (no icon library/font) |
| Map | Google Maps embed (iframe, no API key required) |

No npm, no package.json, no build step. This keeps the site lightweight, fast-loading, and easy for a non-technical business owner to hand off to any future developer.

---

## 5. Key Features

### 5.1 Live "Open Now" Status Badge
Located in the top navigation bar. A small script checks the visitor's local time against Relish Food's real weekly hours and displays:
- 🟢 **"Open now · till 10PM"** during business hours
- 🔴 **"Closed now · opens 7AM"** outside business hours
- 🔴 **"Closed today · opens tomorrow"** on Tuesdays

This updates automatically every 60 seconds and requires no manual input.

### 5.2 Business Hours Table
A full weekly hours table (in the "Find Us" section) that automatically highlights the **current day** in the visitor's browser, so it always feels current without needing edits.

```
Monday      7AM – 10PM
Tuesday     Closed
Wednesday   7AM – 10PM
Thursday    7AM – 10PM
Friday      7AM – 10PM
Saturday    7AM – 10PM
Sunday      7AM – 10PM
```

### 5.3 One-Tap Contact Actions
- **Call button** — `tel:+2349097619343` opens the phone dialer directly on mobile.
- **WhatsApp button** — links to `https://wa.me/2349097619343`, opening a chat directly.
- Both appear in the navigation bar, hero section, and the closing call-to-action band.

### 5.4 Embedded Map
A Google Maps iframe pre-loaded with the business address, so customers can get directions with one tap — no API key or billing account needed.

### 5.5 Menu Highlights
Three category cards — **Fresh Bakes**, **Breakfast Plates**, **Cold-Pressed Juices** — with representative item lists. These are placeholder examples based on typical offerings for this type of business and **should be replaced with the real menu and pricing** (see [Section 7](#7-customization-guide)).

### 5.6 Fully Responsive Layout
Built mobile-first with breakpoints for tablet and desktop. All sections (navigation, hero, category strip, hours table, footer) reflow cleanly down to small phone screens.

### 5.7 Accessibility & Performance
- Visible keyboard focus states on all interactive elements (buttons, links).
- Semantic HTML (`header`, `main`, `section`, `footer`, proper heading hierarchy).
- Respects `prefers-reduced-motion` — animations are disabled for users who have that OS setting turned on.
- No render-blocking scripts; page loads fast even on slow mobile connections.

---

## 6. Design System

| Token | Value | Used for |
|---|---|---|
| `--ink` | `#2A1B12` | Primary text, dark sections |
| `--paper` | `#FBF1DC` | Page background |
| `--paper-soft` | `#FFFBF2` | Card backgrounds |
| `--papaya` | `#F2760A` | Primary accent, CTAs, "open" highlights |
| `--herb` | `#3F6B34` | Secondary accent, "open" status dot |
| `--berry` | `#B23A2E` | "Closed" status indicator |

**Fonts:**
- **Unbounded** — headlines, brand name, section titles (bold, geometric, distinctive)
- **Inter** — body copy, paragraphs
- **IBM Plex Mono** — labels, eyebrows, hours, phone numbers (gives a market-signage / receipt feel appropriate to a bakery)

All colors and fonts are defined once at the top of the `<style>` block using CSS variables, so the entire palette can be changed by editing a handful of lines.

---

## 7. Customization Guide

### 7.1 Replace placeholder content
| What | Where in the file | Notes |
|---|---|---|
| Menu items & prices | `<section id="menu">` | Currently illustrative — replace with real dishes and prices |
| Photos | Not yet included | Site currently uses illustrated SVG graphics in place of photography; real photos of the bakery, food, and interior are strongly recommended |
| Opening hours | `hours` object in the `<script>` tag **and** the `<table class="hours">` rows | Must be updated in **both** places if hours ever change |
| Phone number | Search for `+2349097619343` (appears ~5 times: `tel:` links, WhatsApp link, footer) | |
| Address | Search for the address text (appears in hero meta, "Find Us" section, footer, and the Google Maps iframe `src`) | |

### 7.2 Change colors
Edit the CSS variables at the top of the `<style>` block (see [Section 6](#6-design-system)). Changing `--papaya`, `--herb`, or `--ink` will cascade through the entire site automatically.

### 7.3 Add real photography
Recommended spots to add images:
- Hero section (currently an illustrated emblem)
- About section (currently a patterned SVG panel)
- Menu cards (currently icon badges only)

When adding images, use compressed `.webp` or `.jpg` files and include `loading="lazy"` on any image below the fold to keep load times fast.

### 7.4 Add social media links
The footer has a "Categories" column; a "Follow" column with Instagram/Facebook/WhatsApp Business links can be added the same way as the existing footer columns.

---

## 8. Deployment Options

Since this is a static file with no backend, it can be hosted for free on any of the following:

| Platform | Steps |
|---|---|
| **Netlify Drop** | Go to [app.netlify.com/drop](https://app.netlify.com/drop), drag `relish-food.html` (renamed to `index.html`) into the browser. Live in seconds. |
| **GitHub Pages** | Push the file (renamed `index.html`) to a GitHub repo → Settings → Pages → deploy from `main` branch. |
| **Vercel** | `vercel deploy` from the folder, or drag-and-drop via the Vercel dashboard. |
| **Cheap shared hosting / cPanel** | Upload `relish-food.html` (renamed `index.html`) via FTP to the `public_html` folder. |

**Recommended:** Once hosted, connect a custom domain (e.g. `relishfoodabuja.com`) and update Google Business Profile with the new website link.

---

## 9. Browser Support

Tested to work on current versions of:
- Chrome / Edge (desktop & Android)
- Safari (desktop & iOS)
- Firefox

The site uses standard CSS Grid, Flexbox, and CSS variables — all well-supported in modern browsers (2020+). No Internet Explorer support.

---

## 10. Known Limitations / Next Steps

- [ ] Replace illustrated graphics with real photos of food, storefront, and interior
- [ ] Replace placeholder menu items with actual dishes and pricing
- [ ] Add customer reviews/testimonials section
- [ ] Add social media links (Instagram/Facebook) once available
- [ ] Consider adding an online ordering form or delivery partner links (e.g. Chowdeck, Glovo) if applicable
- [ ] Register a custom domain for a more professional web address
- [ ] Set up Google Analytics or a privacy-friendly alternative to track visits

---

## 11. Credits

Designed and built as a sample/concept website to demonstrate a professional web presence for Relish Food. Map data via Google Maps. Fonts via Google Fonts.

---

## 12. License / Usage

This file was created specifically for Relish Food's use. It may be freely modified, hosted, and maintained by the business or any developer working on their behalf.