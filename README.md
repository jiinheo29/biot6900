
# BIOT 6900 · AI-Powered Biotech Workflows

**Name:** Jiin Heo  
**Disease focus:** High-grade serous ovarian cancer (HGSOC)

## Module 1: Environment Setup & Database Queries

**Overview:**  
Set up and verified the computational environment for BIOT 6900, including Python, conda, Git, and BioPython. Practiced retrieving and interpreting biological information from public databases.

**Data sources:**
- PubMed: Biomedical literature
- UniProt: Protein sequences and functional annotations
- Protein Data Bank (PDB): Experimental protein structures
- GWAS Catalog: Genetic associations with diseases and traits

**Execution:**  
Completed Parts A–C of the assignment.

**Issues:**  
No major issues were reported during the original assignment.

## Module 2: Disease and Data Exploration

**Overview:**  
Completed the Module 2 assignment.

**Disease focus:** High-grade serous ovarian cancer.

**Data sources:** To be confirmed from the Module 2 notebook.

**Issues:** No specific execution issues documented.

## Module 3: Protein Language Models

**Overview:**  
Explored protein language models through sequence conservation, masked amino acid prediction, embeddings, and variant scoring.

**Methods:**  
Worked with a synthetic toy protein model to understand how sequence-based models represent protein families and evaluate amino acid substitutions.

**Data sources:** Synthetic sequences provided in the course materials.

**Issues:** No major issues were reported.

## Module 4: Structure Prediction & Druggability

**Disease:** High-grade serous ovarian cancer (`ov`)

**Targets:**
- KRAS (UniProt: P01116)
- PIK3CA (UniProt: P42336)

**Files:**
- `BIOT6900_Module4_Assignment.ipynb`
- `structure_assessment_ov.csv`
- `BIOT6900_Module4_Report_jh.pdf`

**Issues:** No execution failures reported.

## Module 5: CYP2C9 Variant Interpretation

**Gene:** CYP2C9  
**AlphaGenome Atlas:** Live analysis, 36 variants scored.

CYP2C9 was selected because the gene allocation list could not be located on Canvas, and Step 1 of the assignment permitted independent gene selection.

**Files:**
- `BIOT6900_Module5_Part3_Assignment.ipynb`
- `pgx_classified_CYP2C9.csv`
- `BIOT6900_Module5_Report_jh.pdf`

The `data/` directory is not committed. The API key is loaded from the environment rather than stored in the notebook.

### Limitations and Troubleshooting

**Calibration:**  
Calibration was not possible because only eight variants retained both a clinical label and a CADD score after the 0.15 frequency filter (1 P/LP and 7 B/LB). Every score band contained fewer than 10 variants. A second gene was not pooled, and all 22 VUS remained classified as VUS.

**Atlas merge correction:**  
The supplied Atlas code merged scores using `rsid`, which caused duplicate rows and incorrect `avi` and `top_feature` values for variants without rsIDs. The merge key was changed to `hgvs_g`, and the Atlas and discordance analyses were rerun.

**Atlas coverage limitations:**  
The Atlas query supports SNVs only and could not score the frameshift deletion `chr10:g.94949282del`. Two records with identical reference and alternate alleles (`chr10:g.94942290C>C` and `chr10:g.94981296A>A`) also failed. These may represent star-allele records, although their mapping was not independently confirmed.

## Module 6: PRS Portability Across Ancestry Groups

**Disease:** Alzheimer's Disease

This analysis evaluates the portability of a European-derived polygenic risk score (PRS) across ancestry groups using real 1000 Genomes genotype data and simulated disease outcomes.

The analysis includes allele harmonization, PRS calculation, ancestry-specific distribution shifts, discrimination, calibration, and incremental predictive value beyond age.

### Key Files
- `BIOT6900_Module6_Part3_Graded_Starter(1).ipynb` — Analysis notebook
- `BIOT6900_Module6_Report_jh.pdf` — Final report

### Reproducibility
1. Open the Module 6 notebook in Jupyter.
2. Set `USE_DEMO = False`.
3. Ensure the required input data files are available.
4. Run **Kernel → Restart & Run All**.
5. Confirm that Section 2 displays `source: REAL` and file checksums.

**Note:** Genotype and PRS input data are real, but Alzheimer's disease case/control labels are simulated. The reported predictive performance is illustrative and not clinically validated.

## Portfolio Deliverable 1: Multi-Omics Target Discovery

**Disease:** Ovarian Cancer

This portfolio integrates three computational analyses to prioritize potential therapeutic targets.

- **Module 2:** Multi-omics integration of RNA, protein, and mutation data.
- **Module 3:** ESM-C protein language model-based druggability assessment and target re-ranking.
- **Module 4:** AlphaFold structural confidence and binding-pocket analysis of KRAS and PIK3CA.

### Key Files
- `BIOT6900_Portfolio Deliverable 1_jh.pdf` — Final portfolio report
- `targets_ov.csv` — Multi-omics target ranking
- `targets_ov_w3.csv` — Druggability-informed target ranking
- Module 2–4 notebooks and associated figures

## Module 7: Knowledge Graphs for Biomedical Data Integration

**Disease:** Ovarian Cancer

This module uses Neo4j and NetworkX to integrate ovarian cancer multi-omics results with genes, biological pathways, clinical phenotypes, drugs, and genetic variants.

