# CLAUDE.md - Project Memory

## Project Context

**People Management** is an engineering management toolkit for coordinating performance review workflows. It integrates data from multiple sources to create evidence-based performance reviews.

## Purpose

This project serves as a coordination hub for:
- Tracking performance review status for 16 engineers
- Gathering data from 5 sources (EOY PDFs, MYR assessments, 360° feedback, GitHub, manager notes)
- Generating comprehensive performance reviews (Version 3.0 format)
- Uploading reviews to Confluence
- Managing sensitive HR documents securely

## Key Principles

### 1. Data Security First
- The `2025/` folder contains sensitive HR data and is NEVER committed to git
- Credentials are gitignored (.env, .github_token, etc.)
- Performance reviews contain confidential information (salaries, ratings, peer feedback)

### 2. Evidence-Based Reviews
Performance reviews combine 5 data sources in priority order:
1. EOY Performance PDFs (official ratings, manager comments)
2. Mid-Year Review Self-Assessments (goals, reflections)
3. 360° Feedback Forms (peer reviews, competency ratings)
4. GitHub Contribution Reports (quantitative metrics)
5. Manager observations and 1-on-1 notes

### 3. Integration Over Implementation
This project coordinates existing tools rather than reimplementing functionality:
- `document-cruncher` - Extract text from PDFs, DOCX, Excel
- `github-muncher` - Analyze GitHub contributions
- `foundations-features-documentation` - Upload to Confluence
- `engineering-manager` agent - Automate review compilation

### 4. Version 3.0 Format
Performance reviews follow a standardized structure:
- Executive Summary (1 paragraph with overall rating)
- Performance Ratings (Overall, WHAT, HOW, Risk Modifier)
- Goal Achievement Analysis (for each of 5 goals)
- Strengths & Achievements
- 360° Feedback Synthesis
- Areas for Development
- Manager Comments & Assessment
- Employee Self-Assessment Highlights
- Performance Review Conclusion

## Project Structure

### Core Files
- `README.md` - Project documentation
- `CLAUDE.md` - This file (project memory)
- `history.md` - Session history and changes
- `Engineer_Tracking.md` - Status tracker for 16 engineers
- `PERFORMANCE_REVIEW_SOURCES.md` - Data sources checklist
- `.gitignore` - Security rules (exclude 2025/, credentials)

### Data Directories
- `2025/` - Sensitive HR data (gitignored)
  - `EOY performance/EOY reviews/` - Performance review PDFs
  - `mid year performance/` - Self-assessments and 360° feedback
  - `Promotions/` - Promotion letters
  - `2025 salary increase/` - Salary letters
  - `output/` - Generated reviews and reports

- `github_tracking/` - Deprecated local implementation
  - Functionality extracted to `github-muncher` tool
  - Kept for reference and documentation

## Integration Points

### 1. Team Roster
- Location: `~/Projects/claude/TEAM_ROSTER.md`
- Purpose: Single source of truth for 16 engineers
- Data: Names, employee IDs, GitHub usernames, emails, roles

### 2. document-cruncher
- Location: `~/Projects/claude/document-cruncher`
- Purpose: Extract text from documents
- Commands: `extract-pdf`, `extract-docx`, `extract-excel`

### 3. github-muncher
- Location: `~/Projects/claude/github-muncher`
- Purpose: GitHub contribution analysis
- Commands: `generate-report`, `analyze-user`

### 4. foundations-features-documentation
- Location: `~/Projects/claude/foundations-features-documentation`
- Purpose: Confluence integration
- Command: `confluence_manager.py`

### 5. engineering-manager agent
- Location: `~/Projects/claude/engineering-manager.ts`
- Purpose: Automated review compilation
- Usage: `/engineering-manager generate performance review for [Name]`

## Workflows

### Primary Workflow: Generate Performance Review
1. Extract EOY PDF using document-cruncher
2. Extract MYR self-assessment from Excel
3. Extract 360° feedback from Excel
4. Generate GitHub report using github-muncher
5. Compile review combining all 5 sources
6. Update Engineer_Tracking.md with status and rating
7. Upload to Confluence

### Secondary Workflow: Track Progress
1. Open Engineer_Tracking.md
2. Update status (⬜ → 🔄 → ✅)
3. Add ratings, dates, links
4. Calculate statistics

## Data Sources Priority

When conflicts occur, use this priority:
1. **EOY Performance PDF** - Official ratings and manager comments (highest authority)
2. **MYR Self-Assessment** - Employee's goal progress and reflections
3. **360° Feedback** - Peer perspectives and competency ratings
4. **GitHub Reports** - Quantitative contribution data
5. **Manager Notes** - Direct observations and 1-on-1 discussions

## Template References

Use these reviews as examples:
- Caroline Cories (Employee ID: n621320) - Rating: 1.85
- Steven Jackson (Employee ID: n444266) - Rating: 1.85

Both reviews demonstrate Version 3.0 format with comprehensive 5-source integration.

## Security Reminders

**NEVER commit:**
- 2025/ folder
- confluence.properties
- .github_token
- .env files
- Any file containing salaries, ratings, or peer feedback

**Always gitignore:**
- Sensitive HR data
- Credentials and API keys
- Personal identifiable information (PII)

## Current Status

- Project initialized: January 2026
- Git repository: https://github.com/laguh1/people-management.git
- Structure: Complete
- Documentation: In progress
- Engineer tracking: Pending setup
- Performance reviews: 0/16 completed in this instance

## Notes for Future Sessions

1. **Check TEAM_ROSTER.md** - Verify engineer names and IDs before generating reviews
2. **Use symbolic links** - Link document-cruncher workspace to 2025/ folder for easy access
3. **Update tracking immediately** - Don't batch updates; update after each action
4. **Follow Version 3.0 format** - Maintain consistency across all reviews
5. **Test extractions first** - Verify document-cruncher can read PDFs before starting full workflow

## Key Metrics

- Total Engineers: 16
- Data Sources per Review: 5
- Target Review Length: 180-250 lines (12-20KB)
- Review Format Version: 3.0
- Integration Tools: 4 (document-cruncher, github-muncher, foundations, engineering-manager)

## References

- Reproduction Guide: `REPRODUCTION_GUIDE.md` (gitignored)
- Project README: `README.md`
- Tracking Dashboard: `Engineer_Tracking.md`
- Source Checklist: `PERFORMANCE_REVIEW_SOURCES.md`
