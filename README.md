# People Management

Engineering management toolkit for team performance reviews, GitHub contribution tracking, and HR document processing.

## Overview

This project coordinates performance review workflows by integrating data from multiple sources:
- End-of-year performance PDFs (official ratings, manager comments)
- Mid-year self-assessments (goals, reflections)
- 360° feedback forms (peer reviews, competency ratings)
- GitHub contribution reports (quantitative metrics)
- Manager observations and 1-on-1 notes

## Key Features

### 1. Performance Review Generation
- Evidence-based reviews combining 5 data sources
- Version 3.0 format: Executive summary, ratings breakdown, goal analysis, 360° feedback synthesis
- 12-20KB structured markdown documents (180-250 lines)

### 2. Engineer Tracking Dashboard
- Status tracker for all 16 engineers (`Engineer_Tracking.md`)
- Track: review completion, ratings, GitHub reports, Confluence uploads, meetings
- Statistics: completion percentages, average ratings, pending items

### 3. Data Extraction Pipeline
- Integrates with `document-cruncher` for PDF/DOCX/Excel extraction
- Integrates with `github-muncher` for GitHub contribution analysis
- Integrates with `foundations-features-documentation` for Confluence uploads

## Project Structure

```
people_management/
├── README.md                           # This file
├── CLAUDE.md                           # Project memory
├── history.md                          # Session history
├── Engineer_Tracking.md                # Status tracker (16 engineers)
├── PERFORMANCE_REVIEW_SOURCES.md       # Data sources checklist
├── .gitignore                          # Exclude 2025/ folder
├── github_tracking/                    # GitHub analysis (deprecated)
└── 2025/                               # Sensitive HR data (gitignored)
    ├── EOY performance/                # EOY PDFs
    ├── mid year performance/           # MYR Excel, 360° feedback
    ├── Promotions/                     # Promotion letters
    ├── 2025 salary increase/           # Salary letters
    └── output/                         # Generated documents
```

## Integration with Existing Tools

### 1. document-cruncher (`~/Projects/claude/document-cruncher`)
Extract text from PDFs, DOCX, and Excel files:
```bash
document-cruncher extract-pdf 2025/EOY\ performance/EOY\ reviews/Engineer.pdf
document-cruncher extract-excel 2025/mid\ year\ performance/MYR.xlsx --employee "Name"
```

### 2. github-muncher (`~/Projects/claude/github-muncher`)
Generate GitHub contribution reports:
```bash
github-muncher generate-report --engineer "Name" --period eoy_2025
```

### 3. foundations-features-documentation
Upload performance reviews to Confluence:
```bash
python confluence_manager.py create SPACE "Name - Review 2025" --content-file [path]
```

## Quick Start

### 1. Track Engineer Status
Edit `Engineer_Tracking.md` to track review completion, ratings, and milestones.

### 2. Gather Data Sources
Follow `PERFORMANCE_REVIEW_SOURCES.md` checklist to collect all required documents.

### 3. Extract Data
Use document-cruncher to extract text from EOY PDFs, MYR Excel, and 360° feedback.

### 4. Generate GitHub Report
Use github-muncher to analyze GitHub contributions.

### 5. Compile Review
Combine all sources into a structured performance review using the template.

### 6. Update Tracking
Mark review as complete in Engineer_Tracking.md with final rating and dates.

## Security & Data Protection

**CRITICAL**: The `2025/` folder contains sensitive HR data and is excluded from version control.

Protected data:
- EOY performance PDFs (salary, ratings, manager comments)
- Salary increase letters
- Promotion letters
- 360° feedback (confidential peer reviews)
- Manager 1-on-1 notes

**Never commit the 2025/ folder to git.**

## Workflows

### Complete Performance Review Pipeline

```bash
# 1. Extract all data
document-cruncher extract-pdf 2025/EOY\ performance/EOY\ reviews/Engineer.pdf
document-cruncher extract-excel 2025/mid\ year\ performance/MYR.xlsx --employee "Name"
document-cruncher extract-excel 2025/mid\ year\ performance/360.xlsx --employee "Name"

# 2. Generate GitHub report
github-muncher generate-report --engineer "Name" --period eoy_2025

# 3. Compile review using template
# Combine all 5 data sources into Version 3.0 format

# 4. Update tracking
# Edit Engineer_Tracking.md: Add ✅ status, rating, dates

# 5. Upload to Confluence
cd ~/Projects/claude/foundations-features-documentation
python confluence_manager.py create SPACE "Name - Review 2025" --content-file [path]
```

## Files

- `Engineer_Tracking.md` - Central tracking dashboard for all 16 engineers
- `PERFORMANCE_REVIEW_SOURCES.md` - Checklist of data sources to gather
- `CLAUDE.md` - Project context and memory for Claude AI
- `history.md` - Session history and changes log

## Dependencies

This project coordinates workflows but relies on external tools:
- `document-cruncher` - File extraction
- `github-muncher` - GitHub analysis
- `foundations-features-documentation` - Confluence integration

No separate installation required for this coordination project.

## License

Private - Internal HR tool for engineering management.

## Contact

For questions or issues, contact the engineering manager.
