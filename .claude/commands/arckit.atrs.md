---
description: Generate Algorithmic Transparency Recording Standard (ATRS) record for AI/algorithmic tools
---

You are helping a UK government organization create an Algorithmic Transparency Recording Standard (ATRS) record for an AI or algorithmic tool.

## User Input

```text
$ARGUMENTS
```

## Instructions

1. **Understand ATRS requirements**:
   - ATRS is **MANDATORY** for all central government departments and arm's length bodies
   - Two-tier structure: Tier 1 (public summary) + Tier 2 (detailed technical)
   - Published records on GOV.UK repository
   - Must be clear, accurate, and comprehensive

2. **Identify the algorithmic tool**:
   - Tool name and purpose
   - Type of algorithm (rule-based, ML, generative AI, etc.)
   - Government function (benefits, healthcare, policing, etc.)
   - Current phase (pre-deployment, beta, production, retired)
   - Users (staff and/or citizens)

3. **Determine risk level** (similar to AI Playbook):
   - **HIGH-RISK**: Automated decisions affecting rights, benefits, legal status, healthcare
   - **MEDIUM-RISK**: Semi-automated with human review, significant resource allocation
   - **LOW-RISK**: Administrative, productivity tools, recommendations with human control

4. **Read relevant project documents**:
   - Read `.arckit/memory/architecture-principles.md` (if exists)
   - Read `projects/{project-dir}/requirements.md` (if exists)
   - Read `projects/{project-dir}/ai-playbook-assessment.md` (if exists - for AI systems)
   - Read `.arckit/templates/uk-gov-atrs-template.md` for structure

5. **Complete TIER 1 - Summary Information** (for general public):
   - Use clear, simple, jargon-free language
   - Explain what the tool does in plain English
   - Include basic contact information
   - Make it accessible to non-technical readers

**Key Tier 1 Fields**:
- **Name**: Tool identifier
- **Description**: 1-2 sentence plain English summary
- **Website URL**: Link to more information
- **Contact Email**: Public contact
- **Organization**: Department/agency name
- **Function**: Area (benefits, healthcare, policing, etc.)
- **Phase**: Pre-deployment/Beta/Production/Retired
- **Geographic Region**: England/Scotland/Wales/NI/UK-wide

6. **Complete TIER 2 - Detailed Information** (for specialists):

### Section 1: Owner and Responsibility
- Organization and team
- Senior Responsible Owner (name, role, accountability)
- External suppliers (names, Companies House numbers, roles)
- Procurement procedure type (G-Cloud, DOS, open tender, etc.)
- Data access terms for suppliers

### Section 2: Description and Rationale
- Detailed technical description
- Algorithm type (rule-based, ML, generative AI, etc.)
- AI model details (if applicable): provider, version, fine-tuning
- Scope and boundaries (intended use and out-of-scope)
- Benefits and impact metrics
- Previous process (how it was done before)
- Alternatives considered (and why rejected)

### Section 3: Decision-Making Process
- Process integration (role in workflow)
- Provided information (outputs and format)
- Frequency and scale of usage
- **Human decisions and review**:
  - Human-in-the-loop (review every decision)
  - Human-on-the-loop (periodic review)
  - Human-in-command (can override)
  - Fully automated (must justify)
- Required training for staff
- Appeals and contestability (how users can contest decisions)

### Section 4: Data
- Data sources (types, origins, fields used)
- Personal data and special category data
- Data sharing arrangements
- Data quality and maintenance
- Data storage location and security (UK/EU/USA, cloud provider)
- Encryption, access controls, audit logging
- Cyber Essentials / ISO 27001 certification

### Section 5: Impact Assessments
- **DPIA (Data Protection Impact Assessment)**: Status, date, outcome, risks
- **EqIA (Equality Impact Assessment)**: Protected characteristics, impacts, mitigations
- **Human Rights Assessment**: ECHR articles, safeguards
- **Other assessments**: Environmental, accessibility, security

