# GitHub Tracking (DEPRECATED)

## Status: Migrated to github-muncher

The GitHub contribution analysis functionality has been **extracted to a standalone tool** called `github-muncher`.

**Migration Date**: December 19, 2025

## Current Usage

### Use github-muncher CLI

**Location**: `~/Projects/claude/github-muncher`

**Commands**:
```bash
# Navigate to github-muncher
cd ~/Projects/claude/github-muncher
source .venv/bin/activate

# Generate report for an engineer
github-muncher generate-report --engineer "Engineer Name" --period eoy_2025 \
  --output ~/Projects/claude/people_management/2025/output/github_reports/

# Analyze user activity
github-muncher analyze-user --username github_username

# Team summary
github-muncher team-summary --period eoy_2025
```

## Why This Folder Exists

This folder is kept for:
1. **Historical Reference** - Documentation of the original approach
2. **Dependencies Reference** - List of packages used (see requirements.txt)
3. **Archive** - Old scripts and outputs are stored in `archive/`

## What Was Migrated

The following functionality was extracted to github-muncher:
- GitHub API integration (PyGithub)
- Commit analysis and metrics calculation
- Pull request and code review tracking
- Repository contribution analysis
- Markdown report generation
- Team collaboration scoring

## Archive Structure

```
github_tracking/
├── README.md                    # This file
├── requirements.txt             # Dependencies reference (deprecated)
└── archive/
    ├── scripts/                 # Old Python scripts (archived)
    └── output/                  # Sample reports (archived)
```

---

*This folder is maintained for reference only. All active development happens in github-muncher.*
