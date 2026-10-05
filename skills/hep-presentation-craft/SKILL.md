---
name: hep-presentation-craft
description: >-
  Methodology and principles for drafting, reviewing, and refining High-Energy Physics (HEP) presentations and slide decks using Markdown and HTML. Enforces ASD-STE100 (Simplified Technical English) for cognitive ease, the Assertion-Evidence slide architecture, strict telegraphic bullet budgets (<=20 words), and visual-first communication for CERN/CMS working group, test-beam, and approval talks.
allowed-tools: Read Write Edit Bash
---

# HEP Presentation Craft & Simplified Technical English Skill

This skill provides a publication-grade protocol for designing, writing, and reviewing **High-Energy Physics (HEP) presentations and slide decks** using **Markdown and HTML**.

It combines the **ASD-STE100 (Simplified Technical English)** standard with the **Assertion-Evidence slide architecture**. Its goal is to make complex physics, detector hardware, and software topics **instantly understandable by the human brain** during live meetings and conferences.

---

## 1. Core Architecture: The Three Presentation Pillars

```
┌─────────────────────────────────────────────────────────────────────────────────────────────────┐
│                                 The Three Presentation Pillars                                  │
└───────────────────────────────────────────────┬─────────────────────────────────────────────────┘
                                                │
       ┌────────────────────────────────────────┼────────────────────────────────────────┐
       ▼                                        ▼                                        ▼
【Pillar 1: ASD-STE100 Controlled Language】 【Pillar 2: Assertion-Evidence Layout】 【Pillar 3: Visual & Cognitive Delivery】
 • Max 20 Words per Bullet Line       • Slide Title = Physical Conclusion   • 60-70% Visual Real Estate
 • Active Voice & Imperative Verbs    • Topic Titles Strictly Forbidden     • One Dominant Visual per Slide
 • Max 3 Consecutive Nouns            • 2–3 Telegraphic Supporting Bullets  • Brain-Friendly Mental Models
 • One Meaning per Word (No Ambiguity)• Dedicated "Bottom Line" Callout     • Formats: Marp & Pure HTML/CSS
```

---

## 2. Pillar 1: ASD-STE100 Standard for Presentations

ASD-STE100 was created for safety-critical aerospace engineering to prevent human misunderstanding. In HEP presentations, it ensures that your audience catches the physics immediately while you speak.

### A. The 6 Mandatory Language Rules

1. **Rule 1: Strict Word Budget**
   - **Instruction / Procedure**: Maximum **20 words** per bullet.
   - **Descriptive sentence**: Maximum **25 words**.
   - If a point requires 35 words, split it into two short, punchy statements.

2. **Rule 2: Maximum 3 Consecutive Nouns (Stop Noun Stacking)**
   - ❌ **Non-STE100**: *"Barrel timing layer concentrator card optical link buffer overflow error"* (8 nouns stacked).
   - ✅ **STE100**: *"Buffer overflow in the receiver on the concentrator card optical link"*.

3. **Rule 3: One Meaning per Word (Unambiguous Vocabulary)**
   - Do not use words with dual interpretations:
     - ❌ *"Since the bias voltage dropped..."* (Does "since" mean time or causality?)
     - ✅ Cause: *"Because the bias voltage dropped..."*
     - ✅ Time: *"After the bias voltage dropped..."*
   - Avoid vague modals:
     - Use **"can"** for capability or possibility.
     - Use **"must"** or **"do not"** for rules and requirements.
     - Never use *"may"* or *"might"* when specifying detector safety or limits.

4. **Rule 4: Active Voice and Imperative Commands**
   - ❌ Passive bloat: *"A phase training sequence is executed by the script before data collection is started."* (15 words)
   - ✅ Active STE100: *"The script trains the clock phase before it collects data."* (10 words)
   - ✅ Bullet command: *"Train clock phase before data acquisition."* (6 words)

5. **Rule 5: No Defensive Hedging or Conversational Filler**
   - Eliminate academic filler words that add zero physics value:
     - Delete: *"It is important to remember that..."*
     - Delete: *"As is clearly visible from the plot..."*
     - Delete: *"Needless to say, one can observe that..."*
     - Delete: *"Basically", "Essentially", "Relatively", "Quite"*.

