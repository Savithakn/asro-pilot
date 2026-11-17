# ASRO pathology check - summary (Camelyon17-WILDS; seen hospitals [0, 3, 4], new hospital 2; 64 + 64 test patches; seed 0)

## Accuracy of the simple classifier
- standard  seen: accuracy 0.812, mean loss 1.358
- standard  new : accuracy 0.828, mean loss 0.839
- registers seen: accuracy 0.844, mean loss 1.280
- registers new : accuracy 0.922, mean loss 0.528

## Concentration (stable rank, mean over patches)
- standard  seen: layers 9-11 1.05-1.20, final layer 1.47, outliers/patch (max) 3.27
- standard  new : layers 9-11 1.06-1.22, final layer 1.49, outliers/patch (max) 3.28
- registers seen: layers 9-11 2.04-2.62, final layer 1.21, outliers/patch (max) 0.00
- registers new : layers 9-11 2.03-2.63, final layer 1.22, outliers/patch (max) 0.00

## Directions that hurt the task (share of patch x direction cases; chance level about 0.05)
- registers delta 0.1: harmful seen 0.075 vs new 0.051; patches with a harmful direction seen 0.21 vs new 0.16
- registers delta 1.0: harmful seen 0.076 vs new 0.044; patches with a harmful direction seen 0.18 vs new 0.09
- standard  delta 0.1: harmful seen 0.073 vs new 0.070; patches with a harmful direction seen 0.18 vs new 0.18
- standard  delta 1.0: harmful seen 0.077 vs new 0.065; patches with a harmful direction seen 0.18 vs new 0.15

## Per layer (delta 0.1): harmful seen / new
- registers layer  8: 0.086 / 0.057
- registers layer  9: 0.084 / 0.059
- registers layer 10: 0.076 / 0.051
- registers layer 12: 0.053 / 0.037
- standard  layer  8: 0.096 / 0.098
- standard  layer  9: 0.078 / 0.080
- standard  layer 10: 0.072 / 0.061
- standard  layer 12: 0.045 / 0.041

(total run time 17 min)