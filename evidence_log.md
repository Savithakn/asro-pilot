# Evidence log

## 2026-11-12 (W1, Thu)
- Ran: outlier-token map (asro_day_20261112.ipynb), DINOv2-base, 32 Imagenette val images, threshold 10x median
  - outliers per image: L6 0 | L8 0 | L9 3.34 | L10 3.16 | L11 2.84 | L12 0;
    max/median norm 52.8 (L9), 34.3 (L10), 20.5 (L11)
  - top-left patch (0,0) is an outlier in 100% of images at L9, L10, L11 -> positional effect
  - other outliers (~2 per image) sit on plain, uniform patches: similarity to neighbours
    0.67 vs 0.42 for other patches (L10, top-left patch excluded; token-level bootstrap)
  - no border bias once the top-left patch is excluded (border share 0.33 vs area share 0.44)
  - same patches across layers: Jaccard 0.95 (L9-10), 0.91 (L10-11), 0.88 (L9-11)
- Note: the day notebook used a slightly different set of 32 images from pilot v0;
  Cells 12-14 added to asro_pilot_v0.ipynb (same images as Figure 1a) -> rerun and use those numbers
- Made: Figure 1b (fig1b_tiny.png: church + cassette player; blue = top-left token, red = other outliers)
- Proposal: v7 (Figure 1b beside 1a, labels (a)/(b)) and v8 (linear-probe loss for ViTs, gate defined,
  sigma_i -> g_i sigma_i sentence, "to our knowledge", NeuTRENO reference added, SoftDecay cost claim
  corrected, gender text); proposal keeps 2 figures (Figure 1 + Gantt); pilot v1 will be reported in text only
- Repo: notebooks/README.md, results README.md and figure_captions.md updated
- Maths: ___ (exercises ___/5)
- Reading: Darcet et al. 2024, Sections 1-3: ___
- Open question: does the top-left outlier disappear with registers? (check in W2)
- Next: matrix calculus (gradient G = dL/dX, first-order score); pilot v1 set-up
- 
## 2026-11-11 (W1, Wed)
- Ran: Cell 6 randomised SVD study (Halko et al., 2011), DINOv2-base layer 6, image 0, k = 8, p = 8
  - max rel. error of sigma_1–8: ~30% (q = 0), ~2.6% (q = 1), ~0.25% (q = 2), ~0.01% (q = 4)
  - each extra power iteration reduces the error ~10x; sigma_1 is most accurate (large spectral gap)
- Ran: Cell 6b, layers 6 and 9, all 32 images, q = 2: mean rel. error 0.95% (L6), 0.61% (L9);
  worst 3.5% (L6), 2.0% (L9); min cos(v1) = 0.9999 (both). q = 4: worst 0.41% / 0.12%.
- Decision: ASRO uses k = 8, q = 2 power iterations
- Made: simple one-panel Figure 1 (Cell 10c) -> fig1_proposal_simple.png; old figure kept as Figure S1
- Notebook: added Cells 6b, 10c, 11; removed old Cells 7 and 10
- Repo: README, figure_captions.md and data tables updated
- Proposal: v6 drafted (private, not on GitHub): pilot sentence in 1.1, registers explained,
  new preliminary-results paragraph naming the two causes ("at least two"), simple Figure 1 + caption,
  randomised SVD sentence in 1.2, pilot line in 1.4
- Maths: randomised SVD algorithm, HMT error bound, power iteration; exercises ___/5
- Next: outlier-token map (background vs object); spectral gap; read Darcet et al. 2024, Sections 1–2

## 2026-11-10 (W1, Tue)
- Ran: pilot v0, DINOv2-base, 32 Imagenette val images, seed 0
- Found: abrupt collapse at layers 9–11 (stable rank ≈ 1.05), caused by ~3 high-norm patch tokens
  (21–53× median); removing them restores stable rank ≈ 4
- Control: DINOv2-with-registers has no outliers and no collapse; layer 12 still concentrated (sr 1.81)
- Made: Figure 1 (proposal version)
- Next: randomised SVD study (Cell 6); pilot v1 (does damping help or hurt?)
