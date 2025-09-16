### Athinia Style Guide: Monochromatic Techy Design

This style guide is derived from Athinia's Q2 2025 and Q2 2022 Business Update PDFs, emphasizing a minimalist, monochromatic, high-tech aesthetic with dark/light mode variants. The 2025 design leans toward dark themes for a sleek tech feel, while 2022 introduces light mode elements (e.g., for covers) and additional layouts like achievement grids and sector-focused pages with full-color images. Extensions focus on new formats not covered in the original (e.g., no overlap with existing title, disclaimer, or chart pages), such as highlights with inverted cards, irregular image grids, and light mode inversions. Core monochromatic palette remains (black/white/gray/teal), but full-color photos are allowed in image-heavy sections for realism.

The guide is structured for replication by an LLM or designer. Use for slides, reports, or web pages mimicking Athinia's style. Assume slide-based format, with each "page" as a full-screen card.

#### 1. **Color Palette (Hex Codes)**
Core palette is monochromatic with teal accents. Extensions from 2022 add light mode inversions (black text on white/light gray) without overlapping dark mode rules.

- **Primary Background (Dark Card/Slide Body)**: #121212 (near-black)
- **Primary Background (Light Card/Slide Body - Extension from 2022)**: #F0F0F0 (light gray, used for covers or inverted sections; invert text to black)
- **Secondary Background (Page/Outer Container)**: #F0F0F0 (light gray for dark cards) or #121212 (dark gray for light cards - new variant)
- **Text Primary (On Dark)**: #FFFFFF (white)
- **Text Primary (On Light - Extension from 2022)**: #000000 (black for high contrast on light backgrounds)
- **Text Secondary (Subtitles, Footnotes, Labels - On Dark)**: #D0D0D0 (light gray)
- **Text Secondary (On Light - Extension from 2022)**: #4A4A4A (mid-gray)
- **Accent (Highlights, Key Data Points)**: #00E6C3 (teal/cyan, sparse for metrics; e.g., growth % in 2022 highlights remains black unless positive emphasis)
- **Neutral Gray (Borders, Dividers)**: #4A4A4A (mid-gray)
- **Error/Negative**: #808080 (darker gray)
- **Links/Calls to Action**: #FFFFFF (on dark) or #000000 (on light) with underline in #D0D0D0 or #4A4A4A
- **Images (Extension from 2022)**: Allow full-color photos (e.g., real-world scenes like labs or cities) for non-monochromatic realism; desaturate subtly if needed to fit tech vibe.

Rules:
- Dark mode: 90% black/white/gray; teal for emphasis.
- Light mode (new): Invert for covers/highlights; black/gray text on light.
- No gradients except faint teal on accents.
- Full-color images only in grid/sector pages; keep surrounding elements monochromatic.

#### 2. **Typography**
No changes to core; extensions clarify usage in light mode and new bullet styles from 2022.

- **Font Family**: "Inter" (primary); fallback: system-ui, Helvetica, Arial. Weights: 400, 500, 700, 900.
- **Sizes**:
  - Main Titles: 72px (4.5rem), Bold (700), Title Case, Letter-spacing: 0.05em.
  - Section Headers: 48px (3rem), Bold (700).
  - Subheaders: 32px (2rem), Medium (500).
  - Body Text: 14px (0.875rem), Regular (400), Line-height: 1.5.
  - Footnotes/Copyright: 10px (0.625rem), Regular (400).
  - Metrics/Highlights: 24px (1.5rem), Bold (700); black on light in new variants.
  - Quotes: 24px (1.5rem), Italic, Line-height: 1.4.
- **Alignment**: Left-aligned.
- **Spacing**: Letter: 0.02em body, 0.05em titles; Line: 1.2 titles, 1.5 body.
- **Special Elements**:
  - Logo: "⊙ Athinia" (Unicode ⊙), 24px, Bold; color inverts by mode (white on dark, black on light).
  - Bullets (Existing)**: "→" or "➤" for lists (white/teal on dark).
  - Bullets (Extension from 2022)**: "•" for achievement grids (white on dark, no arrows to avoid overlap).
  - Uppercase: Abbreviations (e.g., "Y/Y", "TTM").

