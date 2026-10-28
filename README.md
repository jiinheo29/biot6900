
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
