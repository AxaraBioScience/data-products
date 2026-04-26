# LINKEDIN PUBLISH POST
# (This is the short text that appears above the newsletter link in the feed)
# Character limit: ~3,000 but optimal engagement is 150-300 words
# ═══════════════════════════════════════════════════════════════════

We just published the AXARA p53 Y220C Covalent Tractability Map.

Four clinical programs are running on the same pocket. An NDA is filing in Q1 2027. Every lab that read the NEJM Phase 1 paper in February is now starting a p53 Y220C photoaffinity programme.

Most of them are going to make the same mistake on day one. It is not in the drug discovery literature. It is not in any published PAL protocol for this target. It took us digging through the structural biology thermodynamics literature to find it — and it explains why a large number of p53 Y220C crosslinking experiments have produced non-specific, irreproducible results.

We documented it. We scored every nucleophilic residue in the DNA-binding domain. We validated the engine against five independent co-crystal structures from three independent research groups.

Then we wrote two experiment protocols that do not exist anywhere else in the published literature — one that generates a residue-level pharmacodynamic readout for a Phase 2 drug, and one that exploits a selectivity property unique to this mutation.

The full report, scored CSV, annotated PDB, Digital Twin JSON, Validation Certificate, and Probe Reference Cards are available now.

Read the full newsletter below. The report is at axara.bio/data-products.

---

# LINKEDIN NEWSLETTER ARTICLE
# Title: We Built the p53 Y220C Probe Design Map. Here Is What We Found.
# ═══════════════════════════════════════════════════════════════════


## We Built the p53 Y220C Probe Design Map. Here Is What We Found.

*By AXARA BioScience | April 2026*

---

An NDA is filing for the first p53 Y220C drug in Q1 2027.

Rezatapopt, developed by PMV Pharmaceuticals, has just reported a 34% objective response rate across 103 patients in eight solid tumour types. The Phase 1 data landed in the New England Journal of Medicine in February. Three additional programs — Jacobio's JAB-30355, UDO Biopharma's NTS071, and Frontier Medicines' FMC-220 — are in or approaching the clinic.

TP53 Y220C accounts for approximately 125,000 new cancer cases per year. Every academic lab that read the NEJM paper is now asking the same question: where do I attach the photoaffinity linker?

We built the answer.

---

### What the p53 Y220C Neomorphic Pocket Actually Is

The Y220C mutation does something structurally unusual. It replaces a tyrosine with a cysteine at position 220, and in doing so creates a hydrophobic surface crevice of approximately 310 Å³ that does not exist in wild-type p53. The pocket is not drugging an existing feature of the protein. It is exploiting a new cavity that the mutation itself creates.

This neomorphic crevice has three subsites. The central cavity is where scaffold cores sit. Subsite 1, at the pocket opening, is defined by Phe109, Leu145, and Trp146 — halogen bond acceptors that the iodophenol series uses at 2.8–3.0 Å to Leu145. Subsite 2 is a narrow hydrophobic channel gated by Pro153. Subsite 3, the pocket floor, is where CYS220 sits.

CYS220 is the mutant residue. It does not exist in wild-type p53. Tyr220 fills the pocket in normal tissue. This is not just a structural fact — it is a selectivity property that defines what kind of probe this is.

---

### What the Engine Found

We ran every nucleophilic residue in the p53 DNA-binding domain through the AXARA Dataset Engine v3.0. Three-component scoring: fpocket binding pocket proximity, Shrake-Rupley solvent accessibility, and diazirine carbene chemistry preference. Four structural filters: zinc coordination, disulfide bonds, solvent accessibility threshold, and valid residue range.

Thirty-three residues scored. Twenty-three excluded.

The primary site ranked first with a score of 18.31 — leading the next-ranked residue by a factor of three. It ranked first in every one of the five validation structures we ran it against, from three independent research groups.

We are not going to name the site here. If you work in this field you already know what it is. The report tells you what its score means, what its solvent accessibility is, what the pocket geometry looks like around it, and how to design the probe.

What we will say is this: the validation set — five independent co-crystal structures confirming the same attachment site — is the strongest validation panel any AXARA product has shipped with. KRAS had sotorasib and adagrasib. p53 Y220C has five structures from three groups spanning three different chemical scaffolds. That is not an accident. It is a reflection of how much crystallographic effort the field has invested in this pocket.

---

### The Finding That Will Save Some Labs Months of Failed Experiments

We documented something in this report that is not in any published photoaffinity labelling protocol for p53 Y220C. It is not in the drug discovery papers. It is buried in the structural biology thermodynamics literature and requires connecting several sources to understand its experimental implications.

We are not going to reveal it here either. That would defeat the purpose of charging $4,500 for the report.

What we will say is that it concerns the physical state of the protein under standard laboratory conditions. If you have been running p53 Y220C photoaffinity experiments and getting non-specific crosslinks to what looks like the hydrophobic core of the protein — crosslinks that make no sense given where you designed your probe to bind — this finding explains exactly why that happened and what to do differently.

