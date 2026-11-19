# Launch Readiness Checklist

*The week before go-live. Every unchecked box is either fixed or written down as an accepted risk, with a name next to it.*

[Framework: README](../README.md)

---

**System:** ____________ **Tier:** ____ **Planned go-live:** ____________

## Foundations (all tiers)

- ☐ [Use Case Intake](01-use-case-intake.md) approved, with a problem statement that does not mention AI
- ☐ Tier confirmed with the [tier matrix](../docs/02-risk-classification.md)
- ☐ Named owner
- ☐ Only approved AI tools and accounts in use

## Gate A · Data (Tier 2 and 3)

- ☐ DPA in place; training on our data excluded; retention window known
- ☐ Inputs minimized to what the task needs
- ☐ Processing region recorded (required for regulated customers)

## Gate B · Logic (Tier 2 and 3)

- ☐ Hard bounds written, and each "must never" enforced by something stronger than the prompt
- ☐ Grounded in a controlled knowledge source; sources cited where possible
- ☐ Prompt and model version under version control

## Gate C · Reach (any system with tools)

- ☐ [Tool Permission Register](03-tool-permission-register.md) complete; least privilege confirmed
- ☐ Permissions inherited from the user, or a dedicated agent identity
- ☐ Approvals configured for binding actions and changes to records of truth
- ☐ Combination check done

## Gate D · Human (Tier 2 and 3)

- ☐ Review model in place (sampling rate, or approval on every output for Tier 3)
- ☐ Review screen shows the source next to the claim
- ☐ Escalation path documented, tested, and known to the team
- ☐ Kill switch tested within 60 seconds by the Designated Lead
- ☐ Users told they are interacting with AI, where they are

## Evaluation (Tier 2 and 3)

- ☐ Golden set built, including must-never-fail and should-escalate cases
- ☐ Pass criteria written before results were seen, and met
- ☐ Shadow or pilot phase complete
- ☐ Monitoring metrics live, each efficiency metric paired with a quality metric

## Accountability (Tier 2 and 3)

- ☐ [AI System Card](02-ai-system-card.md) complete
- ☐ Incident Owner named and briefed
- ☐ Severity levels agreed ([Incident Response](../docs/08-incident-response.md))
- ☐ Logs capture inputs, outputs, actions, and reviewer

## Tier 3 Only

- ☐ Legal or Compliance sign-off
- ☐ Validation evidence filed, proportional to risk
- ☐ Audit question answered: "show me how this output came to exist," in under five minutes
- ☐ Tabletop incident exercise completed
- ☐ Accountable executive named

---

**Go / No-go:** ☐ Go ☐ Go with accepted risks (listed below) ☐ No-go

| Accepted risk | Owner | Review by |
|:--|:--|:--|
| | | |

**Signed / date:**
