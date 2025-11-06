# Installing Deep Research as a Claude Code Skill

This repository has been converted into an importable Claude Code skill. Follow these instructions to download and install it.

## 🚀 One-Command Install (Fastest)

If you're comfortable with terminal commands, copy and paste this **entire block** into your terminal:

**Linux/macOS:**
```bash
cd ~ && \
git clone https://github.com/shafra-com/Claude-Code-Deep-Research.git && \
cd Claude-Code-Deep-Research && \
mkdir -p ~/.claude/skills/ && \
cp -r deep-research ~/.claude/skills/ && \
echo "✅ Installation complete! Open Claude Code and say: 'Deep research on [your topic]'"
```

**Windows (Git Bash):**
```bash
cd ~ && \
git clone https://github.com/shafra-com/Claude-Code-Deep-Research.git && \
cd Claude-Code-Deep-Research && \
mkdir -p ~/.claude/skills/ && \
cp -r deep-research ~/.claude/skills/ && \
echo "✅ Installation complete! Open Claude Code and say: 'Deep research on [your topic]'"
```

**Windows (PowerShell):**
```powershell
cd $HOME; git clone https://github.com/shafra-com/Claude-Code-Deep-Research.git; cd Claude-Code-Deep-Research; mkdir -Force $HOME\.claude\skills; Copy-Item -Recurse deep-research $HOME\.claude\skills\; Write-Host "✅ Installation complete! Open Claude Code and say: 'Deep research on [your topic]'"
```

---

## 📋 What's Included

The `deep-research/` folder contains:
- **SKILL.md** - Core skill instructions (auto-loaded by Claude Code)
- **REFERENCE.md** - Detailed methodology and troubleshooting
- **README.md** - Installation and usage guide

---

## 📖 Step-by-Step Installation Guide

