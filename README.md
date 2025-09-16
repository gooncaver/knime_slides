# KNIME Converter Slides (v2) – Replication Guide for LLMs

This repository contains a custom, lightweight HTML slide deck (13 slides + `index.html` controller) used to present the KNIME → Python conversion system. Each slide is a standalone HTML file styled inline (no build step) and loaded inside an `<iframe>` by `index.html`, which provides keyboard navigation, prefetching, fullscreen, and subtle transition effects.

The following specification is written so that another Large Language Model (LLM) can deterministically recreate the same slide system (structure, styling conventions, behaviors, and component patterns) without having to inspect the originals. Follow the steps in order; each contains required constraints and acceptance checks.

---
## 1. Global Structure
1. Root folder `v2/` contains:
	- `index.html` (controller shell – full viewport, black background, loads slides via `<iframe id="slideFrame">`).
	- `slide1.html` … `slide13.html` (sequential content). File naming MUST be contiguous with no gaps; navigation logic assumes `slide${n}.html`.
	- `imgs/` asset directory (images referenced by relative paths, e.g. `imgs/isometric/isometric1.jpg`).
2. No external bundler; all CSS per slide is embedded in a `<style>` tag in the `<head>`.
3. Shared visual language (dark card UI inside a neutral light page background) implemented independently in each slide (intentional duplication for portability).

Acceptance: Opening `index.html` in a browser renders slide 1 immediately; arrow keys cycle through slides; total = 13.

---
## 2. `index.html` Controller Specification
Implement a class `SlidePresentation` with properties:
- `currentSlide` (int, starts at 1), `totalSlides` (hard-coded 13), element refs: `slideFrame`, `currentSlideElement`, `prevBtn`, `nextBtn`, `fullscreenBtn`, `loadingScreen`, `controlsHint`.

Functional Requirements:
1. Initial Loading Overlay: `<div id="loadingScreen">` fades (class `hidden`) ~1000ms after DOM load.
2. Controls Hint: `<div id="controlsHint">` auto-hides after 5000ms (or 3000ms when re-entering fullscreen).
3. Keyboard Mapping:
	- Left / Up → previous slide
	- Right / Down / Space → next slide
	- Home → slide 1
	- End → slide 13
	- Escape → exit fullscreen (if active)
	- Ctrl+F (or Cmd+F) → toggle fullscreen
4. Navigation Chevrons: invisible by default (opacity:0); appear on hover over `.presentation-container`.
5. Slide Transition: Add class `transitioning` to `<iframe>` for 100ms before replacing `src`; remove after load (~100ms next tick) – CSS reduces opacity and scales slightly.
6. Prefetch Adjacent Slides: Use `<link rel="prefetch" href="slide{n}.html">` for next and previous valid indices each navigation.
7. Fullscreen Toggle: Button at top-left updates text to `Enter Fullscreen` / `Exit Fullscreen` on state change (listens to `fullscreenchange`).

Styling Requirements (controller):
- Background `#000000`; overlay UI (loading, hints, nav pills) use semi‑transparent black with subtle blur (`backdrop-filter: blur(10px)`).
- Typography: system uses `'Inter', system-ui, Helvetica, Arial, sans-serif`.

Acceptance: Navigating rapidly (holding Right) shows smooth transitions with no visible flash/blank states between slides; network panel shows prefetch requests.

---
## 3. Common Slide Layout Pattern
Each slide file contains:
1. Standard HTML5 scaffold (no frameworks except optional externally loaded libraries per-slide—e.g., Mermaid, Blueprint Icons) and a `<style>` block.
2. Root `.slide-container` sized 1280×720, centered in viewport using `body { display:flex; align-items:center; justify-content:center; }`.
3. Elements (consistent positions):
	- `.nav-pill` (top-left) – pill with context label (e.g., "KNIME to Python").
	- `.pagination` (bottom center) – 13 `.dot` elements; the active slide shows `class="dot active"` at its index position (purely visual; not interactive).
	- `.footer` (bottom-left) – copyright text.
4. Slide-specific content inside container (columns, grids, cards, etc.).
5. Animation classes defined locally (e.g., `.animate-on-load`, `.fade-in`, `.slide-in-left`, `.scale-in`) and triggered via a small `window.addEventListener('load', ...)` script adding `start-animation` after a short timeout (200–400ms); each motion uses `transition-delay` utility classes (`.delay-N`).
6. Color / Theme Tokens:
	- Dark surfaces: `#121212`, `#1C1C1E`, `#2A2A2C` (gradients allowed).
	- Accent Teal: `#00E6C3` for highlights, borders, icons, active dots.
	- Neutral Text: Primary `#FFFFFF`, secondary `#D0D0D0`.
	- Borders: `#3A3A3C` base; hover states lighten (e.g., `#4A4A4A`).
7. Typography Scale Guidelines:
	- Hero / Title: 60–72px, weight 900, tight line-height (≈0.85).
	- Section Subtitle / Pill: 12–16px uppercase, tracking +0.05em.
	- Body Copy: 13–16px, weight 400, line-height 1.4–1.6.
	- KPI Value: 28–48px, weight 900.

