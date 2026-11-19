# 09 · Where the Rules Stand

> *The law moves slower than the models,*
> *and faster than most compliance calendars.*

[← Incident Response](08-incident-response.md) · [Next: Field Patterns →](10-field-patterns.md)

---

**Snapshot date: 19 November 2026.** This chapter is a map, not legal advice. It is written by an operator for operators, to show the shape of the terrain so you know which questions to bring to your lawyers. Laws in this area change quickly; check every date against the primary source before relying on it. Sources are listed at the end.

---

## The Short Version

1. **Nothing was cancelled. Several things were postponed.** The EU's high-risk AI obligations moved to December 2027 and August 2028. The obligations themselves did not change.
2. **Transparency is live now.** In the EU, telling people they are interacting with AI has applied since 2 August 2026.
3. **Canada chose a strategy and a privacy bill, not an AI act.** Automated decision-making transparency is coming through privacy law.
4. **The US is a patchwork under pressure.** No comprehensive federal statute; state laws remain enforceable while federal preemption is fought in courts and Congress.
5. **Standards are becoming the common language.** NIST AI RMF for thinking, ISO/IEC 42001 for proving, OWASP for agent security. Customers increasingly ask for them by name.

A framework built on the [four gates](03-the-four-gates.md) and the [tier matrix](02-risk-classification.md) will map onto all of these without a rewrite. That is the point of governing by risk rather than by jurisdiction.

---

## European Union · AI Act

The AI Act (Regulation (EU) 2024/1689) applies in stages. In 2026 the EU amended its timeline through the **Digital Omnibus on AI**, approved by Parliament on 16 June 2026 and the Council on 29 June 2026, and published in the Official Journal on 24 July 2026.

| Obligation | Applies from | Notes |
|:--|:--|:--|
| Prohibited practices (Article 5) | 2 February 2025 | The Omnibus adds new prohibitions, including AI generating non-consensual intimate imagery, from 2 December 2026 |
| General-purpose AI model obligations | 2 August 2025 | Unchanged by the Omnibus |
| Transparency obligations (Article 50), such as telling people they are interacting with AI | 2 August 2026 | Unchanged by the Omnibus |
| Machine-readable marking of AI-generated content (Article 50(2)), for systems already on the market before 2 August 2026 | 2 December 2026 | Four-month grace period |
| High-risk systems in Annex III (standalone: employment, education, credit, essential services, and others) | **2 December 2027** | Deferred from 2 August 2026 |
| High-risk AI embedded in regulated products in Annex I (including medical devices and machinery) | **2 August 2028** | Deferred from 2 August 2027 |

**What it means for operators:** if your AI talks to people in the EU, the transparency duty is already yours. If you build or deploy systems in an Annex III area (hiring and HR tools are the most common surprise), the delay is runway, not relief. Use it to build the documentation, logging, and human oversight the obligations will require, all of which this framework already asks for at Tier 3.

---

## Canada

Canada's first attempt at a federal AI statute, the **Artificial Intelligence and Data Act (AIDA)**, died with Bill C-27 when Parliament was prorogued in January 2025. It has not been revived.

- **National strategy.** On 4 June 2026 the federal government released **"AI for All,"** its refreshed national AI strategy. Commentators read it as a shift toward targeted regulation of specific risks rather than one comprehensive AI law. It also announced a planned "Canada Trusted AI Certification" program.
- **Privacy reform with AI provisions.** On 15 June 2026, Minister of Artificial Intelligence and Digital Innovation Evan Solomon tabled **Bill C-36, the Protecting Privacy and Consumer Data Act**, to replace the private-sector privacy rules in PIPEDA. It does not include a standalone AI statute, but it would require transparency about automated decision-making for significant decisions about individuals, create a new regulator (the Digital Safety and Data Protection Commission of Canada), and raise maximum penalties to $25 million or 5% of global revenue. Check its current status in Parliament before relying on it.
- **Quebec.** Quebec's Law 25 already requires organizations to inform individuals when a decision about them is based exclusively on automated processing, and to let them have the decision reviewed by a person.

