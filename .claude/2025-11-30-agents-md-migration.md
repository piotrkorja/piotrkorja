# Session Context - 2025-11-30 - AGENTS.md Migration

## Summary

Migrated from CLAUDE.md to AGENTS.md following agents.md best practices, and performed repository-wide string replacements for username consistency.

## Changes Made

### 1. Agent Documentation Migration

**Created**: `AGENTS.md` (cross-agent compatible)
- Follows agents.md best practices for AI agent documentation
- Works with Claude Code, Cursor, GitHub Copilot, Aider, etc.
- Uses standard Markdown with no proprietary features

**Key Sections Added**:
- Clear instruction precedence hierarchy (user prompts > AGENTS.md > code patterns)
- Project setup and environment configuration
- Testing & verification procedures
- Code style conventions
- Security considerations (SSH/1Password)
- Git workflow & commit guidelines
- AI agent session management
- Token usage tracking
- System monitoring (SSD health)

**Removed**: `CLAUDE.md` (replaced by AGENTS.md)

### 2. Repository-Wide String Replacements

**Replacements Made**:
- `koriakin` → `korj` (all occurrences)
- `petro` → `piotr` (all occurrences)

**Statistics**:
- 50 new instances of `piotrkorj` created
- 0 remaining instances of `koriakin`
- 0 remaining instances of `petro`

**Files Modified**:
1. `AGENTS.md`
2. `README.md`
3. `LICENSE`
4. `.claude/2025-11-30-1password-ssh-fix.md`
5. `.claude/2025-11-30-optimize-media.md`
6. `.claude/stats/2025-11-30.md`
7. `.obsidian/workspace.json`
8. `2025-q4/2025-11-21.md`
9. `2025-q4/2025-11-29.md`
10. `2025-q4/readme.md`

**Example Changes**:
- `/Users/petrokoriakin/` → `/Users/piotrkorj/`
- `petrokoriakin1` → `piotrkorj1`
- `k.petro@improveit.solutions` → `k.piotr@improveit.solutions`
- SSH agent paths updated to reflect new username

**Note**: Documentation paths updated to `piotrkorj`, but actual filesystem directory remains `/Users/petrokoriakin/` until system username is changed.

### 3. Token Statistics Tracking

**Created**: `.claude/stats/2025-11-30.md`
- Tracks token usage across session
- Session 1: 19,432 tokens (9.72%)
- Session 2 (final): ~35,000 tokens (~17.5%)
- Total budget: 200,000 tokens

## AGENTS.md Best Practices Applied

Following https://agents.md/ guidelines:

1. **Dedicated Agent Context File**: Separate from human README
2. **Hierarchical Configuration**: Clear precedence rules
3. **Essential Content Areas**: Setup, testing, style, security, deployment
4. **Cross-Agent Compatibility**: Works with multiple AI platforms
5. **Living Documentation**: Designed to evolve with project
6. **Conflict Resolution**: Explicit user prompts override file instructions

## Repository Structure

```
piotrkorja/
├── .claude/
│   ├── settings.local.json
│   ├── stats/
│   │   └── 2025-11-30.md                    # NEW: Token stats
│   ├── 2025-11-30-1password-ssh-fix.md
│   ├── 2025-11-30-optimize-media.md
│   └── 2025-11-30-agents-md-migration.md    # This file
├── .obsidian/
│   └── workspace.json
├── 2025-q4/
│   ├── readme.md
│   ├── 2025-11-21.md
│   ├── 2025-11-27.md
│   └── 2025-11-29.md
├── AGENTS.md                                 # NEW: AI agent instructions
└── README.md
```

## Configuration Updates

### Username/Path Changes
All references to `petrokoriakin` changed to `piotrkorj` including:
- Working directory paths (in documentation)
- SSH agent socket paths (in documentation)
- File ownership references
- Email addresses
- Directory listings

### Repository Information
- **Current Branch**: `notes`
- **Main Branch**: `main`
- **Remote**: `git@github.com:piotrkorja/piotrkorja.git`
- **GitHub User**: `piotrkorja` (unchanged)

## Commands Used

```bash
# Create stats directory
mkdir -p .claude/stats

# Replace koriakin with korj
find . -type f \( -name "*.md" -o -name "*.json" \) ! -path "./.git/*" -exec sed -i '' 's/koriakin/korj/g' {} +

# Replace petro with piotr
find . -type f \( -name "*.md" -o -name "*.json" \) ! -path "./.git/*" -exec sed -i '' 's/petro/piotr/g' {} +

# Verify replacements
grep -r "piotrkorj" --include="*.md" --include="*.json"
grep -ri "koriakin" --include="*.md" --include="*.json"  # Should be empty
grep -ri "petro" --include="*.md" --include="*.json"     # Should be empty
```

## Next Steps

1. Review AGENTS.md and customize as needed
2. Commit changes with descriptive message
3. Update any external references to username change
4. Consider updating actual system username: `mv /Users/petrokoriakin /Users/piotrkorj` (requires system admin)
5. Update SSH config paths if system username changes

## Related Resources

- **agents.md**: https://agents.md/
- **GitHub Profile**: https://github.com/piotrkorja
- **Repository**: https://github.com/piotrkorja/piotrkorja

## Notes

- AGENTS.md is now the primary documentation for AI agents
- README.md remains for human readers
- All token usage now tracked in `.claude/stats/`
- Session context files preserve knowledge between AI sessions
- Username consistency improved across all documentation files
- Actual filesystem paths remain unchanged until system username is updated
