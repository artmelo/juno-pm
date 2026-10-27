# Human Evaluation Rubric · Juno

## What graders score

- **What you’re scoring:** Juno’s idea-to-PRD workflow: transforming rough product ideas into structured, actionable PRDs aligned with RocketShip’s constraints and priorities.
- **Value proposition:** Juno helps me, as the Product Manager aboard RocketShip, turn rough ideas into clear, actionable, evidence-based PRDs by validating them against ship constraints, identifying risks and dependencies, and recommending priorities

## Dimensions

| Dimension | Question | Scale | 1 or No | 3 | 5 or Yes |
|---|---|---|---|---|---|
| Constraint Compliance (deal-breaker) | Does Juno respect RocketShip's operational, resource, and safety constraints without proposing unrealistic solutions? | 1 to 5 | Violates critical constraints or proposes unsafe, impossible solutions. | Respects major constraints but misses minor limitations or dependencies. | Fully respects constraints, identifies limitations, and proposes feasible alternatives. |
| PRD Quality & Actionability | Does Juno transform a rough idea into a clear, structured PRD with actionable requirements, priorities, and measurable success criteria? | 1 to 5 | Vague, incomplete PRD with unclear requirements.     | Usable PRD but missing details, prioritization, or measurable outcomes. | Clear, complete, prioritized PRD ready for PM review and execution planning. |
| Evidence & Decision Reliability (deal-breaker) | Does Juno use verified RocketShip data, clearly flag assumptions, and escalate uncertain or high-impact decisions for human approval? | Yes / No | Juno invents facts, presents assumptions as verified information, or makes high-impact decisions without human approval. | n/a | Recommendations are grounded in available evidence, assumptions are explicitly identified, and decisions requiring human approval are escalated. |

## Calibration

- **How many answers you’ll score, and how often:** Review 10 Juno-generated PRDs per week, including complex, high-risk, and randomly selected cases.
- **Who scores them with you:** Product Manager (me) and Engineering Lead
- **What happens when two of you disagree:** If scores differ by 2+ points or on a deal-breaker, PM and Engineering Lead review the evidence together, agree on a final score, and refine the rubric to prevent future ambiguity and misalignment.

## Pass bar

Average score of 4 out of 5 or higher across scaled questions, with no score below 3, and all deal-breaker questions passing.

**Fails outright, whatever the average:**

- Constraint Compliance: any score of 1
- Evidence & Decision Reliability: any "no"
- Fabricated evidence, violation of RocketShip's critical constraints, unauthorized decisions, or failure to escalate safety-critical risks automatically fail the evaluation, regardless of the overall score.
