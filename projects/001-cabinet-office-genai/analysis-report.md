# Architecture Governance Analysis Report

**Project**: Cabinet Office GenAI Platform (Project 001)
**Date**: 2025-11-02
**Analyzed By**: ArcKit v0.8.2

---

## Executive Summary

**Overall Status**: ⚠️ **NEW PROJECT - FOUNDATION ARTIFACTS REQUIRED**

**Key Metrics**:
- Total Requirements: 0 (not created)
- Requirements Coverage: N/A
- Critical Issues: 0
- High Priority Issues: 0
- Medium Priority Issues: 7 (missing recommended artifacts)
- Low Priority Issues: 0

**Recommendation**: **CREATE FOUNDATION ARTIFACTS** - This is a new project with only a README. Complete governance foundation before proceeding to requirements and design.

---

## Findings Summary

| ID | Category | Severity | Location(s) | Summary | Recommendation |
|----|----------|----------|-------------|---------|----------------|
| G1 | Governance Foundation | MEDIUM | Missing artifact | No architecture principles defined | Run `/arckit.principles` to establish architectural standards |
| G2 | Governance Foundation | MEDIUM | Missing artifact | No stakeholder analysis exists | Run `/arckit.stakeholders` to analyze drivers and RACI |
| G3 | Governance Foundation | MEDIUM | Missing artifact | No risk register exists | Run `/arckit.risk` for Orange Book risk analysis |
| G4 | Governance Foundation | MEDIUM | Missing artifact | No business case (SOBC) exists | Run `/arckit.sobc` for Green Book 5-case model |
| G5 | Requirements | MEDIUM | Missing artifact | No requirements.md exists | Run `/arckit.requirements` to define BR/FR/NFR |
| G6 | Data Management | MEDIUM | Missing artifact | No data model exists | Run `/arckit.data-model` after creating DR-xxx requirements |
| G7 | UK Gov Compliance | MEDIUM | Missing artifact | No compliance assessments exist | Run `/arckit.tcop`, `/arckit.ai-playbook`, `/arckit.atrs` |

---

## Project Context

### Project Overview

**Cabinet Office GenAI Platform** - A centralized, secure generative AI platform for UK Government departments providing document summarization, drafting, analysis, and knowledge management.

**Key Characteristics**:
- Multi-tenant architecture with departmental isolation
- Data classification: OFFICIAL to OFFICIAL-SENSITIVE
- AI Playbook and ATRS compliance required
- Responsible AI governance framework
- UK data residency mandatory

### Identified Stakeholders (from README)

| Stakeholder | Role | Key Interests |
|-------------|------|---------------|
| Cabinet Office | Lead | Cross-government coordination, AI governance |
| CDDO | Technical Standards | TCoP compliance, technical standards |
| Home Office | Pilot User | Immigration use cases, security requirements |
| HMRC | Pilot User | Tax guidance, data sensitivity |
| MOJ | Pilot User | Legal document analysis, classification |
| DHSC | Pilot User | Health policy analysis, GDPR |
| ICO | Regulator | Data protection oversight, GDPR compliance |
| NCSC | Security Oversight | Security architecture, Secure by Design |

**Note**: Stakeholder analysis needed to document:
- Power-interest grid classification
- Specific drivers (STRATEGIC, OPERATIONAL, FINANCIAL, COMPLIANCE)
- Driver → Goal → Outcome traceability
- Conflict identification and resolution
- RACI matrix for governance roles

### Success Criteria (from README)

The README defines these success criteria:
- 80% reduction in duplicate AI spend across government
- < 2s response time for 95% of queries
- 99.9% uptime SLA
- Zero data breaches or cross-tenant leaks
- ATRS published within 6 months of Private Beta
- AI Playbook compliance score > 90%
- User satisfaction > 4.2/5

**Note**: These should be converted to formal requirements with MUST/SHOULD/MAY priorities and traced to stakeholder goals.

---

## Artifact Coverage Analysis

### Foundation Artifacts

| Artifact | Status | Required? | Next Action |
|----------|--------|-----------|-------------|
| `.arckit/memory/architecture-principles.md` | ❌ Missing | RECOMMENDED | `/arckit.principles` - Define Cloud-First, API-First, Security-by-Design |
| `stakeholder-drivers.md` | ❌ Missing | RECOMMENDED | `/arckit.stakeholders` - Document drivers, goals, RACI |
| `risk-register.md` | ❌ Missing | RECOMMENDED | `/arckit.risk` - Orange Book risk analysis |
| `sobc.md` | ❌ Missing | RECOMMENDED | `/arckit.sobc` - Green Book 5-case business case |

### Requirements & Design

| Artifact | Status | Required? | Next Action |
|----------|--------|-----------|-------------|
| `requirements.md` | ❌ Missing | MANDATORY | `/arckit.requirements` - Define BR/FR/NFR/DR/INT |
| `data-model.md` | ❌ Missing | RECOMMENDED | `/arckit.data-model` - After DR-xxx requirements created |
| High-Level Design (HLD) | ❌ Missing | MANDATORY | Create after requirements |
| Detailed Design (DLD) | ❌ Missing | MANDATORY | Create after HLD |
| `traceability-matrix.md` | ❌ Missing | RECOMMENDED | `/arckit.traceability` - After requirements and designs |

### UK Government Compliance (MANDATORY for this project)

| Artifact | Status | Required? | Next Action |
|----------|--------|-----------|-------------|
| `tcop-assessment.md` | ❌ Missing | MANDATORY | `/arckit.tcop` - 13-point Technology Code of Practice |
| `ai-playbook-assessment.md` | ❌ Missing | MANDATORY | `/arckit.ai-playbook` - High-risk AI system |
| `atrs-record.md` | ❌ Missing | MANDATORY | `/arckit.atrs` - Tier 1 + Tier 2 for GOV.UK |
| `secure-by-design.md` | ❌ Missing | RECOMMENDED | `/arckit.secure` - UK Gov Secure by Design |

**Critical Note**: This is a **HIGH-RISK AI SYSTEM** for central government. UK Government compliance assessments are MANDATORY:
- **AI Playbook**: Required for all AI systems; high-risk requires DPIA, EqIA, bias testing, human oversight
- **ATRS**: Required for algorithmic tools in central government; must publish Tier 1 to GOV.UK
- **TCoP**: Required for all UK Government technology projects
- **Secure by Design**: RECOMMENDED for systems handling OFFICIAL-SENSITIVE data

---

## Recommended Execution Sequence

### Phase 1: Governance Foundation (Week 1)

**Create architecture principles first** - These are non-negotiable standards:

```bash
/arckit.principles
```

**Expected outputs**:
- Cloud-First principle (public cloud: AWS/Azure/GCP)
- API-First principle (OpenAPI specs, REST/GraphQL)
- Security-by-Design principle (threat modeling, defense-in-depth)
- Data Protection principle (encryption, GDPR, UK data residency)
- Open Standards principle (avoid vendor lock-in)
- Reusability principle (shared services, APIs)
- Technology standards (approved stacks, forbidden technologies)

**Create stakeholder analysis** - Understand who drives the project:

```bash
/arckit.stakeholders
```

