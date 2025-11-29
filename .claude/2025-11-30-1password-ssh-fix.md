# Project Context - piotrkorja

Personal notes repository for tracking daily activities, plans, technical cheat sheets, and SSD health monitoring.

## Repository Information

- **Current Branch**: `notes`
- **Main Branch**: `main`
- **Remote**: `git@github.com:piotrkorja/piotrkorja.git`
- **Status**: 3 commits ahead of origin/notes
- **GitHub Profile**: https://github.com/piotrkorja

## SSH Key Configuration (Updated 2025-11-29)

### 1Password SSH Agent Setup

**Active Configuration** (`~/.ssh/config`):
```
Host github.com
	IdentityAgent "/Users/piotrkorj/Library/Group Containers/2BUA8C4S2C.com.1password/t/agent.sock"
	IdentityFile ~/.ssh/piotrkorja_github.pub
	IdentitiesOnly yes

Host *
	IdentityAgent "/Users/piotrkorj/Library/Group Containers/2BUA8C4S2C.com.1password/t/agent.sock"
```

**SSH Keys in 1Password**:
1. `GitHub SSH Key` (Ed25519) - General GitHub key
2. `Magnite SSH Key` (RSA)
3. `some macos id_ed25519` (Ed25519)
4. `PiotrKorja GitHub Ed25519` (Ed25519) - **ACTIVE for github.com**

**Authentication**:
- GitHub authenticates as: `piotrkorja`
- SSH Key: `ED25519 SHA256:bK/JcGx3VwOzdig46n4DTOtTfvnOxeJdH5pj5K7NhgM`

**Backup**:
- Old local keys backed up:
  - `~/.ssh/id_ed25519.old`
  - `~/.ssh/id_ed25519.pub.old`

## Project Structure

```
piotrkorja/
├── .claude/
│   ├── settings.local.json
│   └── context.md              # This file
├── .obsidian/                  # Obsidian vault configuration
│   └── workspace.json
└── 2025-q4/                    # Q4 2025 notes directory
    ├── readme.md               # Cheat sheet (was readme.md.md, renamed)
    ├── 2025-11-21.md           # Daily note
    ├── 2025-11-27.md           # Daily note with plans
    └── 2025-11-29.md           # Daily note with plans and resources
```

## Current Work & Plans

### Active Plans (from daily notes)
- ✅ Fix SSH keys - **COMPLETED 2025-11-29**
- Cleanup tailwind
- Monitor SSD health (Data Units Written tracking)

### Common Commands (from readme.md)

```bash
# Empty commit for tracking
git commit --allow-empty -m 'start'

# SSD health monitoring
sudo smartctl -a disk0 | grep -i "Data Units Written"

# Quick commit and push
git add .; git commit -m 'finish'; git push
```

### SSD Health Tracking
- Recent measurement: ~69.2-69.8 TB written
- Command: `sudo smartctl -a disk0 | grep -i "Data Units Written"`

## Recent Activity

- **2025-11-29**: Fixed SSH key configuration to use 1Password agent
- **2025-11-27**: Planning SSH key fixes
- Exercise tracking: "sixteen stories downstair barefoot walk"
- Managing daily notes in Obsidian

## Related Projects (Parent Directory)

Located in `/Users/piotrkorj/proc/`:
- active-adminix
- adminix-app
- ai-robo-advisor
- alkoframework
- contributors-gitlab-com
- csv mappers
- hotwired-november-todoapp
- moneygun
- piotrkorj1
- **piotrkorja** (this repository)
- swa1

## External Resources

- **Grok Project**: https://grok.com/project/65863763-9ebc-42ca-a6ef-c22b58781fd4?tab=attachments
- **YouTube Playlist**: https://youtube.com/playlist?list=PLrqTmwlqqVAtMUpiQZIVD8szuiIYl1er_&si=Gf8Wuk7jm3yyWwcL

## Git Workflow

### Pending Changes
```
Modified:
- .obsidian/workspace.json (Obsidian workspace state)
- 2025-q4/readme.md.md → renamed to readme.md

Untracked:
- 2025-q4/2025-11-27.md
- 2025-q4/2025-11-29.md
```

### Recent Commits
```
5bb6d4f excersise: sixteen stories downstair barefoot walk
a04e731 Data Units Written: 136,391,862 [69.8 TB]
72041d5 Data Units Written: 136,290,744 [69.7 TB]
ccaae8d finish
4a9fa9c finish
```

## Tools & Environment

- **Obsidian**: Note management and daily journal
- **1Password**: SSH key management and authentication
- **Git**: Version control for notes
- **smartctl**: SSD health monitoring
- **Platform**: macOS (Darwin 23.6.0)

## Notes

- This repository uses Obsidian for note management
- The `.obsidian/workspace.json` tracks current workspace state and open files
- All SSH authentication now goes through 1Password SSH agent
- SSD health is tracked via git commits with empty messages containing SMART data
