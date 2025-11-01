---
description: Perform comprehensive governance quality analysis across architecture artifacts (requirements, principles, designs, assessments)
---

## User Input

```text
$ARGUMENTS
```

## Goal

Identify inconsistencies, gaps, ambiguities, and compliance issues across all architecture governance artifacts before implementation or procurement. This command performs **non-destructive analysis** and produces a structured report saved to the project directory for tracking and audit purposes.

## Operating Constraints

**Non-Destructive Analysis**: Do **not** modify existing artifacts. Generate a comprehensive analysis report and save it to the project directory for tracking, sharing, and audit trail.

**Architecture Principles Authority**: The architecture principles (`.arckit/memory/architecture-principles.md`) are **non-negotiable**. Any conflicts with principles are automatically CRITICAL and require adjustment of requirements, designs, or vendor proposals—not dilution or reinterpretation of the principles.

**UK Government Compliance Authority** (if applicable): TCoP, AI Playbook, and ATRS compliance are mandatory for UK government projects. Non-compliance is CRITICAL.

## Execution Steps

### 1. Discover Project Context

Identify the project directory to analyze:
- If user specifies project: Use specified project directory
- If only one project exists: Analyze that project
- If multiple projects: Ask user which project to analyze

Expected structure:
```
projects/
└── {project-dir}/
    ├── stakeholder-drivers.md (RECOMMENDED - added v0.2.1)
    ├── risk-register.md (RECOMMENDED - added v0.3.0)
    ├── sobc.md (RECOMMENDED - added v0.3.0)
    ├── requirements.md
    ├── data-model.md (if DR-xxx requirements exist - added v0.3.1)
    ├── sow.md (if vendor procurement)
    ├── evaluation-criteria.md (if vendor procurement)
    ├── vendors/
    │   └── {vendor-name}/
    │       ├── hld-v1.md
    │       ├── dld-v1.md
    │       └── reviews/
    ├── tcop-assessment.md (if UK Gov)
    ├── ai-playbook-assessment.md (if UK Gov AI)
    ├── atrs-record.md (if UK Gov AI)
    ├── mod-secure-by-design.md (if MOD project)
    └── traceability-matrix.md
```

### 2. Load Artifacts (Progressive Disclosure)

Load only minimal necessary context from each artifact:

**From `.arckit/memory/architecture-principles.md`** (if exists):
- Strategic principles (Cloud-First, API-First, etc.)
- Security principles
- Data principles
- Technology standards
- Compliance requirements

**From `projects/{project-dir}/stakeholder-drivers.md`** (if exists):
- Stakeholder roster with power-interest grid
- Driver types (STRATEGIC, OPERATIONAL, FINANCIAL, COMPLIANCE, PERSONAL, RISK, CUSTOMER)
- Driver → Goal → Outcome traceability
- Conflicts and resolutions
- RACI matrix for governance

**From `projects/{project-dir}/risk-register.md`** (if exists):
- Risk categories (Strategic, Operational, Financial, Compliance, Reputational, Technology)
- Inherent vs Residual risk scores (5×5 matrix)
- Risk responses (4Ts: Tolerate, Treat, Transfer, Terminate)
- Risk owners (should align with RACI matrix)
- Risk appetite and tolerance levels

**From `projects/{project-dir}/sobc.md`** (if exists):
- Strategic Case (problem, drivers, stakeholder goals)
- Economic Case (options, benefits, NPV, ROI)
- Commercial Case (procurement strategy)
- Financial Case (budget, TCO)
- Management Case (governance, delivery, change, risks, benefits realization)

**From `projects/{project-dir}/requirements.md`** (if exists):
- Business requirements (BR-xxx)
- Functional requirements (FR-xxx)
- Non-functional requirements (NFR-xxx)
  - Security (NFR-S-xxx)
  - Performance (NFR-P-xxx)
  - Compliance (NFR-C-xxx)
  - Accessibility (NFR-A-xxx)
- Integration requirements (INT-xxx)
- Data requirements (DR-xxx)
- Success criteria

**From `projects/{project-dir}/data-model.md`** (if exists):
- Entity-Relationship Diagram (ERD)
- Entity catalog (E-001, E-002, etc.)
- PII identification and GDPR compliance
- Data governance matrix (owners, stewards, custodians)
- CRUD matrix (component access patterns)
- Data integration mapping (upstream/downstream)
- DR-xxx requirement traceability to entities

**From `projects/{project-dir}/sow.md`** (if exists):
- Scope of work
- Deliverables
- Technical requirements
- Timeline and budget

**From `projects/{project-dir}/vendors/{vendor}/hld-v*.md`** (if exists):
- Architecture overview
- Component design
- Technology stack
- Security architecture
- Data architecture

**From `projects/{project-dir}/vendors/{vendor}/dld-v*.md`** (if exists):
- Component specifications
- API contracts
- Database schemas
- Security implementation

**From UK Government Assessments** (if exist):
- `tcop-assessment.md`: TCoP compliance status
- `ai-playbook-assessment.md`: AI Playbook compliance status
- `atrs-record.md`: ATRS record completeness

**From MOD Assessment** (if exists):
- `mod-secure-by-design.md`: MOD SbD compliance status
  - 7 SbD Principles assessment
  - NIST CSF (Identify, Protect, Detect, Respond, Recover)
  - CAAT registration and self-assessment completion
  - Three Lines of Defence
  - Delivery Team Security Lead (DTSL) appointment
  - Supplier attestation (for vendor-delivered systems)

### 3. Build Semantic Models

Create internal representations (do not include raw artifacts in output):

**Stakeholder Traceability Matrix** (if stakeholder-drivers.md exists):
- Each stakeholder with drivers, goals, outcomes
- RACI roles for governance
- Conflicts and resolutions
- Which requirements trace to which stakeholder goals?

**Risk Coverage Matrix** (if risk-register.md exists):
- Each risk with category, inherent/residual scores, response
- Risk owners from RACI matrix
- Which requirements address risk mitigation?
- Which design elements mitigate risks?

**Business Case Alignment Matrix** (if sobc.md exists):
- Benefits mapping to stakeholder goals
- Benefits mapping to requirements
- Costs mapping to requirements scope
- Risks from risk register reflected in Management Case

**Requirements Inventory**:
- Each requirement with ID, type, priority (MUST/SHOULD/MAY)
- Map to principles (which principles does this requirement satisfy?)
- Map to stakeholder goals (which goals does this requirement address?)
- Map to success criteria

**Data Model Coverage Matrix** (if data-model.md exists):
- Each DR-xxx requirement mapped to entities
- Each entity with PII flags, governance owners, CRUD access
- Data owners from stakeholder RACI matrix
- Database schema in DLD matches data model entities

**Principles Compliance Matrix**:
- Each principle with validation criteria
- Which requirements/designs satisfy each principle?

**Design Coverage Matrix**:
- Which requirements are addressed in HLD/DLD?
- Which components implement which requirements?

