# PXR OpenADMET Challenge

This repository describes my submission to the OpenADMET PXR Blind Challenge





## Methodology Report

(Activity track)

# Introduction

This submission intentionally adopts a minimalist modeling strategy to reflect the realities of drug discovery, where predictive models often need to be developed under tight deadlines. To mimic this, the entire modeling effort using the unblinded training dataset was initiated only a few days before the challenge submission deadline. Given this compressed timeline, our objective was not to exhaustively optimize model performance but to establish a baseline that leverages a semi-autonomous agent (in this case, Claude) for brainstorming modeling strategies, generating code, and implementing iterative improvements. The initial prompt referenced both the challenge website and scripts from our previous challenge submissions, allowing Claude to build upon an existing codebase rather than starting from scratch.

# Leaderboard Results

Out of **350 participants**:

| Phase | Compound set | Rank | Performance Tier | MAE | R2 | Spearman | Kendall |
|:-----:|:-------------|:----:|:----------------:|-----:|-----:|--------:|--------:|
| 1 | Analog Set 1 & 2 | 3/350 | ![Tier 1](https://img.shields.io/badge/Tier%201-2ea44f) | 0.4057 | 0.6427 | 0.8293 | 0.6449 |
| 1 | Analog Set 2 only | -- | -- | 0.4189 | 0.5818 | 0.8103 | 0.6220 |
| 2 | Analog Set 2 only | 17/350 | ![Tier 1](https://img.shields.io/badge/Tier%201-2ea44f) | 0.4275 | 0.5608 | 0.8035 | 0.6188 |

> **Tier 1** indicates statistically equivalent performance to the #1 submission.

Reference:

Deep Learning vs Classical Methods in Potency and ADME Prediction: Insights from a Computational Blind Challenge.  
*J. Chem. Inf. Model. 2025, 65 (24), 13115–13131.*

- [JCIM Article](https://doi.org/10.1021/acs.jcim.5c01982) 
- [ChemRxiv Preprint](https://doi.org/10.26434/chemrxiv-2025-64fcb-v3)
  
**Algorithms**: weighted average ensemble of multiple models without hyperparameter tuning
- Message passing neural network (MPNN) as implemented in ChemProp 2.2
- Transformer pretrained on tabular data as implemented in TabPFNv2
- Classical tree based models: Random Forest, LightGBM, XGBoost
- AutoGluon ensembles (extreme preset)
  
**Additional Molecular Features**
- Structural fingerprints: ECFP4, FCFP4, Avalon
- Physchem descriptors: RDKit-2d, Mordred, ADMET-AI predictions
- Learned embeddings: CheMeleon, MiniMol, CLAMP
- Meta features: Predictions of Chemeleon trained on related PXR data (single-dose, counterscreen, and CHEMBL) 

**Additional Data**
- Only publicly available data were leveraged.

**Performance comments**  
- Feature augmentation via meta-models trained on single-dose data plus ADME predictions boosted performance
- Large errors in low activity regions
- Autogluon led to some of my best-performing individual models
- Ensembling multiple models improved performance

(Structure track)
- Boltz2 and ESMFold2 used out-of-the-box, best IPTM is selected  




