# The Three Risks Every BTK Probe Programme Carries —
# And How Computational Tractability Analysis Eliminates Them Before Synthesis

**AXARA BioScience · axara.bio**
*A technical whitepaper on covalent probe site validation for BTK CYS481*

---

## Introduction

Bruton's Tyrosine Kinase (BTK) is the second-largest validated covalent target
in oncology after EGFR. Four FDA and EMA-approved covalent BTK inhibitors —
ibrutinib, acalabrutinib, zanubrutinib, and tirabrutinib — share a single
mechanism: irreversible covalent bond formation with CYS481, a cysteine residue
in the ATP-binding pocket hinge of the BTK kinase domain.

The commercial validation of CYS481 as a covalent attachment site is beyond
question. Combined annual revenues from BTK inhibitors exceeded $12 billion
in 2024. The structural basis for CYS481 reactivity has been confirmed by
X-ray crystallography across multiple inhibitor-bound and apo structures,
and by mass spectrometry studies documenting irreversible adduct formation
with the ibrutinib acrylamide warhead.

Yet despite this extraordinary level of clinical and structural validation,
BTK probe programmes — academic and industrial — continue to encounter the
same three failure modes at predictable points in the development timeline.

This whitepaper describes those failure modes, explains why they occur even
in well-resourced programmes, and outlines the computational framework that
eliminates all three before a single probe molecule is synthesised.

---

## The Clinical Context: Why BTK Probe Design Matters Now

The BTK inhibitor landscape has changed fundamentally since the approval of
pirtobrutinib (Jaypirca, FDA 2023) — the first non-covalent BTK inhibitor
approved for patients who have failed covalent therapy.

Pirtobrutinib was developed specifically to address the dominant resistance
mechanism to ibrutinib, acalabrutinib, and zanubrutinib: the C481S mutation.
Serine substitution at position 481 abolishes the covalent bond between the
drug's electrophilic warhead and the BTK thiol, rendering all three approved
covalent inhibitors pharmacologically inert at that site.

C481S accounts for approximately 80% of clinical ibrutinib resistance cases.
In a patient population of 200,000 or more CLL patients in the United States
alone, this represents a substantial and growing cohort of patients transitioning
from covalent to non-covalent BTK inhibitor therapy.

Simultaneously, a new generation of BTK-directed degraders — PROTACs and
molecular glues — has entered clinical development. NX-5948 (Nurix Therapeutics),
BGB-16673 (BeiGene), and several other agents are in Phase 1 and Phase 1/2
trials, recruiting patients who have failed both covalent and non-covalent
BTK inhibitor therapy.

Each of these clinical developments creates a specific and unmet need for a
validated CYS481 SDA photoaffinity probe:

For resistance research: a probe that labels WT BTK but not C481S-mutant BTK
provides a direct protein-level readout of covalent site availability —
complementary to, and more informative than, DNA-level resistance detection
by NGS or ddPCR.

For combination therapy research: a probe that can be used alongside pirtobrutinib
to distinguish covalent from non-covalent BTK occupancy in the same experiment
addresses a pharmacological question that no published assay currently answers.

For degrader programmes: a probe that quantifies residual BTK pool before and
after PROTAC or molecular glue treatment provides the pharmacodynamic baseline
that clinical pharmacology teams require for dose optimisation and resistance
monitoring.

The scientific demand for a validated BTK CYS481 probe has never been greater.
The three failure modes described below are what stand between that demand and
a working assay.

---

## Failure Mode 1 — Probe Site Selection Error

### What happens

A probe is designed against a BTK residue that is computationally predicted,
structurally adjacent to the known pharmacophore, or selected on the basis of
literature precedent from a related kinase. The probe is synthesised, validated
for BTK binding by SPR or ITC, and advanced to cell-based experiments.

The Western blot shows no band, or a band that does not compete with ibrutinib.
The probe is labelling something — but not CYS481.

### Why it happens

CYS481 presents a structural paradox that is not apparent from sequence analysis
alone. In inhibitor-bound crystal structures, the ATP pocket is occupied by the
co-crystallised ligand. CYS481 has effectively zero solvent accessible surface
area in these structures — it is completely buried by the drug molecule.