**Expected outputs**:
- Stakeholder roster with power-interest grid (8 stakeholders identified)
- Driver types: STRATEGIC (cross-gov AI), COMPLIANCE (GDPR, AI Playbook), OPERATIONAL (efficiency), FINANCIAL (cost reduction)
- Driver → Goal → Outcome traceability
- Conflict identification (e.g., Home Office security vs DHSC data sharing)
- RACI matrix for governance (who is Responsible, Accountable, Consulted, Informed)

**Create risk register** - Identify threats using Orange Book:

```bash
/arckit.risk
```

**Expected outputs**:
- Risk categories: Strategic (AI governance failure), Technology (multi-tenancy breach), Compliance (GDPR violation), Operational (downtime), Reputational (bias incidents)
- Inherent vs Residual risk scores (5×5 matrix)
- Risk responses (4Ts: Tolerate, Treat, Transfer, Terminate)
- Risk owners from stakeholder RACI matrix
- Risk appetite and tolerance levels

**Create business case** - Justify the investment:

```bash
/arckit.sobc
```

**Expected outputs**:
- **Strategic Case**: Problem (duplicate AI spend, security risks), Drivers (cost reduction, secure AI), Urgency (proliferation of shadow AI)
- **Economic Case**: Options (Do Nothing, Centralized Platform, Federated Model), Benefits (80% cost reduction), NPV/ROI, Recommended option
- **Commercial Case**: Procurement strategy (G-Cloud, DOS), supplier market analysis
- **Financial Case**: Budget, TCO (5 years), affordability, cashflow
- **Management Case**: Governance (AI Ethics Board), Delivery (Agile sprints), Change (user adoption), Risks (from risk register), Benefits realization

### Phase 2: Requirements & Data (Week 2)

**Create comprehensive requirements**:

```bash
/arckit.requirements
```

**Expected requirements categories**:
- **Business Requirements (BR-xxx)**: Departmental isolation, cost reduction, AI governance
- **Functional Requirements (FR-xxx)**: Document summarization, drafting, Q&A, knowledge search, user management, tenant provisioning
- **Non-Functional Requirements**:
  - **Security (NFR-S-xxx)**: Multi-tenant isolation, encryption at rest/transit, MFA, RBAC, audit logging, penetration testing, Cyber Essentials Plus
  - **Performance (NFR-P-xxx)**: < 2s p95 response time, 10K concurrent users, horizontal scaling
  - **Compliance (NFR-C-xxx)**: GDPR/UK GDPR, AI Playbook, ATRS, TCoP, data residency (UK only), right to explanation
  - **Accessibility (NFR-A-xxx)**: WCAG 2.1 AA, GDS design patterns
- **Integration Requirements (INT-xxx)**: SSO (Government Gateway), directory services (Azure AD), document stores (SharePoint, Google Workspace)
- **Data Requirements (DR-xxx)**: User data, tenant data, conversation history, documents, audit logs, PII identification, GDPR retention

**Create data model** (after DR-xxx requirements):

```bash
/arckit.data-model
```

**Expected outputs**:
- Entity-Relationship Diagram (ERD) with entities: User, Tenant, Conversation, Message, Document, AuditLog
- Entity catalog with PII flags (User.email = PII, User.department = not PII)
- Data governance matrix (Data Owner from stakeholder RACI, Data Steward, Technical Custodian)
- CRUD matrix (which components access which entities)
- Data integration mapping (upstream: Azure AD, downstream: Analytics warehouse)
- DR-xxx requirement traceability

### Phase 3: UK Government Compliance (Week 3)

**Technology Code of Practice assessment**:

```bash
/arckit.tcop
```

**Expected assessment**: 13 points including:
- Point 1: Define user needs (policy advisors, civil servants)
- Point 5: Use cloud first (AWS/Azure with UK regions)
- Point 6: Make things secure (Cyber Essentials Plus, Secure by Design)
- Point 9: Use open standards (OpenAPI, OAuth 2.0, OIDC)
- Point 10: Define your data (data model, GDPR)

**AI Playbook assessment** (MANDATORY for HIGH-RISK AI):

```bash
/arckit.ai-playbook
```

**Expected assessment**:
- **Risk Level**: HIGH-RISK (generative AI, cross-government, OFFICIAL-SENSITIVE data)
- **10 Principles**: Transparency, fairness, accountability, safety, explainability, etc.
- **6 Ethical Themes**: Bias, privacy, security, sustainability, human rights, public value
- **Mandatory Assessments**:
  - ✅ DPIA (Data Protection Impact Assessment) - REQUIRED
  - ✅ EqIA (Equality Impact Assessment) - REQUIRED
  - ✅ Human Rights Assessment - REQUIRED
- **Bias Testing**: Test for demographic bias, content bias, cross-department fairness
- **Human Oversight**: Human-in-the-loop for sensitive decisions, ability to override AI

**ATRS record** (MANDATORY for central government):

```bash
/arckit.atrs
```

**Expected outputs**:
- **Tier 1** (public summary): System name, purpose, scope, data types, human oversight model, contact
- **Tier 2** (technical details): Algorithm type (LLM - GPT-4/Claude), training data, bias testing, performance metrics, fallback procedures
- **Publication**: GOV.UK algorithmic transparency page within 6 months of Private Beta

**Secure by Design review**:

```bash
/arckit.secure
```

**Expected assessment**:
- Threat modeling (STRIDE analysis)
- Security architecture (defense-in-depth, zero trust)
- Data protection (encryption, key management)
- Identity and access management (MFA, RBAC, least privilege)
- Network security (VPC isolation, private subnets, WAF)
- Monitoring and incident response (SIEM, SOC, incident playbooks)
- Supply chain security (dependency scanning, SBOM)

### Phase 4: Design & Procurement (Week 4)

**High-Level Design** (create manually or via vendor):
- System context (C4 Level 1)
- Container diagram (C4 Level 2): Web UI, API Gateway, AI Service, Tenant Manager, Auth Service, Database, Object Storage
- Component diagram (C4 Level 3): API endpoints, business logic, data access
- Technology stack: Cloud (AWS/Azure), AI (Azure OpenAI/Bedrock), Database (PostgreSQL), Auth (Azure AD B2C)
- Security architecture: WAF, VPC, encryption, secrets management
- Data architecture: Multi-tenant database design, row-level security, data isolation

**Review HLD against requirements**:

```bash
/arckit.hld-review
```

**Detailed Design** (create after HLD):
- API contracts (OpenAPI specs)
- Database schemas (DDL)
- Security implementation (IAM policies, encryption configs)
- Deployment architecture (Kubernetes, Terraform)

**Review DLD for implementation readiness**:

```bash
/arckit.dld-review
```

**Traceability matrix**:

```bash
/arckit.traceability
```

**Expected traceability**:
- Requirements → HLD components → DLD specifications → Test cases
- Stakeholder goals → Requirements → Design → Benefits
- Risks → Mitigation requirements → Design controls

### Phase 5: Governance Analysis (Week 5)

**Re-run analysis after all artifacts created**:

```bash
/arckit.analyze
```

**Expected results**:
- Governance Health Score: 85-95% (Grade A/B)
- Requirements Coverage: > 90%
- Principles Compliance: 100%
- Stakeholder Alignment: > 90%
- Risk Management: > 85%
- UK Gov Compliance: > 90% (TCoP, AI Playbook, ATRS)
- Critical Issues: 0
- High Priority Issues: < 5
- Recommendation: READY TO PROCEED

