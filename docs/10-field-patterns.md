# 10 · Field Patterns

> *Frameworks are written at desks.*
> *These were learned on the floor.*

[← Where the Rules Stand](09-where-the-rules-stand.md) · [Back to README](../README.md)

---

These are patterns from AI deployments I led or worked on in B2B SaaS and in regulated clinical trial software. They are generalized and anonymized: no employers, customers, or internal systems are named, and numbers are rounded. Each pattern shows where it sits in the framework, what worked, and the lesson that changed how I govern.

---

## Pattern 1 · Customer Support Automation, Business Case to Production

**Setting:** a B2B SaaS company serving enterprise customers, with a support team handling a high volume of repeat questions.

**What was built:** an AI support agent answering customer questions from a curated knowledge base, with escalation to human agents.

**Where it sits:** Consequence C2 (customer-facing), Agency A3 (sends answers directly). **Tier 2 · autonomous**, which meant the scope had to be proven before the agent was trusted with it. That shaped the rollout: a written business case and ROI model first, an evaluation framework with defined pass criteria, a controlled pilot, acceptance testing, and only then a staged production rollout with human-in-the-loop controls, sampling, and escalation to people for anything outside its proven scope.

**What happened:** roughly two-thirds of conversations came to be resolved without a human, returning well over a hundred hours of work to the team each month.

**The lesson:** *the escalation path was the product.* The moments that protected trust were not the answers the agent gave, but the clean, fast handoffs when it should not answer. We spent as much design time on "when to stop" as on "what to say," and the quality metrics that mattered most were reopen rates and satisfaction on AI-handled conversations, not the resolution rate on the dashboard.

**Framework links:** [Risk Classification](02-risk-classification.md) · [Gate D](03-the-four-gates.md#gate-d--human-in-the-loop-what-goes-out) · [Evaluation and Drift](07-evaluation-and-drift.md)

---

## Pattern 2 · Release Notes in Regulated Software

**Setting:** a clinical trial technology company shipping software under compliance controls, where release documentation is reviewed by quality teams and can be examined in audits.

**What was built:** an AI workflow, built by an operator rather than engineering, that turns a release's ticket data into three outputs: a draft referencing every source ticket, a customer-ready version in the approved compliant format, and a review checklist for the subject matter expert. A companion workflow prepares help center articles so they can go live with each release.

**Where it sits:** Consequence C2, Agency A1 (reads tickets; a human edits and publishes). The regulated-output modifier raises it to **Tier 3**: every note is reviewed and approved by a named expert before publication.

**What happened:** a manual process that took anywhere from fifteen minutes to over two hours per release came down to a few minutes for the draft, even for releases spanning hundreds of tickets. That made a new standard practical: no release ships without live notes.

**The lesson:** *the speed came from the structure, not the model.* Traceability to ticket keys, a template that enforced the compliant format, and a checklist that told the reviewer exactly what to verify did more for quality than any instruction in the prompt. And because the controls were built in, the compliance case was easier to make, not harder.

**Framework links:** [Regulated Environments](06-regulated-environments.md) · [Builder Governance](05-builder-governance.md)

---

## Pattern 3 · The Operator-Built Board

**Setting:** the same product organization, where release status lived across several systems and weekly planning meetings were spent assembling the picture.

**What was built:** an AI-assisted release board consolidating status, remaining work, risks, and key freeze dates into one view, built by an operator and respecting the viewer's existing permissions.

**Where it sits:** Consequence C2 (informs leadership decisions), Agency A1. **Tier 2:** an internal planning view, not a regulated record. It began as a personal tool and moved through the [builder lifecycle](05-builder-governance.md#the-lifecycle-of-a-builder-tool) quickly: within weeks it was used by around two dozen people in weekly release planning, and those meetings got noticeably shorter.

**The lesson:** *permissions were inherited, never invented.* The board only showed each person what they could already see in the source systems. That single design decision is what made it safe to share widely. The second lesson came with adoption: once a team plans around a tool, it needs a how-to, a backup owner, and a clear statement that the source systems remain the truth.

**Framework links:** [Builder Governance](05-builder-governance.md) · [Gate C](03-the-four-gates.md#gate-c--reach-what-it-can-touch--new-in-version-2)

---

## Pattern 4 · Voice of the Customer at Scale

**Setting:** several years of customer satisfaction responses and support tickets that had accumulated faster than anyone could read them.

**What was built:** an AI-assisted analysis to group feedback into themes, quantify the largest pain points, and surface patterns nobody had acted on.

**Where it sits:** Consequence C2 (shapes priorities), Agency A0. **Tier 2.** Because it fed product decisions in a regulated company, the method was documented to the standard an auditor would expect.

**What happened:** the analysis quantified the two biggest pain points and surfaced an unaddressed support pattern that leadership then fixed. The work was later reviewed favourably during a compliance audit.

**The lesson:** *document the method, and keep the conclusions human.* The AI did the sorting at a scale no person could. The judgment about what mattered, and what to recommend, stayed with people. Because how the AI was used was written down (inputs, grouping, what the human checked), the work could stand up to an auditor's questions.

**Framework links:** [Regulated Environments](06-regulated-environments.md#six-controls-that-survive-an-audit) · [Trust and the Human Factor](01-trust-and-the-human-factor.md#the-metric-trap)

---

## Pattern 5 · Discovery for an AI Product

**Setting:** an AI product that extracts clinical data from documents for expert users to review.

**What was done:** interviews with expert users about how they actually verify extracted data, turned into a specification for the engineering team.

**Where it sits:** this is governance at design time, before any tier is assigned. The product's oversight model depends on how well a human can check its work.

**What happened:** the findings reshaped the data review interface.

**The lesson:** *the review interface is the control.* Human-in-the-loop is only as strong as the screen the human works in. If the source is not next to the extracted value, reviewers check against memory. If accepting is easier than correcting, the system gets accepted. Governing AI products means sitting with the people who review the output, and designing for how they really work.

**Framework links:** [Gate D](03-the-four-gates.md#gate-d--human-in-the-loop-what-goes-out) · [Trust and the Human Factor](01-trust-and-the-human-factor.md)

---

## What the Patterns Share

Five settings, one thread: **the controls that worked were structural.** An escalation path, a template, a checklist, inherited permissions, a review screen. None of them depended on the model behaving perfectly. All of them made it obvious, quickly, when it did not.

> *Trust the structure you can see.*
> *Verify the model you cannot.*

[Back to README](../README.md)
