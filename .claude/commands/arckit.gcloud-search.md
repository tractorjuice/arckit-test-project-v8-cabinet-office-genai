---
description: Find G-Cloud services on UK Digital Marketplace with live search and comparison
---

You are helping an enterprise architect find and compare G-Cloud services on the UK Digital Marketplace.

## User Input

```text
$ARGUMENTS
```

## Context

**G-Cloud** is the UK Digital Marketplace framework for procuring off-the-shelf cloud services:
- Cloud hosting, IaaS, PaaS
- SaaS platforms and tools
- Cloud support services
- No custom development - just service procurement

This command:
1. Analyzes your project requirements to identify cloud service needs
2. Generates G-Cloud procurement requirements
3. **Searches the Digital Marketplace for matching services** (live search)
4. Compares services and provides recommendations

## Instructions

### 1. Prerequisites Check

**IMPORTANT**: Check prerequisites before proceeding:

a. **Project with Requirements** (MUST exist):
   - Check if user specified a project name/number
   - Look for `projects/[project]/requirements.md`
   - If NOT found: ERROR "Run /arckit.requirements first to define project needs"

b. **Architecture Principles** (RECOMMENDED):
   - Check if `.arckit/memory/architecture-principles.md` exists
   - If exists: Read it for cloud strategy, security requirements
   - If NOT found: WARN "Consider running /arckit.principles to define cloud governance"

### 2. Load Project Context

Run `.arckit/scripts/bash/list-projects.sh --json` to get available projects, then:

1. Read `projects/[project]/requirements.md`
2. Read `.arckit/memory/architecture-principles.md` if available
3. Parse user input for specific service types needed

### 3. Analyze Cloud Service Needs

**Scan requirements** to identify what cloud services are needed:

**Look for**:
- INT-xxx mentioning: "cloud hosting", "SaaS", "IaaS", "PaaS", "monitoring", "email service"
- NFR-xxx mentioning: "uptime", "availability", "disaster recovery", "cloud infrastructure"
- FR-xxx mentioning: "platform", "service", "hosting", "managed service"

**Service categories to identify**:
- **Cloud Hosting**: IaaS, VMs, containers, Kubernetes
- **Cloud Software**: SaaS platforms, tools, applications
- **Cloud Support**: Managed services, monitoring, backup
- **Specialized Services**: Email, CDN, databases, analytics

**Determine**:
- Primary service category needed
- Must-have requirements (from MUST priority)
- Desirable requirements (from SHOULD priority)
- Compliance needs (security certifications, data residency)

### 4. Generate G-Cloud Requirements Document

Create directory: `projects/[project]/procurement/`

Generate `projects/[project]/procurement/gcloud-requirements.md`:

```markdown
# UK Digital Marketplace: G-Cloud Service Procurement

**Framework**: G-Cloud
**Service Category**: [Cloud Hosting / Cloud Software / Cloud Support]
**Generated**: [DATE]
**Project**: [PROJECT_NAME]
**Project ID**: [PROJECT_ID]
**Requirements Source**: [Link to requirements.md]

---

## 1. Service Overview

### 1.1 What We Need

[Describe what cloud service/software is needed - from requirements.md]

### 1.2 Why We Need It

[Business context from BR-xxx requirements]

### 1.3 Strategic Alignment

**Architecture Principles** (if exists):
[Reference relevant principles, especially cloud strategy, security principles]

### 1.4 Integration Context

[Extract from INT-xxx requirements - what systems this service will integrate with]

---

## 2. Must-Have Requirements

The service **MUST** provide:

[Extract MUST requirements from requirements.md]

### 2.1 Functional Requirements
- **[Requirement 1]**: [From FR-xxx or NFR-xxx]
- **[Requirement 2]**: [From FR-xxx or NFR-xxx]
- **[Requirement 3]**: [From FR-xxx or NFR-xxx]

### 2.2 Performance Requirements
- **[Performance Target]**: [From NFR-P-xxx with measurable metric]
- **[Performance Target]**: [From NFR-P-xxx with measurable metric]

### 2.3 Security Requirements
- **[Security Requirement]**: [From NFR-S-xxx or architecture-principles.md]
- **[Security Requirement]**: [From NFR-S-xxx or architecture-principles.md]

### 2.4 Compliance Requirements
- **[Compliance Standard]**: [From NFR-C-xxx]
- **[Certification Needed]**: [e.g., ISO 27001, Cyber Essentials Plus]
- **[Data Residency]**: [e.g., UK data centers only, GDPR compliance]

### 2.5 Integration Requirements
- **[Integration Point]**: [From INT-xxx]
- **[Integration Method]**: [API, webhook, file transfer, etc.]

---

## 3. Desirable Requirements

The service **SHOULD** provide:

[Extract SHOULD requirements from requirements.md]
- [Desirable feature 1]
- [Desirable feature 2]
- [Desirable feature 3]

---

## 4. Success Criteria

[Extract measurable success criteria from requirements.md BR-xxx]

- [Criterion 1 with metric]
- [Criterion 2 with metric]
- [Criterion 3 with metric]

---

## 5. Evaluation Criteria

### 5.1 Functional Fit (50%)

- **Must-Have Coverage** (30%): Meets all MUST requirements
- **Desirable Features** (20%): Coverage of SHOULD requirements

### 5.2 Reliability & Performance (25%)

- **Service Level Agreements** (10%): Uptime guarantees, support response times
- **Performance Specifications** (10%): Meets NFR-P-xxx requirements
- **Disaster Recovery** (5%): DR/BC capabilities

### 5.3 Security & Compliance (15%)

- **Security Certifications** (5%): ISO 27001, Cyber Essentials Plus, etc.
- **Data Protection** (5%): GDPR compliance, data residency
- **Compliance Standards** (5%): Industry-specific certifications

### 5.4 Cost & Support (10%)

- **Pricing Model** (5%): Transparency, predictability, value
- **Support Availability** (3%): Support hours, escalation process
- **Contract Flexibility** (2%): Terms, exit strategy, lock-in

```

### 5. Search Digital Marketplace (WebSearch)

**IMPORTANT**: Now perform **live marketplace search** to find actual services.

For each service category identified:

#### 5.1 Build Search Query

Create search query:
```
site:digitalmarketplace.service.gov.uk g-cloud [service category] [key requirements]
```

**Examples**:
- `site:digitalmarketplace.service.gov.uk g-cloud cloud hosting kubernetes`
- `site:digitalmarketplace.service.gov.uk g-cloud monitoring prometheus grafana`
- `site:digitalmarketplace.service.gov.uk g-cloud email delivery service`

**Include in query**:
- Service category name
- Key technical requirements (from MUST requirements)
- Important features (top 2-3 from requirements)

#### 5.2 Execute WebSearch

Use WebSearch tool to search Digital Marketplace.

**For each major service type needed** (up to 3 service types):
1. Execute WebSearch with built query
2. Parse results to extract:
   - Service names
   - Supplier names
   - Service descriptions
   - Links to service pages
   - Pricing information (if mentioned)
   - Key features mentioned

#### 5.3 Parse and Filter Results

For each service found:
- **Check MUST requirements**: Does service mention capabilities for MUST requirements?
- **Score SHOULD requirements**: How many desirable features are mentioned?
- **Check compliance**: Are required certifications mentioned?
- **Extract pricing**: If mentioned in search results
- **Capture link**: Direct URL to service page

#### 5.4 Generate Service Shortlist

**Add to gcloud-requirements.md**:

```markdown

---

## 6. Digital Marketplace Search Results

**Search Performed**: [DATE and TIME]
**Search Queries Used**:
- Query 1: `[search query 1]`
- Query 2: `[search query 2]` (if multiple searches)

### 6.1 Service Category: [Category Name]

#### Top Matching Services

[For each of top 3-5 services found]

**Service: [Service Name]**
- **Supplier**: [Supplier Name]
- **Service ID**: [Service ID from URL if available]
- **Link**: [Direct URL to service page]
- **Key Features**:
  - [Feature 1 mentioned in description]
  - [Feature 2 mentioned in description]
  - [Feature 3 mentioned in description]
- **Pricing**: [If mentioned, otherwise "See service page for pricing"]
- **Must-Have Match**: [X/Y] requirements mentioned
- **Desirable Features**: [X/Y] desirable features mentioned
- **Compliance**: [Certifications mentioned]

---

### 6.2 Service Comparison Table

| Service | Supplier | Must-Have Match | Desirable Features | Compliance | Estimated Cost | Link |
|---------|----------|----------------|-------------------|------------|---------------|------|
| [Service 1] | [Supplier 1] | X/Y | X/Y | [Certs] | [Price] | [Link] |
| [Service 2] | [Supplier 2] | X/Y | X/Y | [Certs] | [Price] | [Link] |
| [Service 3] | [Supplier 3] | X/Y | X/Y | [Certs] | [Price] | [Link] |

---

### 6.3 Detailed Comparison

**[Service 1 Name]**
- ✅ **Strengths**:
  - [Strength 1 based on requirements match]
  - [Strength 2 based on features]
  - [Strength 3 based on compliance/pricing]
- ⚠️ **Gaps/Concerns**:
  - [Gap 1 - MUST requirement not clearly mentioned]
  - [Gap 2 - desirable feature missing]
- **Best For**: [Use case where this service excels]

**[Service 2 Name]**
- ✅ **Strengths**:
  - [Strength 1]
  - [Strength 2]
  - [Strength 3]
- ⚠️ **Gaps/Concerns**:
  - [Gap 1]
  - [Gap 2]
- **Best For**: [Use case where this service excels]

**[Service 3 Name]**
- ✅ **Strengths**:
  - [Strength 1]
  - [Strength 2]
  - [Strength 3]
- ⚠️ **Gaps/Concerns**:
  - [Gap 1]
  - [Gap 2]
- **Best For**: [Use case where this service excels]

---

## 7. Recommendation

### 7.1 Recommended Service

**[Service Name]** by [Supplier Name]

**Rationale**:
- ✅ Meets [X/Y] MUST requirements ([list any gaps if exist])
- ✅ Provides [X/Y] desirable features
- ✅ [Compliance advantage - e.g., strongest security certification coverage]
- ✅ [Cost advantage - e.g., best value for required features]
- ✅ [Other advantage - e.g., UK data residency, 24/7 support]

**Next Steps for This Service**:
1. Visit service page: [Link]
2. Verify all MUST requirements are met (contact supplier if needed)
3. Request detailed pricing quote
4. Schedule demo/technical discussion with supplier
5. Validate integration capabilities (INT-xxx requirements)
6. Check client references

### 7.2 Alternative Option

**[Service Name]** by [Supplier Name]

**Why Consider This**:
[Reason - e.g., "If [condition] is priority" or "If [Recommended Service] doesn't meet [specific need]"]

**Link**: [URL]

---

## 8. Important Gaps to Address

[If any MUST requirements were NOT clearly met by any service]

⚠️ **Requirement Gap**: [MUST requirement ID and description]
- **Finding**: None of the top services clearly mention this capability
- **Action Required**:
  - Contact shortlisted suppliers directly to confirm capability
  - May need to broaden search or adjust requirements
  - Consider hybrid approach (e.g., combine services)

```

### 6. Handle Search Scenarios

**If WebSearch finds 5+ good matches**:
- Show top 5 services in comparison table
- Provide recommendation with clear rationale

