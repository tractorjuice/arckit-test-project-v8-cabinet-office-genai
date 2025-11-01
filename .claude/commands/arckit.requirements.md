---
description: Create comprehensive business and technical requirements
---

You are helping an enterprise architect define comprehensive requirements for a project that will be used for vendor RFPs and architecture reviews.

## User Input

```text
$ARGUMENTS
```

## Instructions

1. **Check for architecture principles and stakeholder analysis**:
   - First, check if `.arckit/memory/architecture-principles.md` exists
     - If it doesn't exist, suggest running `/arckit.principles` first
   - Then, check if a stakeholder analysis exists for this project
     - Look for `projects/*/stakeholder-drivers.md` files
     - If stakeholder analysis exists, read it to understand stakeholder goals and priorities
     - If it doesn't exist, strongly recommend running `/arckit.stakeholders` first to understand who cares and what they need
     - Stakeholder drivers should inform requirement prioritization and success criteria

2. **Create or find the project**:
   - Run `.arckit/scripts/bash/create-project.sh --name "$PROJECT_NAME" --json` to create project structure
   - Parse the JSON output to get the project directory path
   - Or if the user specifies an existing project number (e.g., "001"), use that

3. **Read the template**: Read `.arckit/templates/requirements-template.md` to understand the structure

4. **Generate comprehensive requirements** based on user input:

   **Business Requirements (BR-xxx)**:
   - Business objectives and success criteria
   - ROI and cost savings expectations
   - Timeline and milestones
   - Stakeholder needs

   **Functional Requirements (FR-xxx)**:
   - User personas and their needs
   - User stories and use cases
   - Features and capabilities
   - User workflows

   **Non-Functional Requirements (NFR-xxx)**:
   - Performance (response time, throughput, concurrent users)
   - Security (authentication, authorisation, encryption, compliance)
   - Scalability (growth projections, load handling)
   - Reliability (uptime SLA, MTBF, MTTR)
   - Compliance (regulations, standards, certifications)

   **Integration Requirements (INT-xxx)**:
   - Upstream/downstream systems
   - APIs and protocols
   - Data exchange formats
   - Authentication methods

   **Data Requirements (DR-xxx)**:
   - Data models and schemas
   - Data retention and archival
   - Data privacy and classification
   - Migration requirements

5. **Ensure traceability**: Each requirement MUST have:
   - Unique ID (BR-001, FR-001, NFR-P-001, etc.)
   - Clear requirement statement
   - Acceptance criteria (testable)
   - Priority (MUST/SHOULD/MAY)
   - Rationale

6. **Align with stakeholder goals and architecture principles**:
   - If stakeholder analysis exists, trace requirements back to stakeholder goals:
     - Example: "BR-001 addresses CFO's goal G-1: Reduce infrastructure costs 40% by end of Year 1"
     - Example: "NFR-P-001 supports Operations Director's outcome O-3: Maintain 99.95% uptime"
   - Reference relevant principles from `.arckit/memory/architecture-principles.md`:
     - Example: "NFR-S-001 aligns with Security by Design principle (SEC-001)"
   - Ensure high-priority stakeholder drivers get MUST requirements
   - Document which stakeholder benefits from each requirement

7. **Identify and resolve conflicting requirements**:
   - Review stakeholder analysis `conflict analysis` section for known competing drivers
   - Identify requirement conflicts that arise from stakeholder conflicts:
     - **Speed vs Quality**: CFO wants fast delivery vs Operations wants thorough testing
     - **Cost vs Features**: Finance wants minimal spend vs Product wants rich features
     - **Security vs Usability**: Security wants MFA vs Users want seamless experience
     - **Flexibility vs Standardization**: Business wants customization vs IT wants standards
   - For each conflict, document:
     - **Conflicting Requirements**: Which requirements are incompatible (e.g., FR-001 vs NFR-P-002)
     - **Stakeholders Involved**: Who wants what (e.g., CFO wants X, CTO wants Y)
     - **Trade-off Analysis**: What is gained and lost with each option
     - **Resolution Strategy**: How will this be resolved:
       - **Prioritize**: Choose one over the other based on stakeholder power/importance
       - **Compromise**: Find middle ground (e.g., MFA for admin, passwordless for regular users)
       - **Phase**: Satisfy both but at different times (e.g., MVP focused on speed, Phase 2 adds quality)
       - **Innovate**: Find creative solution that satisfies both (e.g., automated testing for speed AND quality)
   - **Decision Authority**: Reference stakeholder analysis RACI matrix for who decides
   - **Document Resolution**: Create explicit "Requirement Conflicts & Resolutions" section showing:
     - What was chosen and why
     - What was deferred or rejected
     - Which stakeholder "won" and which "lost"
     - How losing stakeholder will be managed (communication, future consideration)
   - **Transparency**: Be explicit about trade-offs - don't hide conflicts or pretend both can be satisfied

