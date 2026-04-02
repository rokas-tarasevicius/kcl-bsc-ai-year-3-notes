## Goal

Turn the user-provided **lecture slides** and **example/past exam questions** into **exam-focused LaTeX revision notes** that are:

- **Consistent** across modules (same structure, same environments, same conventions)
- **Exam-focused** (what to spot, what to apply, where marks come from, common traps)
- **Learnable** (intuition → definition → method → examples)
- **Technically correct** (definitions, notation, assumptions)

Do **not** invent syllabus content. If the slides/questions don't justify a claim, add a **TODO** and ask a targeted question.

## Compactness requirement (apply everywhere)

Keep the notes **dense but readable** (exam notes you can actually revise from):

- Prefer **short, information-dense** bullets over long prose.
- Prefer **fewer, better** worked examples:
  - Per topic/week: often **4–8** high-signal examples (quiz-style + longer ones).
- Avoid repetition: cross-reference earlier sections instead of re-explaining.

## Repository structure (one folder per module)

Create one folder per module under **either** `modules/` (preferred) or `notes/` (if the repo already uses it). Default to `modules/`.

For a module named `{MODULE_CODE} {MODULE_TITLE}`, create:

```
modules/{module-slug}/
  README.md
  main.tex
  preamble.tex
  topics/
    00-module-overview.tex
    week-01-{topic-slug}.tex
    week-02-{topic-slug}.tex
    ...
```

### Naming rules

- `module-slug`: kebab-case, short, stable (e.g. `cs301-algorithms`, `math210-linear-algebra`)
- `topic-slug`: kebab-case, short, stable (e.g. `probability-basics`, `pca`, `tcp-congestion`)

## Required document structure (per module)

The rendered notes must follow this outline:

1. **Module overview**
2. **Week 1: {title}**
   - 2.1 **Topic summary**
   - 2.2 **Overview + core concepts + extended theory** (merged)
3. **Week 2: {title}**
4. …

### File splitting rule (important)

Do **not** split into many files.

- Exactly **one** `main.tex` per module.
- Exactly **one** `.tex` file per topic/week under `topics/`.
- `00-module-overview.tex` counts as the "module overview topic file".

## Assembly (`main.tex`)

`main.tex` should:

- `\input{preamble.tex}`
- Include a clean **title page** (module code/title, year/semester, compiled date)
- Put `\tableofcontents` on its own page
- Ensure **module overview** starts on a new page
- Ensure **each week/topic starts on a new page** (`\clearpage` before each `\input`)
- `\input{topics/00-module-overview.tex}`
- `\input{topics/week-01-...tex}`, `\input{topics/week-02-...tex}`, etc (in week order)

## Root `README.md` (required): link the latest PDFs

Maintain a **single, canonical list** of "Latest compiled PDFs" at the **top of the repo root** `README.md`.

- When a **new module** folder is created under `modules/`, add a new bullet linking to its **current latest compiled PDF** (relative link).
- When a module's PDF filename/location changes (e.g. `main.pdf` vs `NLP.pdf`), update the existing link (don't add duplicates).
- Prefer compiling to `modules/<module-slug>/main.pdf` for consistency, but if a module already uses a different name, link to whatever is actually present.
- Keep the list **one line per module** and **easy to scan** (module code + title).

## Preamble template (`preamble.tex`)

The preamble should use `\IfFileExists` for optional packages to ensure portability:

```latex
% Optional packages with fallbacks
\IfFileExists{fancyhdr.sty}{\usepackage{fancyhdr}...}{}
\IfFileExists{enumitem.sty}{\usepackage{enumitem}...}{}
\IfFileExists{cleveref.sty}{\usepackage{cleveref}}{%
  \providecommand{\cref}[1]{\ref{##1}}  % Note: ## inside \IfFileExists
}
\IfFileExists{microtype.sty}{\usepackage[expansion=false]{microtype}}{}
```

**Key settings**:
- `\setlength{\parindent}{0pt}` and `\setlength{\parskip}{4pt}` for clean spacing.
- Define colors: `DefBlue`, `ThmGreen`, `ExOrange`, `TipRed`, `KeyGray`.
- Utility commands: `\separator`, `\bigseparator`, `\TODO`, `\code{}`, `\term{}`.

## Per-topic file template (`topics/week-XX-*.tex`)

Each topic file should begin with `\section{Week X: <title>}` and contain compact subsections:

