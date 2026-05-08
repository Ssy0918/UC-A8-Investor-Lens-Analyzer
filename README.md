# UC-A8 Investor Lens Analyzer

A multi-phase Python/LLM project that analyzes public companies through the investment frameworks of legendary investors. The project converts investor letters, memos, and interviews into structured **Investor DNA** documents, then applies those frameworks to company-level analysis, validation tests, and multi-investor comparison reports.

---

## 1. Project Overview

The core idea is to answer questions like:

- How would Warren Buffett evaluate Apple, Costco, or NVIDIA?
- Would Howard Marks pass or reject a company based on risk, cycles, and market psychology?
- How do different investors disagree on the same company?
- Can an investor framework predict known holdings and obvious mismatches?

The project is designed as a learning and analysis tool rather than a stock recommendation engine. It helps users stress-test an investment idea using multiple documented investor styles.

---

## 2. Project Goals

The project has three main goals:

1. **Investor Framework Extraction**  
   Build structured profiles of investors from their original letters, memos, or writings.

2. **Company Analysis Through Investor Lenses**  
   Apply one investor's framework to a company or opportunity and generate a detailed written analysis.

3. **Validation and Comparison**  
   Test whether the framework produces reasonable verdicts for known positions and known passes, then compare multiple investor lenses on the same company.

---

## 3. Current Project Structure

The project is organized by workflow stage. Output files follow reusable naming patterns rather than being tied to one fixed company or investor.

```text
UC-A8 Investor Lens Analyzer/
│
├── Code/
│   ├── investor_dna.ipynb
│   ├── investor_analysis.ipynb
│   ├── investor_validation.ipynb
│   └── investor_comparison.ipynb
│
├── Investor DNA/
│   ├── {investor_name}_dna.md
│   ├── {investor_name}_evidence.csv
│   └── {investor_name}_evidence.json
│
├── Investor Analysis/
│   └── {investor_name}_{ticker}_phase2_analysis.md
│
├── Validation/
│   ├── {investor_name}_validation_results.csv
│   └── {investor_name}_validation_summary.json
│
├── Comparison/
│   ├── {ticker}_comparison_{analysis_date}.md
│   └── {ticker}_verdicts_{analysis_date}.csv
│
├── README.md
├── instructions.md
└── source file.txt
```

Example placeholders:

- `{investor_name}`: `warren_buffett`, `howard_marks`, `peter_lynch`, `nick_sleep`
- `{ticker}`: `aapl`, `nvda`, `cost`, `jpm`
- `{analysis_date}`: `2026-05-07`


## 4. Main Notebooks

### 4.1 `investor_dna.ipynb` — Phase 1: Investor DNA

This notebook creates the foundational investor framework.

It performs the following steps:

1. Select one investor from the investor registry.
2. Download or load the investor source PDF.
3. Extract text from the PDF.
4. Clean and chunk the extracted text.
5. Select evidence passages based on investor-specific keyword hints.
6. Use the LLM to synthesize an **Investor DNA** Markdown document.
7. Save structured evidence in `.json` and `.csv` formats.

Main outputs:

```text
Investor DNA/{investor_name}_dna.md
Investor DNA/{investor_name}_evidence.json
Investor DNA/{investor_name}_evidence.csv
```

Example:

```text
Investor DNA/warren_buffett_dna.md
Investor DNA/warren_buffett_evidence.json
Investor DNA/warren_buffett_evidence.csv
```

---

### 4.2 `investor_analysis.ipynb` — Phase 2: Single-Investor Company Analysis

This notebook applies one investor's DNA to one target company.

It performs the following steps:

1. Select an investor.
2. Enter company information such as company name, ticker, current price, market cap, and business description.
3. Load the selected investor's DNA and evidence files.
4. Ask the LLM to evaluate the company using that investor's style.
5. Save a detailed Markdown analysis.

Main output:

```text
Investor Analysis/{investor_name}_{ticker}_phase2_analysis.md
```

Example:

```text
Investor Analysis/warren_buffett_aapl_phase2_analysis.md
```

The output includes:

- Initial screen
- What the investor would like
- What the investor would worry about
- Key questions the investor would ask
- Upside/downside framing
- Deal breakers or edge cases
- Likely verdict
- Confidence calibration

---

### 4.3 `investor_validation.ipynb` — Phase 3: Validation

This notebook tests whether each investor DNA behaves consistently with known examples.

It performs the following steps:

1. Select one investor.
2. Load that investor's DNA and evidence files.
3. Run the framework against known positions and known passes.
4. Classify each output into one of the allowed verdict labels.
5. Compare the generated verdict with the expected result.
6. Save both detailed validation results and a summary file.

Main outputs:

```text
Validation/{investor_name}_validation_results.csv
Validation/{investor_name}_validation_summary.json
```

Example:

```text
Validation/howard_marks_validation_results.csv
Validation/howard_marks_validation_summary.json
```

Allowed verdict classes:

```text
STRONG BUY
INTERESTED
WATCHLIST
PASS
HARD PASS
```

---

### 4.4 `investor_comparison.ipynb` — Phase 4: Multi-Investor Comparison

This notebook runs one target company through multiple investor lenses at the same time.

It performs the following steps:

1. Select active investors.
2. Enter the target company information.
3. Load all selected investor DNA and evidence files.
4. Generate a quick verdict from each investor perspective.
5. Create a comparison table.
6. Generate a synthesis section covering consensus, disagreement, and key insight.
7. Save a full Markdown report and a structured CSV verdict table.

Main outputs:

```text
Comparison/{ticker}_comparison_{analysis_date}.md
Comparison/{ticker}_verdicts_{analysis_date}.csv
```

Examples:

```text
Comparison/nvda_comparison_2026-05-08.md
Comparison/nvda_verdicts_2026-05-08.csv
```

---

## 5. Current Investor Coverage

The current implementation focuses on four working investor lenses:

| Investor | Style | Current Status |
|---|---|---|
| Warren Buffett | Quality Compounder | Working |
| Howard Marks | Credit/Cycles | Working |
| Peter Lynch | Value/Growth | Working |
| Nick Sleep | Value/Distressed / Quality Compounder Elements | Working |
| Seth Klarman | Value/Distressed | Registry exists, but source PDF may return HTTP 403 in Colab |

The original project specification also discusses Bill Ackman and George Soros as potential lenses, but source PDFs are lacking, can be added when known pdf link later.

---

## 6. Source Materials

The project uses public investor letter or memo compilations as source material.

Current source links include:

| Investor | Source |
|---|---|
| Howard Marks | Oaktree memo collection |
| Warren Buffett | Berkshire / Buffett letter compilation |
| Seth Klarman | Baupost letter compilation |
| Peter Lynch | Fort Worth investor letter collection |
| Nick Sleep | Nomad Investment Partnership letter collection |

The source URLs are listed in `source file.txt` and in the investor registry inside `investor_dna.ipynb`.

---

## 7. Environment and Dependencies

The notebooks are designed to run in Google Colab with Google Drive mounted.

### Core Python packages

```python
pypdf
requests
google-genai
pandas
pathlib
json
re
time
```

### LLM provider

The current notebook setup uses Google's Gemini / Vertex AI workflow through:

```python
from google import genai
```

A GPT-4-class or Claude-class model can also be used conceptually, but the current notebook code is written around the Google GenAI client.

---

## 8. Google Drive Setup

The expected base directory is:

```text
/content/drive/MyDrive/UC-A8 Investor Lens Analyzer
```

The notebooks save outputs into subfolders under this base directory:

```text
Investor DNA/
Investor Analysis/
Validation/
Comparison/
```

In Colab, mount Google Drive first:

```python
from google.colab import drive
drive.mount("/content/drive")
```

If Drive has already been mounted and causes an error, use:

```python
drive.mount("/content/drive", force_remount=True)
```

---

## 9. How to Run the Project

### Step 1: Generate Investor DNA

Open:

```text
Code/investor_dna.ipynb
```

Change:

```python
ACTIVE_INVESTOR = "warren_buffett"
```

Run the notebook.

Repeat this step for each investor:

```python
ACTIVE_INVESTOR = "howard_marks"
ACTIVE_INVESTOR = "peter_lynch"
ACTIVE_INVESTOR = "nick_sleep"
```

After this step, confirm that the `Investor DNA/` folder contains `.md`, `.json`, and `.csv` files for each investor.

---

### Step 2: Run Single-Investor Company Analysis

Open:

```text
Code/investor_analysis.ipynb
```

Edit:

```python
ACTIVE_INVESTOR = "warren_buffett"

COMPANY_NAME = "Apple Inc."
TICKER = "AAPL"
CURRENT_PRICE = "$287.42"
MARKET_CAP = "$4.22 trillion"
TARGET_DESCRIPTION = """
Apple is a global consumer technology company with strong hardware,
software, services, brand loyalty, and ecosystem advantages.
"""
```

Run the notebook.

The output will be saved as:

```text
Investor Analysis/{investor_name}_{ticker}_phase2_analysis.md
```

Example:

```text
Investor Analysis/warren_buffett_aapl_phase2_analysis.md
```

Use this notebook when you want a detailed report from one investor's perspective.

---

### Step 3: Run Validation Tests

Open:

```text
Code/investor_validation.ipynb
```

Change the active investor, for example:

```python
ACTIVE_INVESTOR = "howard_marks"
```

Run the notebook.

The validation notebook compares the model's verdicts against a set of expected examples, usually including companies or situations that should fit the investor and companies or situations that should not fit the investor.

The output will be saved as:

```text
Validation/{investor_name}_validation_results.csv
Validation/{investor_name}_validation_summary.json
```

Use the CSV file to inspect each individual test case. Use the JSON summary to quickly check the overall validation result.

---

### Step 4: Run Multi-Investor Comparison

Open:

```text
Code/investor_comparison.ipynb
```

Edit the target company information:

```python
COMPANY_NAME = "NVIDIA Corporation"
TICKER = "NVDA"
CURRENT_PRICE = "$211.50"
MARKET_CAP = "$5.14 trillion"

TARGET_DESCRIPTION = """
NVIDIA is a leading semiconductor company focused on GPUs, accelerated computing,
AI infrastructure, data center chips, gaming GPUs, and related software platforms.
"""
```

Run the notebook.

The comparison output will be saved as:

```text
Comparison/{ticker}_comparison_{analysis_date}.md
Comparison/{ticker}_verdicts_{analysis_date}.csv
```

Use the Markdown report for the written comparison and the CSV file for the structured verdict table.

---

## 10. Output File Guide

### Investor DNA outputs

```text
{investor_name}_dna.md
```

A complete written framework for one investor, including philosophy, buy criteria, red flags, risk management, selling discipline, quotes, and historical examples.

```text
{investor_name}_evidence.csv
{investor_name}_evidence.json
```

Structured evidence extracted from the source material. These files support later analysis and quote grounding.

### Investor Analysis outputs

```text
{investor_name}_{ticker}_phase2_analysis.md
```

A full company analysis from one investor's perspective. This is the main individual analysis report.

### Validation outputs

```text
{investor_name}_validation_results.csv
```

Detailed validation cases and model verdicts.

```text
{investor_name}_validation_summary.json
```

Summary metrics for one investor's validation run.

### Comparison outputs

```text
{ticker}_comparison_{analysis_date}.md
```

Full multi-investor comparison report.

```text
{ticker}_verdicts_{analysis_date}.csv
```

