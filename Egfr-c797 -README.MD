# EGFR C797 Covalent Tractability Map

**AXARA BioScience · [axara.bio](https://axara.bio) · April 2026**

[![Validation](https://img.shields.io/badge/validation-6%2F6%20PASS-brightgreen)](https://axara.bio/data-products)
[![Engine](https://img.shields.io/badge/engine-AXARA%20v3.0-blue)](https://axara.bio)
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.10.5281/zenodo.19794917.svg)](https://doi.org/10.5281/zenodo.PENDING)

---

## What this is

A computed, literature-validated covalent tractability map for the EGFR kinase domain. It identifies and ranks all nucleophilic residues in the kinase domain (residues 696–1022) by their suitability as SDA Me-Diazirine photoaffinity probe attachment sites.

**Primary probe site:** CYS797 — the ATP-binding pocket hinge cysteine. Covalent attachment site for osimertinib (Tagrisso), afatinib (Gilotrif), neratinib (Nerlynx), rociletinib, and dacomitinib (Vizimpro). Validated at rank #1 across six independent EGFR crystal structures.

**Discovery site:** CYS775 — a back-pocket cysteine with no approved drug. Active against C797S-mutant EGFR — the dominant resistance mechanism to osimertinib (~40% of resistance cases). Characterised here for the first time in a commercial tractability report.

---

## Validation

CYS797 ranks #1 in all six validation structures. Pass criterion: rank ≤ 3.

| PDB ID | Drug / context | Resolution | CYS797 rank |
|---|---|---|---|
| 4WD5 | Osimertinib (FDA/EMA approved) | 1.95 Å | #1 |
| 4ZAU | Rociletinib (Phase III) | 2.1 Å | #1 |
| 4G5J | Afatinib + L858R (FDA/EMA approved) | 3.05 Å | #1 |
| 2JIV | Wild-type apo kinase domain | 2.8 Å | #1 |
| 3W2S | T790M apo kinase domain | 2.5 Å | #1 |
| 2JIT | Wild-type apo (2nd copy) | 2.8 Å | #1 |

---

## What makes this report different

**CYS775 as a discovery site.** CYS775 ranks #2 out of 60 scored residues with a score of 9.64/25.0. Published inhibitors targeting CYS775 show nanomolar potency against C797S-mutant EGFR (Kuki et al. 2023; Wittlinger et al. 2024). The Gray lab bidentate compound YNW-1 (bioRxiv December 2025) engages both CYS775 and CYS797 simultaneously, demonstrating slower resistance emergence than osimertinib. No approved drug targets CYS775.

**Protocol B — C797S resistance detection.** An SDA probe crosslinks CYS797 in wild-type EGFR and all sensitising mutation backgrounds (L858R, exon19del, T790M) but does not label C797S-mutant EGFR. As resistant clones emerge under osimertinib selection, probe signal at CYS797 decreases quantitatively. Residue-level longitudinal resistance monitoring from tumour lysates — no published method achieves this.

**Protocol C — redox competition.** CYS797 undergoes H₂O₂-driven sulfenylation in response to EGF signalling, enhancing kinase activity (Heppner et al. 2018). An SDA probe competes directly with this modification. Protocol C documents this as a pharmacodynamic readout for oxidative stress-driven drug resistance in the tumour microenvironment. No existing tractability report covers this angle.

**Cross-mutant utility.** One probe covers wild-type, L858R, exon19del, T790M, and L858R+T790M EGFR. C797S is the only clinical background that abolishes labelling — making the negative result a resistance assay.

---

## Six deliverables

| File | Contents |
|---|---|
| Main PDF report | Scored residue table · evidence tiers · Protocols A/B/C · cross-mutant table · 10 references |
| Tractability CSV | 60 scored residues — SASA, proximity, score, region, evidence tier |
| Digital Twin JSON | Machine-readable provenance for LIMS and pipeline integration |
| Annotated PDB | B-factor = tractability score — open in PyMOL in 30 seconds |
| Validation Certificate | 6/6 structure panel · Zenodo DOI · novel contributions documented |
| Probe Reference Cards | Bench-ready one-page cards for CYS797 and CYS775 |

---

## Licensing

| Tier | Price | Users | For |
|---|---|---|---|
| Research | $7,500 | 1 named user | Academic PI · individual researcher |
| Discovery | $15,000–$25,000 | 2–5 users | Biotech · CRO |
| Enterprise | $50,000+ | Organisation-wide | Big Pharma · global R&D |

→ [Buy Research Licence](https://axara.bio/data-products)  
→ [Enterprise enquiry](mailto:axara@axara.bio)

---

## References

1. Brunner J (1993) New photolabeling and crosslinking methods. *Annu Rev Biochem* 62:483–514.
2. Kotzyba-Hibert F et al. (1995) Recent trends in photoaffinity labeling. *Angew Chem Int Ed Engl* 34:1296–1312.
3. Murale DP et al. (2017) Photo-affinity labeling in chemical proteomics. *Proteome Sci* 15:14.
4. Yosaatmadja Y et al. (2015) EGFR kinase + osimertinib at 1.95 Å. PDB: 4WD5.
5. Heppner DE et al. (2018) Molecular basis for redox activation of EGFR kinase. *Structure* 26:1372–1383.
6. Kuki N et al. (2023) Covalent fragment strategy targeting CYS775. *RSC Med. Chem.* 14:2731–2737.
7. Wittlinger F et al. (2024) Alkynylpyridopyrimidinones targeting CYS775. *J. Med. Chem.* 67:21438–21469.
8. Li Z, Gray NS et al. (2025) Bidentate C775+C797 inhibitors. *bioRxiv* 2025.11.28.691243.
9. Zhang D et al. (2025) Fourth-generation EGFR-TKI review. *J Enzyme Inhib Med Chem* 40:2481392.
10. Heppner DE, Carroll KS (2022) CYS797 sulfenic acid signalling. *Cell Chem Biol* 29:792–806.

---

## Citation

```
AXARA BioScience (2026). EGFR C797 Covalent Tractability Map v1.0.
AXARA Dataset Engine v3.0. https://axara.bio/data-products
DOI: 10.5281/zenodo.PENDING
```

---

*AXARA BioScience · axara.bio · axara@axara.bio*
