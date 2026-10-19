<div align="center">

# Content Workflow Agent

**From source material to publication-ready drafts, with your AI assistant.**

Content Workflow Agent helps creators, bloggers, publishers, and editorial teams research topics, analyze source materials, write articles, review content, optimize SEO metadata, and prepare Markdown documents for publication.

**One workspace. Eleven reusable skills.**

</div>

- Set up your publication's editorial context, audience, and writing style.
- Research topics using source documents and optional web research.
- Create structured articles with a consistent editorial voice.
- Optimize titles, descriptions, categories, and tags.
- Review content before publication.
- Export Markdown or optionally create WordPress drafts.

### Works with your existing AI assistant

Designed for Codex, Claude Code, GitHub Copilot, and other compatible AI agents that can read the repository's instructions and work with local files.

No dedicated platform required. No vendor lock-in. Your content stays in Markdown, ready for the publishing tools you choose.

**Start with onboarding. Create drafts safely. Publish only when you decide.**

---

## 🚀 Start Here

This repository helps AI agents such as Codex, GitHub Copilot, Claude, Gemini, or similar tools create structured article drafts.

The first action in a fresh copy of this repository is always onboarding.

`project-context.md` is intentionally not included. It is created by onboarding for a specific site, author, brand, publication, or editorial team.

> Onboarding is intentionally short. It creates a first usable `project-context.md`, and you can manually edit that file at any time later.

## 🧭 Quick Start

Use one of these entry points:

```text
codex "Start onboarding for this repository"
```

```text
codex '$onboarding'
```

In GitHub Copilot:

```text
Run the onboarding workflow for this repository.
```

Or copy the ready prompt from:

```text
prompts/start-onboarding.md
```

The agent should:

1. Read `README.md`.
2. Read `AGENTS.md`.
3. Read `.agents/skills/onboarding/SKILL.md`.
4. Tell the user that `project-context.md` can be edited manually later.
5. Ask only short onboarding questions, one at a time, including article length, heading preference, source link preference, and whether the user wants the optional WordPress draft step after the Markdown file is created.
6. Create `project-context.md`.
7. Stop before article writing or publishing.

## ✏️ You Can Edit Context Later

The onboarding result is not final or locked. It is only a starting profile for the agent.

After onboarding, you can open `project-context.md` and change anything manually:

- project description,
- audience,
- tone,
- source rules,
- categories and tags,
- publishing target,
- notes about what to avoid,
- examples of articles to follow.

You do not need to get everything right during onboarding.

## 📝 Create An Article

After onboarding:

1. Create one topic folder in `source/`.
   - Example: `source/mikroplastik-w-rzekach/`
2. Add all source materials for one article to that folder.
   - PDFs, reports, notes, links, briefs, text files, and reference material are all acceptable.
3. Ask the agent to create the article, or copy:

```text
prompts/create-article.md
```

Finished drafts should be written to:

```text
articles/<topic>.md
```

### Create an article with a skill

The `create-article` skill connects the specialized skills into the complete workflow. Start your assistant in this repository, then supply a topic folder.

In Codex CLI or the Codex IDE extension, type:

```text
$create-article source/drought_in_europe
```

You can also run `/skills`, select `create-article`, and provide the topic folder in your message. Codex discovers the skill in `.agents/skills/create-article/`.

In Claude Code, type `/` and select `create-article`, or enter:

```text
/create-article source/drought_in_europe
```

The repository includes `.claude/skills/create-article` as a relative symlink to `.agents/skills/create-article`. Both assistants read the same instructions. Keep the symlink when cloning or copying the repository. The other editorial skills are read from their files as needed, so they do not need separate Claude Code commands.

