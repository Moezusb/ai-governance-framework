# Prompt and Model Change Log

*Any change underneath the system is a change to the system. Log every change to the prompt, model, knowledge sources, or tools, and re-run the golden set before it reaches production. Tier 3 changes need a second person's approval.*

[Framework: Evaluation and Drift](../docs/07-evaluation-and-drift.md)

---

**System:** ____________ **Tier:** ____ **Golden set location:** ____________

| # | Date | Type | What changed | Why | Eval result before | Eval result after | Changed by | Approved by (Tier 3) | Rollback plan |
|:--|:--|:--|:--|:--|:--|:--|:--|:--|:--|
| 1 | | ☐ Prompt ☐ Model ☐ Knowledge ☐ Tool | | | | | | | |
| 2 | | ☐ Prompt ☐ Model ☐ Knowledge ☐ Tool | | | | | | | |

---

**Change types to watch for**

- **Prompt:** any edit to instructions, examples, or output format, however small.
- **Model:** a version change, a provider's automatic update, or a deprecation notice. Record the exact model version.
- **Knowledge:** changes to the help center, policy documents, templates, or data the system draws from.
- **Tool:** a connector added, removed, updated, or rescoped. Update the [Tool Permission Register](03-tool-permission-register.md) too.
