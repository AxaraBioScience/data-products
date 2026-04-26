# p53 Y220C Covalent Tractability Map v1.1
### AXARA BioScience · Dataset Engine v3.0 · April 2026

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.19788871.svg)](https://doi.org/10.5281/zenodo.19788871)
[![Engine Validation](https://img.shields.io/badge/Engine%20Validation-5%2F5%20PASS-2E7D32)](https://doi.org/10.5281/zenodo.19788871)
[![Clinical Stage](https://img.shields.io/badge/Clinical-NDA%20Q1%202027-1a4a7a)](https://axara.bio/data-products)
[![Product](https://img.shields.io/badge/Product-$4%2C500-0E7C7B)](https://axara.bio/data-products)

---

## What This Is

The only independently validated, engine-scored SDA photoaffinity probe tractability map for the p53 Y220C neomorphic pocket.

Every nucleophilic residue in the p53 DNA-binding domain (residues 94–292) ranked by probe attachment tractability. Validated against five published co-crystal structures from three independent research groups. Two advanced experiment protocols not available anywhere else in the published literature.

**This repository contains the public documentation for this product.** The full data product — scored CSV, Digital Twin JSON, annotated PDB, validation certificate, and probe reference cards — is available at [axara.bio/data-products](https://axara.bio/data-products).

---

## Files in This Directory

| File | Description |
|---|---|
| `p53-Y220C-README.md` | This file |
| `p53-y220c-tractability-map.md` | Product whitepaper — what the report contains and why |
| `p53-y220c-newsletter.md` | Full technical newsletter — what the engine found and what it means |

---

## The Target

**TP53 Y220C** — the ninth most frequent TP53 mutation in human cancer.

~125,000 new cases per year across ovarian, lung, breast, endometrial, colorectal and other solid tumours.

The mutation replaces Tyr220 with a cysteine, creating a solvent-exposed neomorphic hydrophobic crevice of ~310 Å³ at the S7/S8 loop junction. This crevice does not exist in wild-type p53. It is both the drug target and the probe design target.

**CYS220 is the mutant residue. It is absent in wild-type p53.** A probe designed to crosslink CYS220 is inherently tumour-selective.

---

## Clinical Context

| Program | Company | Stage | Note |
|---|---|---|---|
| Rezatapopt (PC14586) | PMV Pharmaceuticals (NASDAQ: PMVP) | Phase 2 Registrational | PYNNACLE · NCT04585750 · NDA Q1 2027 · 34% ORR · NEJM Feb 2026 |
| JAB-30355 | Jacobio Pharmaceuticals | Phase 1 | IND cleared 2024 |
| NTS071 | UDO Biopharma | Phase 1 | FDA IND cleared April 2025 |
| FMC-220 | Frontier Medicines | Preclinical / IND-enabling | Covalent activator mechanism |

Four competing programs. None will publish their probe design data during active clinical development. This product is the only independent source of p53 Y220C probe site intelligence available to any of them without competitive exposure.

---

## Engine Results

**Primary scoring structure:** 8QWN (p53 Y220C apo, hexagonal crystal form, 1.85 Å, chain A, Joerger lab 2024)

**Scoring parameters:**
- Proximity decay: exp(−0.15 × dist_Å) — calibrated for surface crevice geometry
- SASA threshold: rel_SASA < 0.03 excluded
- Zinc coordination filter: CYS176, CYS238, CYS242, HIS179 excluded
- Valid range: residues 94–292 (DBD only)
- Pocket multiplier: 3.0× for CYS, 1.0× all others

**Results:**
- Residues scored: **33**
- Residues excluded: **23**
- Primary site rank: **#1**
- Primary site score: **18.31** (leads next-ranked residue by 3×)

---

## Validation — 5/5 PASS

Pass criterion: primary probe attachment site must rank in top 3 scored residues.

| Structure | Ligand | Attachment Site Confirmed | Engine Rank | Result |
|---|---|---|---|---|
| 8DC8 | KG13 (azaindole covalent agonist) | CYS220 — acrylamide Michael addition | #1 | ✅ PASS |
| 5G4O | CF3-PhiKan083 carbazole (1.35 Å) | CYS220 sulfur — CF3 F interactions | #1 | ✅ PASS |
| 2VUK | PhiKan083 pioneer (Joerger/Fersht MRC-LMB) | CYS220 pocket contact confirmed | #1 | ✅ PASS |
| 4AGP | Iodophenol — Leu145 halogen bond | CYS220 pocket occupancy confirmed | #1 | ✅ PASS |
| 5AOJ | Pyrrole-pyrazole — full pocket contact map | CYS220 — Leu145/Val147/Pro151/Thr230 | #1 | ✅ PASS |

*Note: 9S9O, 9BR3, 9BR4 (rezatapopt/PMV series) under wwPDB embargo April 2026. Published binding mode incorporated into probe design guidance. Will be added when coordinates release.*

Full validation methodology: [DOI 10.5281/zenodo.19788871](https://doi.org/10.5281/zenodo.19788871)

---

## Novel Contributions in This Product

**1. Zinc coordination filter**
CYS176, CYS238, CYS242, and HIS179 correctly excluded as zinc-coordinating residues. A naive SASA-based screen would flag all four as high-priority probe sites. This filter is unique to p53 and is not present in any published probe design guidance for this target.

**2. Proximity decay calibration**
Decay constant 0.15 Å⁻¹ selected for p53 Y220C surface crevice geometry — shallower than deep enclosed cavities such as KRAS Switch II (0.30 Å⁻¹). Published contact maps (5G4O, 5AOJ) confirm ligand contacts to residues up to 12 Å from pocket centroid.

**3. CYS277 Scientific Probe**
CYS277 on the L3 loop, adjacent to canonical DNA contact residues Arg273 and Arg248, identified as a scientific probe target for DNA contact surface mapping — distinct from the Y220C drug pocket programme. Paired experiment design specified: CYS277 labelling before and after stabiliser treatment as a structural pharmacodynamic marker for p53 reactivation.

**4. Protocol A — Rezatapopt competition assay**
Residue-level target engagement IC50 for a Phase 2 drug. No published method currently provides this measurement in intact protein or cell lysates.

**5. Protocol B — Tumour-selective in-cell labelling**
Exploits the absence of CYS220 in wild-type p53 for inherently tumour-selective crosslinking in mixed cell populations. Framework for PET tracer development specified.

---

## Pocket Architecture

The Y220C neomorphic crevice has three subsites:

**Central Cavity (~310 Å³)**
Bounded by S7/S8 loop (Pro222, Pro223, Thr230) and S3/S4 strand (Val147, Thr150, Pro151). Scaffold core sits here.

**Subsite 1 — Pocket opening**
Phe109, Leu145, Trp146. Halogen bond donors (I, Br) engage Leu145 backbone carbonyl at 2.8–3.0 Å. Confirmed in 4AGP.

**Subsite 2 — Hydrophobic channel**
Narrow channel gated by Pro153.

**Subsite 3 — Pocket floor**
CYS220 thiol. Primary SDA attachment zone. Rotamer switches trans (apo 8QWN) to gauche- (rezatapopt complex — published binding mode).

---

## Six Deliverables on Purchase

| Deliverable | Format | Description |
|---|---|---|
| Probe Design Report | PDF | Full ranked analysis, probe recommendations, advanced protocols, clinical landscape |
| Tractability Scores | CSV | All 33 scored residues — SASA, proximity, chemistry, evidence tier, region |
| Digital Twin | JSON | Machine-readable provenance — integrates with FragPipe, AlphaFold3, IND packages |
| Annotated PDB | PDB | 8QWN chain A, B-factor = tractability score · `spectrum b, blue_white_red, minimum=0, maximum=25` |
| Validation Certificate | PDF | 5/5 engine pass documentation |
| Probe Reference Cards | PDF | Bench-ready one-page cards per probe target |

---

## Evidence Tiers

| Tier | Label | Meaning |
|---|---|---|
| 1 | VALIDATED | Covalent attachment confirmed by X-ray crystallography |
| 2 | LITERATURE-SUPPORTED | Confirmed in published inhibitor binding data |
| 3 | LITERATURE-ADJACENT | In confirmed binding region, specific residue not directly tested |
| Sci | SCIENTIFIC PROBE | Publishable biology independent of Y220C drug pocket |
| 4 | NOVEL PREDICTION | Computationally predicted, no prior experimental confirmation |

---

## References

1. Guiley KZ, Shokat KM. *Cancer Discovery* 2023;13:56–69. PDB 8DC8.
2. Mavridi D et al. *Cell Death & Disease* 2026;17:268. PDB 9S9O (embargo).
3. Vu BT et al. *ACS Med Chem Lett* 2025;16:34–39. PDB 9BR4, 9BR3 (embargo).
4. Klett T et al. *ACS Pharmacol Transl Sci* 2024;7:3984–99. SNAr series.
5. Joerger AC et al. *Cell Death & Disease* 2024. PDB 8QWN.
6. Schram AM et al. *Cancer Treatment Reviews* 2025. PYNNACLE protocol.
7. PMV Pharmaceuticals. Full Year 2025 Results. GlobeNewswire March 2026.
8. Brunner J. *Annu Rev Biochem* 1993;62:483–514.
9. Kotzyba-Hibert F et al. *Angew Chem Int Ed* 1995;34:1296–1312.
10. Murale DP et al. *Proteome Sci* 2017;15:14.

---

## Citation

```
AXARA BioScience. (2026). AXARA Dataset Engine v3.0: SDA Photoaffinity Probe
Tractability Scoring for the p53 Y220C Neomorphic Pocket — Validation Against
Five Independent Co-Crystal Structures. Zenodo.
https://doi.org/10.5281/zenodo.19788871
```

---

## Purchase

**→ [axara.bio/data-products](https://axara.bio/data-products)**

**axara@axara.bio**

$4,500 · All six deliverables · 48-hour delivery · Institutional licensing available

---

*For research use only. Not for diagnostic or therapeutic application. All structural data derived from publicly deposited PDB structures. AXARA BioScience is not affiliated with PMV Pharmaceuticals, Jacobio Pharmaceuticals, UDO Biopharma, or Frontier Medicines.*

*Copyright © 2026 AXARA BioScience*
