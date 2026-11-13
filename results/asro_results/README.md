# Pilot outputs (figures and CSV files)

All files are produced by `notebooks/asro_pilot_v0.ipynb` (DINOv2-base, 32 Imagenette validation
images, seed 0). Figure captions: `figure_captions.md`.

## Main findings
1. **Two causes of spectral concentration.** Layers 9-11 collapse because of a few high-norm
   outlier tokens; the final layer is concentrated along a direction shared by all tokens.
   Registers remove only the first (Figure 1a).
2. **Where the outlier tokens are.** One is always the top-left token; the others sit on plain
   regions such as sky or walls (Figure 1b).
3. **Cheap directions.** Randomised SVD with 2 power iterations matches the exact SVD closely.

## Files
| File | What it is | Cells |
|---|---|---|
| `fig1_proposal_simple.png` | Figure 1a (proposal) | 11 |
| `fig1b_tiny.png`, `fig1b_tiny.pdf` | Figure 1b (proposal) | 14 |
| `fig_prelim_concentration.png` | Figure S1 (detailed Figure 1a) | 10 |
| `pilot_v0.png` | Figure S2 (first pilot) | 5 |
| `rsvd_study.png` | Figure S3 (randomised SVD) | 6 |
| `sample_images.png` | Figure S4 (the images) | 3 |
| `fig_outlier_map_L10.png`, `fig_outlier_similarity_L10.png` | Outlier map on 16 images + similarity histogram | 15 |
| `fig1b_detailed.png`, `fig1b_detailed.pdf` | Detailed Figure 1b with bar chart | 16 |
| `pilot_v0_results.json` | Summary numbers of pilot v0 (energy share, stable rank per layer) | 5 |
| `pilot_v0_mean_singular_values.csv` | Mean top-8 singular values per layer (data of Figure S2) | 5 |
| `pilot_v0_diagnostics.csv` | Outlier vs mean-direction diagnosis per layer | 8 |
| `pilot_v0_registers_control.csv` | Same diagnosis, model with registers | 9 |
| `pilot_v0_outlier_location.csv` | Where the outlier tokens are | 13 |
| `rsvd_study_per_image.csv`, `rsvd_study_summary.csv` | Randomised SVD vs exact SVD | 7 |

**Next:** pilot v1 - does damping each direction help or hurt the loss? (from 16 Nov 2026)
