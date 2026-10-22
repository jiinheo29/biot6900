# BIOT 6900 · AI-Powered Biotech Workflows

Name: Jiin Heo  
Disease: Ovarian cancer (high-grade serous)

## Module 3 Assignment
Module 3 assignment completed successfully.
No major issues were encountered.

## Module 4 Assignment (Structure Prediction & Druggability)
- **Disease:** Ovarian cancer (high-grade serous), `ov`
- **Targets:** KRAS (P01116), PIK3CA (P42336)
- **Files:** `BIOT6900_Module4_Assignment.ipynb`, `structure_assessment_ov.csv`, `BIOT6900_Module4_Report_jh.pdf`
- **What didn't work:** Nothing failed.

## Module 5: CYP2C9

**Name:** Heo Ji In
**Gene:** CYP2C9
**AlphaGenome Atlas:** run live (36 variants scored)

I could not find the gene allocation list on Canvas, so I chose CYP2C9, as Step 1 of the brief allows.

Files: `BIOT6900_Module5_Part3_Assignment.ipynb`, `pgx_classified_CYP2C9.csv`, `BIOT6900_Module5_Report_jh.pdf`. `data/` is not committed. No API key is in the notebook; it is read from the environment.

What did not work, and what I changed:
- **Calibration was not possible.** After the 0.15 frequency filter only 8 variants carried both a label and a CADD score (1 P/LP, 7 B/LB), and every band had fewer than 10. I did not pool a second gene. All 22 VUS stay VUS.
- **Atlas merge fix.** The supplied Atlas cell merged scores back on `rsid`. Many variants have no rsid, so the merge duplicated rows and produced wrong `avi` and `top_feature` values. I changed the key to `hgvs_g` (two lines) and re-ran the Atlas and discordance cells.
- **Atlas coverage.** The Atlas query accepts SNVs only, so it could not score the frameshift deletion (chr10:g.94949282del). Two records with identical reference and alternate alleles (chr10:g.94942290C>C and chr10:g.94981296A>A) also failed. These appear to be star-allele records rather than SNVs; I did not independently confirm their mapping.
