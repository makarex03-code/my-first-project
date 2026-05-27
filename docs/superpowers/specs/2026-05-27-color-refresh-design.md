# Color Refresh Design — Iza Portfolio
**Date:** 2026-05-27  
**Status:** Approved  
**Scope:** CSS color token overhaul + emerald section background for Skills

---

## 1. Goal

Make the Iza VA portfolio feel more premium, distinctive, and boutique — shifting from a "generic dark luxury" look (pure black + brassy gold) to a refined, editorial aesthetic (obsidian blue-black + antique gold + deep emerald island).

The site should feel like a high-end agency or bespoke boutique brand — comparable to Bottega Veneta, high-end PR firms, and luxury creative agencies — rather than a standard corporate VA site.

---

## 2. Design Direction

**Chosen approach:** Distinctive & Boutique — Obsidian + Antique Gold + Deep Emerald (Section Background variant)

The core insight: using emerald as a **single full-section background** (the Skills section) creates a "color island" — a moment of rich, unexpected color in an otherwise refined monochromatic palette. This is the technique used by premium editorial sites to create memorable scroll experiences and break visual monotony without sacrificing elegance.

---

## 3. Color Token Changes

### CSS `:root` variables — before → after

| Token | Old Value | New Value | Rationale |
|---|---|---|---|
| `--black` | `#0A0A0A` | `#16202E` | Blue-black obsidian — adds depth, avoids flat pure black |
| `--charcoal` | `#111111` | `#1E2D3D` | Rich dark slate — maintains dark-section contrast |
| `--gold` | `#C9A84C` | `#C4A44A` | Slightly cooler — antique gold vs brassy gold |
| `--gold-light` | `#D8B96D` | `#D4B96A` | Matching refinement |
| `--cream` | `#F5EFE6` | `#F2EDE4` | Warmer linen tone |
| `--offwhite` | `#FAF7F2` | `#F9F5EE` | Warmer ivory base |
| `--muted` | `#A99C8D` | `#8BA89C` | Sage-grey — reads well on both dark and ivory backgrounds |

### New tokens added

| Token | Value | Purpose |
|---|---|---|
| `--emerald` | `#0F3D2E` | Full section background (Skills) |
| `--emerald-mid` | `#1A5C42` | Cards and elements on the emerald background |
| `--sage-light` | `#C8DBD4` | Muted label/accent text on the emerald section |

---

## 4. Section Color Map

Current HTML class assignments (verified), with the one change highlighted:

```
Section         Class             Background           Change?
────────────────────────────────────────────────────────────────────
Navbar          (fixed)           #16202E (Obsidian)   token update
Hero            (custom)          #16202E → #1E2D3D    token update
About           section-light     #F9F5EE (Ivory)      token update
Skills          section-dark      #1E2D3D (Slate)    → section-emerald #0F3D2E ← THE CHANGE
Services        section-light     #F9F5EE (Ivory)      token update
Experience      section-dark      #1E2D3D (Slate)      token update
Portfolio       section-dark      #1E2D3D (Slate)      token update
Testimonials    section-light     #F9F5EE (Ivory)      token update
Contact         section-dark      #1E2D3D (Slate)      token update
Footer          (custom)          #16202E (Obsidian)   token update
```

Only **Skills** changes its section class (`section-dark` → `section-emerald`). All other sections keep their existing class — they benefit automatically from the refined token values.

**Resulting scroll rhythm:** Dark → Light → **Emerald** → Light → Dark → Dark → Light → Dark → Obsidian

---

## 5. Emerald Section — Skills — Detailed Spec

All elements within `#skills` (`.section-accent` or a new `.section-emerald` class):

| Element | Value |
|---|---|
| Section background | `--emerald` `#0F3D2E` |
| `.section-label` | `--sage-light` `#C8DBD4` |
| `.section-title` | `--cream` `#F2EDE4` |
| `.skill-card` background | `rgba(255,255,255,0.06)` |
| `.skill-card` border | `rgba(255,255,255,0.10)` |
| `.skill-card:hover` bg | `rgba(255,255,255,0.11)` |
| `.skill-card:hover` border | `rgba(196,164,74,0.45)` (gold glow) |
| `.skill-card h3` | `--cream` `#F2EDE4` |
| `.skill-card p` | `rgba(242,237,228,0.78)` |
| `.skill-tags span` bg | `rgba(200,219,212,0.12)` (sage-tint) |
| `.skill-tags span` border | `rgba(200,219,212,0.22)` |
| `.skill-tags span` text | `--sage-light` `#C8DBD4` |
| `.tools-strip` border | `rgba(255,255,255,0.10)` |
| `.tools-label` | `rgba(200,219,212,0.70)` |
| `.tools-list span` bg | `rgba(255,255,255,0.08)` |
| `.tools-list span` text | `rgba(242,237,228,0.78)` |

A new CSS class `.section-emerald` is added to handle these overrides cleanly, applied to `#skills` alongside `.section`.

---

## 6. Shadow & Interaction Updates

Current shadows use pure-black rgba. With the new blue-black base, shadows pick up the obsidian tone for a more cohesive feel:

| Token | Old | New |
|---|---|---|
| `--shadow-sm` | `0 8px 28px rgba(0,0,0,0.22)` | `0 8px 28px rgba(13,20,28,0.28)` |
| `--shadow-md` | `0 16px 52px rgba(0,0,0,0.25)` | `0 16px 52px rgba(13,20,28,0.32)` |
| `--shadow-lg` | `0 24px 84px rgba(0,0,0,0.30)` | `0 24px 84px rgba(13,20,28,0.38)` |

---

## 7. What Does NOT Change

- Typography: Playfair Display + Inter — unchanged
- Layout, spacing, grid — unchanged
- Section structure and content — unchanged
- Scroll animations — unchanged
- Button shapes and border-radius — unchanged
- Mobile responsive breakpoints — unchanged

Only the **color values** change. No HTML edits required except adding `.section-emerald` to the Skills section `<section>` tag.

---

## 8. Files Changed

| File | Change |
|---|---|
| `portfolio/styles.css` | Update `:root` color tokens; add `.section-emerald` rule block |
| `portfolio/index.html` | Add `section-emerald` class to `#skills` `<section>` element |

---

## 9. Success Criteria

- Scrolling through the site produces a clear visual rhythm with emerald as the standout moment
- Gold accents read as "antique" not "brassy" — refined, not flashy
- The dark sections feel deep and dimensional (blue-black) not flat (pure black)
- The ivory/cream sections feel warm, not sterile
- All text passes WCAG AA contrast on every section background
- No visual regressions on mobile (700px) or tablet (900px) breakpoints

---

## 10. Research References

- [9 Luxury Color Palettes (Brandlic)](https://brandlic.studio/9-luxury-color-palettes-that-define-high-end-design-in-2025/)
- [Luxury Website Colors (Hook Agency)](https://hookagency.com/blog/luxury-website-colors/)
- [15 Luxury Brand Colors & Palettes (Zoviz)](https://zoviz.com/blog/luxury-brand-colors-meanings)
- [101+ Website Color Schemes 2026 (Hook Agency)](https://hookagency.com/blog/website-color-schemes/)
- [Portfolio Design Trends 2026 (Colorlib)](https://colorlib.com/wp/portfolio-design-trends/)
