# Features

The Marketing Agent is built as an end-to-end campaign operating system rather than a single-purpose caption generator. The features below are described at a portfolio-safe level.

## Menu-level capability model

| Menu | What it demonstrates |
|---|---|
| Agent Chat | Natural-language command surface for analysis, package preparation, campaign planning, scheduling proposals, simulation requests, and queue status. |
| Autopilot | Content fundus ingestion, topic-bundle recognition, media dedupe, package creation, content requests, posting plan creation, and optional simulation. |
| Credentials | Provider profiles, OAuth connection flows, masked secret feedback, website/FTP inventory, MiroFish configuration, Paperclip configuration, and custom connector profiles. |
| Product Growth | CSV product import, top hero-product ranking, weak-product diagnosis, conversion strategy, and landing-page brief generation. |
| New Campaign | Typed campaign creation with objective, audience, platforms, duration, topics, variants, workspace context, and report generation. |
| Approval | Human-in-the-loop review for package state, captions, titles, descriptions, hashtags, CTAs, schedules, and destination platforms. |
| Media | Workspace asset library for uploaded images, videos, scripts, usage notes, and reusable campaign references. |
| Pipeline | Readiness model that checks media, packages, approvals, policy, platform capability, simulation, and scheduling. |
| Simulation | Local campaign preflight plus optional MiroFish orchestration and feedback import. |
| Paperclip | Optional agent-company control plane for governed roles, tasks, heartbeats, status, and audit mirrors. |
| Workspaces | Multi-brand separation for identity, audiences, products, media, policies, connected accounts, and campaign history. |

## Strategy and content generation

The system can produce:

- campaign strategies;
- audience hypotheses;
- platform-specific content angles;
- title and description variants;
- captions and calls to action;
- hashtags and metadata;
- approval-ready post packages;
- landing-page briefs for selected hero products;
- recommendations for next content requests when the fundus is too small.

Generated content is treated as a draft artifact that must pass policy and approval before external side effects.

## Campaign Autopilot

Autopilot is the core long-running campaign feature. It allows a human or an external creative agent to place a large content fundus into one campaign dossier.

Recommended operating model:

```text
campaign-dossier/
  BRIEF.md
  campaign.yaml
  fundus/
    _brand/
      logo.png
      claims_no_gos.md
      links.md
    01_product_intro/
      script.md
      final_video_9x16.mp4
      final_image.jpg
    02_customer_story/
      story.md
      final_video_16x9.mp4
    analytics/
      youtube_export.csv
```

The same brand, same objective, and same time horizon should normally be one campaign with many numbered topic bundles. Separate dossiers are recommended only for separate brands, materially different goals, different compliance contexts, or independent time horizons.

Package count follows this rule:

```text
topic bundle count x platform count x packages per platform
```

For example, fifteen topic bundles across YouTube and TikTok with one package per platform creates approximately thirty packages.

## Product growth

Product Growth connects marketing content with commercial prioritization. It supports:

- product catalog import;
- hero-product ranking, commonly up to twenty products;
- scoring based on demand, proof, economics, content potential, SEO, and readiness;
- weak-product diagnosis;
- landing-page brief generation;
- strategic rationale for campaign focus.

The result is not a sales guarantee. It is decision support for choosing where campaign energy should go first.

## Publishing and scheduler

The system is designed to avoid accidental platform side effects:

- generated packages start in reviewable states;
- human approval is required by default;
- dry-run is the recommended first publishing mode;
- scheduler execution is tick-based and can be invoked by CLI, API, MCP, or service wrapper;
- idempotency keys reduce duplicate-post risk;
- live publishing requires connector support, platform permission, credentials, approval, and policy compliance.

Platform maturity is intentionally mixed. YouTube has the strongest real connector path. TikTok and Instagram have dry-run and guarded scaffolds until the required platform permissions and reviews are complete.

## Analytics learning loop

The learning loop supports:

- importing platform analytics exports;
- summarizing performance by platform;
- extracting reusable lessons;
- improving title, hook, timing, and content recommendations;
- training learned scorers where sufficient data exists;
- feeding lessons into future campaign planning.

Real platform analytics remain the source of truth. Synthetic simulation is useful for preflight, but live results decide long-term optimization.

