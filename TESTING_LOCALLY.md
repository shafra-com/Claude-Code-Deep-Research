# Testing the Deep Research Skill Locally

This guide shows how to test the skill in a project-specific way before installing globally.

## Why Test Locally First?

- **Safe testing**: Won't affect other projects
- **Easy removal**: Just delete `.claude/skills/` folder
- **Version testing**: Test different skill versions in different projects
- **Isolation**: Understand how the skill works before global install

## Quick Test Setup

### Step 1: Create Test Project

```bash
# Create test directory
mkdir -p ~/test-deep-research-skill
cd ~/test-deep-research-skill

# Create project-specific skills directory
mkdir -p .claude/skills/
```

### Step 2: Copy Skill to Project

**If you've already cloned the repo:**
```bash
# From the repository directory
cp -r deep-research ~/test-deep-research-skill/.claude/skills/
```

**If starting from scratch:**
```bash
cd ~/test-deep-research-skill
git clone https://github.com/shafra-com/Claude-Code-Deep-Research.git temp
cp -r temp/deep-research .claude/skills/
rm -rf temp
```

### Step 3: Verify Installation

```bash
# Check files are in place
ls .claude/skills/deep-research/
# Should show: SKILL.md  REFERENCE.md  README.md

# Check YAML frontmatter
head -5 .claude/skills/deep-research/SKILL.md
# Should show the frontmatter
```

### Step 4: Test in Claude Code

```bash
# Launch Claude Code in this directory
cd ~/test-deep-research-skill
# Open Claude Code here
```

Then request:
```
"Deep research on renewable energy trends"
```

If the skill is working, Claude will:
1. Ask clarifying questions about your research needs
2. Create a research plan
3. Deploy agents
4. Generate outputs in `RESEARCH/` folder

### Step 5: Verify Outputs

```bash
# Check if research outputs were created
ls RESEARCH/
```

## Testing Different Versions

You can test multiple versions side-by-side:

```bash
# Project A: Use version 1.0
cd ~/project-a
mkdir -p .claude/skills/
cp -r /path/to/deep-research-v1 .claude/skills/deep-research

# Project B: Use version 2.0
cd ~/project-b
mkdir -p .claude/skills/
cp -r /path/to/deep-research-v2 .claude/skills/deep-research

# Global: Use stable version
cp -r /path/to/deep-research-stable ~/.claude/skills/deep-research
```

## Modifying the Skill for Testing

Since it's local, you can edit and test changes:

```bash
# Edit the skill
nano .claude/skills/deep-research/SKILL.md

# Test your changes immediately
# Claude Code will use the modified version
```

## When You're Happy: Install Globally

```bash
# Copy tested version to global location
cp -r .claude/skills/deep-research ~/.claude/skills/

# Now it's available in all projects
```

## Removing Test Installation

```bash
# Remove from project only
rm -rf .claude/skills/deep-research

# Remove from global (if installed)
rm -rf ~/.claude/skills/deep-research
```

## Project vs Global Comparison

| Installation Type | Location | Scope | Use Case |
|------------------|----------|-------|----------|
| **Project** | `.claude/skills/` | Single project only | Testing, project-specific needs |
| **Global** | `~/.claude/skills/` | All projects | Daily use, stable skills |
| **Plugin** | Plugin marketplace | All projects | Official/community skills |

## Troubleshooting Test Installation

### Skill not detected in project

Check directory structure:
```bash
tree .claude/
# Should show:
# .claude/
# └── skills/
#     └── deep-research/
#         ├── SKILL.md
#         ├── REFERENCE.md
#         └── README.md
```

### Still using global skill instead of project skill

Project skills have **higher priority**. If it's still using global:
1. Make sure you're in the right directory
2. Check the skill name matches exactly
3. Try restarting Claude Code

### Want to force project skill

Temporarily rename global skill:
```bash
mv ~/.claude/skills/deep-research ~/.claude/skills/deep-research.backup
# Now only project skill will be used
```

## Complete Test Example

Here's a complete workflow from start to finish:

```bash
# 1. Create test environment
mkdir -p ~/skill-test
cd ~/skill-test

# 2. Clone and setup
git clone https://github.com/shafra-com/Claude-Code-Deep-Research.git
mkdir -p .claude/skills/
cp -r Claude-Code-Deep-Research/deep-research .claude/skills/
rm -rf Claude-Code-Deep-Research

# 3. Verify
ls .claude/skills/deep-research/
head -5 .claude/skills/deep-research/SKILL.md

# 4. Launch Claude Code in this directory
# Then request: "Deep research on AI safety"

# 5. Check outputs
ls RESEARCH/

# 6. If satisfied, install globally
cp -r .claude/skills/deep-research ~/.claude/skills/

# 7. Clean up test directory
cd ~
rm -rf ~/skill-test
```

## Windows Testing

**PowerShell:**
```powershell
# Create test directory
mkdir $HOME\skill-test
cd $HOME\skill-test

# Clone and setup
git clone https://github.com/shafra-com/Claude-Code-Deep-Research.git
mkdir -Force .claude\skills
Copy-Item -Recurse Claude-Code-Deep-Research\deep-research .claude\skills\
Remove-Item -Recurse Claude-Code-Deep-Research

# Verify
Get-ChildItem .claude\skills\deep-research

# Test in Claude Code, then install globally if satisfied
Copy-Item -Recurse .claude\skills\deep-research $HOME\.claude\skills\
```

## Best Practices

1. **Always test locally first** before global installation
2. **Keep test projects separate** from production work
3. **Document any modifications** you make during testing
4. **Verify outputs** thoroughly before trusting the skill
5. **Check resource usage** (token consumption, API calls)

---

**Ready to test?** Run this now:

```bash
mkdir -p ~/skill-test && cd ~/skill-test && git clone https://github.com/shafra-com/Claude-Code-Deep-Research.git && mkdir -p .claude/skills/ && cp -r Claude-Code-Deep-Research/deep-research .claude/skills/ && echo "✅ Ready to test! Open Claude Code in $(pwd)"
```
