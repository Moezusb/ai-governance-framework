# 08 · Incident Response

> *Something will go wrong.*
> *The only question you still control is what you do in the first hour.*

[← Evaluation and Drift](07-evaluation-and-drift.md) · [Next: Where the Rules Stand →](09-where-the-rules-stand.md)

---

## The Goal

And something will go wrong. The goal is not to prevent all AI errors; that is not achievable. The goal is to respond in a way that reinforces rather than destroys trust.

Customers forgive mistakes far more readily than they forgive silence, spin, or the same mistake twice.

---

## Severity Levels

Agree on these before go-live, so nobody debates definitions during the incident.

| Severity | Definition | Example | Response |
|:--|:--|:--|:--|
| **Sev 1** | Binding harm: a commitment made, money moved, data exposed, a regulated record affected, or many customers affected | Agent issues unauthorized refunds; customer data appears in another customer's answer | Kill switch immediately; Incident Owner leads; Legal and leadership informed within the hour |
| **Sev 2** | Customer-facing error with real impact, contained to a few customers | Wrong policy information sent to several enterprise accounts | Suspend the affected capability; Incident Owner leads; customers contacted |
| **Sev 3** | Error caught before it caused harm, or with minimal impact | Reviewer catches a pattern of incorrect citations in sampling | Fix and log; reviewed at the next cadence meeting |
| **Sev 4** | Quality issue or near miss | Tone off-brand in a handful of internal drafts | Log; add to golden set |

An [Incident Report](../templates/07-incident-report.md) is written within 48 hours for anything at Sev 1 or Sev 2.

---

## The Five Steps

**1. Contain.** Suspend the specific agent, capability, or API key. For agents, revoke credentials and cancel queued actions, not only the conversation. Scope the blast radius before doing anything else: which customers, which records, which actions, since when.

**2. Trace.** Reconstruct the full chain that produced the error: inputs, retrieved content, prompt version, model version, tools called, and outputs. Not to assign blame, but to understand the system's behavior precisely enough to prevent recurrence. This step is only possible if the logging required by your tier was in place before the incident. You cannot trace what you did not record.

**3. Communicate.** Transparent, prompt disclosure to affected customers, usually through Customer Success. The framing matters: "here is what happened, here is what we have done, here is what we are changing." Customers who receive that communication promptly and honestly are more likely to trust you after an incident than before it. Where regulators or contractual notice periods apply, Legal sets the clock.

**4. Harden.** Fix the cause at the strongest available layer. Version 1 of this framework said to update the system prompt with a negative constraint. That is still worth doing, and it is no longer enough on its own. A prompt is a request, not a lock. Prefer, in order:
   - **Remove the capability.** If the agent should never have been able to do it, take the tool away.
   - **Enforce in code or permissions.** Validation, scopes, approval gates.
   - **Change the structure.** Templates, required fields, review checklists.
   - **Then** add the instruction to the prompt, and the case to the golden set, so the evals catch it next time.

   Document the incident, the root cause, and the change made. This documentation is your institutional memory.

**5. Review.** Every Sev 1 and Sev 2 incident triggers a cross-functional review: Operations, Engineering, Customer Success, and Legal or Compliance where applicable. The review is not a post-mortem for its own sake. It is the mechanism by which your governance framework learns. The question that ends every review: *does this incident change the tier, the gates, or the framework itself?*

---

## Undo Is a Feature

For agents, ask during design, not during the incident: **for each action this system can take, how do we undo it?** A drafted ticket can be deleted. A changed record can be restored from history if history is kept. A sent email cannot be unsent; it can only be followed by a better one. Actions without an undo path belong on the top rungs of the [action ladder](04-agents-and-tool-permissions.md#the-action-ladder), behind a human approval.

---

## Practice Before You Need It

Run a tabletop exercise before every Tier 3 launch and once a year for every Tier 2 system: a realistic scenario, the real Incident Owner, a clock. Time the kill switch. Draft the customer message. Find out which log you forgot to keep while it is still a drill.

---

> *An incident is the framework asking you a question in public.*
> *Answer it honestly, and it becomes the reason people trust you.*

[Next: Where the Rules Stand →](09-where-the-rules-stand.md)