6. **Rule 6: No Double Negatives**
   - ❌ *"It is not impossible for the channel not to lock."*
   - ✅ *"The channel can fail to lock."*

---

## 3. Pillar 2: The Assertion-Evidence Slide Architecture

In HEP collaboration meetings, attendees look at a slide for **3 to 5 seconds** before deciding whether to listen to the speaker or read their email. The traditional slide format (*Title: "TDC Scan", 8 long narrative bullets*) fails because it forces the audience to read a paper while listening.

### A. The Anatomy of an Assertion-Evidence Slide

```
┌─────────────────────────────────────────────────────────────────────────────────────────────────┐
│ [SLIDE HEADER]: Complete Physical Assertion (15–20 words, Active Verb, Finding/Conclusion)     │
├────────────────────────────────────────────────────────┬────────────────────────────────────────┤
│                                                        │                                        │
│               PRIMARY VISUAL EVIDENCE                  │      TELEGRAPHIC ASD-STE100 BULLETS    │
│                     (60–70% Area)                      │                                        │
│                                                        │ • Bold Physical Anchor: Key metric     │
│   • Efficiency vs. Voltage Curve                       │ • Short action phrase (<= 15 words)    │
│   • Waveform / Timing Residual Histogram               │ • Contrast: What was expected vs. seen │
│   • Architectural Block Diagram                        │                                        │
│                                                        │                                        │
├────────────────────────────────────────────────────────┴────────────────────────────────────────┤
│ 💡 BOTTOM LINE: One-sentence plain-English takeaway answering "Why does this matter?"          │
└─────────────────────────────────────────────────────────────────────────────────────────────────┘
```

### B. Title Comparison (Topic vs. Assertion)

| Topic Title (❌ Forbidden) | Assertion Title (✅ Required) |
| :--- | :--- |
| `"Discriminator Scan Results"` | `"S-curve Knee Aligns at DAC 180; Threshold Spread Stays Within $\pm 2\,\text{LSB}$"` |
| `"Multi-RU Readout Status"` | `"Concurrent Two-RU Capture Requires Hardware Buffer Lock in FPGA Firmware"` |
| `"SiPM Current Measurements"` | `"Dark Current Decreases by 50% for Each $8\,^\circ\text{C}$ Temperature Drop"` |
| `"Beam Test Timing Resolution"` | `"Average Single-Hit Time Resolution Reaches $32\,\text{ps}$ at $42\,\text{V}$ Bias"` |

---

## 4. Pillar 3: Human Brain Processing & Cognitive Anchors

When explaining complex hardware (ASICs, optical transceivers, FPGAs) or complex analysis methods (STXS, Combine datacards), the human brain requires **intuitive cognitive anchors** before processing raw technical numbers.

### A. The 3-Step Cognitive Ladder
Whenever introducing a complex mechanism, follow this 3-step sequence:

1. **Step 1: The Intuitive Real-World Analogy (The Mental Anchor)**
   - *Example*: The "Two-Camera Analogy" for multi-RU synchronization, or the "Lego Bricks" analogy for reusable DAQ primitives.
2. **Step 2: The Physical Mechanism**
   - Explain what physical signals, registers, or particles are moving.
3. **Step 3: The Quantitative Metric**
   - Provide the exact numbers, tolerances, units, and errors ($\pm 1.5\,\text{ps}$, $3.8\,\text{V}$, $1.6\times 10^{15}\,\text{n_{eq}/cm^2}$).

---

## 5. Supported Slide Formats (Markdown & HTML Only)

### Format A: Marp (Markdown Presentation Ecosystem)