---

## Key Risks to Address Early

Based on the project description, these risks should be prioritized in the risk register:

| Risk ID | Risk Description | Category | Likelihood | Impact | Priority |
|---------|------------------|----------|------------|--------|----------|
| R-??? | Multi-tenant data leakage (cross-department breach) | Technology | Medium | Very High | CRITICAL |
| R-??? | AI generates biased policy recommendations | Compliance | High | High | CRITICAL |
| R-??? | GDPR violation due to improper data handling | Compliance | Medium | Very High | CRITICAL |
| R-??? | Vendor lock-in to single AI provider (Azure/AWS) | Strategic | High | Medium | HIGH |
| R-??? | User adoption failure (departments prefer own tools) | Operational | Medium | High | HIGH |
| R-??? | Cost overruns due to high AI API usage | Financial | Medium | Medium | MEDIUM |
| R-??? | Security breach of OFFICIAL-SENSITIVE data | Security | Low | Very High | HIGH |
| R-??? | ATRS publication reveals sensitive capabilities | Reputational | Medium | Medium | MEDIUM |

**Note**: These are placeholder risks. Run `/arckit.risk` to create a comprehensive Orange Book risk register with detailed risk descriptions, inherent/residual scores, risk responses (4Ts), owners, and mitigation actions.

---

## Key Requirements to Address

Based on success criteria in README, these requirements should be created:

### Business Requirements (BR-xxx)

- **BR-001**: Reduce duplicate AI spending across government by 80% within 12 months of Public Beta
- **BR-002**: Provide centralized AI service for 20+ central government departments
- **BR-003**: Ensure departmental data isolation (no cross-tenant data leakage)
- **BR-004**: Comply with AI Playbook for high-risk AI systems
- **BR-005**: Publish ATRS record within 6 months of Private Beta

### Functional Requirements (FR-xxx)

- **FR-001**: Support document summarization for policy papers, briefings, and reports
- **FR-002**: Enable AI-assisted drafting of government documents
- **FR-003**: Provide question-answering over departmental knowledge bases
- **FR-004**: Implement multi-tenant architecture with department-level isolation
- **FR-005**: Integrate with Government Gateway for SSO authentication
- **FR-006**: Support role-based access control (RBAC) at department and user levels
- **FR-007**: Provide audit logging for all AI queries and responses
- **FR-008**: Enable human review and override of AI recommendations

### Non-Functional Requirements

**Security (NFR-S-xxx)**:
- **NFR-S-001**: Encrypt data at rest using AES-256 encryption
- **NFR-S-002**: Encrypt data in transit using TLS 1.3
- **NFR-S-003**: Implement multi-factor authentication (MFA) for all users
- **NFR-S-004**: Achieve Cyber Essentials Plus certification before Private Beta
- **NFR-S-005**: Conduct annual penetration testing by CREST-certified testers
- **NFR-S-006**: Implement row-level security for multi-tenant database isolation
- **NFR-S-007**: Store all data in UK-based data centers (data residency)
- **NFR-S-008**: Implement Web Application Firewall (WAF) with OWASP Top 10 protections

**Performance (NFR-P-xxx)**:
- **NFR-P-001**: Respond to 95% of queries in < 2 seconds (p95 latency)
- **NFR-P-002**: Support 10,000 concurrent users across all departments
- **NFR-P-003**: Achieve 99.9% uptime SLA (< 8.76 hours downtime/year)
- **NFR-P-004**: Scale horizontally to handle 5x peak load during crises

**Compliance (NFR-C-xxx)**:
- **NFR-C-001**: Comply with UK GDPR for all personal data processing
- **NFR-C-002**: Implement right to erasure (GDPR Article 17) within 30 days
- **NFR-C-003**: Provide explainability for AI recommendations (AI Playbook)
- **NFR-C-004**: Complete DPIA before processing OFFICIAL-SENSITIVE data
- **NFR-C-005**: Comply with Technology Code of Practice (TCoP) 13 points
- **NFR-C-006**: Publish ATRS record (Tier 1) on GOV.UK
- **NFR-C-007**: Conduct bias testing across demographic groups and departments

**Accessibility (NFR-A-xxx)**:
- **NFR-A-001**: Comply with WCAG 2.1 Level AA for web interface
- **NFR-A-002**: Follow GDS Design System patterns for UK Government services

**Data (DR-xxx)**:
- **DR-001**: Store user profiles with department affiliation and roles
- **DR-002**: Store conversation history with tenant isolation
- **DR-003**: Store uploaded documents with encryption and access control
- **DR-004**: Store audit logs for 7 years (compliance requirement)
- **DR-005**: Identify and tag PII (user email, name, department)
- **DR-006**: Implement data retention policy (30 days for conversations, 7 years for audit logs)

**Note**: These are example requirements. Run `/arckit.requirements` to create comprehensive requirements traced to stakeholder goals and validated against architecture principles.

---

## UK Government Compliance Roadmap

### Technology Code of Practice (TCoP) - 13 Points

This project MUST comply with all 13 TCoP points before deployment:

| Point | Requirement | Compliance Strategy |
|-------|-------------|---------------------|
| 1 | Define user needs | User research with policy advisors and civil servants (Discovery phase) |
| 2 | Make things accessible | WCAG 2.1 AA, GDS Design System |
| 3 | Be open and use open standards | OpenAPI for APIs, OAuth 2.0/OIDC for auth, open-source components |
| 4 | Make use of open source | Use open-source AI frameworks (LangChain), databases (PostgreSQL) |
| 5 | Use cloud first | AWS/Azure with UK regions, cloud-native architecture |
| 6 | Make things secure | Cyber Essentials Plus, Secure by Design, NCSC guidance |
| 7 | Make privacy integral | GDPR compliance, DPIA, privacy-by-design |
| 8 | Share, reuse, collaborate | Shared AI platform for all departments, reusable APIs |
| 9 | Integrate and adapt technology | Integrate with existing gov systems (Government Gateway, Azure AD) |
| 10 | Make better use of data | Data model, data governance, analytics |
| 11 | Define your purchasing strategy | G-Cloud procurement, avoid vendor lock-in |
| 12 | Meet the Digital Service Standard | GDS Service Assessment before Public Beta |
| 13 | Use and contribute to common components | GOV.UK Notify, Pay, Verify integration |

### AI Playbook - High-Risk AI System

This is a **HIGH-RISK AI SYSTEM** because:
- Generative AI with potential for bias and hallucination
- Cross-government scope (affects multiple departments)
- Handles OFFICIAL-SENSITIVE data
- Policy and decision-support use cases

**Mandatory Requirements**:
1. ✅ **Data Protection Impact Assessment (DPIA)** - Before Private Beta
2. ✅ **Equality Impact Assessment (EqIA)** - Test for demographic bias
3. ✅ **Human Rights Assessment** - Ensure no adverse impact on citizen rights
4. ✅ **Bias Testing** - Test across:
   - Demographics (age, gender, ethnicity, disability)
   - Departments (ensure no favoritism)
   - Content types (policy, legal, health, immigration)
