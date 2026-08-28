---
name: hep-text-review
description: >-
  Comprehensive publication-grade methodology and principles for reviewing, fact-checking, and polishing high-energy physics documentation, Analysis Notes (AN), PAS, physics papers, and detector/instrumentation writeups (TDRs, JINST, NIMA, IEEE, PoS). Ensures item-by-item ground truth verification against project code, CAD/hardware specs, and test-beam artifacts, citation graph integrity, and removal of AI-style language through Nature-style active narrative, PRL-style compactness, and CMS operational precision.
allowed-tools: Read Write Edit Bash
---

# High-Energy Physics Text Review and De-AI-ification Skill

This skill provides a publication-grade protocol for reviewing, fact-checking, and refining scientific text in High-Energy Physics (HEP) collaborations (CMS, ATLAS, LHCb, ALICE). It supports two specialized review tracks:
- **Track 1: Physics Analysis Papers & Notes (AN, PAS, Physics Letters)**
- **Track 2: Detector Instrumentation, Hardware & Upgrade Papers (TDR, JINST, NIMA, IEEE NSS/MIC, PoS)**

It combines experimental verification rigor with the **Nature / Nature Physics narrative philosophy**, **Physical Review Letters (PRL) compactness standards**, and systematic **AI de-identification mechanisms** (inspired by `nature-skills`).

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
 • 4-Tier Authority Hierarchy         • 9-Role Citation Taxonomy            • 5 Editorial Flavors (A–E)
 • Claim-to-Artifact Provenance       • Ghost & Orphan Citation Audit       • Dual-Track Terminology Ledger
 • Channel & Yield Invariant Audits   • Collaboration & CDS Metadata        • 10–30 Word Sentence Budget
 • Radiation & SEB Boundary Checks    • Clause-Level Binding Precision      • Shortest Sufficient Evidence
