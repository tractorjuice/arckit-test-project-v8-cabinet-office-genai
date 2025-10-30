---
description: Analyze stakeholder drivers, goals, and measurable outcomes
---

You are helping an enterprise architect or project manager understand stakeholder drivers, how they manifest into goals, and what measurable outcomes will satisfy each stakeholder.

## User Input

```text
$ARGUMENTS
```

## Instructions

1. **Create or find the project**:
   - Run `.arckit/scripts/bash/create-project.sh --name "$PROJECT_NAME" --json` to create project structure
   - Parse the JSON output to get the project directory path
   - Or if the user specifies an existing project number (e.g., "001"), use that directory

2. **Read the template**: Read `.arckit/templates/stakeholder-drivers-template.md` to understand the comprehensive structure

3. **Check for existing context**:
   - If `.arckit/memory/architecture-principles.md` exists, read it to understand organizational context
   - If `projects/{project}/requirements.md` exists, read it to understand stakeholder mentions
   - Use this context to make the analysis more realistic and aligned

4. **Analyze and generate stakeholder drivers analysis** based on user input:

   **Phase 1: Identify Stakeholders**
   - List all relevant internal stakeholders (executives, business units, technical teams, operations, compliance, security, finance)
   - List external stakeholders (regulators, customers, vendors, partners)
   - Create a Power-Interest grid showing who needs what level of engagement

   **Phase 2: Understand Drivers**
   For each key stakeholder, identify:
   - **STRATEGIC drivers**: Competitive advantage, market position, innovation
   - **OPERATIONAL drivers**: Efficiency, quality, speed, reliability
   - **FINANCIAL drivers**: Cost reduction, revenue growth, ROI
   - **COMPLIANCE drivers**: Regulatory requirements, audit findings, risk mitigation
   - **PERSONAL drivers**: Career advancement, workload reduction, reputation
   - **RISK drivers**: Avoiding penalties, preventing failures, reducing exposure
   - **CUSTOMER drivers**: Satisfaction, retention, acquisition

   For each driver, document:
   - Clear driver statement (what motivates them)
   - Context & background (why this exists)
   - Intensity (CRITICAL | HIGH | MEDIUM | LOW)
   - Enablers (what would help)
   - Blockers (what would hinder)

   **Phase 3: Map Drivers to Goals**
   - Convert each driver into specific, measurable SMART goals
   - Show which drivers feed into which goals (one goal may satisfy multiple drivers)
   - Define success metrics, baselines, targets, and measurement methods
   - Identify dependencies and risks to goal achievement

   Example: Driver "Reduce operational costs" → Goal "Reduce invoice processing time from 7 days to 2 days by Q2 2026"

   **Phase 4: Map Goals to Outcomes**
   - Define measurable business outcomes that prove goals are achieved
   - Specify KPIs, current values, target values, measurement frequency
   - Quantify business value (financial, strategic, operational, customer impact)
   - Define timeline with phase targets
   - Identify leading indicators (early signals) and lagging indicators (final proof)

   Example: Goal "Reduce processing time" → Outcome "30% operational efficiency increase measured by transactions per FTE"

   **Phase 5: Traceability Matrix**
   - Create complete Stakeholder → Driver → Goal → Outcome traceability table
   - Identify conflicts (competing drivers between stakeholders)
   - Identify synergies (drivers that align across stakeholders)
   - Propose resolution strategies for conflicts

   **Phase 6: Engagement Plan**
   - Create stakeholder-specific messaging addressing their drivers
   - Define communication frequency and channels
   - Assess change impact and resistance risk
   - Identify champions, fence-sitters, and resisters

   **Phase 7: Governance**
   - Define RACI matrix for key decisions
   - Document escalation path
   - Create risk register for stakeholder-related risks

5. **Make it actionable and realistic**:
   - Use real-world metrics and timeframes
   - Be specific about measurement methods
   - Acknowledge conflicts honestly
   - Provide practical resolution strategies
   - Include both quantitative and qualitative measures
   - Consider UK Government context if applicable (Minister accountability, public scrutiny, parliamentary questions, transparency requirements)

6. **Write the output**:
   - Write to `projects/{project-dir}/stakeholder-drivers.md`
   - Use the exact template structure
   - Fill in ALL sections with realistic, thoughtful analysis
   - DO NOT leave sections as TBD unless genuinely unknown

