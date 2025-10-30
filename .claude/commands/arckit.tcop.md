---
description: Generate a Technology Code of Practice (TCoP) review document for a UK Government technology project
tags: [governance, compliance, uk-government, tcop, digital-spend-control]
---

# Technology Code of Practice Review

You are helping to conduct a **Technology Code of Practice (TCoP) review** for a UK Government technology project or programme.

## Context

The Technology Code of Practice is a set of 13 criteria to help government design, build and buy technology. It's used by the Digital Spend Control team to assess technology spending proposals.

**TCoP Reference**: https://www.gov.uk/guidance/the-technology-code-of-practice

## Your Task

Generate a comprehensive TCoP review document by:

1. **Loading the template**: Use the TCoP review template from `.specify/templates/tcop-review-template.md`

2. **Understanding the project**: Based on the user's description and any existing project documentation (specs, architecture, requirements), assess compliance against all 13 TCoP points:
   - Point 1: Define user needs
   - Point 2: Make things accessible and inclusive
   - Point 3: Be open and use open source
   - Point 4: Make use of open standards
   - Point 5: Use cloud first
   - Point 6: Make things secure
   - Point 7: Make privacy integral
   - Point 8: Share, reuse and collaborate
   - Point 9: Integrate and adapt technology
   - Point 10: Make better use of data
   - Point 11: Define your purchasing strategy
   - Point 12: Make your technology sustainable
   - Point 13: Meet the Service Standard

3. **For each TCoP point**:
   - Assess status: ✅ Compliant / ⚠️ Partially Compliant / ❌ Non-Compliant / N/A Not Applicable
   - Provide evidence of how the project meets (or fails to meet) the criteria
   - Check relevant checklist items based on project information
   - Identify gaps and required actions

4. **Check for existing documentation**:
   - Look for requirements documents in `specs/*/requirements.md`
   - Look for architecture documents in `specs/*/diagrams/`
   - Look for any existing compliance documents
   - Use information from these documents to inform your assessment

5. **Provide realistic assessments**:
   - Be honest about compliance gaps
   - Mark items as "Partially Compliant" if only some aspects are met
   - Use "N/A" only when truly not applicable
   - Provide actionable recommendations for gaps

6. **Generate compliance scorecard**: Create a summary showing status of all 13 points

7. **Prioritize actions**: Identify critical issues requiring immediate attention

8. **Save the document**: Write to `specs/[project-folder]/tcop-review.md`

## Output Format

The document must include:
- Executive summary with overall compliance status
- Detailed assessment for each of the 13 TCoP points
- Evidence and checklist items for each point
- Gaps and required actions
- Overall compliance scorecard (X/13 compliant)
- Critical issues list
- Prioritized recommendations (High/Medium/Low)
- Next steps with timeline
- Approval section

## Assessment Guidelines

**When assessing compliance**:

- **✅ Compliant**: Clear evidence exists, all key criteria met, no significant gaps
- **⚠️ Partially Compliant**: Some aspects addressed but significant gaps remain, or evidence is incomplete
- **❌ Non-Compliant**: Criteria not met, no evidence of compliance, or critical gaps exist
- **N/A**: Point is genuinely not applicable (e.g., Point 13 if not building a public service)

**Common critical issues**:
- No DPIA for projects processing personal data (Point 7)
- No accessibility testing for user-facing services (Point 2)
- No security assessment completed (Point 6)
- Public cloud not considered (Point 5)
- No user research conducted (Point 1)

**Project phases matter**:
- **Discovery/Alpha**: User research, technical spikes, open source exploration expected
- **Beta**: Accessibility testing, security assessments, DPIA should be complete
- **Live**: All 13 points must be fully compliant

## Special Considerations

**For AI/ML systems**: Also consider requirements from the AI Playbook (may need ATRS - Algorithmic Transparency Record)

**For public-facing services**: Point 13 (Service Standard) is mandatory - must pass GDS service assessments

**For Digital Spend Control submissions**: Focus on points most relevant to spending approval:
- Point 5 (Cloud First)
- Point 11 (Purchasing Strategy)
- Point 8 (Reuse and Collaboration)

**Data protection**: If processing personal data, Point 7 is critical - DPIA completion is mandatory before going live

## UK Government Context

Be aware of:
- **Digital Marketplace**: G-Cloud, DOS frameworks for procurement
- **GDS Service Standard**: 14-point standard for public services
- **NCSC guidance**: Cyber security best practices
- **UK GDPR**: Data protection requirements
- **Cyber Essentials**: Baseline security certification
- **Cloud First policy**: Public cloud preferred unless justified otherwise

## Example Output Structure

```markdown
# Technology Code of Practice (TCoP) Review

**Project**: Benefits Eligibility Chatbot
**Overall TCoP Compliance**: Partially Compliant

## TCoP Point 1: Define User Needs
**Status**: ✅ Compliant
**Evidence**: User research completed with 50+ DWP claimants...
[Checked items and gaps listed]

## TCoP Point 6: Make Things Secure
**Status**: ⚠️ Partially Compliant
**Evidence**: Threat model exists, but penetration testing not yet completed...
**Gaps/Actions Required**:
- Schedule pen test before Private Beta (HIGH PRIORITY)
...

## Overall Compliance Summary
**Score**: 9/13 Compliant (3 Partially Compliant, 1 N/A)
**Critical Issues**:
1. DPIA not completed (Point 7) - BLOCKING for Beta
2. Accessibility audit incomplete (Point 2) - Required for Beta
```

## Notes

- Be thorough but practical - this is a governance document, not just a checkbox exercise
- Highlight blockers that prevent progression to next phase
- Reference official GOV.UK guidance URLs for each point
- Consider the project's maturity - don't expect Live compliance in Discovery
- Provide specific, actionable recommendations rather than generic advice

Generate the TCoP review now based on the project information provided.
