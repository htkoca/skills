---
name: performance
description: Performance, LCP, CLS, INP, Core Web Vitals, Lighthouse, page speed, slow load, lazy-loading, above/below the fold, image optimization, SVG vs raster, bundle size, font loading, FOUT, motion budget. Use when adding images, media, animation, or custom fonts, or when reviewing a page for load or interactivity regressions.
---

# Performance

Fast is a feature; the presentation layer never gets to make the site feel slow.

1. **LCP first.** Fast LCP on desktop and mobile; the first screenful renders without layout shift.
2. **Images lazy-load below the fold.** Decorative image layers (texture backgrounds, thumbnail walls) never block LCP.
3. **Vector geometry ships as optimized SVG**: marks, lines, letterforms, not raster.
4. **The presentation layer has a budget.** Entry and loading sequences are capped in duration; motion never blocks interactivity or input.
5. **Motion discipline.** Durations, easings, and variants are defined once and imported: no ad-hoc magic numbers per component.
6. **Font loading causes no flash of invisible text and no layout shift** on swap.