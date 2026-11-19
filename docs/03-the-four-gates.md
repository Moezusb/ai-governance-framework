# 03 · The Four Gates

> *Four doors between the model and the world:*
> *what it hears, how it thinks, what it touches, what it says.*

[← Risk Classification](02-risk-classification.md) · [Next: Agents and Tool Permissions →](04-agents-and-tool-permissions.md)

---

Version 1 of this framework had a Triple-Gate Safety Protocol: data in, logic, human review out. It was built for AI that answers. Agents added a door the original design never had to guard, so the protocol now has four gates. Each tier passes all four; what changes by tier is how heavy each gate is.

```
   ┌──────────┐    ┌──────────┐    ┌──────────┐    ┌──────────┐
   │  GATE A  │ →  │  GATE B  │ →  │  GATE C  │ →  │  GATE D  │
   │   Data   │    │  Logic   │    │  Reach   │    │  Human   │
   │ what goes│    │ what gets│    │ what it  │    │ what goes│
   │    in    │    │ reasoned │    │ can touch│    │    out   │
   └──────────┘    └──────────┘    └──────────┘    └──────────┘
```

---

## Gate A · Data Sovereignty (What Goes In)

Data governance is not an IT problem. It is a trust problem. Every piece of customer data sent to a third-party model is a decision your customer did not explicitly make. Treat it accordingly.

**Contracts first.** No personal or confidential customer data reaches a model provider without a Data Processing Agreement and enterprise terms in place. This is non-negotiable for Tier 2 and above, and it includes the "free trial" tool someone connected last week.

**Two controls, not one.** Version 1 asked for "zero-retention providers," which blurred two different questions. Ask both, separately:
- **Training use.** Does the provider use your inputs or outputs to train or improve its models? For customer data, the contractual answer must be no.
- **Retention.** How long does the provider keep your inputs and outputs, and why? Zero data retention is the strongest position where it is available. Where it is not, the window must be known, short, documented, and matched to a real need such as abuse monitoring.

"We assume they don't use it" is not a data governance position.

**Data minimization.** Send only what the task requires. If a support automation needs a ticket category, do not send it the full account history. Scoping inputs is the cheapest form of risk reduction available.

**Know your residency.** For regulated customers, where the data is processed can matter as much as whether it is processed. Record the region in the [System Card](../templates/02-ai-system-card.md).

**Treat retrieved content as untrusted input.** Documents, web pages, emails, and tickets that a system reads can contain instructions written to hijack it. This is prompt injection, and it turns Gate A into a security gate as well as a privacy one. Content the system reads is data, never commands.

---

## Gate B · Logic Guardrails (What Gets Reasoned Over)

The system prompt is a contract with the model. Treat it with the same rigor you would apply to any other operational contract.

**Hard bounds.** Every system prompt for Tier 2 and Tier 3 deployments states explicitly what the system must not do: no price negotiation, no contract modification, no commitment to timelines not sourced from a verified system of record, no medical or legal advice outside a defined scope.

**Grounding against verified sources.** High-stakes outputs must be drawn from, and traceable to, a controlled knowledge base, not the open internet and not the model's general memory. What the model can say is bounded by what you have verified. Where possible, the output cites the source it used, so a reviewer can check the claim instead of the tone.

**Structure over prose.** Where an output feeds a process, ask for structured output (fields, schemas, checklists) and validate it before it moves on. A malformed field fails loudly. A malformed paragraph fails quietly, three steps downstream.

**Prompt integrity audits.** System prompts are version-controlled and reviewed on a defined cadence (monthly for Tier 2, bi-weekly for Tier 3). A prompt that worked in January may behave differently after a model update in March. See [Evaluation and Drift](07-evaluation-and-drift.md).

**Know the limit of this gate.** A prompt is a request, not a lock. Instructions shape behavior; they do not guarantee it. Anything that must never happen is enforced by Gate C, in permissions and code, not by asking nicely in Gate B.

