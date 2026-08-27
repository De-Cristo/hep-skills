---
name: hep-text-review
description: >-
  Comprehensive methodology and principles for reviewing, fact-checking, and polishing high-energy physics documentation, Analysis Notes (AN), PAS, papers, and technical writeups. Use whenever reviewing or editing physics text to ensure item-by-item ground truth verification against project code/artifacts, citation integrity, and removal of AI-style language through Nature-style active narrative, PRL-style compactness, and CMS operational precision while strictly preserving physics meaning.
allowed-tools: Read Write Edit Bash
---

# High-Energy Physics Text Review and De-AI-ification Skill

This skill provides a comprehensive, publication-grade protocol for reviewing, fact-checking, and refining scientific text in High-Energy Physics (HEP) collaborations (CMS, ATLAS, etc.). It combines experimental verification rigor with the **Nature / Nature Physics narrative philosophy**, **Physical Review Letters (PRL) compactness standards**, and systematic **AI de-identification mechanisms** (inspired by `nature-skills`).

---

## 1. The Three Core Review Pillars

```
┌─────────────────────────────────────────────────────────────────────────────────────────────────┐
│                                The Three Review Pillars                                         │
└───────────────────────────────────────────────┬─────────────────────────────────────────────────┘
                                                │
       ┌────────────────────────────────────────┼────────────────────────────────────────┐
       ▼                                        ▼                                        ▼
【Pillar 1: Ground Truth Protocol】  【Pillar 2: Citation Graph Protocol】  【Pillar 3: De-AI & Nature Polish】
 • 4-Tier Authority Hierarchy         • 5-Role Citation Taxonomy            • 4 Editorial Flavors (A–D)
 • Claim-to-Artifact Provenance       • Ghost & Orphan Citation Audit       • Terminology Ledger
 • Partition & Invariant Audits       • Collaboration & CDS Metadata        • 10–30 Word Sentence Budget
 • Boundary Precision (<= vs <)       • Clause-Level Binding Precision      • Shortest Sufficient Evidence
```

---

## 2. Pillar 1: The Proof-Carrying Ground Truth Protocol

### 1.1 Four-Tier Authority Hierarchy
When resolving conflicts or verifying statements in text, adhere strictly to this precedence hierarchy:
1. **Tier 1 — Executable Runtime Authority (Highest):**
   - Executable Python configuration (`.py`, `.yaml`, `.json`), column derivations in NanoAOD processors (`processor.py`, `accumulator.py`), and frozen output artifacts (Parquet tables, Combine datacards, ROOT histograms).
2. **Tier 2 — Observational Validation Evidence:**
   - Produced validation CSVs, truth-cleaning scan outputs, response matrix dumps, closure test logs.
3. **Tier 3 — Informal Documentation (Non-Authoritative):**
   - Inline code comments, runbooks, READMEs, commit messages. (Comments are documentation, never configuration).
4. **Tier 4 — Historical Precedents:**
   - Run 2 ANs, legacy PASs, old talks. (Valuable for context, but cannot override Run 3 conditions or NanoAODv12/v15 schemas).

### 1.2 The Claim-to-Artifact Provenance Audit
Every numerical value, migration fraction, binning definition, and efficiency figure in the text must have a direct, verifiable provenance trace:
- **Trace Rule:** If a number cited in text (e.g. *"+1.90% agreement"*, *"30 reco categories"*, *"32 bins over $[-1.2, 5.2]$"*) cannot be traced to a specific code expression, config file, or validation table in $\le 3$ lookup steps, it must be flagged explicitly as:
  $$\texttt{[UNVERIFIED: Missing artifact/code reference]}$$
- **Zero Hallucination Tolerance:** Never invent numbers, interpolate undocumented scan points, or guess parameter values.

### 1.3 Mathematical Invariants & Partition Completeness Audit
- **Yield / Probability Conservation:** Check that all scaling and reweighting formulations mathematically conserve total counts across categories:
  $$N_P' + N_F' \equiv N_P + N_F \quad \forall \SF$$
  $$w_{\mathrm{tagged}}\,\varepsilon + w_{\mathrm{untagged}}\,(1 - \varepsilon) \equiv 1$$
- **Partition Completeness:** Verify that reconstructed categories and POI bins form a mutually exclusive, collectively exhaustive partition of the target phase space with zero unaccounted gaps or double counts.

### 1.4 Kinematic Boundary & Syntax Precision Check
- **Relational Operator Rigor:** Verify exact boundary definitions: inclusive ($\le, \ge$) versus strict exclusive ($<, >$).
- **Variable Distinction:** Confirm that raw variables (e.g., raw soft-drop mass $\msd > 40\GeV$) are never confused with corrected variables (e.g., corrected $\msd \in [100, 150]\GeV$).