```

---

## 2. Pillar 1: The Proof-Carrying Ground Truth Protocol

### 1.1 Four-Tier Authority Hierarchy
When resolving conflicts or verifying statements in text, adhere strictly to this precedence hierarchy based on the manuscript track:

#### Track 1: Physics Analysis Documents
1. **Tier 1 — Executable Runtime Authority (Highest):**
   - Executable Python configuration (`.py`, `.yaml`, `.json`), column derivations in NanoAOD processors (`processor.py`, `accumulator.py`), and frozen output artifacts (Parquet tables, Combine datacards, ROOT histograms).
2. **Tier 2 — Observational Validation Evidence:**
   - Validation CSVs, truth-cleaning scan outputs, response matrix dumps, closure test logs.
3. **Tier 3 — Informal Documentation (Non-Authoritative):**
   - Inline code comments, runbooks, READMEs, commit messages.
4. **Tier 4 — Historical Precedents:**
   - Run 2 ANs, legacy PASs, old talks.

#### Track 2: Detector & Instrumentation Documents
1. **Tier 1 — Engineering Specifications & Frozen TDRs (Highest):**
   - Mechanical CAD envelopes (radial clearance, stay-clear boundaries, services envelopes).
   - ASIC register specifications, bit depths, and pinouts (TDC binning, ToT dynamic range, clock distribution trees).
   - Radiation qualification databases (NIEL $1\,\mathrm{MeV}\,\mathrm{n_{eq}/cm^2}$, TID in $\mathrm{Mrad}/\mathrm{kGy}$).
2. **Tier 2 — Experimental Test-Beam & QA/QC Campaign Logs:**
   - Test-beam scan dumps (SPS, DESY, FNAL), cosmic ray telescope logs, laser / radioactive source ($^{90}\mathrm{Sr}$) charge collection curves, and assembly QA yield matrices.
3. **Tier 3 — Pre-production Projections & Assembly Runbooks:**
   - Pre-series qualification notes, assembly procedure manuals.
4. **Tier 4 — Early Conceptual R&D:**
   - Early sensor prototypes and preliminary simulation feasibility studies.

### 1.2 The Claim-to-Artifact Provenance Audit
Every numerical value, migration fraction, channel count, geometric dimension, and efficiency figure in the text must have a direct, verifiable provenance trace:
- **Trace Rule:** If a number cited in text (e.g. *"+1.90% agreement"*, *"331,776 channels"*, *"30 ps resolution"*, *"32 bins over $[-1.2, 5.2]$"*) cannot be traced to a specific code expression, config file, CAD drawing, or validation table in $\le 3$ lookup steps, it must be flagged explicitly as:
  $$\texttt{[UNVERIFIED: Missing artifact/code reference]}$$
- **Zero Hallucination Tolerance:** Never invent numbers, interpolate undocumented scan points, or guess parameter values.

### 1.3 Mathematical Invariants & Physical Conservation Audits

#### Track 1: Yield & Probability Invariants
- **Yield / Probability Conservation:** Check that all scaling and reweighting formulations mathematically conserve total counts across categories:
  $$N_P' + N_F' \equiv N_P + N_F \quad \forall \mathrm{SF}$$
  $$w_{\mathrm{tagged}}\,\varepsilon + w_{\mathrm{untagged}}\,(1 - \varepsilon) \equiv 1$$
- **Partition Completeness:** Verify that reconstructed categories and POI bins form a mutually exclusive, collectively exhaustive partition of the target phase space.

#### Track 2: Hardware Hierarchy & Resolution Invariants
- **Channel Multiplication Tree:** Verify exact mathematical channel conservation from sub-components to full sub-detectors:
  $$N_{\mathrm{channels}} \equiv N_{\mathrm{sensors/bars}} \times N_{\mathrm{readout/unit}} \times N_{\mathrm{units}}$$
  *(e.g., $165\,888\text{ LYSO bars} \times 2\text{ SiPMs/bar} = 331\,776\text{ channels}$)*.
- **Timing Resolution Decomposition:**
  $$\sigma_t^2 \simeq \sigma_{\mathrm{sensor}}^2 + \sigma_{\mathrm{jitter}}^2 + \sigma_{\mathrm{clock}}^2 + \sigma_{\mathrm{cal}}^2$$
  Ensure electronic jitter is correctly defined: $\sigma_{\mathrm{jitter}} \approx t_{\mathrm{rise}} / (S/N) = \sigma_V / (dV/dt)$.
- **Single-Hit vs. Per-Track Resolution:** Explicitly differentiate single-hit measurement precision $\sigma_{\mathrm{hit}}$ from combined track timestamp precision $\sigma_{\mathrm{track}} = \sigma_{\mathrm{hit}} / \sqrt{N_{\mathrm{hits}}}$.

### 1.4 Kinematic & Radiation Boundary Rigor
- **Kinematic Variables:** Inclusive ($\le, \ge$) versus strict exclusive ($<, >$) boundaries; distinguish raw variables (raw $m_{\mathrm{SD}} > 40\,\mathrm{GeV}$) from corrected variables ($m_{\mathrm{SD}} \in [100, 150]\,\mathrm{GeV}$).
- **Radiation Metrics:** Strictly distinguish Non-Ionizing Energy Loss (NIEL) displacement damage ($1\,\mathrm{MeV}\,\mathrm{n_{eq}/cm^2}$) from Total Ionizing Dose (TID) ($\mathrm{Mrad}$).
- **Electrical & Defect Boundaries:**
  - Verify sensor bulk electric field remains strictly below Single-Event Burnout (SEB) breakdown limits ($E < 11.5\,\mathrm{V/\mu m}$).
  - Verify SiPM overvoltage definitions: $V_{\mathrm{ov}} \equiv V_{\mathrm{bias}} - V_{\mathrm{bd}}$.
  - Account for defect compensation: boron acceptor removal compensation via bias voltage ramps and carbon co-implantation.

---

## 3. Pillar 2: The Citation Graph & Provenance Protocol

### 2.1 Nine-Role Citation Taxonomy
Every citation in an HEP manuscript must serve an explicit role. Generic citations are prohibited when primary definitions exist:

#### Common Physics & Theory Roles
- **Role A — Authoritative Formal Definitions:** Primary definitions of physics frameworks (STXS Stage 1.2 in `\cite{LHCHWG:STXSStage1p2}`, anti-$k_t$ jet algorithm in `\cite{Cacciari:2008gp}`).
- **Role B — Benchmark Physics Precedents:** Prior experimental baselines and legacy Run 2 methodology (BTV $\mu$-tag calibration in `\cite{CMS:AN-2021-005}`, Run 2 VH combination in `\cite{CMS:2023vzh}`).
- **Role C — Theoretical Predictions & Uncertainties:** Cross section benchmarks, NNLO+NNLL calculations, and benchmark scale schemes (e.g., `\cite{Stewart:2011cf}`).
- **Role D — Experimental Object & Algorithm Performance:** Object identification, reconstruction papers, and tagger performance (PNet, ParT, Muon POG).
- **Role E — Software & Statistical Frameworks:** Simulation generators (\MADGRAPH, \PYTHIA), ROOT, Combine tool.

#### Detector & Instrumentation Roles
- **Role F — Technical Design Reports (TDR) & Design Reviews:** Primary collaboration baseline blueprints (e.g. `\cite{MTDTDR}`, `CERN-LHCC-YYYY-NNN`, `CMS-TDR-NNN`).
- **Role G — Custom Readout ASICs & Mixed-Signal ICs:** Primary publications for front-end chips (TOFHIR2 in `\cite{TOFHIR2}`, ETROC2 in `\cite{ETROC2}`, lpGBT, ALTIROC, RD53).
- **Role H — Sensor & Scintillator Technology R&D:** Primary sensor R&D and radiation-hardness benchmarks (CERN RD50, RD51, crystal scintillation studies).
- **Role I — Dedicated Test-Beam Facilities & Campaigns:** Test-beam validation papers (CERN SPS North Area in `\cite{BTLTestBeam}`, DESY II, FNAL FTBF).

### 2.2 Ghost, Orphan, and Misplaced Citation Audits
- **Ghost Citations:** Statements citing a paper that does *not* actually contain the claimed measurement or method. Audit the target paper's abstract/conclusions to confirm it supports the specific claim.
- **Orphan Citations in `.bib`:** Audit `.bib` files and remove unused entries to prevent bibliographic bloat.
- **Missing Milestone Citations:** Ensure core frameworks (Combine, STXS, FastJet, TDRs) are properly cited rather than treated as implicit jargon.

### 2.3 Collaboration & CDS Metadata Integrity
- **CMS Analysis Notes (AN):** Must use `author = {{CMS Collaboration}}`, `institution = {CERN}`, `type = {CMS Analysis Note}`, `number = {CMS AN-YYYY/NNN}`.
- **CMS Physics Analysis Summaries (PAS):** Must use `number = {CMS-PAS-HIG-YY-NNN}`.
- **Detector Performance Summaries (DP):** Must use `number = {CMS-DP-YYYY-NNN}`.
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
【Flavor A: Nature Style】   【Flavor B: PRL Style】   【Flavor C: CMS Note Style】
• Active voice & agency       • Zero throat-clearing    • Positive definitions
• Topic-assertion openings    • Direct metric binding   • Clean math invariants
• Variable sentence cadence   • Maximum density         • Explicit phase space
                                  │
          ┌───────────────────────┴───────────────────────┐
          ▼                                               ▼
【Flavor D: AI Disinfectant】              【Flavor E: Instrumentation Tone】
• Anti-nominalization                      • Engineering metric binding
• Eliminate CS/AI buzzwords                • Precise hardware state naming
• Strip defensive hedging                  • Thermal & operational clarity
```

