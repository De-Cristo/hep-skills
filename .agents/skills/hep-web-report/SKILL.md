---
name: hep-web-report
description: >-
  Methodology and principles for authoring, reviewing, and compiling High-Energy Physics (HEP) technical research notebooks, DAQ reports, and interactive web documentation into self-contained HTML/Markdown documents. Enforces ASD-STE100 (Simplified Technical English) for cognitive clarity, "Start Here / 60-Second Mental Models", Lego-block functional categorizations, responsive layouts, MathJax, and Mermaid vector diagrams.
allowed-tools: Read Write Edit Bash
---

# HEP Web Report & Interactive Documentation Skill

This skill provides a publication-grade protocol for designing, writing, and compiling **interactive technical reports, DAQ research notebooks, and system documentation** in High-Energy Physics using **Markdown and standalone HTML**.

It enforces the **ASD-STE100 (Simplified Technical English)** standard for language economy, while structuring complex technical systems into **brain-friendly mental models**, **modular functional clusters (Lego blocks)**, and **self-contained portable web artifacts**.

---

## 1. Core Architecture: The Four Web Pillars

```
┌─────────────────────────────────────────────────────────────────────────────────────────────────┐
│                                   The Four Web Report Pillars                                   │
└───────────────────────────────────────────────┬─────────────────────────────────────────────────┘
                                                │
       ┌───────────────────┬────────────────────┴────────────────────┬───────────────────┐
       ▼                   ▼                                         ▼                   ▼
【Pillar 1: Mental Model】 【Pillar 2: Functional Clusters】 【Pillar 3: STE100 Language】 【Pillar 4: Portable HTML】
 • "Start Here" in 60s    • The "Lego Box" Paradigm      • Max 25 Words / Sentence   • 100% Self-Contained
 • Real-World Analogy     • Group dense tables into 3–4  • Max 3 Consecutive Nouns   • Dark / Light Theme
 • Physical vs. Electrical  functional clusters          • Plain-Language Column     • Mermaid Diagrams
   Hierarchy Mapping      • Summary of Pitfalls/Traps      in Register Tables        • Instant EOS/WWW Deploy
```

---

## 2. Pillar 1: The "Start Here" 60-Second Mental Model

Technical research reports often fail because they drop the reader immediately into register addresses, XML tags, or raw Python functions.

Every report written with this skill **must open with a dedicated "Start Here" section** containing:

1. **The Executive Problem Statement (Today vs. Tomorrow)**:
   - What the system does today (e.g. tests one board in isolation).
   - What the system must do tomorrow (e.g. record synchronized data across 6 boards).
   - The primary technical obstacle in 1 sentence.
2. **The Physical-to-Electronics Architecture Diagram**:
   - A clean ASCII or Mermaid diagram mapping the physical detector parts (Tray, Readout Unit, Detector Module, Sensor) to the electronic control stack (Back-End FPGA, Concentrator Card, Front-End ASICs, Host Software).
3. **The Intuitive Real-World Analogy**:
   - A physical analogy that gives the non-expert an immediate intuition before reading equations or code (e.g. *The Two-Camera Analogy* for hardware capture synchronization).

---

## 3. Pillar 2: Functional Clustering (The "Lego Box" Model)

When a DAQ or analysis system contains 10 to 30 individual functions or registers, **never present them as a flat, unorganized list**. The human working memory can only hold $4 \pm 1$ chunks at a time.

Group all primitives into **3 to 4 functional clusters** before showing the detailed reference tables:

```
+----------------------------------------------------------------------------------------------------+
|                                THE REUSABLE CAPABILITIES (LEGO BRICKS)                             |
+----------------------------------------------------------------------------------------------------+
|  🔌 Cluster 1: Link & Timing Infrastructure      |  🎛️ Cluster 2: Slow Control & Telemetry         |
|  - Open optical links and lock reference clocks. |  - Read sensor temperatures and bias currents.   |
|  - Align e-link receiver phases.                 |  - Set ALDO power rails and I2C peripherals.     |
+--------------------------------------------------+--------------------------------------------------+
|  ⚡ Cluster 3: Front-End Configuration & Command  |  💾 Cluster 4: Data Capture & Evacuation         |
|  - Program ASIC registers and thresholds.        |  - Arm FPGA buffers and trigger common capture.  |
|  - Distribute fast RESYNC and trigger pulses.    |  - Drain raw data blocks over IPbus to disk.     |
+----------------------------------------------------------------------------------------------------+
```

---

## 4. Pillar 3: Comprehensive ASD-STE100 Language Standard for Web

Technical readers skim web reports across laptops, tablets, and phones. The **ASD-STE100 (Simplified Technical English)** specification ensures that documentation is unambiguous, easy to translate, and causes zero mental fatigue.

### A. The 8 Mandatory ASD-STE100 Rules for Web Documentation