### Key Results
- Constructed a knowledge graph with 24 nodes and 29 relationships.
- Integrated seven ovarian cancer-associated genes from Module 2.
- Identified three drug-target connections: Alpelisib–PIK3CA, Gefitinib–EGFR, and Trastuzumab–ERBB2.
- Combined PageRank with multi-omics evidence scores to rank candidate biomarkers. TP53 ranked highest, followed by EGFR and ERBB2.
- Identified five communities, including cell-cycle regulation, ERBB signaling, and PI3K/AKT signaling.
- Explored a cross-disease drug repurposing path involving Fulvestrant, ESR1, breast cancer, and ovarian cancer.

### Files
- `BIOT6900_Module7_Starter.ipynb` — Completed knowledge graph analysis
- `BIOT6900_Module7_Report_jh.pdf` — Final report and biological interpretation
- `my_knowledge_graph.png` — Knowledge graph visualization
- `nodes.csv` — Exported graph nodes
- `edges.csv` — Exported graph relationships
- `biomarker_rankings.csv` — Ranked biomarker candidates

### Limitations
The graph includes a limited set of ovarian cancer genes, and some biological relationships require further verification. The drug repurposing results are intended for hypothesis generation rather than evidence of clinical efficacy.

### Tools
Python, pandas, NetworkX, Neo4j AuraDB, Cypher

## Module 9: Clinical NLP and Outcome Prediction

**Disease:** Acute Respiratory Failure

This module uses a synthetic cohort of 400 patients to extract clinical features from patient notes and predict mortality. The main goal was to identify data leakage and evaluate how it affects model performance.

### Key Results
- Configured three early signals: hypoxemia, tachypnea, and increased work of breathing.
- Identified three treatment-related leakage features: intubation, mechanical ventilation, and ICU transfer.
- Detected `renal_replacement` as an additional hidden leakage feature.
- Classified `lactate_not_clearing` as a potential early signal, depending on when it was measured.
- Compared cross-validated AUROC before and after removing leakage:
  - All features: **0.912**
  - Declared leakage removed: **0.806**
  - All leakage removed: **0.709**
- After leakage removal, age, lactate, hypoxemia, and lactate_not_clearing were the most important predictors.

### Files
- `BIOT6900_Module9_Notebook3_Graded.ipynb` — Completed clinical NLP pipeline, model evaluation, and D1–D4 answers.

### Limitations
The dataset is synthetic, and clinical documentation may be less consistent in real patient records. The timing of repeated lactate measurements also needs to be considered when evaluating leakage.

### Tools
Python, pandas, scikit-learn, clinical NLP, cross-validation, permutation importance

**Execution notes:** No unresolved execution issues.

## Module 8: Single-Cell and Spatial Transcriptomics

**Topic:** Integrating single-cell and spatial transcriptomics to investigate ERBB2 expression in breast cancer.

This project combined breast cancer scRNA-seq data from CELLxGENE Census with a 10x Genomics Visium tissue section. The analysis compared scVI and Harmony for donor integration and examined ERBB2 expression across annotated cell populations and spatial tissue regions.

**Methods:** Scanpy, scvi-tools, Harmony, Squidpy, UMAP, silhouette scores, Moran's I, and spatial neighborhood enrichment.

**Key findings:**
- Analyzed 18,388 cells from 10 donors and 3,798 spatial spots.
- Harmony achieved a lower donor silhouette score (−0.082), while scVI achieved a slightly higher cell-type silhouette score (0.031).
- ERBB2 expression was heterogeneous across cell populations and tissue regions.
- Spatial analyses identified organized tissue domains, although precise tumor-core, invasive-margin, and immune-niche assignments remained uncertain.

**Files:**
- `BIOT6900_Module8_Assignment_jh.ipynb`
- `BIOT6900_Module8_Report_jh.pdf`

## Module 10: Medical Imaging AI

**Topic:** Evaluating shortcut learning in a pathology image classifier.

This project fine-tuned a pretrained DenseNet121 on PathMNIST normal and tumour tissue images. A synthetic scanner calibration patch was introduced into tumour images to test whether the classifier would learn a non-biological shortcut. The confounded model was compared against an independently trained clean control.

**Methods:** Transfer learning, DenseNet121, Grad-CAM, occlusion sensitivity, artifact reliance testing, and prediction flip testing.

**Key findings:**
- Clean model: 95.8% validation accuracy and 93.0% test accuracy.
- Confounded model: 100% validation accuracy.
- Removing the scanner patch reduced confounded tumour recall from 99.7% to 39.3%.
- Adding the patch to normal tiles caused an 84.7% normal-to-tumour flip rate, compared with 2.7% for the clean control.
- Grad-CAM and occlusion supported artifact-specific shortcut learning.

**Files:**
- `BIOT6900_Module10_Graded_Assignment.ipynb`
- `BIOT6900_Module10_Report_jh.pdf`

## Reproducibility

The analyses were developed using Python and Jupyter notebooks in the `biot6900` environment.

Module 8 includes a computationally intensive scVI integration step that was trained using an NVIDIA Tesla P100 GPU. Saved intermediate results may be required when reproducing the notebook without retraining the model. Module 10 was designed to run on a laptop CPU.

See the individual notebooks for preprocessing, model training, evaluation, and visualization steps.
