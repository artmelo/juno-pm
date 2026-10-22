# AI PRD · Juno

## Problem & user

RocketShip PMs need this handled: Juno acts as RocketShip's AI Product Management Copilot. It analyzes customer feedback, support tickets, sales commitments, executive requests, and engineering constraints to produce a ranked list of product priorities (P0–P3), with strategic rationale, business impact, feasibility, risks, and recommended next actions. Juno does this inside limits a human set on purpose, and defends every call it makes.

## The harness

| Surface | Specification |
|---|---|
| 01 Context | Juno can read the RocketShip Product Strategy One-Pager, Product Quarterly Roadmap, Raw Signals, Engineering Capacity Note, and Sales… |
| 02 Tools | Juno can analyze the five provided documents, extract and consolidate signals, identify duplicates, map requests to strategic pillars,… |
| 03 Loop | One analysis pass per request. Juno reviews the available documents, evaluates each signal against the strategy and constraints, and… |
| 04 Memory | Juno stops after delivering a ranked priority list with rationale, supporting evidence, business impact, feasibility, dependencies, and… |
| 05 Permissions | read auto · draft auto · write confirm · send confirm |
| 06 Verification | Juno checks each recommendation against RocketShip's P0–P3 priority framework, strategic pillars, existing roadmap, engineering capacity,… |

## 01 Context · Data Requirements

**Required sources and exclusions**

Juno can read the RocketShip Product Strategy One-Pager, Product Quarterly Roadmap, Raw Signals, Engineering Capacity Note, and Sales Pipeline Snapshot. It uses these documents to understand strategic pillars, P0–P3 definitions, customer pain points, revenue risks, existing commitments, engineering capacity, and dependencies. It distinguishes verified facts from assumptions and identifies conflicting information.

**How fresh must it be**

Juno should use the latest available versions of the five RocketShip context documents. Raw Signals, Sales Pipeline, and Engineering Capacity should be refreshed at least weekly or immediately after significant changes. Refresh Strategy and Roadmap whenever they are officially updated.

## 02 Tools · System Capabilities

**The verb list**

Juno can analyze the five provided documents, extract and consolidate signals, identify duplicates, map requests to strategic pillars, assign proposed P0–P3 priorities, evaluate revenue and customer impact, flag engineering dependencies, and generate a ranked recommendation table. It can draft decision briefs, stakeholder questions, and suggested next actions. It cannot access live systems, change the roadmap, create tickets, contact customers, or commit engineering resources.

**Deliberate omissions**

Juno deliberately has no write access to Jira/Azure DevOps, CRM, Slack, or the product roadmap. It cannot modify priorities, create tickets, update sales commitments, or contact stakeholders.

These limitations prevent unauthorized changes, accidental commitments, and decisions based on incomplete information. Juno acts as a read-only Product Management Copilot, providing evidence-based recommendations while keeping final decisions and execution under the Product Manager's control.

## 03 Loop · AI Costs & Latency

**Turn ceiling and escalation**

One analysis pass per request. Juno reviews the available documents, evaluates each signal against the strategy and constraints, and produces a prioritized recommendation. If information is missing or contradictory, it flags the gap rather than repeatedly searching or inventing answers. The Product Manager can provide additional context and request another pass.

**Latency and cost target**

Juno should deliver standard prioritization recommendations within 10 seconds and full analysis of all five RocketShip documents within 30 seconds for 95% of requests.

To control cost and latency, Juno uses a single analysis pass, retrieves only relevant context, and avoids unnecessary tool calls or repeated LLM turns. Maximum 2 LLM turns per task, with no autonomous retry loops.

Target cost: under $0.05 per standard request and $0.15 per full analysis. If limits are reached, Juno returns a partial result with clear limitations rather than continuing indefinitely.

## 04 Memory · Data Requirements

**What persists, at what scope**

Juno stops after delivering a ranked priority list with rationale, supporting evidence, business impact, feasibility, dependencies, and recommended next actions. Each item must have a proposed priority or an explicit 'Needs clarification' status. Unresolved conflicts and missing evidence are listed separately. Juno does not continue analysis indefinitely or take action without a new request.

**Expiry and write rules**

Juno applies the following expiry rules:

Raw Signals and Sales Pipeline: 7 days.

Engineering Capacity: 7 days or immediately after resource changes.

Product Roadmap: 30 days or when officially updated.

Product Strategy: 90 days or when officially revised.

AI-generated recommendations: expire after 7 days or when underlying evidence changes.

Source of truth: Verified Product Manager corrections override previous AI-generated outputs. Official, current RocketShip documents take precedence over stored AI assumptions. Conflicting information must be flagged for human review, not silently overwritten.

Juno cannot modify source documents or permanently store decisions without explicit Product Manager approval. Expired facts must be revalidated before use in new recommendations.

## 05 Permissions · AI Risks & Mitigations

**The permission tier**

| Side-effect class | Tier |
|---|---|
| read | auto |
| draft | auto |
| write | confirm |
| send | confirm |

**Justification**

Juno may independently read provided context, analyze signals, propose priorities, identify risks, and draft recommendations. It must ask for approval before changing priorities, modifying roadmap commitments, sharing information externally, contacting stakeholders, or initiating any action affecting customers or engineering teams. The Product Manager retains all decision-making authority.

## 06 Verification · AI Testing & Measurement

**The check before output ships**

Juno checks each recommendation against RocketShip's P0–P3 priority framework, strategic pillars, existing roadmap, engineering capacity, and sales risks. Every material claim must reference its source document. It flags unsupported assumptions, contradictory commitments, and unavailable capacity. It must not present unshipped features as available. No automated outcome validation exists yet; the Product Manager reviews the recommendations before acting.

**Failure behaviour**

If verification fails due to missing, outdated, conflicting, or unsupported information, Juno must not present the recommendation as validated.

Juno should:

Clearly flag the affected recommendations as "Needs Review" and explain why verification failed.

Provide partial results supported by reliable evidence, distinguishing facts from assumptions.

Identify missing information and suggest specific actions to resolve the issue.

Never invent data, silently omit failed checks, or automatically change priorities.

Request Product Manager review before any decision based on unverified information.

If critical sources are unavailable, Juno returns a structured failure summary instead of a ranked priority list. All failures remain visible to the user, and Juno takes no external actions.

## Eval plan

_Stub. Module 6 fills this in: golden set, pass thresholds, and regression cadence for the verification gate above._

## Out of scope

Any capability not in the verb list above, and any action tiered `blocked`. Both are decisions on the record, not omissions.