**UK Government Compliance Matrix** (if applicable):
- TCoP: 13 points with compliance status
- AI Playbook: 10 principles + 6 themes with compliance status
- ATRS: Mandatory fields completion status

**MOD Compliance Matrix** (if mod-secure-by-design.md exists):
- 7 SbD Principles with compliance status
- NIST CSF functions (Identify, Protect, Detect, Respond, Recover)
- CAAT registration status
- Three Lines of Defence implementation

### 4. Detection Passes (Token-Efficient Analysis)

Focus on high-signal findings. Limit to 50 findings total; aggregate remainder in overflow summary.

#### A. Requirements Quality Analysis

**Duplication Detection**:
- Near-duplicate requirements across BR/FR/NFR categories
- Redundant requirements that should be consolidated

**Ambiguity Detection**:
- Vague adjectives lacking measurable criteria ("fast", "secure", "scalable", "intuitive")
- Missing acceptance criteria for functional requirements
- Unresolved placeholders (TODO, TBD, TBC, ???, `<placeholder>`)

**Underspecification**:
- Requirements with verbs but missing measurable outcomes
- Missing non-functional requirements (no security, no performance, no compliance)
- Missing data requirements (system handles sensitive data but no DR-xxx)
- Missing integration requirements (integrates with external systems but no INT-xxx)

**Priority Issues**:
- All requirements marked as MUST (no prioritization)
- No MUST requirements (everything is optional)
- Conflicting priorities

#### B. Architecture Principles Alignment

**Principle Violations** (CRITICAL):
- Requirements or designs that violate architecture principles
- Technology choices that conflict with approved stack
- Security approaches that violate security-by-design principle
- Cloud architecture that violates Cloud-First principle

**Missing Principle Coverage**:
- Principles not reflected in requirements
- Principles not validated in design reviews

**Principle Drift**:
- Inconsistent interpretation of principles across artifacts

#### C. Requirements → Design Traceability

**Coverage Gaps**:
- Requirements with zero design coverage (not addressed in HLD/DLD)
- Critical MUST requirements not covered
- Security requirements (NFR-S-xxx) not reflected in security architecture
- Performance requirements (NFR-P-xxx) not validated in design
- Compliance requirements (NFR-C-xxx) not addressed

**Orphan Design Elements**:
- Components in HLD/DLD not mapped to any requirement
- Technology choices not justified by requirements
- Architecture complexity not justified by requirements

**Traceability Completeness**:
- Does traceability matrix exist?
- Are all requirements mapped?
- Are all design elements mapped?

#### D. Vendor Procurement Analysis (if applicable)

**SOW Quality**:
- SOW requirements match requirements.md?
- All technical requirements from requirements.md included in SOW?
- Missing evaluation criteria?
- Ambiguous acceptance criteria?

**Vendor Evaluation**:
- Evaluation criteria align with requirements priorities?
- Scoring methodology fair and unbiased?
- All critical requirements included in evaluation?

**Vendor Design Review**:
- HLD addresses all SOW requirements?
- Technology stack matches approved standards?
- Security architecture meets NFR-S requirements?
- Performance architecture meets NFR-P requirements?

#### E. Stakeholder Traceability Analysis (if stakeholder-drivers.md exists)

**Stakeholder Coverage**:
- All requirements traced to stakeholder goals?
- Orphan requirements (not linked to any stakeholder goal)?
- Requirements missing stakeholder justification?

**Conflict Resolution**:
- Requirement conflicts documented and resolved?
- Stakeholder impact of conflict resolutions documented?
- Decision authority identified for conflicting requirements?

**RACI Governance Alignment**:
- Risk owners from stakeholder RACI matrix?
- Data owners from stakeholder RACI matrix?
- Delivery roles aligned with RACI assignments?

**Missing Stakeholder Analysis**:
- Project has requirements but no stakeholder analysis (RECOMMENDED to run `/arckit.stakeholders`)

#### F. Risk Management Analysis (if risk-register.md exists)

**Risk Coverage**:
- High/Very High inherent risks have mitigation requirements?
- Risks reflected in design (risk mitigation controls in HLD/DLD)?
- Risk owners assigned and aligned with RACI matrix?
- Risk responses appropriate (4Ts: Tolerate, Treat, Transfer, Terminate)?

**Risk-SOBC Alignment** (if sobc.md exists):
- Strategic risks reflected in Strategic Case urgency?
- Financial risks reflected in Economic Case cost contingency?
- Risks from risk register included in Management Case Part E?

**Risk-Requirements Alignment**:
- Risk mitigation actions translated into requirements?
- Security risks addressed by NFR-S-xxx requirements?
- Compliance risks addressed by NFR-C-xxx requirements?

**Missing Risk Assessment**:
- Project has requirements but no risk register (RECOMMENDED to run `/arckit.risk`)

#### G. Business Case Alignment (if sobc.md exists)

**Benefits Traceability**:
- All benefits in Economic Case mapped to stakeholder goals?
- All benefits supported by requirements?
- Benefits measurable and verifiable?
- Benefits realization plan in Management Case?

**Option Analysis Quality**:
- Do Nothing baseline included?
- Options analysis covers build vs buy?
- Recommended option justified by requirements scope?
- Costs realistic for requirements complexity?

**SOBC-Requirements Alignment**:
- Strategic Case drivers reflected in requirements?
- Economic Case benefits delivered by requirements?
- Financial Case budget adequate for requirements scope?
- Management Case delivery plan realistic for requirements?

**SOBC-Risk Alignment**:
- Risks from risk register included in Management Case?
- Cost contingency reflects financial risks?
- Strategic risks justify urgency ("Why Now?")?

**Missing Business Case**:
- Project has requirements but no SOBC (RECOMMENDED for major investments to run `/arckit.sobc`)

#### H. Data Model Consistency (if data-model.md exists)

**DR-xxx Requirements Coverage**:
- All DR-xxx requirements mapped to entities?
- All entities traced back to DR-xxx requirements?
- Missing data requirements (system handles data but no DR-xxx)?

**Data Model-Design Alignment**:
- Database schemas in DLD match data model entities?
- CRUD matrix aligns with component design in HLD?
- Data integration flows in HLD match data model upstream/downstream mappings?

**Data Governance Alignment**:
- Data owners from stakeholder RACI matrix?
- Data stewards and custodians assigned?
- PII identified and GDPR compliance documented?

**Data Model Quality**:
- ERD exists and renderable (Mermaid syntax)?
- Entities have complete attribute specifications?
- Relationships properly defined (cardinality, foreign keys)?
- Data quality metrics defined and measurable?

**Missing Data Model**:
- Project has DR-xxx requirements but no data model (RECOMMENDED to run `/arckit.data-model`)

#### I. UK Government Compliance (if applicable)

**Technology Code of Practice (TCoP)**:
- Assessment exists?
- All 13 points assessed?
- Critical issues resolved?
- Evidence provided for each point?