7. **Summarize what you created**:
   - How many stakeholders analyzed
   - How many drivers identified
   - How many goals defined
   - How many outcomes mapped
   - Key conflicts or risks
   - Critical success factors
   - Suggested next steps: "Now run `/arckit.requirements` to create requirements that align with and address these stakeholder goals and drivers"

## Example Usage

**Example 1**: New project
```
/arckit.stakeholders Analyze stakeholders for a cloud migration project where the CFO wants cost savings, the CTO wants innovation, Operations is worried about downtime, and Security needs enhanced controls
```

You should:
- Create project "cloud-migration" (gets number 001)
- Identify stakeholders: CFO, CTO, Operations Director, CISO, App Owners, End Users
- Document drivers:
  - CFO: Reduce datacenter costs by £2M annually (FINANCIAL)
  - CTO: Modernize tech stack to attract talent (STRATEGIC)
  - Operations: Minimize downtime risk during migration (RISK)
  - CISO: Improve security posture and compliance (COMPLIANCE)
- Map to goals:
  - G-1: Reduce infrastructure costs 40% by end of Year 1
  - G-2: Migrate 80% of workloads to cloud in 18 months
  - G-3: Zero unplanned downtime during migration
  - G-4: Achieve ISO 27001 certification
- Map to outcomes:
  - O-1: £2M annual cost savings (CFO satisfied)
  - O-2: 50% faster time-to-market for new features (CTO satisfied)
  - O-3: 99.95% uptime maintained (Operations satisfied)
  - O-4: Zero security incidents during migration (CISO satisfied)
- Identify conflict: CFO wants speed (cost savings start sooner) vs Operations wants slow careful migration (minimize risk)
- Resolution strategy: Phased approach - start with low-risk apps for quick wins, save critical apps for later when team has experience
- Write to `projects/001-cloud-migration/stakeholder-drivers.md`

**Example 2**: UK Government AI project
```
/arckit.stakeholders Analyze stakeholders for a DWP benefits chatbot where the Minister wants quick delivery, Civil Service wants due diligence, Citizens need accuracy, and ICO requires data protection
```

You should identify UK Government specific drivers:
- Minister: Deliver manifesto commitment, respond to parliamentary questions (POLITICAL)
- Permanent Secretary: Ensure proper governance, avoid NAO criticism (RISK/ACCOUNTABILITY)
- Service Delivery: Reduce call center volume, improve citizen experience (OPERATIONAL)
- Digital/Technology: Modern architecture, attract digital talent (STRATEGIC)
- Citizens: Fast accurate answers, accessible service (USER)
- ICO: Data protection compliance, transparency (REGULATORY)
- Treasury: Value for money, spending controls (FINANCIAL)

Include UK-specific outcomes like:
- Ministerial dashboard metrics for parliamentary questions
- NAO audit readiness
- GDS service assessment pass rate
- Technology Code of Practice compliance
- User satisfaction on GOV.UK

## Important Notes

- **Drivers are the WHY**: Don't just list what stakeholders want - dig into WHY they want it (career, pressure from boss, regulatory deadline, competitive threat)
- **Goals are the WHAT**: Specific, measurable targets that address the drivers
- **Outcomes are the PROOF**: Business metrics that prove goals were achieved and drivers satisfied
- **Traceability matters**: Every outcome should trace back through goals to specific stakeholder drivers
- **Conflicts are normal**: Don't hide them - document honestly and propose resolutions
- **Be realistic**: Use actual timeframes, real budget numbers, achievable metrics
- **Stakeholders are people**: They have careers, fears, ambitions - not just "business needs"
- **Update regularly**: This is a living document - stakeholders' drivers evolve as context changes

## Success Criteria

A good stakeholder drivers analysis will:
- ✅ Identify all stakeholders with power or interest (don't miss hidden influencers)
- ✅ Dig into underlying motivations (not surface-level wants)
- ✅ Show clear Driver → Goal → Outcome traceability chains
- ✅ Quantify everything possible (metrics, timelines, costs)
- ✅ Acknowledge conflicts honestly and propose pragmatic resolutions
- ✅ Identify synergies that create stakeholder alignment
- ✅ Provide actionable communication and engagement strategies
- ✅ Include governance and decision rights
- ✅ Set up measurable success criteria that stakeholders care about

This document becomes the foundation for:
- Requirements prioritization (align to high-impact drivers)
- Design decisions (optimize for stakeholder outcomes)
- Communication plans (message to each stakeholder's drivers)
- Change management (address resistance rooted in threatened drivers)
- Success metrics (measure what stakeholders actually care about)
- Governance (give decision rights to stakeholders with most at stake)
