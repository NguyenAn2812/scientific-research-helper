# Scientific Research Helper — Claude Skill

> A Claude skill that guides students through every stage of academic research — from brainstorming a topic to verifying statistical outputs.

---

## What This Skill Does

**Scientific Research Helper** turns Claude into a dedicated academic research companion for undergraduate and graduate students across all disciplines. Instead of generic AI responses, you get a structured, stage-aware assistant that knows where you are in the research process and what you actually need next.

Whether you're staring at a blank page trying to pick a topic, stuck on your methodology section, or getting feedback on a draft thesis — this skill has a workflow for it.

---

## Key Features

### File Review — Upload & Get Structured Feedback
Drop in a PDF, DOCX, or paste your draft. The skill reads it end-to-end, identifies the document type (thesis, IMRAD paper, research proposal, internship report, etc.), and gives you structured feedback across three dimensions:

- **Consistent** — strengths worth keeping
- **Needs review** — ambiguous or underdeveloped areas
- **Clear contradictions** — internal inconsistencies flagged with specific quotes

### Writing Plan & Asset Inventory
Tell the skill your topic, share your evidence files, and it generates a complete inventory of everything your paper needs: a personalized section outline, a full table list, and a figure list — each with instructions on how to extract or produce the asset from your actual data files.

### Literature Search & Overlap Check
Before you invest weeks into a topic, the skill searches Google Scholar, Semantic Scholar, and ResearchGate to assess how saturated the research space is — and suggests angles for original contribution. It can also spot-check citations in your bibliography for accuracy.

### Data & Code Verification
Paste your Python, R, SPSS, Stata, or MATLAB files alongside your report. The skill cross-references the numbers in your text against your actual analysis output and flags any discrepancies — before your supervisor does.

---

## Supported Research Stages

| Stage | What the Skill Helps With |
|-------|--------------------------|
| **1 — Brainstorming** | Topic ideas, research questions, feasibility check |
| **2 — Proposal** | Objectives, hypotheses, scope, theoretical framework |
| **3 — Literature Review** | Search strategy, clustering themes, writing the review |
| **4 — Methodology** | Quantitative / qualitative / mixed methods guidance |
| **5 — Review & Critique** | Full document review with structured feedback |
| **6 — Finalization** | Conclusions, citation formatting, consistency check |

---

## Supported File & Evidence Types

| Input | What the Skill Does |
|-------|---------------------|
| PDF / DOCX thesis or paper | Reviews structure, consistency, and argumentation |
| `.csv` / `.xlsx` data files | Checks sample size, distribution, and outliers |
| `.py` / `.R` / `.do` / `.m` scripts | Reads analysis logic, verifies outputs match report |
| SPSS output / screenshots | Cross-references result tables with reported figures |
| SQL queries | Checks whether data collection matches description |

---

## How to Install

1. Download or clone this repository
2. Open [Claude.ai](https://claude.ai) and navigate to **Skills**
3. Click **Add Skill** → **Upload from file**
4. Select `scientific-research-helper.skill`
5. The skill is now available in your conversations

---

## Repository Structure

```
scientific-research-helper/
├── SKILL.md                              # Core skill instructions
└── references/
    ├── research-proposal-template.md    # Standard proposal structure
    ├── writing-review-checklist.md      # Section-by-section review checklist
    └── topic-idea-checklist.md          # Topic feasibility evaluation checklist
```

---

## Design Philosophy

- **Guide, don't ghostwrite.** The skill helps you think through your research — it won't write your thesis for you.
- **Ask before assuming.** When context is unclear, it asks one or two targeted questions rather than making wrong assumptions.
- **Evidence first.** For quantitative research, it always asks to verify numbers against actual outputs before giving feedback.
- **No hallucinated references.** If it can't find a source through search, it says so. It will never fabricate author names or paper titles.

---

## Contributing

Found a gap in the workflows? Have a document type or discipline not well covered? Pull requests are welcome. Please open an issue first to describe what you'd like to add.

---

## License

MIT License — free to use, modify, and distribute.
