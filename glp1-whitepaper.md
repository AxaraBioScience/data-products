# AXARA BioScience — GLP-1 GPCR Covalent Tractability Atlas
## Methodology Whitepaper · Dataset Engine v3.0 · Coming Q2 2026

---

### Abstract

This whitepaper describes the planned computational methodology for the AXARA GLP-1 GPCR Covalent Tractability Atlas — a pre-computed SDA photoaffinity probe design dataset covering four metabolic disease GPCRs: GLP-1 Receptor (GLP-1R), GIP Receptor (GIPR), Glucagon Receptor (GCGR), and GLP-2 Receptor (GLP-2R).

The atlas applies the same validated three-component scoring engine used in the AXARA KRAS dataset, with additional methodology for transmembrane protein topology filtering — ensuring probe recommendations reflect extracellular and intracellular accessible residues rather than membrane-embedded domains inaccessible to aqueous probes.

**Status**: In development. Expected release Q2 2026. Early access pricing available — contact info@axara.bio.

---

### 1. Background

GLP-1 receptor agonists (semaglutide, liraglutide, tirzepatide) represent the fastest-growing drug class in metabolic disease. The mechanistic basis for their efficacy — and for the differences between GLP-1R, GIPR, and GCGR signalling — is incompletely understood at the residue level.

Photoaffinity labelling with SDA probes provides a direct experimental approach to mapping ligand-receptor contacts, allosteric sites, and effector binding interfaces. However, GPCR probe design faces a unique challenge absent from soluble protein targets: the majority of residues are embedded in the lipid bilayer and inaccessible to aqueous SDA probes.

The AXARA GLP-1 Atlas addresses this by applying a membrane topology filter to restrict recommendations to extracellular domains, intracellular loops, and the cytoplasmic face — the regions accessible to SDA probes in standard PAL experiments.

---

### 2. Target Panel

| Receptor | Gene | Disease relevance | Approved drugs |
|----------|------|------------------|----------------|
| GLP-1R | GLP1R | Type 2 diabetes, obesity | Semaglutide, liraglutide, exenatide |
| GIPR | GIPR | Type 2 diabetes, obesity | Tirzepatide (dual GLP-1R/GIPR) |
| GCGR | GCGR | Type 2 diabetes, hypoglycaemia | Cotadutide (dual GLP-1R/GCGR) |
| GLP-2R | GLP2R | Short bowel syndrome | Teduglutide |

---

### 3. Methodology

#### 3.1 Three-Component Scoring

The atlas uses the same validated three-component engine as the KRAS dataset:

1. **Binding pocket proximity** — fpocket Voronoi tessellation on available crystal structures and cryo-EM models
2. **Solvent accessibility** — Shrake-Rupley SASA on chain A
3. **Residue-type SDA chemistry preference** — same coefficients as KRAS dataset

The engine was validated at 4/4 pass rate against approved covalent drug co-crystal structures prior to application to GPCR targets. See the KRAS whitepaper for full validation details.

#### 3.2 Membrane Topology Filter

GPCRs contain seven transmembrane helices with residues embedded in the lipid bilayer. These residues have near-zero effective SASA in an aqueous probe context and cannot be reached by SDA probes in standard PAL experiments.

The topology filter applies the following classification to each residue:

| Domain | Filter | Probe accessible |
|--------|--------|-----------------|
| N-terminal extracellular domain | Include | Yes |
| Extracellular loops (ECL1, ECL2, ECL3) | Include | Yes |
| Transmembrane helices (TM1-7) | Exclude | No |
| Intracellular loops (ICL1, ICL2, ICL3) | Include | Yes |
| C-terminal intracellular domain | Include | Yes |

Topology assignments are derived from UniProt topology annotations and cross-validated against available crystal structures.

#### 3.3 Structure Sources

| Receptor | PDB / Model | Resolution | Notes |
|----------|-------------|------------|-------|
| GLP-1R | 5VAI, 6X1A | 2.7 Å, 3.3 Å | Peptide-bound and apo |
| GIPR | 7DTY | 3.3 Å | Tirzepatide-bound |
| GCGR | 5EE7, 6LMK | 2.8 Å, 3.0 Å | Apo and antagonist-bound |
| GLP-2R | AlphaFold2 | Predicted | No experimental structure available |

For GLP-2R, AlphaFold2 predicted structure will be used with confidence filtering (pLDDT > 70) to exclude low-confidence loop regions from recommendations.

---

### 4. Atlas Structure

The full atlas contains:

**Per-receptor sections** (4 receptors):
- Binding site probe recommendations — extracellular and intracellular separately
- Surface accessibility probes — for positive controls
- Do not use list — transmembrane residues and unstable loop regions
- Evidence tier classification (VALIDATED / LITERATURE-SUPPORTED / NOVEL PREDICTION)

**Cross-receptor comparative analysis** (full atlas only):
- Pan-receptor probe opportunities — residues accessible across multiple receptors
- Selectivity insights — sites unique to one receptor vs conserved across the panel
- Tirzepatide dual-receptor binding context — GLP-1R and GIPR shared sites

---

### 5. Deliverables

Each atlas purchase includes:

| File | Format | Purpose |
|------|--------|---------|
| Probe design report | PDF | Full binding site and surface probe recommendations |
| Scored residue dataset | CSV | All accessible residues with scores and topology classification |
| Digital Twin | JSON | ELN-ready provenance for IND/patent citation |
| Annotated structures | PDB × 4 | B-factors replaced by tractability scores |
| Validation Certificate | PDF | Engine 4/4 pass against approved covalent drugs |
| Probe Reference Cards | PDF | One A4 per receptor for bench use |
| Cross-receptor analysis | PDF | Full atlas only — pan-receptor opportunities |

---

### 6. Pricing

| Product | Price |
|---------|-------|
| Single receptor report | $6,000 – $8,000 |
| Any two receptors | $14,000 |
| Full atlas (all four receptors + cross-receptor analysis) | $25,000 |

Early access pricing available for Q2 2026 launch. Contact info@axara.bio.

---

### 7. Limitations

- Cryo-EM and crystal structures of GPCRs represent conformational snapshots — multiple conformations exist in solution
- AlphaFold2 structure used for GLP-2R introduces additional uncertainty in loop region predictions
- Transmembrane residue accessibility in detergent-solubilised or nanodisc preparations may differ from lipid bilayer conditions
- All recommendations are computational predictions requiring experimental validation

---

### 8. Citation

```
AXARA BioScience (2026). GLP-1 GPCR Covalent Tractability Atlas v1.0.
Dataset Engine v3.0. axara.bio. DOI: pending.
GitHub: github.com/axara-bioscience/datasets
```

---

### 9. Early Access

To join the early access list for the GLP-1 Atlas:

- Email: info@axara.bio
- Subject: GLP-1 Atlas Early Access
- Include: institution, receptor(s) of interest, intended use case

Early access customers receive priority delivery, pre-launch pricing, and the option to provide input on receptor selection and probe chemistry focus areas.

---

*AXARA BioScience · axara.bio · info@axara.bio · April 2026*
*This whitepaper describes planned methodology subject to refinement prior to release.*