---

## 3. Pillar 2: The Citation Graph & Provenance Protocol

### 2.1 Five-Role Citation Taxonomy
Every citation in an HEP manuscript must serve one of five explicit roles. Never cite generic papers when a primary definition exists:
- **Role A — Authoritative Formal Definitions:** Primary definitions of physics frameworks (e.g., STXS Stage 1.2 in `\cite{LHCHWG:STXSStage1p2}`, anti-$k_t$ jet algorithm in `\cite{Cacciari:2008gp}`).
- **Role B — Benchmark Physics Precedents:** Prior experimental baselines and legacy Run 2 methodology (e.g., BTV $\mu$-tag calibration in `\cite{CMS:AN-2021-005}`, Run 2 VH combination in `\cite{CMS:2023vzh}`).
- **Role C — Theoretical Predictions & Uncertainties:** Cross section benchmarks, NNLO+NNLL calculations, and benchmark scale schemes (e.g., `\cite{Stewart:2011cf}`).
- **Role D — Experimental Object & Algorithm Performance:** Object identification, reconstruction papers, and tagger performance (PNet, ParT, Muon POG).
- **Role E — Software & Statistical Frameworks:** Simulation generators (\MADGRAPH, \PYTHIA), ROOT, Combine tool.

### 2.2 Ghost, Orphan, and Misplaced Citation Audits
- **Ghost Citations:** Statements citing a paper that does *not* actually contain the claimed measurement or method. Audit the target paper's abstract/conclusions to confirm it supports the specific claim.
- **Orphan Citations in `.bib`:** Audit `.bib` files and remove unused entries to prevent bibliographic bloat.
- **Missing Milestone Citations:** Ensure core frameworks (Combine, STXS, FastJet) are properly cited rather than treated as implicit jargon.

### 2.3 Collaboration & CDS Metadata Integrity
- **CMS Analysis Notes (AN):** Must use `author = {{CMS Collaboration}}`, `institution = {CERN}`, `type = {CMS Analysis Note}`, `number = {CMS AN-YYYY/NNN}`.
- **CMS Physics Analysis Summaries (PAS):** Must use `number = {CMS-PAS-HIG-YY-NNN}`.
- **Journal Papers:** Must include DOI, journal volume, page/article number, and arXiv ID.

### 2.4 Clause-Level Placement Precision
- Citations must be attached to the exact clause or noun phrase they qualify, never dumped at the end of a paragraph.

---

## 4. Pillar 3: Language De-AI-ification & Nature/PRL Polish

```
   ┌─────────────────────────────────────────────────────────────┐
   │                    Pillar 3 Editorial Flavors               │
   └──────────────────────────────┬──────────────────────────────┘
                                  │
    ┌─────────────────────────────┼─────────────────────────────┐
    ▼                             ▼                             ▼
【Flavor A: Nature Style】   【Flavor B: PRL Style】   【Flavor C: CMS AN Style】
• Active voice & agency       • Zero throat-clearing    • Positive definitions
• Topic-assertion openings    • Direct metric binding   • Clean math invariants
• Variable sentence cadence   • Maximum density         • Explicit phase space
                                  │
                                  ▼
                    【Flavor D: AI Disinfectant】
                    • Anti-nominalization (un-smother verbs)
                    • Eliminate CS/AI metaphors & buzzwords
                    • Strip defensive hedging & apologies
```

### 4.1 Editorial Flavors
- **Flavor A (*Nature / Nature Physics*):** Active voice default (*"The fit extracts..."* vs *"An extraction is achieved by the fit"*); topic-assertion openings; dynamic sentence length cadence (10–15 word punchy sentences + 20–25 word compound explanatory sentences).
- **Flavor B (*PRL / Letters*):** Zero throat-clearing (*"It is important to note..."* $\to$ cut); direct metric binding (every claim directly paired with its numerical metric).
- **Flavor C (*CMS / CERN Notes*):** Positive definitions (state what a cut *is*, not a catalog of what it is not); concise mathematical invariants.
- **Flavor D (AI Tonal Disinfectant):** De-nominalization (turn smothered nouns back into action verbs: *"execution of an optimization"* $\to$ *"optimized"*); purge AI clichés (*"crucial"*, *"notably"*, *"delve"*, *"serves as a testament to"*); purge CS jargon (*"oracle"*, *"monitored as a guard"*, *"silently redefine"*).

---

## 5. Structural & Sentence-Level Mechanisms (from *Nature Skills*)

### Mechanism 1: The Terminology Ledger (One Concept, One Name)
- **Rule:** A manuscript must use exactly one name for one thing. Do not introduce arbitrary synonyms just to vary the prose (e.g., swapping between *"reconstructed category"*, *"analysis bin"*, *"selection box"*, and *"event slice"*).
- Maintain rigorous consistency for observable names, particle macros, tagger thresholds, and dataset labels across all sections, tables, and figures.

