# HEP Skills: Rigorous Scientific Review & De-AI-ification for High-Energy Physics

[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Skills](https://img.shields.io/badge/Skills-hep--text--review%20%7C%20hep--presentation--craft%20%7C%20hep--web--report-success.svg)](skills/)
[![Standard](https://img.shields.io/badge/Standard-ASD--STE100-orange.svg)](#asd-ste100-standard)
[![Compatibility](https://img.shields.io/badge/Agents-Antigravity%20%7C%20Claude%20Code%20%7C%20Codex%20%7C%20OpenCode-blueviolet)](#installation)

**`hep-skills`** provides production-grade, reproducible Agent Skills designed specifically for **High-Energy Physics (HEP)** researchers working within large international collaborations (CMS, ATLAS, LHCb, ALICE).

It equips AI coding assistants (Antigravity, Claude Code, OpenAI Codex, OpenCode, Cursor) with formal protocols for **item-by-item truth verification**, **citation graph integrity**, **ASD-STE100 (Simplified Technical English) cognitive clarity**, and **Nature/PRL/CMS-grade scientific language polishing**.

---

## 🧩 The Three-Skill Suite

| Skill | Primary Focus & Formats | Language & Cognitive Standard | Key Features |
| :--- | :--- | :--- | :--- |
| **[`hep-text-review`](skills/hep-text-review/SKILL.md)** | LaTeX, Papers, AN, PAS, TDRs, JINST, NIMA | Nature / PRL / CMS Operational Precision | 4-Tier Authority, 9-Role Citations, Dual-Track (Physics vs. Hardware). |
| **[`hep-presentation-craft`](skills/hep-presentation-craft/SKILL.md)** | Markdown & HTML Slides (Marp, HTML decks) | **ASD-STE100** Controlled English | Assertion-Evidence Titles, $\le 20$ Words/Bullet, 60–70% Visual Area. |
| **[`hep-web-report`](skills/hep-web-report/SKILL.md)** | Markdown & Standalone Portable HTML | **ASD-STE100** Controlled English | "Start Here" in 60s, Lego Functional Clusters, Self-Contained HTML. |

---

## 🎯 The Three Review Pillars

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

### 1. Pillar 1: Proof-Carrying Ground Truth Protocol
- **4-Tier Authority Hierarchy:**
  - *Analysis Track:* Executable Python config (`.py`, `.yaml`), column derivations in processors (`processor.py`), and frozen output artifacts (Parquet tables, Combine datacards, ROOT histograms) are Tier 1 authority.
  - *Detector Track:* CAD drawings, mechanical envelopes, ASIC specifications, radiation qualification databases ($1\,\mathrm{MeV}\,\mathrm{n_{eq}/cm^2}$, $\mathrm{Mrad}$), and test-beam run logs are Tier 1/2 authority.
- **Claim-to-Artifact Provenance ($\le 3$ Steps):** Every number, migration fraction, channel count, geometric dimension, or selection cut cited in text must trace directly to a reproducible code line or output artifact; otherwise, it is explicitly flagged as `[UNVERIFIED: Missing artifact/code reference]`.
- **Mathematical & Hardware Invariants:** Enforces count conservation ($N_P' + N_F' \equiv N_P + N_F$), channel tree multiplication ($\text{Channels} \equiv N_{\mathrm{bars}} \times 2$), radiation breakdown boundaries ($E < 11.5\,\mathrm{V/\mu m}$), and single-hit vs per-track timing decompositions.

### 2. Pillar 2: Citation Graph & Provenance Protocol
- **9-Role Citation Taxonomy:** Disallows generic citing; enforces explicit roles:
  - **Role A:** Formal Physics Definitions (STXS Stage 1.2, anti-$k_t$, PUPPI).
  - **Role B:** Benchmark Physics Precedents (Run 2 calibration notes, legacy combinations).
  - **Role C:** Theoretical Benchmarks (Yellow Reports, NNLO+NNLL calculations).
  - **Role D:** Object & Tagger Performance (ParticleNet, ParT, Muon POG).
  - **Role E:** Simulation & Statistical Frameworks (MadGraph5, Pythia 8, Combine).
  - **Role F:** Technical Design Reports (TDRs) & Engineering Design Reviews (EDRs).
  - **Role G:** Front-End Readout ASICs & Mixed-Signal ICs (TOFHIR2, ETROC2, lpGBT, RD53).
  - **Role H:** Sensor & Scintillator Technology R&D (RD50, RD51, LYSO:Ce kinetics).
  - **Role I:** Test-Beam Facilities & Campaigns (CERN SPS North Area, DESY II, FNAL FTBF).
- **Ghost & Orphan Audits:** Verifies that cited papers actually contain the claimed measurement, strips unused `.bib` entries, and checks CERN CDS metadata standards.

### 3. Pillar 3: Language De-AI-ification & High-Impact Scientific Prose
Transforms bloated, robotic AI drafts into publication-standard text through 5 complementary editorial flavors:
- **Flavor A (*Nature / Nature Physics*):** Active voice default (*"The fit extracts..."* vs *"An extraction is achieved by the fit"*); topic-assertion paragraph openings; dynamic sentence length cadence.
- **Flavor B (*Physical Review Letters*):** Zero throat-clearing (*"It is important to note..."* $\to$ cut); direct metric binding (claims must be immediately paired with numbers).
- **Flavor C (*CMS / CERN Notes*):** Positive definitions (state what a cut *is*, not a catalog of what it is not); clean mathematical invariants.
- **Flavor D (AI Tonal Disinfectant):** De-nominalization (turn smothered nouns back into action verbs); purge AI clichés (*"crucial"*, *"notably"*, *"delve"*); purge CS/AI jargon (*"oracle"*, *"monitored as a guard"*).
- **Flavor E (Instrumentation Precision):** Quantitative operational descriptions ($V_{\mathrm{ov}}$, DCR, ToT, DLED, TEC cooling) and precise hardware state naming.

---

## 📦 Installation

### Option 1: Claude Code

Clone the repository and install the skill into Claude Code:

```bash
# Clone to your local workspace or tools directory
git clone https://github.com/De-Cristo/hep-skills.git ~/hep-skills

# Option A: Copy all skills directly to Claude skills directory
mkdir -p ~/.claude/skills
cp -r ~/hep-skills/skills/* ~/.claude/skills/
```

---

### Option 2: Google Antigravity (AGY) / Gemini CLI

For global availability across all workspaces:

```bash
mkdir -p ~/.agents/skills
cp -r ~/hep-skills/skills/* ~/.agents/skills/
```

For project-level availability (committed with your analysis or detector repository):

```bash
cd your-project-repo/
mkdir -p .agents/skills
cp -r ~/hep-skills/skills/* .agents/skills/
git add .agents/skills/
git commit -m "chore: add hep-skills suite (text review, presentation craft, web report)"
```

---

### Option 3: OpenAI Codex / OpenCode / Hermes

```bash
# Install to Codex global skills
mkdir -p ~/.codex/skills
cp -r ~/hep-skills/skills/* ~/.codex/skills/
```

---

## 🚀 Usage & Prompt Examples

Once installed, invoke the desired skill directly in your AI assistant:

### 1. Reviewing an Analysis Note or Paper (`hep-text-review`):
```text
Review sections/06_mutag_hbb_calibration.tex using the hep-text-review skill:
1. Verify every cut, bin boundary, and formula against the code in mutag-calib/
2. Audit all citations in AN-26-078.bib against the 9-role taxonomy
3. De-AI-ify the language using Flavor A (Nature active voice) and Flavor B (PRL compactness)
```

### 2. Crafting Markdown / HTML Slides (`hep-presentation-craft`):
```text
Help me draft slides for tomorrow's CMS BTL Working Group meeting using hep-presentation-craft:
1. Format as Marp markdown using the Assertion-Evidence model.
2. Enforce ASD-STE100 rules (max 20 words per bullet, active voice, no noun stacking).
3. Structure: 6 slides covering our lpGBT phase lock fix, two-RU synchronization, and next beam test goals.
```

### 3. Authoring an Interactive Research Report (`hep-web-report`):
```text
Convert our DAQ multi-RU research notes into a standalone HTML report using hep-web-report:
1. Add a "Start Here" 60-second mental model with a physical-to-electronic architecture diagram.
2. Group the 13 hardware operations into 4 Lego functional clusters.
3. Apply ASD-STE100 language rules with a plain-language meaning column for register tables.
4. Compile into a self-contained HTML file ready for /eos/user/l/lichengz/www/ deployment.
```

---

## 📚 Anti-Pattern Quick Reference

| AI Anti-Pattern | Problem | Refined HEP / Nature / CMS Style |
| :--- | :--- | :--- |
| *"Background processes are absent, so the matrices do not measure bin purity or the final expected sensitivity."* | Defensive hedging / stating the obvious. | *"Response matrices are evaluated from nominal signal yields passing preselection. Background processes are not included at this stage."* |
| *"The cutting-edge sensor design achieves unmatched precision under harsh conditions."* | Vague marketing hype; lacks physical metrics. | *"The $50\,\mu\mathrm{m}$ LGAD maintains a single-hit resolution of $30\text{--}40\,\mathrm{ps}$ over a $70\,\mathrm{V}$ operating window at $1.6\times 10^{15}\,\mathrm{n_{eq}/cm^2}$."* |
| *"In the shared 250–400 GeV interval, the boundary is not implemented as a simple overwrite. This boosted-priority arbitration prevents double assignment..."* | Conversational software meta-commentary. | *"In the overlapping 250–400 GeV interval, events passing boosted signal-region requirements are assigned to the boosted categories, while remaining events enter the resolved categories."* |
| *"It is essential to consider the thermal budget to avoid catastrophic failure."* | Defensive, conversational hedging. | *"Evaporative $\mathrm{CO_2}$ cooling at $-35\,^\circ\mathrm{C}$ combined with integrated TECs maintains SiPM temperatures below $-40\,^\circ\mathrm{C}$ to suppress dark count rates."* |
| *"...using samples in which HTXS_njets30 is available as an oracle."* | Inappropriate CS / ML jargon. | *"...using samples where HTXS_njets30 is available as a benchmark reference."* |
| *"The execution of an optimization on the veto radius was carried out to achieve a minimization of migrations."* | Heavy nominalization / passive bloat. | *"We optimized the veto radius to minimize category migrations."* |

---

## 📄 License

Apache-2.0 License. See [LICENSE](LICENSE) for details.
