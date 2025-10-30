---
description: Create or update enterprise architecture principles
---

You are helping an enterprise architect define architecture principles that will govern all technology decisions in the organization.

## User Input

```text
$ARGUMENTS
```

## Instructions

1. **Read the template**: Read `.arckit/templates/architecture-principles-template.md` to understand the structure

2. **Understand the request**: The user may be:
   - Creating principles from scratch for a new organization
   - Adding specific principles (e.g., "add API-first principle")
   - Updating existing principles
   - Tailoring principles for a specific industry (e.g., financial services, healthcare, retail)

3. **Generate comprehensive principles**: Based on the user's input, create detailed architecture principles following the template structure:
   - Strategic Principles (Scalability, Resilience, Interoperability, Security by Design, etc.)
   - Data Principles (Single Source of Truth, Data Quality, Privacy by Design)
   - Integration Principles (Loose Coupling, Standard Interfaces, Asynchronous Communication)
   - Quality Attributes (Performance, Availability, Maintainability, Observability)
   - Development Practices (Automation, Testing, Code Review, Continuous Improvement)
   - Exception Process (how to request deviations)

   **IMPORTANT**: Principles MUST be **technology-agnostic**:
   - Focus on CHARACTERISTICS, not specific products (e.g., "horizontally scalable" not "use Kubernetes")
   - Focus on QUALITIES, not specific technologies (e.g., "encrypted in transit" not "use TLS 1.3")
   - Focus on PATTERNS, not specific implementations (e.g., "event-driven integration" not "use Kafka")
   - Focus on OUTCOMES, not specific tools (e.g., "infrastructure as code" not "use Terraform")

   **What TO include**: Architectural qualities, patterns, practices, and decision criteria
   **What NOT to include**: Specific vendors, products, cloud providers, programming languages, frameworks

4. **Make it actionable**: Each principle MUST include:
   - Clear principle statement with MUST/SHOULD/MAY (technology-agnostic)
   - Rationale explaining WHY this principle matters
   - Implications (how it affects design decisions)
   - Validation gates (checklist items to verify compliance)
   - Example scenarios (good vs bad, without naming specific products)
   - Common violations to avoid

5. **Industry-specific customization**: If the user mentions an industry:
   - **Financial Services**: Add principles for transaction integrity, audit trails, regulatory compliance (SOX, PCI-DSS)
   - **Healthcare**: Add HIPAA compliance, PHI data handling, consent management
   - **Retail**: Add principles for payment processing, inventory systems, customer data
   - **Government**: Add accessibility (Section 508), public records, security clearances

6. **Write the output**:
   - If `.arckit/memory/architecture-principles.md` exists, update it
   - If it doesn't exist, create it with comprehensive principles
   - Use the exact template structure
   - Make it ready for immediate use by development teams

7. **Summarize what you created**: After writing, provide a brief summary:
   - How many principles were defined
   - Key areas covered
   - Any industry-specific additions
   - Suggested next steps: "Now run `/arckit.stakeholders` to analyze stakeholder drivers and goals for your project"

## Example Usage

User: `/arckit.principles Create principles for a financial services company focusing on cloud migration`

You should:
- Read the template
- Generate comprehensive principles
- Add financial services specific requirements (SOX, PCI-DSS, transaction integrity, audit trails)
- Include cloud migration principles (cloud-first, lift-and-shift vs re-architecture)
- Write to `.arckit/memory/architecture-principles.md`
- Confirm completion with summary

## Important Notes

- **Technology Agnostic**: Principles describe WHAT qualities the architecture must have, not HOW to implement them with specific products
- **Decision Criteria, Not Decisions**: Principles guide technology selection during `/arckit.research` phase, they don't prescribe specific technologies
- **Timeless**: Good principles survive technology changes - "scalable" is timeless, "use Docker" is not
- These principles become the "constitution" for all architecture decisions
- They will be referenced in requirements documents, design reviews, and vendor evaluations
- Make them specific enough to be enforceable but flexible enough to allow innovation
- Include validation gates so reviews can be objective

## Examples of Good vs Bad Principles

**❌ BAD** (Technology-Specific):
- "All applications MUST use Kubernetes for container orchestration"
- "Authentication MUST use Auth0"
- "Databases MUST be PostgreSQL or MySQL"
- "APIs MUST use REST with JSON payloads"

**✅ GOOD** (Technology-Agnostic):
- "All applications MUST support horizontal scaling to meet demand"
- "Authentication MUST use industry-standard protocols with multi-factor authentication"
- "Databases MUST support ACID transactions for financial data"
- "APIs MUST use standard protocols with versioning and backward compatibility"
