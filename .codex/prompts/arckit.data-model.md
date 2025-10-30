---
description: Create comprehensive data model with entity relationships, GDPR compliance, and data governance
---

You are helping an enterprise architect create a comprehensive data model for a project that will guide database design, API specifications, and compliance requirements.

## User Input

```text
$ARGUMENTS
```

## Instructions

1. **Check for prerequisites**:
   - **MANDATORY**: Check if requirements.md exists for this project
     - Look for `projects/*/requirements.md` files
     - If requirements don't exist, **STOP** and tell user to run `/arckit.requirements` first
     - Data model MUST be based on Data Requirements (DR-xxx) from requirements.md
   - **RECOMMENDED**: Check if stakeholder analysis exists
     - Look for `projects/*/stakeholder-drivers.md` files
     - If it exists, read it to identify data owners and governance stakeholders
     - Use RACI matrix to assign data ownership responsibilities
   - **OPTIONAL**: Check if SOBC exists
     - Look for `projects/*/sobc.md` files
     - If it exists, reference data-related benefits and costs

2. **Find the project**:
   - If user specifies project name or number, use that
   - Otherwise, look for most recent project directory in `projects/`
   - Use the same project directory where requirements.md exists

3. **Read the template**: Read `.arckit/templates/data-model-template.md` to understand the structure

4. **Extract data requirements**:
   - Read the project's `requirements.md` file
   - Extract ALL Data Requirements (DR-xxx)
   - Also look for privacy/GDPR requirements in NFR section
   - Identify integration requirements (INT-xxx) that involve data exchange
   - Note any data-related business requirements (BR-xxx)

5. **Generate comprehensive data model**:

   **A. Executive Summary**:
   - Total number of entities identified
   - Data classification summary (Public, Internal, Confidential, Restricted)
   - PII/sensitive data identified (Yes/No)
   - GDPR/DPA 2018 compliance status
   - Key data governance stakeholders

   **B. Visual Entity-Relationship Diagram (ERD)**:
   - Create Mermaid ERD syntax showing:
     - All entities (E-001, E-002, etc.)
     - Relationships (one-to-one, one-to-many, many-to-many)
     - Cardinality notation
   - Organize by logical domain/bounded context if possible
   - Use descriptive entity and relationship names

   **C. Entity Catalog** (E-001, E-002, etc.):
   - For each entity, document:
     - **Entity ID**: E-001, E-002, etc.
     - **Entity Name**: Customer, Transaction, Product, etc.
     - **Description**: What this entity represents
     - **Source Requirement**: Which DR-xxx requirement(s) drive this entity
     - **Business Owner**: From stakeholder RACI matrix
     - **Technical Owner**: Data steward or database team
     - **Data Classification**: Public/Internal/Confidential/Restricted
     - **Estimated Volume**: Initial records + growth rate
     - **Retention Period**: How long data is kept (GDPR requirement)
     - **Attributes Table**:
       ```
       | Attribute | Type | Required | PII | Description | Validation | Source Req |
       |-----------|------|----------|-----|-------------|------------|------------|
       | customer_id | UUID | Yes | No | Unique identifier | UUID v4 | DR-001 |
       | email | String(255) | Yes | Yes | Contact email | RFC 5322, unique | DR-002 |
       ```
     - **Relationships**: What other entities this connects to
     - **Indexes**: Primary key, foreign keys, performance indexes
     - **Privacy Notes**: GDPR considerations, data subject rights

   **D. Data Governance Matrix**:
   - For each entity, identify:
     - **Data Owner**: Business stakeholder responsible (from RACI matrix)
     - **Data Steward**: Person responsible for quality and compliance
     - **Data Custodian**: Technical team managing storage/backups
     - **Access Control**: Who can view/modify (roles/permissions)
     - **Sensitivity**: Public, Internal, Confidential, Restricted
     - **Compliance**: GDPR, PCI-DSS, HIPAA, etc.
     - **Quality SLA**: Accuracy, completeness, timeliness targets

   **E. CRUD Matrix** (Create, Read, Update, Delete):
   - Map which components/systems can perform which operations on each entity
   - Example:
     ```
     | Entity | Payment API | Admin Portal | Reporting Service | CRM Integration |
     |--------|-------------|--------------|-------------------|-----------------|
     | E-001: Customer | CR-- | CRUD | -R-- | -R-- |
     | E-002: Transaction | CR-- | -R-- | -R-- | ---- |
     ```
   - Helps identify unauthorized access patterns and data flows

   **F. Data Integration Mapping**:
   - **Upstream Systems**: Where data comes from
     - System name, entity mapping, update frequency, data quality SLA
   - **Downstream Systems**: Where data goes to
     - System name, entity mapping, sync method (API, batch, event), latency SLA
   - **Master Data Management**: Which system is "source of truth" for each entity

   **G. Privacy & Compliance**:
   - **GDPR/DPA 2018 Compliance**:
     - List all PII attributes across all entities
     - Document legal basis for processing (consent, contract, legitimate interest, etc.)
     - Data subject rights implementation (access, rectification, erasure, portability)
     - Data retention schedules per entity
     - Cross-border data transfer considerations (UK-EU adequacy)
   - **Data Protection Impact Assessment (DPIA)**:
     - Is DPIA required? (Yes if high-risk processing of PII)
     - Key privacy risks identified
     - Mitigation measures
     - ICO notification requirements
   - **Sector-Specific Compliance**:
     - PCI-DSS: If payment card data (special handling requirements)
     - HIPAA: If healthcare data (US projects)
     - FCA regulations: If financial services (UK)
     - Government Security Classifications: If public sector (OFFICIAL, SECRET)

   **H. Data Quality Framework**:
   - **Quality Dimensions**:
     - **Accuracy**: How correct is the data? (validation rules, reference data)
     - **Completeness**: Required fields populated? (% target)
     - **Consistency**: Same data across systems? (reconciliation rules)
     - **Timeliness**: How current is the data? (update frequency, staleness tolerance)
     - **Uniqueness**: No duplicates? (deduplication rules)
     - **Validity**: Conforms to format? (regex patterns, enums, ranges)
   - **Data Quality Metrics**:
     - Define measurable targets per entity (e.g., "Customer email accuracy >99%")
     - Data quality monitoring approach
     - Data quality issue resolution process

   **I. Requirements Traceability**:
   - Create traceability table:
     ```
     | Requirement | Entity | Attributes | Rationale |
     |-------------|--------|------------|-----------|
     | DR-001 | E-001: Customer | customer_id, email, name | Store customer identity |
     | DR-002 | E-002: Transaction | transaction_id, amount, status | Track payments |
     | NFR-SEC-003 | E-001: Customer | password_hash (encrypted) | Secure authentication |
     ```
   - Show how every DR-xxx requirement maps to entities/attributes
   - Flag any DR-xxx requirements NOT yet modeled (gaps)

   **J. Implementation Guidance**:
   - **Database Technology Recommendation**:
     - Relational (PostgreSQL, MySQL) for transactional data
     - Document (MongoDB, DynamoDB) for flexible schemas
     - Graph (Neo4j) for highly connected data
     - Time-series (InfluxDB, TimescaleDB) for metrics/events
   - **Schema Migration Strategy**: How to evolve schema (Flyway, Liquibase, Alembic)
   - **Backup and Recovery**: RPO/RTO targets, backup frequency
   - **Data Archival**: When to move data from hot to cold storage
   - **Testing Data**: Anonymization/pseudonymization for test environments