### Section 6: Fairness, Bias, and Discrimination
- Bias testing completed (methodology, date)
- Fairness metrics (demographic parity, equalized odds, etc.)
- Results by protected characteristic (gender, ethnicity, age, disability)
- Known limitations and biases
- Training data bias review
- Ongoing bias monitoring (frequency, metrics, alert thresholds)

### Section 7: Technical Details
- Model performance metrics (accuracy, precision, recall, F1)
- Performance by demographic group
- Model explainability approach (SHAP, LIME, etc.)
- Model versioning and change management
- Model monitoring and drift detection
- Retraining schedule

### Section 8: Testing and Assurance
- Testing approach (unit, integration, UAT, A/B, red teaming)
- Edge cases and failure modes
- Fallback procedures
- Security testing (pen testing, AI-specific threats):
  - Prompt injection (for LLMs)
  - Data poisoning
  - Model inversion
  - Adversarial attacks
- Independent assurance and external audit

### Section 9: Transparency and Explainability
- Public disclosure (website, GOV.UK, model card, open source)
- User communication (how users are informed)
- Information provided to users (that algorithm is used, how it works, how to contest)
- Model card published

### Section 10: Governance and Oversight
- Governance structure (board/committee composition, responsibilities)
- Risk register and top risks
- Incident management (response plan, process, contact)
- Audit trail (logging, retention, review)

### Section 11: Compliance
- Legal basis (primary legislation, regulatory compliance)
- Data protection (controller, DPO, ICO registration, legal basis)
- Standards compliance (TCoP, GDS Service Standard, Data Ethics Framework, ISO)
- Procurement compliance (route, value, IR35)

### Section 12: Performance and Outcomes
- Success metrics and KPIs
- Benefits realized (with evidence)
- User feedback and satisfaction
- Continuous improvement log

### Section 13: Review and Updates
- Review schedule (frequency, next review date)
- Triggers for unscheduled review
- Version history
- Contact for updates

7. **Provide risk-appropriate guidance**:

**For HIGH-RISK algorithmic tools** (affecting rights, benefits, healthcare):
- **CRITICAL**: DPIA is MANDATORY before deployment
- **CRITICAL**: EqIA is MANDATORY
- Human-in-the-loop STRONGLY RECOMMENDED
- Bias testing across ALL protected characteristics REQUIRED
- ATRS publication on GOV.UK MANDATORY
- Quarterly reviews RECOMMENDED
- Independent audit STRONGLY RECOMMENDED

**For MEDIUM-RISK tools**:
- DPIA likely required
- EqIA recommended
- Human oversight required (human-on-the-loop minimum)
- Bias testing recommended
- ATRS publication MANDATORY
- Annual reviews

**For LOW-RISK tools**:
- DPIA assessment (may determine not required)
- Basic fairness checks
- Human oversight recommended
- ATRS publication MANDATORY
- Periodic reviews

8. **Link to existing ArcKit artifacts**:
   - Map to requirements from `requirements.md`
   - Reference AI Playbook assessment (if exists)
   - Reference TCoP assessment (if exists)
   - Reference design reviews (HLD/DLD)

9. **Flag missing mandatory items**:

**BLOCKERS** (must complete before publication):
- [ ] DPIA completed (for high-risk)
- [ ] EqIA completed (for high-risk)
- [ ] Senior Responsible Owner identified
- [ ] Human oversight model defined
- [ ] Bias testing completed (for ML/AI)
- [ ] Public-facing description written
- [ ] Contact details provided

**WARNINGS** (should complete):
- [ ] Alternatives considered documented
- [ ] Training program defined
- [ ] Incident response plan
- [ ] Review schedule set

10. **Generate comprehensive ATRS record**:

Output location: `projects/{project-dir}/atrs-record.md`

Use the template structure from `uk-gov-atrs-template.md`

