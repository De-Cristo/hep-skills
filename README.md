# HEP Skills: Rigorous Scientific Review & De-AI-ification for High-Energy Physics

[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Skills](https://img.shields.io/badge/Skills-hep--text--review-success.svg)](skills/hep-text-review/SKILL.md)
[![Compatibility](https://img.shields.io/badge/Agents-Antigravity%20%7C%20Claude%20Code%20%7C%20Codex%20%7C%20OpenCode-blueviolet)](#installation)

**`hep-skills`** provides production-grade, reproducible Agent Skills designed specifically for **High-Energy Physics (HEP)** researchers working within large collaborations (CMS, ATLAS, LHCb, ALICE).

It equips AI coding assistants (Antigravity, Claude Code, OpenAI Codex, OpenCode, Cursor) with formal protocols for **item-by-item truth verification**, **citation graph integrity**, and **Nature/PRL/CMS-grade scientific language polishing** that systematically removes "AI-style" writing artifacts while strictly preserving physics accuracy.

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
 • 4-Tier Authority Hierarchy         • 5-Role Citation Taxonomy            • 4 Editorial Flavors (A–D)
 • Claim-to-Artifact Provenance       • Ghost & Orphan Citation Audit       • Terminology Ledger
 • Partition & Invariant Audits       • Collaboration & CDS Metadata        • 10–30 Word Sentence Budget
 • Boundary Precision (<= vs <)       • Clause-Level Binding Precision      • Shortest Sufficient Evidence
```

### 1. Pillar 1: Proof-Carrying Ground Truth Protocol
- **4-Tier Authority Hierarchy:** Runtime executable code (`.py`, `.yaml`, processors, ROOT/Parquet outputs) is Tier 1 authority. Comments and informal notes are never treated as configuration.
- **Claim-to-Artifact Provenance ($\le 3$ Steps):** Every number, migration fraction, bin count, or selection cut cited in text must trace directly to a reproducible code line or output artifact; otherwise, it is explicitly flagged as `[UNVERIFIED: Missing artifact/code reference]`.
- **Mathematical Invariants:** Enforces exact count conservation ($N_P' + N_F' \equiv N_P + N_F$) and mutually exclusive, collectively exhaustive phase-space partitioning.

### 2. Pillar 2: Citation Graph & Provenance Protocol
- **5-Role Citation Taxonomy:** Disallows generic citing; enforces explicit roles:
  - **Role A:** Formal Definitions (STXS Stage 1.2, anti-$k_t$, PUPPI).
  - **Role B:** Benchmark Precedents (Run 2 calibration notes, legacy combinations).
  - **Role C:** Theoretical Benchmarks (Yellow Reports, NNLO+NNLL calculations).
  - **Role D:** Object & Tagger Performance (ParticleNet, ParT, Muon POG).
  - **Role E:** Simulation & Statistical Frameworks (MadGraph5, Pythia 8, Combine).
- **Ghost & Orphan Audits:** Verifies that cited papers actually contain the claimed measurement, strips unused `.bib` entries, and checks CERN CDS metadata standards.

### 3. Pillar 3: Language De-AI-ification & High-Impact Scientific Prose
Transforms bloated, robotic AI drafts into publication-standard text through 4 complementary editorial flavors:
- **Flavor A (*Nature / Nature Physics*):** Active voice default (*"The fit extracts..."* vs *"An extraction is achieved by the fit"*); topic-assertion paragraph openings; dynamic sentence length cadence.
- **Flavor B (*Physical Review Letters*):** Zero throat-clearing (*"It is important to note..."* $\to$ cut); direct metric binding (claims must be immediately paired with numbers).
- **Flavor C (*CMS / CERN Notes*):** Positive definitions (state what a cut *is*, not a catalog of what it is not); clean mathematical invariants.
- **Flavor D (AI Tonal Disinfectant):** De-nominalization (turn smothered nouns back into action verbs); purge AI clichés (*"crucial"*, *"notably"*, *"delve"*); purge CS/AI jargon (*"oracle"*, *"monitored as a guard"*, *"silently redefine"*).

---

## 📦 Installation

### Option 1: Claude Code

Clone the repository and install the skill into Claude Code:

```bash
# Clone to your local workspace or tools directory
git clone https://github.com/De-Cristo/hep-skills.git ~/hep-skills

# Option A: Copy directly to Claude skills directory
mkdir -p ~/.claude/skills
cp -r ~/hep-skills/skills/hep-text-review ~/.claude/skills/

# Option B: Create a subagent wrapper
mkdir -p ~/.claude/agents
cat > ~/.claude/agents/hep-reviewer.md << 'EOF'
---
name: hep-reviewer
description: Rigorous HEP text review, fact-checking, citation audit, and Nature/PRL-style polishing.
---
When invoked, read `~/hep-skills/skills/hep-text-review/SKILL.md` and follow its 3-pillar protocol strictly.
EOF
```

---

### Option 2: Google Antigravity (AGY) / Gemini CLI

For global availability across all workspaces:

```bash
mkdir -p ~/.agents/skills
cp -r ~/hep-skills/skills/hep-text-review ~/.agents/skills/
```

For project-level availability (committed with your analysis repository):

```bash
cd your-analysis-repo/
mkdir -p .agents/skills
cp -r ~/hep-skills/skills/hep-text-review .agents/skills/
git add .agents/skills/hep-text-review
git commit -m "chore: add hep-text-review agent skill"
```

---

### Option 3: OpenAI Codex / OpenCode / Hermes

```bash
# Install to Codex global skills
mkdir -p ~/.codex/skills
cp -r ~/hep-skills/skills/hep-text-review ~/.codex/skills/
```

---

## 🚀 Usage & Prompt Examples

Once installed, invoke the skill directly in your AI assistant:

### Reviewing an Analysis Note Section:
```text
Review sections/06_mutag_hbb_calibration.tex using the hep-text-review skill:
1. Verify every cut, bin boundary, and formula against the code in mutag-calib/
2. Audit all citations in AN-26-078.bib
3. De-AI-ify the language using Flavor A (Nature active voice) and Flavor B (PRL compactness)
```

### Fact-Checking & Proof-Carrying Audit:
```text
Apply the hep-text-review ground truth protocol on sections/05_stxs_poi_reco_binning.tex:
- Audit all category migration numbers against our validation Parquet dumps.
- Flag any claim that cannot be traced to an artifact within 3 steps.
```

### LaTeX Polishing & De-Nominalization:
```text
Polish this draft section according to hep-text-review:
- Remove passive nominalizations and software-style defensive hedging.
- Enforce the 10-30 word sentence budget.
- Ensure proper mathematical macro formatting (\SF, \qqWH, \ptv).
```

---

## 📚 Anti-Pattern Quick Reference

| AI Anti-Pattern | Problem | Refined HEP / Nature / CMS Style |
| :--- | :--- | :--- |
| *"Background processes are absent, so the matrices do not measure bin purity or the final expected sensitivity."* | Defensive hedging / stating the obvious. | *"Response matrices are evaluated from nominal signal yields passing preselection. Background processes are not included at this stage."* |
| *"In the shared 250–400 GeV interval, the boundary is not implemented as a simple overwrite. This boosted-priority arbitration prevents double assignment..."* | Conversational software meta-commentary. | *"In the overlapping 250–400 GeV interval, events passing boosted signal-region requirements are assigned to the boosted categories, while remaining events enter the resolved categories."* |
| *"...using samples in which HTXS_njets30 is available as an oracle."* | Inappropriate CS / ML jargon. | *"...using samples where HTXS_njets30 is available as a benchmark reference."* |
| *"This decomposition exists because a consuming analysis spanning several bins must not treat the correlated part as uncorrelated, which would understate it by up to the square root of the number of bins."* | Pedagogical lecturing of the reader. | *"The total uncertainty is decomposed into statistical (uncorrelated across bins), profiled systematic (correlated), and proxy-transfer (correlated) components."* |
| *"Replacing an invalid ratio with unity or any other default weight is prohibited everywhere in the chain, and every merge is recorded."* | Internal runbook policy / defensive logging. | *"Low-occupancy cells with fewer than 20 effective entries are merged with neighbouring cells within the same pT interval."* |

---

## 📄 License

Licensed under the [Apache License, Version 2.0](LICENSE).
