# AXARA BioScience — KRAS Mutant Covalent Tractability Map
## Methodology Whitepaper · Dataset Engine v3.0 · April 2026

---

### Abstract

This whitepaper describes the computational methodology used to generate the AXARA KRAS Mutant Covalent Tractability Map — a pre-computed SDA photoaffinity probe design dataset covering four major KRAS oncogenic mutants: G12C, G12D, G12V, and G12R. The dataset provides residue-level probe attachment site recommendations, structured for direct use in photoaffinity labelling (PAL) experimental design.

The scoring engine uses a three-component model combining binding pocket proximity (fpocket Voronoi tessellation), solvent-accessible surface area (Shrake-Rupley algorithm), and residue-type SDA photochemistry preference. The engine was validated against known covalent drug binding sites in four approved drug co-crystal structures, achieving a 4/4 pass rate.

---

### 1. Background

Photoaffinity labelling with SDA (succinimidyl 4,4′-azipentanoate) diazirine reagents has become a standard approach for mapping protein-ligand interactions in covalent chemical biology. A central challenge in PAL experiment design is selecting which residue to target for probe attachment — a decision that determines crosslinking efficiency, target engagement confidence, and structural interpretability of mass spectrometry data.

For well-characterised targets such as KRAS G12C, the covalent attachment site is established by clinical drugs. For the remaining KRAS mutants — G12D (present in 36% of KRAS-mutant cancers), G12V, and G12R — no approved covalent therapy exists and probe attachment site selection has relied on manual structural analysis or been absent entirely.

The AXARA Dataset Engine addresses this gap by providing systematic, validated, computationally-derived probe attachment site recommendations for all four major KRAS mutants.

---

### 2. Computational Methodology

#### 2.1 Three-Component Scoring

Each nucleophilic residue (CYS, LYS, TYR, HIS, SER, THR) in chain A of each target structure is assigned a tractability score using three components:

**Component 1 — Binding Pocket Proximity (fpocket)**

Pocket detection was performed using fpocket v4.0 (Schmidtke & Barril, 2010), which identifies protein surface cavities using Voronoi tessellation of alpha-sphere centres. For each residue, the minimum distance from any residue atom to any pocket atom coordinate was calculated. Proximity is scored as:

```
proximity = max(0, 1 - (min_distance / threshold))
```

with a distance threshold of 8.0 Å. Pocket identification used the Switch II pocket anchor residues HIS95 and TYR64 to identify the biologically relevant pocket from among all detected pockets.

**Component 2 — Solvent Accessible Surface Area (Shrake-Rupley)**

SASA was calculated using the Shrake-Rupley rolling sphere algorithm as implemented in BioPython (Cock et al., 2009), with a probe radius of 1.4 Å on chain A of each structure. SASA values were normalised to a maximum reference of 150 Å².

**Component 3 — SDA Chemistry Preference**

Residue-type chemistry scores reflect known SDA carbene reactivity with amino acid side chains:

| Residue | Chemistry Score | Rationale |
|---------|----------------|-----------|
| CYS | 10.0 | Thiol — highest SDA carbene reactivity |
| LYS | 6.0 | Primary amine — efficient NHS ester conjugation |
| TYR | 5.0 | Phenol — moderate SDA reactivity |
| HIS | 4.0 | Imidazole — pH-dependent, feasible |
| SER | 2.5 | Hydroxyl — lower reactivity |
| THR | 2.0 | Hydroxyl — sterically hindered |

**Combined Score Formula**

```
base_score = chemistry × (0.4 + 0.6 × accessibility)
pocket_mult = 3.0 if CYS else 1.0
total_score = min(base_score + proximity × 8.0 × pocket_mult, 25.0)
```

The CYS pocket multiplier reflects the exceptional SDA carbene reactivity of thiols relative to other nucleophiles when in a binding pocket context.

#### 2.2 Two-Structure Approach

A two-structure approach was used to separate pocket detection from accessibility scoring:

- **Pocket detection**: Apo (unliganded) structures where available, to ensure the binding site cavity is not occluded by a bound ligand
- **SASA scoring**: The same apo structure, ensuring accessibility reflects the unoccupied protein

For KRAS G12C, the ligand-bound structure (6OIM) was used for both, as the partially buried CYS12 in the sotorasib co-crystal structure is the correct reference for the clinically validated site.

| Mutant | Pocket Structure | PDB | Type |
|--------|-----------------|-----|------|
| G12C | 6OIM | Sotorasib co-crystal | Ligand-bound |
| G12D | 4EPV | GDP-bound apo | Apo |
| G12V | 4TQ9 | GDP-bound apo | Apo |
| G12R | 4QL3 | GDP-bound apo | Apo |

#### 2.3 Evidence Tiers

Scored residues are classified into evidence tiers:

- **VALIDATED**: Engine prediction confirmed against an approved covalent drug co-crystal structure
- **LITERATURE-SUPPORTED**: Residue named in published inhibitor binding or fragment screening data
- **NOVEL PREDICTION**: Three-component engine prediction — not previously characterised experimentally

---

### 3. Validation

The engine was validated against known covalent drug binding sites in four approved drug co-crystal structures:

