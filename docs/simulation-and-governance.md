# Simulation and Governance

The Marketing Agent separates prediction support from operational truth. Synthetic simulation can improve campaign decisions before publishing, while real platform analytics remain the source of performance truth after publishing.

## MiroFish campaign preflight

MiroFish is integrated as an optional external simulation layer. The Marketing Agent can create campaign seed material, start the simulation workflow, poll status, fetch reports, and import lessons back into the campaign pipeline.

At a portfolio-safe level, the simulation path is:

```mermaid
flowchart TD
    A["Selected campaign packages"] --> B["Build campaign seed"]
    B --> C["MiroFish ontology generation"]
    C --> D["Graph build"]
    D --> E["Simulation create"]
    E --> F["Prepare agents"]
    F --> G["Start simulation"]
    G --> H["Poll run status"]
    H --> I["Generate report"]
    I --> J["Fetch report"]
    J --> K["Normalize lessons"]
    K --> L["Improve strategy and package recommendations"]
```

MiroFish is useful for:

- stress-testing campaign angles;
- identifying weak messaging;
- comparing buyer-intent hypotheses;
- detecting synthetic audience objections;
- surfacing communication and controversy risks;
- improving hooks, captions, titles, and platform targeting before approval.

MiroFish is not a factual prediction oracle. The system treats it as synthetic decision support, and the operator should compare lessons against real analytics after publishing.

## Local simulation

The local simulation path can run without an external simulator. It provides immediate preflight scoring and package feedback using the local campaign context.

This is useful when:

- MiroFish is not configured;
- the operator needs a fast review loop;
- the campaign is not ready for external simulation;
- a package needs lightweight ranking before human approval.

## Paperclip control plane

Paperclip is integrated as an optional agent-company sidecar. It does not replace the Marketing Agent. It adds governance around delegated tasks.

Paperclip can represent roles such as:

- strategy lead;
- content operator;
- product-growth analyst;
- simulation analyst;
- compliance reviewer;
- publishing coordinator;
- analytics analyst.

The Marketing Agent remains the owner of campaign state and platform safety. Paperclip delegates allowlisted work and mirrors task records, but it does not receive raw platform credentials and cannot publish directly.

## Paperclip sequence

```mermaid
sequenceDiagram
    participant User as Operator
    participant UI as Paperclip page
    participant API as Marketing Agent API
    participant PC as Paperclip sidecar
    participant Tools as Marketing services
    participant Audit as Local audit mirror
    participant Approval as Approval queue

    User->>UI: Create governed task
    UI->>API: Submit role, action, goal, context
    API->>API: Validate workspace and allowlisted action
    API->>PC: Optional sidecar coordination
    API->>Tools: Execute safe marketing service
    Tools-->>API: Artifacts, package IDs, recommendations
    API->>Audit: Mirror task result
    API->>Approval: Create approval request when needed
    API-->>UI: Show status and evidence
```

## Human-in-the-loop governance

The governance model is intentionally conservative:

- generated packages are drafts until reviewed;
- approval is required before scheduling and publishing;
- dry-run is the first publishing mode during setup;
- connector maturity is checked before live actions;
- account assignment is checked at workspace level where supported;
- MiroFish feedback is advisory, not authoritative;
- Paperclip tasks are allowlisted by role and action;
- external LLMs operate through MCP tools, not direct secret access.

## Governance principle

The Marketing Agent is designed to let AI do the heavy coordination work while preserving human responsibility for brand judgment, platform authorization, legal/compliance risk, and final publishing approval.