### Mechanism 2: The 10–30 Word Sentence Budget & Proposition Audit
- **Length Budget:** Target sentences in the **10–30 word range**.
- **Proposition Limit:** If a sentence exceeds 20 words, check whether it contains more than one main physical proposition. Split overloaded sentences rather than applying cosmetic punctuation fixes.
- **Audit Paragraph Conclusions:** The final sentence of an AI-written paragraph is frequently the longest and weakest (often devolving into generic summary or hedging). Explicitly audit and tighten paragraph endings.

### Mechanism 3: Shortest Sufficient Evidence Chain (Main Text vs Appendix Allocation)
- **Main Text:** Carries the core physical argument, key selections, primary response matrices, and finalized scale factor/uncertainty summaries.
- **Appendix:** Receives complete diagnostic scans, secondary validation slices, acceptance breakdowns, and extended parameter tables.
- **Zero Double-Reporting:** Do not duplicate full numerical catalogs across both main text body and figure captions.

### Mechanism 4: Strict Order of Operations in Editing
Always resolve editing issues in this hierarchy:
$$\text{Section Purpose} \longrightarrow \text{Paragraph Logic} \longrightarrow \text{Evidence Placement} \longrightarrow \text{Sentence De-AI Polish}$$
Never polish sentence phrasing while leaving the underlying physical argument or evidence chain broken.

---

## 6. Anti-Pattern & Refinement Guide

| AI Anti-Pattern | Why It Is Problematic | Refined HEP / Nature / CMS Style |
| :--- | :--- | :--- |
| *"Background processes are absent, so the matrices do not measure bin purity or the final expected sensitivity."* | Defensive hedging / stating what is obvious from the context. | *"Response matrices are evaluated from nominal signal yields passing preselection. Background processes are not included at this stage."* |
| *"In the shared 250–400 GeV interval, the boundary is not implemented as a simple overwrite. This boosted-priority arbitration prevents double assignment..."* | Conversational software meta-commentary. | *"In the overlapping 250–400 GeV interval, events passing boosted signal-region requirements are assigned to the boosted categories, while remaining events enter the resolved categories."* |
| *"...using samples in which HTXS_njets30 is available as an oracle."* | Inappropriate CS / ML jargon. | *"...using samples where HTXS_njets30 is available as a benchmark reference."* |
| *"This decomposition exists because a consuming analysis spanning several bins must not treat the correlated part as uncorrelated, which would understate it by up to the square root of the number of bins."* | Pedagogical lecturing of the reader. | *"The total uncertainty is decomposed into statistical (uncorrelated across bins), profiled systematic (correlated), and proxy-transfer (correlated) components."* |
| *"Replacing an invalid ratio with unity or any other default weight is prohibited everywhere in the chain, and every merge is recorded."* | Internal runbook policy / defensive logging statement. | *"Low-occupancy cells with fewer than 20 effective entries are merged with neighbouring cells within the same pT interval."* |
| *"The execution of an optimization on the veto radius was carried out to achieve a minimization of migrations."* | Heavy nominalization / passive bloat. | *"We optimized the veto radius to minimize category migrations."* |

---

## 7. Mathematical & Formatting Standards in LaTeX

- **Scale Factors:** Write $\mathrm{SF}(\pt)$ or $\text{SF}(\pt)$ using `\mathrm{SF}` or `\SF`, never bare $SF(\pt)$ which renders as $S \times F$.
- **Processes and Particles:** Use standard particle and process macros (e.g., `\qqWH`, `\qqZH`, `\ggZH`, `\bbbar`, `\pt(V)`, `\msd`, `\tautwoone`).
- **Units and Spacings:** Always use proper units formatting (e.g., `\GeV`, `\TeV`, `\pt > 250\GeV`).
- **Equations:** Ensure yield conservation equations and reweighting formulations are mathematically unambiguous.

---

## 8. Verification Workflow for Review Tasks

When reviewing or editing analysis documents:
1. **Source Inspection:** Read source `.tex` and `.bib` files end-to-end.
2. **Pillar 1 Execution:** Audit claims against the 4-Tier Authority Hierarchy and trace numbers to code/artifacts. Flag unreferenced items.
3. **Pillar 2 Execution:** Audit citations against the 5-Role Taxonomy; verify `.bib` metadata and clause-level placement.
4. **Pillar 3 Application:** Refactor text applying Flavors A–D and Mechanisms 1–4 (Active voice, high information density, terminology ledger, sentence proposition audit).
5. **LaTeX Build Validation:** Execute `tdr` or `latexmk` to ensure zero compilation errors and warnings.