**Format**:
- Tier 1: Clear, simple, jargon-free language
- Tier 2: Technical detail sufficient for specialists
- All mandatory fields completed
- Links to supporting documentation
- Publication checklist at end

11. **Provide publication guidance**:

After generating the ATRS record:
- Summary of completeness (what percentage of fields are complete)
- List of blocking issues (must resolve before publication)
- List of warnings (should address)
- Next steps:
  1. Complete missing mandatory fields
  2. Get SRO approval
  3. Legal/compliance review
  4. DPO review
  5. Publish on GOV.UK ATRS repository
  6. Publish on department website
  7. Set review date

## Example Usage

User: `/arckit.atrs Generate ATRS record for our benefits eligibility chatbot using GPT-4`

You should:
- Identify tool: Benefits eligibility chatbot, Generative AI (LLM)
- Determine risk: **HIGH-RISK** (affects access to benefits - fundamental right)
- Read existing requirements, AI Playbook assessment (if exists)
- Complete Tier 1 (public summary):
  - Name: DWP Benefits Eligibility Chatbot
  - Description: "An AI-powered chatbot that helps people understand their eligibility for benefits by answering questions about their circumstances in plain English."
  - Function: Benefits and welfare
  - Phase: Private Beta
  - Region: England and Wales
- Complete Tier 2 (detailed):
  - Section 1: DWP Digital, Benefits Policy Team, SRO: [Senior Responsible Owner] (Director)
  - External Supplier: OpenAI (GPT-4), Companies House: 12345678
  - Section 2: Generative AI (LLM), GPT-4, fine-tuned on benefits policy
  - Section 3: Human-in-the-loop (all advice reviewed before shown to users)
  - Section 4: Personal data (income, household composition), UK data residency, AWS
  - Section 5: DPIA completed, EqIA completed, Human Rights assessed
  - Section 6: Bias testing across gender, ethnicity, age, disability - results documented
  - Section 7: Accuracy 85%, explanation provided using prompt engineering
  - Section 8: Red teaming for prompt injection, content filtering
  - Section 9: Published on GOV.UK, users informed in-app
  - Section 10: AI Governance Board oversight, monthly reviews
  - Section 11: UK GDPR, Data Protection Act 2018, Public Task legal basis
  - Section 12: KPI: User satisfaction 78%, reduced call center volume 15%
  - Section 13: Quarterly review, next review 2025-07-01
- Flag completeness: 95% complete
- **BLOCKING**: Need to add fallback procedure for system failures
- **WARNING**: Model card not yet published (recommended)
- Write to `projects/NNN-benefits-chatbot/atrs-record.md`
- Provide next steps: "Complete fallback procedures, then ready for SRO approval and GOV.UK publication"

## Important Notes

- ATRS publication is **MANDATORY** for central government
- Records must be published on GOV.UK ATRS repository: https://www.gov.uk/algorithmic-transparency-records
- ATRS is PUBLIC - do not include sensitive information (security vulnerabilities, personal data, commercially sensitive details)
- Use plain English in Tier 1 - imagine explaining to a family member
- Tier 2 should be detailed enough for technical scrutiny
- Update ATRS record when significant changes occur (new version, scope change, incidents)
- Regular reviews required (annually minimum, quarterly for high-risk)
- Contact algorithmic-transparency@dsit.gov.uk for guidance

## Related Frameworks

- **AI Playbook** - responsible AI deployment (use `/arckit.ai-playbook` first for AI systems)
- **Technology Code of Practice** - broader technology governance (use `/arckit.tcop`)
- **Data Ethics Framework** - responsible data use
- **GDS Service Standard** - service design and delivery

## Resources

- ATRS Guidance: https://www.gov.uk/government/publications/guidance-for-organisations-using-the-algorithmic-transparency-recording-standard
- ATRS Template: https://www.gov.uk/government/publications/algorithmic-transparency-template
- ATRS Repository: https://www.gov.uk/algorithmic-transparency-records
- Contact: algorithmic-transparency@dsit.gov.uk
