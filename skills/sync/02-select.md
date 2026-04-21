# Step 02: Select — Choose Exclusions

## Purpose

Let the user choose which items to EXCLUDE from sync. Default is sync everything.

## Procedure

### 1. Explain the model

```
All items are synced by default.
Select only the items you want to EXCLUDE. (Say "none" if nothing to exclude)
```

### 2. Ask per category

**Skills:**
```
Any skills to exclude?
Specify by number or name (comma-separated, glob patterns supported)
e.g.: wf, poppy-*, mally-local-e2e-test
```

**Hooks:**
```
Any hooks to exclude?
Specify by number or filename (comma-separated)
e.g.: rtk-rewrite.sh, record-surface-session.sh
```

**CLAUDE.md sections:**
```
Any sections to exclude from AGENTS.md?
Specify by number or section name (comma-separated)
e.g.: @RTK.md, Sub-Agent Policy
```

### 3. Confirm selections

```
Exclusion summary:

[Skills] wf, poppy-*
[Hooks] rtk-rewrite.sh
[CLAUDE.md] @RTK.md

Proceed? Let me know if you want to change anything.
```

Wait for user confirmation before proceeding.

## Checklist

- [ ] Explain default-include model
- [ ] Collect skill exclusions
- [ ] Collect hook exclusions
- [ ] Collect CLAUDE.md section exclusions
- [ ] Present summary and get confirmation
