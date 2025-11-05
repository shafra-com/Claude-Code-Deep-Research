# Deep Research Skill for Claude Code

A comprehensive multi-agent research skill using Graph of Thoughts methodology, parallel exploration, rigorous citation tracking, and structured outputs.

## Features

- **7-Phase Research Process**: Systematic approach from scoping to delivery
- **Multi-Agent Deployment**: Parallel research with specialized agents
- **Graph of Thoughts**: Advanced reasoning with exploration, scoring, and pruning
- **Rigorous Citations**: Every claim backed by verifiable sources
- **Structured Outputs**: Executive summaries, full reports, data files, visualizations
- **Source Verification**: Cross-referencing and credibility assessment
- **Quality Assurance**: Hallucination prevention and completeness checks

## Installation

### Option 1: Personal Skills (Available across all projects)

Copy the `deep-research/` folder to your Claude Code skills directory:

```bash
# Create skills directory if it doesn't exist
mkdir -p ~/.claude/skills/

# Copy the skill
cp -r deep-research ~/.claude/skills/

# Verify installation
ls ~/.claude/skills/deep-research/
# Should show: SKILL.md  REFERENCE.md  README.md
```

### Option 2: Project Skills (Only for specific project)

Copy the skill to your project's `.claude/skills/` directory:

```bash
# Navigate to your project
cd /path/to/your/project

# Create skills directory
mkdir -p .claude/skills/

# Copy the skill
cp -r /path/to/deep-research .claude/skills/

# Verify installation
ls .claude/skills/deep-research/
# Should show: SKILL.md  REFERENCE.md  README.md
```

### Option 3: Clone from Repository

```bash
# For personal installation
cd ~/.claude/skills/
git clone https://github.com/shafra-com/Claude-Code-Deep-Research.git temp-repo
mv temp-repo/deep-research ./
rm -rf temp-repo

# For project installation
cd your-project/.claude/skills/
git clone https://github.com/shafra-com/Claude-Code-Deep-Research.git temp-repo
mv temp-repo/deep-research ./
rm -rf temp-repo
```

## Usage

Once installed, Claude Code will automatically detect and use the skill when you request deep research.

### Basic Usage

Simply ask Claude Code to conduct deep research:

```
"Deep research on quantum computing"
"Conduct comprehensive research about AI in healthcare"
"I need multi-agent research on CRISPR safety"
```

### The Research Process

Claude will:

1. **Ask Clarifying Questions** about:
   - Research focus and scope
   - Output format preferences
   - Target audience
   - Source requirements
   - Deliverable structure

2. **Create Research Plan** with:
   - Subtopic breakdown
   - Multi-agent deployment strategy
   - Output folder structure
   - Quality criteria

3. **Deploy Specialized Agents** for:
   - Web research (current trends, news)
   - Academic/technical research (papers, studies)
   - Case studies and applications
   - Future trends and predictions
   - Cross-verification and fact-checking

4. **Synthesize Findings** into:
   - Executive summary
   - Comprehensive full report
   - Data files and statistics
   - Visualizations (when applicable)
   - Source bibliography
   - Research notes

5. **Quality Assurance** to ensure:
   - All claims properly cited
   - No hallucinations
   - Contradictions addressed
   - Complete coverage

### Output Structure

Research outputs are saved to `/RESEARCH/[topic_name]/`:

```
RESEARCH/
└── your_topic_name/
    ├── README.md                    # Navigation guide
    ├── executive_summary.md         # 1-2 page summary
    ├── full_report.md               # Comprehensive findings
    ├── data/
    │   ├── raw_data.csv
    │   ├── processed_data.json
    │   └── statistics_summary.md
    ├── visuals/
    │   ├── charts/
    │   └── graphs/
    ├── sources/
    │   ├── bibliography.md          # Full citations
    │   └── source_summaries.md
    ├── research_notes/
    │   ├── agent_1_findings.md      # Individual agent outputs
    │   ├── agent_2_findings.md
    │   └── synthesis_notes.md
    └── appendices/
        ├── methodology.md
        └── limitations.md
```

## Examples

### Example 1: Technology Research

**Request:**
```
Deep research on the current state of large language models
```

**Claude will ask about:**
- Focus areas (capabilities, limitations, applications, ethical concerns?)
- Output format (executive summary, full report, technical analysis?)
- Scope (specific model families, time period, geographic focus?)
- Audience (technical, business, general?)

**Deliverable includes:**
- Executive summary of LLM landscape
- Technical capabilities analysis
- Use case studies
- Limitations and challenges
- Future trends
- Competitive analysis
- Full bibliography

### Example 2: Medical Research

**Request:**
```
I need comprehensive research on immunotherapy for cancer treatment
```

**Claude will ask about:**
- Specific cancer types or general overview?
- Focus on efficacy, safety, both?
- Include cost-benefit analysis?
- Target audience (clinicians, patients, researchers?)
- Source requirements (peer-reviewed only, include industry?)

**Deliverable includes:**
- Clinical trial data and outcomes
- Mechanism of action analysis
- Comparative effectiveness vs other treatments
- Safety profile and adverse events
- Cost and access considerations
- Future developments
- Patient case studies
- Regulatory landscape

### Example 3: Market Research

**Request:**
```
Deep research electric vehicle market trends and future outlook
```