| Target | PDB | Drug | Known Site | Engine Rank | Result |
|--------|-----|------|-----------|-------------|--------|
| KRAS G12C | 6OIM | Sotorasib | CYS12 | 1 | PASS |
| BTK | 3GEN (apo) | Ibrutinib | CYS481 | 1 | PASS |
| EGFR | 6JX0 | Osimertinib | CYS797 | 1 | PASS |
| MAOB | 2V5Z | Selegiline | CYS397 | 3 | PASS |

**Pass criteria**: Known covalent attachment site ranks in top 3 scored residues.

**Overall result**: 4/4 PASS

---

### 4. Results Summary

#### KRAS G12C
- **Binding site probes**: CYS12 (VALIDATED), TYR64 (LITERATURE-SUPPORTED), HIS95
- **Surface probes**: LYS169 (positive control)
- **CYS12** is the Switch II pocket thiol exploited by sotorasib and adagrasib

#### KRAS G12D
- **Binding site probes**: TYR64 (LITERATURE-SUPPORTED — MRTX1133 contact residue, Wang et al. J Med Chem 2022), HIS95 (LITERATURE-SUPPORTED), LYS101 (NOVEL PREDICTION)
- **Surface probes**: LYS128, LYS147
- No CYS12 — Asp12 substitution eliminates the Switch II thiol

#### KRAS G12V
- **Binding site probes**: LYS101 (NOVEL PREDICTION), HIS95/94 (LITERATURE-SUPPORTED — Switch II anchor, Broker et al. J Med Chem 2022), TYR64 (LITERATURE-SUPPORTED)
- **Surface probes**: LYS165 (highest SASA across all mutants), LYS128

#### KRAS G12R
- **Binding site probes**: LYS101 (NOVEL PREDICTION), HIS95/94 (LITERATURE-SUPPORTED), TYR64 (LITERATURE-SUPPORTED)
- **Surface probes**: LYS165, LYS169
- Published covalent targeting of ARG12 directly (Fell et al. JACS 2022) provides orthogonal experimental evidence for Switch II pocket tractability

---

### 5. Probe Design Guidance

#### Binding Site Probes
Design your scaffold to bind the Switch II pocket using the PDB structure listed above as template. Attach SDA at the recommended residue using the following chemistry:

- **CYS sites**: NHS ester conjugation to thiol (thioester linkage). Linker: 4-6 carbon. UV: 365 nm.
- **LYS sites**: NHS ester conjugation to primary amine. Linker: 4-6 carbon. UV: 365 nm.
- **TYR sites**: Aryl-SDA conjugate. Phenol crosslinks under standard PAL conditions.
- **HIS sites**: SDA crosslinking to imidazole. Optimise pH 6.5-7.4.

#### Surface Probes
Surface probes (high SASA, low pocket proximity) are recommended for:
1. Positive controls to confirm probe reaches the protein
2. Establishing crosslinking conditions before binding site experiments
3. Whole-protein surface mapping studies

Do not use surface probe results to draw conclusions about binding site engagement.

---

### 6. Limitations

- All recommendations are computational predictions and require experimental validation
- Static crystal structures do not capture protein dynamics — loop flexibility may affect accessibility in solution
- The scoring coefficients for SDA chemistry preference are based on published photochemistry literature principles, not a formal regression against experimental crosslinking efficiency data
- LYS site recommendations are novel predictions without published experimental validation; CYS and TYR sites have literature support
- Membrane protein topology was not applied in this dataset — relevant for future GPCR datasets

---

### 7. Software and Data Sources

| Component | Tool | Version | Reference |
|-----------|------|---------|-----------|
| Pocket detection | fpocket | 4.0 | Schmidtke & Barril, J Chem Inf Model 2010 |
| SASA calculation | BioPython Shrake-Rupley | 1.81 | Cock et al., Bioinformatics 2009 |
| Structure parsing | BioPython MMCIFParser | 1.81 | Cock et al., Bioinformatics 2009 |
| Structures | RCSB Protein Data Bank | — | Berman et al., Nucleic Acids Res 2000 |

All PDB structures are used under the RCSB PDB open access policy.

---

### 8. Citation

If you use this dataset or methodology in your research, please cite:

```
AXARA BioScience (2026). KRAS Mutant Covalent Tractability Map v3.0.
Dataset Engine v3.0. axara.bio. DOI: pending.
GitHub: github.com/axara-bioscience/datasets
```

---

### 9. References

- Wang X et al. Identification of MRTX1133, a noncovalent, potent, and selective KRASG12D inhibitor. *J Med Chem* 2022; 65(4):3123–3133.
- Broker J et al. Fragment optimization of reversible binding to the switch II pocket on KRAS leads to a potent, in vivo active KRASG12C inhibitor. *J Med Chem* 2022; 65(21):14614–14629.
- Fell JB et al. Chemoselective covalent modification of K-Ras(G12R) with a small molecule electrophile. *J Am Chem Soc* 2022; 144(35):15916–15921.
- Schmidtke P, Barril X. Understanding and predicting druggability: a high-throughput method for detection of drug binding sites. *J Med Chem* 2010; 53(15):5858–5867.
- Cock PJA et al. Biopython: freely available Python tools for computational molecular biology and bioinformatics. *Bioinformatics* 2009; 25(11):1422–1423.

---

*AXARA BioScience · axara.bio · info@axara.bio · April 2026*
*Confidential methodology documentation — dataset licensed for single-institution use*
