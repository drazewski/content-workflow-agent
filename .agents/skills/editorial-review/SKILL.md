---
name: editorial-review
description: Review a draft against project context, source material, and optionally existing published content before publication.
---

# Purpose

Use this skill when the user asks for editorial review, quality control, or comparison with existing site content.

This step is optional and should not be assumed in the default workflow unless `project-context.md` says it is required.

# Review checklist

Check the draft for:

- factual support from sources,
- unsupported claims,
- exaggerated or moralizing language,
- missing caveats,
- tone mismatch against `project-context.md`,
- weak title, slug, excerpt, or meta description,
- duplicate or vague headings,
- taxonomy problems,
- missing source list when sources are required,
- accidental live-publishing assumptions.

# Optional existing-content comparison

If the user provides a site archive, export, URL list, or search endpoint:

1. Identify articles with similar topics.
2. Check whether the new draft duplicates existing content.
3. Suggest internal links only when they help the reader.
4. Suggest angle changes if the draft repeats existing material too closely.

# Optional articles style comparison

If already existing articles are provided and are accepted by the user, check the draft for:
- style and tone consistency,
- formatting consistency,
- voice consistency,
- terminology consistency,
- structure consistency.

# Output

Return:

- findings ordered by importance,
- concrete edit suggestions,
- unresolved questions,
- publication readiness: ready, needs edits, or blocked.
