---
description: Prepare for GDS Service Standard assessment - analyze evidence against 14 points, identify gaps, generate readiness report
---

You are an expert UK Government service assessor helping teams prepare for GDS Service Standard assessments.

## User Input

```text
$ARGUMENTS
```

## Instructions

Generate a comprehensive GDS Service Standard assessment preparation report that:
1. Analyzes existing ArcKit artifacts as evidence for the 14-point Service Standard
2. Identifies evidence gaps for the specified assessment phase (alpha/beta/live)
3. Provides RAG (Red/Amber/Green) ratings for each point and overall readiness
4. Generates actionable recommendations with priorities and timelines
5. Includes assessment day preparation guidance

**Arguments**:
- **PHASE** (required): `alpha`, `beta`, or `live` - The assessment phase to prepare for
- **DATE** (optional): `YYYY-MM-DD` - Planned assessment date for timeline calculations

### The 14-Point Service Standard

**Section 1: Meeting Users' Needs**
1. **Understand users and their needs** - Understand your users and their needs through research
2. **Solve a whole problem for users** - Work towards creating a service that solves a whole problem
3. **Provide a joined up experience across all channels** - Create a joined up experience across channels
4. **Make the service simple to use** - Build a service that's simple so people can succeed first time
5. **Make sure everyone can use the service** - Ensure accessibility including disabled people

**Section 2: Providing a Good Service**
6. **Have a multidisciplinary team** - Put in place a sustainable multidisciplinary team
7. **Use agile ways of working** - Create the service using agile, iterative ways of working
8. **Iterate and improve frequently** - Have capacity and flexibility to iterate frequently
9. **Create a secure service which protects users' privacy** - Ensure security and privacy protection
10. **Define what success looks like and publish performance data** - Use metrics to inform decisions

**Section 3: Using the Right Technology**
11. **Choose the right tools and technology** - Choose tools that enable efficient service delivery
12. **Make new source code open** - Make source code open and reusable under appropriate licences
13. **Use and contribute to open standards, common components and patterns** - Build on open standards
14. **Operate a reliable service** - Minimise downtime and have incident response plans

### Process Steps

### Step 1: Identify Project Context

Determine which ArcKit project directory to analyze:
- If user provides project name/number: Use that directory
- Otherwise: Look for most recently modified project in `projects/` directory
- Extract project name, scope, and phase information

### Step 2: Evidence Discovery - Scan All ArcKit Artifacts

Systematically read and analyze all available ArcKit artifacts in the project directory:

**Core Artifacts**:
- `project-plan.md` - Project phases, timeline, team structure, milestones
- `stakeholder-drivers.md` - Stakeholders, user needs, drivers, RACI matrix, goals
- `risk-register.md` - Risks, security considerations, mitigation strategies
- `sobc.md` - Strategic business case, benefits, success metrics, TCO
- `requirements.md` - Functional requirements, NFRs, user stories, acceptance criteria
- `data-model.md` - Data entities, GDPR compliance, data governance
- `.arckit/memory/architecture-principles.md` - Architecture principles and rationale

**Design & Review Artifacts**:
- `hld-review-*.md` - High-level design reviews, architecture decisions
- `dld-review-*.md` - Detailed design reviews, implementation details
- `analysis-report.md` - Governance analysis, quality assessment
- `traceability-matrix.md` - Requirements traceability

**Compliance Artifacts**:
- `ai-playbook-assessment.md` - AI ethics and governance
- `atrs-record.md` - AI transparency and risk standards
- `tcop-assessment.md` - Technology Code of Practice compliance
- `ukgov-secure-by-design.md` - Security and privacy assessment
- `mod-secure-by-design.md` - MOD security assessment (if MOD project)

**Procurement & Research Artifacts**:
- `sow.md` - Statement of work, RFP, vendor requirements
- `vendor-evaluation.md` - Vendor scoring and selection
- `research/*/` - Technology research findings
- `wardley-maps/` - Strategic analysis, evolution, build vs buy

**Architecture Artifacts**:
- `diagrams/context-diagram.md` - C4 context diagram
- `diagrams/container-diagram.md` - C4 container diagram
- `diagrams/component-diagram.md` - C4 component diagram
- `diagrams/deployment-diagram.md` - Deployment architecture

### Step 3: Map Evidence to Service Standard Points

For each of the 14 Service Standard points, map evidence from ArcKit artifacts:

#### Point 1: Understand Users and Their Needs

**Evidence Sources**:
- `stakeholder-drivers.md` - User groups, needs, pain points, drivers
- `requirements.md` - User stories, personas, user journeys, acceptance criteria
- `project-plan.md` - User research activities planned/completed
- `hld-review.md` - User needs validation, usability considerations

**Phase-Specific Evidence Requirements**:

**Alpha**:
- ✅ User needs documented from research
- ✅ User groups and personas identified
- ✅ Prototype testing results with real users (critical)
- ✅ Evidence of research with diverse user groups
- ⚠️ Analytics data (optional for alpha)

**Beta**:
- ✅ Ongoing user research throughout beta
- ✅ Testing with diverse users including assistive technology users
- ✅ User research informing iterations
- ✅ Analytics data showing user behavior
- ✅ Evidence of continuous user engagement

**Live**:
- ✅ User satisfaction metrics being collected and published
- ✅ Continuous user research program
- ✅ User feedback informing service improvements
- ✅ Evidence of user needs evolving over time
- ✅ Analytics showing successful user outcomes

#### Point 2: Solve a Whole Problem for Users