---

## Gate C · Reach (What It Can Touch) · *New in Version 2*

The gate agents earned. If Gate B governs what the system *intends*, Gate C governs what it is *able* to do, which is the only thing that matters when intent goes wrong.

**Least privilege, per task.** A system gets the narrowest set of tools, scopes, and data it needs for one defined job. A release-notes assistant needs read access to tickets. It does not need write access to the backlog, and it certainly does not need the CEO's inbox.

**Read before write.** Start every new deployment read-only. Grant write access only after the read-only version has passed its evals and someone has written down why the write is needed.

**Inherit permissions; never invent them.** A system acting for a user should see only what that user is allowed to see. A board that shows everyone the sum of what its builder can access is a data leak with a nice layout.

**Approval gates on consequential actions.** Binding or irreversible actions (paying, refunding, deleting, changing a record of truth, deploying, agreeing to terms) always require a human yes. Non-binding external actions, such as sending an informational answer from verified knowledge, may run autonomously at Tier 2, but only within a documented scope that has passed its evals.

**A register of every tool.** Every connector, API key, and tool an AI system can call is listed in the [Tool Permission Register](../templates/03-tool-permission-register.md): what it can do, why it is needed, who approved it, and when it is next reviewed.

The full treatment is in [Agents and Tool Permissions](04-agents-and-tool-permissions.md).

---

## Gate D · Human-in-the-Loop (What Goes Out)

The most important gate, and the one most organizations implement performatively rather than substantively.

**The 10% audit, risk-weighted.** At least ten percent of autonomous AI outputs are reviewed by a human, not for accuracy alone, but for tone, brand alignment, and the quality of judgment the system demonstrated. The reviewer is looking for the cases where the system was technically correct but humanly wrong. Ten percent is a starting point, not a law: sample more heavily where the stakes are higher, the topic is new, or the system just changed, and sample less where months of clean results have earned it.

**Review the review.** Track how long reviews take and how often reviewers disagree with the system. A reviewer who approves everything in four seconds is not a control. They are a signature.

**The 60-second kill switch.** Every AI agent has a centralized disable command reachable by a Designated Lead within 60 seconds. This is not a technical nice-to-have. It is the difference between an incident and a crisis. For agents, "disable" means revoking tool access and credentials, not only stopping the chat.

**Escalation paths.** Every customer-facing deployment has a defined escalation path to a human. The path is documented, tested quarterly, and known to the full support team. "The AI should handle it" is never an acceptable answer to "what happens when it can't?"

**Tell people they are talking to AI.** Where people interact with an AI system, they know it. In the EU this is now a legal obligation for many systems (see [Where the Rules Stand](09-where-the-rules-stand.md)); everywhere else it is simply part of keeping trust.

**Design the review screen.** The human gate is only as good as the interface it runs in. If reviewers cannot see the source next to the claim, they will check the claim against their memory. If approving is one click and rejecting is five, the system will be approved. The review interface is the control.

---

## Gate Weight by Tier

| Gate | Tier 1 | Tier 2 | Tier 3 |
|:--|:--|:--|:--|
| **A · Data** | Approved tools only; no customer data in consumer accounts | DPA, no training use, known retention, minimization | All of Tier 2, plus residency documented and Legal sign-off |
| **B · Logic** | Sensible prompt; owner aware of limits | Hard bounds, grounding, versioned prompts, monthly review | All of Tier 2, plus cited sources and bi-weekly review |
| **C · Reach** | Read-only or none | Least privilege, register; autonomous external actions only within a tested scope; binding actions approved | No autonomous consequential action; every one approved |
| **D · Human** | Spot checks | Risk-weighted sampling, kill switch, escalation path | Human approval on every consequential output; reviewer and decision logged |

---

> *Every gate is a question someone answered in advance,*
> *so that no one has to answer it in a panic.*

[Next: Agents and Tool Permissions →](04-agents-and-tool-permissions.md)
