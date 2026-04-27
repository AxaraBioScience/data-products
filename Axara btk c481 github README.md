# BTK C481 Covalent Tractability Map v1

**AXARA BioScience · [axara.bio](https://axara.bio) · axara@axara.bio**

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.19821043.svg)](https://doi.org/10.5281/zenodo.19821043)

---

> Three failure modes account for the majority of covalent probe programme
> losses in BTK drug discovery. This dataset is designed to eliminate all three
> before a single probe molecule is synthesised.

---

## The Problem This Solves

Every BTK probe programme faces the same three risks.

**Risk 1 — Probe site selection error**
You design against a residue that is buried, disulfide-bonded, or inaccessible
in the relevant biological context. Discovery occurs at the Western blot —
typically six to twelve months into the programme.

**Risk 2 — Off-target crosslinking**
Your probe crosslinks a kinase you did not intend to label. The competition
signal is misinterpreted as target engagement. Discovery occurs at the
proteomics stage, after biological conclusions have already been drawn.

**Risk 3 — Patient stratification error**
You run a probe-based assay in a resistance cohort without knowing which
mutations abolish probe labelling and which do not. Your dataset becomes
uninterpretable.

This dataset addresses all three — computationally, before synthesis begins.

---

## Target

**BTK — Bruton's Tyrosine Kinase**
UniProt Q06187 · Kinase domain residues 382–659
Primary covalent site: CYS481 — ATP-binding pocket hinge

Four FDA/EMA-approved covalent BTK inhibitors bind CYS481:
ibrutinib (Imbruvica), acalabrutinib (Calquence),
zanubrutinib (Brukinsa), and tirabrutinib (Velexbru).
Combined annual revenues exceed $12 billion.

---

## Validation — 4/4 PASS

Independent validation across four BTK crystal structures.
Pass criterion: CYS481 must rank in the top 3 scored residues.

| PDB | Context | Resolution | CYS481 Rank | Result |
|-----|---------|------------|-------------|--------|
| 5P9J | Ibrutinib-bound | 2.2 Å | **1** | ✓ PASS |
| 6J6M | Acalabrutinib-bound | 2.6 Å | **1** | ✓ PASS |
| 5VFI | WT apo kinase domain | 2.1 Å | **1** | ✓ PASS |
| 3GEN | WT apo kinase domain | — | **1** | ✓ PASS |

CYS481 ranks first in every structure tested — inhibitor-bound and apo forms.
No adjustment to engine parameters was made between validation structures.

Validation certificate: [10.5281/zenodo.19821043](https://doi.org/10.5281/zenodo.19821043)

---

## What The Full Dataset Contains

The Zenodo record contains the validation certificate only.
The full commercial dataset contains nine categories of deliverable:

**1. Full residue tractability map**
All nucleophilic residues in the BTK kinase domain scored and ranked.
Evidence tiers assigned. Do Not Pursue list with documented exclusion reasons.
Eliminates probe site selection error.

**2. Kinome selectivity analysis**
46 human kinases scored against the BTK CYS481 ATP pocket reference.
Identifies which kinases carry a structurally equivalent cysteine.
Eliminates off-target crosslinking risk before synthesis.

**3. Resistance variant atlas**
Computationally predicted structures for five clinically relevant BTK mutations.
Each variant classified for probe labelling compatibility.
Eliminates patient stratification error in resistance cohort studies.

**4. SDA probe scaffold library**
39 ranked candidate SDA probe scaffolds.
Scored by molecular weight, drug-likeness, synthetic accessibility,
cell permeability, and H-bond donors.
Full 2D structures in SDF format — loads directly into Schrödinger,
MOE, and RDKit pipelines.

**5. Four validated assay protocols**
Protocol A: probe site specificity confirmation.
Protocol B: resistance detection in patient-derived samples —
longitudinal monitoring of C481S clonal emergence.
Protocol C: distinguishing covalent from non-covalent BTK occupancy —
no published equivalent exists.
Protocol D: BTK degrader pharmacodynamic baseline —
applicable to all clinical-stage BTK PROTAC and molecular glue programmes.

**6. Annotated PDB structure**
B-factor annotated scored PDB — loads directly into PyMOL.
PyMOL session file included.

**7. Digital Twin JSON**
Machine-readable provenance record.
Pipeline-ready.

**8. Mutation compatibility YAML**
Machine-readable resistance variant table.
Parseable directly by Python and R pipelines.

**9. Validation certificate**
Engine parameters, pass/fail results, literature cross-validation table.
Zenodo DOI for citation.

---

## De-Risking Timeline

Without this dataset, the three failure modes are typically discovered at:

| Failure mode | Typical discovery point | Cost |
|---|---|---|
| Wrong probe site | 6–12 months post-synthesis | Full probe programme restart |
| Off-target crosslinking | Proteomics stage | 3–6 months of misattributed biology |
| Wrong patient cohort | Data lock | Uninterpretable resistance dataset |

With this dataset, all three are identified computationally before synthesis.
Discovery moves from the wet lab to the desktop.

---

## Engine

**AXARA Dataset Engine v3.0**

Three-component scoring:
- Binding pocket proximity — exponential decay from pocket centroid
- Solvent accessibility — BioPython ShrakeRupley, normalised to 40 Å²
- SDA chemistry preference — per residue type, published reactivity data

Final score = geometric mean of three components. Range 0–1.

Four exclusion filters: transmembrane topology, disulfide bonds,
buried SASA, fusion protein inserts.

The engine has been validated across three target families:
KRAS G12C, EGFR C797, and BTK C481.
Methods preprint in preparation.

---

## Pricing

| Tier | Price | Users |
|------|-------|-------|
| Research | $15,000 | 1 user |
| Discovery | $45,000 | 2–5 users |
| Programme | $75,000 | 1 programme team |
| Enterprise | $120,000+ | Organisation-wide + annual update |

---

## Contact

**Licensing and enquiries:** axara@axara.bio
**Website:** axara.bio
**Validation certificate DOI:** [10.5281/zenodo.19821043](https://doi.org/10.5281/zenodo.19821043)

---

## Citation

If you use this dataset or reference the validation results, please cite:

```
AXARA BioScience (2025). BTK CYS481 Covalent Probe Site Validation Certificate —
AXARA Dataset Engine v3.0. Zenodo. https://doi.org/10.5281/zenodo.19821043
```

---

*AXARA BioScience builds validated computational datasets for covalent drug discovery.
Our engine removes the three most common failure modes in probe programme design
before a single molecule is synthesised.*
