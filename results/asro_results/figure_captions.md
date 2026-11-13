# Figure captions

## Figure 1a – fig1_proposal_simple.png (proposal version)
Stable rank ||X||_F^2 / sigma_1^2 of the patch-token matrix X per layer (DINOv2-base, 32 Imagenette
validation images, seed 0; 1 = all the energy in one direction). The standard model collapses
abruptly at layers 9–11 (grey); the model with registers (Darcet et al., ICLR 2024) shows no
collapse, but its final layer stays concentrated (stable rank 1.81). This points to at least two
separate causes: (1) a few high-norm outlier tokens and (2) a direction shared by all tokens.

## Figure 1b – fig1b_tiny.png (proposal version)
Outlier tokens (norm > 10x the median) at layer 10 of DINOv2-base in two of the 32 images
(church, cassette player). Blue: the top-left token, which is an outlier in every image (a
positional effect). Red: the other outliers, which lie on plain, uniform regions such as sky or
walls. The same patches stay outliers across layers 9–11. Numbers: pilot_v0_outlier_location.csv.

## Figure S1 – fig_prelim_concentration.png (detailed version of Figure 1a)
(a) Stable rank of the patch-token matrix per layer for DINOv2-base, DINOv2-base with ~3
high-norm outlier tokens per image removed, and DINOv2-base with registers: the collapse at
layers 9–11 (grey) disappears when the outliers are removed (stable rank 3.8–4.3) or registers
are used; concentration at the final layer persists. (b) Ratio of the largest to the median
token norm (log scale); dotted line = 10x threshold.

## Figure S2 – pilot_v0.png (first pilot)
DINOv2-base, mean over 32 Imagenette validation images. (a) Top-8 singular values of the token
matrix X (257 tokens x 768 features, including CLS) per layer, normalised by ||X||_F.
(b) Top-1 energy share sigma_1^2 / ||X||_F^2 (red, ± 1 s.d. across images) and stable rank (blue).
The top direction takes ~95% of the energy at layers 9–11.

## Figure S3 – rsvd_study.png (randomised SVD check)
Relative error of the top-8 singular values from randomised SVD (Halko, Martinsson & Tropp, 2011;
k = 8, oversampling p = 8) compared with the exact SVD, DINOv2-base layer 6, image 0, for 0, 1, 2
and 4 power iterations. Each extra power iteration reduces the error by roughly 10x; with 2 power
iterations all 8 values are within ~0.3%. Results for layers 6 and 9 on all 32 images:
rsvd_study_summary.csv.

## Figure S4 – sample_images.png
The first 8 of the 32 Imagenette validation images used in the pilot (random selection, seed 0),
with their class labels.

## Figure S5 – fig_outlier_map_L10.png (outlier map)
Layer 10 of DINOv2-base on the first 16 of the 32 images: patch tokens with norm > 10x the median
of that image. Blue = top-left token, red = other outliers; the number in each title is the count
of outliers in that image.

## Figure S6 – fig_outlier_similarity_L10.png (are outliers on plain patches?)
Similarity of each patch to its 4 neighbours (mean cosine similarity of pixels; 1 = plain area),
layer 10: outlier patches (top-left token excluded) compared with normal patches. Outlier patches
are more similar to their neighbours, i.e. they lie on plain, uniform regions.

## Figure S7 – fig1b_detailed.png (detailed version of Figure 1b)
Three of the 32 images with the outlier tokens at layer 10 (blue = top-left token, red = other
outliers), and a bar chart of the similarity to neighbours for the other outliers versus all
other patches (error bar = 95% bootstrap interval, token level).