**If WebSearch finds 3-4 matches**:
- Show all matches in comparison table
- Highlight which best meets requirements
- May suggest alternative search terms

**If WebSearch finds 1-2 matches**:
- Show what was found
- Suggest broader search terms
- Recommend manual marketplace search with guidance

**If WebSearch finds 0 matches**:
- Explain no results found for this query
- Suggest alternative search terms (broader)
- Provide manual search guidance: go to https://www.digitalmarketplace.service.gov.uk/
- List specific search terms to try manually
- Note: Service may exist but not indexed well - encourage direct marketplace search

### 7. Final Output Section

Add to end of `gcloud-requirements.md`:

```markdown

---

## 9. Next Steps

### 9.1 For Procurement Team

1. **Review Shortlisted Services**:
   - Visit each service page on Digital Marketplace
   - Verify MUST requirements are met (contact suppliers for clarification)

2. **Request Additional Information**:
   - Detailed pricing quotes
   - Technical specifications
   - Integration capabilities
   - Client references

3. **Evaluate Services**:
   - Use criteria from Section 5
   - Document scoring and justification (audit trail)

4. **Technical Validation**:
   - Schedule demos with top 2-3 suppliers
   - Validate integration requirements (INT-xxx)
   - Proof of concept if needed for complex integrations

5. **Award Contract**:
   - Select service via Digital Marketplace
   - Create call-off contract
   - Publish award on Contracts Finder

### 9.2 Due Diligence Checklist

Before committing to a service:

- ✅ **Requirements Validation**: All MUST requirements confirmed with supplier
- ✅ **Pricing Clarity**: Full pricing model understood (no hidden costs)
- ✅ **Contract Terms**: Exit strategy, data export, termination terms reviewed
- ✅ **Integration Testing**: API/integration capabilities validated
- ✅ **Security Review**: Certifications verified, security practices reviewed
- ✅ **Data Protection**: GDPR compliance confirmed, data residency verified
- ✅ **Support Terms**: SLA understood, support hours acceptable
- ✅ **References**: Spoke with at least 2 existing clients

---

## 10. Resources

- **Digital Marketplace**: https://www.digitalmarketplace.service.gov.uk/
- **G-Cloud Buyers Guide**: https://www.gov.uk/guidance/g-cloud-buyers-guide
- **Buying Guide**: https://www.gov.uk/guidance/buying-and-selling-on-the-digital-marketplace
- **Contracts Finder**: https://www.gov.uk/contracts-finder

---

## 11. Service Page Links

[List all direct links to services found]

1. [Service 1 Name] - [Supplier]: [URL]
2. [Service 2 Name] - [Supplier]: [URL]
3. [Service 3 Name] - [Supplier]: [URL]
4. [Service 4 Name] - [Supplier]: [URL]
5. [Service 5 Name] - [Supplier]: [URL]

**Browse More**: https://www.digitalmarketplace.service.gov.uk/g-cloud/search

---

## 12. Important Notes

**Framework Agreements**: G-Cloud services are pre-approved - no separate tender needed

**Call-Off Contracts**: Each service purchase creates a call-off contract under the G-Cloud framework

**Integration Testing**: Ensure service can integrate per INT-xxx requirements before commitment

**Exit Strategy**: Always clarify data export and service termination terms before signing

**Audit Trail**: Document evaluation decisions and justification for chosen service

```

### 8. Quality Validation

Before finalizing, validate output:

- ✅ All requirements from requirements.md are included
- ✅ Architecture principles referenced (if available)
- ✅ WebSearch was executed for each major service type
- ✅ At least 3 services found and compared (or explanation if fewer)
- ✅ Comparison table is complete
- ✅ Recommendation has clear rationale
- ✅ All service links are included
- ✅ Must-have requirements are checked against each service
- ✅ Gaps are identified if services don't meet all requirements
- ✅ Next steps are actionable

### 9. Report Completion

Output to user:

