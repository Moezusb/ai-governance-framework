# 07 · Evaluation and Drift

> *It passed in January.*
> *The model changed in March. Nobody told the test.*

[← Regulated Environments](06-regulated-environments.md) · [Next: Incident Response →](08-incident-response.md)

---

## Two Questions, Asked Forever

Every AI deployment has to answer two questions, and neither is ever answered for good:

1. **Does it work?** Before launch, against criteria written before anyone saw the output.
2. **Does it still work?** After launch, every time something underneath it changes.

Most teams answer the first question with a demo. Demos are designed to succeed. Evaluations are designed to find out.

---

## Before Launch: Build the Eval Set

**Start from the problem statement.** The [Use Case Intake](../templates/01-use-case-intake.md) says what problem the system solves. The evaluation tests exactly that, and defines in advance what "good enough to launch" means. Write the pass criteria before you look at a single output, or you will move the bar to wherever the system landed.

**Build a golden set.** A collection of real, representative cases with known good answers, typically somewhere between fifty and a few hundred. Include:
- **The common cases**, in proportion to how often they happen.
- **The hard cases**, the ones experienced staff find tricky.
- **The cases that must never go wrong**, even if they are rare: the refund request, the legal threat, the regulated claim.
- **The cases it should refuse or escalate.** A system that answers everything confidently has failed the test, even if many answers are right.

**Score what matters.** Accuracy, yes. Also: did it cite the right source, did it stay in scope, did it escalate when it should have, was the tone right? A scoring rubric with three to five criteria, applied by a human, beats a single "looks good."

**Roll out in steps.**

| Step | What happens | Exit criteria |
|:--|:--|:--|
| **Shadow** | System runs on real inputs; outputs are logged but not used | Meets pass criteria on the golden set and on shadow traffic |
| **Pilot** | Small, defined slice of real work, with full human review | Quality holds; reviewers trust the review process |
| **Staged rollout** | Expanding share of real work, with tier-level sampling | Metrics stable at each stage |
| **Production** | Full scope, with ongoing monitoring | Reviewed on the tier cadence |

Acceptance testing in this sense is not a ceremony. It is the moment someone with authority signs that the system does what the business case said it would.

---

## After Launch: Five Sources of Drift

A deployed AI system can change behavior without anyone touching it. Know the five ways:

| Source | What happens | Control |
|:--|:--|:--|
| **Model updates** | The provider ships a new version, or retires the one you use | Pin model versions where the provider allows it; re-run the golden set before switching; track deprecation dates |
| **Prompt edits** | Someone "just tweaks" the instructions | Version control and the [change log](../templates/05-prompt-and-model-change-log.md); re-run evals on every edit |
| **Knowledge changes** | The help center, policy documents, or source data the system draws from are updated | Treat knowledge base changes as system changes for Tier 2 and Tier 3 |
| **Tool changes** | A connector adds tools, changes behavior, or updates its permissions | Pin connector versions; review the [Tool Permission Register](../templates/03-tool-permission-register.md) on change |
| **Input shift** | Customers start asking new kinds of questions: a new product, a new market, a new crisis | Monitor topic mix and escalation rates; add new case types to the golden set |

The rule that covers all five: **any change underneath the system is a change to the system.** Re-test before it reaches production, not after a customer notices.

---

## What to Monitor

Pair every efficiency signal with a quality signal that would move the other way if the system were gaming the first. (The reasoning is in [Trust and the Human Factor](01-trust-and-the-human-factor.md).)

| Efficiency signal | Paired quality signal |
|:--|:--|
| Autonomous resolution rate | Reopen rate; CSAT on AI-handled conversations; escalation after "resolution" |
| Time saved | Error rate found in sampled review; downstream rework |
| Volume handled | Share of outputs that cite a verified source |
| Escalation rate going down | Spot check of conversations that were *not* escalated |

Watch the trend, not the snapshot. A slow decline in quality over twelve weeks is the hardest failure to see and the most common one to have.

---

## Retirement Is Part of the Lifecycle

Models get deprecated. Use cases end. Builders move on. Every Tier 2 and Tier 3 system has a planned review at which someone decides, explicitly, to keep, change, or retire it. A system nobody decided to keep is a system nobody is watching.

---

> *Measure the thing the customer feels.*
> *Then measure it again next month, because the ground moved.*

[Next: Incident Response →](08-incident-response.md)
