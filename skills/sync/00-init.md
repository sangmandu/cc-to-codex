# Step 00: Init — Scope Selection

## Purpose

Check for existing config or determine sync scope.

## Procedure

1. Check if a config file already exists:
   ```bash
   ls ~/.cc-to-codex.yaml 2>/dev/null
   # If inside a project, also check:
   ls .cc-to-codex.yaml 2>/dev/null
   ```

   **If config exists**, show its contents and ask:
   ```
   Existing config found:
   <show config contents>

   1. Run sync with this config
   2. Create new config
   ```
   - User picks 1 → skip to `04-execute.md`
   - User picks 2 → continue below

2. Detect if the user is inside a git repository with a `.claude/` directory:
   ```bash
   git rev-parse --show-toplevel 2>/dev/null
   ls -d .claude 2>/dev/null
   ```

3. Present the options:

   **If project `.claude/` exists:**
   ```
   Select sync scope:

   1. Global only — ~/.claude → ~/.codex
   2. Global + Project — ~/.claude + ./.claude → ~/.codex + ./.codex

   Current project: <detected project root>
   ```

   **If no project `.claude/`:**
   ```
   No project .claude/ directory found. Syncing global only.
   → ~/.claude → ~/.codex
   ```
   (Auto-select global only)

4. Save the selection for use in subsequent steps:
   - `scope`: "global" (global only) or project root path e.g. "/Users/mini/mally" (global + project)
   - When project scope, the project root is the scope value itself

## Checklist

- [ ] Check for existing config
- [ ] Detect project context
- [ ] Present scope options
- [ ] User selects scope
- [ ] Record scope selection