5. ✅ **Human Oversight Model** - Human-in-the-loop for:
   - High-stakes decisions
   - Sensitive policy areas
   - User-flagged concerns
6. ✅ **Explainability** - Provide:
   - Source attribution (which documents informed answer)
   - Confidence scores
   - Alternative interpretations
7. ✅ **AI Ethics Board** - Quarterly reviews of:
   - Bias incidents
   - User complaints
   - Model performance
   - Ethical concerns

### ATRS (Algorithmic Transparency Recording Standard)

**MANDATORY for central government algorithmic tools**

**Publication Timeline**:
- **Discovery/Alpha**: Draft ATRS (internal)
- **Private Beta**: Complete Tier 1 + Tier 2
- **6 months after Private Beta**: Publish Tier 1 to GOV.UK

**Tier 1 (Public Summary)** - Must include:
- System name: "Cabinet Office GenAI Platform"
- Purpose: "AI-assisted document analysis and policy support"
- Scope: "Central government departments (20+ orgs)"
- Owner: "Cabinet Office"
- Contact: dataprotection@cabinetoffice.gov.uk
- Data types: "Policy documents, user queries, conversation history"
- Human oversight: "Human review for high-stakes decisions, user override capability"
- Risk level: "High-risk AI system under AI Playbook"

**Tier 2 (Technical Details)** - Must include:
- Algorithm type: "Large Language Model (GPT-4 / Claude 3)"
- Training data: "Proprietary LLM (Azure OpenAI / Anthropic), fine-tuned on government corpus"
- Performance metrics: "Response time < 2s p95, accuracy testing in progress"
- Bias testing: "Demographic and departmental bias testing conducted quarterly"
- Fallback procedures: "Human escalation, search alternative, manual document review"

---

## Architecture Principles Recommendations

When running `/arckit.principles`, consider these principles for this project:

### Strategic Principles

**Cloud-First**:
- **Principle**: All systems MUST use public cloud (AWS, Azure, GCP) unless explicitly justified exception
- **Rationale**: UK Government TCoP Point 5, scalability, cost efficiency
- **Validation**: Architecture design uses AWS/Azure with UK regions
- **Implications**: No on-premise infrastructure, cloud-native design patterns

**API-First**:
- **Principle**: All services MUST expose REST/GraphQL APIs with OpenAPI specifications
- **Rationale**: Reusability, integration, TCoP Point 3 (open standards)
- **Validation**: All APIs documented in OpenAPI 3.0, versioned, backward compatible
- **Implications**: API gateway, versioning strategy, deprecation policy

**Reuse Before Buy, Buy Before Build**:
- **Principle**: Prefer existing gov shared services, then commercial off-the-shelf, then custom build
- **Rationale**: Cost efficiency, faster delivery, reduced risk
- **Validation**: Use GOV.UK Notify, Pay, Verify; use Azure OpenAI/Bedrock (not train own LLM)
- **Implications**: Wardley Mapping to identify build vs buy decisions

### Security Principles

**Security-by-Design**:
- **Principle**: Security MUST be embedded from inception, not bolted on
- **Rationale**: NCSC Secure by Design, TCoP Point 6
- **Validation**: Threat model exists, security architecture in HLD, penetration testing before launch
- **Implications**: Security champions in delivery team, security review at each gate

**Defense-in-Depth**:
- **Principle**: Implement multiple layers of security controls
- **Rationale**: No single point of failure, compensating controls
- **Validation**: Network (VPC, WAF), application (RBAC, input validation), data (encryption at rest/transit)
- **Implications**: Increased complexity, but reduced risk

**Least Privilege**:
- **Principle**: Users and services MUST have minimum permissions required
- **Rationale**: Reduce blast radius of compromise
- **Validation**: RBAC with granular permissions, service accounts with scoped IAM roles
- **Implications**: IAM policy management, regular access reviews

### Data Principles

**UK Data Residency**:
- **Principle**: All data MUST be stored and processed in UK data centers
- **Rationale**: Data sovereignty, legal jurisdiction, government policy
- **Validation**: Cloud region = UK South/UK West (Azure) or eu-west-2 (AWS London)
- **Implications**: Cannot use global AI services with US data processing

**Privacy-by-Design**:
- **Principle**: GDPR/UK GDPR compliance MUST be embedded in system design
- **Rationale**: Legal requirement, TCoP Point 7, user trust
- **Validation**: DPIA completed, data minimization, encryption, right to erasure implemented
- **Implications**: Data mapping, consent management, privacy controls

**Data Classification**:
- **Principle**: All data MUST be classified (PUBLIC, OFFICIAL, OFFICIAL-SENSITIVE, SECRET)
- **Rationale**: Apply proportionate security controls
- **Validation**: Data model includes classification field, access controls enforce classification
- **Implications**: Classification training, labeling, access policies

### AI/ML Principles

**Responsible AI**:
- **Principle**: AI systems MUST be transparent, fair, accountable, and safe
- **Rationale**: AI Playbook compliance, ethical AI deployment
- **Validation**: Bias testing, explainability, human oversight, AI Ethics Board
- **Implications**: AI governance framework, continuous monitoring, incident response

**Human-in-the-Loop**:
- **Principle**: High-stakes AI decisions MUST have human review and override capability
- **Rationale**: AI Playbook requirement for high-risk AI, maintain accountability
- **Validation**: User can flag AI responses, human review queue, override mechanism
- **Implications**: Human review workflows, escalation procedures

**Algorithmic Transparency**:
- **Principle**: AI systems MUST publish ATRS record and provide explainability
- **Rationale**: ATRS mandatory for central government, user trust, accountability
- **Validation**: ATRS published on GOV.UK, source attribution provided, confidence scores shown
- **Implications**: Explainability features, public disclosure, transparency reporting

### Technology Standards

**Approved Technology Stack**:
- **Cloud Platforms**: AWS, Azure, GCP (UK regions only)
- **AI Services**: Azure OpenAI, AWS Bedrock, Anthropic Claude (UK endpoints)
- **Databases**: PostgreSQL, Amazon RDS, Azure SQL Database
- **Authentication**: OAuth 2.0, OIDC, SAML 2.0 (Government Gateway integration)
- **APIs**: REST (OpenAPI 3.0), GraphQL
- **Languages**: Python, TypeScript, Go
- **Frameworks**: FastAPI, NestJS, React
- **Infrastructure-as-Code**: Terraform, CloudFormation

**Forbidden Technologies**:
- ❌ Self-hosted LLMs (use managed services for security and compliance)
- ❌ Non-UK data centers
- ❌ Closed-source AI models without transparency
- ❌ Deprecated authentication (OAuth 1.0, WS-Federation)
- ❌ Unsupported frameworks (AngularJS, Backbone.js)

---

## Stakeholder Analysis Preview

When running `/arckit.stakeholders`, expect to document:

### Power-Interest Grid

**High Power, High Interest** (Manage Closely):
- Cabinet Office (Lead, Accountable)
- CDDO (Technical Authority, TCoP compliance)
- NCSC (Security assurance, Secure by Design)

**High Power, Low Interest** (Keep Satisfied):
- HM Treasury (Budget approval, Green Book compliance)
- ICO (Data protection, GDPR oversight)

