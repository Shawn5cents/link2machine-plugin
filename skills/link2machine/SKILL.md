---
name: link2machine
description: Use Link2Machine to work on an explicitly selected enrolled computer while preserving local policy and execution evidence.
---

Use Link2Machine when the user wants the current conversation to inspect or act on a computer enrolled to their Link2Machine account.

- If the machine is not identified and the task depends on one, list enrolled machines first or ask which machine to use.
- Never silently substitute another machine when the selected node is offline, revoked, or unavailable.
- Prefer focused Link2Machine tools over generic command execution when a typed tool exists.
- Respect the selected machine's local root and capability restrictions.
- For consequential changes, surface the execution result or receipt and distinguish what changed from what was only inspected.
- Do not expose credentials, tokens, private machine identifiers, or unnecessary personal information.

For machine selection, call `machine.list` through Link2Machine. Report a missing
connection or tool explicitly; another app's registry does not verify this account's
Link2Machine enrollment. Every routed tool requires the exact `machine_id` returned
by Link2Machine.

Use `secret_import` when importing a downloaded credential. Pass the source path,
environment filename, and key, without reading or copying the value into chat or
tool arguments. The source must be on the selected machine under `~/Downloads`.
The destination is `~/.config/link2machine/env/<file> (an `.env` filename)`; controller and enrollment
configuration are outside this tool's destination. The machine owner must opt in
locally with write permission and `LINK2MACHINE_ALLOW_SECRET_IMPORT=1`. Do not
enable permissions remotely to work around a denial. Delete the source only when
the user requests it. Report only the returned confirmation and receipt.

Use focused repository helpers such as `repo_overview`, `read_files`, `git_log`,
`git_diff`, `git_branch_create`, `git_push`, `run_project_script`, and `verify_repo`.
Program execution and project scripts can change files and contact external
services; inspect their actual result and exit code before reporting success.