Acceptance: Resizing the browser does NOT cause internal scrollbars inside `.slide-container`; outer body may letterbox.

---
## 4. Component Patterns
1. KPI / Card Grid (`slide7` example):
	- Parent `.kpi-grid` uses CSS Grid with explicit `grid-template-columns: repeat(4, 1fr);` and cards spanning via modifier classes: `.wide` (span 2), `.extra-wide` (span 3), `.tall` (span 2 rows).
	- Card anatomy: `.kpi-card` → `.card-header` (icon + `.card-title`) + content region (values, lists, lists with `.tech-spec-list li` styled with left accent bar + bullet glyph).
2. Mermaid Diagram (architecture flow):
	- Inline `<script src="https://unpkg.com/mermaid@10/dist/mermaid.min.js"></script>`.
	- Container `.mermaid-container` with internal `<div class="mermaid">` block containing definition.
	- Fullscreen: hidden overlay `.fullscreen-modal` toggled by adding `.active`; inside `.fullscreen-content` a duplicate rendering of the same diagram (re-render triggered by resetting `innerHTML` + `removeAttribute('data-processed')`).
	- Use `mermaid.initialize({ startOnLoad: true/false, theme: 'dark', themeVariables: {...} })` with `fontFamily: 'Inter, sans-serif'` and standard teal accent.
3. Animated Closing Slide (slide13): achievements list (`.achievement-card`) with hover border accent + sequential staggered entrance.
4. Image / Split Layout (slide1): two columns (40% text / 60% visual) using flex; hero headline with `<br>` manual line breaks for controlled wrapping.

Acceptance: Reproduced components visually match original proportions when captured in 1280×720 screenshot comparison (tolerance ±4px on spacing, ±2px font size).

---
## 5. Animation System
Guidelines for any new slide:
1. Define minimal base state: `opacity:0`, slight `transform` (translateX/translateY/scale) per variant.
2. Add `.start-animation` to trigger; transitions 0.5s–1.2s ease-out.
3. Provide `.delay-N` classes incrementing by 0.1s–0.3s steps.
4. Avoid `@keyframes` unless continuous motion (e.g., orbiting rings on slide13) is required.

Acceptance: Loading a slide shows staggered reveal; reloading (F5) replays animation.

---
## 6. Accessibility & Performance Considerations
1. All images include `alt` attributes (describe functional role, not decorative style).
2. Avoid layout shift: fixed dimensions for hero visuals.
3. Limit heavy external dependencies; only load Mermaid or Blueprint assets on slides that use them.
4. Preload fonts via Google Fonts single request (already implemented with `Inter` family weights 400/500/700/900).
5. Keep per-slide CSS ≤ ~15KB uncompressed; reuse semantic color tokens rather than duplicating hex variations.

Acceptance: Lighthouse performance on a single slide > 90 (when served locally) and no console errors.

---
## 7. Deterministic Slide Generation Prompt Template (for another LLM)
When asking an LLM to create a new slide (e.g., `slide14.html`), use a structured prompt:

"Create `slide14.html` for the KNIME Converter deck using the established system: (1) HTML5 doc, (2) inline `<style>` matching theme tokens (#121212 / #1C1C1E / #00E6C3 / #FFFFFF / #D0D0D0), (3) 1280×720 `.slide-container`, (4) include `.nav-pill`, `.pagination` (14 dots, last active), `.footer`, (5) main content: [describe], (6) implement staggered animations via classes `.animate-on-load` + `.delay-N` and JS to add `.start-animation` after 300ms, (7) no external libs unless explicitly required, (8) ensure no vertical scroll inside container." 

---
## 8. Extension Guidelines
1. To add slides: increment `totalSlides` in `index.html` and append extra `.dot` in each slide’s `.pagination` with appropriate `.active` class location.
2. To add a second diagram library or charting tool, lazy-load scripts only on the specific slide to avoid global overhead.
3. For theme variations (e.g., light mode), introduce a CSS variable layer instead of editing hex codes everywhere.
4. Consider extracting repeated CSS into a shared file only if build tooling is later introduced; current design optimizes for portability / copy-paste deploys.

---
## 9. Verification Checklist
Before accepting a regenerated deck:
- [ ] All slide files present and named sequentially.
- [ ] `index.html` navigation works with keyboard + chevrons + fullscreen.
- [ ] Prefetch links injected per navigation.
- [ ] No console errors on any slide load.
- [ ] Animations fire once per load; no perpetual layout thrash.
- [ ] Visual hierarchy (title > subtitle > body) respected on every slide.
- [ ] Color palette consistent with spec.

---
## 10. Minimal Diff Policy
When modifying existing slides, maintain: class names, sizing (1280×720), pagination dot count, and animation class semantics to preserve navigation + appearance parity.

---
## 11. Attribution
© 2025 Athinia Technologies LLC. This guide documents structural patterns only—slide narrative content may be proprietary; replace sensitive text if publishing externally.

---
End of replication guide.