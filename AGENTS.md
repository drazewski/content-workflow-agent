# Agent Instructions

This repository is a CMS-neutral article workflow workspace with optional publishing integrations.

## Mandatory Start Behavior

When a user asks for onboarding, says `$onboarding`, or asks to start this repository:

1. Read `README.md`.
2. Read `.agents/skills/onboarding/SKILL.md`.
3. Tell the user that onboarding creates only a first version of `project-context.md`.
4. Tell the user they can manually edit `project-context.md` at any time later.
5. Run the onboarding workflow.
6. Create `project-context.md` from the user's answers.
7. Do not write an article yet.
8. Do not publish anything.

`project-context.md` is expected to be missing in a fresh repository. Do not treat that as an error.

Onboarding should be short. Do not pressure the user to provide complete editorial rules. If something is unclear, use a reasonable default and leave it easy to edit later in `project-context.md`.

During onboarding, ask whether the user wants an optional WordPress draft step. The local Markdown file in `articles/` is always created first and remains the base output.

Ask onboarding questions one at a time. Do not send multiple onboarding questions in a single message.

## Before Article Work

Before creating any article:

1. Confirm that `project-context.md` exists.
2. If it does not exist, run onboarding first.
3. Read the relevant files in `.agents/skills/`.
4. Use `workflows/create-article.md` for the end-to-end workflow.

## Default Rules

- One folder in `source/` equals one article.
- Finished drafts go to `articles/<topic>.md`.
- Local source files are preferred over unsupported assumptions.
- External research is allowed only if `project-context.md` permits it or the user explicitly asks.
- Publishing integrations are disabled unless the user explicitly asks for draft creation or update.
- Markdown export to `articles/<topic>.md` is the required safe base output.
- WordPress posts must stay in `draft` status unless the user explicitly defines a different workflow.

## Skill Map

- `$create-article`: `.agents/skills/create-article/SKILL.md` (complete article workflow)
- `$onboarding`: `.agents/skills/onboarding/SKILL.md`
- `$source-analysis`: `.agents/skills/source-analysis/SKILL.md`
- `$web-research`: `.agents/skills/web-research/SKILL.md`
- `$editorial-style`: `.agents/skills/editorial-style/SKILL.md`
- `$seo`: `.agents/skills/seo/SKILL.md`
- `$taxonomy`: `.agents/skills/taxonomy/SKILL.md`
- `$editorial-review`: `.agents/skills/editorial-review/SKILL.md`
- `$markdown-export`: `.agents/skills/markdown-export/SKILL.md`
- `$social-teaser`: `.agents/skills/social-teaser/SKILL.md`
- `$wordpress-publish`: `.agents/skills/wordpress-publish/SKILL.md`