For invocation and discovery details, see the [official Codex skill documentation](https://learn.chatgpt.com/docs/build-skills) and [Claude Code skill documentation](https://code.claude.com/docs/en/skills).

The skill:

1. Reads the current `project-context.md` on every invocation, including any changes to the publication, language, or style. If the file is missing, it runs onboarding and stops before writing an article.
2. Reads `brief.md`, `links.md`, and the other materials in the selected topic folder. Empty optional brief sections use the project defaults.
3. Analyzes local sources and researches linked or additional sources when permitted.
4. Writes the article, prepares SEO metadata and tags, checks the draft, and saves `articles/<topic>.md` with sources as required.
5. Adds an editorial review or social teasers only when requested or configured. WordPress draft creation or update additionally requires an explicit request and any approval required by the project context, after the Markdown file exists.

If you omit the folder and there is exactly one topic folder in `source/`, the skill uses it. If there are several, it asks which one to use. It clarifies before replacing an existing article unless your request already authorizes an update.

If a newly added skill does not appear, restart your assistant in the repository. This is an AI-guided workflow: the assistant follows the skill and uses the tools available in your environment.

### Example: from brief to finished article

The `examples/` directory contains a complete example of the workflow:

- [Article brief](examples/source/drought_in_europe/brief.md) — the goal, audience, scope, and editorial requirements.
- [Source links](examples/source/drought_in_europe/links.md) — the starting material for research and verification.
- [Finished article: Drought in Europe](examples/articles/drought_in_europe.md) — an article ready for review and publishing.

## ⚙️ Agent Workflow

Use `create-article` to coordinate the article workflow, or follow the individual stages:

1. `onboarding` - create or refresh `project-context.md`.
2. `source-analysis` - analyze PDFs, reports, local notes, and other source documents.
3. `web-research` - use external research only when allowed or requested.
4. `editorial-style` - draft the article in the configured editorial style.
5. `seo` - refine title, slug, excerpt, and meta description.
6. `taxonomy` - choose category and tags.
7. `editorial-review` - optional review before handoff or publishing.
8. `markdown-export` - required default file output to Markdown or MDX.
9. `social-teaser` - optional teaser and social copy.
10. `wordpress-publish` - optional WordPress draft creation only when explicitly requested.

For a complete article workflow, read:

```text
workflows/create-article.md
```

## 📁 Repository Layout

```text
.
+-- AGENTS.md
+-- LICENSE
+-- README.md
+-- .agents/
|   +-- skills/
|       +-- create-article/
|       |   +-- SKILL.md
|       |   +-- agents/
|       |       +-- openai.yaml
|       +-- onboarding/
|       |   +-- SKILL.md
|       +-- source-analysis/
|       |   +-- SKILL.md
|       +-- web-research/
|       |   +-- SKILL.md
|       +-- editorial-style/
|       |   +-- SKILL.md
|       +-- seo/
|       |   +-- SKILL.md
|       +-- taxonomy/
|       |   +-- SKILL.md
|       +-- editorial-review/
|       |   +-- SKILL.md
|       +-- markdown-export/
|       |   +-- SKILL.md
|       +-- social-teaser/
|       |   +-- SKILL.md
|       +-- wordpress-publish/
|           +-- SKILL.md
+-- .claude/
|   +-- skills/
|       +-- create-article -> ../../.agents/skills/create-article
+-- .github/
|   +-- copilot-instructions.md
|   +-- instructions/
|       +-- content-workflow.instructions.md
+-- workflows/
|   +-- create-article.md
+-- prompts/
|   +-- start-onboarding.md
|   +-- create-article.md
+-- examples/
|   +-- articles/
|   |   +-- drought_in_europe.md
|   +-- source/
|       +-- drought_in_europe/
|           +-- brief.md
|           +-- links.md
+-- source/
+-- articles/
+-- .env.example
```

## 🧩 Optional WordPress Integration

The core workflow is CMS-neutral. Markdown is always the primary output format, while WordPress is treated as an optional publishing target.

By default, the workflow operates in Markdown-only mode. However, agents can also create or update WordPress drafts.

Users can decide whether WordPress integration should be enabled during onboarding or later by modifying the `project-context.md` file.

To enable WordPress draft creation:

1. Copy `.env.example` to `.env`
2. Configure the WordPress API credentials
3. Ask the agent to create or update a WordPress draft after generating the Markdown article

All WordPress posts are created with `draft` status by default.

## 📄 License

The reusable workflow, skills, prompts, templates, and project documentation are licensed under the [MIT License](LICENSE).

You can use, modify, and redistribute them, including commercially, provided you retain the copyright and license notice in copies or substantial portions of the licensed material.

This license does not grant rights to third-party source materials or automatically apply to articles created with the workflow. Those materials and articles require their own licensing decisions by the relevant rights holders.