8. **Write the output**:
   - **CRITICAL - Token Efficiency**: Use the **Write tool** to create `projects/{project-dir}/requirements.md`
   - **DO NOT** output the full document in your response (this exceeds 32K token limit!)
   - Use the exact template structure
   - Include all sections even if some are TBD
   - MUST include "Requirement Conflicts & Resolutions" section if any conflicts exist




**CRITICAL - Auto-Populate Document Control Fields**:

Before completing the document, populate ALL document control fields in the header:

### Step 1: Generate Document ID
```bash
# Use the ArcKit document ID generation script
DOC_ID=$(.arckit/scripts/bash/generate-document-id.sh "${PROJECT_ID}" "REQ" "1.0")
# Example output: ARC-001-REQ-v1.0
```

### Step 2: Populate Required Fields

**Auto-populated fields** (populate these automatically):
- `[PROJECT_ID]` → Extract from project path (e.g., "001" from "projects/001-project-name")
- `[VERSION]` → Start with "1.0" for new documents
- `[DATE]` / `[YYYY-MM-DD]` → Current date in YYYY-MM-DD format
- `[DOCUMENT_TYPE_NAME]` → Use the document purpose (e.g., "Business and Technical Requirements")
- `ARC-[PROJECT_ID]-REQ-v[VERSION]` → Use generated DOC_ID from Step 1
- `[COMMAND]` → Current command name (e.g., "arckit.requirements")

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
| 1.0 | {DATE} | ArcKit AI | Initial creation from `/arckit.requirements` command | [PENDING] | [PENDING] |
```

### Step 4: Populate Generation Metadata Footer

The footer should be populated with:
```markdown
**Generated by**: ArcKit `/arckit.requirements` command
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
| **Document ID** | ARC-001-REQ-v1.0 |
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
| 1.0 | 2025-10-29 | ArcKit AI | Initial creation from `/arckit.requirements` command | [PENDING] | [PENDING] |
```


9. **Show summary only** (NOT the full document):

   After writing the file with Write tool, show ONLY this summary:

   ```markdown
   ## Requirements Complete ✅

   **Project**: [Project Name]
   **File Created**: `projects/[PROJECT]/requirements.md`

   ### Requirements Summary

   **Total Requirements**: [Number]
   - Business Requirements (BR-xxx): [Number]
   - Functional Requirements (FR-xxx): [Number]
   - Non-Functional Requirements (NFR-xxx): [Number]
     - Performance (NFR-P-xxx): [Number]
     - Security (NFR-SEC-xxx): [Number]
     - Scalability (NFR-S-xxx): [Number]
     - Availability (NFR-A-xxx): [Number]
     - Compliance (NFR-C-xxx): [Number]
   - Data Requirements (DR-xxx): [Number]
   - Integration Requirements (INT-xxx): [Number]

   **Requirement Conflicts**: [Number] conflicts identified and resolved
   - [Brief summary of key conflicts and resolutions]
   - [Which stakeholders won/lost in conflicts]

   **Compliance Requirements**:
   - [List key compliance frameworks: PCI-DSS, GDPR, HIPAA, etc.]

   **Key Gaps/TBDs**:
   - [List any major gaps that need follow-up]

   ### What's in the Document

   - Business Requirements with measurable success criteria
   - Functional Requirements organized by user journey
   - Non-Functional Requirements with specific targets
   - Data Requirements with GDPR considerations
   - Integration Requirements with third-party systems
   - Acceptance Criteria for each requirement
   - Requirements Traceability Matrix
   - Requirement Conflicts & Resolutions

   ### Next Steps

   - Review `requirements.md` for full details
   - [If DR-xxx exist]: Run `/arckit.data-model` to create comprehensive data model
   - [If no DR-xxx]: Run `/arckit.research` to research technology options
   ```

## Example Usage

User: `/arckit.requirements Create requirements for a payment gateway modernization project`

You should:
- Check for architecture principles
- Create project "payment-gateway-modernization" (gets number 001)
- Generate comprehensive requirements:
  - Business: Cost savings, improved conversion, reduced downtime
  - Functional: Payment processing, refunds, fraud detection, reporting
  - NFR: PCI-DSS compliance, 99.99% uptime, <2s response time, encryption
  - Integration: CRM, accounting system, fraud service
  - Data: Transaction records, PII handling, 7-year retention
- Write to `projects/001-payment-gateway-modernization/requirements.md`
- Confirm completion with summary

## Important Notes

- Requirements drive everything: SOW, vendor evaluation, design reviews, testing
- Be specific and measurable (avoid "fast", use "<2 seconds")
- Include WHY (rationale) not just WHAT
- Make acceptance criteria testable
- Flag compliance requirements clearly (PCI-DSS, HIPAA, SOX, GDPR, etc.)
