# Changelog — johnhekmati.com

Personal / founder site. Newest first.

**Release rule:** ship that changes public copy, bio, links, or deploy → entry here with date.

---

## 2026-08-06 — Modern Method Marketing joins the identity graph

- Footer "Elsewhere" gains `modernmethodmarketing.com` with `rel="me"`; JSON-LD
  `sameAs` array updated to match — per hub doctrine, every property carries the graph.
- Micro-polish: footer link transitions, hero role-line letterspacing, visible
  `:focus-visible` outlines for keyboard users.

## 2026-08-05 — Hero rebuild, shared spine, two new backlinks

- **Alignment fix (root cause):** `.hero-content` carried `.wrap` but overrode it with
  `width:100%; margin:0`, so hero copy hugged the viewport edges while nav and sections sat in a
  centred 72rem column — the two "John Hekmati" lockups were ~300px out of true on desktop.
  Every band now uses `.wrap` and nothing overrides it.
- **Hierarchy:** `h1` is now the dominant type. The repeated giant name demoted to a mono eyebrow;
  the five-word serif roles stack became one letterspaced credential line above the CTAs.
  Three competing serif masses → one.
- **Hero layout:** diagonal split replaced by copy-left / framed-portrait-right. Portrait renders in
  a 30rem panel instead of a full-bleed 100vh cover, so the 1024px source is no longer ~2× upscaled.
  Mobile leads with the portrait.
- **CTAs:** hero 3 → 2, contact 3 → 2. The unfittable `1fr 1fr 1fr` grid inside a 17rem column is gone
  (this is what the 07-28 equal-height entry was treating).
- **Editorial split (`.section--split`):** Life and Builds were leaving the whole right half of the
  72rem spine empty — the page fell from a balanced two-column hero into a narrow left rail.
  Both now run heading-in-a-sticky-left-rail / content-right at desktop, collapsing to stacked on
  mobile. Contact stays centred as the deliberate closing beat.
- **Backlinks:** Star Schema Publishing added to Builds; Hekmati Family linked from the Home block
  and the footer. Both also in a new `Person` JSON-LD `sameAs` block, with `rel="me"` on the property links.
- **Icons / weight:** favicon is now `assets/favicon.svg` (JH monogram) plus a 180px `apple-touch-icon.png`
  for Safari, which ignores SVG icons — the 277 KB portrait JPEG is no longer served as the favicon.
  Portrait gains a 640px `srcset` variant (47 KB) so phones stop pulling the full 1024px file.
- CSS cache-bust `jh11`

## 2026-07-28 — Hero action chips equal height

- Hero CTAs (My Life · What I build · Contact): equal min-height, one row on desktop, stretch align
- CSS cache-bust `jh10`

## 2026-07-28 — Release hygiene baseline

- Established this changelog as required ship surface (parity with other live LOBs)
- No product feature dump in this entry — hygiene only

<!-- Add dated sections above this line for each real ship -->
