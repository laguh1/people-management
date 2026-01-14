# Performance Review Data Sources Checklist

This checklist ensures all required data sources are gathered before compiling a performance review.

## Engineer Information

**Engineer Name**: _________________________

**Employee ID**: _________________________

**Review Period**: 2025

---

## Data Source #1: EOY Performance PDF

**Priority**: HIGHEST (Official ratings and manager comments)

- [ ] **File Located**: `2025/EOY performance/EOY reviews/[Engineer-Name]-EOY.pdf`
- [ ] **Extracted to Text**: `2025/output/processing_aid/[Engineer-Name]-EOY-extracted.txt`
- [ ] **Contains**:
  - [ ] Official overall rating (1-4 scale)
  - [ ] WHAT rating (Technical Delivery)
  - [ ] HOW rating (Collaboration & Behavior)
  - [ ] Risk Modifier (Resilience & Adaptability)
  - [ ] Manager comments and assessment
  - [ ] Final approval signatures

**Extraction Command**:
```bash
document-cruncher extract-pdf "2025/EOY performance/EOY reviews/[Engineer-Name]-EOY.pdf" \
  -o "2025/output/processing_aid/[Engineer-Name]-EOY-extracted.txt"
```

---

## Data Source #2: Mid-Year Review Self-Assessment

**Priority**: HIGH (Employee's goals and reflections)

- [ ] **File Located**: `2025/mid year performance/Mid-Year Review Form.xlsx`
- [ ] **Employee Row Identified**: Engineer name found in Excel sheet
- [ ] **Extracted to JSON**: `2025/output/processing_aid/[Engineer-Name]-MYR.json`
- [ ] **Contains**:
  - [ ] 5 goals with status and progress
  - [ ] Self-reflection on achievements
  - [ ] Challenges and learning
  - [ ] Development areas identified by employee

**Extraction Command**:
```bash
document-cruncher extract-excel "2025/mid year performance/Mid-Year Review Form.xlsx" \
  --employee "[Engineer Name]" --format json \
  -o "2025/output/processing_aid/[Engineer-Name]-MYR.json"
```

---

## Data Source #3: 360° Feedback Forms

**Priority**: HIGH (Peer reviews and competency ratings)

### 3a. 360° Feedback Excel (Quantitative Ratings)

- [ ] **File Located**: `2025/mid year performance/360° Feedback Form.xlsx`
- [ ] **Employee Feedback Found**: All peer reviews for this engineer
- [ ] **Extracted to JSON**: `2025/output/processing_aid/[Engineer-Name]-360-Feedback.json`
- [ ] **Contains**:
  - [ ] Peer competency ratings (typically 5-10 reviewers)
  - [ ] Ratings across technical, collaboration, communication dimensions
  - [ ] Quantitative scores

**Extraction Command**:
```bash
document-cruncher extract-excel "2025/mid year performance/360° Feedback Form.xlsx" \
  --employee "[Engineer Name]" --format json \
  -o "2025/output/processing_aid/[Engineer-Name]-360-Feedback.json"
```

### 3b. 360° Feedback Documents (Qualitative Comments)

- [ ] **File Located**: `2025/mid year performance/feedback documents/[Engineer-Name]-360-Feedback.docx`
- [ ] **Extracted to Markdown**: `2025/output/processing_aid/[Engineer-Name]-360-Comments.md`
- [ ] **Contains**:
  - [ ] Written peer feedback and comments
  - [ ] Specific examples and observations
  - [ ] Qualitative insights

**Extraction Command**:
```bash
document-cruncher extract-docx "2025/mid year performance/feedback documents/[Engineer-Name]-360-Feedback.docx" \
  -o "2025/output/processing_aid/[Engineer-Name]-360-Comments.md"
```

---

## Data Source #4: GitHub Contribution Report

**Priority**: MEDIUM (Quantitative metrics for technical delivery)

- [ ] **Report Generated**: Via github-muncher CLI
- [ ] **Saved to**: `2025/output/github_reports/[Engineer-Name]-GitHub-Report-2025.md`
- [ ] **Contains**:
  - [ ] Total commits and lines changed
  - [ ] Pull requests created and reviewed
  - [ ] Code review participation
  - [ ] Issues created/resolved
  - [ ] Collaboration scores
  - [ ] Repository contributions

**Generation Command**:
```bash
cd ~/Projects/claude/github-muncher
source .venv/bin/activate
github-muncher generate-report --engineer "[Engineer Name]" --period eoy_2025 \
  --output ~/Projects/claude/people_management/2025/output/github_reports/
```

---

## Data Source #5: Manager Notes & Observations

**Priority**: MEDIUM (Direct observations and 1-on-1 context)

- [ ] **1-on-1 Meeting Notes Reviewed**: Personal observations from regular meetings
- [ ] **Key Observations Documented**:
  - [ ] Technical growth and skill development
  - [ ] Team collaboration and communication
  - [ ] Project ownership and initiative
  - [ ] Challenges overcome
  - [ ] Areas for improvement
- [ ] **Direct Quotes Identified**: Specific feedback from manager

**Location**: Personal notes, meeting logs, Confluence pages (not stored in git)

---

## Additional Documents (Optional)

### Salary Increase Letter
- [ ] **File Located**: `2025/2025 salary increase/[Engineer-Name]-Salary-Letter.pdf`
- [ ] **Reviewed**: Salary adjustment details

### Promotion Letter
- [ ] **File Located**: `2025/Promotions/[Engineer-Name]-Promotion-Letter.pdf`
- [ ] **Reviewed**: Promotion details and new role

---

## Confluence Integration

- [ ] **Engineer Profile Page Located**: Confluence profile URL
- [ ] **Project Documentation Reviewed**: Engineer's Confluence contributions
- [ ] **Technical Blog Posts Reviewed**: Engineer's knowledge sharing

**Confluence URL**: _________________________________

---

## Data Validation

Before compiling the review, verify:

- [ ] All 5 primary data sources are gathered
- [ ] Extracted files are readable and complete
- [ ] Data is from 2025 review period
- [ ] Employee ID matches across all sources
- [ ] No conflicting information between sources

## Data Priority for Conflicts

If data sources conflict, use this priority:
1. **EOY Performance PDF** (official ratings - highest authority)
2. **MYR Self-Assessment** (employee perspective)
3. **360° Feedback** (peer perspective)
4. **GitHub Reports** (quantitative data)
5. **Manager Notes** (additional context)

---

## Compilation Checklist

Once all sources are gathered:

- [ ] Create performance review document from template
- [ ] Synthesize data from all 5 sources
- [ ] Include specific examples and quotes
- [ ] Follow Version 3.0 format structure
- [ ] Add cost footer (if using AI compilation)
- [ ] Save to: `2025/output/EOY reports/[Engineer-Name]-Performance-Review-2025.md`
- [ ] Update Engineer_Tracking.md with completion status
- [ ] Upload to Confluence (if required)

---

## Notes

**Date Started**: _________________________

**Date Completed**: _________________________

**Review Rating**: _________________________

**Special Considerations**:

_____________________________________________________________________________

_____________________________________________________________________________

---

*Use this checklist for each engineer to ensure comprehensive, evidence-based performance reviews.*
