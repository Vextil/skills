# Personal skills

Reusable skills shared across computers through this repository.

## Layout

```text
skills/
├── README.md
├── AGENTS.md
└── skills/
    ├── comment-sicko/
    └── grill-me/
```

Each skill contains `SKILL.md`, its upstream `LICENSE`, and `agents/openai.yaml` with manual-only invocation metadata. Add supporting files only when the skill needs them.

## Link once on each computer

Clone the repository first. Link the repository's inner `skills` directory to your personal `~/.agents/skills` directory. Codex supports symlinked skill directories, and skills in this location apply across projects.

### macOS and Linux

For a clone at `~/Repos/skills`:

```sh
mkdir -p "$HOME/.agents"
ln -s "$HOME/Repos/skills/skills" "$HOME/.agents/skills"
```

Run the link command only if `~/.agents/skills` does not already exist. If it exists, inspect its contents and consolidate your personal skills before replacing that directory or link. Do not replace Codex's separate `~/.codex/skills` directory, which may contain bundled system skills.

Verify the target with:

```sh
readlink "$HOME/.agents/skills"
```

### Windows (PowerShell)

For a clone at `C:\Users\<you>\Repos\skills`, use a directory junction:

```powershell
$skillsRepo = Join-Path $env:USERPROFILE 'Repos\skills'
$skillsParent = Join-Path $env:USERPROFILE '.agents'
$skillsLink = Join-Path $skillsParent 'skills'
New-Item -ItemType Directory -Force -Path $skillsParent | Out-Null
if (Test-Path -LiteralPath $skillsLink) {
    throw "Inspect the existing skills directory or link first: $skillsLink"
}
New-Item -ItemType Junction -Path $skillsLink -Target (Join-Path $skillsRepo 'skills')
```

Adjust the clone path if needed. If Codex runs inside WSL, configure its Linux home separately using the Linux instructions.

## Comment Sicko

Manually invoke `$comment-sicko` with files or a diff to remove comments and report `MUST KILL` refactor targets. With no supplied scope, it uses the current diff against `main`. It edits comments only; application code stays unchanged.

The skill preserves pstack Comment Sicko's voice, exception list, deletion rules, treatment of uncertainty, and correctness-suppression flags. Invocation wording is adapted for a skill, and code/history investigations run directly through available tools. It has no other skill or custom-agent dependencies.

Adapted from [pstack's Comment Sicko](https://github.com/cursor/plugins/blob/9bd4a8289f1c3fe870d518051772762a78b66ea0/pstack/agents/comment-sicko.md), revision `9bd4a8289f1c3fe870d518051772762a78b66ea0`, under the MIT license retained alongside the skill.

## Grill Me

Manually invoke `$grill-me` with a plan, decision, or idea. It explores decisions through rounds of questions and recommendations, investigating factual questions directly and waiting for your answers before proceeding.

Imported from [Matt Pocock's grilling skill](https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/skills/productivity/grilling/SKILL.md), revision `3cca18b368ae95cdbdebbff572ccafa662551015`, under the MIT license. The instruction body is unchanged; the installed name is `grill-me`, and automatic invocation is disabled.

