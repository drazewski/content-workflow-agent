---
name: create-article
description: Create an article draft from a topic folder in this repository using the current project context and existing editorial workflow. Use for article-writing requests, not for preparing briefs, editing skills, or changing repository documentation.
---

# Create Article

Coordinate the repository's specialized skills to produce a finished Markdown draft from one topic folder. Read their instructions from disk; they do not need to be registered as commands in the current assistant.

## Resolve the request

1. Locate the repository root containing `AGENTS.md` and `workflows/create-article.md`. Resolve all workspace paths from that root, including when invoked from a subdirectory or through a symlink.
2. Read `AGENTS.md`, `README.md`, and the current `project-context.md` on every invocation. Do not reuse an earlier publication name, language, or editorial profile from the conversation when the file has changed.
3. If `project-context.md` is missing, follow `.agents/skills/onboarding/SKILL.md` to create it, then stop before article writing, as required by repository onboarding rules.
4. Use the topic folder supplied in the invocation or conversation, for example `source/drought_in_europe`. If no folder is supplied and exactly one topic folder exists in `source/`, use it. If several exist, ask which one to use. If the requested folder does not exist, report that and clarify the path rather than choosing another topic.
5. Read the folder's `brief.md`, `links.md`, and other useful source files. Treat the brief as article-specific direction and `project-context.md` as the defaults. Blank optional brief sections use those defaults; ask only when a missing detail or conflict materially prevents drafting.

## Run the article workflow

Follow `workflows/create-article.md`, loading the relevant skill instructions from `.agents/skills/` as each stage requires them:

1. **Analyze sources:** Use `source-analysis/SKILL.md` to extract findings, dates, figures, scope, and limitations from the local materials. Separate sourced findings from interpretation and flag unreadable files or missing evidence.
2. **Research when permitted:** Use `web-research/SKILL.md` for linked sources and additional research when permitted by the project context or explicitly requested. Build a coherent factual base before drafting; do not silently replace stronger local evidence or invent inaccessible source contents.
3. **Write:** Use `editorial-style/SKILL.md` and its relevant examples. Match the current project language, audience, tone, heading rules, and requested article length and angle.
4. **Prepare metadata:** Use `seo/SKILL.md` for the title, slug, excerpt, and meta description, and `taxonomy/SKILL.md` for tags and categories. Respect a project setting of no categories. Add internal links only when relevant articles and their URLs are verified.
5. **Export and check:** Use `markdown-export/SKILL.md` to save `articles/<topic>.md`, where `<topic>` is the selected folder's name. Include source links and a source list as required by the context. Check factual support, source limitations, metadata, and editorial consistency using the workflow's review checklist. If an article already exists, update it only when the user's request clearly authorizes an update; otherwise clarify before replacing it.

Load `editorial-review/SKILL.md` for an additional editorial review only when requested or required by the project context. Use `social-teaser/SKILL.md` only when teaser or social copy is requested.

## Optional WordPress handoff

Invoking `create-article` authorizes the local Markdown draft. It does not by itself authorize a CMS operation. After the Markdown exists, use `wordpress-publish/SKILL.md` only when WordPress draft creation or update is explicitly requested and any approval required by the current project context has been given. Existing authorization remains valid; do not ask for it again. Keep WordPress posts in `draft` status unless the user explicitly defines another workflow.

## Handoff

Return a link to the saved Markdown file, its title, and any material source gaps or unresolved questions. Report WordPress details only if that optional step actually ran. Do not present a research summary or outline as the completed article unless that is what the user requested.
