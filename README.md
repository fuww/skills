# Skills

This is FashionUnited's curated collection of Claude skills, adapted from Anthropic's official skills repository with customizations specific to our B2B fashion platform.

Skills are folders of instructions, scripts, and resources that Claude loads dynamically to improve performance on specialized tasks. Skills teach Claude how to complete specific tasks in a repeatable way, whether that's creating documents with your company's brand guidelines, analyzing data using your organization's specific workflows, or automating personal tasks.

For more information, check out:
- [What are skills?](https://support.claude.com/en/articles/12512176-what-are-skills)
- [Using skills in Claude](https://support.claude.com/en/articles/12512180-using-skills-in-claude)
- [How to create custom skills](https://support.claude.com/en/articles/12512198-creating-custom-skills)
- [Equipping agents for the real world with Agent Skills](https://anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills)

# Quick Start for Claude Web

1. Clone the repo
2. Create a zip of 1 skill
3. Upload to Claude web (admin can do it for whole org.)

# Quick Start for Claude Code

## Add a marketplace

https://code.claude.com/docs/en/plugin-marketplaces

Use `/plugin` in Claude Code or:

```bash
# Official Anthropic
/plugin marketplace add anthropics/claude-code
# FashionUnited Custom
/plugin marketplace add fuww/skills
```

## Install skill

Use `/plugin` in Claude Code or:

```bash
/plugin install plugin-name@marketplace-name

/plugin install skills@fashionunited
```

# About This Repository

This repository contains skills customized for FashionUnited's use with Claude Skills. These skills range from creative applications (art, design) to technical tasks (testing web apps, MCP server generation) to enterprise workflows (communications, branding, etc.).

**Key FashionUnited Customizations:**
- **brand-guidelines-fashionunited** - Updated with FashionUnited's rose color palette, typography, and Material Design standards
- All skills have the `-fashionunited` suffix to prevent conflicts with other installed skills
- Additional skills may be customized or added based on FashionUnited-specific workflows

Each skill is self-contained in its own directory with a `SKILL.md` file containing the instructions and metadata that Claude uses. Browse through these examples to get inspiration for your own skills or to understand different patterns and approaches.

The example skills in this repo are based on Anthropic's open source skills (Apache 2.0). We've also included the document creation & editing skills in the [`document-skills/`](./document-skills/) folder as reference examples, created by Anthropic.

**Note:** This repository is maintained by FashionUnited for internal use and customized to our platform's needs.

## Disclaimer

**These skills are provided for demonstration and educational purposes only.** While some of these capabilities may be available in Claude, the implementations and behaviors you receive from Claude may differ from what is shown in these examples. These examples are meant to illustrate patterns and possibilities. Always test skills thoroughly in your own environment before relying on them for critical tasks.

# Skills Overview

| Skill | Description |
|-------|-------------|
| algorithmic-art-fashionunited | Create generative art using p5.js with seeded randomness, flow fields, and particle systems |
| analytics-tracking-fashionunited | Set up, improve, or audit analytics tracking and measurement |
| article-extractor-fashionunited | Extract clean article content from URLs without ads or clutter |
| beads-fashionunited | Track work sessions and context across conversations |
| brainstorming-fashionunited | Refine rough ideas into fully-formed designs through Socratic questioning |
| brand-guidelines-fashionunited | Apply FashionUnited's official brand colors and typography |
| canvas-design-fashionunited | Design beautiful visual art in .png and .pdf formats using design philosophies |
| cass-fashionunited | Coding Agent Session Search - search local coding agent history |
| codex-fashionunited | Run Codex CLI for code analysis, refactoring, or automated editing |
| condition-based-waiting-fashionunited | Replace arbitrary timeouts with condition polling for flaky tests |
| copywriting-fashionunited | Write or improve marketing copy for pages |
| defense-in-depth-fashionunited | Validate at every layer to make bugs structurally impossible |
| dispatching-parallel-agents-fashionunited | Dispatch multiple agents to investigate independent problems concurrently |
| doc-coauthoring-fashionunited | Structured workflow for co-authoring documentation |
| docx-fashionunited | Create, edit, and analyze Word documents with tracked changes and comments |
| executing-plans-fashionunited | Execute implementation plans in controlled batches with review checkpoints |
| finishing-a-development-branch-fashionunited | Guide completion of development work with merge, PR, or cleanup options |
| frontend-design-fashionunited | Create distinctive, production-grade frontend interfaces |
| gemini-fashionunited | Run Gemini CLI for code review or big context (>200k) processing |
| internal-comms-fashionunited | Write internal communications (status reports, newsletters, FAQs) |
| launch-strategy-fashionunited | Plan product launches, feature announcements, or release strategies |
| marketing-ideas-fashionunited | Marketing ideas and strategies for SaaS or software products |
| mcp-builder-fashionunited | Guide for creating high-quality MCP servers to integrate external APIs |
| mt-updates-fashionunited | Write monthly Management Team updates for FashionUnited |
| notebooklm-skill-fashionunited | Query Google NotebookLM for source-grounded answers |
| obsidian-markdown-fashionunited | Create Obsidian Flavored Markdown with wikilinks, callouts, etc. |
| page-cro-fashionunited | Optimize conversions on marketing pages |
| pdf-fashionunited | Comprehensive PDF manipulation toolkit for extracting, creating, and merging PDFs |
| pptx-fashionunited | Create, edit, and analyze PowerPoint presentations with layouts and charts |
| pricing-strategy-fashionunited | Help with pricing decisions, packaging, or monetization |
| receiving-code-review-fashionunited | Handle code review feedback with technical rigor |
| remotion-best-practices-fashionunited | Best practices for Remotion video creation in React |
| requesting-code-review-fashionunited | Dispatch code-reviewer subagent to review implementation |
| root-cause-tracing-fashionunited | Trace bugs backward through call stack to identify source |
| seo-audit-fashionunited | Audit, review, or diagnose SEO issues |
| sharing-skills-fashionunited | Contribute skills upstream via pull request |
| shell-scripting-fashionunited | Bash scripting with defensive programming and ShellCheck compliance |
| ship-learn-next-fashionunited | Transform learning content into actionable implementation plans |
| skill-creator-fashionunited | Guide for creating effective skills |
| slack-gif-creator-fashionunited | Create animated GIFs optimized for Slack's size constraints |
| social-content-fashionunited | Create and optimize social media content |
| specification-document-generator-fashionunited | Generate architectural documents with requirements traceability |
| subagent-driven-development-fashionunited | Execute plans with fresh subagent per task and code review |
| systematic-debugging-fashionunited | Four-phase debugging framework ensuring understanding before fixes |
| tapestry-fashionunited | Unified content extraction and action planning from URLs |
| test-driven-development-fashionunited | Write tests first, watch fail, write minimal code to pass |
| testing-anti-patterns-fashionunited | Prevent testing mock behavior and production pollution |
| testing-skills-with-subagents-fashionunited | Test skills with subagents before deployment |
| theme-factory-fashionunited | Style artifacts with pre-set professional themes or custom themes on-the-fly |
| using-git-worktrees-fashionunited | Create isolated git worktrees for feature work |
| using-superpowers-fashionunited | Establish mandatory workflows for finding and using skills |
| vercel-react-best-practices-fashionunited | React and Next.js performance optimization from Vercel Engineering |
| vercel-web-design-guidelines-fashionunited | Review UI code for Web Interface Guidelines compliance |
| verification-before-completion-fashionunited | Require running verification before claiming work complete |
| web-artifacts-builder-fashionunited | Build complex claude.ai HTML artifacts using React, Tailwind CSS, and shadcn/ui |
| webapp-testing-fashionunited | Test local web applications using Playwright for UI verification and debugging |
| web-design-guidelines-fashionunited | Review UI code for accessibility and best practices |
| worktrees-fashionunited | Use git worktrees to parallelize development with agents |
| writing-plans-fashionunited | Create implementation plans with exact file paths and code examples |
| writing-skills-fashionunited | Create and test skills with TDD approach |
| xlsx-fashionunited | Create, edit, and analyze Excel spreadsheets with formulas and visualization |
| youtube-transcript-fashionunited | Download YouTube video transcripts |

# Example Skills

This repository includes a diverse collection of example skills demonstrating different capabilities:

## Creative & Design
- **algorithmic-art-fashionunited** - Create generative art using p5.js with seeded randomness, flow fields, and particle systems
- **canvas-design-fashionunited** - Design beautiful visual art in .png and .pdf formats using design philosophies
- **slack-gif-creator-fashionunited** - Create animated GIFs optimized for Slack's size constraints

## Development & Technical
- **web-artifacts-builder-fashionunited** - Build complex claude.ai HTML artifacts using React, Tailwind CSS, and shadcn/ui components
- **mcp-builder-fashionunited** - Guide for creating high-quality MCP servers to integrate external APIs and services
- **webapp-testing-fashionunited** - Test local web applications using Playwright for UI verification and debugging

## Enterprise & Communication
- **brand-guidelines-fashionunited** - Apply FashionUnited's official brand colors and typography to artifacts (rose #ea0151, Helvetica Neue, Material Design)
- **internal-comms-fashionunited** - Write internal communications like status reports, newsletters, and FAQs
- **theme-factory-fashionunited** - Style artifacts with 10 pre-set professional themes or generate custom themes on-the-fly

## Meta Skills
- **skill-creator-fashionunited** - Guide for creating effective skills that extend Claude's capabilities

# Document Skills

The `document-skills/` subdirectory contains skills that Anthropic developed to help Claude create various document file formats. These skills demonstrate advanced patterns for working with complex file formats and binary data:

- **docx-fashionunited** - Create, edit, and analyze Word documents with support for tracked changes, comments, formatting preservation, and text extraction
- **pdf-fashionunited** - Comprehensive PDF manipulation toolkit for extracting text and tables, creating new PDFs, merging/splitting documents, and handling forms
- **pptx-fashionunited** - Create, edit, and analyze PowerPoint presentations with support for layouts, templates, charts, and automated slide generation
- **xlsx-fashionunited** - Create, edit, and analyze Excel spreadsheets with support for formulas, formatting, data analysis, and visualization

**Important Disclaimer:** These document skills are point-in-time snapshots and are not actively maintained or updated. Versions of these skills ship pre-included with Claude. They are primarily intended as reference examples to illustrate how Anthropic approaches developing more complex skills that work with binary file formats and document structures.

# Installing FashionUnited Skills

## Claude Code

You can register this repository as a Claude Code Plugin marketplace by running the following command in Claude Code:
```
/plugin marketplace add fuww/skills
```

Then, to install the skills:
1. Select `Browse and install plugins`
2. Select `fashionunited`
3. Select `skills`
4. Select `Install now`

Alternatively, directly install via:
```
/plugin install skills@fashionunited
```

**Quick Start for FashionUnited Developers:**
```
/plugin marketplace add fuww/skills
/plugin install skills@fashionunited
```

After installing the plugin, you can use the skill by just mentioning it. For instance:
- "Use the brand-guidelines-fashionunited skill to style this presentation with FashionUnited colors"
- "Use the pdf-fashionunited skill to extract the form fields from path/to/some-file.pdf"
- "Use the xlsx-fashionunited skill to analyze the sales data in path/to/report.xlsx"

## Claude.ai

These example skills are all already available to paid plans in Claude.ai.

To use any skill from this repository or upload custom skills, follow the instructions in [Using skills in Claude](https://support.claude.com/en/articles/12512180-using-skills-in-claude#h_a4222fa77b).

## Claude API

You can use Anthropic's pre-built skills, and upload custom skills, via the Claude API. See the [Skills API Quickstart](https://docs.claude.com/en/api/skills-guide#creating-a-skill) for more.

# Creating a Basic Skill

Skills are simple to create - just a folder with a `SKILL.md` file containing YAML frontmatter and instructions. You can use the **template-skill** in this repository as a starting point:

```markdown
---
name: my-skill-name
description: A clear description of what this skill does and when to use it
---

# My Skill Name

[Add your instructions here that Claude will follow when this skill is active]

## Examples
- Example usage 1
- Example usage 2

## Guidelines
- Guideline 1
- Guideline 2
```

The frontmatter requires only two fields:
- `name` - A unique identifier for your skill (lowercase, hyphens for spaces)
- `description` - A complete description of what the skill does and when to use it

The markdown content below contains the instructions, examples, and guidelines that Claude will follow. For more details, see [How to create custom skills](https://support.claude.com/en/articles/12512198-creating-custom-skills).

# Partner Skills

Skills are a great way to teach Claude how to get better at using specific pieces of software. As we see awesome example skills from partners, we may highlight some of them here:

- **Notion** - [Notion Skills for Claude](https://www.notion.so/notiondevs/Notion-Skills-for-Claude-28da4445d27180c7af1df7d8615723d0)
