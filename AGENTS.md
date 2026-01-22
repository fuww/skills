# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is FashionUnited's curated collection of Claude skills, adapted from Anthropic's official skills repository. Skills are folders of instructions, scripts, and resources that Claude loads dynamically to improve performance on specialized tasks.

## Repository Structure

```
skills/
├── skills/                    # Individual skill folders
│   └── brand-guidelines-fashionunited/
│       ├── SKILL.md          # Skill definition (required)
│       └── LICENSE.txt
├── .claude-plugin/
│   └── marketplace.json      # Claude Code plugin marketplace configuration
├── agent_skills_spec.md      # Agent Skills Spec v1.0
└── THIRD_PARTY_NOTICES.md    # Third-party licenses
```

## Skill Structure

Every skill requires a `SKILL.md` file with YAML frontmatter:

```markdown
---
name: skill-name              # lowercase, hyphens only, must match folder name
description: What the skill does and when to use it
license: Optional license reference
allowed-tools:                # Optional: pre-approved tools (Claude Code only)
  - ToolName
metadata:                     # Optional: custom key-value pairs
  custom-key: value
---

# Skill Instructions

[Markdown content with instructions, examples, guidelines]
```

## Plugin Installation (Claude Code)

```bash
# Add FashionUnited marketplace
/plugin marketplace add fuww/skills

# Install skills
/plugin install skills@fashionunited
```

## Creating New Skills

1. Create a folder under `skills/` matching your skill name
2. Add a `SKILL.md` with required frontmatter (`name`, `description`)
3. Add any supporting files (scripts, resources, LICENSE.txt)
4. Update `.claude-plugin/marketplace.json` to include the new skill path

## FashionUnited Brand Guidelines

The `brand-guidelines-fashionunited` skill contains FashionUnited's official brand identity:

- **Primary color**: `#ea0151` (rose[600])
- **Typography**: Helvetica Neue, system fonts, Georgia for articles
- **Spacing**: 8px base unit, Material Design guidelines
- **Breakpoints**: xs(0), xssm(480), sm(600), md(840), lg(1024), xl(1920)