6. **UK Government Compliance** (if applicable):
   - **Government Security Classifications**: OFFICIAL, SECRET, TOP SECRET
   - **Data Standards**: Use GDS Data Standards Catalogue where applicable
   - **Open Standards**: Preference for open data formats (JSON, CSV, OData)
   - **ICO Data Protection**: Reference ICO guidance for public sector
   - **National Cyber Security Centre (NCSC)**: Data security patterns

7. **Write the output**:
   - Write to `projects/{project-dir}/data-model.md`
   - Use the exact template structure from `data-model-template.md`
   - Include Mermaid ERD at the top for quick visualization
   - Include all sections even if some are TBD
   - Create comprehensive entity catalog with ALL attributes

8. **Summarize what you created**:
   - How many entities defined (E-001, E-002, etc.)
   - How many total attributes across all entities
   - How many entities contain PII (privacy-sensitive)
   - Data classification breakdown (Public/Internal/Confidential/Restricted)
   - GDPR compliance status (compliant / needs DPIA / gaps identified)
   - Key data governance stakeholders identified
   - Requirements coverage (% of DR-xxx requirements modeled)
   - Suggested next steps (e.g., "Review data model with data protection officer before proceeding to HLD" or "Run `/arckit.hld-review` to validate database technology choices")

## Example Usage

User: `/arckit.data-model Create data model for payment gateway project`

You should:
- Check prerequisites (requirements.md exists, stakeholder-drivers.md recommended)
- Find project directory (e.g., `projects/001-payment-gateway-modernization/`)
- Extract DR-xxx requirements from requirements.md
- Generate comprehensive data model:
  - Mermaid ERD showing Customer, Transaction, PaymentMethod, RefundRequest entities
  - Detailed entity catalog with attributes, PII flags, retention periods
  - GDPR compliance: PII identified, legal basis documented, DPIA required
  - Data governance: CFO owns financial data, DPO owns PII, IT owns storage
  - CRUD matrix: Payment API can create transactions, Admin can read all, Reporting read-only
  - PCI-DSS compliance: Payment card data encrypted, tokenized, not stored long-term
  - Requirements traceability: All DR-001 through DR-008 mapped to entities
- Write to `projects/001-payment-gateway-modernization/data-model.md`
- Confirm completion with summary

## Important Notes

- **Data model drives database schema, API contracts, and data governance policies**
- **GDPR compliance is MANDATORY for any PII - identify and protect it**
- **Every entity MUST trace back to at least one DR-xxx requirement**
- **Data ownership is critical - assign business owners from stakeholder RACI matrix**
- **PII requires special handling**: encryption at rest, encryption in transit, access controls, audit logging, retention limits
- **Use Mermaid ERD syntax** for GitHub-renderable diagrams (not PlantUML or other formats)
- **Data quality metrics should be measurable** (not "high quality", use "99% accuracy")
- **Consider data lifecycle**: creation, updates, archival, deletion (GDPR "right to erasure")
- **Reference architecture principles** from `.arckit/memory/architecture-principles.md` if they exist
- **Flag any DR-xxx requirements that cannot be modeled** (gaps for requirements clarification)

## Integration with Other Commands

- **Input**: Requires `requirements.md` (for DR-xxx requirements)
- **Input**: Uses `stakeholder-drivers.md` (for data ownership RACI matrix)
- **Input**: References `sobc.md` (for data-related costs and benefits)
- **Output**: Feeds into `/arckit.hld-review` (validates database technology choices)
- **Output**: Feeds into `/arckit.dld-review` (validates schema design, indexes, query patterns)
- **Output**: Feeds into `/arckit.sow` (RFP includes data migration, data governance requirements)
- **Output**: Supports `/arckit.traceability` (DR-xxx → Entity → Attribute → HLD Component)
