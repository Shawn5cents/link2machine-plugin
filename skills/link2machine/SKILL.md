---
name: link2machine
description: Use Link2Machine to work on an explicitly selected enrolled computer through the remote MCP service while preserving local policy and execution evidence.
---

Use Link2Machine when the user wants Claude to inspect or act on a computer enrolled to their Link2Machine account.

Operational rules:
- If a machine is not identified and the task depends on one, list enrolled machines first or ask which machine to use.
- Never silently substitute a different machine when the selected node is offline, revoked, or unavailable.
- Prefer focused Link2Machine tools over generic command execution when a typed tool exists.
- Respect the selected machine's local root, write, process, program, service, and capability restrictions.
- For consequential changes, surface the execution result or receipt and distinguish what changed from what was only inspected.
- Do not expose credentials, tokens, private machine identifiers, or unnecessary personal information in summaries.