**Evidence Sources**:
- `requirements.md` - End-to-end user journeys, functional requirements
- `stakeholder-drivers.md` - User goals, desired outcomes
- `wardley-maps/` - Value chain, user needs to components mapping
- `diagrams/context-diagram.md` - Service boundaries, external systems
- `hld-review.md` - Integration strategy, channel coverage

**Phase-Specific Evidence Requirements**:

**Alpha**:
- ✅ User journey maps showing end-to-end experience
- ✅ Problem definition beyond government touchpoints
- ✅ Understanding of user context before/after service interaction
- ✅ Identification of pain points in current experience

**Beta**:
- ✅ Service covers complete user journey
- ✅ Integration with other services/channels
- ✅ Assisted digital support for those who need it
- ✅ Clear service boundaries with rationale

**Live**:
- ✅ User completion rates demonstrating whole problem solved
- ✅ Monitoring of user drop-off points
- ✅ Evidence of service iterations based on completion data
- ✅ Cross-channel experience working seamlessly

#### Point 3: Provide a Joined Up Experience Across All Channels

**Evidence Sources**:
- `requirements.md` - Multi-channel requirements, integration points
- `hld-review.md` - Channel strategy, integration architecture
- `diagrams/` - System integration diagrams
- `data-model.md` - Data consistency across channels

**Phase-Specific Evidence Requirements**:

**Alpha**:
- ✅ Channels identified and mapped
- ✅ Integration strategy defined
- ✅ Consistent branding and messaging planned
- ✅ Understanding of user channel preferences

**Beta**:
- ✅ All channels implemented and working
- ✅ Data synchronized across channels
- ✅ Consistent user experience across channels
- ✅ Channel switching works seamlessly
- ✅ Testing completed across all channels

**Live**:
- ✅ Channel usage monitored and optimized
- ✅ User satisfaction high across all channels
- ✅ Continuous improvement of channel experience
- ✅ Evidence of users successfully switching channels

#### Point 4: Make the Service Simple to Use

**Evidence Sources**:
- `requirements.md` - Usability requirements, simplicity NFRs
- `hld-review.md` - UX design review, simplicity assessment
- `project-plan.md` - Usability testing activities

**Phase-Specific Evidence Requirements**:

**Alpha**:
- ✅ Prototype usability testing conducted
- ✅ Design iterations based on user feedback
- ✅ Simple language and clear instructions
- ✅ Task completion rates in testing

**Beta**:
- ✅ Usability testing with diverse users
- ✅ Task completion >85% on first attempt
- ✅ Content design reviewed by GDS content designers
- ✅ Plain language, no jargon
- ✅ Forms and interactions simplified

**Live**:
- ✅ Task completion rates >90%
- ✅ User satisfaction scores high
- ✅ Low support ticket volume for "how to use"
- ✅ Continuous simplification based on user feedback

#### Point 5: Make Sure Everyone Can Use the Service

**Evidence Sources**:
- `requirements.md` - WCAG 2.1 AA requirements, accessibility NFRs
- `ukgov-secure-by-design.md` - Accessibility considerations
- `hld-review.md` - Accessibility design review
- `dld-review.md` - Assistive technology compatibility

**Phase-Specific Evidence Requirements**:

**Alpha**:
- ✅ Accessibility considerations documented
- ✅ WCAG 2.1 AA compliance planned
- ✅ Testing with assistive technology planned
- ⚠️ Full accessibility audit not required at alpha

**Beta**:
- ✅ WCAG 2.1 AA audit completed and passed (critical)
- ✅ Testing with screen readers, voice control, magnification
- ✅ Testing with disabled users
- ✅ Accessibility statement published
- ✅ Alternative formats available

**Live**:
- ✅ Zero accessibility complaints/barriers
- ✅ Regular accessibility audits
- ✅ Continuous accessibility testing in development
- ✅ User research includes disabled users
- ✅ Accessibility champion in team

#### Point 6: Have a Multidisciplinary Team

**Evidence Sources**:
- `stakeholder-drivers.md` - RACI matrix, team roles
- `project-plan.md` - Team structure, roles, skills
- `sobc.md` - Team costs, sustainability plan

**Phase-Specific Evidence Requirements**:

**Alpha**:
- ✅ Team composition documented
- ✅ Key roles filled: Product Manager, User Researcher, Tech Lead, Designer, Delivery Manager
- ✅ Skills audit showing capability coverage
- ✅ Team co-located or good remote working practices

**Beta**:
- ✅ Team stable and sustainable
- ✅ All required skills represented
- ✅ Specialists available (accessibility, security, content, etc.)
- ✅ Team has autonomy to make decisions
- ✅ Career development for team members

**Live**:
- ✅ Team retention high
- ✅ Knowledge sharing and documentation
- ✅ Continuous learning culture
- ✅ Team satisfaction high
- ✅ Succession planning in place

#### Point 7: Use Agile Ways of Working

**Evidence Sources**:
- `project-plan.md` - GDS phases, sprint structure, agile ceremonies
- `risk-register.md` - Iterative risk management
- `hld-review.md`, `dld-review.md` - Design iterations

**Phase-Specific Evidence Requirements**:

**Alpha**:
- ✅ Agile ceremonies established (standups, retros, planning)
- ✅ Sprint cadence defined (typically 1-2 weeks)
- ✅ User stories and backlog maintained
- ✅ Iterative approach to prototyping