**AI Playbook** (for AI systems):
- Assessment exists for AI/ML systems?
- Risk level determined (High/Medium/Low)?
- All 10 principles assessed?
- All 6 ethical themes assessed?
- Mandatory assessments completed (DPIA, EqIA, Human Rights)?
- Bias testing completed?
- Human oversight model defined?

**ATRS** (for AI systems):
- ATRS record exists for algorithmic tools?
- Tier 1 (public summary) completed?
- Tier 2 (technical details) completed?
- All mandatory fields filled?
- Ready for GOV.UK publication?

**Compliance Alignment**:
- Requirements aligned with TCoP?
- Design complies with TCoP (Cloud First, Open Standards, Secure)?
- AI requirements comply with AI Playbook?
- ATRS record reflects requirements and design?

#### J. MOD Secure by Design Compliance (if mod-secure-by-design.md exists)

**7 SbD Principles Assessment**:
- Principle 1 (Understand and Define Context): Context documented, data classification determined?
- Principle 2 (Apply Security from the Start): Security embedded from inception, not bolt-on?
- Principle 3 (Apply Defence in Depth): Layered security controls implemented?
- Principle 4 (Follow Secure Design Patterns): NCSC/NIST guidance applied?
- Principle 5 (Continuously Manage Risk): Risk register maintained, continuous testing?
- Principle 6 (Secure the Supply Chain): SBOM maintained, supplier attestations obtained?
- Principle 7 (Enable Through-Life Assurance): Continuous monitoring, incident response capability?

**NIST Cybersecurity Framework Coverage**:
- **Identify**: Asset inventory, business environment, governance, risk assessment?
- **Protect**: Access control, data security, protective technology, training?
- **Detect**: Continuous monitoring, anomaly detection, security testing?
- **Respond**: Incident response plan, communications to MOD CERT, analysis?
- **Recover**: Recovery planning, backup/DR/BC, post-incident improvements?

**Continuous Assurance Process** (replaced RMADS August 2023):
- CAAT (Cyber Activity and Assurance Tracker) registration completed?
- CAAT self-assessment question sets completed based on 7 SbD Principles?
- CAAT continuously updated (not one-time submission)?
- Delivery Team Security Lead (DTSL) appointed?
- Security Assurance Coordinator (SAC) appointed (if applicable)?
- Project Security Officer (PSyO) appointed for SECRET+ systems?

**Three Lines of Defence Implementation**:
- **First Line**: Delivery team owns security, DTSL leads day-to-day management?
- **Second Line**: Technical Coherence assurance, security policies, independent reviews?
- **Third Line**: Independent audit, penetration testing, external audit (NAO, GIAA)?

**Supplier Attestation** (if vendor-delivered system):
- Suppliers attest systems are secure (ISN 2023/10)?
- Supplier-owned continuous assurance (not MOD accreditation)?
- Supplier security requirements in contracts?

**Classification-Specific Requirements**:
- OFFICIAL: Cyber Essentials baseline, basic access controls?
- OFFICIAL-SENSITIVE: Cyber Essentials Plus, MFA, enhanced logging, DPIA?
- SECRET: SC personnel, CESG crypto, air-gap/assured network, enhanced physical security?
- TOP SECRET: DV personnel, compartmented security, strict access control?

**Critical Issues (Deployment Blockers)**:
- SECRET+ data without appropriate controls?
- No encryption at rest or in transit?
- Personnel lacking security clearances?
- No threat model or risk assessment?
- Critical vulnerabilities unpatched?

**Missing MOD SbD Assessment**:
- Project for MOD but no SbD assessment (MANDATORY to run `/arckit.mod-secure`)

#### K. Consistency Across Artifacts

**Terminology Drift**:
- Same concept named differently across files
- Inconsistent capitalization/formatting of terms
- Conflicting definitions

**Data Model Consistency**:
- Data entities referenced in requirements match design
- Database schemas in DLD match data requirements (DR-xxx)
- Data sharing agreements align across artifacts

**Technology Stack Consistency**:
- Stack choices in HLD match principles
- Technology in DLD matches HLD
- Third-party dependencies consistently listed

**Timeline/Budget Consistency** (if vendor procurement):
- SOW timeline realistic for requirements scope?
- Budget adequate for requirements complexity?
- Vendor proposal timeline/budget match SOW?

#### G. Security & Compliance Analysis

**Security Coverage**:
- Security requirements (NFR-S-xxx) exist?
- Threat model documented?
- Security architecture in HLD?
- Security implementation in DLD?
- Security testing plan?

**Compliance Coverage**:
- Compliance requirements (NFR-C-xxx) exist?
- Regulatory requirements identified (GDPR, PCI-DSS, HIPAA, etc.)?
- Compliance validated in design?
- Audit requirements addressed?

**Data Protection**:
- Personal data handling defined?
- GDPR/UK GDPR compliance addressed?
- Data retention policy defined?
- Data breach procedures defined?

### 5. Severity Assignment

Use this heuristic to prioritise findings:

**CRITICAL**:
- Violates architecture principles (MUST)
- Missing core artifact (no requirements.md)
- MUST requirement with zero design coverage
- Stakeholder: Orphan requirements (not linked to any stakeholder goal)
- Risk: High/Very High risks with no mitigation in requirements or design
- Risk: Risk owners not from stakeholder RACI matrix (governance gap)
- SOBC: Benefits not traced to stakeholder goals or requirements
- SOBC: Costs inadequate for requirements scope (budget shortfall)
- Data Model: DR-xxx requirements with no entity mapping
- Data Model: PII not identified (GDPR compliance failure)
- Data Model: Data owners not from stakeholder RACI matrix
- UK Gov: TCoP non-compliance for mandatory points
- UK Gov: AI Playbook blocking issues for high-risk AI
- UK Gov: Missing mandatory ATRS for central government AI
- MOD: CAAT not registered (MANDATORY for all programmes)
- MOD: No DTSL appointed (required from Discovery phase)
- MOD: SECRET+ data without classification-specific controls
- MOD: Supplier attestation missing for vendor-delivered system
- Security requirement with no design coverage
- Compliance requirement with no validation

**HIGH**:
- Duplicate or conflicting requirements
- Ambiguous security/performance attribute
- Untestable acceptance criterion
- Missing non-functional requirements category (no security, no performance)
- Stakeholder: Requirement conflicts not documented or resolved
- Risk: Medium risks with no mitigation plan
- Risk: Risk responses not appropriate (4Ts misapplied)
- SOBC: Benefits not measurable or verifiable
- SOBC: Option analysis missing Do Nothing baseline
- Data Model: Database schema in DLD doesn't match data model entities
- Data Model: CRUD matrix doesn't align with HLD component design
- Vendor design doesn't address SOW requirements
- UK Gov: TCoP partial compliance with gaps
- UK Gov: AI Playbook non-compliance for medium-risk AI
- MOD: SbD Principles partially compliant with significant gaps
- MOD: NIST CSF functions not fully covered