Choose your operating system:
- [Linux/macOS Instructions](#complete-installation-guide-start-to-finish)
- [Windows Instructions](#windows-installation-instructions)

---

## Complete Installation Guide (Start to Finish)

**For Linux and macOS users**

### Step 1: Download the Repository

First, download this repository to your computer:

```bash
# Navigate to your home directory
cd ~

# Clone the repository from GitHub
git clone https://github.com/shafra-com/Claude-Code-Deep-Research.git

# Navigate into the downloaded repository
cd Claude-Code-Deep-Research
```

**Alternative: Download without Git**

If you don't have git installed, download the ZIP file:

1. Visit: https://github.com/shafra-com/Claude-Code-Deep-Research
2. Click the green "Code" button
3. Click "Download ZIP"
4. Extract the ZIP file to a folder
5. Open terminal/command prompt and navigate to that folder:

```bash
cd ~/Downloads/Claude-Code-Deep-Research-main
```

### Step 2: Install the Skill

Now copy the skill to Claude Code's skills directory:

```bash
# Create Claude Code skills directory if it doesn't exist
mkdir -p ~/.claude/skills/

# Copy the skill folder
cp -r deep-research ~/.claude/skills/

# Verify the installation
ls -la ~/.claude/skills/deep-research/
```

You should see output like:
```
SKILL.md
REFERENCE.md
README.md
```

### Step 3: Verify Installation

Check that the YAML frontmatter is correct:

```bash
# Display first 5 lines of SKILL.md
head -5 ~/.claude/skills/deep-research/SKILL.md
```

Expected output:
```
---
name: deep-research
description: Conduct comprehensive multi-agent deep research...
---
```

### Step 4: Start Using the Skill

Open Claude Code and request deep research:

```
"Deep research on quantum computing"
```

Claude Code will automatically detect and use the skill!

---

## Windows Installation Instructions

If you're on Windows, use these commands instead:

### Step 1: Download the Repository

**Option A: Using Git Bash (Recommended)**

1. Install Git for Windows from: https://git-scm.com/download/win
2. Open Git Bash
3. Run these commands:

```bash
# Navigate to your home directory
cd ~

# Clone the repository
git clone https://github.com/shafra-com/Claude-Code-Deep-Research.git

# Navigate into the repository
cd Claude-Code-Deep-Research
```

**Option B: Using Command Prompt**

1. Download ZIP from: https://github.com/shafra-com/Claude-Code-Deep-Research
2. Extract to `C:\Users\YourUsername\Downloads\`
3. Open Command Prompt (cmd) and run:

```cmd
cd %USERPROFILE%\Downloads\Claude-Code-Deep-Research-main
```

### Step 2: Install the Skill

**Using Git Bash or PowerShell:**

```bash
# Create skills directory
mkdir -p %USERPROFILE%\.claude\skills

# Copy the skill
cp -r deep-research %USERPROFILE%\.claude\skills\

# Verify installation
dir %USERPROFILE%\.claude\skills\deep-research
```

**Using Command Prompt (cmd):**

```cmd
# Create skills directory
mkdir %USERPROFILE%\.claude\skills

# Copy the skill
xcopy /E /I deep-research %USERPROFILE%\.claude\skills\deep-research

# Verify installation
dir %USERPROFILE%\.claude\skills\deep-research
```

### Step 3: Verify Installation

**Git Bash:**
```bash
head -5 ~/.claude/skills/deep-research/SKILL.md
```

**Command Prompt:**
```cmd
more %USERPROFILE%\.claude\skills\deep-research\SKILL.md
```

Look for these first lines:
```
---
name: deep-research
description: Conduct comprehensive multi-agent deep research...
---
```

### Step 4: Use the Skill

Open Claude Code and request:
```
"Deep research on AI trends"
```

---

## macOS Installation Instructions

macOS users can follow the main Linux/Unix instructions above. Open Terminal (Applications → Utilities → Terminal) and run:

```bash
# Full installation in one go
cd ~
git clone https://github.com/shafra-com/Claude-Code-Deep-Research.git
cd Claude-Code-Deep-Research
mkdir -p ~/.claude/skills/
cp -r deep-research ~/.claude/skills/
ls ~/.claude/skills/deep-research/
```

---

## Quick Install (If Already Downloaded)

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

## Installation Process Flow

```
┌─────────────────────────────────────────────────┐
│  Step 1: Download Repository                    │
│  • Clone with git OR download ZIP               │
└──────────────┬──────────────────────────────────┘
               │
               ▼
┌─────────────────────────────────────────────────┐
│  Step 2: Navigate to Repository Folder          │
│  • cd Claude-Code-Deep-Research                 │
└──────────────┬──────────────────────────────────┘
               │
               ▼
┌─────────────────────────────────────────────────┐
│  Step 3: Create Skills Directory                │
│  • mkdir -p ~/.claude/skills/                   │
└──────────────┬──────────────────────────────────┘
               │
               ▼
┌─────────────────────────────────────────────────┐
│  Step 4: Copy Skill Folder                      │
│  • cp -r deep-research ~/.claude/skills/        │
└──────────────┬──────────────────────────────────┘
               │
               ▼
┌─────────────────────────────────────────────────┐
│  Step 5: Verify Installation                    │
│  • ls ~/.claude/skills/deep-research/           │
└──────────────┬──────────────────────────────────┘
               │
               ▼
┌─────────────────────────────────────────────────┐
│  Step 6: Use in Claude Code                     │
│  • "Deep research on [topic]"                   │
└─────────────────────────────────────────────────┘
```

---

## ❓ Troubleshooting

### Problem: "git: command not found"

**Solution:** Download the ZIP file instead:

1. Visit: https://github.com/shafra-com/Claude-Code-Deep-Research
2. Click green "Code" button → "Download ZIP"
3. Extract ZIP file
4. Navigate to extracted folder in terminal
5. Continue with Step 2 (copy skill)

### Problem: "No such file or directory: ~/.claude/skills/"

**Solution:** The directory doesn't exist yet. Create it first:

```bash
mkdir -p ~/.claude/skills/
```

Then retry the copy command.

### Problem: Permission denied when copying

**Linux/macOS Solution:**
```bash
# Try with sudo (enter your password when prompted)
sudo cp -r deep-research ~/.claude/skills/
sudo chown -R $USER ~/.claude/skills/
```

**Windows Solution:**
- Right-click Command Prompt or PowerShell
- Select "Run as administrator"
- Retry the copy command

### Problem: Skill not detected by Claude Code

**Check installation location:**
```bash
# Should show SKILL.md, REFERENCE.md, README.md
ls ~/.claude/skills/deep-research/
```

**Check YAML frontmatter:**
```bash
head -5 ~/.claude/skills/deep-research/SKILL.md
```

Should show:
```yaml
---
name: deep-research
description: Conduct comprehensive multi-agent deep research...
---
```

**Restart Claude Code:**
Sometimes Claude Code needs to be restarted to detect new skills.

### Problem: Installation works but skill doesn't activate

**Try explicitly requesting the skill:**
```
"Use the deep-research skill to research [topic]"
```

**Or check available skills:**
```
"What skills are available?"
```

---

## 🆘 Still Need Help?

1. **Check the detailed documentation:**
   - `deep-research/README.md` - Usage guide
   - `deep-research/REFERENCE.md` - Methodology details

2. **Verify file structure:**
   ```bash
   tree ~/.claude/skills/deep-research/
   # Should show:
   # deep-research/
   # ├── SKILL.md
   # ├── REFERENCE.md
   # └── README.md
   ```

3. **Check file permissions:**
   ```bash
   ls -la ~/.claude/skills/deep-research/
   # All files should be readable (r-- in permissions)
   ```

4. **Open an issue:**
   - Visit: https://github.com/shafra-com/Claude-Code-Deep-Research/issues
   - Describe the problem with error messages
   - Include your OS (Windows/macOS/Linux)

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
