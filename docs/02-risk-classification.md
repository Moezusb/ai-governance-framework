# 02 · Risk Classification

> *Not every door needs a guard.*
> *Know which ones open onto the street.*

[← Trust and the Human Factor](01-trust-and-the-human-factor.md) · [Next: The Four Gates →](03-the-four-gates.md)

---

## Why Tiers at All

Not all AI deployments carry the same exposure. Governance overhead should match actual risk. Over-governing low-stakes use cases burns the credibility you need for the conversations that matter, and teaches people that the governance process is something to route around.

Version 1 classified on a single question: *if this system produces a confident wrong answer, what is the worst-case outcome for the customer?* That question still anchors everything. But it was written for AI that answers. For AI that acts, a second question carries as much weight.

---

## Axis 1 · Consequence: What a Wrong Answer Costs

**The question:** "If this system produces a confident wrong answer, what is the worst-case outcome for the person on the other end?"

| Level | Name | What it means | Examples |
|:--|:--|:--|:--|
| **C1** | Contained | Internal, reversible, and a person reads it before it matters | Meeting summaries, first drafts, internal research, code suggestions in review |
| **C2** | Exposed | Reaches customers or the public, or informs a decision someone will act on | Support answers, help center articles, release notes, sales follow-ups, internal reports leadership acts on |
| **C3** | Binding | Creates or changes an obligation, a record of truth, or a significant decision about a person | Pricing, contracts, refunds, legal or compliance statements, clinical or regulated records, hiring, eligibility, access, credit |

If the honest answer involves money, legal exposure, health, someone's livelihood, or significant operational disruption for the customer, it is C3 regardless of how simple the underlying task looks. A one-line answer about a refund policy is a commitment.

---

## Axis 2 · Agency: What It Can Do Without Asking

**The question:** "What can this system do in the world before a human says yes?"

| Level | Name | What it means | Examples |
|:--|:--|:--|:--|
| **A0** | Advise | Produces text or analysis; a human takes every action | A chat assistant, a drafting project, an analysis notebook |
| **A1** | Read | Retrieves from systems through tools or connectors, read-only | Searching tickets, querying a database, reading a calendar |
| **A2** | Act, reversibly | Writes inside your own systems in ways that can be undone | Creating draft tickets, tagging records, posting to an internal channel, updating a board |
| **A3** | Act, irreversibly or externally | Takes actions that leave the building or cannot be cleanly undone | Sending email to customers, issuing refunds, deleting data, deploying code, publishing, changing a record of truth |

The principle behind this axis: **a system that drafts is not a system that sends, even when the words are identical.** The same paragraph is a C2/A0 risk in a draft and a C2/A3 risk in an outbox.

---

## The Tier Matrix

| | **A0** Advise | **A1** Read | **A2** Act, reversibly | **A3** Act, irreversibly or externally |
|:--|:--|:--|:--|:--|
| **C1** Contained | Tier 1 | Tier 1 | Tier 2 | Tier 2 |
| **C2** Exposed | Tier 2 | Tier 2 | Tier 2 | Tier 2 · autonomous, tested scope required |
| **C3** Binding | Tier 3 | Tier 3 | Tier 3 | Tier 3 · no autonomous action |

In words: **consequence sets the floor, agency raises it, and binding consequence plus autonomous action is a design you do not ship.**

- A contained system moves from Tier 1 to Tier 2 the moment it can act. A summarizer is not an agent, even if it reads the same tickets.
- An exposed system is Tier 2 whether it drafts or sends, but sending changes which controls apply. A drafting assistant needs reviewers who do not rubber-stamp. An autonomous one needs a tested scope, an escalation path, disclosure, and a kill switch. (See [the action ladder](04-agents-and-tool-permissions.md#the-action-ladder).)
- Read the bottom-right cell twice. A system that can make binding commitments *and* act on them without a human is not a higher tier. Break it into an AI that prepares the action and a human who takes it.

### Modifiers

Apply these after the matrix. Each can raise a tier; none can lower one.

| Modifier | Effect |
|:--|:--|
| **Sensitive data** (personal information, health data, financial account data, confidential customer data) | Minimum Tier 2 |
| **Regulated output** (the output enters a regulated process or record: clinical and life sciences documentation, financial reporting and controls, credit, insurance, employment, education) | Raise one tier, up to Tier 3 |
| **Decisions about people** (anything that affects someone's access, eligibility, employment, or treatment) | Tier 3 |
| **Operator-built, single reviewer** (the builder is also the only person checking outputs) | Minimum Tier 2 until a second reviewer exists. See [Builder Governance](05-builder-governance.md) |

---

## The Oversight Model for Each Tier

| | **Tier 1 · Contained** | **Tier 2 · Supervised** | **Tier 3 · Accountable** |
|:--|:--|:--|:--|
| **Owner** | Named owner | Named owner and named Incident Owner | Named owner, Incident Owner, and accountable executive |
| **Registration** | Lightweight entry in the AI register | [AI System Card](../templates/02-ai-system-card.md) | System Card plus sign-off from Legal or Compliance |
| **Before launch** | Problem statement | Eval set with pass criteria, pilot | Eval set, pilot, acceptance testing, validation record where regulated |
| **Human review** | Spot sampling, weekly | Daily sampling, risk-weighted (start at 10%) | Human approval before every consequential output or action |
| **Kill switch** | Owner can disable | Designated Lead can disable within 60 seconds | Designated Lead can disable within 60 seconds; tested before launch |
| **Change control** | Note changes | [Change log](../templates/05-prompt-and-model-change-log.md), re-run evals on change | Change log, re-run evals, second-person approval for every prompt or model change |
| **Review cadence** | Quarterly | Monthly | Bi-weekly |
| **Audit trail** | Not required | Inputs, outputs, and actions logged | Inputs, outputs, actions, reviewer, and decision logged and retained |

---

## Worked Examples

| Use case | Consequence | Agency | Modifiers | Tier |
|:--|:--|:--|:--|:--|
| Assistant summarizes new bug reports for a product manager | C1 | A0 | None | **Tier 1** |
| Agent reads the same bug reports and creates tagged draft tickets in the backlog | C1 | A2 | None | **Tier 2** |
| Support assistant drafts answers from a curated help center; an agent edits and sends | C2 | A1 | None | **Tier 2** |
| Support agent answers customers directly from a curated help center and escalates when unsure | C2 | A3 | None | **Tier 2 · autonomous** |
| The same support agent is given the ability to issue refunds | C3 | A3 | None | **Tier 3 · no autonomous action:** it prepares the refund, a person approves it |
| AI drafts release notes from ticket data for regulated software; a subject matter expert edits and publishes | C2 | A1 | Regulated output | **Tier 3** |
| AI screens job applications and ranks candidates | C3 | A1 | Decisions about people | **Tier 3** |

Three lessons hide in that table. First, the bug-report pair: the same input, one tier apart, on agency alone. Tiers are not only a label. They are a lever. Second, the support agent stays in Tier 2 until someone hands it money, and then the right answer is not a higher tier but a different design. Third, the release notes example lands in Tier 3 because of where it lives, not what it does. Regulated work earns its own chapter: [Regulated Environments](06-regulated-environments.md).

---

> *The question is never "is the model good?"*
> *It is "what happens on the day it isn't?"*

**Try it:** the [interactive tier classifier](https://moezusb.github.io/ai-governance-framework/) walks through both axes and the modifiers, and gives you a summary to paste into your intake form.

[Next: The Four Gates →](03-the-four-gates.md)
