# AI System Card

*Required before go-live for Tier 2 and Tier 3. One page that answers the questions an incident, an audit, or a new team member will ask. Keep it next to the system, and update it when the system changes.*

[Framework: The Four Gates](../docs/03-the-four-gates.md)

---

| | |
|:--|:--|
| **System name** | |
| **Version / date of this card** | |
| **Tier** | ☐ Tier 2 · Supervised ☐ Tier 2 · autonomous ☐ Tier 3 · Accountable |
| **Owner** | |
| **Incident Owner** | |
| **Designated Lead (kill switch)** | |
| **Intake form** | link |

---

## Purpose and Scope

**What it does (one job):**
>

**What it must never do:** (the hard bounds in its instructions, and how each is enforced)

| Must never | Enforced by (permission, code, template, prompt) |
|:--|:--|
| | |

**Who uses it, who is affected:**
>

**Disclosure:** how people know they are interacting with AI
>

---

## Gate A · Data

| Question | Answer |
|:--|:--|
| Data sent to the model | |
| Personal or sensitive data? | |
| Provider and product | |
| DPA in place? | |
| Training on our data excluded? | |
| Retention window | |
| Processing region | |

## Gate B · Logic

| Question | Answer |
|:--|:--|
| Model and version (pinned?) | |
| Prompt / instructions location and version | |
| Knowledge sources it is grounded in | |
| Does it cite sources in its output? | |
| Structured output and validation | |

## Gate C · Reach

Tools and connectors are listed in the [Tool Permission Register](03-tool-permission-register.md). Summary:

| Highest rung on the action ladder | Approval required for |
|:--|:--|
| | |

## Gate D · Human

| Question | Answer |
|:--|:--|
| Review model (sampling rate or approval on every output) | |
| Escalation path to a human | |
| Kill switch: how, who, last tested | |
| Logs kept (inputs, outputs, actions, reviewer) and retention | |

---

## Evaluation

| Question | Answer |
|:--|:--|
| Golden set location and size | |
| Pass criteria | |
| Last evaluated (date, result) | |
| Monitoring metrics (efficiency and paired quality) | |

## Known Limitations

*What it is bad at, honestly. The failures from evaluation. The cases it should escalate.*
>

## Review

| Next review date | Retirement criteria |
|:--|:--|
| | |