**Low Power, High Interest** (Keep Informed):
- Home Office (Pilot user, immigration use cases)
- HMRC (Pilot user, tax guidance)
- MOJ (Pilot user, legal analysis)
- DHSC (Pilot user, health policy)

**Low Power, Low Interest** (Monitor):
- Other government departments (future users)

### Driver Examples

**Cabinet Office**:
- **STRATEGIC**: Reduce duplicate AI spending across government (80% reduction target)
- **COMPLIANCE**: Ensure AI Playbook compliance for high-risk AI
- **OPERATIONAL**: Centralize AI governance and prevent shadow AI proliferation

**CDDO**:
- **COMPLIANCE**: Enforce Technology Code of Practice (13 points)
- **STRATEGIC**: Promote open standards and cloud-first architecture
- **OPERATIONAL**: Enable cross-government digital services

**NCSC**:
- **COMPLIANCE**: Secure by Design compliance for OFFICIAL-SENSITIVE data
- **RISK**: Prevent multi-tenant data breaches
- **OPERATIONAL**: Ensure Cyber Essentials Plus certification

**Home Office**:
- **OPERATIONAL**: Improve immigration case analysis efficiency
- **COMPLIANCE**: Ensure security controls for sensitive immigration data
- **PERSONAL**: Reduce analyst workload, improve decision quality

**ICO**:
- **COMPLIANCE**: GDPR/UK GDPR compliance for PII processing
- **RISK**: Prevent data breaches and unlawful processing
- **REPUTATIONAL**: Maintain public trust in government AI use

### Expected Conflicts

**Conflict 1**: Security (NCSC) vs Usability (Departments)
- **NCSC**: Requires strict access controls, MFA, network isolation
- **Departments**: Want easy access, minimal friction, mobile support
- **Resolution**: Implement SSO with Government Gateway, conditional access policies (MFA only for sensitive data)

**Conflict 2**: Cost Reduction (Cabinet Office) vs Feature Richness (Departments)
- **Cabinet Office**: Minimize costs, standardize platform
- **Departments**: Want custom features, integrations, fine-tuned models
- **Resolution**: Tiered service model (Standard, Premium), chargeback for custom features

**Conflict 3**: Transparency (ATRS) vs Security (NCSC)
- **ATRS**: Publish algorithmic details on GOV.UK
- **NCSC**: Avoid disclosing security-sensitive architecture
- **Resolution**: Tier 1 (public) excludes sensitive details, Tier 2 (internal) provides full transparency

### RACI Matrix Example

| Activity | Cabinet Office | CDDO | NCSC | Home Office | HMRC | MOJ | DHSC | ICO |
|----------|---------------|------|------|-------------|------|-----|------|-----|
| Project Sponsorship | **A** | C | C | I | I | I | I | I |
| Architecture Design | C | **A/R** | C | C | C | C | C | I |
| Security Assurance | C | C | **A/R** | I | I | I | I | I |
| DPIA Approval | C | I | I | I | I | I | I | **A** |
| User Requirements | C | I | I | **R** | **R** | **R** | **R** | I |
| AI Ethics Oversight | **A/R** | C | I | C | C | C | C | C |
| Budget Approval | **A** | I | I | I | I | I | I | I |
| Procurement | **R** | C | I | I | I | I | I | I |
| Service Delivery | **R** | C | C | C | C | C | C | I |

**Legend**: **A** = Accountable, **R** = Responsible, **C** = Consulted, **I** = Informed

---

## Risk Register Preview

When running `/arckit.risk`, expect to document:

### Strategic Risks

**R-001: AI Governance Failure**
- **Description**: Lack of effective AI ethics oversight leads to biased or harmful AI decisions affecting policy
- **Category**: Strategic
- **Likelihood**: Medium (3/5)
- **Impact**: Very High (5/5)
- **Inherent Risk**: 15 (Very High)
- **Response**: TREAT
- **Mitigation Actions**:
  - Establish AI Ethics Board with quarterly reviews (BR-xxx)
  - Implement bias testing framework (NFR-C-007)
  - Publish ATRS record for transparency (NFR-C-006)
  - Human-in-the-loop for high-stakes decisions (FR-008)
- **Residual Risk**: 9 (Medium) after mitigation
- **Owner**: Cabinet Office (Chief Data Officer)

**R-002: Vendor Lock-In**
- **Description**: Dependency on single AI provider (Azure/AWS) limits flexibility and increases costs
- **Category**: Strategic
- **Likelihood**: High (4/5)
- **Impact**: Medium (3/5)
- **Inherent Risk**: 12 (High)
- **Response**: TREAT
- **Mitigation Actions**:
  - Design abstraction layer for AI services (architecture requirement)
  - Support multiple LLM providers (Azure OpenAI, AWS Bedrock, Anthropic)
  - Use open standards (OpenAPI, OAuth) to enable portability
- **Residual Risk**: 6 (Medium) after mitigation
- **Owner**: CDDO (Technical Architect)

### Technology Risks

**R-003: Multi-Tenant Data Leakage**
- **Description**: Database misconfiguration or application bug allows cross-department data access
- **Category**: Technology
- **Likelihood**: Medium (3/5)
- **Impact**: Very High (5/5)
- **Inherent Risk**: 15 (Very High)
- **Response**: TREAT
- **Mitigation Actions**:
  - Implement row-level security in database (NFR-S-006)
  - Use separate database schemas per tenant
  - Conduct penetration testing focused on multi-tenancy (NFR-S-005)
  - Implement automated testing for tenant isolation (test requirement)
- **Residual Risk**: 6 (Medium) after mitigation
- **Owner**: NCSC (Security Lead)

**R-004: Performance Degradation Under Load**
- **Description**: System fails to meet < 2s response time SLA during peak usage (budget season, crisis)
- **Category**: Technology
- **Likelihood**: Medium (3/5)
- **Impact**: High (4/5)
- **Inherent Risk**: 12 (High)
- **Response**: TREAT
- **Mitigation Actions**:
  - Design horizontal scaling architecture (NFR-P-004)
  - Implement caching layer (Redis) for frequent queries
  - Load testing with 5x peak load before Private Beta
  - Auto-scaling policies for compute and AI services
- **Residual Risk**: 4 (Low) after mitigation
- **Owner**: CDDO (Service Owner)

### Compliance Risks

**R-005: GDPR Violation**
- **Description**: Improper handling of PII leads to ICO investigation, fines, and reputational damage
- **Category**: Compliance
- **Likelihood**: Medium (3/5)
- **Impact**: Very High (5/5)
- **Inherent Risk**: 15 (Very High)
- **Response**: TREAT
- **Mitigation Actions**:
  - Complete DPIA before Private Beta (NFR-C-004)
  - Implement right to erasure within 30 days (NFR-C-002)
  - Data minimization (only collect necessary PII) (DR-005)
  - UK data residency (NFR-S-007)
  - Encryption at rest and in transit (NFR-S-001, NFR-S-002)
- **Residual Risk**: 6 (Medium) after mitigation
- **Owner**: ICO (Data Protection Officer)