```markdown
---
marp: true
theme: gaia
_class: lead
paginate: true
backgroundColor: #0d1117
color: #c9d1d9
---

# Two-Stage Phase Lock Aligns lpGBT Clocks Within 50 ps

<!-- Top Assertion Title: Physical Conclusion -->

![bg left:60% 90%](figures/tdc_phase_scan_2ru.png)

### Key Results
- **Phase step size**: $50\,\text{ps}$ steps across the $25\,\text{ns}$ clock cycle.
- **Lock criterion**: Minimum 3 consecutive stable bits in EPRX.
- **Inter-channel jitter**: Measures $< 15\,\text{ps}$ RMS across 24 channels.

> 💡 **Bottom Line:** Both readout units lock to the Serenity clock without manual phase tuning.

<!--
Speaker Notes (ASD-STE100):
- Explain that lpGBT phase locking now runs automatically in the setup script.
- Point to the stable green plateau in the left plot between steps 12 and 18.
- Note that jitter remains well below our 30 ps design budget.
-->
```

### Format B: Native Standalone HTML/CSS Slide Deck

```html
<section class="slide" id="slide-04">
  <header class="slide-header">
    <h2>Two-Stage Phase Lock Aligns lpGBT Clocks Within 50 ps</h2>
  </header>
  
  <div class="slide-body grid-2col">
    <!-- Visual Evidence (65% width) -->
    <div class="visual-pane">
      <img src="figures/tdc_phase_scan_2ru.svg" alt="TDC Phase Scan Residuals" />
      <span class="source-tag">Serenity Board s12 • Run 2026-09-18 • Beam H4</span>
    </div>

    <!-- ASD-STE100 Telegraphic Bullets (35% width) -->
    <div class="bullet-pane">
      <ul class="ste-bullets">
        <li><strong>Phase step</strong>: $50\,\text{ps}$ steps over one $25\,\text{ns}$ LHC clock cycle.</li>
        <li><strong>Lock criterion</strong>: Requires 3 consecutive error-free bits in lpGBT EPRX.</li>
        <li><strong>Residual jitter</strong>: Measures $< 15\,\text{ps}$ RMS across all 24 channels.</li>
      </ul>
      
      <div class="takeaway-card">
        <strong>Bottom Line:</strong> Both readout units lock automatically to the reference clock without manual tuning.
      </div>
    </div>
  </div>
</section>
```

---

## 6. Talk Archetypes & Timing Budgets

| Meeting Archetype | Duration | Slide Budget | Core Narrative Structure |
| :--- | :--- | :--- | :--- |
| **Weekly WG / Hardware Update** | 5–10 min | 5–7 slides | Context (1) $\to$ Progress Since Last Week (2) $\to$ Current Data/Puzzle (2) $\to$ Action Items (1). |
| **Test-Beam / Commissioning Briefing** | 12–15 min | 8–10 slides | Setup & Mapping (2) $\to$ Beam Quality (1) $\to$ Hit Efficiency & Timing (4) $\to$ Summary (1). |
| **Approval / Pre-Approval Presentation** | 20–30 min | 16–20 slides | Motivation (2) $\to$ Object ID & Calibration (4) $\to$ Signal/Background (4) $\to$ Systematics (3) $\to$ Results (3). |

---

## 7. Anti-Pattern Ledger (Before vs. After)

| Common Flawed Slide Style (❌) | Why It Fails | ASD-STE100 & Assertion Style (✅) |
| :--- | :--- | :--- |
| Title: *"Introduction & Setup"* | Zero information conveyed; audience must read body. | Title: *"Serenity ATCA Board Connects 6 Readout Units via 25 Gbps Optical Fibers"* |
| *"In this scan, we set the bias voltage across the SiPMs and carefully observed that the dark count rates were somewhat elevated at higher temperatures."* | 26 words, passive, vague qualifiers (*"carefully"*, *"somewhat elevated"*). | - **Dark count rate increases**: Doubles every $8\,^\circ\text{C}$ rise.<br>- **Cooling limit**: $\text{CO}_2$ system holds sensors at $-35\,^\circ\text{C}$. |
| *"The reason why Unit B failed to read was due to the fact that the link selector register was inadvertently overwritten by Unit A's routine."* | Conversational meta-commentary (25 words). | - **Unit B lost connection**: `selectLink()` wrote over shared FPGA registers.<br>- **Fix**: Added single-process lock. |
| Slide with 9 densely packed bullet points and tiny font. | Severe cognitive overload; audience stops listening to speaker. | Max 3 bullets + 1 dominant SVG/PNG plot + 1 takeaway callout box. |
