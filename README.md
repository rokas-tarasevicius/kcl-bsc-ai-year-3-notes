# KCL BSc AI Year 3 Revision Notes 2025/26

### Latest compiled PDFs (and coverage)

| Module | PDF | Weeks covered | Latest week |
|---|---|---:|---:|
| **6CCSAACV — Advanced Computer Vision** | [main.pdf](modules/6ccsaacv-advanced-computer-vision/main.pdf) | 2 (W1–W2) | 2 |
| **6CCSACCM — Cooperation, Coordination and Multi-Agent Systems** | [main.pdf](modules/6ccsaccm-cooperation-coordination-multiagent-systems/main.pdf) | 6 (W1–W5, W8) | 8 |
| **6CCSAHAI — Human-AI Interaction** | [HAI.pdf](modules/6ccsahai-human-ai-interaction/HAI.pdf) | 9 (W1–W5, W7–W10) | 10 |
| **6CCSANLP — Natural Language Processing** | [NLP.pdf](modules/6ccsanlp-natural-language-processing/NLP.pdf) | 10 (W1–W5, W7–W11) | 11 |
| **6CCSAPEA — Philosophy & Ethics of AI** | [Philosophy\_and\_ethics.pdf](modules/6ccsapea-philosophy-ethics-ai/Philosophy_and_ethics.pdf) | 9 (W1–W9) | 9 |
| **6CCSAPRA — Principles of Robot Autonomy** | [main.pdf](modules/6ccsapra-principles-robot-autonomy/main.pdf) | 1 (W1) | 1 |

Weeks covered are counted from `topics/week-*.tex` files in each module folder.

This template helps you quickly create new modules and weekly content for your revision notes. The AI assistant uses the **NLP module** (`modules/6ccsanlp-natural-language-processing/`) as the gold standard for formatting and structure.

---

## Template 1: Creating a New Module

Use this prompt structure when starting a new module:

```
Please create a new module lecture notes using the NLP notes structuring as the 
gold standard—those have the best formatting and structuring rules, so explore that.

The module:

[MODULE_CODE] [YEAR]~[YEAR] SEM[SEMESTER] [SECTION_ID] [MODULE_NAME]
Module Overview

**Module Overview Section**

[Paste the module overview text from KEATS, including:]
- Module title and description
- Introduction/welcome text
- Aims
- Learning Outcomes
- Assessment information
- Feedback and formative assessment details
```

### Example:

```
Please create a new module lecture notes using the NLP notes structuring as the 
gold standard—those have the best formatting and structuring rules, so explore that.

The module:

6CCSACCM 25~26 SEM2 000001 COOPERATION, COORDINATION AND MULTI-AGENT SYSTEMS
Module Overview

Welcome to Cooperation, Coordination and Multi-Agent Systems.

A multi-agent system consists of multiple autonomous entities that possess 
distributed information, computational capabilities, and potentially conflicting 
objectives. These systems can be cooperative, such as sensor networks or teams 
of mobile robots operating in a warehouse, or competitive, like electronic 
marketplaces or scenarios involving resource and task allocation.

Aims:
- [List aims]

Learning Outcomes:
By the end of this module, you will be able to:
CCM1. [Outcome 1]
CCM2. [Outcome 2]
...
```

### What the AI Will Create:

- Module folder: `modules/[module-slug]/`
- `README.md` — Build instructions
- `main.tex` — Assembly file (title page, TOC, topic includes)
- `preamble.tex` — Shared packages + box environments
- `topics/00-module-overview.tex` — Module overview with learning outcomes
- Compiled PDF

---

## Template 2: Creating a New Week of Material

Use this prompt structure when adding weekly content:

```
[MODULE_CODE] [YEAR]~[YEAR] SEM[SEMESTER] [SECTION_ID] [MODULE_NAME]
Week [N] - [Topic Title]

Week [N] - [Topic Title]
Section outline

**Overview Section**

[Paste the week overview from KEATS, including:]
- Overview paragraph
- Learning Objectives (bulleted list)
- Instructions

**Material Section**

[Title of lecture slides or material]

material:

[Paste the full content of:]
1. Lecture slides (text extracted from PDFs)
2. Additional slides or examples
3. Exercise materials

Transcripts:

[Paste the full transcript of any video lectures]
```

### Example:

```
6CCSACCM 25~26 SEM2 000001 COOPERATION, COORDINATION AND MULTI-AGENT SYSTEMS
Week 1 - Non-cooperative games (part I)

Overview:
This week introduces the fundamental concepts of non-cooperative game theory...

Learning Objectives:
After studying this topic, students will be able to:
- Define the core concepts of non-cooperative game theory...
- Formulate real-world scenarios as strategic-form games...
- [etc.]

Material:

6CCSACCM: Cooperation, Coordination and Multi-Agent Systems
Week 1
Non-cooperative games (part I)
Maria Polukarov

[Full slide content here]

Transcripts:

Hello, and welcome to Cooperation, Coordination, and Multi-Agent Systems...
[Full transcript here]
```