**MEDIUM**:
- Terminology drift
- Missing optional non-functional requirement coverage
- Underspecified edge case
- Minor traceability gaps
- Documentation incomplete
- Stakeholder: Missing stakeholder analysis (recommended to add)
- Risk: Missing risk register (recommended to add)
- SOBC: Missing business case (recommended for major investments)
- Data Model: Missing data model (recommended if DR-xxx exist)
- Data Model: Data quality metrics not defined
- UK Gov: TCoP minor gaps
- MOD: CAAT self-assessment incomplete (some question sets missing)
- MOD: Third Line of Defence not fully implemented

**LOW**:
- Style/wording improvements
- Minor redundancy not affecting execution
- Documentation formatting
- Non-critical missing optional fields

### 6. Produce Comprehensive Analysis Report

Generate a comprehensive Markdown report and save it to `projects/{project-dir}/analysis-report.md` with the following structure:

```markdown
# Architecture Governance Analysis Report

**Project**: {project-name}
**Date**: {current-date}
**Analyzed By**: ArcKit v{version}

---

## Executive Summary

**Overall Status**: ✅ Ready / ⚠️ Issues Found / ❌ Critical Issues

**Key Metrics**:
- Total Requirements: {count}
- Requirements Coverage: {percentage}%
- Critical Issues: {count}
- High Priority Issues: {count}
- Medium Priority Issues: {count}
- Low Priority Issues: {count}

**Recommendation**: [PROCEED / RESOLVE CRITICAL ISSUES FIRST / MAJOR REWORK NEEDED]

---

## Findings Summary

| ID | Category | Severity | Location(s) | Summary | Recommendation |
|----|----------|----------|-------------|---------|----------------|
| R1 | Requirements Quality | HIGH | requirements.md:L45-52 | Duplicate security requirements | Merge NFR-S-001 and NFR-S-005 |
| P1 | Principles Alignment | CRITICAL | requirements.md:L120 | Violates Cloud-First principle | Change to cloud-native architecture |
| T1 | Traceability | HIGH | No HLD coverage | NFR-P-002 (10K TPS) not addressed | Add performance architecture section to HLD |
| UK1 | UK Gov Compliance | CRITICAL | Missing DPIA | AI system requires DPIA before deployment | Complete DPIA for AI Playbook compliance |

---

## Requirements Analysis

### Requirements Coverage Matrix

| Requirement ID | Type | Priority | Design Coverage | Tests Coverage | Status |
|----------------|------|----------|-----------------|----------------|--------|
| BR-001 | Business | MUST | ✅ HLD | ❌ Missing | ⚠️ Partial |
| FR-001 | Functional | MUST | ✅ HLD, DLD | ✅ Tests | ✅ Complete |
| NFR-S-001 | Security | MUST | ❌ Missing | ❌ Missing | ❌ Not Covered |

**Statistics**:
- Total Requirements: {count}
- Fully Covered: {count} ({percentage}%)
- Partially Covered: {count} ({percentage}%)
- Not Covered: {count} ({percentage}%)

### Uncovered Requirements (CRITICAL)

| Requirement ID | Priority | Description | Why Critical |
|----------------|----------|-------------|--------------|
| NFR-S-003 | MUST | Encrypt data at rest | Security requirement |
| NFR-P-002 | MUST | Support 10K TPS | Performance critical |

---

## Architecture Principles Compliance

| Principle | Status | Evidence | Issues |
|-----------|--------|----------|--------|
| Cloud-First | ✅ COMPLIANT | AWS architecture in HLD | None |
| API-First | ⚠️ PARTIAL | REST APIs defined, missing OpenAPI specs | Document API contracts |
| Security-by-Design | ❌ NON-COMPLIANT | No threat model, missing security architecture | Add security sections |

**Critical Principle Violations**: {count}

---

## Stakeholder Traceability Analysis

**Stakeholder Analysis Exists**: ✅ Yes / ❌ No (RECOMMENDED)

**Stakeholder-Requirements Coverage**:
- Requirements traced to stakeholder goals: {percentage}%
- Orphan requirements (no stakeholder justification): {count}
- Requirement conflicts documented and resolved: ✅ Yes / ⚠️ Partial / ❌ No

**RACI Governance Alignment**:
| Artifact | Role | Aligned with RACI? | Issues |
|----------|------|-------------------|--------|
| Risk Register | Risk Owners | ✅ Yes / ❌ No | Missing 3 risk owners from RACI |
| Data Model | Data Owners | ✅ Yes / ❌ No | None |
| SOBC | Benefits Owners | ✅ Yes / ❌ No | 2 benefits lack owner assignment |

**Critical Issues**:
- Orphan requirements: {count} requirements not linked to stakeholder goals
- Unresolved conflicts: {count} requirement conflicts without resolution

---

## Risk Management Analysis

**Risk Register Exists**: ✅ Yes / ❌ No (RECOMMENDED)

**Risk Coverage**:
| Risk ID | Category | Inherent | Residual | Response | Mitigation in Req? | Mitigation in Design? |
|---------|----------|----------|----------|----------|-------------------|---------------------|
| R-001 | Strategic | Very High | High | Treat | ✅ BR-003 | ✅ HLD Section 4 |
| R-005 | Technology | High | Medium | Treat | ❌ Missing | ❌ Missing |

**High/Very High Risks Requiring Attention**:
| Risk ID | Description | Current Status | Required Action |
|---------|-------------|----------------|-----------------|
| R-005 | Cloud provider lock-in | No mitigation | Add multi-cloud requirements |
| R-012 | Data breach | Partial mitigation | Complete security architecture in HLD |

**Risk-SOBC Alignment** (if SOBC exists):
- Strategic risks reflected in Strategic Case: ✅ Yes / ❌ No
- Financial risks in Economic Case cost contingency: ✅ Yes / ❌ No
- Risks included in Management Case Part E: ✅ Yes / ❌ No

**Risk Governance**:
- Risk owners from stakeholder RACI: ✅ Yes / ⚠️ Partial / ❌ No
- Risk appetite compliance: {count} risks within tolerance

---

## Business Case Analysis

**SOBC Exists**: ✅ Yes / ❌ No (RECOMMENDED for major investments)

**Benefits Traceability**:
| Benefit ID | Description | Stakeholder Goal | Requirements | Measurable? | Status |
|------------|-------------|------------------|--------------|-------------|--------|
| B-001 | Reduce costs 40% | CFO Goal G-1 | BR-002, NFR-P-003 | ✅ Yes | ✅ Complete |
| B-003 | Improve UX | CTO Goal G-5 | FR-008, NFR-A-001 | ❌ No | ❌ Not measurable |

**Benefits Coverage**:
- Total benefits: {count}
- Benefits traced to stakeholder goals: {percentage}%
- Benefits supported by requirements: {percentage}%
- Benefits measurable and verifiable: {percentage}%

**Option Analysis Quality**:
- Do Nothing baseline included: ✅ Yes / ❌ No
- Options analyzed: {count} options
- Recommended option: {option name}
- Justification: ✅ Strong / ⚠️ Weak / ❌ Missing

**SOBC-Requirements Alignment**:
- Strategic Case drivers in requirements: ✅ Yes / ⚠️ Partial / ❌ No
- Economic Case benefits achievable with requirements: ✅ Yes / ⚠️ Questionable / ❌ No
- Financial Case budget adequate: ✅ Yes / ⚠️ Tight / ❌ Insufficient

**Critical Issues**:
- Non-measurable benefits: {count}
- Benefits without requirement support: {count}
- Budget shortfall: £{amount} (requirements scope exceeds budget)

---

## Data Model Analysis

**Data Model Exists**: ✅ Yes / ❌ No (RECOMMENDED if DR-xxx exist)

**DR-xxx Requirements Coverage**:
| Requirement ID | Description | Entities | Attributes | Status |
|----------------|-------------|----------|------------|--------|
| DR-001 | Store customer data | E-001: Customer | customer_id, email, name | ✅ Complete |
| DR-005 | GDPR erasure | E-001: Customer | [All PII] | ✅ Complete |
| DR-008 | Payment history | ❌ No entity | N/A | ❌ Missing |

**Data Requirements Coverage**:
- Total DR-xxx requirements: {count}
- DR-xxx mapped to entities: {percentage}%
- Entities traced to DR-xxx: {percentage}%

**Data Model Quality**:
- ERD exists and renderable: ✅ Yes / ❌ No
- Entities with complete specs: {count}/{total}
- PII identified: ✅ Yes / ⚠️ Partial / ❌ No
- GDPR compliance documented: ✅ Yes / ⚠️ Partial / ❌ No

**Data Governance**:
| Entity | Data Owner (from RACI) | Data Steward | Technical Custodian | Status |
|--------|------------------------|--------------|---------------------|--------|
| E-001: Customer | CFO (from stakeholder RACI) | Data Governance Lead | Database Team | ✅ Complete |
| E-003: Payment | ❌ Not assigned | ❌ Not assigned | Database Team | ❌ Missing owners |

**Data Model-Design Alignment**:
- Database schemas in DLD match entities: ✅ Yes / ⚠️ Partial / ❌ No / N/A
- CRUD matrix aligns with HLD components: ✅ Yes / ⚠️ Partial / ❌ No / N/A
- Data integration flows match upstream/downstream: ✅ Yes / ⚠️ Partial / ❌ No / N/A

**Critical Issues**:
- DR-xxx requirements with no entity mapping: {count}
- PII not identified (GDPR risk): {count} entities
- Data owners not from RACI matrix: {count} entities

---

## UK Government Compliance Analysis

### Technology Code of Practice (TCoP)

**Overall Score**: {score}/130 ({percentage}%)
**Status**: ✅ Compliant / ⚠️ Partial / ❌ Non-Compliant

| Point | Requirement | Status | Score | Issues |
|-------|-------------|--------|-------|--------|
| 1 | Define User Needs | ✅ | 9/10 | Minor: User research from 2023 (update) |
| 5 | Use Cloud First | ✅ | 10/10 | AWS cloud-native |
| 6 | Make Things Secure | ❌ | 3/10 | Missing: Cyber Essentials, threat model |

**Critical TCoP Issues**: {count}

### AI Playbook (if AI system)

**Risk Level**: HIGH-RISK / MEDIUM-RISK / LOW-RISK
**Overall Score**: {score}/160 ({percentage}%)
**Status**: ✅ Compliant / ⚠️ Partial / ❌ Non-Compliant

**Blocking Issues**:
- [ ] DPIA not completed (MANDATORY for high-risk)
- [ ] No human-in-the-loop (REQUIRED for high-risk)
- [ ] ATRS not published (MANDATORY for central government)

### ATRS (if AI system)

**Completeness**: {percentage}%
**Status**: ✅ Ready for Publication / ⚠️ Incomplete / ❌ Missing

**Missing Mandatory Fields**:
- [ ] Senior Responsible Owner
- [ ] Bias testing results
- [ ] Fallback procedures

---

## MOD Secure by Design Analysis

**MOD SbD Assessment Exists**: ✅ Yes / ❌ No (MANDATORY for MOD projects)

**Overall SbD Maturity**: Level {0-5} (Target: Level 3+ for operational systems)

### 7 SbD Principles Compliance

| Principle | Status | Score | Issues |
|-----------|--------|-------|--------|
| 1. Understand and Define Context | ✅ | 9/10 | Minor: Data classification pending final review |
| 2. Apply Security from the Start | ⚠️ | 6/10 | Security architecture not in initial specs |
| 3. Apply Defence in Depth | ❌ | 3/10 | Missing: Network segmentation, IDS/IPS |
| 4. Follow Secure Design Patterns | ✅ | 8/10 | NCSC guidance applied, minor OWASP gaps |
| 5. Continuously Manage Risk | ✅ | 9/10 | Risk register active, continuous monitoring planned |
| 6. Secure the Supply Chain | ⚠️ | 5/10 | Missing: SBOM, supplier attestations |
| 7. Enable Through-Life Assurance | ⚠️ | 6/10 | Monitoring planned, incident response incomplete |

**Overall Score**: {score}/70 ({percentage}%)

### NIST Cybersecurity Framework Coverage

| Function | Status | Coverage | Critical Gaps |
|----------|--------|----------|---------------|
| Identify | ✅ | 90% | Asset inventory incomplete for contractor systems |
| Protect | ⚠️ | 65% | MFA not implemented, PAM missing |
| Detect | ❌ | 40% | No SIEM integration, limited monitoring |
| Respond | ⚠️ | 70% | Incident response plan exists, not tested |
| Recover | ✅ | 85% | Backup/DR tested, BC plan approved |

**Overall CSF Score**: {percentage}%

### Continuous Assurance Process

**CAAT (Cyber Activity and Assurance Tracker)**:
- CAAT registered: ✅ Yes / ❌ No (MANDATORY)
- Registration date: {date}
- Self-assessment question sets completed: {count}/{total}
- Based on 7 SbD Principles: ✅ Yes / ⚠️ Partial / ❌ No
- Continuously updated: ✅ Yes / ⚠️ Sporadic / ❌ One-time only
- Last update: {date}

**Key Roles**:
- Delivery Team Security Lead (DTSL) appointed: ✅ Yes / ❌ No (REQUIRED)
- DTSL name: {name}
- Security Assurance Coordinator (SAC) appointed: ✅ Yes / ❌ No / N/A
- Project Security Officer (PSyO) for SECRET+: ✅ Yes / ❌ No / N/A

### Three Lines of Defence

| Line | Responsibility | Implementation | Status |
|------|----------------|----------------|--------|
| First Line | Delivery team owns security (DTSL) | DTSL appointed, day-to-day management | ✅ Effective |
| Second Line | Technical Coherence assurance | Quarterly reviews scheduled | ⚠️ Partial |
| Third Line | Independent audit (NAO, GIAA) | Pen test planned Q2 | ⚠️ Planned |

**Overall Governance**: ✅ Strong / ⚠️ Adequate / ❌ Weak

### Supplier Attestation (if vendor-delivered)

**Supplier Attestation Required**: ✅ Yes / ❌ No / N/A

**Attestation Status**:
- Suppliers attest systems are secure (ISN 2023/10): ✅ Yes / ❌ No
- Supplier-owned continuous assurance: ✅ Yes / ❌ No
- Supplier security requirements in contracts: ✅ Yes / ⚠️ Partial / ❌ No
- Contract includes CAAT self-assessment obligations: ✅ Yes / ❌ No

### Classification-Specific Requirements

**Data Classification**: OFFICIAL / OFFICIAL-SENSITIVE / SECRET / TOP SECRET

**Classification Requirements Met**:
| Requirement | Status | Evidence |
|-------------|--------|----------|
| Personnel security clearances | ✅ / ❌ | All SC cleared for OFFICIAL-SENSITIVE |
| Cryptography (CESG-approved) | ✅ / ❌ | AES-256, TLS 1.3 |
| Network security (air-gap/assured) | ✅ / ⚠️ / ❌ | Assured connectivity approved |
| Physical security | ✅ / ❌ | Enhanced access controls in place |
| Cyber Essentials / Cyber Essentials Plus | ✅ / ❌ | Cyber Essentials Plus certified |

### Critical Issues (Deployment Blockers)

**Blocking Issues**:
- [ ] CAAT not registered (MANDATORY for all programmes)
- [ ] No DTSL appointed (required from Discovery phase)
- [ ] SECRET+ data without SC cleared personnel
- [ ] No encryption at rest or in transit
- [ ] No threat model or risk assessment
- [ ] Critical vulnerabilities unpatched
- [ ] Supplier attestation missing for vendor-delivered system

**Deployment Readiness**: ✅ Ready / ⚠️ Issues to resolve / ❌ BLOCKED

---

## Traceability Analysis

**Traceability Matrix**: ✅ Exists / ❌ Missing

**Forward Traceability** (Requirements → Design → Tests):
- Requirements → HLD: {percentage}%
- HLD → DLD: {percentage}%
- DLD → Tests: {percentage}%

**Backward Traceability** (Tests → Requirements):
- Orphan components (not linked to requirements): {count}

**Gap Summary**:
- {count} requirements with no design coverage
- {count} design elements with no requirement justification
- {count} components with no test coverage

---

## Vendor Procurement Analysis

### SOW Quality
**Status**: ✅ Complete / ⚠️ Issues / ❌ Insufficient

**Issues**:
- [ ] SOW missing NFR-P-xxx performance requirements
- [ ] Acceptance criteria ambiguous for deliverable 3
- [ ] Timeline unrealistic for scope (6 months vs 50 requirements)

### Vendor Evaluation
**Evaluation Criteria Defined**: ✅ Yes / ❌ No

**Alignment Check**:
- All MUST requirements in scoring? ✅ Yes / ❌ No
- Scoring methodology fair? ✅ Yes / ⚠️ Issues / ❌ No
- Technical evaluation covers all areas? ✅ Yes / ⚠️ Gaps / ❌ No

### Vendor Design Review
**HLD Review Completed**: ✅ Yes / ❌ No
**DLD Review Completed**: ✅ Yes / ❌ No

**Coverage Analysis**:
| SOW Requirement | HLD Coverage | DLD Coverage | Status |
|-----------------|--------------|--------------|--------|
| Cloud infrastructure | ✅ | ✅ | Complete |
| Security architecture | ❌ | ❌ | Missing |
| Performance (10K TPS) | ⚠️ | ❌ | Insufficient |

---

## Security & Compliance Summary

### Security Posture
- Security requirements defined: ✅ Yes / ❌ No
- Threat model documented: ✅ Yes / ❌ No
- Security architecture in HLD: ✅ Yes / ⚠️ Partial / ❌ No
- Security implementation in DLD: ✅ Yes / ⚠️ Partial / ❌ No
- Security testing plan: ✅ Yes / ❌ No

**Security Coverage**: {percentage}%

### Compliance Posture
- Regulatory requirements identified: ✅ Yes / ❌ No
- GDPR/UK GDPR compliance: ✅ Yes / ⚠️ Partial / ❌ No
- Industry compliance (PCI-DSS, HIPAA, etc.): ✅ Yes / ⚠️ Partial / ❌ No / N/A
- Audit readiness: ✅ Yes / ⚠️ Partial / ❌ No

**Compliance Coverage**: {percentage}%

---

## Recommendations

### Critical Actions (MUST resolve before implementation/procurement)

1. **[P1] Add Cloud-First architecture**: Current design violates Cloud-First principle. Redesign with AWS/Azure/GCP.
2. **[R1] Cover security requirements**: NFR-S-003, NFR-S-007, NFR-S-012 have no design coverage. Add security architecture to HLD.
3. **[UK1] Complete DPIA**: HIGH-RISK AI system requires completed DPIA before deployment (AI Playbook MANDATORY).

### High Priority Actions (SHOULD resolve before implementation/procurement)

1. **[T1] Document API contracts**: Add OpenAPI specifications for all REST APIs.
2. **[T2] Add performance architecture**: NFR-P-002 (10K TPS) not addressed in design. Add performance section to HLD.
3. **[V1] Update SOW acceptance criteria**: Deliverable 3 acceptance criteria too vague. Add measurable criteria.

### Medium Priority Actions (Improve quality)

1. **[Q1] Consolidate duplicate requirements**: Merge NFR-S-001 and NFR-S-005 (identical).
2. **[Q2] Fix terminology drift**: "User" vs "Customer" used inconsistently. Standardize.
3. **[D1] Complete traceability matrix**: Add backward traceability from tests to requirements.

### Low Priority Actions (Optional improvements)

1. **[S1] Improve requirement wording**: Replace "fast" with measurable criteria (e.g., "< 200ms p95").
2. **[S2] Add edge case documentation**: Document edge cases for error handling.

---

## Metrics Dashboard

### Requirement Quality
- Total Requirements: {count}
- Ambiguous Requirements: {count}
- Duplicate Requirements: {count}
- Untestable Requirements: {count}
- **Quality Score**: {percentage}%

### Architecture Alignment
- Principles Compliant: {count}/{total}
- Principles Violations: {count}
- **Alignment Score**: {percentage}%

### Traceability
- Requirements Covered: {count}/{total}
- Orphan Components: {count}
- **Traceability Score**: {percentage}%

### Stakeholder Traceability (if applicable)
- Requirements traced to stakeholder goals: {percentage}%
- Orphan requirements: {count}
- Conflicts resolved: {percentage}%
- RACI governance alignment: {percentage}%
- **Stakeholder Score**: {percentage}%

### Risk Management (if applicable)
- High/Very High risks mitigated: {percentage}%
- Risk owners from RACI: {percentage}%
- Risks reflected in design: {percentage}%
- Risk-SOBC alignment: {percentage}%
- **Risk Management Score**: {percentage}%

### Business Case (if applicable)
- Benefits traced to stakeholder goals: {percentage}%
- Benefits supported by requirements: {percentage}%
- Benefits measurable: {percentage}%
- Budget adequacy: ✅ Adequate / ⚠️ Tight / ❌ Insufficient
- **Business Case Score**: {percentage}%

### Data Model (if applicable)
- DR-xxx requirements mapped to entities: {percentage}%
- Entities traced to DR-xxx: {percentage}%
- PII identified: {percentage}%
- Data governance complete: {percentage}%
- Data model-design alignment: {percentage}%
- **Data Model Score**: {percentage}%

### UK Government Compliance (if applicable)
- TCoP Score: {score}/130 ({percentage}%)
- AI Playbook Score: {score}/160 ({percentage}%)
- ATRS Completeness: {percentage}%
- **UK Gov Compliance Score**: {percentage}%

### MOD Compliance (if applicable)
- 7 SbD Principles Score: {score}/70 ({percentage}%)
- NIST CSF Coverage: {percentage}%
- CAAT registered and updated: ✅ Yes / ❌ No
- Three Lines of Defence: {percentage}%
- **MOD SbD Score**: {percentage}%

### Overall Governance Health
**Score**: {percentage}%
**Grade**: A / B / C / D / F

**Grade Thresholds**:
- A (90-100%): Excellent governance, ready to proceed
- B (80-89%): Good governance, minor issues
- C (70-79%): Adequate governance, address high-priority issues
- D (60-69%): Poor governance, major rework needed
- F (<60%): Insufficient governance, do not proceed

---

## Next Steps

### Immediate Actions

1. **If CRITICAL issues exist**: ❌ **DO NOT PROCEED** with implementation/procurement until resolved.
   - Run: `/arckit.requirements` to fix requirements issues
   - Run: `/arckit.hld-review` to address design gaps
   - Run: `/arckit.ai-playbook` (if AI system) to complete mandatory assessments

2. **If only HIGH/MEDIUM issues**: ⚠️ **MAY PROCEED** with caution, but address issues in parallel.
   - Document exceptions for HIGH issues
   - Create remediation plan for MEDIUM issues

3. **If only LOW issues**: ✅ **READY TO PROCEED**
   - Address LOW issues during implementation as improvements

### Suggested Commands

Based on findings, consider running:

**Governance Foundation**:
- `/arckit.principles` - Create/update architecture principles
- `/arckit.stakeholders` - Analyze stakeholder drivers, goals, conflicts (RECOMMENDED)
- `/arckit.risk` - Create risk register using Orange Book framework (RECOMMENDED)
- `/arckit.sobc` - Create Strategic Outline Business Case using Green Book 5-case model (RECOMMENDED for major investments)

**Requirements & Design**:
- `/arckit.requirements` - Refine requirements to address ambiguity/gaps
- `/arckit.data-model` - Create data model with ERD, GDPR compliance (RECOMMENDED if DR-xxx exist)
- `/arckit.hld-review` - Re-review HLD after addressing issues
- `/arckit.dld-review` - Re-review DLD after addressing issues

**UK Government Compliance**:
- `/arckit.tcop` - Complete TCoP assessment for UK Gov projects
- `/arckit.ai-playbook` - Complete AI Playbook assessment for AI systems
- `/arckit.atrs` - Generate ATRS record for algorithmic tools
- `/arckit.secure` - UK Government Secure by Design review

**MOD Compliance**:
- `/arckit.mod-secure` - MOD Secure by Design assessment with CAAT (MANDATORY for MOD projects)

**Vendor Procurement**:
- `/arckit.sow` - Generate statement of work for RFP
- `/arckit.evaluate` - Update vendor evaluation criteria

**Analysis & Traceability**:
- `/arckit.traceability` - Generate/update traceability matrix
- `/arckit.analyze` - Re-run this analysis after fixes

### Re-run Analysis

After making changes, re-run analysis:
```bash
/arckit.analyze
```

Expected improvement in scores after addressing findings.

---

## Detailed Findings

(Expand top findings with examples and specific recommendations)

### Finding R1: Duplicate Security Requirements (HIGH)

**Location**: `requirements.md:L45-52` and `requirements.md:L120-125`

**Details**:
```
NFR-S-001: System MUST encrypt data at rest using AES-256
NFR-S-005: All stored data SHALL be encrypted with AES-256 encryption
```

**Issue**: These are duplicate requirements with inconsistent language (MUST vs SHALL).

**Impact**: Confuses implementation team, wastes evaluation points in vendor scoring.

**Recommendation**:
1. Keep NFR-S-001 (clearer wording)
2. Delete NFR-S-005
3. Update traceability matrix

**Estimated Effort**: 10 minutes

---

### Finding P1: Violates Cloud-First Principle (CRITICAL)

**Location**: `requirements.md:L120`, Architecture Principles violation

**Details**:
```
FR-025: System SHALL deploy to on-premise servers in corporate datacenter
```

**Issue**: Violates "Cloud-First" architecture principle defined in `.arckit/memory/architecture-principles.md`. Principle states "MUST use public cloud (AWS/Azure/GCP) unless explicitly justified exception."

**Impact**: Architecture doesn't align with organization standards. Blocks procurement approval.

**Recommendation**:
1. Change FR-025 to require AWS/Azure/GCP deployment
2. OR: Document formal exception with justification (security, regulatory, etc.)
3. Get exception approved by Architecture Review Board

**Estimated Effort**: 2 hours (requirement change + design update)

---

(Continue with detailed findings for top 10-20 issues)

---

## Appendix: Analysis Methodology

**Artifacts Analyzed**:
- {list of files}

**Detection Rules Applied**:
- {count} duplication checks
- {count} ambiguity patterns
- {count} principle validations
- {count} traceability checks

**Analysis Runtime**: {duration}

**Analysis Version**: ArcKit v{version}

---

**END OF ANALYSIS REPORT**
```