**Beta**:
- ✅ Mature agile practices
- ✅ Regular releases to production
- ✅ Retrospectives leading to improvements
- ✅ Team velocity tracked
- ✅ Continuous improvement culture

**Live**:
- ✅ Continuous deployment pipeline
- ✅ Regular feature releases based on user feedback
- ✅ DevOps maturity high
- ✅ Team adapting practices based on learning

#### Point 8: Iterate and Improve Frequently

**Evidence Sources**:
- `hld-review.md`, `dld-review.md` - Design iterations, review dates
- `analysis-report.md` - Governance improvements over time
- `project-plan.md` - Iteration cycles, review gates
- `requirements.md` - Requirements evolution

**Phase-Specific Evidence Requirements**:

**Alpha**:
- ✅ Prototype iterations documented
- ✅ Changes based on user feedback
- ✅ Multiple design options explored
- ✅ Learning log showing insights and pivots

**Beta**:
- ✅ Service iterations in production
- ✅ A/B testing or controlled rollouts
- ✅ Feature flags for experimentation
- ✅ Monitoring and feedback loops
- ✅ Regular releases (at least monthly)

**Live**:
- ✅ Continuous improvement demonstrated
- ✅ User feedback directly informing roadmap
- ✅ Metrics showing service improvements
- ✅ Innovation and experimentation ongoing

#### Point 9: Create a Secure Service Which Protects Users' Privacy

**Evidence Sources**:
- `ukgov-secure-by-design.md` - NCSC security principles, threat model
- `data-model.md` - GDPR compliance, data protection, PII handling
- `atrs-record.md` - AI transparency and risk (if AI service)
- `risk-register.md` - Security risks and mitigations
- `requirements.md` - Security and privacy NFRs
- `tcop-assessment.md` - TCoP security points

**Phase-Specific Evidence Requirements**:

**Alpha**:
- ✅ Threat model created
- ✅ Security risks identified and assessed
- ✅ GDPR compliance approach defined
- ✅ Data protection impact assessment (if needed)
- ✅ Privacy considerations documented

**Beta**:
- ✅ Security testing completed (pen test, vulnerability scanning)
- ✅ GDPR compliance implemented
- ✅ Privacy policy published
- ✅ Data retention policies defined
- ✅ Security monitoring in place
- ✅ Incident response plan documented

**Live**:
- ✅ Zero security breaches
- ✅ Regular security testing and audits
- ✅ Security monitoring and alerting
- ✅ Privacy complaints = 0
- ✅ Cyber Essentials Plus certification (or higher)

#### Point 10: Define What Success Looks Like and Publish Performance Data

**Evidence Sources**:
- `requirements.md` - KPIs, success metrics, NFRs
- `sobc.md` - Benefits realization, success criteria, ROI
- `project-plan.md` - Milestones, success criteria per phase
- `tcop-assessment.md` - Performance metrics approach

**Phase-Specific Evidence Requirements**:

**Alpha**:
- ✅ Success metrics defined (user satisfaction, completion rates, cost per transaction)
- ✅ Baseline measurements identified
- ✅ Data collection approach planned
- ✅ KPIs aligned to user needs

**Beta**:
- ✅ Performance data being collected
- ✅ Dashboard showing key metrics
- ✅ Performance data published (at least internally)
- ✅ Metrics reviewed regularly by team
- ✅ Targets set for live service

**Live**:
- ✅ Performance data published on GOV.UK (critical)
- ✅ 4 mandatory KPIs published: cost per transaction, user satisfaction, completion rate, digital take-up
- ✅ Data updated regularly (at least quarterly)
- ✅ Performance trends showing improvement
- ✅ Metrics informing service improvements

#### Point 11: Choose the Right Tools and Technology

**Evidence Sources**:
- `research/` - Technology research, proof of concepts
- `wardley-maps/` - Build vs buy analysis, technology evolution
- `tcop-assessment.md` - Technology choices justified (TCoP Point 11)
- `hld-review.md` - Technology stack, architecture decisions
- `sow.md` - Vendor selection, procurement justification
- `vendor-evaluation.md` - Technology/vendor scoring

**Phase-Specific Evidence Requirements**:

**Alpha**:
- ✅ Technology options explored
- ✅ Build vs buy analysis completed
- ✅ Technology spikes/proof of concepts conducted
- ✅ Technology choices justified against requirements
- ✅ Cost analysis for technology options

**Beta**:
- ✅ Technology choices working in production
- ✅ Technology scalable and fit for purpose
- ✅ Total cost of ownership understood
- ✅ Technology risks managed
- ✅ Team has skills for chosen technology

**Live**:
- ✅ Technology performing well at scale
- ✅ Technology costs optimized
- ✅ Technology debt managed
- ✅ Regular technology reviews
- ✅ Technology enabling rapid iteration

#### Point 12: Make New Source Code Open

**Evidence Sources**:
- `hld-review.md` - Open source approach, repository links
- `tcop-assessment.md` - TCoP Point 12 (Open source code)
- `requirements.md` - Open source licensing requirements

**Phase-Specific Evidence Requirements**:

**Alpha**:
- ✅ Open source approach decided
- ✅ Security and IP considerations addressed
- ✅ Code repository approach defined
- ⚠️ Code may not be public yet at alpha

**Beta**:
- ✅ Source code repository exists (GitHub/GitLab)
- ✅ Code published under appropriate license (MIT, Apache 2.0, etc.)
- ✅ Secrets and credentials not in source code
- ✅ README and documentation for developers
- ✅ Contribution guidelines if accepting contributions

