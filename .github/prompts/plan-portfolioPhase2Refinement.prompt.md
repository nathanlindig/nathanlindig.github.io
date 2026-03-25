# Plan: Portfolio Website — Phase 2 Refinement

**TL;DR:** Three phases targeting layout hierarchy first, then interactions (especially the card mechanic overhaul), then text polish. All changes are in `portfolio.html`.

---

## Phase A — Layout & Visual Hierarchy

**A1. Hero**
- Raise text contrast: `text-gray-400` → `text-gray-200` on the tagline/description block so it reads against the dark background
- Add an animated scroll-down chevron anchored at the bottom of the hero (`bottom-10 center`) to signal scrollability

**A2. About — left column dead space**
- Left `md:col-span-4` only contains a tiny 10px "About" label — visually empty
- Add a large decorative element (stacked meta info, rotated label, or gold rule) to give that column intentional weight

**A3. Skills — no hierarchy**
- Every skill tag renders identically — primary and secondary skills look the same
- Give core skills (top 5–7 per category) a brighter treatment: `text-white border-white/30` vs. the current uniform `text-gray-400 border-white/10`
- Reconsider the equal-width 4-column grid — "Technical Specialties" has ~2× more items than the other columns

**A4. Experience cards — card structure**
- "Click to Expand" text (`text-gray-600`) is nearly invisible — replace with a visible `+`/`×` icon that rotates on expand
- **Remove the hover contribution overlay entirely** — move the contribution summary into the **always-visible collapsed card body** as a gold-bordered "My Contribution" block below the description paragraph (no hover, no mobile issues)
- Reveal the full bullet list on expand as before

**A5. Expand animation**
- Replace `max-height: 2000px` transition (variable-speed) with `grid-template-rows: 0fr ↔ 1fr` for a smooth, consistent expand at ~0.3s

**A6. Timeline — invisible divider line**
- `border-l-2 border-white/5` is essentially invisible — change to `border-brand-gold/30` for a gold accent line, add small gold dot markers at each entry

**A7. Contact section — copy**
- "Contact details coming soon" is too flat — update to a more professionally worded placeholder ("Currently open to new opportunities. Contact information available upon request.")

---

## Phase B — Interactions & UX

**B1. Nav active state** — `IntersectionObserver` highlights the link for whichever section is currently in view (gold dot or brighter text)

**B2. Scroll-triggered entrance animations** — elements fade/slide up 20px on first entry into viewport; staggered delay on card grids (+80ms per card); one-shot (doesn't re-trigger)

**B3. Mobile hamburger nav** — a hamburger button (hidden on `md+`) opens a fullscreen overlay with all section links and a close button

---

## Phase C — Text & Copy

**C1.** Hero tagline — keep overall structure, potentially sharpen the third line ("Fluent across the full CG pipeline") to be more TA-specific

**C2.** About — tighten Paragraph 1 (three run-on clauses); Paragraph 3 is the strongest, can promote its best phrase

**C3.** Earlier Work intro line — "The following reels represent foundational work…" is flat; rewrite as a breadth statement

**C4.** Timeline descriptions — currently echo the Experience section heavily; trim to emphasize role/scope rather than repeating activities

---

## Relevant Files
- `c:\Users\lindigit\Documents\website\portfolio.html` — only file; all changes happen here

## Implementation Order
1. Phase A1–A7 (layout) — these unblock visual assessment of everything else
2. Phase B1 (card contribution redesign) — depends on A4 structural change
3. Phase B2–B4 (nav + animations) — independent, can be done in parallel with A
4. Phase C (copy) — can be done last or interspersed throughout

## Verification
1. Open in browser and scroll all sections — confirm visual hierarchy reads clearly
2. Test experience card expand/collapse on both desktop and mobile viewport
3. Confirm hover overlays are gone; contribution block always visible
4. Verify IntersectionObserver animations trigger correctly and don't re-fire
5. Test mobile nav opens/closes and scrolls to correct section
6. Check nav active state updates as you scroll through sections
7. Resize viewport to confirm skills grid responds correctly

---

## Open Questions
1. **About section left column** — photo eventually, or keep purely typographic/decorative?
    1. Answer: No photo. Purely decorative/typographic. I want the text in this section to not be a huge focus. Currently the text is far too large and it should be more in line with the font size in other sections.
2. **Skills hierarchy** — define primary skills explicitly, or infer from context?
    2. Answer: Infer from context. I may decide later to maintain a set of primary skills but for now lets let it be intuited from the rest of the website content.
3. **Phase order** — implement all three phases in one pass, or review A before B?
    3. Answer: I want to review A before moving onto B.