Structured comparison table containing each investor's initial screen, key appeal, key concern, and likely verdict.

---

## 11. Verdict Labels

The project standardizes final outputs into five labels:

| Label | Meaning |
|---|---|
| `STRONG BUY` | Very strong fit with the investor's framework |
| `INTERESTED` | Attractive enough for deeper research or possible position building |
| `WATCHLIST` | Interesting, but waiting for better price, more evidence, or a specific condition |
| `PASS` | Does not fit the investor's framework well enough |
| `HARD PASS` | Clear disqualifying red flags |

For validation and comparison, free-form LLM responses are mapped back into these standardized categories so results can be compared across investors.

---

## 12. Recommended Workflow

A clean run should follow this order:

1. Run `investor_dna.ipynb` for each investor.
2. Check that every selected investor has a DNA Markdown file and evidence files.
3. Run `investor_analysis.ipynb` for single-investor company reports.
4. Run `investor_validation.ipynb` to test whether each investor framework behaves reasonably.
5. Run `investor_comparison.ipynb` to compare multiple investor lenses on the same target company.
6. Review the Markdown outputs and CSV outputs in Google Drive.

The notebooks depend on earlier outputs. For example, analysis, validation, and comparison require the Investor DNA files to already exist.

---

## 13. How to Add a New Investor

To add another investor lens:

1. Add the investor to the investor registry in `investor_dna.ipynb`.
2. Provide the investor name, slug, style, core framework, PDF file name, source URL, and emphasis terms.
3. Run `investor_dna.ipynb` to create the new DNA and evidence files.
4. Confirm that the following files are created:

```text
Investor DNA/{new_investor_name}_dna.md
Investor DNA/{new_investor_name}_evidence.csv
Investor DNA/{new_investor_name}_evidence.json
```

5. Add the same investor slug to the active investor list in the analysis, validation, or comparison notebook if needed.
6. Run validation examples before relying on the new lens for comparison.

Good new investors should have enough public source material to support quotes and repeated patterns. If source material is thin, the generated DNA may become too generic.

---

## 14. Known Limitations

- The project depends on the quality of extracted PDF text. Some PDFs have formatting, encoding, or layout issues.
- Investor writings may not reveal the investor's full decision process.
- Some investors changed their style over time, so one static DNA document may simplify their evolution.
- Current company descriptions are manually entered, so analysis quality depends heavily on the target description.
- The project does not automatically pull current financial statements, valuation multiples, SEC filings, or live market data.
- LLM outputs can vary between runs, especially in verdict classification and wording.
- Validation is directional, not a formal proof that the model can predict an investor's real decisions.

---

## 15. Future Improvements

Potential next steps include:

- Build a simple web interface where users can select investor, company, and LLM provider.
- Allow users to upload their own investor PDFs.
- Add support for OpenAI, Claude, and other LLM APIs in addition to Gemini.
- Add automatic financial data retrieval for company fundamentals and valuation multiples.
- Add RAG-based quote retrieval for stronger citation grounding.
- Expand the investor universe to include activist, macro, growth, and quantitative investors.
- Improve validation with larger known-position and known-pass datasets.
- Export final reports to PDF or HTML.

---

## 16. Project Status

Current working components:

- Investor DNA generation
- Single-investor company analysis
- Validation testing
- Multi-investor comparison
- Google Drive output organization

Current working investor lenses:

- Warren Buffett
- Howard Marks
- Peter Lynch
- Nick Sleep

---

## 17. Important Notes

This project is for analytical purposes only. The generated reports should not be treated as investment advice. The model applies documented investor frameworks to user-provided company descriptions, but it does not replace full due diligence, financial modeling, or professional judgment.

Before using any output in a presentation or report, manually check:

- Whether the source quote is relevant
- Whether the verdict logically follows from the investor framework
- Whether the company description is accurate and current
- Whether the analysis reflects the intended investor style rather than generic finance language
