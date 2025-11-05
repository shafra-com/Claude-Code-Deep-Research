---
name: deep-research
description: Conduct comprehensive multi-agent deep research with Graph of Thoughts methodology, parallel exploration, citation tracking, and structured outputs
---

# Deep Research Skill

## Overview

This skill enables autonomous, multi-step research using Graph of Thoughts (GoT) framework, parallel agent deployment, and rigorous citation standards. It produces comprehensive, well-sourced research reports with executive summaries, data analysis, and visual elements.

## When to Use This Skill

Use this skill when the user requests:
- Deep research on any topic
- Comprehensive analysis with sources
- Multi-perspective investigation
- Literature reviews or state-of-the-art surveys
- Market research or competitive analysis
- Technical or academic research

## The 7-Phase Deep Research Process

### Phase 1: Question Scoping
**ALWAYS start by gathering requirements from the user:**

Ask the user about:
1. **Core Research Question**: Main topic and specific aspects of interest
2. **Output Requirements**: Format (report/presentation), length, file structure
3. **Scope & Boundaries**: Geographic focus, time period, industry constraints
4. **Sources & Credibility**: Preferred source types, required credibility level
5. **Deliverable Structure**: Folder organization, file formats, visual requirements
6. **Special Requirements**: Specific data needs, target audience, compliance considerations

**Do not proceed until you have clear answers to these questions.**

### Phase 2: Retrieval Planning
After gathering requirements, create a research plan:

1. Break the main question into 3-5 subtopics
2. Design multi-agent deployment strategy
3. Present the plan to user for approval
4. Use TodoWrite to track all research tasks

**Example plan structure:**
```
Research Plan: [Topic]

Subtopics:
1. Current state and trends
2. Key challenges and limitations
3. Future developments
4. Case studies and applications
5. Expert opinions and perspectives

Multi-Agent Deployment:
- Agent 1: Web research for current information
- Agent 2: Academic/technical research
- Agent 3: Case studies and real-world data
- Agent 4: Future trends and predictions
- Agent 5: Cross-verification and fact-checking

Output Structure:
RESEARCH/[topic_name]/
├── README.md
├── executive_summary.md
├── full_report.md
├── data/
├── visuals/
├── sources/
├── research_notes/
└── appendices/
```

### Phase 3: Iterative Querying (Multi-Agent Execution)

Deploy specialized research agents in parallel using Task tool:

**Agent Template:**
```
Research [specific aspect] of [main topic].

Use these tools:
1. WebSearch to find relevant sources (try multiple query variations)
2. WebFetch to extract content from promising URLs
3. If JavaScript required, use mcp__puppeteer__ for navigation

Focus on:
- Recent information (prioritize last 2 years)
- Authoritative sources
- Specific data and statistics
- Multiple perspectives

For every factual claim, provide:
- Direct quote or data point
- Author/organization name
- Publication year
- Full title
- Direct URL/DOI
- Confidence rating (High/Medium/Low)

Return structured summary with all source URLs and inline citations.
```

**Deploy 5-7 agents simultaneously** in a single response with multiple Task calls.

### Phase 4: Source Triangulation

After agents complete, verify findings:
- Compare results across multiple sources
- Validate claims with cross-references
- Handle inconsistencies and contradictions
- Assess source credibility (rate A-E)
- Use verification agent for critical claims

**Source Quality Ratings:**
- **A**: Peer-reviewed RCTs, systematic reviews, meta-analyses
- **B**: Cohort studies, case-control studies, clinical guidelines
- **C**: Expert opinion, case reports, mechanistic studies
- **D**: Preliminary research, preprints, conference abstracts
- **E**: Anecdotal, theoretical, or speculative

### Phase 5: Knowledge Synthesis

Create structured research outputs:

1. **Executive Summary** (1-2 pages)
   - Key findings
   - Main conclusions
   - Recommendations

2. **Full Report** (organized by subtopic)
   - Introduction
   - Methodology
   - Findings for each subtopic
   - Discussion
   - Conclusions
   - References

3. **Supporting Materials**
   - Data files (CSV/JSON)
   - Visualizations
   - Source bibliography
   - Research notes from agents
   - Appendices

**Break large reports into multiple files** (e.g., Full_Report_Part1.md, Full_Report_Part2.md) to avoid context limitations.

### Phase 6: Quality Assurance

Before finalizing, verify:

- [ ] Every claim has a verifiable source
- [ ] Multiple sources corroborate key findings
- [ ] Contradictions are acknowledged and explained
- [ ] Sources are recent and authoritative
- [ ] No hallucinations or unsupported claims
- [ ] Clear logical flow from evidence to conclusions
- [ ] Proper citation format throughout
- [ ] All original research tasks are completed

### Phase 7: Output & Packaging

Create all files in: `/RESEARCH/[topic_name]/`

**Standard folder structure:**
```
RESEARCH/
└── [topic_name]/
    ├── README.md (Navigation guide)
    ├── executive_summary.md
    ├── full_report.md (or split into parts)
    ├── data/
    │   ├── raw_data.csv
    │   ├── processed_data.json
    │   └── statistics_summary.md
    ├── visuals/
    │   ├── charts/
    │   └── graphs/
    ├── sources/
    │   ├── bibliography.md
    │   └── source_summaries.md
    ├── research_notes/
    │   ├── agent_1_findings.md
    │   ├── agent_2_findings.md
    │   └── synthesis_notes.md
    └── appendices/
        ├── methodology.md
        └── limitations.md
```

