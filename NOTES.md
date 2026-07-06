# Project notes — carport build set

Working notes for the 13'×28' lean-to carport on the 25'×28' Power Steel garage
(PSB job 010659, Haliburton ON). Sheet: SK-1 rev H, 2026-07-05.

## Where everything lives

- **Live site:** https://ndroo.github.io/carport/ (3D: `#walkthrough`)
- **Source of truth:** `index.html` in this repo — one self-contained file, no dependencies.
  All 2D drawings are drawn by inline JS (the `Dwg` class) from real dimensions; the 3D
  walkthrough is a small WebGL renderer; a collision pass (`untangle`) separates
  overlapping labels and re-fits each drawing's frame after render.
- **`local/carport-sheet-full.html`** — same file WITH the street address in the header
  (kept out of git; `index.html` is the redacted public copy). Use this one for permit PDFs.
- **PDF export** (12×18 sheet, matches the web layout):
  `"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless=new \
    --no-pdf-header-footer --virtual-time-budget=9000 \
    --print-to-pdf=out.pdf "file://$PWD/local/carport-sheet-full.html"`
  ⚠ use `--headless=new` and do NOT pass `--disable-gpu`, or the WebGL canvas exports blank.
- **To update the site:** edit `index.html`, commit, push — the Actions workflow
  (`.github/workflows/pages.yml`) deploys automatically. If the deploy fails with
  "Deployment failed, try again later", it's a GitHub transient: re-run the workflow
  or push again.

## Design decisions & why (the short history)

1. **Ledger bolts only at the 3 steel columns** (0'/14'/28') — the panel skin, single
   girt (7'-6") and eave strut can't carry roof load. So the ledger is (2) 1¾×11⅞ LVL
   acting as a beam spanning 14' column-to-column.
2. **Existing gutter stays** — ledger top dropped to 11'-0" to pass under it, leaving
   ~6" of panel for the apron flashing. Clearance under beam ≈ 7'-3".
3. **Panel ribs are VERTICAL @ 12"** — bolts go through the flat pans (which sit tight
   on the column flanges), with a vertical rib-depth packer strip (¾"+½" ext. ply,
   butyl-faced — Detail 6) filling the gap behind the LVL. Never bolt through rib crowns;
   never bare PT against galvalume.
4. **Snow governs everything** — 61 psf ground / 56.85 psf roof per the PSB cover sheet,
   plus drift and slide off the garage's 2:12 metal roof. Hence 2×10 rafters @ 16",
   (2)-ply 2×12 beam, 4 posts @ 9'-4".
5. **Beam sits in notched 6×6s, notch on the GARAGE side** (flipped from the original
   outer-side notch) so the inner faces are flush → knee braces mount flat on the inside,
   out of the weather and clear of the downspout at the rear post.
6. **Knee braces** (2×6, 45° both ends, long edge 3'-4½", Detail 7): end posts get one
   brace flush to the post's outer edge and the beam top; interior posts get a pair
   butting at the post centreline (no overlap). They stop racking along the beam line;
   crosswise the rafters brace back into the building.
7. **Ply joints in the beam land ON posts, staggered** between plies. Never mid-span.
8. **Water at the wall joint** — shed-and-catch, not hermetic: membrane over the LVL top
   (protects structure), pre-taped foam closures + butyl sandwich under the apron's top
   edge (butyl seals, foam shapes; once closures are in, the top tape run is FLAT at the
   crown plane), apron laps 4"+ onto the roof. **Drip-cap Z is optional** (+$54) — the
   exposed strip is 4-6" under the gutter's shadow; retrofit any time.
9. **Downspout jogs** via two elbows from the gutter (12" outboard) back to the rear
   post's outer face — which is free because the braces moved inside.
10. **One-person build** — steps 8/9: laser + story pole to capture each pier height,
    cut/notch on the horses, stand each post once. Cleat shelf for the LVL lift, saddle
    cleats to walk beam plies up. Panels on a calm day only.
11. **Permit framing** — designed to OBC Div. B Part 9 (O. Reg. 332/12), sections cited
    per step; no engineer references in the set (removed intentionally for submission).

## Numbers to remember

- Budget ≈ $5,025 + tax (big-box, 07/2026); carry $5,500–6,100. Optional drip cap +$54.
- Footings: 4 × 16"Ø × 4'-0" min (Dysart frost), anchors @ 9'-4" o.c., 12'-0" off the wall.
- Rafter template: ±13'-2" along the slope, plumb cuts @ 2:12; panels trimmed to 13'-4".
- Post seats ≈ 7'-3" (measure off the REAL ledger); notch 3" × 11¼", garage side.