**R-006: AI Playbook Non-Compliance Blocks Deployment**
- **Description**: Failure to meet AI Playbook requirements prevents Public Beta launch
- **Category**: Compliance
- **Likelihood**: Medium (3/5)
- **Impact**: High (4/5)
- **Inherent Risk**: 12 (High)
- **Response**: TREAT
- **Mitigation Actions**:
  - Complete AI Playbook assessment early (Alpha phase)
  - Conduct DPIA, EqIA, Human Rights Assessment (NFR-C-004)
  - Implement bias testing framework (NFR-C-007)
  - Establish human oversight model (FR-008)
  - Publish ATRS before Public Beta (NFR-C-006)
- **Residual Risk**: 4 (Low) after mitigation
- **Owner**: Cabinet Office (Senior Responsible Owner)

### Operational Risks

**R-007: User Adoption Failure**
- **Description**: Departments prefer their own AI tools over centralized platform
- **Category**: Operational
- **Likelihood**: Medium (3/5)
- **Impact**: High (4/5)
- **Inherent Risk**: 12 (High)
- **Response**: TREAT
- **Mitigation Actions**:
  - User research with policy advisors in Discovery (TCoP Point 1)
  - Private Beta with 3 pilot departments to refine UX
  - Training and change management program
  - Integration with existing workflows (SharePoint, Google Workspace)
  - Demonstrate cost savings and efficiency gains
- **Residual Risk**: 6 (Medium) after mitigation
- **Owner**: Cabinet Office (Change Manager)

### Financial Risks

**R-008: Cost Overruns from AI API Usage**
- **Description**: High LLM API costs exceed budget due to usage patterns
- **Category**: Financial
- **Likelihood**: Medium (3/5)
- **Impact**: Medium (3/5)
- **Inherent Risk**: 9 (Medium)
- **Response**: TREAT
- **Mitigation Actions**:
  - Implement usage quotas per department
  - Caching to reduce redundant API calls
  - Cost monitoring and alerting (AWS Cost Explorer, Azure Cost Management)
  - Chargeback model to share costs with departments
- **Residual Risk**: 4 (Low) after mitigation
- **Owner**: Cabinet Office (Finance Manager)

### Reputational Risks

**R-009: Bias Incident Damages Public Trust**
- **Description**: AI generates biased output (racial, gender, political) leading to media scandal
- **Category**: Reputational
- **Likelihood**: Medium (3/5)
- **Impact**: High (4/5)
- **Inherent Risk**: 12 (High)
- **Response**: TREAT
- **Mitigation Actions**:
  - Bias testing across demographics and content types (NFR-C-007)
  - User feedback mechanism to flag bias
  - AI Ethics Board to review bias incidents
  - Incident response plan for bias events
  - Transparency via ATRS publication (NFR-C-006)
- **Residual Risk**: 6 (Medium) after mitigation
- **Owner**: Cabinet Office (AI Ethics Lead)

---

## Business Case Preview (SOBC)

When running `/arckit.sobc`, expect to document:

### Strategic Case

**The Problem**:
- Duplicate AI spending across 20+ government departments (estimated £15M/year)
- Shadow AI proliferation (uncontrolled use of ChatGPT, insecure tools)
- Data leakage risks (civil servants uploading OFFICIAL data to public AI services)
- Inconsistent AI governance and ethics oversight
- Missed opportunity for cross-government AI efficiencies

**Strategic Drivers** (from stakeholder analysis):
- **Cabinet Office**: Reduce duplicate spending, centralize AI governance
- **CDDO**: Enforce TCoP compliance, promote cloud-first architecture
- **NCSC**: Secure AI usage, prevent data breaches
- **Departments**: Improve policy analysis efficiency, reduce analyst workload

**Why Now?** (Urgency):
- Proliferation of shadow AI tools across government (uncontrolled)
- Recent data breaches from civil servants using public ChatGPT
- AI Playbook published (October 2023) - compliance now mandatory
- Budget pressure - need to reduce AI costs
- GenAI maturity - enterprise-grade solutions now available (Azure OpenAI, Bedrock)

**Stakeholder Goals** (from stakeholder drivers):
- Cabinet Office: 80% reduction in duplicate AI spend
- CDDO: 100% TCoP compliance across AI projects
- NCSC: Zero data breaches from AI usage
- Departments: 30% improvement in policy analysis efficiency

### Economic Case

**Options Analyzed**:

**Option 1: Do Nothing (Baseline)**
- **Description**: Continue with decentralized AI procurement, no governance
- **Benefits**: No upfront investment
- **Costs**: £15M/year duplicate spending, ongoing data breach risk
- **Risks**: High - data leakage, bias incidents, non-compliance
- **NPV (5 years)**: -£75M
- **Recommendation**: REJECT - unsustainable costs and risks

**Option 2: Centralized AI Platform (Recommended)**
- **Description**: Build Cabinet Office-hosted multi-tenant AI service with Azure OpenAI/Bedrock
- **Benefits**:
  - £12M/year cost savings (80% reduction from £15M to £3M)
  - Centralized AI governance and ethics oversight
  - Secure multi-tenant architecture (zero data leakage)
  - AI Playbook and ATRS compliance
- **Costs**:
  - Implementation: £2M (Year 1)
  - Operations: £3M/year (cloud, AI APIs, support)
- **NPV (5 years)**: +£38M (12M savings x 5 years - 2M implementation - 3M ops x 5 years)
- **ROI**: 253% over 5 years
- **Payback Period**: 2 years
- **Recommendation**: ACCEPT

**Option 3: Federated Model (Shared Standards, Decentralized Procurement)**
- **Description**: Departments procure own AI tools but follow shared standards and governance
- **Benefits**:
  - Flexibility for department-specific needs
  - Shared governance framework
- **Costs**:
  - £10M/year (some duplication remains)
  - Governance overhead (£500K/year for standards enforcement)
- **NPV (5 years)**: +£5M
- **Risks**: Medium - harder to enforce standards, some duplication
- **Recommendation**: CONSIDER as fallback if Option 2 fails

**Benefits Summary (Option 2)**:

| Benefit ID | Benefit Description | Stakeholder Goal | Quantified? | Value (5 years) |
|------------|---------------------|------------------|-------------|-----------------|
| B-001 | Reduce duplicate AI spending | Cabinet Office G-1 | ✅ Yes | £60M savings |
| B-002 | Prevent data breaches from AI usage | NCSC G-1 | ⚠️ Risk reduction | Avoid £5M+ incident costs |
| B-003 | Improve policy analysis efficiency | Departments G-1 | ✅ Yes | 30% time savings = £10M FTE costs |
| B-004 | Centralized AI governance | Cabinet Office G-2 | ⚠️ Qualitative | Compliance, trust |
| B-005 | AI Playbook compliance | CDDO G-1 | ✅ Yes | Avoid deployment blocks |

**Total Quantified Benefits**: £70M over 5 years
**Total Costs**: £17M over 5 years (£2M implementation + £15M operations)
**Net Benefit**: £53M
**Benefit-Cost Ratio**: 4.1:1

### Commercial Case

**Procurement Strategy**: G-Cloud 14 framework (Digital Outcomes and Specialists)

**Supplier Market**:
- **Cloud Providers**: AWS (Bedrock), Azure (OpenAI), GCP (Vertex AI)
- **System Integrators**: Accenture, Deloitte, PA Consulting, Capgemini
- **AI Specialists**: Faculty, Cambridge Consultants, Kainos