```
✅ Generated G-Cloud service search for [PROJECT_NAME]

Framework: G-Cloud
Document: projects/[project]/procurement/gcloud-requirements.md

Requirements Summary:
- ✅ Requirements extracted from requirements.md
- [✅/⚠️] Architecture principles referenced
- ✅ Service category identified: [Category]

Marketplace Search Results:
- ✅ Executed WebSearch for: [search query 1]
- [✅] Executed WebSearch for: [search query 2] (if multiple)
- ✅ Found [X] matching services
- ✅ Shortlisted top [X] services for comparison

Recommended Service:
🏆 [Service Name] by [Supplier Name]
   - Match Score: [X/Y] MUST + [X/Y] SHOULD requirements
   - Link: [URL]

Alternative Services:
2. [Service Name] by [Supplier] - [URL]
3. [Service Name] by [Supplier] - [URL]

Next Steps:
1. Review document: projects/[project]/procurement/gcloud-requirements.md
2. Visit recommended service page: [Link]
3. Contact supplier for detailed information
4. Validate integration requirements (INT-xxx)
5. Complete due diligence checklist (Section 9.2)
6. Award contract via Digital Marketplace

Important: All shortlisted services should be validated against MUST requirements before selection.
```

## Key Principles

1. **Live Search**: Always use WebSearch to find actual services - don't just generate requirements
2. **Requirements-Driven**: Build search queries from actual project requirements
3. **Comparison Focus**: Provide side-by-side comparison with clear recommendation
4. **Practical Links**: Include direct links to every service mentioned
5. **Gap Identification**: Clearly identify if services don't meet MUST requirements
6. **Actionable Output**: Next steps should be concrete and immediately actionable
7. **Traceability**: Maintain requirement IDs throughout evaluation

## Search Query Examples

**For Cloud Hosting**:
- `site:digitalmarketplace.service.gov.uk g-cloud cloud hosting kubernetes docker`
- `site:digitalmarketplace.service.gov.uk g-cloud iaas virtual machines linux`
- `site:digitalmarketplace.service.gov.uk g-cloud paas cloud platform managed`

**For SaaS Platforms**:
- `site:digitalmarketplace.service.gov.uk g-cloud monitoring observability prometheus`
- `site:digitalmarketplace.service.gov.uk g-cloud email delivery service smtp`
- `site:digitalmarketplace.service.gov.uk g-cloud ci cd pipeline automation`
- `site:digitalmarketplace.service.gov.uk g-cloud analytics data warehouse`

**For Specialized Services**:
- `site:digitalmarketplace.service.gov.uk g-cloud cdn content delivery network`
- `site:digitalmarketplace.service.gov.uk g-cloud backup disaster recovery`
- `site:digitalmarketplace.service.gov.uk g-cloud security scanning vulnerability`

## Error Handling

- **No requirements**: ERROR "Run /arckit.requirements first - need to define service needs"
- **Custom development detected**: ERROR "This is for custom development - use /arckit.dos instead"
- **No service needs found**: WARN "No cloud service requirements found - are you sure this is G-Cloud procurement?"
- **No search results**: Suggest broader search terms, provide manual search guidance
- **Few search results (1-2)**: Show what was found, suggest alternative searches

## G-Cloud vs DOS Guidance

If requirements suggest custom development rather than cloud services:
```
⚠️ FRAMEWORK MISMATCH DETECTED

Your requirements suggest custom development (FR-xxx functional requirements for building features).

G-Cloud is for buying off-the-shelf cloud services, not custom development.

✅ Use /arckit.dos instead - Digital Outcomes and Specialists

DOS is the correct framework for:
- Custom software development
- Building new systems
- Hiring developers/specialists
- Project outcomes that require custom implementation

Only use /arckit.gcloud-search if you need:
- Cloud hosting or infrastructure (IaaS/PaaS)
- Off-the-shelf SaaS platforms
- Managed cloud services
```
