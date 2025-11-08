# Changelog

All notable changes to the Deep Research Skill will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added
- Importable Claude Code skill structure
- Comprehensive installation documentation
- Local testing workflow support
- Cross-platform installation support (Linux, macOS, Windows)

## [1.0.0] - 2025-11-08

### Added
- **Deep Research Skill** - Complete Claude Code skill implementation
  - `deep-research/SKILL.md` - Core skill with YAML frontmatter (380 lines)
  - `deep-research/REFERENCE.md` - Detailed methodology reference (789 lines)
  - `deep-research/README.md` - Installation and usage guide (438 lines)

- **Installation Documentation**
  - `INSTALL_SKILL.md` - Comprehensive installation guide with OS-specific instructions (541 lines)
  - One-command install for Linux, macOS, Windows
  - Step-by-step installation guides
  - Visual installation flow diagram
  - Comprehensive troubleshooting section

- **Testing Documentation**
  - `TESTING_LOCALLY.md` - Guide for local/project-based testing (236 lines)
  - Project vs global installation comparison
  - Testing workflow documentation
  - Modification and debugging guides

- **Skill Features**
  - 7-phase deep research process (Scoping → Planning → Querying → Triangulation → Synthesis → QA → Packaging)
  - Multi-agent deployment with parallel execution
  - Graph of Thoughts integration (Generate, Aggregate, Refine, Score operations)
  - Rigorous citation management (mandatory sources, quality ratings A-E)
  - Structured output generation (executive summaries, reports, data files, visualizations)
  - Source verification protocol
  - Hallucination prevention techniques
  - Chain-of-Verification (CoVe) methodology
  - Chain-of-Density (CoD) summarization

- **Platform Support**
  - Linux installation support
  - macOS installation support
  - Windows support (Git Bash, Command Prompt, PowerShell)
  - Project-local installation (`.claude/skills/`)
  - Global installation (`~/.claude/skills/`)

- **User Experience**
  - User interaction protocol with clarifying questions
  - Research plan approval workflow
  - Progress tracking with TodoWrite
  - Clear output structure in `/RESEARCH/[topic_name]/`
  - Quality assurance checklist

### Changed
- **README.md** - Updated with skill announcement and installation instructions
  - Added prominent skill availability section
  - Added documentation links
  - Maintained original Deep Research content

### Documentation Improvements
- Agent prompt templates (General Research, Academic/Technical, Verification, Synthesis)
- Tool usage guidelines (WebSearch, WebFetch, MCP Puppeteer)
- Citation format examples and requirements
- Source credibility assessment framework
- Red flags checklist for unreliable sources
- User interaction examples
- Troubleshooting solutions

### Technical Details
- Proper YAML frontmatter format
- Skill detection by Claude Code
- Skill priority order (project > global > plugin > built-in)
- Compatible with Claude Code 0.1.0+

## [Pre-1.0.0] - Before 2025-11-08

### Existing Features (Preserved)
- `CLAUDE.md` - Original implementation plan with GoT integration
- `Claude2.md` - Enhanced GoT implementation
- `deepresearchprocess.md` - Comprehensive 134KB methodology playbook
- `Deep Research Question Generator System Prompt.md` - ChatGPT prompt for question refinement
- `examples/` - Example research outputs (AI Detection Research)
- MIT License
- README with original documentation

---

## Version Numbering

- **Major version (X.0.0)** - Incompatible skill format changes
- **Minor version (1.X.0)** - New features, backward compatible
- **Patch version (1.0.X)** - Bug fixes, documentation updates

---

## Links

- [Installation Guide](INSTALL_SKILL.md)
- [Testing Guide](TESTING_LOCALLY.md)
- [Formalization Review](FORMALIZATION_REVIEW.md)
- [Repository](https://github.com/shafra-com/Claude-Code-Deep-Research)
- [Issues](https://github.com/shafra-com/Claude-Code-Deep-Research/issues)

---

## Contributing

See [FORMALIZATION_REVIEW.md](FORMALIZATION_REVIEW.md) for guidelines on contributing to this project.