### 7. Write Analysis Report to File

Save the complete analysis report generated in Step 6 to:

**`projects/{project-dir}/analysis-report.md`**

The saved report must include:
- ✅ All sections from Executive Summary to Detailed Findings
- ✅ Complete metrics dashboard
- ✅ Actionable recommendations with priorities
- ✅ Next steps and suggested commands
- ✅ Traceability to source artifacts

After writing the file, provide a summary message to the user:

```
✅ Governance Analysis Complete

**Project**: {project-name}
**Report Location**: projects/{project-dir}/analysis-report.md

**Overall Status**: ✅ Ready / ⚠️ Issues Found / ❌ Critical Issues
**Governance Health Score**: {score}/100 ({grade})

**Issue Summary**:
- Critical Issues: {count}
- High Priority Issues: {count}
- Medium Priority Issues: {count}
- Low Priority Issues: {count}

**Key Metrics**:
- Requirements Coverage: {percentage}%
- Principles Compliance: {percentage}%
- Traceability Score: {percentage}%
- Stakeholder Alignment: {percentage}%
- Risk Management: {percentage}%
- UK Gov Compliance: {percentage}% (if applicable)
- MOD SbD Compliance: {percentage}% (if applicable)

**Top 3 Critical Issues**:
1. {issue} - {location}
2. {issue} - {location}
3. {issue} - {location}

**Recommendation**: {PROCEED / RESOLVE CRITICAL ISSUES FIRST / MAJOR REWORK NEEDED}

**Next Steps**:
- {action}
- {action}
- {action}

📄 Full analysis report saved to: projects/{project-dir}/analysis-report.md
```

