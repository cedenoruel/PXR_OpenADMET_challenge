# PXR_OpenADMET_challenge

This repository describes my submission to the OpenADMET PXR Blind Challenge

## Methodology Report

(Activity track)

The approach is similar to that described in our recent publication:

Deep Learning vs Classical Methods in Potency and ADME Prediction: Insights from a Computational Blind Challenge.  
*J. Chem. Inf. Model. 2025, 65 (24), 13115–13131.*

- [JCIM Article](https://doi.org/10.1021/acs.jcim.5c01982) 
- [ChemRxiv Preprint](https://doi.org/10.26434/chemrxiv-2025-64fcb-v3)
  
**Algorithms**: weighted average ensemble of multiple models without hyperparameter tuning
- Message passing neural network (MPNN) as implemented in ChemProp 2.2
- Transformer pretrained on tabular data as implemented in TabPFNv2
- Classical tree based models: Random Forest, LightGBM, XGBoost 
  
**Additional Molecular Features**
- Structural fingerprints: ECFP4, FCFP4, Avalon
- Physchem descriptors: RDKit-2d, Mordred, ADMET-AI predictions
- Learned embeddings: CheMeleon, MiniMol, CLAMP
- Meta features: Predictions of Chemeleon trained on related PXR data (single-dose, counterscreen, and CHEMBL) 

**Additional Data**
- Only publicly available data were leveraged.

**Performance comments**  
- Autogluon models led to some of best-performing individual models
- Feature augmentation via meta-models trained on single-dose data plus ADME predictions helped
- Large errors in low activity regions

(Structure track)
- Boltz2 and ESMFold2 used out-of-the-box, best IPTM is selected  