It is the most commercially valuable single piece of content in the report. Not because it is the most scientifically complex. Because it is the most practically urgent.

---

### Two Experiments That Do Not Exist in the Published Literature

We included two advanced experiment protocols in the report. Neither is in the published literature for this target.

**Protocol A** generates a quantitative, residue-level pharmacodynamic readout for rezatapopt. To our knowledge, no published method currently provides direct target engagement measurement for this compound at the residue level in intact protein or cell lysates. The protocol tells you exactly how to set up the experiment, what concentrations to use, what controls to run, and what to expect in the LC-MS/MS output. If you run this experiment and publish it, it will be a meaningful contribution to the p53 Y220C pharmacology literature.

**Protocol B** exploits the selectivity property we mentioned earlier — the fact that the probe attachment site is the mutant residue itself, absent in wild-type p53. This has implications that go beyond standard target engagement assays. The report specifies the experimental design and identifies the application areas, including one with significant clinical translation potential.

We designed these protocols because the most valuable thing we can do for a lab starting a p53 Y220C programme is not just tell them where the attachment site is. It is tell them what to do with the probe once they have made it.

---

### The Commercial Position

Four competing clinical programs are active on the same pocket. None of them will publish their probe design data during active clinical development. Competitive intelligence prevents it — PMV and Jacobio are not sharing their crosslinking data with each other.

AXARA is the only independent source of p53 Y220C probe site intelligence available to any of them without disclosing proprietary information to a competitor. This report can be purchased by all four simultaneously. It can also be purchased by every academic lab that read the NEJM paper and is now trying to figure out where to start.

We are not a competitor to any of these programs. We are the map they are all working without.

---

### What the Report Contains

Six deliverables:

A PDF report covering the full residue analysis, probe design recommendations, advanced experiment protocols, pocket architecture, clinical landscape, and methodology.

A scored CSV with every ranked residue, structural annotations, and evidence tiers — ready for downstream analysis.

A Digital Twin JSON file — machine-readable provenance linking every score to its structural input, engine parameters, and literature evidence. Integrates directly with FragPipe workflows, AlphaFold3 pipelines, and IND package documentation.

An annotated PDB file with tractability scores in the B-factor column. Load it in PyMOL, run one command, and the probe site ranking appears on the three-dimensional structure.

A Validation Certificate documenting the 5/5 engine pass across five independent co-crystal structures.

Probe Reference Cards — bench-ready one-page cards per probe target with synthesis guidance, UV parameters, and controls checklist.

---

### On the Science

We want to be direct about what this report is and is not.

It is not a discovery product. CYS220 as the drug target was established by the Joerger lab, the Shokat lab at UCSF, and PMV Pharmaceuticals. The three-subsite pocket architecture was characterised by Boeckler, Bauer, and Joerger. We did not discover any of that.

What we did is take that scattered body of structural knowledge, run it through a validated computational engine, filter it through structural biology expertise, and produce a bench-ready document that tells a chemical biologist exactly how to design a photoaffinity probe for this target without spending weeks doing what we spent weeks doing.

The temperature caveat is the most original contribution in the report. The zinc coordination filter — which correctly excludes four residues that a naive SASA-based screen would flag as high-priority probe sites — is a genuine technical contribution for this target. The CYS277 paired experiment design for mapping DNA contact surface accessibility before and after stabiliser treatment is publishable biology that we have not seen proposed anywhere else.

The rest is expert synthesis and delivery. We think that is worth $4,500. The four clinical programs and every academic lab starting in this field will have to make the same judgement.

---

### Pricing and Access

The p53 Y220C Covalent Tractability Map is $4,500 for all six deliverables. Institutional licensing and academic consortium pricing are available on request.

The full product listing, whitepaper, and related products — including the KRAS Mutant Panel and GLP-1 GPCR Atlas — are at:

**axara.bio/data-products**

For direct enquiries: **axara@axara.bio**

The GitHub whitepaper for this product is at:

**github.com/AxaraBioScience/data-products**

---

### What Comes Next

We are building the WRN helicase tractability map. WRN is a synthetic lethal target in microsatellite-unstable cancers, five clinical programs are active, and the cysteine pocket is validated. The engine is ready.

After that: EGFR C797 and the p53 hotspot mutant panel — R175H, R248W, R273H — as a four-mutant comparison product for labs working across the TP53 mutation landscape.

If there is a target you are working on and want to discuss whether it fits the engine criteria, contact us.

---

*AXARA BioScience provides high-purity Me-Diazirine SDA photoaffinity probes and validated covalent mapping data products for structural mass spectrometry. Every data product ships with a Digital Twin JSON and is validated against approved covalent drugs before release.*

*axara.bio | axara@axara.bio | Dataset Engine v3.0 | April 2026*

*For research use only. Not for diagnostic or therapeutic application. AXARA BioScience is not affiliated with PMV Pharmaceuticals, Jacobio Pharmaceuticals, UDO Biopharma, or Frontier Medicines.*
