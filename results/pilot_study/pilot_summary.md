# ASRO pilot study - summary (DINOv2-base, 32 Imagenette validation images, seed 0)

## A. Where is the concentration?
- standard, layers 9-11: top-1 energy 0.78-0.95, stable rank 1.06-1.28
- outliers per image 2.75-3.34, max/median norm 20.87-52.96
- stable rank without outliers 3.83-4.29; centred 1.05-1.24
- standard layers 1-8: stable rank 3.25-6.16
- registers: outliers per image (all layers) max 0.00; stable rank layers 9-11 4.08-4.78
- final layer 12: stable rank standard 2.59 -> centred 5.03; registers 1.81 -> centred 3.86
- randomised SVD (2 power iterations): mean error 0.01-0.01, worst 0.024, min cos v1 1.0000
- outlier location: top-left token outlier in 100%-100% of images; other outliers per image 1.75-2.34
- plainness: median pixel std outliers 0.03-0.03 vs other 0.12-0.12; near-flat 0.40-0.45 vs 0.10-0.10; same patches next layer [0.97, 0.85]

## B. Harmful or useful? (clean images)
- standard: probe accuracy 1.000
- registers: probe accuracy 0.969
- standard, delta 1, directions 1-2, layers 8-10: loss change 0.08-2.34, accuracy after 0.31-0.97
- registers, delta 1, directions 1-2, layers 8-10: loss change 0.14-6.06, accuracy after 0.09-0.94
- delta 0.1: harmful 0.02-0.04, neutral 0.92-0.94, useful 0.02-0.05
- delta 1.0: harmful 0.02-0.04, neutral 0.68-0.93, useful 0.05-0.30
- fast test delta 0.1: Spearman 0.54-0.66; sign agreement (large effects) layer 12: 1.00-1.00, other layers: 0.94-1.00
- fast test delta 1.0: Spearman 0.07-0.56; sign agreement (large effects) layer 12: 0.91-0.95, other layers: 0.50-0.67

## C. Under distribution shift (mean over layers)
- registers blur         delta 0.1: accuracy 0.97, harmful 0.033, useful 0.033
- registers blur         delta 1.0: accuracy 0.97, harmful 0.032, useful 0.194
- registers clean        delta 0.1: accuracy 0.97, harmful 0.027, useful 0.036
- registers clean        delta 1.0: accuracy 0.97, harmful 0.036, useful 0.187
- registers high-res 448 delta 0.1: accuracy 0.97, harmful 0.029, useful 0.031
- registers high-res 448 delta 1.0: accuracy 0.97, harmful 0.037, useful 0.169
- registers noise        delta 0.1: accuracy 0.97, harmful 0.032, useful 0.039
- registers noise        delta 1.0: accuracy 0.97, harmful 0.031, useful 0.188
- standard  blur         delta 0.1: accuracy 1.00, harmful 0.052, useful 0.045
- standard  blur         delta 1.0: accuracy 1.00, harmful 0.031, useful 0.204
- standard  clean        delta 0.1: accuracy 1.00, harmful 0.029, useful 0.039
- standard  clean        delta 1.0: accuracy 1.00, harmful 0.019, useful 0.192
- standard  high-res 448 delta 0.1: accuracy 1.00, harmful 0.034, useful 0.030
- standard  high-res 448 delta 1.0: accuracy 1.00, harmful 0.033, useful 0.172
- standard  noise        delta 0.1: accuracy 1.00, harmful 0.050, useful 0.054
- standard  noise        delta 1.0: accuracy 1.00, harmful 0.023, useful 0.219

(total run time 22 min)