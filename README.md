# Personal skills

Reusable skills I use.

## Link once on each computer

Clone the repository first. Link the repository's inner `skills` directory to your personal `~/.agents/skills` directory.

### macOS and Linux

For a clone at `~/Repos/skills`:

```sh
mkdir -p "$HOME/.agents"
ln -s "$HOME/Repos/skills/skills" "$HOME/.agents/skills"
```

Run the link command only if `~/.agents/skills` does not already exist. If it exists, inspect its contents and consolidate your personal skills before replacing that directory or link.

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