### 4.1 Editorial Flavors
- **Flavor A (*Nature / Nature Physics*):** Active voice default (*"The fit extracts..."* vs *"An extraction is achieved by the fit"*); topic-assertion openings; dynamic sentence length cadence (10–15 word punchy sentences + 20–25 word compound explanatory sentences).
- **Flavor B (*PRL / Letters*):** Zero throat-clearing (*"It is important to note..."* $\to$ cut); direct metric binding (every claim directly paired with its numerical metric).
- **Flavor C (*CMS / CERN Notes*):** Positive definitions (state what a cut *is*, not a catalog of what it is not); concise mathematical invariants.
- **Flavor D (AI Tonal Disinfectant):** De-nominalization (turn smothered nouns back into action verbs: *"execution of an optimization"* $\to$ *"optimized"*); purge AI clichés (*"crucial"*, *"notably"*, *"delve"*, *"serves as a testament to"*); purge CS jargon (*"oracle"*, *"monitored as a guard"*, *"silently redefine"*).
- **Flavor E (Instrumentation Precision):** Quantitative operational descriptions (*"cooled to $-35\,^\circ\mathrm{C}$ via evaporative $\mathrm{CO_2}$ and integrated TECs"* vs *"proper cooling is applied"*); precise electrical terminology ($V_{\mathrm{ov}}$, DCR, ToT, DLED, TDC binning).

---

## 5. Structural & Sentence-Level Mechanisms

### Mechanism 1: Dual-Track Terminology Ledger (One Concept, One Name)
- **Rule:** A manuscript must use exactly one name for one thing. Do not introduce arbitrary synonyms just to vary the prose.
- **Physics Analysis Ledger:** Consistent naming for categories, selection regions, tagger working points, and datasets.
- **Detector Ledger:** Consistent naming for hardware modules (Sensor Module $\to$ Detector Module $\to$ Readout Unit $\to$ Tray/Disk), sensor parameters ($V_{\mathrm{bias}}$, $V_{\mathrm{bd}}$, $V_{\mathrm{ov}}$, DCR), and ASIC functional blocks (discriminator, TDC, ToT, PLL).

