# asro-pilot

Pilot study for my MSCA Postdoctoral Fellowship 2027 proposal (working title: ASRO – knowing when to correct spectral concentration in transformers).

**Question:** inside a vision transformer, the token representations of a layer often concentrate in a few dominant directions. Where does this happen, does it help or hurt the task, and can a cheap test tell which?

## Pilot study
- **Notebook:** [notebooks/asro_pilot_study.ipynb](notebooks/asro_pilot_study.ipynb) – open in Google Colab, choose a T4 GPU, then Runtime -> Run all (about 25 minutes). All settings are in Cell 1.
- **Results:** [results/pilot_study/](results/pilot_study/) – all numbers in [pilot_summary.md](results/pilot_study/pilot_summary.md)
- **Models:** DINOv2-base and DINOv2-base with registers (Hugging Face), frozen. **Data:** 32 Imagenette validation images (seed 0); 500 training images for a simple linear classifier.

![Figure 1a: stable rank per layer](results/pilot_study/fig1a_stable_rank.png)

## Findings
1. **Two causes of concentration.** At layers 9-11 a few high-norm outlier tokens collapse the token matrix to almost one direction; at the final layer a direction shared by all tokens dominates. Registers remove only the first.
2. **Dominant directions are mostly useful.** Removing the dominant direction at layers 8-10 lowers accuracy from 100% to about 50%.
3. **Harm is rare in a well-trained model.** Directions that hurt the task occur at the same rate as for random directions (2-4%), also on blurred, noisy or larger images. Genuinely new data (for example a new hospital) is needed to test where harm appears.
4. **A cheap test works for small corrections.** A first-order score from one gradient computation predicts help or harm correctly in 94-100% of clear cases.

## Pathology check (tissue images)
- **Notebook:** [notebooks/asro_pathology_check.ipynb](notebooks/asro_pathology_check.ipynb) – Run all (downloads Camelyon17-WILDS, about 10.7 GB, then about 15 minutes)
- **Results:** [results/pathology_check/](results/pathology_check/) – all numbers in [pathology_summary.md](results/pathology_check/pathology_summary.md)

**Findings (64 + 64 tissue patches):**
1. The same collapse appears in tissue images: at layers 9-11 the token matrix lies almost in one direction, with about 3 outlier tokens per patch; registers remove the outliers but the final layer stays concentrated.
2. Directions that hurt the task occur in 5-10% of cases, about twice the rate on natural images: a first sign that harm appears when a model is used outside its training domain.
3. Patches from an unseen hospital did not show more harm, but the classifier also did not lose accuracy there; hospital effects need larger tests.

## Files
| Folder | Contents |
|---|---|
| `notebooks/` | `asro_pilot_study.ipynb` – the complete pilot study (15 cells, run all) |
| `results/pilot_study/` | Figures (`fig1a_stable_rank`, `fig1b_outliers`), CSV tables (A = concentration, B = harmful/useful, C = shifted images), `pilot_summary.md` |

| `notebooks/` | `asro_pilot_study.ipynb` – complete pilot study; `asro_pathology_check.ipynb` – pathology check |
| `results/` | `pilot_study/` and `pathology_check/` – figures, CSV tables and summaries |

## Licence
MIT – see [LICENSE](LICENSE).