A naive SASA-based accessibility calculation on an ibrutinib-bound structure
will exclude CYS481 from consideration. A pocket detection algorithm such as
fpocket will identify zero pockets in the ATP site because the cavity is
pharmacologically occupied.

Without a framework that explicitly accounts for ligand-induced burial —
and rescues pocket-proximal cysteines that are accessible in the apo state —
CYS481 will score poorly or be excluded from the tractability analysis entirely.

The residues that score well under a naive analysis are surface-exposed
nucleophiles with high absolute SASA: lysines and tyrosines on the protein
surface that are accessible but pharmacologically irrelevant.

### The computational solution

A validated tractability engine must incorporate a pocket-proximal bypass:
a mechanism that identifies cysteines buried by co-crystallised ligands
and rescues them from SASA exclusion when they fall within a defined
distance of the known pocket centroid.

This bypass must be validated against experimental data — not just applied
as a heuristic. The bypass is only credible if CYS481 achieves a top-3
ranking across multiple independent crystal structures, including both
inhibitor-bound and apo forms, without modification of engine parameters
between structures.

---

## Failure Mode 2 — Off-Target Crosslinking

### What happens

A probe designed against CYS481 is used in a competition experiment.
Ibrutinib pre-treatment reduces probe signal. The researcher concludes
that the probe is CYS481-specific and advances to cell-based and
patient-derived sample experiments.

Months later, a chemoproteomics experiment reveals that the probe is
also labelling one or more non-BTK kinases at levels sufficient to
contribute to the competition signal. The biological conclusions
drawn from the probe assay require reassessment.

### Why it happens

The BTK ATP pocket geometry is not unique. Across the 518 human kinases,
multiple members carry a cysteine residue in a structurally analogous
position to CYS481 — within the ATP-binding hinge or at the pocket entrance.

The proximity of these residues to a druggable cavity, combined with their
solvent exposure and intrinsic cysteine reactivity, means that an SDA
diazirine probe optimised for CYS481 may crosslink them under physiological
conditions.

The ibrutinib competition experiment does not distinguish CYS481-specific
labelling from off-target labelling at other kinases that happen to be
displaced by ibrutinib at the concentrations used. A positive competition
result is necessary but not sufficient evidence for CYS481 specificity.

### The computational solution

Kinome selectivity analysis — scoring the most accessible cysteine in each
of 46 or more human kinases against the BTK CYS481 structural reference —
identifies which kinases carry a comparable tractability score to CYS481
before the probe is synthesised.

Kinases scoring above a high-risk threshold require inclusion in the
selectivity panel from the outset. Kinases scoring below a minimal-risk
threshold can be deprioritised.

This analysis transforms selectivity panel design from a post-hoc
damage limitation exercise into a prospective, data-driven decision
made before a single molecule is synthesised.

---

## Failure Mode 3 — Patient Stratification Error

### What happens

A probe-based longitudinal assay is designed to monitor resistance emergence
in a CLL patient cohort receiving ibrutinib. PBMC samples are collected at
baseline and at defined timepoints. The probe is applied to lysates,
BTK is immunoprecipitated, and probe:total BTK ratios are calculated.

At month 12, the data shows unexplained variance. Some patients show falling
ratios consistent with C481S emergence. Others show stable ratios despite
clinical ibrutinib failure. The dataset is difficult to interpret.

Post-hoc NGS reveals that several patients with clinical resistance carry
T474I or L528W mutations rather than C481S. These mutations confer ibrutinib
resistance through non-covalent mechanisms — but CYS481 is structurally
intact. The probe labels their BTK normally. Their stable probe:total ratio
was not a data quality issue — it was a correct readout that the study
design was not equipped to interpret.

### Why it happens

The assumption embedded in most probe-based resistance assays is that
ibrutinib resistance equals C481S equals abolished probe labelling.
This assumption is incorrect for approximately 20% of resistance cases.

T474I, T474A, and L528W mutations confer ibrutinib resistance through
mechanisms that do not affect CYS481 — gate-keeper residue changes,
allosteric conformational shifts, and other structural alterations that
reduce ibrutinib binding affinity without altering the thiol chemistry
at position 481.

