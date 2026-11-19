# Use Case Intake

*Fill this in before a single prompt is written. It should take 20 minutes. If it takes longer, the use case is not clear yet, and that is the most useful thing this form can tell you.*

[Framework: Risk Classification](../docs/02-risk-classification.md) · [Tier classifier](https://moezusb.github.io/ai-governance-framework/)

---

## 1. The Problem

**What problem does this solve, in one or two sentences, without mentioning AI?**
>

**Who has this problem today, and what does it cost them?** (time, errors, delay, customer impact)
>

**How is it solved today?**
>

**How will we know it worked?** (the metric, the baseline, the target, and the paired quality metric)

| Efficiency metric | Baseline | Target | Paired quality metric |
|:--|:--|:--|:--|
| | | | |

**Why AI, and not a simpler fix?** (a template, a rule, a process change, a form)
>

---

## 2. The System

**What will the system do?** (one job, described as inputs and outputs)
>

**Who will use it, and who will be affected by its outputs?**
>

**Build or buy?** ☐ Vendor product ☐ Built by engineering ☐ Built by an operator ([register it](04-builder-tool-registration.md))

**Model provider and product:**
>

---

## 3. Classification

**Consequence:** if this system produces a confident wrong answer, what is the worst-case outcome for the person on the other end?

☐ **C1 Contained:** internal, reversible, someone reads it before it matters
☐ **C2 Exposed:** reaches customers or the public, or informs a decision
☐ **C3 Binding:** money, contracts, legal, health, regulated records, or decisions about people

**Agency:** what can it do before a human says yes?

☐ **A0 Advise** ☐ **A1 Read** ☐ **A2 Act, reversibly** ☐ **A3 Act, irreversibly or externally**

**Modifiers** (each can raise the tier, none can lower it)

☐ Sensitive data (minimum Tier 2)
☐ Regulated output (raise one tier)
☐ Decisions about people (Tier 3)
☐ Operator-built with a single reviewer (minimum Tier 2)

**Resulting tier:** ☐ Tier 1 · Contained ☐ Tier 2 · Supervised ☐ Tier 3 · Accountable

---

## 4. Data

**What data goes in?** (be specific: fields, documents, systems)
>

**Does it include personal, health, financial, or confidential customer data?** ☐ No ☐ Yes:
>

**Is a DPA in place? Is training on our data contractually excluded? What is the retention window?**
>

---

## 5. Owners

| Role | Name |
|:--|:--|
| Owner (accountable for the system) | |
| Incident Owner (Tier 2 and 3) | |
| Designated Lead for the kill switch (Tier 2 and 3) | |
| Reviewer(s) | |
| Legal / Compliance contact (Tier 3) | |

---

## 6. Decision

☐ Approved to build at Tier ___ ☐ Approved with conditions ☐ Not approved

**Conditions or reasons:**
>

**Approved by / date:**
>