1. **Rule 1: Sentence Length Budgets**
   - **Descriptive sentences**: Maximum **25 words**.
   - **Procedural steps & instructions**: Maximum **20 words**.
   - **Bullet points**: Maximum **20 words**.
   - *If an idea has two thoughts, write two separate sentences.*

2. **Rule 2: Noun Cluster Limit (Maximum 3 Nouns)**
   - Do not stack more than three nouns together. Unbundle long technical names using prepositions (*of*, *for*, *on*):
   - ❌ **Non-STE100**: *"Serenity ATCA board optical transceiver link FIFO buffer overflow"* (8 nouns stacked).
   - ✅ **STE100**: *"Overflow of the FIFO buffer in the optical receiver on the Serenity board"*.

3. **Rule 3: One Meaning per Word (Unambiguous Vocabulary)**
   - Words with multiple meanings are strictly controlled:
     - Use **"because"** for cause (never use *"since"* or *"as"* to mean because).
     - Use **"after"** for time sequences (never use *"subsequent to"* or *"following"*).
     - Use **"before"** for prior events (never use *"prior to"* or *"in advance of"*).
     - Use **"while"** only for simultaneous time (never use *"while"* to mean although).

4. **Rule 4: Approved Controlled Vocabulary for HEP Documentation**

| Unapproved Word / Bloat (❌) | Approved ASD-STE100 Word (✅) | Example in HEP Web Documentation |
| :--- | :--- | :--- |
| *prior to* | **before** | *"Configure the lpGBT before you train the clock phase."* |
| *subsequent to* | **after** | *"Read the buffer after the trigger sequence finishes."* |
| *in order to* | **to** | *"Press the button to freeze the capture."* |
| *terminate / abort* | **stop** | *"Stop the acquisition if the link drops."* |
| *demonstrate / exhibit* | **show** | *"The histogram shows a clear peak at 125 GeV."* |
| *utilize / employ* | **use** | *"Use the SCA ADC to measure temperature."* |
| *commence / initiate* | **start** | *"Start the calibration routine."* |
| *it is recommended that* | **we recommend** / **should** | *"We recommend a bias voltage of 42.5 V."* |
| *is capable of* | **can** | *"The chip can measure 24 channels."* |
| *is mandatory to* | **must** | *"You must lock the clock before readout."* |

5. **Rule 5: Active Voice Default**
   - Put the actor first: **Subject + Action Verb + Object**.
   - ❌ Passive: *"A reset of the FPGA memory is executed by the script before reading."*
   - ✅ Active: *"The script resets the FPGA memory before it reads data."*

6. **Rule 6: Imperative Mood for Steps and Procedures**
   - In numbered walkthroughs and guides, start each step directly with a strong command verb:
   - ❌ *"The user should proceed to power up the board and then verification of the LED status follows."*
   - ✅ *"1. Power up the board.<br>2. Check that the green LED turns on."*

7. **Rule 7: No Double Negatives or Ambiguous Modals**
   - Never write negative statements when a positive expression is possible:
   - ❌ *"It is not impossible for the link to not synchronize."*
   - ✅ *"The link can fail to synchronize."*
   - Never use *"may"* or *"might"* for rules. Use **"must"** (required), **"do not"** (forbidden), or **"can"** (possible).

8. **Rule 8: Mandatory "Plain-Language Meaning" Column in Data Tables**
   - When presenting registers, bit masks, XML address tables, or configuration parameters, **never show raw hex codes alone**.
   - Every table must include a dedicated **"Plain-Language Meaning (STE100)"** column:

| Interface / Register | Address / Offset | Observed Behavior | Plain-Language Meaning (ASD-STE100) |
| :--- | :--- | :--- | :--- |
| `MEM_RESET` | `0x42` | Toggles high/low | Clears the FPGA data buffer. Erases all unread data! |
| `selectLink(L)` | `0x10` | Writes `chan_sel` | Chooses the optical link. Overwrites the previous link setting! |
| `MEM_LOCKED` | `0x41` | Read-only bit | Indicates that the buffer holds a frozen measurement block. |
| `valdo_*_dac` | TOFHIR reg | Programs 10-bit DAC | Sets the ALDO output voltage for SiPM bias. |

---

### B. The "Traps & Pitfalls" Table (Cognitive Contrast)
When explaining why older software or single-unit scripts cannot be composed together, provide a dedicated summary table contrasting **"What happens today"** against **"Why it breaks in multi-unit operation"**:

| # | Trap / Pitfall | What Happens Today (Single-Unit) | Why It Breaks in Multi-Unit Operation (STE100) |
| :--- | :--- | :--- | :--- |
| **1** | **Shared Selector** | `selectLink()` writes global FPGA registers. | Selecting Unit B silently overwrites the active link for Unit A. |
| **2** | **Coupled Reset** | `read_buffers(reset=True)` clears memory. | Reading Unit A clears Unit B's data before Unit B is read. |
| **3** | **Lost Source ID** | Decoder drops link number during conversion. | Hits from Unit A and Unit B get mixed together in analysis. |