A patient with T474I resistance has BTK that cannot be effectively
inhibited by ibrutinib but can still be labelled by a CYS481-directed
probe. Without knowing this in advance, the probe data is misinterpreted.

### The computational solution

A resistance variant atlas — built from computationally predicted structures
of clinically relevant BTK mutations and scored through the same tractability
engine — provides probe labelling compatibility classifications for each
mutation before the assay is designed.

This classification directly informs patient stratification:
which patients in a resistance cohort are expected to show probe labelling
(CYS481-intact variants) and which are not (CYS481-abolished variants).
The assay design and data interpretation framework are built around this
classification from the outset.

---

## The AXARA Approach

The AXARA Dataset Engine v3.0 was developed specifically to address these
three failure modes through a validated computational framework applied
prior to probe synthesis.

The engine combines three independent scoring signals — binding pocket
proximity, solvent accessible surface area, and SDA diazirine chemistry
preference — into a single tractability score for every nucleophilic
residue in the target protein. Four exclusion filters are applied:
transmembrane topology, disulfide bond involvement, buried SASA below
threshold, and fusion protein contamination.

Critically, the engine incorporates the pocket-proximal bypass described
above — rescuing CYS481 from SASA exclusion in inhibitor-bound structures
through explicit identification of the ATP pocket lining residues.

The BTK C481 Covalent Tractability Map v1 is the output of this engine
applied to the BTK kinase domain. It has been independently validated
across four BTK crystal structures. The validation certificate is publicly
available at Zenodo (DOI: 10.5281/zenodo.19821043).

The full dataset addresses each failure mode directly:

Failure Mode 1 is addressed by the full residue tractability map with
evidence tiers, documented exclusion reasons, and the Do Not Pursue list.

Failure Mode 2 is addressed by the kinome selectivity analysis across
46 human kinases.

Failure Mode 3 is addressed by the resistance variant atlas for five
clinically relevant BTK mutations, with probe labelling compatibility
classified for each.

Additionally, the dataset includes a ranked SDA probe scaffold library
of 39 candidates with full physicochemical profiling and 2D structures
in SDF format — and four validated assay protocols, two of which address
experimental contexts for which no published method currently exists.

---

## Conclusion

CYS481 is the right probe site for BTK. The clinical validation is
unambiguous. The structural basis is confirmed across multiple independent
crystal structures. The disease relevance — CLL, MCL, Waldenström's
macroglobulinaemia, and a growing resistance and degrader landscape —
is urgent and commercially substantial.

The three failure modes described in this whitepaper are not hypothetical.
They represent real costs — in time, in resources, and in biological
conclusions that require revision — incurred by programmes that begin
probe synthesis without a validated computational framework.

The BTK C481 Covalent Tractability Map v1 is that framework.
It is designed to move probe site selection, kinome selectivity assessment,
and patient stratification from the wet lab to the desktop —
before a single molecule is synthesised.

---

## Access and Licensing

**Validation certificate (public):**
Zenodo DOI: 10.5281/zenodo.19821043
https://doi.org/10.5281/zenodo.19821043

**Full dataset (commercial licence):**

| Tier | Price | Users |
|------|-------|-------|
| Research | $15,000 | 1 user |
| Discovery | $45,000 | 2–5 users |
| Programme | $75,000 | 1 programme team |
| Enterprise | $120,000+ | Organisation-wide + annual update |

**Contact:** axara@axara.bio
**Website:** axara.bio

---

## About AXARA BioScience

AXARA BioScience builds validated computational datasets for covalent
drug discovery. The AXARA Dataset Engine v3.0 has been validated across
three target families: KRAS G12C, EGFR C797, and BTK C481.
A methods preprint describing the full validation panel is in preparation.

---

*© 2025 AXARA BioScience. All rights reserved.*
*This whitepaper may be shared freely for non-commercial purposes.*
*Scored residue data, probe scaffolds, kinome selectivity results,*
*resistance variant classifications, and assay protocols are proprietary*
*commercial deliverables available under licence.*
*Contact axara@axara.bio for licensing information.*
