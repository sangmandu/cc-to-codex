# Step 04: Execute — Run Sync

## Purpose

Ask user for confirmation, then execute the sync.

## Procedure

1. Show what will happen:
   ```
   Ready to sync:

   Source: ~/.claude → Dest: ~/.codex
   Config: <config_path>
   Excluded: <exclusion summary>

   Run --dry-run preview first?
   ```

2. If user wants dry-run first:
   ```bash
   bash <path-to>/cc-to-codex.sh --dry-run --config <config_path>
   ```
   Show output, then ask:
   ```
   Proceed with actual sync?
   ```

3. If user confirms (or skips dry-run):
   ```bash
   bash <path-to>/cc-to-codex.sh --config <config_path>
   ```

4. Show results:
   ```
   Sync complete!
     Changed: N
     Skipped: N
   ```

## Checklist

- [ ] Show sync summary
- [ ] Offer dry-run preview
- [ ] Get user confirmation
- [ ] Execute sync
- [ ] Report results