**What it means for operators:** for Canadian organizations, the near-term AI obligations arrive through privacy law. Any system that makes or materially supports significant decisions about people should already be able to explain what it used and offer a human review. That is Tier 3 in this framework.

---

## United States

There is no comprehensive federal AI statute.

- **Federal posture.** A December 11, 2025 executive order, "Ensuring a National Policy Framework for Artificial Intelligence," directed federal agencies to challenge state AI laws considered inconsistent with national policy and created a Department of Justice AI Litigation Task Force. A March 2026 national policy framework recommended that Congress preempt conflicting state laws. An executive order is not itself preemption: state laws remain enforceable until courts or Congress say otherwise.
- **Colorado.** The first comprehensive state AI law (SB 24-205) was stayed in April 2026 and then **repealed and replaced** on 14 May 2026 by SB 26-189, a narrower framework focused on automated decision-making technology used in consequential decisions, built around notice and consumer rights. The new law takes effect 1 January 2027.
- **Other states.** California, Texas, Illinois, and others have AI-related laws in effect from 2026, covering areas such as frontier-model transparency, employment decisions, and disclosure. The list changes monthly.

**What it means for operators:** govern to the strictest market you actually serve, and keep a short register of which state laws touch which of your systems. The register is cheap; discovering the gap during a sales cycle is not.

---

## Health and Life Sciences

- **FDA, drugs and biologics.** January 2025 draft guidance, *Considerations for the Use of Artificial Intelligence to Support Regulatory Decision-Making for Drug and Biological Products*, proposes a seven-step, risk-based credibility assessment framework centred on the model's **context of use**. It focuses on AI that produces information supporting regulatory decisions about safety, effectiveness, or quality; uses limited to internal operational efficiency are generally outside its scope.
- **FDA and EMA, joint principles.** In January 2026 the FDA and the European Medicines Agency published guiding principles of good AI practice in drug development: non-binding, but a clear signal of where both regulators are heading.
- **Good Clinical Practice.** ICH E6(R3) does not contain AI-specific rules, but its risk-proportionate approach to computerized systems and data integrity applies to AI-assisted trial processes like any other system.
- **EU medical devices.** AI embedded in medical devices falls under the AI Act's Annex I high-risk regime from 2 August 2028, on top of existing device regulation.

**What it means for operators:** define the context of use in writing, match the evidence to the risk, and keep a named human accountable. The [Regulated Environments](06-regulated-environments.md) chapter turns that into day-to-day controls.

---

## Standards and Frameworks

