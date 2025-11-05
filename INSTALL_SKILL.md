# Installing Deep Research as a Claude Code Skill

This repository has been converted into an importable Claude Code skill. Follow these instructions to install and use it.

## What's Included

The `deep-research/` folder contains:
- **SKILL.md** - Core skill instructions (auto-loaded by Claude Code)
- **REFERENCE.md** - Detailed methodology and troubleshooting
- **README.md** - Installation and usage guide

## Quick Install

### Option 1: Personal Installation (Recommended)

Install for all your projects:

```bash
# Copy the skill to your Claude Code skills directory
cp -r deep-research ~/.claude/skills/

# Verify installation
ls ~/.claude/skills/deep-research/
```

### Option 2: Project-Specific Installation

Install only for the current project:

```bash
# In your project directory
mkdir -p .claude/skills/
cp -r deep-research .claude/skills/

# Verify installation
ls .claude/skills/deep-research/
```

### Option 3: Clone from GitHub

```bash
# For personal installation
cd ~/.claude/skills/
git clone https://github.com/shafra-com/Claude-Code-Deep-Research.git
mv Claude-Code-Deep-Research/deep-research ./
rm -rf Claude-Code-Deep-Research

# For project installation
cd your-project/.claude/skills/
git clone https://github.com/shafra-com/Claude-Code-Deep-Research.git
mv Claude-Code-Deep-Research/deep-research ./
rm -rf Claude-Code-Deep-Research
```

## Usage

Once installed, simply ask Claude Code:

```
"Deep research on [your topic]"
"Conduct comprehensive research about [topic]"
"I need multi-agent research on [topic]"
```

Claude Code will automatically use the skill and:
1. Ask clarifying questions about your research needs
2. Create a detailed research plan
3. Deploy specialized agents in parallel
4. Synthesize findings with proper citations
5. Deliver structured outputs

## Output Location

Research is saved to: `/RESEARCH/[topic_name]/`

Structure includes:
- Executive summary
- Full report
- Data files
- Visualizations
- Source bibliography
- Research notes

## Documentation

- **Installation & Usage**: `deep-research/README.md`
- **Detailed Methodology**: `deep-research/REFERENCE.md`
- **Core Instructions**: `deep-research/SKILL.md`

## Original Repository Files

The following files remain in the repository for reference:
- `CLAUDE.md` - Original implementation plan
- `Claude2.md` - Enhanced GoT implementation
- `deepresearchprocess.md` - Comprehensive methodology (134KB)
- `examples/` - Example research outputs
- `Deep Research Question Generator System Prompt.md` - Question refinement guide

## Verification

To verify the skill is installed correctly:

```bash
# Check file exists
cat ~/.claude/skills/deep-research/SKILL.md | head -5

# Should display:
# ---
# name: deep-research
# description: Conduct comprehensive multi-agent deep research...
# ---
```

## Support

For issues or questions:
1. Check `deep-research/REFERENCE.md` for troubleshooting
2. Review examples in `examples/` directory
3. Open an issue on GitHub

## Version

**Current Version**: 1.0.0
**Last Updated**: 2025-11-05
**Compatible with**: Claude Code 0.1.0+

---

## Quick Start

```bash
# 1. Install
cp -r deep-research ~/.claude/skills/

# 2. Use Claude Code
# Simply request: "Deep research on quantum computing"

# 3. Review outputs
ls RESEARCH/
```

That's it! The skill handles everything else automatically.
