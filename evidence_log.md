# Evidence log

## 2026-11-17 (Tue, W2) - pilot v1 + plainness fix (asro_pilot_v0.ipynb Cells 17-23)
- Plainness (Cell 17): outlier patches median pixel std 0.03 vs 0.12; near-flat 40-45% vs 10% -> outliers sit on plain patches
- Probe accuracy on the 32 pilot images: standard 100%, registers 97%
- delta 1: removing direction 1-2 raises loss by 1.4-2.3 (standard, L8-10) and 4-6 (registers); accuracy drops to 9-59%
- Harmful cases 1.6-4.3% (at noise level, tau = 95th percentile of random directions); delta 0.1: 92-94% neutral
- Layer 12: removing direction 1 barely changes the loss (0.002 standard, 0.11 registers)
- Conclusion: in-distribution, dominant directions are useful; harm must be tested under shift
- Files: results/asro_results/pilot_v1_labels.csv, pilot_v1_summary.csv, pilot_v1_dL.png, pilot_v0_plainness_std.csv

## 2026-11-13 (W1, Fri)
- Pilot notebook rerun in full (cells 1-17); reproduces earlier results exactly
  (stable rank 1.06-1.28 at L9-11, 2.59 at L12; rSVD q=2 mean error 0.95% (L6) / 0.61% (L9))
- Official outlier numbers (Cell 13, same 32 images as Figure 1a): top-left token is an outlier in 100%
  of images (L9-11); other outliers 1.8-2.3 per image on plainer patches (similarity 0.51-0.52 vs 0.37);
  no border bias; same patches across layers (Jaccard 0.97 / 0.87 / 0.84)
- Figure 1b remade from the official images (3: cassette player, 4: cassette recorder)
- Repo: results/asro_results/ recreated with 18 files; READMEs and figure captions updated;
  notebook cells renumbered 1-17
- Maths: matrix calculus; first-order damping score -delta sigma_i u_i^T G v_i
- Proposal: v9 (new Figure 1b, O2 bullet with cost and error bound)
- Next (Mon 16 Nov): corner check with registers + damping demo (Cells 18-19); pilot v1; Darcet reading

## 2026-11-12 (W1, Thu)
- First outlier-token map (separate notebook, different 32 images): top-left token always an outlier;
  other outliers on plain patches (superseded by the official numbers of 13 Nov)
- Proposal: v7 (Figure 1b beside 1a) and v8 (linear-probe loss, gate defined, NeuTRENO reference,
  SoftDecay claim corrected, gender text); 2 figures only (Figure 1 + Gantt)
- Decisions: one model for the pilot (DINOv2-base, standard + registers); W4 = code teaching + repo setup
- Darcet et al. 2024 reading moved to week 2

## 2026-11-11 (W1, Wed)
- Ran: randomised SVD study (Halko et al., 2011), DINOv2-base layer 6, image 0, k = 8, p = 8
  - max rel. error of sigma_1–8: ~30% (q = 0), ~2.6% (q = 1), ~0.25% (q = 2), ~0.01% (q = 4)
  - each extra power iteration reduces the error ~10x; sigma_1 is most accurate (large spectral gap)
- Ran: layers 6 and 9, all 32 images, q = 2: mean rel. error 0.95% (L6), 0.61% (L9);
  worst 3.5% (L6), 2.0% (L9); min cos(v1) = 0.9999 (both). q = 4: worst 0.41% / 0.12%
- Decision: ASRO uses k = 8, q = 2 power iterations
- Made: simple one-panel Figure 1 -> fig1_proposal_simple.png; old figure kept as Figure S1
- Proposal: v6 drafted (pilot sentence in 1.1, registers explained, two causes in preliminary results,
  simple Figure 1, randomised SVD sentence in 1.2, pilot line in 1.4)
- Maths: randomised SVD algorithm, HMT error bound, power iteration

## 2026-11-10 (W1, Tue)
- Ran: pilot v0, DINOv2-base, 32 Imagenette val images, seed 0
- Found: abrupt collapse at layers 9–11 (stable rank ≈ 1.05), caused by ~3 high-norm patch tokens
  (21–53× median); removing them restores stable rank ≈ 4
- Control: DINOv2-with-registers has no outliers and no collapse; layer 12 still concentrated (sr 1.81)
- Made: Figure 1 (proposal version)
- Next: randomised SVD study; pilot v1 (does damping help or hurt?)