### Mechanism 2: The 10–30 Word Sentence Budget & Proposition Audit
- **Length Budget:** Target sentences in the **10–30 word range**.
- **Proposition Limit:** If a sentence exceeds 20 words, check whether it contains more than one main physical proposition. Split overloaded sentences rather than applying cosmetic punctuation fixes.
- **Audit Paragraph Conclusions:** The final sentence of an AI-written paragraph is frequently the longest and weakest (often devolving into generic summary or hedging). Explicitly audit and tighten paragraph endings.

### Mechanism 3: Shortest Sufficient Evidence Chain
- **Main Text:** Carries the core physical argument, key detector parameters, primary beam-test validation curves, and finalized performance summaries.
- **Appendix:** Receives complete diagnostic scans, channel maps, secondary calibration curves, and extended assembly QA tables.
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
| *"The cutting-edge sensor design achieves unmatched precision under harsh conditions."* | Vague marketing hype; lacks physical metrics. | *"The $50\,\mu\mathrm{m}$ LGAD maintains a single-hit resolution of $30\text{--}40\,\mathrm{ps}$ over a $70\,\mathrm{V}$ operating window at $1.6\times 10^{15}\,\mathrm{n_{eq}/cm^2}$."* |
| *"It is essential to consider the thermal budget to avoid catastrophic failure."* | Defensive, conversational hedging. | *"Evaporative $\mathrm{CO_2}$ cooling at $-35\,^\circ\mathrm{C}$ combined with integrated TECs maintains SiPM temperatures below $-40\,^\circ\mathrm{C}$ to suppress dark count rates."* |
| *"The ASIC seamlessly processes data with negligible latency."* | Conversational software fluff. | *"The TOFHIR2 ASIC digitizes pulse time and charge via Time-over-Threshold at hit rates exceeding $2.5\,\mathrm{MHz/channel}$."* |
| *"A multi-stage quality control process ensures reliable detector assembly."* | Generic pedagogical textbook statement. | *"Tray qualification proceeds sequentially from sensor modules to readout units across four regional assembly centres."* |
| *"The execution of an optimization on the veto radius was carried out to achieve a minimization of migrations."* | Heavy nominalization / passive bloat. | *"We optimized the veto radius to minimize category migrations."* |

---

## 7. Mathematical & Formatting Standards in LaTeX

- **Scale Factors:** Write $\mathrm{SF}(\pt)$ or $\text{SF}(\pt)$ using `\mathrm{SF}` or `\SF`, never bare $SF(\pt)$.
- **Processes and Particles:** Use standard particle and process macros (e.g., `\qqWH`, `\qqZH`, `\ggZH`, `\bbbar`, `\pt(V)`, `\msd`, `\tautwoone`).
- **Detector Variables:** Format sensor properties consistently: $V_{\mathrm{bias}}$, $V_{\mathrm{ov}}$, $\sigma_t$, $1\,\mathrm{MeV}\,\mathrm{n_{eq}/cm^2}$, $\mathrm{CO_2}$.
- **Units and Spacings:** Always use proper units formatting (`\GeV`, `\TeV`, `30\,\mathrm{ps}`, `\pt > 250\,\mathrm{GeV}`).
- **Compiler Resilience (Proceedings & Journals):**
  - Avoid raw LaTeX `picture` drawing environments with `\oval` (which call obsolete `lcircle1` bitmap fonts); prefer native vector PDF inclusions or standard `tabular`/`fcolorbox` boxes.
  - Avoid complex math scripts or `\textsuperscript` inside `\caption{...}` blocks to prevent font size metric conflicts in `pos.sty` / `newtxmath`.

---

## 8. Verification Workflow for Review Tasks

When reviewing or editing analysis and detector documents:
1. **Source Inspection:** Read source `.tex` and `.bib` files end-to-end.
2. **Pillar 1 Execution:** Audit claims against the 4-Tier Authority Hierarchy (code/artifacts for analysis; CAD/TDR/test-beams for hardware). Flag unreferenced items as `[UNVERIFIED]`.
3. **Pillar 2 Execution:** Audit citations against the 9-Role Taxonomy; verify `.bib` metadata and clause-level placement.
4. **Pillar 3 Application:** Refactor text applying Flavors A–E and Mechanisms 1–4 (Active voice, metric binding, terminology ledger, sentence proposition audit).
5. **LaTeX Build Validation:** Execute `tdr`, `tectonic`, or `latexmk` to ensure zero compilation errors, zero missing font warnings, and adherence to page budgets.