## Citation Requirements

**Every factual claim must include:**
1. Author/Organization
2. Publication date
3. Source title
4. Direct URL/DOI
5. Page numbers (when applicable)

**Citation format examples:**

Academic:
```
(Smith et al., 2023, p. 145)
Full: Smith, J., Johnson, K., & Lee, M. (2023). "Title." Journal, 45(3), 140-156. https://doi.org/10.xxxx/xxxxx
```

Web sources:
```
(Organization, 2024, "Section Title")
Full: Organization. (2024). "Title." Retrieved [date] from https://example.com/page
```

Direct quotes:
```
"Exact quote from source" (Author, 2023, p. XX)
```

## Graph of Thoughts Integration

For complex research, use GoT framework:

1. **Multiple Paths**: Explore different research angles in parallel
2. **Scoring**: Evaluate information quality (0-10 scale)
3. **Aggregation**: Combine best findings from multiple agents
4. **Refinement**: Improve synthesis through iterative enhancement
5. **Pruning**: Drop low-quality or redundant information

**GoT Operations:**
- **Generate(k)**: Deploy k agents exploring different angles
- **Score**: Evaluate source quality and insight value
- **Aggregate(k)**: Merge k findings into stronger synthesis
- **Refine**: Enhance clarity and completeness
- **KeepBestN(n)**: Retain only top n sources per category

## Implementation Protocol

When user requests deep research:

1. **Gather Requirements** (Phase 1)
   - Ask clarifying questions
   - Define scope and outputs
   - Get user approval before proceeding

2. **Create Research Plan** (Phase 2)
   - Break into subtopics
   - Design agent deployment
   - Create todo list with TodoWrite
   - Get user approval for plan

3. **Deploy Agents** (Phase 3)
   - Launch 5-7 specialized agents in parallel
   - Each agent focuses on specific subtopic
   - Use WebSearch, WebFetch, and MCP tools

4. **Verify & Synthesize** (Phases 4-5)
   - Cross-check findings
   - Resolve contradictions
   - Create structured outputs
   - Generate visualizations if needed

5. **Quality Check** (Phase 6)
   - Verify all citations
   - Check for completeness
   - Ensure no hallucinations
   - Mark all todos as completed

6. **Deliver** (Phase 7)
   - Save all files to RESEARCH folder
   - Create comprehensive README
   - Provide navigation guide

## Tools to Use

### Core Tools:
- **WebSearch**: Primary tool for finding sources
- **WebFetch**: Extract content from specific URLs
- **Task**: Deploy specialized research agents
- **TodoWrite**: Track research progress
- **Read/Write**: Manage research documents
- **Bash**: Create directories, organize files

### MCP Tools (if available):
- **mcp__filesystem__**: File operations
- **mcp__puppeteer__**: Browser automation for JavaScript-heavy sites
  - Navigate to dynamic pages
  - Take screenshots
  - Extract interactive content

### Research Strategy:
1. Start with WebSearch for general discovery
2. Use WebFetch for specific content extraction
3. Use mcp__puppeteer__ for sites requiring JavaScript
4. Prefer MCP web fetch tools when available

## Best Practices

### Multi-Agent Research:
- **Launch agents in parallel** (single response with multiple Task calls)
- **Clear task boundaries** to minimize redundancy
- **Comprehensive prompts** with all necessary context
- **Always include verification agent** for fact-checking
- **Plan result integration** before launching agents

### Hallucination Prevention:
- Ground all statements in source material
- Use Chain-of-Verification for critical claims
- Cross-reference multiple sources
- State uncertainty explicitly when appropriate

### Coverage Optimization:
- Use diverse search queries
- Check multiple perspectives
- Include recent sources (check dates)
- Acknowledge limitations and gaps

### Citation Management:
- Track source URLs and access dates
- Quote relevant passages verbatim
- Maintain source-to-statement mapping
- Use consistent citation format

## Red Flags for Unreliable Sources

Avoid or flag sources with:
- No author attribution
- Missing publication dates
- Broken or suspicious URLs
- Claims without data
- Undisclosed conflicts of interest
- Predatory journals
- Retracted papers (check RetractionWatch)

## Example Agent Deployment

For topic "AI in Healthcare":

```
Agent 1: Research current AI applications in clinical diagnosis
Agent 2: Find challenges and ethical concerns in medical AI
Agent 3: Investigate future AI healthcare innovations and predictions
Agent 4: Gather case studies of successful AI healthcare implementations
Agent 5: Cross-reference and verify key statistics about AI healthcare impact
```

Each agent gets:
- Specific research focus
- Tool usage instructions
- Citation requirements
- Expected output format

## Output Quality Standards

Research is complete when:
- All subtopics thoroughly covered
- Every claim properly cited
- Multiple authoritative sources for key findings
- Contradictions identified and explained
- Executive summary captures essence
- Full report is comprehensive and well-organized
- All supporting materials included
- Bibliography is complete and properly formatted
- All todo items marked as completed

## Ready to Begin

To use this skill, simply request:
- "Deep research on [topic]"
- "Conduct comprehensive research about [topic]"
- "I need multi-agent research on [topic]"

I will:
1. Ask clarifying questions about your needs
2. Create a detailed research plan
3. Deploy specialized agents in parallel
4. Synthesize findings with proper citations
5. Deliver comprehensive, well-organized outputs

See REFERENCE.md for additional methodology details, advanced techniques, and example workflows.