Rules:
- No serifs.
- In light mode (new): Use black (#000000) for bold emphasis on metrics.
- High contrast always.

#### 3. **Layout and Structure**
Core dark card structure remains; extensions add light mode variant and new page types from 2022 (e.g., highlights with stacked cards, achievement grids, sector pages). No overlap: Existing covers dark, charts have sidebars; new types are list/grid-focused without sidebars.

- **Overall Page/Slide Structure**:
  - Container: Rounded rectangle (border-radius: 16px), Padding: 48px (3rem).
  - Outer Canvas: #F0F0F0 (for dark cards) or #121212 (for light cards - new).
  - Navigation Pill (Top-Left): Rounded (border-radius: 999px), Size: 12px text; Dark mode: #4A4A4A bg with #FFFFFF text (e.g., "KNIME to Python"); Light mode (extension): #F0F0F0 bg with #000000 text.
  - Pagination Dots (Bottom-Center): Circles (12px diameter), Border: 1px #D0D0D0 (dark) or #4A4A4A (light); Fill: #FFFFFF/#000000 for active by mode. Spacing: 8px.
  - Footer: Copyright bottom-left, 10px, #D0D0D0 (dark) or #4A4A4A (light).

- **Modes (Extension from 2022)**:
  - **Dark Mode (Default, as in 2025)**: Dark card on light canvas, white text.
  - **Light Mode Variant**: Light card on dark canvas, black text; use for covers or highlights to match 2022 evolution. Invert colors for elements (e.g., dots: black fill on light).

- **Sections**:
  - **Title Slides** (Existing, Updated with Variant): Top: "Q2" left large (#D0D0D0 dark/#4A4A4A light). Middle: Logo left small, Year right large. Bottom: Title large. Horizontal 1px dividers #4A4A4A. Light variant: All black text on #F0F0F0 card.
  - **Text-Heavy Pages** (e.g., Safe Harbor): Justified body, tabs top-left (e.g., "Disclaimer | Safe Harbor") as connected rounded pills (#121212 bg white text dark; invert for light).
  - **Chart Pages** (e.g., Rule of 40): Left light sidebar title black, source gray; right dark chart white dots, teal PLTR, dashed #D0D0D0 lines. No light variant in sources.
  - **Highlights Lists (Extension from 2022, No Overlap with Existing Striped Bars)**: Large title (48px, white on dark). Stacked rounded white cards (#FFFFFF bg, border-radius: 8px) on dark background, black text, "→" arrow left (black, 24px). Metrics bold black. Spacing: 16px between cards. Footnote bottom small gray/white.
  - **Achievement Grids (Extension from 2022 "When it has to work")**: Large title (48px, white on dark). Irregular grid (2-3 columns, flexible rows) of "•" bullets (white, 16px) above full-color rounded images (border-radius: 16px, no borders, size ~200x150px). Grid uses negative space; left-align text. Dark background only; images provide color contrast.
  - **Sector Focus Pages (Extension from 2022 Healthcare)**: Left column: Large title (48px, white on dark) with metric bold (teal if positive growth), followed by "→" bullet list (white, 24px) of sectors. Right: Scattered full-color rounded images (border-radius: 16px, varying sizes ~150-300px, overlapped slightly for dynamic feel). Dark background; footnote bottom small white. 60/40 split (text/images).
  - Other existing sections unchanged.

- **Spacing and Grids**:
  - Margins: 48px outer, 24px inner.
  - Grid: CSS Grid/Flex for columns; irregular for achievements (e.g., position: absolute for scatter).
  - Borders: 1px #4A4A4A dividers; rounded 8-16px on cards/images.

#### 4. **Visual Elements and Icons**
- **Icons**: Minimal Unicode (→, • - new for grids, ⊙). No complex unless tech (▶ video).
- **Charts/Graphs**: Unchanged.
- **Images (Extension from 2022)**: Full-color allowed in grids/sectors (e.g., photos of planes, labs, cities); rounded 16px, no overlays unless faint dark scrim for text legibility.
- **Animations**: Subtle fades.

#### 5. **General Rules for Reproduction**
- **Monochromatic Techy Vibe**: Simplicity, data focus, contrast. Allow color in images only for new sections.
- **Consistency**: Every slide has rounded card, pill, footer, dots; invert for light mode.
- **Accessibility**: WCAG AA+ contrast.
- **Output Format**: Dark default; specify mode if light. For HTML/CSS, use prefers-color-scheme for variants.
- **Variations**: Light mode for 2022-style covers; grids for image-heavy content.
- **Do Not**: Overlap formats (e.g., no striped bars in new highlights); use colors outside palette except images.