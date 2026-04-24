# AXARA BioScience — Data Products

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.19728050.svg)](https://doi.org/10.5281/zenodo.19728050)
[![bioRxiv](https://img.shields.io/badge/bioRxiv-2026.720342-blue)](https://biorxiv.org)
![Validation](https://img.shields.io/badge/Validation-9%2F9%20PASS-brightgreen)
![Families](https://img.shields.io/badge/Protein%20Families-5-teal)

**Validated SDA photoaffinity probe design datasets for high-value drug targets.**

Engine validated 9/9 against approved covalent drug co-crystal structures spanning five protein families. Primary site rankings 100% stable across 81 parameter combinations.

---

## Available Datasets

### GLP-1 GPCR Covalent Tractability Atlas v1.0
**Targets:** GLP-1R · GIPR · GCGR · GLP-2R

| Receptor | Primary Site | Score | Structure | Drug |
|----------|-------------|-------|-----------|------|
| GLP-1R | LYS202 | 12.9 | PDB 6X1A | Semaglutide |
| GIPR | TYR200 | 13.0 | PDB 7DTY | Tirzepatide |
| GCGR | LYS381 | 11.0 | PDB 8JIT | Cotadutide |
| GLP-2R | Topology only | — | OpenFold3 | Teduglutide |

Full atlas (4 receptors + cross-receptor analysis): **$12,000**
Single receptor: **$3,500**
Contact: axara@axara.bio

---

### KRAS Mutant Panel v3
**Targets:** G12C · G12D · G12V · G12R

**Free G12C report available in this repository — no registration required.**

| Mutant | Primary Site | Validation Status |
|--------|-------------|------------------|
| G12C | CYS12 | ✓ Confirmed — sotorasib + adagrasib |
| G12D | LYS | Novel prediction |
| G12V | LYS | Novel prediction |
| G12R | LYS | Novel prediction |

Full panel (G12D + G12V + G12R): **$12,000**
Single mutant: **$3,500**
Contact: axara@axara.bio

---

## Engine Validation — 9/9 PASS

| Target | Family | Drug | Known Site | Rank |
|--------|--------|------|-----------|------|
| KRAS G12C | GTPase | Sotorasib | CYS12 | 1 |
| BTK | Kinase | Ibrutinib | CYS481 | 1 |
| EGFR | Kinase | Osimertinib | CYS797 | 2 |
| MAOB | Oxidoreductase | Selegiline | CYS397 | 3 |
| EGFR | Kinase | Afatinib | CYS797 | 1 |
| BTK | Kinase | Zanubrutinib | CYS481 | 1 |
| EGFR T790M | Kinase | Neratinib | CYS797 | 2 |
| 3CLpro | Protease | Bofutrelvir | CYS145 | 3 |
| HER2 | RTK | Covalent inhibitor | CYS805 | 1 |

Pass criterion: known attachment site ranks within top 3 scored residues.
6/9 ranked first. Zero false negatives.

---

## Scoring Methodology

Three-component framework integrating:

1. **Binding pocket proximity** — fpocket Voronoi tessellation (Schmidtke & Barril, J Med Chem 2010)
2. **Solvent-accessible surface area** — Shrake-Rupley algorithm (Shrake & Rupley, J Mol Biol 1973)
3. **SDA chemistry preference** — published diazirine carbene insertion frequencies (Klinman 2017; Qin 2019; Hacker 2021)

Four sequential filters: transmembrane topology · disulfide bond status · surface burial · pocket-proximal CYS accessibility correction

Sensitivity analysis: 81 parameter combinations (±20% variation). Primary sites 100% rank stable.

Full methodology: bioRxiv preprint BIORXIV/2026/720342

---

## Free Resources

| Tool | URL |
|------|-----|
| Rule of 25 Engine | https://rule-25-engine-861834762353.us-central1.run.app/ |
| Mass Adduct Calculator | https://axara.bio/sda-mass-adduct-calculato |
| Carbene Insertion Frequencies | https://axara.bio/carbene-insertion-frequen |
| UV Crosslinking Guide | https://axara.bio/uv-crosslinking-guide |
| GPCR Topology Reference | https://axara.bio/gpcr-topology-reference |
| PAL Experiment Checklist | https://axara.bio/pal-experiment-checklist |

---

## Citation

If you use these datasets in your research, please cite:

**Dataset:**
> Hill T. AXARA BioScience Data Products. Zenodo. 2026.
> DOI: 10.5281/zenodo.19728050
> https://doi.org/10.5281/zenodo.19728050

**Methodology preprint:**
> Hill T. A Structure-Based Computational Framework for SDA Photoaffinity Probe Site Prioritisation: Validation Across Nine Approved Covalent Drug Targets and Application to Metabolic Disease GPCRs. bioRxiv. 2026. BIORXIV/2026/720342

---

## Contact

**AXARA BioScience**
axara@axara.bio | axara.bio | +27 83 407 6037

Zero Retention Certificate — your data is never stored or shared.

---

*Engine v4.0 | Atlas v1.0 | April 2026*
