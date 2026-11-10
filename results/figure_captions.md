# Figure captions

## Figure 1 – fig_prelim_concentration.png (proposal version)
Spectral concentration in DINOv2-base (32 Imagenette validation images, seed 0).
(a) Stable rank ||H||_F^2 / sigma_1^2 of the patch-token matrix per layer: an abrupt collapse
at layers 9–11 (grey) disappears when ~3 high-norm outlier tokens per image are removed, or when
registers are used (Darcet et al., ICLR 2024); concentration at the final layer persists in both
models. (b) Ratio of the largest to the median token norm (log scale); dotted line = 10x threshold.
Two distinct mechanisms motivate a per-layer, loss-aware correction.

## Figure S1 – pilot_v0.png (first pilot)
DINOv2-base, mean over 32 Imagenette validation images. (a) Top-8 singular values of the token
matrix H (257 tokens x 768 features, including CLS) per layer, normalised by ||H||_F.
(b) Top-1 energy share sigma_1^2 / ||H||_F^2 (red, ± 1 s.d. across images) and stable rank (blue).
The top direction takes ~95% of the energy at layers 9–11.

## Figure S2 – pilot_v0_registers_comparison.png (draft of Figure 1)
Earlier version of Figure 1 with the same data; superseded by fig_prelim_concentration.png.

## Figure S3 – sample_images.png
The first 8 of the 32 Imagenette validation images used in the pilot (random selection, seed 0),
with their class labels.
