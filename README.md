
# Scientific Research Helper — Claude Skill

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Platform: Claude.ai](https://img.shields.io/badge/Platform-Claude.ai-orange.svg)](https://claude.ai)
[![Target: Academic Research](https://img.shields.io/badge/Target-Academic%20Research-blue.svg)](#supported-research-stages)

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

## Installation

### Prerequisites

- A [Claude.ai](https://claude.ai) account (free or paid)
- Node.js installed on your machine

### Choose Your Installation Method

#### Option 1: Quick Install via npx (Recommended)

You can add this skill directly to your local project environment or global skill registry using the package runner:

```bash
npx skill add NguyenAn2812/scientific-research-helper

```

*This command automatically pulls the instruction assets (`SKILL.md` and templates) from the remote repository and initializes them for your workspace.*

#### Option 2: Manual Installation from Source

1. **Clone the repository**

```bash
   git clone [https://github.com/NguyenAn2812/scientific-research-helper.git](https://github.com/NguyenAn2812/scientific-research-helper.git)
   cd scientific-research-helper

```

2. **Open Claude.ai**

Navigate to [Claude.ai](https://www.google.com/url?sa=E&source=gmail&q=https://claude.ai) and sign in to your account.

3. **Access the Skills panel**

Click your avatar in the bottom-left corner, then select **Skills** (or **Projects** / **Custom Instructions** depending on your Claude interface) from the menu.

4. **Add the skill**

Click **Add Skill** → **Upload from file**, then select `SKILL.md` from your local copy of the repository.

5. **Verify the installation**

The skill should now appear in your Skills library. Start a new conversation and select **Scientific Research Helper** from the skill picker to begin.

### Keeping the Skill Updated

To sync the latest improvements and template updates:

```bash
# If installed via manual clone
git pull origin main

# If managed via CLI tool
npx skill update NguyenAn2812/scientific-research-helper

```

---
## Evaluation & Benchmark

To validate the efficiency of the **Scientific Research Helper**, we established a rigorous technical benchmark. For this evaluation, we selected **DeepSeek-V4** (via open-source deployment) as our base language model. 

### Why DeepSeek-V4?
* **Cost-Effective & Open-Source:** It is currently one of the most powerful, highly accessible, and completely free/open-source models available, making it the perfect daily driver for students and independent researchers.
* **Reasoning Capabilities:** It provides an ideal baseline to test whether an external system prompt (Skill) can significantly amplify a model's architectural and mathematical verification capabilities.

### Before vs. After Evaluation Matrix (IEEE Layout & PyTorch Code Verification)

The benchmark was conducted using a "trapped" IEEE paper draft paired with an actual Jupyter Notebook (`.ipynb`) containing silent bugs (e.g., unreported data dropping via `.dropna()`, model architecture mismatches like `nn.GELU()` vs. `ReLU`, and heavy validation overfitting logs).

The evaluation is based on a strict 1–5 scoring rubric measuring the model's accuracy, deep structural vision, and behavioral adherence:

| Evaluation Metrics (IEEE & Code Verification Tasks) | Environment | Score | Empirical Evidence from Model Output | Status |
| :--- | :--- | :---: | :--- | :---: |
| **Task 1: Accuracy Mismatch Detection**<br>*Paper: claims 96.5% \| Notebook: logs 78.5%* | **Before**<br>(Pure DeepSeek-V4) | **2/5** | Overlooked the final training log cell entirely. Simply parsed the plain text and praised the 96.5% paper claim. | ❌ Fail |
| | **After**<br>(DeepSeek + Skill) | **5/5** | Flagged under `Clear contradictions`: *"Mâu thuẫn: Văn bản ghi đạt 96.5% nhưng dòng log số #3 trong Notebook chỉ đạt val_acc: 0.785"*. |  Success |
| **Task 2: Dataset Sample Size ($N$) Drop**<br>*Paper: states N=10,000 \| Notebook: drops to 8,450* | **Before**<br>(Pure DeepSeek-V4) | **1/5** | Completely missed the data-reduction caused silently by the `.dropna()` method. | ❌ Fail |
| | **After**<br>(DeepSeek + Skill) | **4/5** | Successfully detected the sample size contraction. Prompted the user to update the methodology section (Section III) of the IEEE paper. |  Success |
| **Task 3: Mathematical & Code Alignment**<br>*Paper: defines ReLU \| Notebook: uses GELU* | **Before**<br>(Pure DeepSeek-V4) | **3/5** | Ignored the discrepancy, treating both activation functions as generic, interchangeable non-linear layers. | ⚠️ Marginal |
| | **After**<br>(DeepSeek + Skill) | **5/5** | Logged under `Needs review`: *"Kiến trúc mạng trong PyTorch sử dụng nn.GELU() nhưng công thức toán ở phần III (IEEE Layout) lại định nghĩa ReLU"*. |  Success |
| **Task 4: Structural Response Adherence**<br>*Requirement: Strict 3-tier Markdown layout* | **Before**<br>(Pure DeepSeek-V4) | **3/5** | Generated a long, essay-style narrative review. Required the researcher to manually dissect the feedback. | ⚠️ Text-heavy |
| | **After**<br>(DeepSeek + Skill) | **5/5** | Strictly adhered to the requested Markdown format: utilized structural rules (`---`), targeted bolding, and structured inventory tables. |  Success |

### Performance Improvement Formula

Using the quantified benchmark matrix above, we can measure the net performance gain:

$$\text{Improvement Rate} = \left( \frac{\sum \text{After Scores} - \sum \text{Before Scores}}{\sum \text{Before Scores}} \right) \times 100\%$$

* **Total Before Score:** $2 + 1 + 3 + 3 = 9$
* **Total After Score:** $5 + 4 + 5 + 5 = 19$
* **Net Skill Performance Boost:** **~111.1% increase** in structural code-to-paper verification accuracy.
## Repository Structure

```
scientific-research-helper/
├── SKILL.md                              # Core skill instructions
├── scientific-research-helper.skill      # skill kit
└── references/
    ├── research-proposal-template.md    # Standard proposal structure
    ├── writing-review-checklist.md      # Section-by-section review checklist
    └── topic-idea-checklist.md          # Topic feasibility evaluation checklist

```

---

## Design Philosophy

* **Guide, don't ghostwrite.** The skill helps you think through your research — it won't write your thesis for you.
* **Ask before assuming.** When context is unclear, it asks one or two targeted questions rather than making wrong assumptions.
* **Evidence first.** For quantitative research, it always asks to verify numbers against actual outputs before giving feedback.
* **No hallucinated references.** If it can't find a source through search, it says so. It will never fabricate author names or paper titles.

---

## Contributing

Contributions are welcome and appreciated! Whether you're fixing a typo, adding support for a new research methodology, or improving an existing workflow — your help makes this skill better for everyone.

### Ways to Contribute

* **Report a bug** — Open an issue describing the problem, including the steps to reproduce it and your environment.
* **Suggest a feature** — Have an idea for a new workflow, document type, or discipline? Open an issue with the **enhancement** label.
* **Submit a pull request** — See something you can fix or improve? We'd love to review your PR.

### Step-by-Step Contribution Guide

If you'd like to code or write templates for this repository, please follow these steps:

1. **Open an issue first** — Describe what you'd like to change and why so the community can discuss it.
2. **Fork the repository** — Create your own copy of the project on GitHub.
3. **Clone your fork locally**

```bash
   git clone [https://github.com/your-username/scientific-research-helper.git](https://github.com/your-username/scientific-research-helper.git)
   cd scientific-research-helper

```

4. **Create a feature branch**

```bash
   git checkout -b feat/your-awesome-feature

```

5. **Make your changes** & follow the [Development Guidelines](https://www.google.com/search?q=%23development-guidelines) below.
6. **Commit and Push your changes**

```bash
   git add .
   git commit -m "feat: add support for qualitative narrative analysis"
   git push origin feat/your-awesome-feature

```

7. **Open a Pull Request** — Navigate to the original repository and click "New Pull Request". Reference your initial issue in the PR description.

### Development Guidelines

* **Match the existing tone** — The skill communicates with users in a structured, encouraging, and evidence-first style. New instructions should follow the same voice.
* **Preserve stage awareness** — If your contribution adds a new research stage or workflow, ensure it integrates cleanly with the existing stage system (Stages 1–6).
* **Don't break existing workflows** — Verify that your changes don't introduce regressions in the file review, writing plan, or literature search features.
* **Document your additions** — If you add new references or templates to the `references/` directory, include a brief header explaining their purpose.

### Code of Conduct

This project adheres to a simple standard: **be respectful and constructive**. Harassment, personal attacks, or unprofessional behavior will not be tolerated. All interactions — whether in issues, pull requests, or discussions — should foster a welcoming and collaborative environment.

---

## License

MIT License — free to use, modify, and distribute.

