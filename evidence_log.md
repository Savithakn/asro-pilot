# Evidence log

## 2026-11-10 (W1, Tue)
- Ran: pilot v0, DINOv2-base, 32 Imagenette val images, seed 0
- Found: abrupt collapse at layers 9–11 (stable rank ≈ 1.05), caused by ~3 high-norm patch tokens
  (21–53× median); removing them restores stable rank ≈ 4
- Control: DINOv2-with-registers has no outliers and no collapse; layer 12 still concentrated (sr 1.81)
- Made: Figure 1 (proposal version)
- Next: randomised SVD study (Cell 6); pilot v1 (does damping help or hurt?)