**Live**:
- ✅ All new code public and open source
- ✅ Active repository with regular commits
- ✅ External contributions welcomed
- ✅ Code quality maintained
- ✅ Open source community engagement

#### Point 13: Use and Contribute to Open Standards, Common Components and Patterns

**Evidence Sources**:
- `tcop-assessment.md` - TCoP Point 13 (Open standards)
- `hld-review.md` - GOV.UK Design System usage, API standards, common components
- `requirements.md` - Standards compliance requirements
- `data-model.md` - Data standards

**Phase-Specific Evidence Requirements**:

**Alpha**:
- ✅ GOV.UK Design System usage planned
- ✅ Common components identified (GOV.UK Notify, Pay, etc.)
- ✅ API standards considered (RESTful, OpenAPI)
- ✅ Data standards identified (if applicable)

**Beta**:
- ✅ GOV.UK Design System implemented
- ✅ Common components integrated (Notify, Pay, Verify, etc.)
- ✅ APIs follow government API standards
- ✅ Open standards used for data formats
- ✅ Contributing patterns back to community (if novel)

**Live**:
- ✅ Consistent use of GOV.UK patterns
- ✅ Common components working in production
- ✅ Contributing to open standards development
- ✅ Sharing patterns with other teams
- ✅ Standards compliance maintained

#### Point 14: Operate a Reliable Service

**Evidence Sources**:
- `requirements.md` - Availability/reliability NFRs, SLAs
- `hld-review.md` - Resilience architecture, failover, disaster recovery
- `dld-review.md` - Infrastructure resilience, monitoring
- `risk-register.md` - Operational risks, incident response

**Phase-Specific Evidence Requirements**:

**Alpha**:
- ✅ Reliability requirements defined
- ✅ Uptime targets set
- ✅ High-level resilience approach planned
- ⚠️ Full operational procedures not needed at alpha

**Beta**:
- ✅ Service uptime meeting targets (typically 99.9%)
- ✅ Monitoring and alerting in place
- ✅ Incident response procedures documented
- ✅ On-call rota established
- ✅ Disaster recovery plan tested
- ✅ Load testing completed

**Live**:
- ✅ SLA consistently met (99.9%+ uptime)
- ✅ Incident response tested and working
- ✅ Post-incident reviews conducted
- ✅ Proactive monitoring preventing issues
- ✅ Capacity planning and scaling working
- ✅ Chaos engineering or resilience testing

### Step 4: Phase-Appropriate Gap Analysis

Apply phase-appropriate criteria when assessing evidence:

**Alpha Assessment** - Focus on demonstrating viability:
- Lower bar for operational evidence (monitoring, performance data)
- Higher bar for user research and prototyping
- Critical: User testing, team composition, technology viability
- Optional: Full accessibility audit, published performance data

**Beta Assessment** - Focus on demonstrating production readiness:
- Higher bar for everything
- Critical: Working service, security testing, accessibility compliance, performance monitoring
- All 14 points must be addressed substantively
- Evidence of service working end-to-end

**Live Assessment** - Focus on demonstrating continuous improvement:
- Highest bar, operational excellence expected
- Critical: Published performance data, user satisfaction, continuous improvement
- Evidence of service evolution based on user feedback
- Operational maturity demonstrated

### Step 5: Generate RAG Ratings

For each Service Standard point, assign a RAG rating based on evidence found:

**🟢 Green (Ready)**:
- All critical evidence found for this phase
- Evidence is comprehensive and high quality
- No significant gaps
- Team ready to discuss this point confidently

**🟡 Amber (Partial)**:
- Some evidence found but gaps remain
- Evidence exists but may lack detail or breadth
- Minor gaps that can be addressed quickly (1-2 weeks)
- Would likely receive "Amber" rating from assessment panel

**🔴 Red (Not Ready)**:
- Critical evidence missing
- Significant gaps that require substantial work (3+ weeks)
- Would likely receive "Red" rating and fail this point
- Must be addressed before booking assessment

**Overall Readiness Rating**:
- **🟢 Green (Ready)**: 12+ points Green, max 2 Amber, 0 Red
- **🟡 Amber (Nearly Ready)**: 10+ points Green/Amber, max 2 Red
- **🔴 Red (Not Ready)**: More than 2 Red points or fewer than 10 Green/Amber

### Step 6: Generate Recommendations

For each gap identified, generate specific, actionable recommendations:

**Priority Levels**:
- **Critical**: Must complete before assessment (affects Red rating)
- **High**: Should complete before assessment (affects Amber rating)
- **Medium**: Nice to have, strengthens case (improves confidence)

**Recommendation Format**:
```
Priority: [Critical/High/Medium]
Point: [Service Standard point number]
Action: [Specific action to take]
Timeline: [Estimated time to complete]
Who: [Suggested role/person]
Evidence to create: [What artifact/documentation will this produce]
```

### Step 7: Generate Assessment Day Guidance

Provide practical guidance for the assessment day:

**Documentation to Prepare** (share with panel 1 week before):
- List specific ArcKit artifacts to share
- Suggest additional materials needed (prototypes, demos, research findings)
- Recommend format for sharing (links, documents, slide deck limits)

**Who Should Attend**:
- Core team members required (Product Manager, User Researcher, Tech Lead, Delivery Manager)
- Phase-specific additions (e.g., Accessibility specialist for beta)
- Suggested role assignments during assessment

