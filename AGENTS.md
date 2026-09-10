# Personal skill authoring

Create and edit this repository's skills under `skills/<skill-name>/SKILL.md`. This repository is the source of truth; use its `skills/` directory as the output location when invoking the skill creator.

Each skill needs YAML frontmatter with `name` and `description`, followed by task-specific instructions. Use a lowercase, hyphenated name matching the containing directory.

Add scripts, references, assets, and UI metadata only when the skill needs them. Use paths relative to the skill directory and describe platform-specific dependencies when applicable.

Keep credentials, local environments, and generated task outputs outside the repository. Do not copy bundled system skills or plugin caches into it.