---

### C. Real-World Transformation Examples (Before vs. After)

* **Example 1: Firmware & Memory Architecture**
  - ❌ *Before (51 words, passive, dense jargon)*: *"Because the shared link selection register inside the datapath region of the Serenity firmware is modified globally upon every execution of selectLink without thread-level or process-level mutex isolation, any sequential invocation over multiple concentrator card objects inevitably overwrites previous channel settings, thereby invalidating synchronized acquisition across independent readout units."*
  - ✅ *After (ASD-STE100, 3 clear sentences, max 19 words each)*: *"The FPGA uses global registers (`quad_sel` and `chan_sel`) to choose the active link. When you select a new link for Unit B, the FPGA overwrites the setting for Unit A. Because the software does not lock this register, two units cannot share the link selector at the same time."*

* **Example 2: Detector Commissioning & Safety**
  - ❌ *Before (33 words, passive, negative hedge)*: *"It is of utmost importance that the bias voltage should not be increased beyond the breakdown threshold until such time as the thermal cooling system has achieved a temperature of minus thirty-five degrees."*
  - ✅ *After (ASD-STE100, 16 words, active, direct)*: *"Do not raise the bias voltage above breakdown until the cooling system reaches $-35\,^\circ\text{C}$."*

---

## 5. Pillar 4: Portable, Standalone HTML Standard

Reports compiled with this skill must be **completely self-contained single HTML files** that can be emailed, opened offline in a browser, or served from CERN EOS web space (`/eos/user/.../www/`).

### A. Core Frontend Requirements
1. **Responsive Dual Layout**:
   - Sticky sidebar navigation on desktop ($\ge 960\,\text{px}$) with active scroll-spy.
   - Clean single-column layout on mobile/tablets with a collapsible menu.
2. **Instant Dark / Light Mode**:
   - Zero-flicker CSS variable system (`[data-theme="light"]` and `[data-theme="dark"]`).
   - Theme preference saved to `localStorage`.
3. **Interactive Vector Diagrams (Mermaid.js)**:
   - State diagrams, flowcharts, and sequence diagrams rendered natively in the browser.
4. **Formula Precision (MathJax)**:
   - LaTeX mathematical expressions ($\text{erfc}$, $\chi^2/\text{ndf}$, jitter integrals) rendered with MathJax.
5. **Print & PDF Export Styling**:
   - Automatically hides sidebars, expands widths, and sets background to white during `@media print`.

---

## 6. Standalone Python Compilation Recipe

To compile any Markdown research report into the publication-grade HTML format, use this standard generator pattern:

```python
#!/usr/bin/env python3
"""compile_report.py - Compiles Markdown to a standalone, responsive HTML report."""
import re
import markdown

def compile_markdown_to_html(input_md_path: str, output_html_path: str, title: str):
    with open(input_md_path, 'r', encoding='utf-8') as f:
        md_content = f.read()

    # Protect mermaid diagram code blocks from markdown mangling
    mermaid_blocks = []
    def extract_mermaid(match):
        idx = len(mermaid_blocks)
        mermaid_blocks.append(match.group(1).strip())
        return f"\n\n___MERMAID_BLOCK_{idx}___\n\n"

    md_processed = re.sub(r'```mermaid\s*\n(.*?)\n```', extract_mermaid, md_content, flags=re.DOTALL)

    # Convert markdown to html with extended tables, toc, and fenced code
    html_body = markdown.markdown(
        md_processed,
        extensions=['tables', 'fenced_code', 'toc', 'sane_lists', 'attr_list', 'def_list'],
        extension_configs={'toc': {'toc_depth': '2-3'}}
    )

    # Restore mermaid containers
    for idx, block in enumerate(mermaid_blocks):
        replacement = f'<div class="mermaid">\n{block}\n</div>'
        html_body = html_body.replace(f'<p>___MERMAID_BLOCK_{idx}___</p>', replacement)
        html_body = html_body.replace(f'___MERMAID_BLOCK_{idx}___', replacement)

    # Wrap in self-contained responsive HTML shell (with CSS, MathJax, Mermaid, theme toggle)
    # [Insert standard CSS theme variables, sidebar, and layout template]
    
    with open(output_html_path, 'w', encoding='utf-8') as f:
        f.write(full_html)
```

---

## 7. CERN Web & EOS Deployment Guidelines

When deploying reports for collaboration review:

1. **Target Directory**:
   ```bash
   mkdir -p /eos/user/<initial>/<username>/www/reports/
   cp report.html /eos/user/<initial>/<username>/www/reports/
   ```
2. **Permissions**:
   Ensure CERN web server read permissions:
   ```bash
   chmod 644 /eos/user/<initial>/<username>/www/reports/report.html
   ```
3. **Public URL**:
   The report is immediately accessible at:
   ```text
   https://<username>.web.cern.ch/<username>/reports/report.html
   ```