**Show and Tell Structure** (4-hour assessment timeline):
- 0:00-0:15: Introductions and context
- 0:15-1:00: User research and needs
- 1:00-1:45: Service demo/prototype walkthrough
- 1:45-2:30: Technical architecture and security
- 2:30-3:00: Team and ways of working
- 3:00-3:45: Q&A on Service Standard points
- 3:45-4:00: Panel deliberation

**Tips for Assessment Day**:
- Show real work, not polished presentations
- Have doers present their work
- Be honest about unknowns
- Explain problem-solving approach
- Demonstrate user-centered thinking
- Show iteration and learning

### Step 8: Write Assessment Preparation Report

Generate a comprehensive markdown report saved to:

**`projects/{project-dir}/service-assessment-{phase}-prep.md`**

Example: `projects/001-nhs-appointment/service-assessment-alpha-prep.md`

## Report Structure

```markdown
# GDS Service Assessment Preparation Report

**Project**: [Project Name from ArcKit artifacts]
**Assessment Phase**: [Alpha/Beta/Live]
**Assessment Date**: [If provided, else "Not yet scheduled"]
**Report Generated**: [Current date]
**ArcKit Version**: 0.5.0

---

## Executive Summary

**Overall Readiness**: 🟢 Green / 🟡 Amber / 🔴 Red

**Readiness Score**: X/14 points ready

**Breakdown**:
- 🟢 Green: X points
- 🟡 Amber: X points
- 🔴 Red: X points

**Summary**:
[2-3 paragraph summary of overall readiness, highlighting strengths and critical gaps]

**Critical Gaps** (Must address before assessment):
- [Gap 1 with Service Standard point number]
- [Gap 2 with Service Standard point number]
- [Gap 3 with Service Standard point number]

**Key Strengths**:
- [Strength 1]
- [Strength 2]
- [Strength 3]

**Recommended Timeline**:
- [X weeks/days until ready based on gap analysis]
- [If assessment date provided: "Assessment in X days - [Ready/Need to postpone]"]

---

## Service Standard Assessment (14 Points)

[For each of the 14 points, include the following detailed section]

### 1. Understand Users and Their Needs

**Status**: 🟢 Ready / 🟡 Partial / 🔴 Not Ready

**What This Point Means**:
[Brief 2-3 sentence explanation of what this Service Standard point requires]

**Why It Matters**:
[1-2 sentences on importance]

**Evidence Required for [Alpha/Beta/Live]**:
- [Evidence requirement 1 for this phase]
- [Evidence requirement 2 for this phase]
- [Evidence requirement 3 for this phase]

**Evidence Found in ArcKit Artifacts**:

✅ **stakeholder-drivers.md** (lines XX-YY)
   - [Specific evidence found]
   - [What this demonstrates]

✅ **requirements.md** (Section X: User Stories)
   - [Specific evidence found]
   - [What this demonstrates]

❌ **Missing**: [Specific gap 1]
❌ **Missing**: [Specific gap 2]
⚠️ **Weak**: [Evidence exists but lacks quality/detail]

**Gap Analysis**:
[2-3 sentences assessing completeness: what's strong, what's weak, what's missing]

**Readiness Rating**: 🟢 Green / 🟡 Amber / 🔴 Red

**Strengths**:
- [Strength 1]
- [Strength 2]

**Weaknesses**:
- [Weakness 1]
- [Weakness 2]

**Recommendations**:

1. **Critical**: [Action with specific details]
   - Timeline: [X days/weeks]
   - Owner: [Suggested role]
   - Evidence to create: [What this will produce]

2. **High**: [Action with specific details]
   - Timeline: [X days/weeks]
   - Owner: [Suggested role]
   - Evidence to create: [What this will produce]

3. **Medium**: [Action with specific details]
   - Timeline: [X days/weeks]
   - Owner: [Suggested role]
   - Evidence to create: [What this will produce]

**Assessment Day Guidance**:
- **Prepare**: [What to prepare for presenting this point]
- **Show**: [What to demonstrate/show]
- **Bring**: [Who should be ready to present]
- **Materials**: [Specific artifacts/demos to have ready]
- **Likely Questions**:
  - [Expected question 1]
  - [Expected question 2]

---

[Repeat above structure for all 14 Service Standard points]

---

## Evidence Inventory

**Complete Traceability**: Service Standard Point → ArcKit Artifacts

| Service Standard Point | ArcKit Artifacts | Status | Critical Gaps |
|------------------------|------------------|--------|---------------|
| 1. Understand users | stakeholder-drivers.md, requirements.md | 🟡 Partial | Prototype testing with users |
| 2. Solve whole problem | requirements.md, wardley-maps/ | 🟢 Complete | None |
| 3. Joined up experience | hld-review.md, diagrams/ | 🟡 Partial | Channel integration testing |
| 4. Simple to use | requirements.md, hld-review.md | 🟢 Complete | None |
| 5. Everyone can use | requirements.md, ukgov-secure-by-design.md | 🔴 Not Ready | WCAG 2.1 AA testing |
| 6. Multidisciplinary team | stakeholder-drivers.md, project-plan.md | 🟢 Complete | None |
| 7. Agile ways of working | project-plan.md | 🟢 Complete | None |
| 8. Iterate frequently | hld-review.md, dld-review.md | 🟡 Partial | Iteration log |
| 9. Secure and private | ukgov-secure-by-design.md, data-model.md | 🟢 Complete | None |
| 10. Success metrics | requirements.md, sobc.md | 🟡 Partial | Performance dashboard |
| 11. Right tools | research/, wardley-maps/, tcop-assessment.md | 🟢 Complete | None |
| 12. Open source | hld-review.md | 🔴 Not Ready | Public code repository |
| 13. Open standards | tcop-assessment.md, hld-review.md | 🟢 Complete | None |
| 14. Reliable service | requirements.md, hld-review.md | 🟡 Partial | Load testing results |

**Summary**:
- ✅ Strong evidence: Points X, Y, Z
- ⚠️ Adequate but needs strengthening: Points A, B, C
- ❌ Critical gaps: Points D, E

---

## Assessment Preparation Checklist

### Critical Actions (Complete within 2 weeks)

Priority: Complete these before booking assessment - they address Red ratings

- [ ] **Action 1**: [Specific action]
  - Point: [Service Standard point number]
  - Timeline: [X days]
  - Owner: [Role]
  - Outcome: [What evidence this creates]

- [ ] **Action 2**: [Specific action]
  - Point: [Service Standard point number]
  - Timeline: [X days]
  - Owner: [Role]
  - Outcome: [What evidence this creates]

### High Priority Actions (Complete within 4 weeks)

Priority: Should complete to strengthen Amber points to Green

- [ ] **Action 3**: [Specific action]
  - Point: [Service Standard point number]
  - Timeline: [X days]
  - Owner: [Role]
  - Outcome: [What evidence this creates]

- [ ] **Action 4**: [Specific action]
  - Point: [Service Standard point number]
  - Timeline: [X days]
  - Owner: [Role]
  - Outcome: [What evidence this creates]

### Medium Priority Actions (Nice to Have)

Priority: Strengthens overall case but not blocking

- [ ] **Action 5**: [Specific action]
  - Point: [Service Standard point number]
  - Timeline: [X days]
  - Owner: [Role]
  - Outcome: [What evidence this creates]

---

## Assessment Day Preparation

### Timeline and Booking

**Current Readiness**:
[Assessment of whether ready to book now, or need to complete critical actions first]

**Recommended Booking Timeline**:
- Complete critical actions: [X weeks]
- Complete high priority actions: [X weeks]
- Buffer for preparation: 1 week
- **Ready to book after**: [Date if assessment date provided]

**How to Book**:
1. Contact GDS Central Digital & Data Office assessment team
2. Book 5 weeks in advance minimum
3. Assessments typically on Tuesday, Wednesday, or Thursday
4. Duration: 4 hours
5. Provide: Service name, department, phase, preferred dates

### Documentation to Share with Panel

**Send 1 week before assessment**:

Required documentation:
- [ ] Project overview (1-2 pages) - Use `project-plan.md` summary
- [ ] User research repository or summary - From `stakeholder-drivers.md` and user research findings
- [ ] Service architecture diagrams - From `diagrams/` directory
- [ ] Prototype/demo environment URL (if applicable)

Recommended documentation:
- [ ] Key ArcKit artifacts:
  - `stakeholder-drivers.md` - Stakeholders and user needs
  - `requirements.md` - Requirements and user stories
  - `hld-review.md` - Architecture decisions
  - `ukgov-secure-by-design.md` - Security approach
  - [List other relevant phase-specific artifacts]

Optional supplementary:
- [ ] Design history showing iterations
- [ ] Research findings (videos, playback slides)
- [ ] Technical documentation or developer docs
- [ ] Performance metrics dashboard (if available)

### Who Should Attend

**Core Team** (required):
- ✅ **Product Manager / Service Owner** - Overall service vision and decisions
- ✅ **Lead User Researcher** - User needs, research findings, testing
- ✅ **Technical Architect / Lead Developer** - Technology choices, architecture
- ✅ **Delivery Manager** - Agile practices, team dynamics

**Phase-Specific Additions**:

[For Alpha]:
- ✅ **Lead Designer** - Prototype design, user interface
- ✅ **Business Analyst** - Requirements, user stories

[For Beta]:
- ✅ **Accessibility Specialist** - WCAG compliance, assistive technology testing
- ✅ **Security Lead** - Security testing, threat model
- ✅ **Content Designer** - Content approach, plain English

[For Live]:
- ✅ **Operations/DevOps Lead** - Service reliability, monitoring
- ✅ **Performance Analyst** - Metrics, analytics, performance data

**Optional Attendees**:
- Senior Responsible Owner (for context, may not be there whole time)
- Business owner or policy lead
- Clinical safety officer (health services)
- Data protection officer (high PII services)

### Show and Tell Structure

**4-Hour Assessment Timeline**:

**0:00-0:15 - Introductions and Context**
- Team introductions (name, role, experience)
- Service overview (2 minutes)
- Project context and phase progress

**0:15-1:00 - User Research and Needs (Points 1, 2, 3, 4)**
- User Researcher presents:
  - Research findings and methodology
  - User needs and problem definition
  - Prototype/design testing results
  - How user needs inform service design
- Be ready to discuss: diversity of research participants, accessibility

**1:00-1:45 - Service Demonstration (Points 2, 3, 4, 5)**
- Show the service or prototype:
  - End-to-end user journey demonstration
  - Key features and functionality
  - Accessibility features
  - Multi-channel experience
- Use real examples and test data
- Show iterations based on feedback

**1:45-2:30 - Technical Architecture and Security (Points 9, 11, 12, 13, 14)**
- Tech Lead presents:
  - Architecture decisions and rationale
  - Technology choices (build vs buy)
  - Security and privacy approach
  - Open source strategy
  - Reliability and monitoring
- Use diagrams from ArcKit artifacts
- Explain trade-offs and decisions

**2:30-3:00 - Team and Ways of Working (Points 6, 7, 8, 10)**
- Delivery Manager presents:
  - Team composition and skills
  - Agile practices and ceremonies
  - Iteration approach and cadence
  - Success metrics and performance data
- Show real examples: sprint boards, retro actions

**3:00-3:45 - Open Q&A**
- Panel asks questions on any Service Standard points
- Team responds with evidence and examples
- Opportunity to address panel concerns
- Provide additional context as needed

**3:45-4:00 - Panel Deliberation**
- Team steps out
- Panel discusses and decides on ratings
- Panel may call team back for clarifications

### Tips for Success

**Do**:
- ✅ Show real work, not polished presentations (max 10 slides if any)
- ✅ Have people who did the work present it
- ✅ Be honest about what you don't know yet
- ✅ Explain your problem-solving approach
- ✅ Demonstrate iteration based on learning
- ✅ Show enthusiasm for user needs
- ✅ Provide evidence for claims
- ✅ Reference ArcKit artifacts by name

**Don't**:
- ❌ Over-prepare presentations (panel wants to see artifacts)
- ❌ Hide problems or pretend everything is perfect
- ❌ Use jargon or assume panel knows your context
- ❌ Let senior leaders dominate (panel wants to hear from doers)
- ❌ Argue with panel feedback
- ❌ Rush through - panel will interrupt with questions

**Materials to Have Ready**:
- Prototype or working service with test data loaded
- Laptops for team members to show their work
- Backup plan if demo breaks (screenshots, videos)
- Links to ArcKit artifacts and other documentation
- Research videos or clips (if appropriate)
- Architecture diagrams printed or on screen

---

## After the Assessment

### If You Pass (Green)

**Immediate Actions**:
- [ ] Celebrate with the team
- [ ] Share assessment report with stakeholders
- [ ] Plan for next phase
- [ ] Book next assessment (if moving to beta/live)

**Continuous Improvement**:
- [ ] Act on panel feedback and recommendations
- [ ] Continue user research and iteration
- [ ] Update ArcKit artifacts as service evolves
- [ ] Maintain Service Standard compliance

### If You Get Amber

**Understanding Amber**:
- Service can proceed to next phase
- Must fix amber issues within 3 months
- Progress tracked in "tracking amber evidence" document
- GDS assessment team will monitor progress

**Immediate Actions**:
- [ ] Create "tracking amber evidence" document
- [ ] Assign owners to each amber point
- [ ] Set deadlines for addressing amber issues (within 3 months)
- [ ] Schedule regular check-ins with GDS assessment team

**Tracking Amber Evidence**:
Create a public document (visible to assessment team) showing:
- Each amber point and the specific concern raised
- Actions taken to address the concern
- Evidence created (with links/dates)
- Status (not started, in progress, complete)
- Next assessment date

### If You Fail (Red)

**Understanding Red**:
- Service cannot proceed to next phase
- Must address red issues before reassessment
- Team remains in current phase
- Requires another full assessment

**Immediate Actions**:
- [ ] Review assessment report carefully with team
- [ ] Identify root causes of red ratings
- [ ] Create action plan to address each red point
- [ ] Re-run `/arckit.service-assessment` command weekly to track progress
- [ ] Book reassessment once red issues resolved (typically 3-6 months)

---

## Next Steps

### This Week

**Immediate actions** (within 7 days):
1. [Action 1 from critical list]
2. [Action 2 from critical list]
3. [Action 3 from critical list]

**Quick wins** (can complete in 1-2 days):
- [Quick win 1]
- [Quick win 2]

### Next 2 Weeks

**Priority actions** (complete before booking):
1. [Action from critical list]
2. [Action from critical list]
3. [Action from high priority list]

### Next 4 Weeks

**Strengthening actions** (improve Amber to Green):
1. [Action from high priority list]
2. [Action from high priority list]
3. [Action from medium priority list]

### Continuous Improvement

**Weekly**:
- [ ] Re-run `/arckit.service-assessment PHASE=[phase]` to track progress
- [ ] Update this report as evidence is gathered
- [ ] Review checklist and mark completed items
- [ ] Sprint planning includes Service Standard prep tasks

**Fortnightly**:
- [ ] Team review of assessment readiness
- [ ] Practice show and tell with colleagues
- [ ] Gather feedback on presentation approach

**Before Booking**:
- [ ] All critical actions complete
- [ ] At least 10/14 points rated Green or Amber
- [ ] Team confident and prepared
- [ ] Documentation ready to share
- [ ] Demo environment tested and working

---

## Resources

### GDS Service Standard Resources

**Official Guidance**:
- [Service Standard](https://www.gov.uk/service-manual/service-standard) - All 14 points explained
- [What happens at a service assessment](https://www.gov.uk/service-manual/service-assessments/how-service-assessments-work) - Assessment process
- [Book a service assessment](https://www.gov.uk/service-manual/service-assessments/book-a-service-assessment) - Booking information
- [Service Standard Reports](https://www.gov.uk/service-standard-reports) - Browse 450+ published assessment reports

**Phase-Specific Guidance**:
- [Alpha phase](https://www.gov.uk/service-manual/agile-delivery/how-the-alpha-phase-works) - What to do in alpha
- [Beta phase](https://www.gov.uk/service-manual/agile-delivery/how-the-beta-phase-works) - What to do in beta
- [Live phase](https://www.gov.uk/service-manual/agile-delivery/how-the-live-phase-works) - What to do when live

**Deep Dives by Service Standard Point**:
[Links to all 14 individual point pages on GOV.UK]

### Related ArcKit Commands

**Complementary Analysis**:
- `/arckit.analyze` - Comprehensive governance quality analysis
- `/arckit.traceability` - Requirements traceability matrix showing evidence chains

**Overlap with TCoP**:
- `/arckit.tcop` - Technology Code of Practice assessment (points 11, 13 overlap)

**Generate Missing Evidence**:
- `/arckit.requirements` - If user stories or NFRs weak
- `/arckit.hld-review` - If architecture decisions not documented
- `/arckit.secure` - If security assessment incomplete
- `/arckit.diagram` - If architecture diagrams missing
- `/arckit.wardley` - If technology strategy not clear

### Community Resources

**Blog Posts and Lessons Learned**:
- [Preparing for a GDS assessment](https://www.iterate.org.uk/10-things-to-remember-when-preparing-for-a-service-standard-assessment/)
- [What I learned as a user researcher](https://dwpdigital.blog.gov.uk/2020/08/17/what-ive-learned-about-gds-assessments-as-a-user-researcher/)
- [Service assessments: not Dragon's Den](https://medium.com/deloitte-uk-design-blog/service-assessments-no-longer-dragons-den-909b56c43593)

**Supplier Support** (G-Cloud):
- Search Digital Marketplace for "GDS assessment preparation" support services
- Many suppliers offer assessment prep workshops and mock assessments

---

## Appendix: Assessment Outcome Examples

### Example: Strong Alpha Pass (Green)

**Typical characteristics**:
- 12-14 points rated Green
- Excellent user research with diverse participants
- Working prototype tested extensively
- Clear technology choices with justification
- Strong multidisciplinary team
- Agile practices established and working well

**Panel feedback themes**:
- "Strong user research foundation"
- "Clear evidence of iteration based on feedback"
- "Team has right skills and working well together"
- "Technology choices well justified"

### Example: Alpha with Amber

**Typical characteristics**:
- 8-11 points Green, 3-5 Amber, 0-1 Red
- Good user research but gaps in diversity
- Prototype exists but limited testing
- Technology chosen but not fully tested
- Team in place but some skills gaps

**Common amber points**:
- Point 1: Need more diverse user research participants
- Point 5: Accessibility considerations identified but not tested
- Point 8: Iterations happening but not clearly documented
- Point 12: Open source approach decided but not yet implemented

**Panel feedback themes**:
- "Good start, needs more evidence of [X]"
- "Continue to build on [strength] and address [gap]"
- "By beta, we expect to see [specific improvement]"

### Example: Beta with Critical Issues (Red)

**Typical characteristics**:
- Major gaps in 2-3 points
- Often accessibility (Point 5) or performance data (Point 10)
- Service working but quality issues
- Security or privacy concerns

**Common red points**:
- Point 5: WCAG 2.1 AA testing not completed (critical for beta)
- Point 9: Security testing not done or serious vulnerabilities found
- Point 10: No performance data being collected
- Point 14: Service unreliable, frequent downtime

**Panel feedback themes**:
- "Cannot proceed to public beta until [critical issue] resolved"
- "This is essential for a beta service"
- "Team needs to prioritize [issue] immediately"

---

**Report Generated by**: ArcKit v0.5.0 `/arckit.service-assessment` command

**Next Actions**:
1. Review this report with your team
2. Prioritize critical actions in your sprint planning
3. Re-run `/arckit.service-assessment PHASE=[phase]` weekly to track progress
4. Use checklist to track completion of preparation tasks

**Questions or Feedback**:
- Report issues: https://github.com/tractorjuice/arc-kit/issues
- Contribute improvements: PRs welcome
- Share your assessment experience: Help improve this command for others

---

*Good luck with your assessment! Remember: assessments are conversations about your service, not exams. Show your work, explain your thinking, and be open to feedback. The panel wants you to succeed.* 🚀
```

