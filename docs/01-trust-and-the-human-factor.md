# 01 · Trust and the Human Factor

> *Trust arrives on foot and leaves on horseback,* as the Dutch proverb goes.
> *Build for the walk back.*

[← Back to README](../README.md) · [Next: Risk Classification →](02-risk-classification.md)

---

## The Foundational Insight: Trust Is the Asset

Before risk matrices and safety gates, one framing question:

**What is the actual thing you are protecting?**

Not data. Not legal liability. Not uptime.

**Trust.**

Enterprise B2B runs on trust. Your customers have handed you their workflows, their data, and in many cases their ability to serve their own customers. When AI enters that chain, the question is not "how do we avoid a bad outcome?" The question is "how do we remain the kind of company our customers would defend if something goes wrong?"

That distinction changes everything about how you build. A company optimizing to avoid liability writes policies that protect itself. A company optimizing to maintain trust writes policies that protect the customer, and earns the loyalty that makes it genuinely defensible.

In regulated work the chain is longer. A clinical trial sponsor trusts its software vendor; a regulator trusts the sponsor's records; a patient trusts all of them without ever seeing any of them. Every AI output that touches that chain borrows against trust that belongs to people who were never asked.

---

## The Human Psychology You Are Actually Managing

Governance frameworks that ignore behavioral dynamics fail in practice. These are the forces that matter most in AI deployment environments. The first three were in version 1. The last three became impossible to ignore once AI moved into everyday work.

**Automation bias.** People systematically overtrust automated outputs. Once a system is running, the human reviewers, who were hired to catch errors, begin deferring to it. This is not laziness. It is a documented cognitive pattern. Your oversight process must be designed with this in mind, not against it. Rotating reviewers, blind sampling, and explicit "challenge the output" protocols all counteract automation bias structurally.

**Social proof as a deployment driver.** Teams deploy AI because competitors are deploying AI. This is Cialdini's social proof principle operating at the organizational level, and it produces the most dangerous category of AI deployment: the one where nobody in the room has clearly articulated what problem it solves. Every deployment in this framework requires a written problem statement before a single prompt is written.

**The bystander effect in incident response.** When an AI system produces a bad output, the natural organizational response is to wait: for someone with more authority to decide, for more information to arrive, for the situation to clarify. This is the bystander effect transposed into operations. It is why this framework mandates a named, single Incident Owner for every Tier 2 and Tier 3 deployment before go-live. Diffused responsibility in AI incidents is how small errors become crises.

**Fluency mistaken for accuracy.** A language model's worst answers are delivered in the same calm, well-formatted voice as its best ones. Humans read confidence from tone, and AI has perfect tone. The practical consequence: reviewers must check claims against sources, not against how sure the answer sounds. Every review checklist in this framework asks "where did this come from?" before it asks "does this look right?"

**Approval fatigue.** Agents ask for permission. The first ten requests get read. The hundredth gets clicked. An approval step that fires on every trivial action trains people to approve without looking, which is worse than no approval at all, because it creates a record that someone checked. Approvals must be rare enough to be real: reserve them for consequential, irreversible, or external actions, and let the low-stakes ones through on policy. (See [Agents and Tool Permissions](04-agents-and-tool-permissions.md).)

**Skill fade.** When the AI drafts every release note, triages every ticket, and answers every routine question, the humans who once did that work slowly lose the ability to tell good from bad. The reviewer you are relying on in year two is not the expert you had in year one. Keep humans doing a portion of the work by hand, rotate review duties, and treat "could we still do this if the system went down tomorrow?" as a standing question in quarterly reviews.

---

## The Metric Trap

One more force deserves its own heading, because it hides inside every AI success story.

When a measure becomes a target, it stops being a good measure. An AI support agent rewarded for resolution rate will learn, through whoever tunes it, to close conversations that should have been escalated. A drafting tool measured on minutes saved will be praised for speed while quietly shipping errors downstream to someone else's queue.

The defence is to pair every efficiency metric with a quality metric that would move in the opposite direction if the system were gaming the first one:

| If you measure... | Also measure... |
|:--|:--|
| Autonomous resolution rate | Reopen rate, escalation-after-resolution, CSAT on AI-handled conversations |
| Time saved per task | Error rate found in review, downstream rework |
| Adoption (number of users) | Number of users who still check the output |
| Approvals completed | Time spent per approval (too fast is a signal) |

Measure what the customer feels, not just what the dashboard counts.

---

> *The model does not know whose trust it is spending.*
> *You do. Write it down.*

[Next: Risk Classification →](02-risk-classification.md)
