# Review notes and suggested extensions

This page is a critical review of the roadmap. **Everything here is a suggestion. None of it is part of the original 14-stage pipeline.** The original is documented in the [README](../README.md) and in [`source/`](../source/).

## Strengths

- The route covers the full life of a project, from problem framing to monitoring, not only training.
- The leakage rule, the baseline and the "close the loop" check are written into the route.
- Guidance is tied to the model family, for example which models need scaling and which do not.
- Drift is split into data drift and concept drift, and it feeds back to stage 01.

## Ambiguities and possible redundancies

| Where | Observation |
|---|---|
| Stages 04 to 07 | Stages 05 and 06 come before the split in stage 07, but some of their steps learn from data (imputation, scaling, feature selection, resampling for class imbalance). The leakage rule says these should be fitted on the training set only. |
| Stage 06 | PCA is listed under both dimensionality reduction and feature selection. PCA creates new components, so it fits feature extraction better than selection. |
| Stages 01, 08, 09 | The task families (regression, classification, clustering, forecasting and so on) appear in all three. |
| Stages 09, 10, 11 | In practice these form a loop. The route map draws a line. |
| Stage 12 | Tracking runs alongside training, not after tuning. It could be shown as a cross-cutting concern. |
| Stage 04 | Class imbalance options (SMOTE, ADASYN, over or undersampling) are treatments, and belong with the training data only. |

## Missing from the roadmap

- Success criteria and stakeholders in stage 01
- Formal data validation and schema checks
- Automated testing
- Data and model versioning beyond DVC
- Rollback
- The retraining process itself, beyond "loop back to 01"

## Before treating it as production-ready

The roadmap lists tools and topics per stage, but does not specify inputs, outputs or artifacts for each stage, and it does not define thresholds for its checks. Those would need to be added per project.
