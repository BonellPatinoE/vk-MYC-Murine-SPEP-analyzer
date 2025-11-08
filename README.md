# 🧬 Vk*MYC - Murine SPEP Analyzer  
**Semi-Automated Quantification of Serum Protein Electrophoresis (SPEP) Gels**

A fully interactive Jupyter Notebook for quantitative analysis of serum protein electrophoresis (SPEP) gels — optimized for **Vk*MYC multiple myeloma models** and compatible with any densitometric lane-based analysis.  
Developed by **Bonell Patiño-Escobar** (Wiita Lab, UCSF).

---

## 🚀 Overview
This tool provides an intuitive interface to quantify SPEP gels directly from image files.  
Users can interactively select lanes, define protein bands, and input control concentrations. The notebook then fits calibration curves per band and calculates relative concentrations (g/dL) for each sample.

### ✳️ Key Features
- 🖼️ Works with `.jpg`, `.png`, `.tif` / `.tiff` images  
- ✍️ Lane selection with custom names  
- 🧩 Dual-panel band selection (full SPEP + zoomed lane view)  
- 🔁 Auto-reuse of band names across all samples  
- 📊 Manual entry of control concentrations (no CSVs required)  
- 🧠 Grouped calibration by identical control names (e.g., all “Negative” lanes share one input)  
- ⚙️ Linear regression calibration (optional intercept; through origin)  
- 🚫 Clamps negative predictions to zero  
- 💻 Notebook output summary + optional CSV export  

---

## 🧭 Quick Start
1. **Open the notebook** (`vkMYC_SPEP_analyzer.ipynb`) in Jupyter or Google Colab.  
2. **Run all cells.** When prompted, select your SPEP gel image file.  
3. **Select lanes**:
   - Negative (NEG), Positive (POS), and Sample lanes.
   - Give each lane a descriptive name (e.g., “Negative”, “Positive 1”, “Sample A”).  
4. **Name bands** (Albumin, Alpha1, Alpha2, Beta, Gamma) for the first control lane.  
5. **Select bands** for all lanes (top → bottom).  
6. **Enter control concentrations** when prompted.  
   - If multiple lanes share the same name (e.g., all “Negative”), you’ll only enter values once.  
7. **View results** in the notebook output.  
8. **Optionally save** the results to CSV when prompted.
9. Save PNG with the linear regression data

---

## ⚙️ Configuration
You can adjust key settings at the top of the script:

| Variable | Description | Default |
|-----------|--------------|----------|
| `FIT_THRU_ORIGIN` | Force regression through origin (0 intercept) | `False` |
| `CLAMP_NONNEG` | Clamp predicted concentrations ≥ 0 | `True` |
| `GROUP_CONTROLS_BY_LANE_NAME` | Group lanes with same name to reuse entered values | `True` |
| `CONTROL_NAME_NORMALIZE` | Normalize whitespace when grouping control names | `True` |

---

## 📁 Outputs
| File | Description |
|------|--------------|
| `sample_concentrations.csv` | Predicted band concentrations (g/dL) per lane |
| `calibration_diagnostics.csv` | Internal calibration details (optional) |

Example output:

Lane       Band       IOD     Conc (g/dL)
Sample_1   Albumin    50234   2.923
Sample_1   Alpha1     16343   0.512
Sample_1   Beta       40211   0.812

---

## 💡 Notes
- Works without NumPy, but uses it automatically if available (“lazy NumPy” mode).  
- Recommended for use with murine **Vk*MYC** or **hIL-6 myeloma** SPEP studies.  
- Calibration quality improves with multiple positive and negative control lanes.  
- Identical lane names (e.g., “Negative”) share input; different names (“Negative 1”, “Negative 2”) are treated separately.  

---

## 🧑‍🔬 Author & Citation
**Bonell Patiño-Escobar**, Wiita Lab, Department of Laboratory Medicine, UCSF  
For questions, contact via UCSF email or Wiita Lab GitHub.  
If you use or modify this notebook, please cite:

> Patiño-Escobar B. *Vk*MYC SPEP Analyzer — Semi-Automated Quantification of Serum Protein Electrophoresis Gels.* UCSF Wiita Lab, 2025.

---

## 🧰 Requirements
- Python ≥ 3.9  
- Jupyter Notebook or Google Colab  
- Libraries:
