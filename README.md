# hughesjoe.com — portfolio

Single-file static site, no build step. Concept: "Phase Space" — a live de Jong
strange attractor traced behind oversized editorial type. Physics foundation, made literal.

Active palette: E — Black & Yellow. Near-black base, cream type, acid-yellow accent.
The attractor renders as yellow sparks on black. All text passes WCAG AA contrast (see below).

---

## Deploy to Cloudflare Pages
Drag-and-drop (fastest): Cloudflare dashboard -> Workers & Pages -> Create -> Pages ->
Upload assets -> drop this folder -> Deploy. Then add hughesjoe.com under Custom Domains.

Git: push this folder to a repo, then Pages -> Connect to Git. Build command: blank.
Output directory: /

## Before going live (all in index.html)
- Update the GitHub + LinkedIn URLs (currently placeholders).
- Confirm the mailto: address.
- Drop a resume.pdf in this folder — the Resume button links to /resume.pdf.

---

## Active palette — E (Black & Yellow)
Defined in the :root block at the top of index.html:

    --paper:    #121311   near-black base
    --paper-2:  #1B1D19   raised surface: nav, cards
    --ink:      #F1F2E9   cream — headlines + body        16.5:1  AAA
    --ink-soft: #C9CBBE   lede, descriptions              11.3:1  AAA
    --muted:    #8C8F80   mono labels                      5.6:1  AA
    --muted-2:  #828578   faint index nums, plus-signs     4.5:1  AA
    --accent:   #CADB2A   acid yellow                     12.1:1  AAA

Contrast ratios are vs. the #121311 base. --muted-2 was lifted from #5E6155 to
#828578 specifically so it clears AA on the dark base (the lighter palettes didn't
need this). If you darken any text token, re-check it stays above 4.5:1.

The dark base also gets a few extra rules appended after the main stylesheet:
dimmed grain, a stronger plot-grid, a translucent-dark scrolled nav, and a yellow
solid contact button with black text.

---

## Swapping palettes
Every alternate is just a different :root block — paste over the active one. The hero
canvas also has one hardcoded color line (search ctx.fillStyle=isAccent); update the
two rgb() values to match the new ink + accent if you switch.

The five alternates explored (light-base versions don't need the dark extra-rules block):

    A — Oxblood & Bone   paper #F4EFE6  ink #1C1714  accent #8E2A2B (deep red)
    B — Ironwood         paper #EEEEE8  ink #1A1C1B  accent #1F6F6B (teal) + #C28A2C (ochre)
    C — Aubergine Dusk   paper #EFEAEC  ink #241A22  accent #7A2E8F (plum)
    D — Acid Lime/Light  paper #F4F2EA  ink #16160F  accent #7A8A00 text / #B6C400 neon
    F — Orange & Silver  paper #ECEDEE  ink #17191B  accent #E8551E (orange) + silver dots

Note on D: on a light base, pure neon fails contrast as small text, so labels use the
deeper olive-lime and the bright neon is reserved for the big hero word + status dots.

---

## Design notes
- Type: Fraunces (display, italic accents) / Space Grotesk (body) / JetBrains Mono (data).
- Hero canvas is a de Jong attractor; particles spring to the orbit and repel from the
  cursor. Honors prefers-reduced-motion (static, fewer points).
- Work index is an expandable scientific-catalog table, not a card grid.
- Two highest-leverage knobs for tinkering, both near the bottom of the <script>:
  the attractor constants (a, b, c, d — change the orbit shape) and the 0.86 damping
  value (cursor-repel springiness). Accent color is the single --accent variable up top.
