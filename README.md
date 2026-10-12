# Hi there, I'm Sam

### Data Engineer | DataOps Foundation, Research Production & Enterprise AI Integration

I am a Data Engineer working at the intersection of data architecture, cloud platforms, applied economics, and research production. I design reliable data systems that transform complex analytical requirements into scalable, production-ready pipelines and governed data products. 

My work builds the operational trust and continuity layer of the research production system. By converting external data sources into governed institutional evidence, I ensure that analytics, Data Science, Machine Learning, AI agents, researchers, and publication products can use data responsibly. 

A research product is only as trustworthy as the evidence chain behind it and only as sustainable as the operating process that can recreate it. DataOps establishes and maintains both. I approach engineering with an emphasis on reproducibility, idempotency, observability, dependency control, and clear operational handoffs, making recurring research products sustainable and reproducible without heroic manual effort.

---

## Core Capabilities

### DataOps Foundation and Evidence Control
- Establishing source integrity and historical continuity.
- Building controlled and restartable ingestion pipelines.
- Implementing data validation and quality controls to prevent failed data from silently reaching downstream users.
- Applying stable series identifiers and standardizing definitions, units, frequencies, and geographic fields.
- Preserving versioned data snapshots and end-to-end lineage from source to silver-table.
- Creating reusable bronze, silver, and enriched-silver data products.

### Production Assurance & Lifecycle Management
- Binding research releases to a specific source snapshot to guarantee release reproducibility.
- Designing production validation gates to evaluate analytical outputs before publication.
- Orchestrating recurring execution workflows and managing processing state.
- Monitoring pipelines to detect source failures, stale data, and schema changes.
- Tracking upstream data revisions and managing correction controls.

### Microsoft Data Platform & Architecture
- Microsoft Fabric, OneLake, and Fabric Lakehouse architectures.
- Delta tables and medallion-pattern transformations.
- Data Factory pipelines and Fabric notebooks.
- Cloud and platform migration.

### Engineering Automation and DevOps
- Python, PowerShell 7, Bash, and Docker.
- WSL2 and Git environment management.
- Structured logging and idempotent workflow design.

### Economics and Analytics
- Macroeconomic data
- Time-series analysis, ARMA models, and fixed-effects models.
- Stata and Tableau.

---

## DataOps and Research Production

Public-facing reports, forecasts, dashboards, commentaries, and briefings are the visible outputs of analytical work; their credibility and sustainability, however, depend on a largely invisible operational foundation. 

Research methodology establishes whether an interpretation is defensible, while DataOps establishes whether the evidence supporting that interpretation is authentic, traceable, and reproducible. Together, they make the public-facing research product credible. My infrastructure guarantees that every published claim can be traced to its source data, ensuring that the source, acquisition date, transformations, definitions, and quality checks are documented.

---

## Governed AI-Assisted Discovery

The same DataOps foundation that supports current research also enables future AI-assisted discovery. Validated, documented, and queryable Delta tables allow Data Science, Machine Learning, and human-guided AI agents to search series, identify candidate indicators, compare trends, surface possible relationships, generate hypotheses for review, and cite the underlying definitions and lineage.

AI cannot compensate reliably for weak metadata, inconsistent definitions, duplicate series, unclear temporal alignment, missing lineage, or unvalidated data. Therefore, I design trusted analytical interfaces to ensure AI agents return traceable results. AI-generated ideas do not bypass Data Science; they must enter formal methodological testing, ensuring AI-assisted discoveries are validated before reaching the productionization decision.

---

## Enterprise AI Gateway and Developer-Agent Integration

My work with AI extends beyond using generative-AI chat interfaces. I configure and maintain the model-access layer through which developer-facing AI tools connect to organizationally approved models.

The architecture connects custom organizational API Management endpoints to a locally hosted LiteLLM gateway bound to `localhost:4000`. Compatible coding agents and command-line tools are configured to use this gateway instead of connecting directly to their default provider-hosted models.

![AI Routing Architecture Diagram](assets/interactive-ai-routing-and-credential-isolation.png)
*Figure 1: AI Routing Architecture detailing the boundaries between the local developer environment, enterprise cloud, and remote model providers.*
 
### Integration Responsibilities
- Configure custom API Management URLs, credentials, and model deployments.
- Configure and operate a locally bound LiteLLM gateway to normalize provider-specific deployments behind stable model aliases.
- Route supported coding agents through the local gateway to maintain compatibility across Copilot, Claude Code, and Codex.
- Separate infrastructure configuration from conversational AI usage.

---

## Credential Security and PowerShell Environment Integration

Gateway credentials are not stored directly in scripts or PowerShell profile files. Secrets are stored in a PowerShell SecretManagement-compatible vault and retrieved when the developer environment is initialized.

My PowerShell `$PROFILE` serves as a controlled developer-environment initialization layer, dynamically preparing supported tools with the appropriate LiteLLM gateway URL, authentication credential, and enterprise model alias.

![AI Initialization Sequence Diagram](assets/secure-initialization-and-interactive-agentic-loop.png)
*Figure 2: Secure Initialization Sequence demonstrating how `$PROFILE.CurrentUserAllHosts` fetches credentials dynamically and scopes them to the agent.*

### The initialization layer is responsible for:
- Retrieving credentials from the configured vault and scoping them to the appropriate local process.
- Avoiding hard-coded secrets in reusable scripts and limiting unnecessary exposure of gateway credentials.
- Separating secret storage from routing configuration.

---

## Model Lifecycle Management

The configuration must evolve as the organization's model catalog changes. Stable aliases reduce disruption to downstream tools, meaning a coding agent can continue using a consistent local model name even when the underlying organizational deployment, API version, or provider changes.

![AI Lifecycle Workflow Diagram](assets/model-lifecycle-management-and-policy-routing.png)
*Figure 3: Model Lifecycle Workflow highlighting stable alias translation and policy enforcement without disrupting the agentic loop.*

### Lifecycle responsibilities include:
1. Identifying newly available model deployments and validating endpoints.
2. Testing model compatibility through LiteLLM and updating stable local aliases.
3. Migrating tools away from superseded deployments and retiring obsolete mappings.
4. Preserving a recoverable previous state when practical.
