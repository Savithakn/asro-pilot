# Evidence log

## 2026-11-11 (W1, Wed)
- Ran: Cell 6 randomised SVD study (Halko et al., 2011), DINOv2-base layer 6, image 0, k = 8, p = 8
  - max rel. error of sigma_1–8: ~30% (q = 0), ~2.6% (q = 1), ~0.25% (q = 2), ~0.01% (q = 4)
  - each extra power iteration reduces the error ~10x; sigma_1 is most accurate (large spectral gap)
- Ran: Cell 6b, layers 6 and 9, all 32 images, q = 2:
  worst rel. error = ___ (layer 6), ___ (layer 9); min cos(v1) = ___ (layer 6), ___ (layer 9)
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
