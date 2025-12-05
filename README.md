# Benchmarking AlphaFold 3 for Calcium-Binding Site Prediction

Accurate metal-ion placement is essential for understanding protein structure, function, and energetics. Although AlphaFold 3 (AF3) introduced explicit small-molecule and ion modelling, the reliability of its Ca²⁺-binding site predictions has not been systematically evaluated.  
This repository provides a structured benchmark comparing AF3-predicted Ca²⁺ positions against experimentally validated crystal structures and electron density.

---

## 🔬 Abstract

We evaluate the accuracy of AlphaFold 3 in predicting Ca²⁺-binding sites across two curated datasets of experimentally determined protein structures. Using RMSD, predicted vs. experimental Ca²⁺ distance, pLDDT, pTM, and ipTM scores, along with electron-density validation, we quantify how well AF3 reproduces known Ca²⁺ coordination environments. AF3 achieves high global structural accuracy and frequently places Ca²⁺ ions within 0.5–1.0 Å of the experimental coordinates. However, discrepancies arise when PDB entries contain missing residues or misassigned ions, and AF3 can reproduce these artifacts. The study highlights both the strengths and caveats of using AF3 for functional metal-site inference.

---

## 📂 Dataset Overview

### Dataset A — Cross-validated PDB Ca²⁺ Structures
- Initial: 134 structures  
- Removed (present in AF3 training set): 26  
- **Final dataset: 105 structures**

Each structure includes:
- Experimental Ca²⁺ location  
- AF3-predicted protein model  
- RMSD, Ca²⁺ distance, pTM, ipTM metrics  

---

### Dataset B — High-quality Post-Cutoff Ca²⁺ Sites
Filtered by:
- Resolution ≤ 2.5 Å  
- R-factor ≤ 0.25  
- Single-chain X-ray structures  
- Post-AlphaFold training cutoff  

Final dataset:
- **73 protein chains**
- **132 Ca²⁺-binding sites**

Each site includes:
- Electron-density validation  
- Metal identity & assignment quality  
- Bond-valence checks  
- AF3-predicted Ca²⁺ position  

---

## ⚙️ Methods

### AlphaFold 3 Model Generation
- Input: protein sequence  
- 5 AF3 models generated per protein  
- Best-ranked model selected  
- Extracted Ca²⁺ positions + AF3 confidence scores (pLDDT, pTM, ipTM)

### Structural Comparison & Metrics
- Backbone RMSD (Å)  
- Ca²⁺ predicted vs. experimental distance  
- Global confidence (pTM, ipTM)  
- Electron-density checks  
- Ion assignment validation (bond-valence, coordination geometry)

---

## 📊 Key Results

### Global & Local Accuracy
- **84/105** Ca²⁺ sites predicted within **0.5 Å**  
- **99/105** within **1.0 Å**  
- **100%** within **2.0 Å**  
- RMSD distribution:  
  - 49 structures < 1 Å  
  - 80 structures < 2 Å  
  - 97 structures < 4 Å  

AF3 predicts global folds well, but **local ion placement accuracy does not always correlate with global confidence metrics**.

### Common Failure Modes
- Missing residues in PDB entries  
- Misassigned ions in experimental structures  
- AF3 reproducing PDB annotation errors  
- Flexible loops altering metal coordination geometry  

---

## 📈 Figures (Placeholders)

Create a `figures/` folder and add plots such as:

