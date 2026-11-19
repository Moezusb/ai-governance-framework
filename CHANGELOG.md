# Changelog

> *Governance that does not evolve is governance that has already failed.*

---

## Version 2.0 · November 2026

Version 1 governed AI that answers. Version 2 governs AI that answers, decides, and acts.

**New**
- **Two-axis risk classification.** Consequence (what a wrong answer costs) and Agency (what the system can do without asking), with modifiers for sensitive data, regulated outputs, decisions about people, and operator-built tools. → [Risk Classification](docs/02-risk-classification.md)
- **Gate C · Reach.** The Triple-Gate Safety Protocol became the Four Gates, adding a gate for tools, connectors, and actions. → [The Four Gates](docs/03-the-four-gates.md)
- **Chapters** on agents and tool permissions, builder governance, regulated environments, evaluation and drift, and a dated snapshot of the regulatory landscape.
- **Field patterns.** Five anonymized patterns from real deployments. → [Field Patterns](docs/10-field-patterns.md)
- **Seven templates.** Intake, System Card, Tool Permission Register, Builder Tool Registration, Change Log, Launch Readiness, Incident Report. → [templates/](templates/)
- **Interactive tier classifier,** a single-file web page. → [moezusb.github.io/ai-governance-framework](https://moezusb.github.io/ai-governance-framework/)
- **Three new human factors:** fluency mistaken for accuracy, approval fatigue, and skill fade, plus a section on metric gaming. → [Trust and the Human Factor](docs/01-trust-and-the-human-factor.md)
- **Severity levels and an "undo" principle** for incident response. → [Incident Response](docs/08-incident-response.md)

**Changed**
- **Data controls split in two.** Version 1's "zero-retention providers only" blurred training use and retention. They are now separate questions with separate answers.
- **The 10% audit is now risk-weighted.** Ten percent is a starting point, not a law.
- **The kill switch covers agents.** Disabling an agent means revoking its credentials and cancelling queued actions, not only stopping the chat.
- **Hardening after incidents prefers structure over instructions.** A prompt is a request, not a lock. Remove the capability, enforce in code or permissions, change the structure, and then update the prompt.

**Kept**
- Trust as the asset. Automation bias, social proof, and the bystander effect. The three tiers. The written problem statement before a single prompt. The 60-second kill switch. Contain, Trace, Communicate, Harden, Review. The $200k account at 11pm on a Friday.

---

## Version 1.0 · March 2026

Single-page playbook for ethical AI deployment in B2B SaaS: trust as the asset, behavioral dynamics, three risk tiers, the Triple-Gate Safety Protocol, and incident response.