### 8. Provide Remediation Guidance

After outputting the report, ask:

> **Would you like me to suggest concrete remediation steps for the top {N} critical/high priority issues?**
>
> I can provide:
> 1. Specific edits to fix requirements
> 2. Design review guidance
> 3. Command sequences to address gaps
> 4. Templates for missing artifacts
>
> (I will NOT make changes automatically - you must approve each action)

## Operating Principles

### Context Efficiency

- **Minimal high-signal tokens**: Focus on actionable findings, not exhaustive documentation
- **Progressive disclosure**: Load artifacts incrementally; don't dump all content into analysis
- **Token-efficient output**: Limit findings table to 50 rows; summarize overflow
- **Deterministic results**: Rerunning without changes should produce consistent IDs and counts

### Analysis Guidelines

- **DO NOT modify existing artifacts** (non-destructive analysis)
- **DO write analysis report** to `projects/{project-dir}/analysis-report.md`
- **NEVER hallucinate missing sections** (if absent, report them accurately)
- **Prioritize principle violations** (these are always CRITICAL)
- **Prioritize UK Gov compliance issues** (mandatory for public sector)
- **Use examples over exhaustive rules** (cite specific instances, not generic patterns)
- **Report zero issues gracefully** (emit success report with metrics)
- **Be specific**: Cite line numbers, requirement IDs, exact quotes
- **Be actionable**: Every finding should have a clear recommendation
- **Be fair**: Flag real issues, not nitpicks

