# Tool Permission Register

*Every tool, connector, API key, and scope an AI system can use, in one place. One row per tool per system. Reviewed on the tier cadence; anything unused since the last review is removed.*

[Framework: Agents and Tool Permissions](../docs/04-agents-and-tool-permissions.md)

---

**System:** ____________ **Tier:** ____ **Owner:** ____________ **Agent identity / service account:** ____________

| Tool or connector | Source and version | Scopes granted | Action ladder rung (1 to 5) | Why it is needed | Approval required? | Acts as (agent identity or user) | Approved by / date | Last used | Next review |
|:--|:--|:--|:--|:--|:--|:--|:--|:--|:--|
| *Example: Issue tracker* | *Official connector v2.3* | *Read issues, project X only* | *1* | *Read closed tickets for release notes* | *No* | *User* | | | |
| | | | | | | | | | |
| | | | | | | | | | |

---

## Combination Check

*Two harmless tools can make one harmful path. List any pair that together could move data outward or cause a binding action, and the control that breaks the chain.*

| Tool A | Tool B | Risk if combined | Control |
|:--|:--|:--|:--|
| | | | |

## Kill Switch for This System

| Step | How | Who | Last tested |
|:--|:--|:--|:--|
| Revoke identity / credentials | | | |
| Cancel queued or scheduled actions | | | |
| Preserve logs | | | |
