# AXARA BioScience — Dataset Repository

**Structural intelligence datasets for covalent probe design.**

This repository contains scientific whitepapers and methodology documentation for AXARA BioScience data products. All datasets are commercially available at [axara.bio/data-products](https://axara.bio/data-products).

---

## Available Datasets

### KRAS Mutant Covalent Tractability Map
**Status**: Available Now · From $6,000/mutant

Pre-computed SDA photoaffinity probe attachment site recommendations for KRAS G12C, G12D, G12V, and G12R. Validated three-component scoring engine. 4/4 pass rate against approved covalent drug co-crystal structures.

→ [Whitepaper](kras/whitepaper.md)
→ [Request dataset](https://axara.bio/data-products)

---

### GLP-1 GPCR Covalent Tractability Atlas
**Status**: Coming Q2 2026 · From $6,000/receptor · Full atlas $25,000

Pre-computed SDA probe design recommendations for GLP-1R, GIPR, Glucagon Receptor, and GLP-2R. Includes membrane topology filter and cross-receptor comparative analysis.

→ [Whitepaper](glp1/whitepaper.md)
→ [Join early access](https://axara.bio/data-products)

---

## What Each Dataset Includes

Every AXARA dataset is delivered as a nine-file package:

| File | Format | Purpose |
|------|--------|---------|
| Probe Design Map | PDF | Binding site and surface probe recommendations |
| Scored Residue Dataset | CSV | All scored residues with evidence classification |
| Digital Twin | JSON | ELN-ready provenance for IND and patent citation |
| Annotated Structures | PDB | Tractability scores in B-factor column |
| Validation Certificate | PDF | Engine validation documentation |
| Probe Reference Cards | PDF | Printable bench tool per target |

---

## Engine Validation

The AXARA Dataset Engine was validated against known covalent drug binding sites in four approved drug co-crystal structures:

| Target | Drug | Known Site | Engine Rank | Result |
|--------|------|-----------|-------------|--------|
| KRAS G12C | Sotorasib | CYS12 | 1 | ✓ PASS |
| BTK | Ibrutinib | CYS481 | 1 | ✓ PASS |
| EGFR | Osimertinib | CYS797 | 1 | ✓ PASS |
| MAOB | Selegiline | CYS397 | 3 | ✓ PASS |

**Overall: 4/4 PASS**

---

## Citation

If you use AXARA datasets in your research please cite:

```
AXARA BioScience (2026). [Dataset name and version].
AXARA Dataset Engine v3.0. axara.bio.
GitHub: github.com/axara-bioscience/datasets
```

---

## Contact

- **Website**: [axara.bio](https://axara.bio)
- **Data products**: [axara.bio/data-products](https://axara.bio/data-products)
- **Email**: info@axara.bio
- **WhatsApp**: +27 83 407 6037

For multi-site licensing, academic pricing, or custom target requests please contact info@axara.bio.

---

## Repository Structure

```
datasets/
├── README.md                   ← this file
├── kras/
│   └── whitepaper.md           ← KRAS methodology whitepaper
└── glp1/
    └── whitepaper.md           ← GLP-1 Atlas methodology whitepaper
```

---

*© 2026 AXARA BioScience. All rights reserved.*
*Scoring methodology and engine parameters are proprietary. Whitepapers describe methodology at a level sufficient for scientific citation and peer review without disclosing proprietary implementation details.*
