# Using ArcKit with OpenAI Codex CLI

<p align="center">
  <img src="../docs/assets/ArcKit_Logo_Horizontal_Dark.svg" alt="ArcKit" height="32">
</p>

This directory contains ArcKit slash commands adapted for [OpenAI Codex CLI](https://chatgpt.com/features/codex).

## Prerequisites

1. **ChatGPT Plan**: Codex CLI is included with ChatGPT Plus, Pro, Business, Edu, or Enterprise plans
2. **Codex CLI installed**: Follow [installation instructions](https://developers.openai.com/codex/cli/)
3. **Git repository**: ArcKit works best in a git repository

## Setup

### Option 1: Project-Specific Commands (Recommended)

Set the `CODEX_HOME` environment variable to use this project's `.codex` directory:

```bash
# Add to your shell profile (~/.zshrc, ~/.bashrc, etc.)
export CODEX_HOME="/path/to/your/project/.codex"

# Or set it per-session
cd /path/to/your/project
export CODEX_HOME="$(pwd)/.codex"

# Start Codex CLI
codex
```

### Option 2: Global Commands

Copy commands to your global Codex prompts directory:

```bash
# Copy all ArcKit commands to global location
cp .codex/prompts/*.md ~/.codex/prompts/

# Start Codex CLI from your project directory
codex
```

## Command Invocation

Codex CLI uses the format `/prompts:command-name` to invoke custom commands.

**ArcKit commands:**

```bash
# Phase 0: Project Planning
/prompts:arckit.plan Create project plan with timeline, phases, gates, and Mermaid diagrams

# Phase 1: Establish Governance
/prompts:arckit.principles Create architecture principles for financial services

# Phase 2: Stakeholder Analysis
/prompts:arckit.stakeholders Analyze stakeholders for cloud migration project

# Phase 3: Risk Assessment
/prompts:arckit.risk Create risk register for payment gateway using Orange Book

# Phase 4: Business Case
/prompts:arckit.sobc Create Strategic Outline Business Case for payment gateway

# Phase 5: Define Requirements
/prompts:arckit.requirements Create requirements for payment gateway modernization

# Phase 5.5: Data Modeling
/prompts:arckit.data-model Create data model for payment gateway with ERD and GDPR compliance

# Phase 6: Strategic Planning with Wardley Mapping
/prompts:arckit.wardley Create Wardley map for digital services showing build vs buy strategy

# Phase 7: Vendor Selection
/prompts:arckit.sow Generate RFP statement of work
/prompts:arckit.evaluate Score vendors against requirements

# Phase 8: Design Reviews
/prompts:arckit.hld-review Review high-level design for scalability
/prompts:arckit.dld-review Review detailed design for security

# Phase 9: Compliance & Security
/prompts:arckit.secure UK Government Secure by Design review
/prompts:arckit.mod-secure MOD Secure by Design review
/prompts:arckit.tcop Technology Code of Practice assessment
/prompts:arckit.atrs AI Transparency Risk Standards assessment
/prompts:arckit.ai-playbook AI Playbook compliance check

# Phase 10: Analysis & Visualization
/prompts:arckit.analyze Analyze architecture for complexity
/prompts:arckit.diagram Generate architecture diagrams
/prompts:arckit.traceability Generate traceability matrix
/prompts:arckit.servicenow Export architecture to ServiceNow CMDB
```

## Workflow

### 0. Project Plan (Start Here!)

```bash
/prompts:arckit.plan Create project plan for cloud migration with 6-month timeline
```

Creates: `projects/001-project-name/project-plan.md`

**Generates comprehensive project plan with:**
- GDS Agile Delivery phases (Discovery → Alpha → Beta → Live)
- Mermaid Gantt chart showing timeline, dependencies, and milestones
- Workflow diagram showing gates and decision points
- Phase-by-phase activity tables with ArcKit command integration
- Approval criteria for Discovery, Alpha, and Beta assessments

**Reads existing artifacts to tailor the plan:**
- Stakeholder analysis → impacts Discovery timeline
- Requirements → impacts Alpha/Beta timeline
- Architecture principles → identifies compliance needs
- Business case → informs budget and team sizing
- Risk register → highlights timeline risks

### 1. Architecture Principles (Foundation)

```bash
/prompts:arckit.principles Create cloud-first principles for our organization
```

Creates: `.arckit/memory/architecture-principles.md`

### 2. Stakeholder Analysis (Before Requirements!)

```bash
/prompts:arckit.stakeholders Analyze stakeholders for cloud migration where CFO wants cost savings, CTO wants innovation, and Operations is worried about downtime
```

Creates: `projects/001-project-name/stakeholder-drivers.md`

**Key output:**
- Power-Interest Grid
- Driver → Goal → Outcome traceability
- Conflict analysis and resolutions
- RACI matrix

### 3. Risk Assessment (NEW - v0.2.4)

```bash
/prompts:arckit.risk Create risk register for cloud migration project
```

Creates: `projects/001-project-name/risk-register.md`

**Follows HM Treasury Orange Book 2023:**
- Part I: 5 Risk Management Principles (Governance, Integration, Collaboration, Risk Processes, Continual Improvement)
- Part II: Risk Control Framework (4-pillar structure)
- 6 risk categories: Strategic, Operational, Financial, Compliance, Reputational, Technology
- 4Ts response: Tolerate, Treat, Transfer, Terminate
- Inherent vs Residual risk (5×5 matrix: Likelihood × Impact)

**Complete stakeholder integration:**
- Every risk has owner from RACI matrix
- Risks link to stakeholder concerns/conflicts
- Risk appetite compliance monitoring

**Feeds into SOBC:**
- Strategic Case: Strategic risks show urgency
- Economic Case: Financial risks inform cost contingency
- Management Case Part E: Full risk register

### 4. Business Case (NEW - v0.2.3)

```bash
/prompts:arckit.sobc Create SOBC for cloud migration with £2M investment
```

Creates: `projects/001-project-name/sobc.md`

**Follows HM Treasury Green Book 5-case model:**
- Strategic Case (problem, drivers, stakeholder goals)
- Economic Case (options analysis, benefits mapping, NPV, ROI)
- Commercial Case (procurement strategy, Digital Marketplace)
- Financial Case (budget, funding, affordability)
- Management Case (governance, delivery, change, benefits realization - uses risk register)

**Complete traceability to stakeholders:**
- All benefits trace to stakeholder goals
- All risks linked to stakeholder conflicts

### 5. Requirements (Informed by Stakeholders)

```bash
/prompts:arckit.requirements Create requirements for the cloud migration project
```

Creates: `projects/001-project-name/requirements.md`

**Automatically traces back to stakeholder goals:**
- Example: "BR-001 addresses CFO's goal G-1: Reduce infrastructure costs 40%"
- Documents requirement conflicts and resolutions

### 5.5. Data Model (NEW)

```bash
/prompts:arckit.data-model Create data model for payment gateway
```

Creates: `projects/001-project-name/data-model.md`

**Creates comprehensive data model based on DR-xxx requirements:**
- Visual Entity-Relationship Diagram (ERD) using Mermaid
- Detailed entity catalog (E-001, E-002, etc.) with attributes, types, validation
- PII identification and GDPR/DPA 2018 compliance
- Data governance matrix (business owners from stakeholder RACI, stewards, custodians)
- CRUD matrix showing which components access which entities
- Data integration mapping (upstream sources, downstream consumers)
- Sector-specific compliance (PCI-DSS for payments, HIPAA for health, etc.)
- Data quality framework with measurable metrics
- Complete traceability: DR-xxx → Entity → Attribute → Stakeholder

**Key Features:**
- **GDPR Compliance**: PII inventory, legal basis for processing, data subject rights, retention schedules
- **Data Governance**: Clear ownership and accountability from stakeholder RACI matrix
- **Integration Ready**: Maps upstream/downstream data flows for HLD/DLD review

### 6. Vendor RFP

```bash
/prompts:arckit.sow Generate statement of work for cloud migration RFP
```

Creates: `projects/001-project-name/sow.md`

### 7. Design Reviews

```bash
/prompts:arckit.hld-review Review the high-level design for our microservices architecture
```

Creates: `projects/001-project-name/hld-review-YYYYMMDD.md`

## Approval Modes

Codex CLI has different approval modes that affect how ArcKit commands work:

### Auto Mode (Recommended)

```bash
codex --auto
```

- Automatically executes bash scripts (`.arckit/scripts/bash/*.sh`)
- Auto-creates files in workspace
- Requires approval for network access or operations outside workspace

### Read Only Mode

```bash
codex --read-only
```

- Good for reviewing plans before making changes
- Won't execute scripts or create files automatically

### Full Access Mode (Use with Caution)

```bash
codex --auto --network
```

- Allows network access without approval
- Use only when needed (e.g., fetching remote templates)

## Differences from Claude Code

| Feature | Claude Code | Codex CLI |
|---------|-------------|-----------|
| **Command format** | `/arckit.principles` | `/prompts:arckit.principles` |
| **Command location** | `.claude/commands/` | `.codex/prompts/` |
| **Environment variable** | N/A | `CODEX_HOME` |
| **Approval modes** | Automatic | `--auto`, `--read-only`, `--network` |
| **Bash scripts** | ✅ Automatic | ✅ With approval (or `--auto`) |
| **File access** | ✅ Full workspace | ✅ Sandboxed to workspace |

## File Structure

```
your-project/
├── .codex/
│   ├── README.md (this file)
│   └── prompts/
│       ├── arckit.plan.md
│       ├── arckit.principles.md
│       ├── arckit.stakeholders.md
│       ├── arckit.risk.md
│       ├── arckit.sobc.md
│       ├── arckit.requirements.md
│       ├── arckit.data-model.md
│       ├── arckit.sow.md
│       ├── arckit.hld-review.md
│       ├── arckit.dld-review.md
│       ├── arckit.evaluate.md
│       ├── arckit.secure.md
│       ├── arckit.mod-secure.md
│       ├── arckit.tcop.md
│       ├── arckit.atrs.md
│       ├── arckit.ai-playbook.md
│       ├── arckit.analyze.md
│       ├── arckit.diagram.md
│       ├── arckit.wardley.md
│       ├── arckit.traceability.md
│       └── arckit.servicenow.md
├── .arckit/
│   ├── memory/
│   │   └── architecture-principles.md
│   ├── scripts/
│   │   └── bash/
│   │       └── create-project.sh
│   └── templates/
│       ├── architecture-principles-template.md
│       ├── stakeholder-drivers-template.md
│       ├── requirements-template.md
│       ├── sow-template.md
│       └── (other templates)
└── projects/
    └── 001-project-name/
        ├── stakeholder-drivers.md
        ├── risk-register.md
        ├── sobc.md
        ├── requirements.md
        ├── data-model.md
        ├── sow.md
        └── (other artifacts)
```

## Troubleshooting

### Commands Not Found

If `/prompts:arckit.principles` doesn't work:

1. **Check CODEX_HOME** is set correctly:
   ```bash
   echo $CODEX_HOME
   # Should show /path/to/your/project/.codex
   ```

2. **Verify files exist**:
   ```bash
   ls -la $CODEX_HOME/prompts/
   # Should show arckit.*.md files
   ```

3. **Restart Codex**:
   ```bash
   # Exit and restart codex CLI
   exit
   codex
   ```

4. **Use global location** as fallback:
   ```bash
   cp .codex/prompts/*.md ~/.codex/prompts/
   ```

### Argument Parsing Error: "expected key=value"

If you get an error like "expected key=value but found 'Add'" or "expected key=value but found 'Create'":

**Problem**: Some prompts accidentally included `$PROJECT_NAME` in example text, which Codex CLI interprets as a required named parameter.

**Solution**: This has been fixed in the prompts (v0.4.1+). If using older versions, provide an empty value:

```bash
# ✅ WORKAROUND for older versions:
/prompts:arckit.stakeholders PROJECT_NAME="" Add GDS as a stakeholder

# ✅ FIXED in v0.4.1+: Just use normally
/prompts:arckit.stakeholders Add GDS as a stakeholder
```

**Why**: Codex CLI detects any `$VARIABLE_NAME` in prompts as a required named parameter. We've fixed this by escaping example variables as `$$VARIABLE_NAME` so they're treated as literal text.

### Bash Scripts Require Approval

If Codex keeps asking for approval to run `.arckit/scripts/bash/*.sh`:

```bash
# Start Codex in auto mode
codex --auto
```

### Permission Denied Errors

Ensure bash scripts are executable:

```bash
chmod +x .arckit/scripts/bash/*.sh
```

## Version

ArcKit v0.4.1 (25 commands)

**What's New in v0.4.1:**
- 🗓️ **Project Planning**: `/prompts:arckit.plan` - Comprehensive project planning with GDS Agile Delivery phases
- 📚 **Documentation Expansion**: 660-line planning guide, expanded design review (+167 lines) and procurement (+191 lines) guides
- 🚀 **Multi-AI Deployment**: Plan command deployed to all three AI systems (Claude, Codex, Gemini)
- 📋 **Updated Workflow**: Plan-first approach with Phase 0 before all other phases
- 🔧 **Version Consistency**: All version references synchronized to v0.4.1
- 🧹 **Asset Cleanup**: Removed versioned PNG banner files

**What was New in v0.3.6:**
- 🗓️ Added `/prompts:arckit.plan` - Project planning with GDS Agile Delivery phases, Mermaid Gantt charts, and workflow gates
- 🤖 Added Gemini CLI support (third AI system!) with automatic converter
- 🏛️ Added `/prompts:arckit.dos` - Digital Outcomes and Specialists procurement
- 🏛️ Added `/prompts:arckit.gcloud` - G-Cloud Framework procurement
- 📚 Triple-AI documentation (Claude Code + Codex CLI + Gemini CLI)
- 🔧 Fixed .codex/.gitignore tracking issue

**What was New in v0.3.5:**
- 🤖 Full OpenAI Codex CLI support with `.codex/` folder structure
- 📚 Comprehensive `.codex/README.md` setup and usage guide
- 🔄 All ArcKit commands available in Codex format
- ⚙️ Automatic CODEX_HOME environment setup

**What was New in v0.3.0:**
- 🎯 Added `/prompts:arckit.sobc` - HM Treasury Green Book Strategic Outline Business Case
- 🛡️ Added `/prompts:arckit.risk` - HM Treasury Orange Book Risk Management
- 📊 Added `/prompts:arckit.data-model` - Data modeling with ERD, GDPR compliance, data governance
- 🔄 Updated workflow: Stakeholders → Risk → SOBC → Requirements → Data Model → Vendor selection
- ✅ Complete UK Government compliance (Green Book + Orange Book)
- 🔗 End-to-end traceability: Stakeholder → Driver → Goal → Risk → Benefit → Requirement → Entity

## Support

- **Documentation**: See main [ArcKit README](../README.md)
- **Issues**: Report Codex-specific issues with `[Codex]` prefix
- **Workflow Guide**: See `.arckit/templates/` for template examples

## Comparison: ChatGPT Plus vs API

| Aspect | ChatGPT Plus + Codex CLI | OpenAI API (Custom Build) |
|--------|--------------------------|---------------------------|
| **Cost** | $20/month (unlimited) | ~$3-5 per project |
| **Setup** | Install CLI, set CODEX_HOME | Build custom CLI tool |
| **UX** | Native terminal experience | Programmatic control |
| **File Access** | ✅ Built-in | ❌ Must implement |
| **Bash Scripts** | ✅ Built-in | ❌ Must implement |
| **Best for** | Enterprise architects, individual users | CI/CD, automation, custom workflows |

**Recommendation**: Use Codex CLI for manual governance workflows. Use OpenAI API for automated compliance checks in CI/CD pipelines.

## Next Steps

1. **Set CODEX_HOME**: `export CODEX_HOME="$(pwd)/.codex"`
2. **Start Codex**: `codex --auto`
3. **Create principles**: `/prompts:arckit.principles Create cloud-first principles`
4. **Analyze stakeholders**: `/prompts:arckit.stakeholders <your project description>`
5. **Define requirements**: `/prompts:arckit.requirements <your project description>`

---

**Happy architecting with ArcKit + Codex CLI!** 🏗️✨