| Framework | What it is | How to use it |
|:--|:--|:--|
| **NIST AI Risk Management Framework (AI RMF 1.0)** with the **Generative AI Profile (NIST AI 600-1)** | Voluntary US framework organized around Govern, Map, Measure, Manage | A shared vocabulary for risk conversations; maps well to this framework's tiers and gates |
| **ISO/IEC 42001:2023** | Certifiable international standard for an AI management system | The "prove it" layer. Increasingly requested in enterprise procurement. ISO/IEC 42006 (2025) sets requirements for the bodies that certify it |
| **OWASP Top 10 for Agentic Applications** (December 2025) | Community-built list of the top security risks for autonomous AI agents | A threat checklist for [Gate C](03-the-four-gates.md#gate-c--reach-what-it-can-touch--new-in-version-2) and the [agents chapter](04-agents-and-tool-permissions.md) |
| **Singapore IMDA Model AI Governance Framework for Agentic AI** (January 2026) | Government guidance specific to agentic systems | A practical reference for matching oversight to agent risk |

---

## How This Framework Maps

| This framework | EU AI Act | Canada (Bill C-36, Law 25) | NIST AI RMF | ISO/IEC 42001 |
|:--|:--|:--|:--|:--|
| [Use Case Intake](../templates/01-use-case-intake.md), problem statement | Intended purpose | Purpose of collection and use | Map | AI system impact assessment |
| [Tier matrix](02-risk-classification.md) | Risk categories, Annex III | Significant decisions | Map, Measure | Risk assessment |
| Gate A · Data | Data governance | Consent, minimization | Manage | Data for AI systems |
| Gate D · Human, disclosure | Human oversight, Article 50 | Explanation, human review | Manage | Human oversight |
| [Evals and drift](07-evaluation-and-drift.md) | Accuracy, robustness, post-market monitoring | Accuracy | Measure | Performance evaluation |
| [Change log](../templates/05-prompt-and-model-change-log.md), logs, System Card | Technical documentation, record-keeping | Accountability | Govern | Documented information |
| [Incident response](08-incident-response.md) | Serious incident reporting | Breach notification | Manage | Nonconformity and corrective action |

This table shows where the ideas meet. It is not a compliance crosswalk; a lawyer or auditor should do that mapping for your specific obligations.

---

## Sources

- Hogan Lovells, [EU legislators agree to delay for high-risk AI rules](https://www.hoganlovells.com/en/publications/eu-legislators-agree-to-delay-for-highrisk-ai-rules)
- Paul, Weiss, [Next stop on the Digital Omnibus: AI Act reforms and new Commission guidance](https://www.paulweiss.com/insights/client-memos/next-stop-on-the-digital-omnibus-ai-act-reforms-and-new-commission-guidance)
- Freshfields, [EU AI Act unpacked #34: The final Digital Omnibus on AI](https://www.freshfields.com/en/our-thinking/blogs/technology-quotient/eu-ai-act-unpacked-34-the-final-digital-omnibus-on-ai-key-amendments-to-the-a-102nber)
- Cooley, [Digital AI Omnibus delays key deadlines, introduces new rules](https://cdp.cooley.com/digital-ai-omnibus-delays-key-deadlines-introduces-new-rules/)
- Baker McKenzie, [Canada: Federal government releases refreshed national AI strategy](https://connectontech.bakermckenzie.com/canada-federal-government-releases-refreshed-national-ai-strategy/)
- McCarthy Tétrault, [Bill C-36: What organizations need to know about Canada's new privacy reform](https://www.mccarthy.ca/en/insights/blogs/techlex/bill-c-36-what-organizations-need-to-know-about-canada-s-new-privacy-reform)
- Fasken, [Bill C-36](https://www.fasken.com/en/knowledge/2026/06/bill-c-36)
- JD Supra, [Colorado's AI reset](https://www.jdsupra.com/legalnews/colorado-s-ai-reset-two-weeks-a-white-1874953/)
- Greenberg Traurig, [Colorado repeals and replaces the Colorado AI Act](https://www.gtlaw.com/en/insights/2026/5/colorado-repeals-and-replaces-the-colorado-ai-act)
- The Clinical Trial Vanguard, [The FDA just handed industry a rulebook on AI in trials](https://clinicaltrialvanguard.com/clinical-bellwether/the-fda-just-handed-industry-a-rulebook-on-ai-in-trials-now-comes-the-hard-part)
- Drug Discovery News, [Regulating AI in drug discovery: what FDA, EMA and ICH guidance means](https://www.drugdiscoverynews.com/regulating-ai-in-drug-discovery-what-fda-ema-and-ich-guidance-means-for-pharma-r-d-17366)
- OWASP GenAI Security Project, [OWASP Top 10 for Agentic Applications](https://genai.owasp.org/2025/12/09/owasp-top-10-for-agentic-applications-the-benchmark-for-agentic-security-in-the-age-of-autonomous-ai/)
- Bright Defense, [ISO/IEC 42001 moves from AI standard to vendor requirement](https://www.brightdefense.com/news/iso-42001-moves-from-ai-standard-to-vendor-requirement/)

---

> *Rules are the slow memory of fast mistakes.*
> *Build as if they have already arrived. Most of them will.*

[Next: Field Patterns →](10-field-patterns.md)