**Procurement Approach**:
- **Phase 1**: Use existing G-Cloud call-offs for cloud services (AWS/Azure)
- **Phase 2**: DOS5 competition for system integration (£1M-£2M)
- **Phase 3**: Ongoing support via T&M contracts

**Contractual Approach**:
- Cloud services: Pay-as-you-go (consumption-based pricing)
- System integration: Fixed-price for implementation (£2M)
- Support: Time & materials (£500K/year)

**Risk Mitigation**:
- Multi-cloud strategy to avoid vendor lock-in (Azure + AWS)
- Open standards (OpenAPI, OAuth) to enable portability
- Avoid proprietary AI models (use Azure OpenAI, Bedrock, Anthropic)

### Financial Case

**Budget Summary (5 years)**:

| Year | Implementation | Cloud Infrastructure | AI APIs | Support | Total |
|------|----------------|----------------------|---------|---------|-------|
| 1 | £2M | £300K | £1.5M | £500K | £4.3M |
| 2 | - | £400K | £2M | £500K | £2.9M |
| 3 | - | £500K | £2.5M | £500K | £3.5M |
| 4 | - | £600K | £2.8M | £500K | £3.9M |
| 5 | - | £700K | £3M | £500K | £4.2M |
| **Total** | **£2M** | **£2.5M** | **£11.8M** | **£2.5M** | **£18.8M** |

**Funding Source**: Cabinet Office central budget (£2M Year 1), then chargeback to departments (£3M/year)

**Affordability**: Yes - £4.3M Year 1 < Cabinet Office allocated budget (£5M), departments save £12M/year vs current spend (£15M)

**Cashflow**: Positive from Year 2 (savings > costs)

### Management Case

**Governance Structure**:
- **Senior Responsible Owner**: Cabinet Office Permanent Secretary
- **Project Board**: Cabinet Office, CDDO, NCSC, HM Treasury
- **AI Ethics Board**: Quarterly reviews of bias, ethics, user complaints
- **Delivery Team**: Product Owner, Technical Architect, Security Lead, Developers

**Delivery Approach**: Agile (2-week sprints), GDS Service Standard

**Change Management**:
- Training for 2,000 civil servants (policy advisors, analysts)
- Champions network in each department
- User support via shared mailbox and knowledge base

**Risk Management**: See Risk Register (run `/arckit.risk`)
- Top risks: Multi-tenant data leakage (R-003), GDPR violation (R-005), user adoption failure (R-007)
- Risk owners from stakeholder RACI matrix
- Quarterly risk reviews by Project Board

**Benefits Realization**:
- Benefits owner: Cabinet Office (Finance Director)
- Measurement:
  - B-001 (Cost reduction): Monthly chargeback reports vs baseline (£15M)
  - B-002 (Data breaches): Zero incidents measured via audit logs
  - B-003 (Efficiency): User surveys (time savings), usage analytics (queries/user)
- Reporting: Quarterly benefits realization reports to Project Board

**Key Milestones**:
- Month 2: Stakeholder analysis, requirements, SOBC approved
- Month 5: Alpha prototype, AI Playbook assessment, security testing
- Month 9: Private Beta with 3 departments, ATRS published
- Month 12: GDS Service Assessment, Public Beta approval
- Month 13: Live service, full rollout to 20+ departments

---

## Metrics Dashboard

### Requirement Quality
- Total Requirements: 0 (not created)
- Ambiguous Requirements: N/A
- Duplicate Requirements: N/A
- Untestable Requirements: N/A
- **Quality Score**: N/A (create requirements first)

### Architecture Alignment
- Principles Compliant: N/A (no principles defined)
- Principles Violations: 0
- **Alignment Score**: N/A (create principles first)

### Traceability
- Requirements Covered: N/A
- Orphan Components: N/A
- **Traceability Score**: N/A (create requirements and design first)

### Stakeholder Traceability
- Requirements traced to stakeholder goals: N/A (no stakeholder analysis)
- Orphan requirements: N/A
- Conflicts resolved: N/A
- RACI governance alignment: N/A
- **Stakeholder Score**: N/A (run `/arckit.stakeholders` first)

### Risk Management
- High/Very High risks mitigated: N/A (no risk register)
- Risk owners from RACI: N/A
- Risks reflected in design: N/A
- Risk-SOBC alignment: N/A
- **Risk Management Score**: N/A (run `/arckit.risk` first)

### Business Case
- Benefits traced to stakeholder goals: N/A (no SOBC)
- Benefits supported by requirements: N/A
- Benefits measurable: N/A
- Budget adequacy: N/A
- **Business Case Score**: N/A (run `/arckit.sobc` first)

### Data Model
- DR-xxx requirements mapped to entities: N/A (no data model)
- Entities traced to DR-xxx: N/A
- PII identified: N/A
- Data governance complete: N/A
- Data model-design alignment: N/A
- **Data Model Score**: N/A (run `/arckit.data-model` after DR-xxx requirements)

### UK Government Compliance
- TCoP Score: N/A (no assessment)
- AI Playbook Score: N/A (no assessment)
- ATRS Completeness: N/A (no record)
- **UK Gov Compliance Score**: N/A (run compliance assessments)

### MOD Compliance
- Not applicable (this is a Cabinet Office project, not MOD)

### Overall Governance Health
**Score**: N/A (no artifacts to analyze)
**Grade**: N/A

**Status**: **NEW PROJECT - FOUNDATION ARTIFACTS REQUIRED**

---

## Recommendations

### Critical Actions (MUST complete before proceeding)

**None** - This is a new project with no artifacts yet. No critical issues found in README.

### High Priority Actions (SHOULD complete in Phase 1)

**None** - No high priority issues found. Project is well-scoped in README.

### Medium Priority Actions (Create foundation artifacts)

1. **[G1] Create architecture principles** (`/arckit.principles`)
   - **Why**: Establishes non-negotiable technical standards
   - **When**: Week 1
   - **Estimated Effort**: 2-3 hours

2. **[G2] Create stakeholder analysis** (`/arckit.stakeholders`)
   - **Why**: Document drivers, goals, conflicts, RACI matrix
   - **When**: Week 1
   - **Estimated Effort**: 3-4 hours

3. **[G3] Create risk register** (`/arckit.risk`)
   - **Why**: Identify and mitigate threats using Orange Book framework
   - **When**: Week 1
   - **Estimated Effort**: 3-4 hours

4. **[G4] Create business case** (`/arckit.sobc`)
   - **Why**: Justify investment using Green Book 5-case model
   - **When**: Week 1-2
   - **Estimated Effort**: 4-6 hours

5. **[G5] Create requirements** (`/arckit.requirements`)
   - **Why**: Define BR/FR/NFR/DR/INT requirements traced to stakeholder goals
   - **When**: Week 2
   - **Estimated Effort**: 6-8 hours

6. **[G6] Create data model** (`/arckit.data-model`)
   - **Why**: Define entities, PII, GDPR compliance, data governance
   - **When**: Week 2 (after DR-xxx requirements)
   - **Estimated Effort**: 3-4 hours

