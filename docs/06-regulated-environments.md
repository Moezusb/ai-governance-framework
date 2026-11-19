# 06 · Regulated Environments

> *In regulated work, the question is not whether the sentence is true.*
> *It is whether you can show how it came to exist.*

[← Builder Governance](05-builder-governance.md) · [Next: Evaluation and Drift →](07-evaluation-and-drift.md)

---

## Why This Gets Its Own Chapter

In most software, a wrong release note is an embarrassment. In clinical trial software, it can mean a site misunderstands how a data field behaves, a sponsor files a question with a regulator, and an auditor asks to see how the note was written, reviewed, and approved. In financial operations, a wrong reconciliation is not a typo. It is a control failure.

Regulated environments do not forbid AI. They ask the same question of AI that they ask of every other process: **is it controlled, documented, and attributable?** Teams that treat that question as a design input ship AI in regulated work faster than teams that treat it as an obstacle, because they only have to answer it once.

This chapter uses health and life sciences as its main example, because that is where the bar is highest. The patterns apply equally to financial services, insurance, and any work with an auditor.

---

## The Core Principle: AI Drafts, People Attest

In regulated work, an AI system can draft, assemble, check, and suggest. A named person reviews and attests. The signature, literally or figuratively, belongs to a human with the authority and the knowledge to give it.

This is not a limitation to be engineered away. It is the design. It is also where most of the value is: a subject matter expert who reviews a well-structured draft in five minutes, instead of writing it from scratch in two hours, is doing the part of the job only they can do.

---

## Six Controls That Survive an Audit

**1. Traceability to source.** Every AI-generated statement can be traced to the record it came from: the ticket key, the document version, the data extract. A release note line that cites its ticket is checkable. A line that does not is a claim.

**2. Compliant structure by template, not by hope.** Regulated formats are enforced by the template the AI fills, not by instructions asking it to "remember the format." Required sections, approved language, and mandatory disclaimers live in the structure, so a missing one is visible immediately.

**3. A review checklist with every draft.** Each AI output ships with its own checklist for the reviewer: what to verify, which claims carry the most risk, what changed since the last version. The checklist turns "please review" into a defined, repeatable control, and it gives the auditor something to look at.

**4. Attributable records.** Who generated the draft, with which tool and version, who reviewed it, what they changed, and when they approved it. Data integrity principles long used in life sciences (records that are attributable, legible, contemporaneous, original, and accurate, often shortened to ALCOA) apply to AI-assisted records exactly as they apply to any other.

**5. Validation proportional to risk.** An AI tool that drafts internal meeting notes does not need the validation package of a system that writes to a regulated record. Regulators have moved toward risk-based approaches to software assurance; use the [tier matrix](02-risk-classification.md) to decide how much evidence each tool needs, and keep that evidence.

**6. Documented method.** For analysis work (customer feedback studies, trend reviews, ticket analysis), document how the AI was used: what data went in, how it was grouped, what the human checked, and which conclusions are the human's. An analysis with a written method can be reviewed by an auditor. An analysis without one can only be trusted or not.

---

## The Audit Question

Before any AI-assisted output enters a regulated process, its owner should be able to answer this, out loud, to a stranger:

> *"Show me how this sentence came to exist."*

That means: the source records, the tool and version that drafted it, the prompt or template it used, the person who reviewed it, what they changed, and when they approved it. If the answer takes a week to assemble, the process is not ready. If it takes five minutes, you have built something an auditor will respect.

---

## Speed Under Controls

A common belief is that controls slow AI down. In practice the opposite tends to happen. A manual process that takes anywhere from fifteen minutes to two hours per release, with formatting done by hand and compliance checked by memory, can become a process that produces a structured, traceable, checklist-ready draft in minutes. The speed does not come from skipping the controls. It comes from building them into the structure, so the expert's time goes to judgment instead of formatting.

That is the argument to bring to a quality or compliance team: not "let us use AI despite the rules," but "let us use AI to make following the rules cheaper." (See [Field Patterns](10-field-patterns.md).)

---

## Working With Quality, Compliance, and Legal

- **Bring them in at the intake, not at launch.** The [Use Case Intake](../templates/01-use-case-intake.md) is the right moment. A quality lead who helped shape the review checklist will defend it in an audit.
- **Speak their language.** Controls, evidence, attribution, change control, deviation. Not "guardrails" and "vibes."
- **Show the failure modes.** Share your eval results, including the failures. Honesty about where the system is weak is what earns the right to use it where it is strong.
- **Agree on what "changed" means.** A new model version, a prompt edit, or a template change may each trigger re-review. Decide in advance which changes need sign-off. (See [Evaluation and Drift](07-evaluation-and-drift.md).)

---

## Where the Rules Point

Health and life sciences regulators have spent 2025 and 2026 publishing principles rather than prohibitions. In the United States, the FDA's January 2025 draft guidance on AI to support regulatory decision-making for drugs and biologics proposes a risk-based credibility assessment built around the model's *context of use*. In January 2026 the FDA and the European Medicines Agency published joint guiding principles of good AI practice in drug development. In the EU, high-risk obligations for AI embedded in regulated products, including medical devices, now apply from August 2028. The direction is consistent: define the context of use, match evidence to risk, keep humans accountable. Details and sources are in [Where the Rules Stand](09-where-the-rules-stand.md).

---

> *Compliance is the memory of every mistake an industry decided not to repeat.*
> *Let the AI carry the paperwork. Let the people carry the judgment.*

[Next: Evaluation and Drift →](07-evaluation-and-drift.md)
