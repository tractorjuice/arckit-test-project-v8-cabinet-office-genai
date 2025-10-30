# Cabinet Office GenAI Implementation - ArcKit Example Project

This repository demonstrates how ArcKit was used to plan and govern a **Cabinet Office GenAI cross-government AI platform** for secure, compliant generative AI services across UK Government departments.

## Project Overview

**Cabinet Office GenAI Platform** - A centralized, secure generative AI service providing:
- Cross-government AI capabilities (document summarization, drafting, analysis)
- Multi-tenancy with departmental isolation
- UK Government security classification support (OFFICIAL to OFFICIAL-SENSITIVE)
- Integration with existing government authentication (Government Gateway, Azure AD)
- Compliance with AI Playbook, ATRS, TCoP, and Secure by Design
- Responsible AI governance and bias monitoring
- Data residency (UK-only), GDPR compliance, and transparency

## Scenario Details

**Context**: Cabinet Office is establishing a shared GenAI service to:
1. Reduce duplication across departments (each building own chatbots)
2. Centralize AI governance and compliance
3. Provide cost-effective, secure AI capabilities
4. Ensure consistent standards and responsible AI practices
5. Enable cross-government knowledge sharing while maintaining department boundaries

**Key Challenges**:
- Multi-department security and data isolation
- Compliance with multiple frameworks (AI Playbook, TCoP, ATRS, Secure by Design)
- Integration with legacy government systems
- Responsible AI (bias, transparency, human oversight)
- Cost control and chargeback model

## ArcKit Commands Used

This project demonstrates the following ArcKit workflow:

### Phase 0: Planning
- `/arckit.plan` - Project plan with GDS Agile Delivery phases

### Phase 1: Governance Foundation
- `/arckit.principles` - Architecture principles for cross-government AI
- `/arckit.stakeholders` - Multi-department stakeholder analysis
- `/arckit.risk` - Risk register (Orange Book)

### Phase 2: Business Case
- `/arckit.sobc` - Strategic Outline Business Case (Green Book)

### Phase 3: Requirements & Design
- `/arckit.requirements` - Functional and non-functional requirements
- `/arckit.data-model` - Data model with GDPR compliance
- `/arckit.wardley` - Wardley Map for build vs buy decisions

### Phase 4: Compliance & Security
- `/arckit.ai-playbook` - UK Government AI Playbook assessment
- `/arckit.atrs` - AI Transparency Risk Standards record
- `/arckit.tcop` - Technology Code of Practice assessment
- `/arckit.secure` - UK Government Secure by Design review

### Phase 5: Procurement & Vendor Selection
- `/arckit.gcloud-search` - G-Cloud supplier search
- `/arckit.gcloud-clarify` - Supplier clarification questions
- `/arckit.sow` - Statement of Work / RFP

### Phase 6: Design Reviews & Analysis
- `/arckit.hld-review` - High-Level Design review
- `/arckit.diagram` - C4 architecture diagrams
- `/arckit.analyze` - Comprehensive governance analysis
- `/arckit.traceability` - Requirements traceability matrix

## Project Structure

```
arckit-test-project-v8-cabinet-office-genai/
├── .arckit/                        # ArcKit configuration
│   ├── memory/
│   │   └── architecture-principles.md
│   └── templates/
├── projects/
│   └── 001-cabinet-office-genai/   # Main project directory
│       ├── project-plan.md
│       ├── stakeholder-drivers.md
│       ├── risk-register.md
│       ├── sobc.md
│       ├── requirements.md
│       ├── data-model.md
│       ├── ai-playbook-assessment.md
│       ├── atrs-record.md
│       ├── tcop-assessment.md
│       ├── ukgov-secure-by-design.md
│       ├── sow.md
│       ├── hld-review.md
│       ├── analysis-report.md
│       ├── traceability-matrix.md
│       ├── diagrams/
│       │   ├── context-diagram.md
│       │   ├── container-diagram.md
│       │   └── deployment-diagram.md
│       └── wardley-maps/
│           └── current-state.md
├── .claude/                        # Claude Code commands
├── .codex/                         # Codex CLI commands
└── .gemini/                        # Gemini CLI commands
```

## Key Features Demonstrated

### 1. Multi-Tenant Architecture
- Department-level isolation with Azure AD integration
- Row-level security for data segregation
- Shared infrastructure with departmental customization

### 2. AI Governance
- Responsible AI framework (bias monitoring, explainability, human-in-the-loop)
- AI Transparency Risk Standards (ATRS) compliance
- Central AI governance board with department representatives

### 3. Security & Compliance
- OFFICIAL and OFFICIAL-SENSITIVE data classification
- UK data residency (Azure UK South/West)
- Cyber Essentials Plus certification
- NCSC Cloud Security Principles compliance

### 4. Cross-Government Integration
- Government Gateway authentication
- Azure AD federated identity
- GOV.UK Notify for communications
- GOV.UK Pay for cost recovery

### 5. Responsible AI Practices
- Bias testing and monitoring dashboard
- Human oversight for sensitive decisions
- Transparency logs for all AI interactions
- Regular AI ethics reviews

## UK Government Compliance

This project demonstrates compliance with:
- ✅ **GDS Service Standard** - Discovery, Alpha, Beta, Live phases
- ✅ **Technology Code of Practice** - All 13 points assessed
- ✅ **AI Playbook** - 10 principles + 6 ethical themes
- ✅ **ATRS** - AI Transparency Risk Standards record
- ✅ **UK GDPR** - Data protection and privacy
- ✅ **Secure by Design** - NCSC security principles
- ✅ **Orange Book** - HM Treasury risk management
- ✅ **Green Book** - HM Treasury business case

## Traceability

Complete traceability chain demonstrated:
- **Stakeholders** → Drivers → Goals → Outcomes
- **Risks** → Mitigation → Requirements → Design Controls
- **Requirements** → Design → Tests → Validation
- **Benefits** → Success Metrics → Measurement Plan

## Cost Model

This project includes:
- Total Cost of Ownership (TCO) analysis
- Departmental chargeback model
- Cost comparison vs decentralized approach
- ROI calculation with 3-year projection

## About ArcKit

ArcKit is an open-source enterprise architecture governance toolkit with 25 AI-assisted commands for systematic, compliant project delivery following UK Government standards.

- **GitHub**: https://github.com/tractorjuice/arc-kit
- **Website**: https://tractorjuice.github.io/arc-kit/
- **License**: MIT

## Example Artifacts

Browse the `/projects/001-cabinet-office-genai/` directory to see:
- Stakeholder analysis with cross-government RACI matrix
- Risk register following Orange Book methodology
- Strategic Outline Business Case using Green Book 5-case model
- Requirements with complete traceability
- AI Playbook assessment for high-risk AI system
- ATRS record ready for GOV.UK publication
- Architecture diagrams (C4 model)
- Wardley Maps showing evolution strategy

---

**Note**: This is a demonstration project created with ArcKit to showcase enterprise architecture governance for complex cross-government AI initiatives. All content is AI-generated for educational purposes.