- `\subsection{Topic Summary}`
  - Start with a **Learning Objectives** `keybox` (copied from slides if available)
  - Add a brief "Big Picture" paragraph explaining what this week covers
  - Add "What Examiners Like to Ask" bullets (derived from quiz questions)

- `\subsection{Overview + core concepts + extended theory}`
  - Use a short **Roadmap** list to orient the reader
  - **Definition boxes** + intuition + mini examples
  - Prefer **tables** for comparisons (e.g. tokens vs types, typology, byte lengths)
  - "Spot it in a question" cues as **Exam tip** boxes
  - Theorem/Algorithm boxes (only the ones that matter for exams)
  - For each method:
    - Statement
    - When to use
    - Assumptions/constraints
    - How to apply (procedure bullets or numbered steps)
    - Typical pitfalls
  - Proofs: omit unless explicitly needed; if omitted, say "Proof omitted (not exam-relevant here)".

## LaTeX conventions (shared)

### Document class + packages

- Prefer `\documentclass[10pt]{article}` (compact print-friendly).
- Use `geometry` with a **larger left margin** for binding/holes (e.g. `left=1.35in, right=1in`).
- Use `amsmath`, `amssymb`, `mathtools`, `geometry`, `graphicx`, `booktabs`, `xcolor`, `hyperref`.
- Optional packages should degrade gracefully (repo may have a minimal TeX install):
  - `tcolorbox` (pretty boxes) → fallback to simple environments
  - `cleveref` → fallback to `\ref`
  - `enumitem` → fallback to tightened default list spacing
  - `microtype` can be problematic → disable expansion or make optional
- Avoid `minted` unless user explicitly requests it (requires shell-escape). Prefer `listings`.

### Environments

Use **simple box environments** (colored bold title + spacing, no fancy borders):

```latex
\newenvironment{defbox}[1][]{%
  \par\medskip\noindent\textbf{\textcolor{DefBlue}{Definition}}%
  \if\relax\detokenize{#1}\relax\else\textbf{\textcolor{DefBlue}{ (#1)}}\fi%
  .\par\smallskip\ignorespaces
}{\par\medskip}
```

Environment types: `defbox`, `thmbox`, `exbox`, `tipbox`, `keybox`.

**Syntax**: Use `\begin{defbox}[Title]` — NOT `\begin{defbox}[title=Title]` (the `title=` prefix will render literally).

### Cross-references

- Label important results and reference via `\cref{}`.
- No unresolved references ("??") in final output.

### Encoding / portability

- Assume `pdflatex` unless the user requests XeLaTeX/LuaLaTeX.
- Avoid raw non-Latin Unicode characters that can break `pdflatex`; use transliteration or LaTeX accent macros (e.g. `Se\~{n}or`, `op\'{e}ra`, `hanzi` instead of 汉字).
- **Table cells**: If a cell starts with `[text]`, escape as `{[text]}` to prevent LaTeX parsing it as an optional argument.

### Compilation

- Always run `pdflatex` **twice** to resolve TOC and cross-references.
- Use `-interaction=nonstopmode -halt-on-error` for automated builds.

## How to process slides + exam questions

- Use slide headings to decide **weeks/topics** and keep slide terminology.
- **Preserve week numbering from slides** — if slides skip Week 6, the notes should too (Week 5 → Week 7).
- Standardize notation (one symbol per concept; define it once).
- For exam/quiz questions:
  - **Quiz questions are gold** — they reveal exactly what examiners test and common wrong answers.
  - Classify into the relevant topic/week.
  - Integrate the best ones into **Worked examples**.
  - Include the **feedback/explanation** from quiz answers as exam tips.
  - Keep solutions concise and mark-focused.

### Content patterns that work well

- **Comparison tables**: Use tables to compare related concepts (e.g., RNN vs LSTM vs Transformer, black-box vs white-box attacks).
- **Summary tables at section end**: A final table comparing all methods/techniques covered helps consolidate learning.
- **Roadmap lists**: Start each major subsection with a numbered roadmap of what will be covered.
- **"What examiners like to ask"**: Extract question patterns from quizzes (e.g., "Explain X", "Compare Y and Z", "Calculate...").
- **Worked examples from quizzes**: Convert MCQ questions + explanations into worked examples.

## When to ask the user questions (required)

Ask for clarification when:

- Slides contradict themselves (notation/sign conventions/definitions)
- A technique appears in exam questions but not in slides (or vice versa)
- A formula is missing assumptions (domain/conditions/units)
