# Deep Research - Reference Documentation

This document provides comprehensive methodology details, advanced techniques, and background on the Deep Research skill implementation.

## Table of Contents

1. [Graph of Thoughts Framework](#graph-of-thoughts-framework)
2. [Advanced Research Methodologies](#advanced-research-methodologies)
3. [User Interaction Examples](#user-interaction-examples)
4. [Source Verification Protocol](#source-verification-protocol)
5. [Agent Prompt Templates](#agent-prompt-templates)
6. [Tool Usage Guidelines](#tool-usage-guidelines)
7. [Troubleshooting](#troubleshooting)

---

## Graph of Thoughts Framework

### What is Graph of Thoughts?

Graph of Thoughts (GoT) is an advanced reasoning framework where:
- **Thoughts = Nodes**: Each research finding or synthesis is a node in a graph
- **Edges = Dependencies**: Connect parent thoughts to child thoughts
- **Transformations**: Operations that create, merge, or improve thoughts
- **Scoring**: Every thought is evaluated 0-10 for quality
- **Pruning**: Low-scoring branches are abandoned
- **Frontier**: Active nodes available for expansion

### Why GoT for Research?

Traditional linear research follows a single path. GoT enables:
1. **Parallel Exploration**: Multiple research angles simultaneously
2. **Quality Optimization**: Scores guide which paths to pursue
3. **Backtracking**: Abandon poor paths for better alternatives
4. **Synthesis**: Combine best findings from multiple branches
5. **Transparency**: Complete reasoning graph is preserved

### GoT Operations

#### Generate(k)
Create k new thoughts from a parent thought.

**Example:**
- Parent: "Research AI in healthcare"
- Generate(3) creates:
  - Branch 1: Clinical diagnosis applications
  - Branch 2: Drug discovery and development
  - Branch 3: Hospital operations and efficiency

#### Aggregate(k)
Merge k thoughts into one stronger unified thought.

**Example:**
- Input: 3 research findings about AI diagnosis accuracy
- Output: Comprehensive synthesis resolving contradictions

#### Refine(1)
Improve a single thought without adding new major content.

**Example:**
- Input: "AI diagnosis shows 85% accuracy"
- Output: "AI diagnosis systems achieve 85% accuracy in detecting diabetic retinopathy (Google Health, 2023, JAMA), though performance varies by image quality and patient demographics"

#### Score
Evaluate thought quality (0-10) based on:
- Citation density and accuracy
- Source credibility
- Claim verification
- Comprehensiveness
- Logical coherence

#### KeepBestN(n)
Prune to keep only top n nodes per level.

**Example:**
- 5 research paths with scores: 8.2, 6.1, 9.1, 5.8, 7.4
- KeepBest3: Retains 9.1, 8.2, 7.4

### GoT Research Workflow

```
Iteration 1: Initialize and Explore
├── Root: "Research [topic]"
├── Generate(3) → 3 parallel agents
├── Results: 3 thoughts with scores
└── Frontier: Top 2 thoughts

Iteration 2: Deepen Best Paths
├── Best thought: Generate(3) for deeper exploration
├── Medium thought: Generate(2)
├── Results: 5 new thoughts
└── Frontier: Top 3 thoughts

Iteration 3: Aggregate Strong Branches
├── Aggregate(3) → Merge best findings
├── Score: 9.3 (exceeds threshold)
└── Proceed to refinement

Iteration 4: Final Polish
├── Refine(1) → Enhance clarity
├── Final score: 9.5
└── Output: Best path becomes research report
```

---

## Advanced Research Methodologies

### Chain-of-Density (CoD) Summarization

Iteratively increase information density while maintaining clarity:

**Pass 1 (Low Density):**
"AI is used in healthcare for various applications."

**Pass 2 (Medium Density):**
"AI is used in healthcare for clinical diagnosis, drug discovery, and operational efficiency."

**Pass 3 (High Density):**
"AI applications in healthcare include clinical diagnosis (85% accuracy in diabetic retinopathy detection), drug discovery (40% faster target identification), and operational efficiency (20% reduction in wait times)."

**Pass 4 (Maximum Density):**
"AI healthcare applications: clinical diagnosis achieves 85% accuracy in diabetic retinopathy (Google Health, JAMA 2023), drug discovery accelerates target identification by 40% (Atomwise, Nature 2023), operational efficiency reduces ED wait times by 20% (Mayo Clinic, 2023)."

### Chain-of-Verification (CoVe)

Prevent hallucinations through systematic verification:

1. **Generate Initial Findings**
   - "AI diagnosis systems are highly accurate"

2. **Create Verification Questions**
   - What is the specific accuracy rate?
   - What medical conditions were tested?
   - What studies support this claim?
   - Are there any contradictory findings?

3. **Search for Evidence**
   - WebSearch for each verification question
   - Extract data from authoritative sources
   - Note any conflicting information

4. **Revise Findings**
   - "AI diagnosis systems achieve 85-95% accuracy for diabetic retinopathy (Google Health, 2023), but only 70-75% for pneumonia detection (Stanford, 2023)"

5. **Repeat Until Verified**
   - Continue until all claims have supporting evidence

### ReAct Pattern (Reason + Act)

Iterative reasoning and action loop:

```
Loop:
  1. REASON: "I need to understand current AI healthcare adoption rates"
  2. ACT: WebSearch("AI healthcare adoption rates 2024")
  3. OBSERVE: "Found report showing 35% hospital adoption"
  4. REASON: "Need to verify this with multiple sources"
  5. ACT: WebSearch("healthcare AI adoption statistics 2024")
  6. OBSERVE: "Second source confirms 30-40% range"
  7. REASON: "Have sufficient evidence, proceed to next topic"
```

### Multi-Agent Orchestration

For complex topics, deploy specialized agent roles:

**Planner Agent:**
- Decomposes research question into subtopics
- Creates research strategy
- Defines success criteria

**Search Agents (3-5):**
- Execute queries for specific subtopics
- Retrieve and filter sources
- Extract relevant information

**Synthesis Agents (1-2):**
- Combine findings from multiple sources
- Resolve contradictions
- Create coherent narratives

**Critic Agent:**
- Fact-checks all claims
- Verifies citation accuracy
- Identifies gaps or weaknesses

**Editor Agent:**
- Polishes final output
- Ensures consistent style
- Formats bibliography

---

## User Interaction Examples

### Example 1: Medical Research

**User:** "I need research on CRISPR gene editing safety"

**Assistant:** "I'll help you research CRISPR gene editing safety. Let me ask some questions to ensure I deliver exactly what you need:

1. **Specific Focus:** What aspects of CRISPR safety interest you most?
   - Clinical trial safety data
   - Off-target effects and mechanisms
   - Long-term safety concerns
   - Ethical and regulatory considerations
   - All of the above

2. **Output Format:** What deliverable would be most useful?
   - Comprehensive report (20-30 pages)
   - Executive summary (3-5 pages)
   - Technical analysis for researchers
   - Risk assessment for stakeholders

3. **Scope:** Any specific constraints?
   - Focus on human applications vs. all uses?
   - Time period (last 5 years, all research)?
   - Specific CRISPR variants (Cas9, Cas12, base editing)?

4. **Audience:** Who will be reading this?
   - Research scientists
   - Biotech executives
   - Regulatory bodies
   - General educated audience"

**User:** "Focus on human clinical applications, comprehensive report, last 3 years, audience is biotech executives considering investment."

**Assistant:** "Perfect! A few more clarifications:

5. **Data Requirements:** Should I include:
   - Clinical trial outcomes and adverse events?
   - Comparison with alternative gene therapies?
   - Market potential and competitive landscape?
   - Regulatory pathway analysis?

6. **Deliverable Structure:**
   - Folder structure with supporting documents?
   - Include raw data files?
   - Visual elements (timelines, comparison tables, risk matrices)?

7. **Source Preferences:**
   - Peer-reviewed journals only?
   - Include preprints and conference presentations?
   - Industry reports acceptable?"

**User:** "Yes to all data requirements, folder structure with visuals, peer-reviewed + credible industry reports."

**Assistant:** "Excellent! Here's my research plan:

**Research Plan: CRISPR Gene Editing Safety**

**Subtopics:**
1. Clinical trial safety data and adverse events (2022-2024)
2. Off-target effects: mechanisms, detection, and mitigation
3. Long-term safety considerations and monitoring
4. Regulatory landscape and approval pathways
5. Competitive analysis vs. alternative gene therapies

**Multi-Agent Deployment:**
- Agent 1: Clinical trial safety data from ClinicalTrials.gov, NEJM, Nature Medicine
- Agent 2: Off-target effects research from peer-reviewed journals
- Agent 3: Long-term safety studies and expert opinions
- Agent 4: FDA/EMA regulatory documents and approval pathways
- Agent 5: Market analysis and competitive landscape
- Agent 6: Cross-verification and fact-checking

**Output Structure:**
```
CRISPR_Safety_Research/
├── README.md
├── 01_Executive_Summary.md
├── 02_Full_Report.md
├── 03_Clinical_Trial_Data/
├── 04_Safety_Analysis/
├── 05_Regulatory_Landscape/
├── 06_Market_Competitive_Analysis/
├── 07_Data/
├── 08_Visuals/
└── 09_Sources/
```

Shall I proceed with this research plan?"

### Example 2: Technology Analysis

**User:** "Deep research quantum computing current state"

**Assistant:** "I'll conduct deep research on the current state of quantum computing. Let me clarify your needs:

1. **Specific Focus:** Which aspects are most important?
   - Technical capabilities and limitations
   - Leading companies and their approaches
   - Practical applications and use cases
   - Timeline to quantum advantage
   - Investment landscape
   - All of the above

2. **Output:** What would be most useful?
   - Executive summary (3-5 pages)
   - Comprehensive report (25-30 pages)
   - Technical deep-dive
   - Market analysis

3. **Audience:**
   - Technical team
   - Business executives
   - Investors
   - General audience

4. **Special Requirements:**
   - Comparison of different quantum approaches (gate-based, annealing, etc.)?
   - Analysis of quantum vs. classical performance?
   - Timeline projections?"

---

## Source Verification Protocol

### Credibility Assessment Framework

#### Primary Source Hierarchy (Highest to Lowest):

1. **Tier 1: Peer-Reviewed Research**
   - Systematic reviews and meta-analyses
   - Randomized controlled trials
   - Published in high-impact journals (Nature, Science, Cell, NEJM, etc.)
   - Verification: Check journal impact factor, review process

2. **Tier 2: Clinical Guidelines & Government Reports**
   - NIH, CDC, FDA, WHO guidelines
   - Government research reports
   - Professional organization consensus statements
   - Verification: Check authoring organization credentials

3. **Tier 3: Academic Publications**
   - Cohort studies, case-control studies
   - Technical reports from universities
   - Conference proceedings (peer-reviewed)
   - Verification: Check institution reputation, peer review status

4. **Tier 4: Industry Reports**
   - Reports from established research firms (Gartner, Forrester, McKinsey)
   - Industry whitepapers with clear methodology
   - Technical documentation from reputable companies
   - Verification: Check methodology transparency, conflicts of interest

5. **Tier 5: News and Media**
   - Science journalism from reputable outlets
   - Industry news from specialized publications
   - Company announcements (with skepticism)
   - Verification: Trace back to original source

### Red Flags Checklist

**Reject or flag sources with:**
- [ ] No identifiable author or organization
- [ ] Publication date missing or >5 years old (for rapidly evolving fields)
- [ ] Broken links or inaccessible content
- [ ] Extraordinary claims without extraordinary evidence
- [ ] No peer review for scientific claims
- [ ] Obvious conflicts of interest not disclosed
- [ ] Published in predatory journals (check Beall's List)
- [ ] Retracted (check RetractionWatch.com)
- [ ] Self-published with no external validation
- [ ] Anonymous or pseudonymous authorship

### Cross-Reference Requirements

**For critical claims, require:**
- 2+ independent sources from different organizations
- At least 1 peer-reviewed source for scientific claims
- Original research paper, not secondary reporting
- Consistent findings across sources

**When sources disagree:**
1. Note the discrepancy explicitly
2. Assess relative credibility of sources
3. Look for additional sources to resolve
4. If unresolvable, present both views with context
5. State uncertainty clearly

### Citation Verification Checklist

Before finalizing research, verify:
- [ ] Every factual claim has a citation
- [ ] All URLs are accessible and correct
- [ ] Citations match the claims they support
- [ ] Direct quotes are verbatim
- [ ] Statistics include sample sizes and confidence intervals
- [ ] Dates are accurate and recent enough
- [ ] Authors/organizations are correctly attributed
- [ ] DOIs resolve to correct papers

---

## Agent Prompt Templates

### General Web Research Agent

```
Research [SPECIFIC_ASPECT] of [MAIN_TOPIC]

Your objective: [CLEAR_GOAL]

Tools to use:
1. WebSearch - Start with broad queries, then refine
   - Initial query: "[TOPIC] [ASPECT] latest research"
   - Follow-up: "[TOPIC] [ASPECT] statistics data"
   - Verification: "[TOPIC] [ASPECT] expert opinion"

2. WebFetch - Extract content from top 3-5 URLs
   - Focus on: Key findings, data points, expert quotes
   - Note: Publication date, author credentials

3. If sites require JavaScript: Use mcp__puppeteer__

Research requirements:
- Find 5-7 authoritative sources
- Prioritize sources from last 2 years
- Include diverse perspectives
- Note any contradictions

For every claim, document:
1. Direct quote or specific data
2. Author/organization
3. Publication year
4. Full title
5. Direct URL
6. Confidence rating: High/Medium/Low

Output format:
## [Aspect Title]

[200-400 word summary with inline citations]

Key findings:
- [Finding 1] (Source, Year)
- [Finding 2] (Source, Year)
- [Finding 3] (Source, Year)

Sources:
1. [Full citation]
2. [Full citation]
...
```

### Academic/Technical Research Agent

```
Find technical and academic information about [TOPIC_ASPECT]

Your objective: Gather peer-reviewed research and technical specifications

Search strategy:
1. WebSearch queries:
   - "[TOPIC] peer-reviewed research"
   - "[TOPIC] systematic review meta-analysis"
   - "[TOPIC] technical specifications standards"
   - "site:arxiv.org [TOPIC]"
   - "site:pubmed.gov [TOPIC]"

2. Prioritize:
   - Peer-reviewed journals
   - Academic preprints (arXiv, bioRxiv)
   - Technical standards documents
   - University research publications

3. For each source, extract:
   - Research methodology
   - Sample sizes and statistical power
   - Key results with p-values/confidence intervals
   - Limitations acknowledged by authors
   - Conflicts of interest

Citation requirements:
- Include DOI or arXiv ID
- Note journal impact factor if available
- Specify study type (RCT, cohort, case study, etc.)
- Include sample size for all studies

Output format:
## Technical Analysis: [Topic]

### Current Research Landscape
[Overview paragraph]

### Key Studies
1. **[Study Title]** (Authors, Journal, Year)
   - Methodology: [Brief description]
   - Sample: N=[number], [demographics]
   - Findings: [Key results with statistics]
   - Limitations: [Notable limitations]
   - DOI: [link]

2. [Additional studies...]

### Technical Specifications
[If applicable]

### Knowledge Gaps
[Areas lacking research]

### Sources
[Full bibliography]
```

### Verification/Fact-Checking Agent

```
Verify the following research findings about [TOPIC]:

Claims to verify:
1. [CLAIM_1]
2. [CLAIM_2]
3. [CLAIM_3]
...

For each claim:

1. Search for supporting evidence:
   - WebSearch: "[claim] evidence study"
   - WebSearch: "[claim] statistics data"
   - Look for original sources, not secondary reporting

2. Search for contradictory evidence:
   - WebSearch: "[claim] criticism debunked"
   - WebSearch: "[claim] alternative view"
   - Check for retractions or corrections

3. Assess source credibility:
   - Is it peer-reviewed?
   - Who are the authors?
   - Any conflicts of interest?
   - How recent is the information?

4. Rate confidence:
   - **High**: 3+ independent peer-reviewed sources agree
   - **Medium**: 2 sources agree, or single high-quality source
   - **Low**: Single source, or conflicting information

Output format:
## Verification Report: [Topic]

### Claim 1: [Claim text]
- **Confidence:** [High/Medium/Low]
- **Supporting Evidence:**
  - [Source 1] confirms [specific finding]
  - [Source 2] reports [specific data]
- **Contradictory Evidence:**
  - [If any]
- **Assessment:** [Final judgment]

### Claim 2: [Claim text]
...

### Red Flags Identified:
[Any unreliable sources or unsupported claims]

### Recommendations:
[Suggestions for strengthening claims]
```

### Synthesis Agent

```
Synthesize research findings from multiple agents into a coherent narrative for [TOPIC]

Input findings:
[AGENT_1_FINDINGS]
[AGENT_2_FINDINGS]
[AGENT_3_FINDINGS]
...

Your tasks:

1. Identify key themes across all findings
2. Organize information logically:
   - Introduction and context
   - Current state/evidence
   - Challenges and limitations
   - Future directions
   - Conclusions

3. Resolve contradictions:
   - Compare conflicting information
   - Assess relative source credibility
   - Present balanced view or explain discrepancy

4. Strengthen weak areas:
   - Note where evidence is limited
   - Identify gaps in current knowledge
   - Suggest areas for caution

5. Ensure all claims retained from original findings have citations

6. Create executive summary (200-300 words)

Output format:
## Executive Summary
[Key findings and conclusions]

## Introduction
[Context and background]

## Section 1: [Theme]
[Integrated findings with citations]

## Section 2: [Theme]
[Integrated findings with citations]

...

## Discussion
[Synthesis and interpretation]

## Conclusions
[Main takeaways]

## Limitations
[Acknowledged gaps and uncertainties]

## References
[Complete bibliography]
```

---

## Tool Usage Guidelines

### WebSearch Best Practices

**Query formulation:**
```
Good: "AI healthcare diagnosis accuracy peer-reviewed 2024"
Better: "AI medical diagnosis accuracy sensitivity specificity 2024"
Best: Multiple queries:
  - "AI diagnosis accuracy systematic review 2024"
  - "machine learning medical diagnosis performance metrics"
  - "deep learning healthcare diagnostic accuracy"
```

**Domain filtering:**
```
Use allowed_domains for authoritative sources:
- Academic: ["scholar.google.com", "pubmed.ncbi.nlm.nih.gov", "arxiv.org"]
- Medical: ["nih.gov", "cdc.gov", "who.int", "bmj.com", "nejm.org"]
- Tech: ["ieee.org", "acm.org", "arxiv.org"]
```

**Query iteration:**
1. Start broad to understand landscape
2. Narrow to specific aspects
3. Search for verification
4. Look for recent updates

### WebFetch Best Practices

**Prompt formulation:**
```
Good: "Summarize this article"
Better: "Extract key findings about AI diagnosis accuracy with statistics"
Best: "Extract:
1. Specific accuracy percentages with confidence intervals
2. Study methodology and sample size
3. Comparison to human performance
4. Limitations acknowledged
5. Full citation information"
```

**Content extraction priorities:**
1. Quantitative data (statistics, percentages, counts)
2. Direct quotes from experts
3. Methodology details
4. Limitations and caveats
5. Publication metadata (date, authors, journal)

### MCP Puppeteer Usage

**When to use:**
- Content requires JavaScript rendering
- Interactive visualizations or charts
- Paywalled content that needs navigation
- Dynamic data loading
- Form submission required

**Example workflow:**
```
1. mcp__puppeteer__puppeteer_navigate
   - URL: [target page]

2. mcp__puppeteer__puppeteer_screenshot
   - Capture rendered content

3. mcp__puppeteer__puppeteer_evaluate
   - Extract specific DOM elements
   - Run JavaScript to access data

4. Save extracted data to RESEARCH folder
```

---

## Troubleshooting

### Issue: Sources lack sufficient detail

**Solution:**
- Use more specific WebFetch prompts
- Request exact data points needed
- Try alternative search queries
- Use mcp__puppeteer__ for dynamic content

### Issue: Conflicting information across sources

**Solution:**
- Assess relative credibility of sources
- Look for additional sources to resolve
- Check publication dates (newer may supersede older)
- Present both views with context if unresolvable

### Issue: Can't find peer-reviewed sources

**Solution:**
- Adjust search queries with academic terms
- Use domain filtering for academic sites
- Expand time window for search
- Consider if topic is too new for peer review
- Use credible industry reports as alternative

### Issue: Agent outputs exceed context limits

**Solution:**
- Break research into smaller subtopics
- Have agents focus on specific aspects
- Split final report into multiple files
- Use summary → detail hierarchy

### Issue: Citations not matching claims

**Solution:**
- Re-verify each source
- Use verification agent to check
- Request more specific extractions
- May need to remove unsupported claims

### Issue: Research taking too long

**Solution:**
- Reduce number of subtopics
- Deploy fewer agents
- Set clearer scope boundaries
- Use faster models for initial exploration
- Save detailed analysis for critical areas

### Issue: Output lacks visual elements

**Solution:**
- Request specific data formats (CSV, JSON)
- Use Python/Bash to generate charts
- Create comparison tables in markdown
- Screenshot relevant charts from sources
- Note limitations if visualization not possible

---

## Additional Resources

### Research Methodology References
- Deep research playbook: See `deepresearchprocess.md` in repository
- Question refinement: See `Deep Research Question Generator System Prompt.md`
- Example outputs: See `examples/` directory

### Related Documentation
- Main skill instructions: `SKILL.md`
- Installation guide: `README.md`
- Repository: https://github.com/shafra-com/Claude-Code-Deep-Research

### Credits
This deep research methodology is inspired by:
- OpenAI's deep research approaches
- Google's Gemini Deep Research
- Graph of Thoughts framework (Yao et al.)
- Chain-of-Verification techniques
- Multi-agent orchestration patterns

---

*Last updated: 2025-11-05*