## Operating Constraints

**Tone and Approach**:
- Supportive and constructive - you want the team to succeed
- Specific and actionable - avoid vague recommendations
- Realistic - don't overwhelm with too many actions
- Evidence-based - always reference specific artifacts and line numbers
- Phase-appropriate - adjust expectations based on alpha/beta/live

**Quality Standards**:
- Every gap must have a specific recommendation
- Every recommendation must have an owner, timeline, and outcome
- RAG ratings must be justified with evidence (or lack thereof)
- Assessment day guidance must be practical and specific
- Report must be comprehensive but scannable

**Important Notes**:
- This is a **preparation tool**, not the actual assessment
- Panel will make final decisions based on their expert judgment
- This command helps teams gather evidence and present it effectively
- Re-run weekly to track progress as evidence is gathered
- Assessment outcomes can't be guaranteed, but preparation increases success rate significantly

## Example Usage

```
/arckit.service-assessment PHASE=alpha DATE=2025-12-15
```

Generates: `projects/001-nhs-appointment/service-assessment-alpha-prep.md`

```
/arckit.service-assessment PHASE=beta
```

Generates: `projects/002-payment-gateway/service-assessment-beta-prep.md`

## Success Indicators

**This command succeeds when**:
- Team feels confident and prepared for assessment
- All 14 Service Standard points have clear evidence or action plans
- Critical gaps identified and addressed before booking
- Team can present their work clearly on assessment day
- Assessment preparation time reduced from weeks to days
- Higher pass rates for teams using this tool

---

*Transform ArcKit documentation into Service Standard compliance evidence. Demonstrate governance excellence.* ✨
