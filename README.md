> **Note:** This repository contains ThepExcel's collection of skills for Claude. For information about the Agent Skills standard, see [agentskills.io](http://agentskills.io).

# Skills

Skills are folders of instructions, scripts, and resources that Claude loads dynamically to improve performance on specialized tasks. Skills teach Claude how to complete specific tasks in a repeatable way.

**Learn more:** [Claude Skills คืออะไร? วิธีสร้างและใช้งาน](https://www.thepexcel.com/claude-skills/)

For official documentation:
- [What are skills?](https://support.claude.com/en/articles/12512176-what-are-skills)
- [Using skills in Claude](https://support.claude.com/en/articles/12512180-using-skills-in-claude)
- [How to create custom skills](https://support.claude.com/en/articles/12512198-creating-custom-skills)

# About This Repository

This repository contains skills developed by [ThepExcel](https://www.thepexcel.com) for productivity, research, problem-solving, and creative tasks. Each skill is self-contained in its own folder with a `SKILL.md` file.

Skills are organized into bundles by domain:

| Bundle | Skills | Description |
|--------|--------|-------------|
| `excel-skills` | xlsx, power-query-coaching | Excel and Power Query |
| `research-education-skills` | deep-research, explain-concepts | Research and learning |
| `innovation-skills` | problem-solving, triz, generate-creative-ideas | Problem-solving and creativity |
| `business-skills` | design-business-model, manage-business-strategy | Business frameworks |
| `prompt-engineering` | optimize-prompt, prompt-ai-image-video | AI prompt optimization |
| `skill-building` | skill-creator, extract-expertise | Create your own skills |
| `visualization-skills` | create-visualization | Diagrams and animations |
| `document-skills` | xlsx, docx, pptx, pdf | Office documents |

> **Note:** `xlsx` appears in both `excel-skills` and `document-skills` - install whichever fits your needs.

# Skill Sets

- [./skills](./skills): All available skills
- [./skills/xlsx](./skills/xlsx), [./skills/docx](./skills/docx), [./skills/pptx](./skills/pptx), [./skills/pdf](./skills/pdf): Document skills (from [Anthropic Official](https://github.com/anthropics/skills))

# Try in Claude Code, Claude.ai, and the API

## Claude Code

Register this repository as a Claude Code Plugin marketplace:

```bash
/plugin marketplace add ThepExcel/claude-skills
```

Then install skill bundles:

```bash
/plugin install excel-skills@thepexcel-skills -s project
/plugin install innovation-skills@thepexcel-skills -s project
/plugin install document-skills@thepexcel-skills -s project
```

**Installation scopes:**

| Scope | Flag | Use case |
|-------|------|----------|
| `project` | `-s project` | Current project only (recommended) |
| `user` | `-s user` | All projects |

**Other commands:**

```bash
/plugin list thepexcel-skills              # List available skills
/plugin marketplace update thepexcel-skills # Update to latest
/plugin uninstall excel-skills@thepexcel-skills
```

## Claude.ai

1. Download a skill folder from [./skills](./skills)
2. ZIP the folder (must contain SKILL.md)
3. Go to **Settings > Capabilities > Skills**
4. Click **Upload skill** and select your ZIP file

> **Requirements:** Pro, Max, Team, or Enterprise plan.

## Manual Installation

For offline access or full control:

```bash
git clone https://github.com/ThepExcel/claude-skills.git
cd claude-skills

# Symlink to ~/.claude/skills/
mkdir -p ~/.claude/skills
for skill in skills/*/; do
    skill_name=$(basename "$skill")
    ln -sf "$(pwd)/$skill" ~/.claude/skills/$skill_name
done
```

# Creating a Basic Skill

Use the `skill-creator` skill or create manually:

```markdown
---
name: my-skill-name
description: A clear description of what this skill does and when to use it
---

# My Skill Name

[Instructions that Claude will follow]

## Examples
- Example usage 1
- Example usage 2

## Guidelines
- Guideline 1
- Guideline 2
```

# License

- **Original skills (ThepExcel):** MIT License
- **Document skills (docx, xlsx, pptx, pdf):** See LICENSE.txt in each folder ([Anthropic Official](https://github.com/anthropics/skills))

# Author

Created by [Sira Ekabut](https://www.thepexcel.com) (ThepExcel)

*Skills developed through human-AI collaboration using Claude Code.*
