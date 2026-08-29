# Lightweight-Attention-for-Range-Doppler

Supplementary repository for the paper:

**Evaluating Lightweight Attention Mechanisms for Range–Doppler Target Classification**
Meliha Demirci, Melike Nur Yegin, Fatma Gumus

> **Status:** under review. This repository currently hosts the supplementary
> material accompanying the submitted manuscript. The full training and
> evaluation source code will be added here upon acceptance.

---

## Overview

This work evaluates a lightweight coordinate-attention CNN (175K parameters) for
classifying range–Doppler maps of cars, drones, and people on the **Real Doppler
RAD-DAR (RDRD)** benchmark. Alongside the model, the paper contributes a
**leakage-controlled, recording-disjoint evaluation protocol** and shows that
near-ceiling accuracies previously reported on this benchmark are optimistic once
exact-duplicate maps are removed and recordings are kept disjoint across splits.

This repository provides the material needed to inspect and reproduce the reported
numbers at full precision.

## Contents

| File | Description |
| --- | --- |
| `Supplementary.pdf` | Full-precision versions of all tables in the paper (per-seed accuracy and F1, per-class scores, significance statistics, and the eight-condition DopplerNet evaluation), plus the reproducibility statement. |
| `split_assignment_supplementary.csv` | Per-sample assignment of every range–Doppler map to the train / validation / test partition, including its class, source file, and recording identifier. This documents the fixed 70/15/15 "study split" and lets anyone verify that the partitions share no identical samples and that recording-disjoint splits are correctly formed. |
| `confusion_matrices.json` | Test-set confusion matrices (representative seed) for all evaluated models: the four attention variants, ResNet-50, ViT-Tiny, DopplerNet, and the proposed coordinate-attention CNN. |
| `LICENSE` | MIT license. |

## Dataset

The Real Doppler RAD-DAR dataset is **not redistributed here**. It is publicly
available and was introduced by Roldan et al. (2020):

- Kaggle: https://www.kaggle.com/datasets/iroldan/real-doppler-raddar-database
- Paper: I. Roldan et al., "DopplerNet: a convolutional neural network for
  recognising targets in real scenarios using a persistent range–Doppler radar,"
  *IET Radar, Sonar & Navigation*, 14(4):593–600, 2020.

Note on duplicates: exact-duplicate matrices were present in our working copy of
the dataset and were removed by content hashing, yielding 17,485 unique maps. The
`split_assignment_supplementary.csv` file is defined over these de-duplicated maps.

## Reproducibility notes

- The train/validation/test split is fixed (70/15/15, stratified by class, fixed
  random seed). Only the model initialization varies across the three seeds; the
  split itself does not change.
- Reported means and standard deviations are computed over three seeds.
- "Study split" refers to the single fixed split used for the main model comparison
  (Tables 2–4 in the paper). The eight-condition DopplerNet analysis additionally
  uses stratified random and recording-disjoint partitions, as detailed in the
  supplementary PDF.

## Citation

A citation will be added here once the paper is published. **Citation pending —
the paper is currently under review; please check back for the final reference and
DOI.** In the meantime, if you use this material, please cite it as:

```
Demirci, M., Yegin, M. N., & Gumus, F. Evaluating Lightweight Attention
Mechanisms for Range–Doppler Target Classification. Manuscript under review.
```

(A BibTeX entry with full publication details and DOI will replace this once
available.)

## License

The contents of this repository are released under the MIT License (see `LICENSE`).
The Real Doppler RAD-DAR dataset is subject to its own license and terms on Kaggle.