### Enterprise Architecture Focus

Unlike Spec Kit's focus on code implementation, ArcKit analyze focuses on:
- **Governance compliance**: Principles, standards, policies
- **Requirements quality**: Completeness, testability, traceability
- **Procurement readiness**: SOW quality, vendor evaluation fairness
- **Design alignment**: Requirements → design traceability
- **UK Government compliance**: TCoP, AI Playbook, ATRS (if applicable)
- **Security & compliance**: Not just mentioned, but architected
- **Decision quality**: Objective, defensible, auditable

## Example Usage

User: `/arckit.analyze`

You should:
1. Identify project (if multiple, ask which)
2. Load artifacts progressively:
   - Architecture principles
   - Stakeholder drivers (if exists - RECOMMENDED)
   - Risk register (if exists - RECOMMENDED)
   - SOBC business case (if exists - RECOMMENDED)
   - Requirements (BR, FR, NFR, INT, DR)
   - Data model (if exists - RECOMMENDED if DR-xxx)
   - Designs (HLD, DLD)
   - UK Gov assessments (TCoP, AI Playbook, ATRS)
   - MOD assessment (SbD with CAAT)
   - Traceability matrix
3. Run detection passes:
   - Requirements quality (duplication, ambiguity, underspecification)
   - Stakeholder traceability (requirements to goals, conflict resolution, RACI alignment)
   - Risk coverage (high/very high risks mitigated, risk-requirements alignment, risk-SOBC alignment)
   - Business case alignment (benefits to stakeholders, benefits to requirements, costs adequacy)
   - Data model consistency (DR-xxx to entities, data governance, design alignment)
   - Principles alignment (violations, coverage)
   - Traceability (coverage gaps, orphans)
   - UK Gov compliance (TCoP, AI Playbook, ATRS)
   - MOD compliance (7 SbD Principles, NIST CSF, CAAT, Three Lines of Defence)
   - Consistency (terminology, data model, tech stack)
   - Security & compliance coverage
