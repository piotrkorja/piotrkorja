# AI Agent Instructions (effective 2025-11-29+)

You are working on my personal notes repository. Follow these rules in strict priority order:

1. **The user’s current chat message overrides EVERYTHING below** — always obey it first.
2. Never use emojis in any file unless I explicitly request them.
3. Daily notes go in the current quarter folder using format:
   ```
   2025-q4/2025-11-29.md   (example)
   ```
4. Session context files (only create when non-trivial work was done):
   ```
   .claude/2025-11-29-short-description.md
   ```
5. Token usage stats — **mandatory at the end of every session**:
   ```
   .claude/stats/2025-11-29.md
   ```
   Use exactly this template:
   ```markdown
   # Token Usage Stats - 2025-11-29
   ## Current Session
   - Timestamp: 2025-11-29 HH:MM
   - Model: [name]
   - Tokens Used / Budget: X,XXX / 200,000
   - Usage %: XX.XX%
   ## Tasks Completed
   - …
   ```
6. **Session workflow (always)**
   - Start → `git commit --allow-empty -m 'start'`
   - End → 
     - dump token stats (rule 5)
     - create/update session context if anything meaningful happened
     - commit with meaningful message or `finish`
     - `git push`
7. **SSD health** — record exactly once per day (first session):
   ```bash
   git commit --allow-empty -m "SSD: $(sudo smartctl -a disk0 | grep -i 'Data Units Written' | awk '{print $NF}' | xargs -I{} echo $(({} * 512 / 1000000000000)) TB written)"
   ```
   (commit message will look like: `SSD: 69.8 TB written`)
8. Preserve existing markdown style, file naming, and structure unless I explicitly say otherwise.
9. This file is living documentation — if a practice actually changes, update only the relevant numbered rule above.
10. Everything not listed here is intentional noise — ignore it unless I specifically reference it.
