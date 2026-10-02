# Plan: Simple AI educational website (HTML)

## Context
- `public/ai-school.html` already exists (untracked, ~290 lines): "Lumen — Learn AI, Calmly".
  Warm editorial look (Instrument Serif + Inter), nav, hero, 3 courses, method, AI-tutor, quote, CTA, footer.
- Its "images" are CSS-drawn illustrations, not real placeholder images.
- The Next.js app (`app/page.tsx`) is still the default starter and isn't needed for a static HTML page.

## Approach
Build on the existing page rather than rewriting it (keep changes minimal).
Served at `http://localhost:3000/ai-school.html` via `npm run dev`, or open the file directly.

## Todo
- [x] Swap CSS-drawn illustrations for real placeholder images (picsum.photos, grayscale, fixed seeds) in hero, course cards, and tutor section — keep alt text
- [x] Tidy the design toward a "modern agency" feel: consistent spacing, a stats/numbers strip under the hero, subtle hover states on course cards
- [x] Check mobile layout (≤860px): nav, hero grid, course grid, split sections stack cleanly, no horizontal scroll
- [x] Verify the page loads in the browser with no console errors
- [x] Add review section to this file

## Out of scope
- No changes to the Next.js app / React components
- No build tooling, frameworks, or JS beyond what exists

## Review
All changes are in `public/ai-school.html`; nothing else was touched.

- **Placeholder images:** the CSS-drawn illustrations in the hero, the 3 course cards, the tutor background and the testimonial avatar are now grayscale `picsum.photos` images with fixed seeds, so the same image shows every time. The unused illustration CSS (`.sun`, `.horizon`, `.m1`–`.m3`) was removed. The hero has a soft bottom gradient so its caption stays readable.
- **Agency polish:** added a 4-up stats row under the hero (2×2 on mobile). Course-card images zoom slightly on hover.
- **Bug fix (was already there):** `.wrap { padding: 0 24px }` was overriding `section`'s vertical padding, so the Courses and Tutor sections had no top or bottom spacing. Changed it to `padding-inline`, and `.quote` to `padding-block`.
- **Verified:** screenshots in headless Chrome at 1280px and 500px; the page has no horizontal overflow (scrollWidth = viewport width).
- **Note:** the images need an internet connection (picsum.photos).