**Claude will ask about:**
- Geographic scope (global, specific regions?)
- Time horizon (current, 5-year, 10-year forecast?)
- Market segments (passenger, commercial, luxury, budget?)
- Analysis focus (technology, consumer behavior, policy, competition?)

**Deliverable includes:**
- Market size and growth projections
- Technology trends (battery, charging, autonomous)
- Consumer adoption patterns
- Regulatory and policy landscape
- Competitive analysis
- Investment and M&A activity
- Risk factors
- Future scenarios

## Configuration

### Customizing Output Location

By default, research is saved to `/RESEARCH/[topic_name]/`. You can request a different location:

```
"Deep research on [topic], save outputs to /path/to/custom/location/"
```

### Customizing Agent Count

The skill deploys 5-7 agents by default. For faster research with less depth:

```
"Quick deep research on [topic] with 3 agents"
```

For maximum thoroughness:

```
"Comprehensive deep research on [topic] with 10 agents"
```

### Customizing Output Format

Specify your preferred format:

```
"Deep research on [topic], deliver as:
- Single markdown file (no folder structure)
- Executive summary only
- Technical report with data files
- Presentation-style slides"
```

## Advanced Features

### Graph of Thoughts Mode

Explicitly request GoT for complex topics:

```
"Deep research on [complex topic] using Graph of Thoughts with multiple exploration paths"
```

This triggers:
- Parallel exploration of multiple angles
- Quality scoring for each research path
- Aggregation of best findings
- Iterative refinement

### Chain-of-Verification

For critical research requiring maximum accuracy:

```
"Deep research on [topic] with chain-of-verification for all claims"
```

This adds:
- Explicit verification steps for each claim
- Multiple source confirmation
- Contradiction detection
- Uncertainty quantification

### Source Filtering

Request specific source types:

```
"Deep research on [topic]:
- Peer-reviewed sources only
- Last 2 years
- Exclude preprints
- Minimum impact factor 5+"
```

## Troubleshooting

### Skill not detected

**Check installation:**
```bash
# For personal skills
ls ~/.claude/skills/deep-research/SKILL.md

# For project skills
ls .claude/skills/deep-research/SKILL.md
```

**Verify YAML frontmatter:**
```bash
head -5 ~/.claude/skills/deep-research/SKILL.md
# Should show:
# ---
# name: deep-research
# description: Conduct comprehensive multi-agent deep research...
# ---
```

### Research incomplete or missing citations

The skill includes quality checks. If output lacks citations:
1. Claude will identify the gaps
2. Re-run verification agent
3. Add missing sources
4. Update outputs

### Context limit exceeded

For very large research topics:
1. Claude automatically splits reports into multiple files
2. Each subtopic gets its own document
3. README provides navigation

### Want more control

You can guide the process at each phase:
- Approve/modify research plan before execution
- Review agent findings before synthesis
- Request additional exploration of specific areas
- Add custom verification requirements

## Documentation

- **SKILL.md**: Core skill instructions and methodology
- **REFERENCE.md**: Detailed methodology, agent templates, troubleshooting
- **Repository**: Full source at https://github.com/shafra-com/Claude-Code-Deep-Research

## Additional Resources

### Example Research Outputs

See the `examples/` directory in the repository for complete research outputs:
- AI Detection Research (comprehensive example)
- Comparisons with other AI research tools

### Methodology Details

The skill implements methodologies from:
- Graph of Thoughts framework (Yao et al.)
- Chain-of-Verification techniques
- Multi-agent orchestration patterns
- OpenAI and Google Gemini deep research approaches

See `deepresearchprocess.md` in the repository for the complete 134KB playbook.

### Question Refinement

For help formulating effective research questions, see:
`Deep Research Question Generator System Prompt.md` in the repository

## Requirements

### Claude Code
This skill requires Claude Code CLI or compatible environment.

### Available Tools
The skill uses these Claude Code tools:
- **WebSearch**: Web search capability
- **WebFetch**: URL content extraction
- **Task**: Multi-agent deployment
- **TodoWrite**: Progress tracking
- **Read/Write**: Document management
- **Bash**: File operations

### Optional MCP Servers
Enhanced functionality with:
- **mcp__filesystem__**: File system operations
- **mcp__puppeteer__**: Browser automation for JavaScript-heavy sites

## Contributing

This skill is based on the Claude-Code-Deep-Research repository.

To contribute or report issues:
1. Visit: https://github.com/shafra-com/Claude-Code-Deep-Research
2. Open an issue or pull request
3. See contribution guidelines in repository

## License

MIT License - See repository for details

## Version

**Version**: 1.0.0
**Last Updated**: 2025-11-05
**Compatible with**: Claude Code 0.1.0+

## Support

For questions or issues:
1. Check REFERENCE.md for detailed guidance
2. Review examples in repository
3. Open issue on GitHub repository

---

## Quick Start Summary

```bash
# 1. Install the skill
mkdir -p ~/.claude/skills/
cp -r deep-research ~/.claude/skills/

# 2. Start Claude Code and request research
# In Claude Code:
"Deep research on [your topic]"

# 3. Answer clarifying questions

# 4. Approve research plan

# 5. Review outputs in RESEARCH/[topic_name]/
```

That's it! Claude Code will handle the multi-agent deployment, source gathering, synthesis, and quality assurance automatically.
