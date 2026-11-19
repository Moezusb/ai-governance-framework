# ⚖️ AI Governance Framework
**An operator's playbook for deploying AI that answers, decides, and acts**

*Version 2.0 · November 2026 · [Try the tier classifier](https://moezusb.github.io/ai-governance-framework/)*

> *Speed is a promise you make to the business.*
> *Governance is how you keep it.*

---

## Why Most AI Governance Fails Before It Starts

Most companies approach AI governance the wrong way around. They deploy first, then write the policy to cover what they have already built. The result is a framework that describes the past and governs nothing going forward.

There is a second failure mode, subtler and more dangerous: governance written by people who have never been in the room when something goes wrong. Frameworks full of the right vocabulary ("human-in-the-loop," "hallucination mitigation," "responsible AI") but with no felt sense of what it actually costs when an AI agent makes a confident, wrong commitment to a $200k enterprise account at 11pm on a Friday.

And now there is a third. Most governance was written for AI that *talks*. The AI arriving in 2026 *acts*. It opens tickets, updates records, sends emails, and calls other systems through connectors nobody on the governance committee has read. A framework that only reviews what the model says, and never what it can touch, is guarding the front door of a house with no walls.

This framework is written from deployment experience, not from first principles. It assumes you are trying to move fast without breaking trust, and that those two things are not actually in conflict if you build the right structure underneath them.

---

## What Changed Since Version 1

Version 1 was a single page about customer-facing AI in B2B SaaS. It still holds. It was also written before three things became ordinary:

1. **AI that acts.** Agents with tools, connectors, and write access. Risk is no longer only about what the model says. It is about what the model can do. → [Agents and Tool Permissions](docs/04-agents-and-tool-permissions.md)
2. **AI that operators build themselves.** The fastest-growing category of AI in most companies is not a vendor product. It is the project, assistant, or board an operations or product person built on a Tuesday afternoon, which twenty colleagues depend on by Friday. → [Builder Governance](docs/05-builder-governance.md)
3. **AI inside regulated work.** Clinical trial software, financial operations, anything with an auditor. Here the question is not "is the output good?" but "can you show how this sentence came to exist?" → [Regulated Environments](docs/06-regulated-environments.md)

The rules moved too. The EU delayed its high-risk obligations, Canada dropped its AI bill in favour of a strategy and a privacy bill, and ISO 42001 started showing up in procurement questionnaires. → [Where the Rules Stand](docs/09-where-the-rules-stand.md)

The full list of changes is in the [Changelog](CHANGELOG.md).

---

## The Framework on One Page

**1. Trust is the asset.** Not data. Not legal liability. Not uptime. Every control in this framework exists to keep you the kind of company your customers would defend if something went wrong. → [Trust and the Human Factor](docs/01-trust-and-the-human-factor.md)

**2. Classify on two axes, not one.** *Consequence:* if this system produces a confident wrong answer, what does it cost the person on the other end? *Agency:* what can the system do without asking first? A system that drafts is not a system that sends, even when the words are identical. → [Risk Classification](docs/02-risk-classification.md)

| Tier | Name | Typical example | Oversight model |
|:--|:--|:--|:--|
| **Tier 1** | Contained | Internal drafting, summarization, research | Named owner, registration, spot sampling |
| **Tier 2** | Supervised | Support automation, reversible internal actions | Daily sampling, guardrails, eval set, named Incident Owner, kill switch |
| **Tier 3** | Accountable | Commitments, regulated records, decisions about people, irreversible actions | Human approval on every consequential output or action, full audit trail |

**3. Pass four gates.** What goes in (data). What gets reasoned over (logic and grounding). What it can reach (tools and actions). What goes out (human review). Version 1 had three gates. Agents earned the fourth. → [The Four Gates](docs/03-the-four-gates.md)

**4. Measure before and after you ship.** An eval set before launch, monitoring after, and a re-test every time the model, the prompt, the knowledge, or the tools change. A system that passed in January has not passed in March. → [Evaluation and Drift](docs/07-evaluation-and-drift.md)

**5. When it breaks, respond in a way that builds trust.** Contain, Trace, Communicate, Harden, Review. And remember that a prompt is a request, not a lock. → [Incident Response](docs/08-incident-response.md)

---

## How to Use This

**If you have five minutes:** open the [tier classifier](https://moezusb.github.io/ai-governance-framework/), answer six questions about one AI use case, and copy the summary it gives you.

**If you have an hour:** fill in the [Use Case Intake](templates/01-use-case-intake.md) for one real deployment. The first question, "what problem does this solve?", will do more governance work than any policy you write this quarter.

**If you are building the program:** read the chapters in order, then adopt the templates. They are deliberately short. A form nobody fills in governs nothing.

---

## What's Inside

| | Chapter | The question it answers |
|:--|:--|:--|
| 01 | [Trust and the Human Factor](docs/01-trust-and-the-human-factor.md) | What are we protecting, and which human instincts work against us? |
| 02 | [Risk Classification](docs/02-risk-classification.md) | How much oversight does this use case deserve? |
| 03 | [The Four Gates](docs/03-the-four-gates.md) | What controls stand between the model and the world? |
| 04 | [Agents and Tool Permissions](docs/04-agents-and-tool-permissions.md) | What changes when AI can act, not just answer? |
| 05 | [Builder Governance](docs/05-builder-governance.md) | Who governs the AI we build for ourselves? |
| 06 | [Regulated Environments](docs/06-regulated-environments.md) | How do AI outputs survive an audit? |
| 07 | [Evaluation and Drift](docs/07-evaluation-and-drift.md) | How do we know it works, and keeps working? |
| 08 | [Incident Response](docs/08-incident-response.md) | What happens in the first hour after it goes wrong? |
| 09 | [Where the Rules Stand](docs/09-where-the-rules-stand.md) | What do the EU, Canada, the US, and the standards bodies expect, as of November 2026? |
| 10 | [Field Patterns](docs/10-field-patterns.md) | What did this look like in real deployments? |

**Templates**

| Template | Use it when |
|:--|:--|
| [Use Case Intake](templates/01-use-case-intake.md) | Before a single prompt is written |
| [AI System Card](templates/02-ai-system-card.md) | Before go-live, for Tier 2 and Tier 3 |
| [Tool Permission Register](templates/03-tool-permission-register.md) | Any time an AI system gets a tool or connector |
| [Builder Tool Registration](templates/04-builder-tool-registration.md) | An operator-built tool gets its second user |
| [Prompt and Model Change Log](templates/05-prompt-and-model-change-log.md) | Every change to a prompt, model, knowledge base, or tool |
| [Launch Readiness Checklist](templates/06-launch-readiness-checklist.md) | The week before go-live |
| [Incident Report](templates/07-incident-report.md) | Within 48 hours of any Sev 1 or Sev 2 incident |

---

## What Governance Actually Unlocks

Framing governance as a constraint on AI deployment misses the strategic point entirely.

A codified safety floor is what allows you to move faster than competitors who are deploying without one. When your CEO asks "can we automate this?" your answer is not "let me check with Legal." Your answer is "yes, here is how we would do it safely, here is the tier it falls into, here is the oversight model." That speed, the ability to say yes with confidence, is what governance is actually for.

Three compounding returns:

**Trust as a market position.** Enterprise buyers now ask about AI governance in procurement, and certification against ISO/IEC 42001 is starting to appear as a vendor requirement. A documented, practiced framework signals the organizational maturity that enterprise contracts require.

**Defensibility.** When an AI system makes an error, and it will, the question your legal team and your auditors will ask is: "what did you have in place?" A version-controlled framework with a documented incident history is a very different answer than "we were following best practices."

**Deployment velocity.** Counterintuitively, governance accelerates deployment. When the safety structure is established and understood, new use cases move through approval faster because the questions have already been answered at the framework level.

---

## A Note on Scope and Honesty

This is an operator's framework. I am not a lawyer, a clinician, or a security engineer, and nothing here is legal advice. It is what I have learned taking AI from business case to production in B2B SaaS and in regulated clinical trial software, written so that the next person does not have to learn it at 11pm on a Friday. The field patterns are drawn from that work, generalized and anonymized, with numbers rounded.

---

**Author:** Mohamed Bah | [LinkedIn](https://www.linkedin.com/in/bah-007700/) | [Portfolio](https://moezusb.github.io)
**Informed by:** Deployment experience, Cialdini's influence research, behavioral operations, NIST AI RMF, ISO/IEC 42001, the OWASP Top 10 for Agentic Applications
**Status:** Living document. Governance that does not evolve is governance that has already failed.

> *Build the floor before you dance on it.*
