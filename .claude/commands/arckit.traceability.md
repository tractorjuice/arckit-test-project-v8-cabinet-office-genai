---
description: Generate requirements traceability matrix from requirements to design to tests
---

You are helping an enterprise architect create a comprehensive traceability matrix that traces requirements through design to implementation and testing.

## User Input

```text
$ARGUMENTS
```

## Instructions

1. **Identify the project**: The user should specify a project name or number
   - Example: "Generate traceability matrix for payment gateway project"
   - Example: "Update traceability for project 001"

2. **Read all project artifacts**:
   - Read `projects/{project-dir}/requirements.md` - Source of truth for all requirements
   - Read `projects/{project-dir}/vendors/{vendor}/hld.md` - High-level design
   - Read `projects/{project-dir}/vendors/{vendor}/dld.md` - Detailed design
   - Read `projects/{project-dir}/vendors/{vendor}/hld-review.md` - Review findings
   - Read `projects/{project-dir}/vendors/{vendor}/dld-review.md` - Review findings
   - Read `.arckit/templates/traceability-matrix-template.md` - Template structure

3. **Build the traceability matrix**:

   ### Forward Traceability (Requirements → Design → Implementation → Tests)

   For each requirement (BR, FR, NFR, INT, DR):

   **Step 1: Requirement Details**
   - Requirement ID (e.g., FR-001)
   - Requirement statement
   - Priority (MUST/SHOULD/MAY)
   - Category (Business/Functional/Non-Functional/Integration/Data)

   **Step 2: Design Mapping**
   - Which HLD components implement this requirement?
   - Which DLD modules/classes handle this?
   - Architecture patterns used
   - Design decisions made

   **Step 3: Implementation Mapping**
   - Source code files/modules (if available)
   - APIs/endpoints that satisfy this
   - Database tables/schemas involved
   - Configuration requirements

   **Step 4: Test Coverage**
   - Unit test references
   - Integration test scenarios
   - Performance test cases (for NFRs)
   - Security test cases (for security requirements)
   - UAT test cases

   **Step 5: Status**
   - ✅ Fully implemented and tested
   - 🔄 In progress
   - ⏳ Planned
   - ❌ Not covered (GAP!)

   ### Backward Traceability (Tests → Implementation → Design → Requirements)

   For each test case:
   - Which requirements does it verify?
   - Which design components does it test?
   - What's the expected outcome?

   ### Gap Analysis

   Identify and flag:
   - **Orphan Requirements**: Requirements with NO design/implementation
   - **Orphan Design Elements**: Design components not linked to requirements (scope creep?)
   - **Orphan Tests**: Tests not linked to requirements (what are they testing?)
   - **Coverage Gaps**: Requirements without adequate test coverage

4. **Analyze coverage metrics**:

   Calculate and report:
   - **Requirements Coverage**: % of requirements with design mapping
   - **Implementation Coverage**: % of requirements implemented
   - **Test Coverage**: % of requirements with tests
   - **By Priority**:
     - MUST requirements: Should be 100% covered
     - SHOULD requirements: Should be >80% covered
     - MAY requirements: Can be <50% covered

   Example:
   ```
   Overall Coverage:
   - Business Requirements: 15/15 (100%)
   - Functional Requirements: 42/45 (93%) - 3 gaps
   - Non-Functional Requirements: 18/22 (82%) - 4 gaps
   - Integration Requirements: 8/8 (100%)

   Priority Coverage:
   - MUST requirements: 68/70 (97%) - 2 CRITICAL GAPS
   - SHOULD requirements: 12/15 (80%)
   - MAY requirements: 3/8 (38%)
   ```

5. **Risk Assessment**:

   Flag high-risk gaps:
   - **CRITICAL**: MUST requirements not covered
   - **HIGH**: Security/compliance requirements without tests
   - **MEDIUM**: Performance requirements without validation
   - **LOW**: Optional features not implemented

6. **Generate Traceability Report**:

   Create comprehensive report with:

   **Executive Summary**:
   - Overall traceability score (0-100)
   - Coverage by requirement type
   - Critical gaps requiring attention
   - Recommendation (Ready for Release / Gaps Must Be Addressed)

   **Detailed Traceability Matrix**:
   Large table with columns:
   | Req ID | Requirement | Priority | HLD Component | DLD Module | Implementation | Tests | Status |

   **Gap Analysis**:
   - List of orphan requirements (requirements not in design)
   - List of orphan design elements (design not in requirements - scope creep!)
   - List of untested requirements
   - Recommendations for each gap

   **Coverage Metrics**:
   - Visual representation (can use markdown tables/charts)
   - Breakdown by requirement type
   - Breakdown by priority
   - Trend over time (if multiple traceability runs)

   **Action Items**:
   - BLOCKING gaps (must fix before release)
   - Non-blocking gaps (fix in next sprint)
   - Technical debt to track

7. **Write outputs**:
   - `projects/{project-dir}/traceability-matrix.md` - Full traceability matrix
   - `projects/{project-dir}/coverage-report.md` - Coverage metrics and gaps
   - `projects/{project-dir}/gaps.md` - Detailed gap analysis with remediation plan



**CRITICAL - Auto-Populate Document Control Fields**:

Before completing the document, populate ALL document control fields in the header:

