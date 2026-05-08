# Investor Lens Analyzer

Assigned To: Shuyan Sun
ID: UC-A8
Last Updated: April 27, 2026 12:31 PM
Priority: High
Spec Status: Yes
Status: In Progress
Team: Alpha (Data)

# Section A: Specification *(Filled by Alban)*

---

### 1. Objective

Analyze investment opportunities through the lens of legendary investors by synthesizing their published letters, memos, and interviews into coherent investment frameworks. When given a company or opportunity, produce analysis as that investor would approach it - capturing their priorities, concerns, blind spots, and decision-making patterns.

**Primary Use Cases:**

- **Learning Tool**: Understand how great investors think and what drives their decisions
- **Devil's Advocate**: Stress-test investment ideas from multiple contrasting perspectives
- **Framework Discovery**: Surface non-obvious considerations by applying different analytical lenses

**Investors to Model (5 contrasting styles):**

| Investor | Style | Core Framework |
| --- | --- | --- |
| Bill Ackman | Activist | Concentrated positions in simple, predictable, FCF-generative businesses with fixable problems |
| Howard Marks | Credit/Cycles | Second-level thinking, risk control, cycle awareness, contrarian positioning |
| Seth Klarman | Value/Distressed | Margin of safety, absolute value (not relative), patience, downside protection |
| Warren Buffett | Quality Compounder | Economic moats, exceptional management, wonderful businesses at fair prices |
| George Soros | Macro/Reflexivity | Reflexivity theory, boom/bust cycles, finding the flaw in every thesis |

---

### 2. Input

**Source Materials (per investor):**

