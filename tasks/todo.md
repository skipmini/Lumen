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

---

# Plan 2: Restyle after reference screenshot (SaaS-style, gray/white/orange)
Same file (`public/ai-school.html`), no JS, keep copy, images and section IDs. Full plan: approved in chat.

## Todo
- [x] Swap design tokens and fonts: Inter + JetBrains Mono, gray/white/orange palette; remove Instrument Serif and the film-grain overlay
- [x] Rebuild the nav and centred hero (announcement pill, image with floating tiles, pill buttons)
- [x] Logos + stats card (CSS marquee of made-up wordmarks)
- [x] "Learning paths" node diagram (inline SVG curves plus pills)
- [x] Courses: restyled cards plus a "Your progress" mockup card
- [x] Method: gray band, dark code card, 3 steps
- [x] AI Tutor: chat UI card
- [x] Testimonial with SVG line chart and stats
- [x] CTA badge card, dark footer with giant wordmark
- [x] Responsive pass (single breakpoint at 860px; everything stacks to one column, no sideways scroll)
- [x] Verify (screenshots, overflow probe, console check), then add a review section

## Review (Plan 2)
Only `public/ai-school.html` changed. It's still one static file with no JavaScript, and the section IDs (`#courses`, `#method`, `#tutor`, `#start`) are kept.

- **Look:** Instrument Serif and the cream/grayscale editorial style are replaced by Inter (600, tight tracking) and JetBrains Mono labels. The palette is warm-gray page, white hairline cards and a single orange accent (`--accent: #f25a1d`). The film-grain overlay is removed and photos are now in colour.
- **Sections:** centred hero with an announcement pill and floating image tiles · logos + stats card (made-up wordmarks) · "Learning paths" SVG node diagram · course cards + "Your progress" dashboard mockup · Method on a gray band with a dark code card · AI Tutor chat card · testimonial with an SVG growth chart and two stats · CTA with badges · dark footer with a giant faded wordmark.
- **Left out on purpose:** the reference's 3D cable illustration and the mascot row.
- **Bonus:** added `prefers-reduced-motion` support, which turns off the marquee, the floating tiles and the hover animations.
- **Verified:** screenshots in headless Chrome at 1280px and 500px. There's no horizontal overflow (scrollWidth = viewport width at both). The console was checked with `--enable-logging=stderr` and showed no errors.
- **Known nits:** on mobile the 5th CTA badge sits alone on its row. Nav links are still hidden on mobile with no menu. Not committed or pushed.