4. Assign severity (CRITICAL, HIGH, MEDIUM, LOW)
5. Generate comprehensive report with:
   - Executive summary
   - Findings table
   - Coverage matrices
   - Stakeholder traceability analysis
   - Risk management analysis
   - Business case analysis
   - Data model analysis
   - UK Gov compliance dashboard
   - MOD compliance dashboard
   - Metrics dashboard
   - Next steps and recommendations
6. Ask if user wants remediation guidance

Example output: "Architecture Governance Analysis Report" with 18 findings (3 CRITICAL, 6 HIGH, 7 MEDIUM, 2 LOW), 87% requirements coverage, 92% stakeholder traceability, 85% risk mitigation, TCoP score 98/130 (75%), MOD SbD score 58/70 (83%), recommendation: "Resolve 3 CRITICAL issues (1 stakeholder orphan, 2 high risks unmitgated) before procurement"

## Important Notes

- This is **non-destructive analysis** - existing artifacts are not modified
- Analysis report is saved to `projects/{project-dir}/analysis-report.md` for audit trail
- Run `/arckit.analyze` after major changes to requirements, designs, or assessments
- Ideal times to run:
  - Before issuing SOW/RFP to vendors
  - After receiving vendor proposals
  - Before design review meetings
  - Before implementation kickoff
  - Before deployment to production
- Analysis identifies issues; you decide how to resolve them
- Re-run after fixing issues to verify improvements
- Target: 90%+ governance health score before proceeding

## Related Commands

After analysis, you may need:

**Governance Foundation**:
- `/arckit.principles` - Create/update architecture principles
- `/arckit.stakeholders` - Analyze stakeholder drivers and conflicts
- `/arckit.risk` - Create Orange Book risk register
- `/arckit.sobc` - Create Green Book business case

**Requirements & Data**:
- `/arckit.requirements` - Fix requirements issues
- `/arckit.data-model` - Create data model with ERD and GDPR compliance

**Design Reviews**:
- `/arckit.hld-review` - Re-review high-level design
- `/arckit.dld-review` - Re-review detailed design

**UK Government Compliance**:
- `/arckit.tcop` - Complete TCoP assessment
- `/arckit.ai-playbook` - Complete AI Playbook assessment
- `/arckit.atrs` - Generate ATRS record
- `/arckit.secure` - UK Government Secure by Design review

**MOD Compliance**:
- `/arckit.mod-secure` - MOD Secure by Design assessment with CAAT

**Traceability**:
- `/arckit.traceability` - Update traceability matrix