### Step 1: Generate Document ID
```bash
# Use the ArcKit document ID generation script
DOC_ID=$(.arckit/scripts/bash/generate-document-id.sh "${PROJECT_ID}" "TRAC" "1.0")
# Example output: ARC-001-TRAC-v1.0
```

### Step 2: Populate Required Fields

**Auto-populated fields** (populate these automatically):
- `[PROJECT_ID]` → Extract from project path (e.g., "001" from "projects/001-project-name")
- `[VERSION]` → Start with "1.0" for new documents
- `[DATE]` / `[YYYY-MM-DD]` → Current date in YYYY-MM-DD format
- `[DOCUMENT_TYPE_NAME]` → Use the document purpose (e.g., "Business and Technical Requirements")
- `ARC-[PROJECT_ID]-TRAC-v[VERSION]` → Use generated DOC_ID from Step 1
- `[COMMAND]` → Current command name (e.g., "arckit.traceability")

**User-provided fields** (extract from project metadata or user input):
- `[PROJECT_NAME]` → Full project name from project metadata or user input
- `[OWNER_NAME_AND_ROLE]` → Document owner (prompt user if not in metadata)
- `[CLASSIFICATION]` → Default to "OFFICIAL" for UK Gov, "PUBLIC" otherwise (or prompt user)

**Calculated fields**:
- `[YYYY-MM-DD]` for Review Date → Current date + 30 days (requirements, research, risks)
- `[YYYY-MM-DD]` for Review Date → Phase gate dates (Alpha/Beta/Live for compliance docs)

**Pending fields** (leave as [PENDING] until manually updated):
- `[REVIEWER_NAME]` → [PENDING]
- `[APPROVER_NAME]` → [PENDING]
- `[DISTRIBUTION_LIST]` → Default to "Project Team, Architecture Team" or [PENDING]

### Step 3: Populate Revision History

```markdown
| 1.0 | {DATE} | ArcKit AI | Initial creation from `/arckit.traceability` command | [PENDING] | [PENDING] |
```

### Step 4: Populate Generation Metadata Footer

The footer should be populated with:
```markdown
**Generated by**: ArcKit `/arckit.traceability` command
**Generated on**: {DATE} {TIME} GMT
**ArcKit Version**: [Read from .arckit/VERSION file or use "0.6.0"]
**Project**: {PROJECT_NAME} (Project {PROJECT_ID})
**AI Model**: [Use actual model name, e.g., "claude-sonnet-4-5-20250929"]
**Generation Context**: [Brief note about source documents used]
```

### Example Fully Populated Document Control Section:

```markdown
## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-001-TRAC-v1.0 |
| **Document Type** | {Document purpose} |
| **Project** | Windows 10 to Windows 11 Migration (Project 001) |
| **Classification** | OFFICIAL-SENSITIVE |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2025-10-29 |
| **Last Modified** | 2025-10-29 |
| **Review Date** | 2025-11-30 |
| **Owner** | John Smith (Business Analyst) |
| **Reviewed By** | [PENDING] |
| **Approved By** | [PENDING] |
| **Distribution** | PM Team, Architecture Team, Dev Team |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2025-10-29 | ArcKit AI | Initial creation from `/arckit.traceability` command | [PENDING] | [PENDING] |
```

## Example Usage

User: `/arckit.traceability Generate traceability matrix for payment gateway project`

You should:
- Read requirements.md (70 requirements total)
- Read HLD and DLD documents
- Read review documents for implementation details
- Build forward traceability:
  - FR-001 (Process payment) → PaymentService (HLD) → PaymentController.processPayment() (DLD) → Test: TC-001, TC-002
  - NFR-S-001 (PCI-DSS) → SecurityArchitecture (HLD) → TokenVault, Encryption (DLD) → Test: SEC-001 to SEC-015
  - BR-003 (Cost savings) → [NO DESIGN MAPPING] - ORPHAN! (GAP)
- Calculate coverage:
  - Business Requirements: 14/15 (93%) - BR-003 missing!
  - Functional Requirements: 45/45 (100%)
  - Non-Functional Requirements: 20/22 (91%) - NFR-R-002, NFR-P-003 missing tests
  - Integration Requirements: 8/8 (100%)
- Identify gaps:
  - CRITICAL: BR-003 (Cost savings) has no success metrics defined
  - HIGH: NFR-R-002 (99.99% uptime) has no disaster recovery tests
  - MEDIUM: NFR-P-003 (Database performance) missing load tests
- **Overall Score**: 85/100 (Good, but gaps must be addressed)
- **Recommendation**: APPROVED WITH CONDITIONS - address 3 critical gaps
- Write detailed matrix to `projects/001-payment-gateway/traceability-matrix.md`
- Write gap analysis to `projects/001-payment-gateway/gaps.md`

## Important Notes

- Traceability is required for compliance (ISO, FDA, automotive, etc.)
- Every MUST requirement MUST be traced to tests (non-negotiable)
- Orphan design elements may indicate scope creep (investigate!)
- Orphan requirements may indicate incomplete design (blocking issue!)
- Traceability matrix should be updated throughout project lifecycle
- Use this for:
  - Go/no-go release decisions
  - Audit trail for compliance
  - Impact analysis for change requests
  - Test coverage verification
- A requirement is only "done" when it's implemented AND tested
- Missing traceability = missing accountability