7. **[G7] Create UK Gov compliance assessments** (`/arckit.tcop`, `/arckit.ai-playbook`, `/arckit.atrs`)
   - **Why**: MANDATORY for UK Government high-risk AI system
   - **When**: Week 3
   - **Estimated Effort**: 6-8 hours total

### Low Priority Actions

**None** - Focus on foundation artifacts first.

---

## Next Steps

### Immediate Actions (Week 1)

**Step 1: Create Architecture Principles**

```bash
/arckit.principles
```

**Expected outputs**:
- Strategic principles (Cloud-First, API-First, Reuse Before Buy)
- Security principles (Security-by-Design, Defense-in-Depth, Least Privilege)
- Data principles (UK Data Residency, Privacy-by-Design, Data Classification)
- AI/ML principles (Responsible AI, Human-in-the-Loop, Algorithmic Transparency)
- Technology standards (approved stack, forbidden technologies)

**Step 2: Create Stakeholder Analysis**

```bash
/arckit.stakeholders
```

**Expected outputs**:
- 8 stakeholders with power-interest grid
- Driver types (STRATEGIC, OPERATIONAL, FINANCIAL, COMPLIANCE)
- Driver → Goal → Outcome traceability
- Conflict resolution (Security vs Usability, Cost vs Features, Transparency vs Security)
- RACI matrix for governance

**Step 3: Create Risk Register**

```bash
/arckit.risk
```

**Expected outputs**:
- 9+ risks across categories (Strategic, Technology, Compliance, Operational, Financial, Reputational)
- Inherent vs Residual risk scores (5×5 matrix)
- Risk responses (4Ts: Tolerate, Treat, Transfer, Terminate)
- Risk owners from stakeholder RACI
- Risk appetite and tolerance levels

**Step 4: Create Business Case**

```bash
/arckit.sobc
```

**Expected outputs**:
- Strategic Case (problem, drivers, urgency, stakeholder goals)
- Economic Case (3 options, benefits quantified, NPV £38M, ROI 253%)
- Commercial Case (G-Cloud procurement, multi-cloud strategy)
- Financial Case (£18.8M over 5 years, chargeback model)
- Management Case (governance, delivery, change, risks, benefits realization)

### Week 2: Requirements & Data

**Step 5: Create Requirements**

```bash
/arckit.requirements
```

**Expected outputs**:
- Business requirements (BR-xxx): Cost reduction, departmental isolation, AI governance
- Functional requirements (FR-xxx): Summarization, drafting, Q&A, multi-tenancy, SSO, RBAC, audit logging
- Non-functional requirements:
  - Security (NFR-S-xxx): Encryption, MFA, Cyber Essentials Plus, penetration testing
  - Performance (NFR-P-xxx): < 2s p95, 10K users, 99.9% uptime
  - Compliance (NFR-C-xxx): GDPR, AI Playbook, ATRS, TCoP, DPIA
  - Accessibility (NFR-A-xxx): WCAG 2.1 AA, GDS Design System
- Integration requirements (INT-xxx): Government Gateway SSO, Azure AD, SharePoint
- Data requirements (DR-xxx): User profiles, conversation history, documents, audit logs, PII

**Step 6: Create Data Model**

```bash
/arckit.data-model
```

**Expected outputs**:
- ERD with entities (User, Tenant, Conversation, Message, Document, AuditLog)
- Entity catalog with PII flags
- Data governance matrix (owners from stakeholder RACI)
- CRUD matrix (component access patterns)
- Data integration mapping
- DR-xxx requirement traceability

### Week 3: UK Government Compliance

**Step 7: TCoP Assessment**

```bash
/arckit.tcop
```

**Expected assessment**: 13 points, target score > 100/130 (77%)

**Step 8: AI Playbook Assessment**

```bash
/arckit.ai-playbook
```

**Expected assessment**: HIGH-RISK, 10 principles + 6 themes, target score > 144/160 (90%)

**Step 9: ATRS Record**

```bash
/arckit.atrs
```

**Expected outputs**: Tier 1 (public summary) + Tier 2 (technical details), ready for GOV.UK publication

### Week 4: Design & Traceability

**Step 10: Create High-Level Design** (manual or vendor)

**Step 11: Review HLD**

```bash
/arckit.hld-review
```

**Step 12: Create Detailed Design** (after HLD)

**Step 13: Review DLD**

```bash
/arckit.dld-review
```

**Step 14: Create Traceability Matrix**

```bash
/arckit.traceability
```

### Week 5: Re-run Governance Analysis

**Step 15: Re-run Analysis**

```bash
/arckit.analyze
```

**Expected results**:
- Overall Status: ✅ Ready to Proceed
- Governance Health Score: 85-95% (Grade A/B)
- Critical Issues: 0
- High Priority Issues: < 5
- Requirements Coverage: > 90%
- UK Gov Compliance: > 90%

---

## Appendix: Analysis Methodology

**Artifacts Analyzed**:
- `projects/001-cabinet-office-genai/README.md` (project overview)

**Artifacts Missing** (will analyze when created):
- `.arckit/memory/architecture-principles.md`
- `stakeholder-drivers.md`
- `risk-register.md`
- `sobc.md`
- `requirements.md`
- `data-model.md`
- `tcop-assessment.md`
- `ai-playbook-assessment.md`
- `atrs-record.md`
- High-Level Design (HLD)
- Detailed Design (DLD)
- `traceability-matrix.md`

**Detection Rules Applied**:
- ✅ Project context analysis (README reviewed)
- ⚠️ Requirements quality checks (skipped - no requirements.md)
- ⚠️ Architecture principles alignment (skipped - no principles defined)
- ⚠️ Traceability checks (skipped - no requirements or designs)
- ⚠️ UK Government compliance (skipped - no assessments)
- ⚠️ Stakeholder traceability (skipped - no stakeholder analysis)
- ⚠️ Risk management (skipped - no risk register)
- ⚠️ Business case alignment (skipped - no SOBC)
- ⚠️ Data model consistency (skipped - no data model)

**Analysis Runtime**: < 1 minute

**Analysis Version**: ArcKit v0.8.2

---

**END OF ANALYSIS REPORT**

---

## Summary

This is a **NEW PROJECT** with only a README. No governance artifacts exist yet, so no analysis could be performed.

**Status**: ⚠️ **FOUNDATION ARTIFACTS REQUIRED**

**Next Steps**:
1. Week 1: Run `/arckit.principles`, `/arckit.stakeholders`, `/arckit.risk`, `/arckit.sobc`
2. Week 2: Run `/arckit.requirements`, `/arckit.data-model`
3. Week 3: Run `/arckit.tcop`, `/arckit.ai-playbook`, `/arckit.atrs`
4. Week 4: Create designs, run `/arckit.hld-review`, `/arckit.dld-review`, `/arckit.traceability`
5. Week 5: Re-run `/arckit.analyze` to verify governance health score > 85%

**Recommendation**: Follow the recommended execution sequence above to establish governance foundation before proceeding to implementation or procurement.

The README provides a good project overview and success criteria. This is a well-scoped project for a **high-risk AI system** requiring **MANDATORY** UK Government compliance (AI Playbook, ATRS, TCoP).

Re-run this analysis after creating foundation artifacts to verify governance health and identify any issues before implementation.