| Source Type | Location | Priority |
| --- | --- | --- |
| Annual/Quarterly Letters | "A Letter a Day" Substack Google Drive compilations ([https://aletteraday.substack.com/p/the-archive](https://aletteraday.substack.com/p/the-archive)) | **Critical** |
| Conference Presentations | Google Drive / YouTube | Optional |
| Interviews & Speeches | YouTube, podcasts, print interviews | Optional |

**Investors with confirmed Google Drive compilations:** (Notes: currently lacking Activist & Macro/Reflexivity style investors)

- Howard Marks (Credit/Cycles)
    - [the-complete-collection](https://www.oaktreecapital.com/docs/default-source/memos/the-complete-collection.pdf)
- Warren Buffett (Quality Compounder)
    - [web_v31.pdf](https://12mv2.com/wp-content/uploads/2023/05/web_v31.pdf)
- Seth Clarman (Value/Distressed)
    - [Microsoft Word - BaupostFundLetters.docx](https://www.safalniveshak.com/wp-content/uploads/2012/09/Seth-Klarman-Baupost-Group-Letters.pdf)
- Peter Lynch (Value/Distressed)
    - [pl_fortworthcollection.pdf](https://12mv2.com/wp-content/uploads/2020/09/pl_fortworthcollection.pdf)
- Nick Sleep (Value/Distressed)
    - [Full_Collection_Nomad_Letters_.pdf](https://igyfoundation.org.uk/wp-content/uploads/2021/03/Full_Collection_Nomad_Letters_.pdf)

**End User Input at Runtime:**

1. **Investor Selection**: Which lens to apply (one or multiple)
2. **Target Opportunity**: Company ticker, situation description, or investment thesis to evaluate
3. **Optional**: Specific question, comparison mode, time horizon context

**Example Inputs:**

```
"Analyze NFLX through Ackman's lens"
"How would Buffett view META at current prices?"
"Run MSFT through the lenses of the five investors"
"Would Klarman be interested in distressed real estate right now?"

```

---

### 3. Expected Output

**Phase 1 Deliverable: Investor DNA Documents (one per investor)**

A structured framework document capturing each investor's complete analytical approach.

It could look something like the document below, but doesn’t have to! 

If you come up with a framework that is more structured / flexible for different investor types please feel free to edit 

On Point 2 “Invariable Truths” here an example of what that could look like

[Underwriting_The_Stock_Market.pdf](Investor%20Lens%20Analyzer/Underwriting_The_Stock_Market.pdf)

```
INVESTOR DNA: [Name]

1. INVESTMENT PHILOSOPHY
   - Core beliefs about markets and investing
   - What they believe their edge is
   - Time horizon and patience level
   - Views on diversification vs. concentration

2. INVARIABLE TRUTHS (Market Axioms)
   Fundamental principles the investor has identified as enduring truths about markets, business, or investing. These are structural realities they believe always hold.

   Example format:
   • "[TRUTH TITLE]"
     - Core principle: [1-2 sentence explanation]
     - Why it's invariable: [Their reasoning]
     - How they exploit it: [Practical application]
     > "[Direct quote from letters/speeches]"

   Categories to capture:
   - Market structure truths (e.g., "markets are designed to appreciate over time")
   - Human behavior truths (e.g., "fear and greed drive cycles")
   - Business economics truths (e.g., "moats erode without reinvestment")
   - Valuation truths (e.g., "entry price determines returns")
   - Risk truths (e.g., "volatility is not risk, permanent capital loss is")

   Target: 5-10 invariable truths per investor, with source citations

3. WHAT THEY LOOK FOR (Buy Criteria)
   - Business Quality: Revenue/earnings characteristics, competitive position, industry preferences
   - Management: Leadership qualities, compensation alignment, capital allocation track record
   - Valuation Approach: Absolute vs. relative, specific metrics, margin of safety definition
   - Catalysts & Timing: Catalyst requirements, patience vs. urgency

3. WHAT THEY AVOID (Red Flags)
   - Business characteristics they dislike
   - Industries they won't touch
   - Management behaviors that disqualify
   - Complexity thresholds

4. POSITION SIZING & PORTFOLIO
   - Typical and maximum position sizes
   - Scaling in/out approach
   - Number of positions typically held
   - Use of leverage

5. SELL DISCIPLINE
   - Sale triggers
   - Handling winners vs. losers
   - "Thesis broken" vs. "price down" distinction

6. RISK MANAGEMENT
   - Risk definition
   - Downside protection methods
   - Hedging approach

7. SIGNATURE PATTERNS
   - Recurring themes in best investments
   - Situations where they excel
   - Contrarian tendencies

8. KNOWN BLIND SPOTS & MISTAKES
   - Historical errors and causes
   - Self-identified weaknesses
   - Lessons learned

9. NOTABLE QUOTES
   - 10-15 representative quotes for citation in analysis

10. HISTORICAL EXAMPLES
    - 3-5 best investments with reasoning
    - 2-3 notable mistakes with lessons

```

**Phase 2 Deliverable: Analysis Output (per request)**

```
[INVESTOR NAME] ANALYSIS: [COMPANY/OPPORTUNITY]

Lens Applied: [Investor Name] | [Investment Style]
Target: [Company] ([Ticker]) | Current Price: $[X] | Market Cap: $[X]B
Analysis Date: [Date]

─────────────────────────────────────────────

INITIAL SCREEN
Would this pass [Investor]'s initial filter?
[ ] YES - Fits core criteria, worth deep investigation
[ ] MAYBE - Some appeal but significant questions
[ ] NO - Doesn't match what they look for

Reasoning: [2-3 sentences]

─────────────────────────────────────────────

WHAT [INVESTOR] WOULD LIKE
• [Positive Factor 1]
  [Explanation]
  > "[Supporting quote from letters/speeches]"

• [Positive Factor 2]
  [Explanation]
  > "[Supporting quote]"

• [Positive Factor 3]
  [Explanation]
  > "[Supporting quote]"

─────────────────────────────────────────────

WHAT [INVESTOR] WOULD WORRY ABOUT
• [Concern 1]
  [Explanation]
  > "[Supporting quote]"

• [Concern 2]
  [Explanation]
  > "[Supporting quote]"

• [Concern 3]
  [Explanation]
  > "[Supporting quote]"

─────────────────────────────────────────────

KEY QUESTIONS [INVESTOR] WOULD ASK
1. [Question reflecting their priorities]
2. [Question reflecting their concerns]
3. [Question reflecting their process]
4. [Question about risk/downside]
5. [Question about valuation/entry]

─────────────────────────────────────────────

HISTORICAL PARALLELS
Similar Investments They Made:
• [Company] ([Year]): [Brief description and relevance]
• [Company] ([Year]): [Brief description and relevance]

Similar Situations They Avoided:
• [Company/Situation]: [Why they passed]

─────────────────────────────────────────────

LIKELY VERDICT
[INVESTOR]'s Probable Conclusion:
[ ] STRONG BUY - High conviction, fits core criteria perfectly
[ ] INTERESTED - Worth building position, monitoring closely
[ ] WATCHLIST - Interesting but needs [specific condition]
[ ] PASS - Doesn't fit framework because [reason]
[ ] HARD PASS - Active red flags: [reason]

Position Sizing Estimate: [If bought, what size?]
Catalyst Dependency: [Need catalyst or buy and wait?]

─────────────────────────────────────────────

CONFIDENCE CALIBRATION
• Framework fit: [High/Medium/Low]
• Data quality: [High/Medium/Low]
• Historical precedent: [High/Medium/Low]

Caveats: [Limitations in applying this lens]

```

**Comparison Mode Output (Multiple Lenses):**

| Dimension | Ackman | Marks | Klarman | Buffett | Soros |
| --- | --- | --- | --- | --- | --- |
| Initial Screen | Pass/Fail | Pass/Fail | Pass/Fail | Pass/Fail | Pass/Fail |
| Key Appeal | [1 line] | [1 line] | [1 line] | [1 line] | [1 line] |
| Key Concern | [1 line] | [1 line] | [1 line] | [1 line] | [1 line] |
| Likely Verdict | [Verdict] | [Verdict] | [Verdict] | [Verdict] | [Verdict] |

Plus: Consensus View, Key Disagreements, Synthesis

---

### 4. Success Criteria

**Minimum Viable Output:**

- [ ]  Analysis clearly reflects the specific investor's style (not generic investment analysis)
- [ ]  At least 3 supporting quotes from actual letters/speeches per analysis
- [ ]  Historical parallels are accurate and relevant
- [ ]  Verdict is logically consistent with stated framework
- [ ]  Key questions reflect that investor's actual documented priorities

**Quality Indicators:**

- [ ]  Someone familiar with the investor would recognize the "voice"
- [ ]  Analysis surfaces non-obvious insights from the framework
- [ ]  Comparison mode reveals meaningful differences between investors
- [ ]  Framework successfully "predicts" the investor's actual positions

**Validation Method:**
Test each Investor DNA framework against:

1. **Known positions**: Does the lens say "buy" for stocks they actually own (could be confirmed by looking at 13F)?
2. **Known passes**: Does the lens say "pass" for obvious mismatches to their style?
3. **Historical examples**: Would the framework have flagged their documented mistakes?

**Validation Deliverable:**

- Test against 5 known positions per investor
- Test against 5 known passes per investor
- Document accuracy metrics and edge cases

---

### 5. Domain Context

**What Students Need to Understand:**

**Investment Styles:**

- **Activist**: Takes large positions, engages with management, pushes for changes to unlock value
- **Value/Distressed**: Buys assets below intrinsic value, often in out-of-favor or troubled situations
- **Quality Compounder**: Seeks excellent businesses that can grow earnings for decades
- **Macro**: Top-down approach, trades based on economic/geopolitical themes
- **Credit/Cycles**: Focus on risk management, understands market cycles, contrarian timing

**Key Concepts:**

- **Margin of Safety**: Buying at price below intrinsic value to protect against errors
- **Moat**: Sustainable competitive advantage (brand, network effects, switching costs, etc.)
- **FCF (Free Cash Flow)**: Cash generated after capital expenditures; what owner actually receives
- **Intrinsic Value**: Estimated true worth of business based on future cash flows
- **13F Filing**: Quarterly SEC disclosure of equity holdings for institutional managers
- **Reflexivity**: Soros's theory that market prices affect fundamentals, creating feedback loops

**Important Nuances:**

- Investors evolve over time; current thinking may differ from historical letters
- Same investor might decide differently in different market environments
- Some decisions are intuitive and not fully captured in writings
- Public letters may not reveal full thinking (especially on current positions)

---

### 6. Technical Constraints

**Required:**

- LLM API access (Claude or GPT-4 class model recommended for nuanced analysis)
- Python for orchestration and data processing
- Access to A Letter a Day Google Drive compilations

**Optional:**

- PDF parsing capability for letter extraction
- Basic web scraping for supplementary materials (YouTube transcripts, etc.)
- Vector database for RAG implementation (Pinecone, Chroma, or similar)

**Approach Options:**

| Approach | Description | Pros | Cons |
| --- | --- | --- | --- |
| **Prompt Engineering** | Curate Investor DNA doc, feed as system prompt | Consistent voice, lower latency, simpler | Limited by context window |
| **RAG-based** | Index all letters, retrieve relevant passages | Cites sources, updatable, handles more material | May feel less coherent |
| **Hybrid** | DNA doc for framework + RAG for specific quotes | Best of both worlds | More complex to build |

**Recommended approach for students:** Start with Prompt Engineering (Phase 1), then optionally add RAG for quote retrieval (Phase 2) if you feel up for the challenge on a technical level.

**Output Format:**

- PDF report for individual analyses
- CSV/structured data for validation testing
- Markdown for Notion integration

---

[Links to be added by students]

## Section B: Progress *(Filled by Students)*

### 7. Approach

*How are you solving this? Key decisions made.*

[To be filled by students]

### 8. Current Status

*Where are you now? What's working/not working?*

[To be filled by students]

### 9. Blockers

*What's preventing progress? Questions for Alban?*

[To be filled by students]

### 10. Deliverables

*Links to code, demos, documentation*

**Required Deliverables:**

- [ ]  Investor DNA Documents (5 total: Ackman, Marks, Klarman, Buffett, Soros)
- [ ]  Working prototype (takes investor + company, produces analysis)
- [ ]  Validation results (accuracy against known positions/passes)
- [ ]  Sample analyses (3 companies through all 5 lenses)
- [ ]  Documentation (usage guide, how to add new investors, limitations)