# cc-to-codex

Config-driven one-way sync from Claude Code (`~/.claude`) to Codex (`~/.codex`).

## What it does

- **Skills** → copies with path/terminology rewrites (`.claude` → `.codex`, `CLAUDE.md` → `AGENTS.md`)
- **Hooks** → copies with path rewrites, excludes configured items
- **CLAUDE.md → AGENTS.md** → copies with section exclusions and `CLAUDE_ONLY` block removal
- **hooks.json** → converts Claude Code settings.json hooks to Codex format

All exclusions are config-driven via `.cc-to-codex.yaml`.

## Quick Start

### 1. Install the skill

```bash
# Copy the skill to your Claude Code skills directory
cp -r skills/cc-to-codex-config ~/.claude/skills/
```

### 2. Generate config (interactive)

In Claude Code:
```
/cc-to-codex-config
```

This walks you through selecting what to sync/exclude and generates `.cc-to-codex.yaml`.

### 3. Run sync

```bash
bash cc-to-codex.sh                          # uses ~/.cc-to-codex.yaml
bash cc-to-codex.sh --config path/to/config  # explicit config
bash cc-to-codex.sh --dry-run                # preview only
```

## Config Schema

```yaml
# .cc-to-codex.yaml

scope: global  # "global" or "project"

project:
  claude_dir: /path/to/project/.claude
  codex_dir: /path/to/project/.codex

exclude:
  skills:
    - wf           # exact match
    - poppy-*      # glob pattern
  hooks:
    - rtk-rewrite.sh
  claude_md_sections:
    - "@RTK.md"
    - "Sub-Agent Policy"
```

## Requirements

- Python 3 with PyYAML (`pip install pyyaml`)
- bash 4+