### What the AI Will Create:

- New topic file: `topics/week-[NN]-[topic-slug].tex`
- Content structured as:
  - **Topic Summary** with Learning Objectives keybox
  - **Big Picture** paragraph
  - **What Examiners Like to Ask** bullets
  - **Overview + Core Concepts + Extended Theory**
  - **Roadmap** for the week
  - **Definition boxes** for key concepts
  - **Theorem boxes** for important results
  - **Example boxes** with worked solutions
  - **Exam tip boxes** for common pitfalls
  - **Summary tables** comparing related concepts
- Updated `main.tex` to include the new week
- Recompiled PDF

---

## Content Extraction Tips

### From KEATS:
1. **Module Overview**: Copy from the main module page, including all sections
2. **Week Overview**: Copy from each week's page, including Learning Objectives
3. **Materials**: Look for lecture slides PDFs or HTML content

### From Lecture Slides (PDF):
- Use PDF text extraction tools or copy directly from the PDF viewer
- Preserve structure: titles, bullet points, formulas, matrices
- Include all examples, definitions, theorems, and worked problems

### From Video Transcripts:
- If available on KEATS, copy the full auto-generated or manual transcript
- These often contain valuable explanations not in slides

---

## Module Naming Conventions

| Component | Format | Example |
|-----------|--------|---------|
| Module code | `6CCS[A-Z]{3-4}` | `6CCSACCM` |
| Module slug | `kebab-case` | `cooperation-coordination-multiagent-systems` |
| Folder name | `[code]-[slug]` | `6ccsaccm-cooperation-coordination-multiagent-systems` |
| Topic slug | `kebab-case` | `non-cooperative-games-part-1` |
| Week file | `week-[NN]-[slug].tex` | `week-01-non-cooperative-games-part-1.tex` |

---

## Quality Checklist

Before submitting content to the AI, ensure:

- ✅ **Module overview** includes aims and learning outcomes
- ✅ **Week overview** includes specific learning objectives
- ✅ **Full slide content** is included (not just summaries)
- ✅ **Examples and exercises** are included
- ✅ **Transcripts** are included if available
- ✅ **Formulas** are clearly formatted (LaTeX will be generated automatically)
- ✅ **Tables and matrices** have clear structure

---

## Expected Output Structure

### Module Folder Structure:
```
modules/[module-slug]/
├── README.md              # Build instructions
├── main.tex               # Assembly file
├── main.pdf               # Compiled output
├── preamble.tex           # Shared packages + environments
└── topics/
    ├── 00-module-overview.tex
    ├── week-01-[topic].tex
    ├── week-02-[topic].tex
    └── ...
```

### Topic File Structure:
```latex
\section{Week N: [Title]}

\subsection{Topic Summary}
  - Learning Objectives keybox
  - Big Picture paragraph
  - What Examiners Like to Ask

\subsection{Overview + Core Concepts + Extended Theory}
  - Roadmap
  - Definitions (defbox)
  - Theorems (thmbox)
  - Examples (exbox)
  - Exam Tips (tipbox)
  - Summary tables
```

---

## Box Environment Reference

The notes use consistent LaTeX environments:

| Environment | Purpose | Usage |
|-------------|---------|-------|
| `keybox` | Learning objectives, key takeaways | `\begin{keybox}[Title]...\end{keybox}` |
| `defbox` | Definitions, formal concepts | `\begin{defbox}[Term]...\end{defbox}` |
| `thmbox` | Theorems, algorithms, procedures | `\begin{thmbox}[Theorem Name]...\end{thmbox}` |
| `exbox` | Worked examples, quiz questions | `\begin{exbox}[Example: Title]...\end{exbox}` |
| `tipbox` | Exam tips, common pitfalls | `\begin{tipbox}[Exam Tip: ...]...\end{tipbox}` |

---

## Pro Tips

1. **More content = better notes**: Include everything—the AI will condense and structure it appropriately
2. **Quiz questions are gold**: Include quiz questions and feedback; they reveal exam patterns
3. **Transcripts add context**: Video transcripts often explain the "why" behind definitions
4. **Update incrementally**: Add weeks as you go through the module
5. **Check the PDF**: Always review the compiled output for formatting issues

---

## Compilation

To compile the notes:

```bash
cd modules/[module-slug]/
pdflatex main.tex
pdflatex main.tex  # Run twice for TOC and cross-references
```

Or use `latexmk`:

```bash
latexmk -pdf main.tex
```
