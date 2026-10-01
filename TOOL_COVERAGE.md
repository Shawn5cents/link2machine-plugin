# Public tool coverage

Link2Machine 0.6.1 provides the following equivalents for Grizzy's public computer
and repository helpers. These are functional mappings, not identical schemas:
Link2Machine routes each operation using the authenticated account's exact
`machine_id`, and its native local permissions and grants remain authoritative.

The public endpoint advertises 98 tools: 95 native tools and the cloud-only
`machine.list`, `account.profile`, and `account.usage`.

| Grizzy helper | Link2Machine equivalent |
| --- | --- |
| `list_repos` | `list_repos` |
| `repo_overview` | `repo_overview` |
| `repo_status` | `git.status` |
| `list_files` | `file.list` |
| `read_file` | `file.read` |
| `read_files` | `read_files` |
| `search_text` | `file.search` |
| `write_file` | `file.write` |
| `replace_text` | `file.edit` |
| `move_path` | `file.move` |
| `copy_path` | `copy_path` |
| `trash_path` | `trash_path` |
| `git_log` | `git_log` |
| `git_diff` | `git_diff` |
| `git_stage` | `git.stage` |
| `git_commit` | `git.commit` |
| `git_branch_create` | `git_branch_create` |
| `git_push` | `git_push` |
| `run_project_script` | `run_project_script` |
| `verify_repo` | `verify_repo` |
| `run_program` | `program.run` |
| `start_program` | `program.start / program.start_durable` |
| `job_status` | `job.status` |
| `job_output` | `job.output` |
| `job_input` | `job.write / job.close_stdin` |
| `job_stop` | `job.stop` |
| `system_snapshot` | `system_snapshot` |
| `process_list` | `process.list` |
| `process_stop` | `process.signal` |
| `network_listeners` | `network_listeners` |
| `secret_import` | `secret_import` |
| `config_set` | `config_set` |
| `user_service_list` | `user_service_list` |
| `user_service_status` | `service.status` |
| `user_service_action` | `service.action` |
| `user_service_install` | `user_service_install` |

Grizzy's fixed lab-node administration, Omi hardware UI/mapping, and private Sparse
Env integrations are excluded. Link2Machine's account-bound machine registry is
its source of enrolled computers; the Grizzy lab registry is not an enrollment
fallback.

## Downloaded secrets

Enable secret import locally on the enrolled Linux machine using
`LINK2MACHINE_ALLOW_WRITE=1` and `LINK2MACHINE_ALLOW_SECRET_IMPORT=1`. These flags
are preserved when installing the node service. If grant scopes are configured,
the grant must include `secrets`. Remote tools cannot raise these local ceilings.

Call `secret_import` with `machine_id`, `source_path`, `file`, and `key`.
For example, use `source_path=~/Downloads/provider-key.txt`, `file=provider.env`,
and `key=PROVIDER_API_KEY`. The optional `delete_source` defaults to false.
Do not read the secret with another tool or pass its value through chat.

The importer reads one nonempty line from a user-owned regular file in the
selected machine's Downloads directory. It rejects traversal, symlinks, NUL,
multiline values, and files larger than 64 KiB. It atomically writes the key to
`~/.config/link2machine/env/provider.env` with mode 0600. The protected directory
uses mode 0700; controller/enrollment configuration is outside this destination.
Responses and receipts include confirmation metadata, never secret content,
prefixes, lengths, hashes, or environment-file snapshots. Optional source deletion
runs only after a successful import.

`config_set` is a separate local opt-in (`LINK2MACHINE_ALLOW_CONFIG_FILES=1`)
for ordinary environment values. Use `secret_import` for downloaded credentials.

## ChatGPT registration

OAuth-mode MCP initialization and tool discovery are accessible before linking.
Every tool declares OAuth at the tool level and in compatibility metadata;
unlinked calls return `mcp/www_authenticate` without reading account data or
routing to a machine. Invalid supplied tokens are rejected with HTTP 401.

A deployed endpoint does not itself publish or install a ChatGPT plugin.
Existing development connections need a tool refresh and a new conversation;
public availability requires the canonical plugin's publisher verification,
review materials, server scan, approval, and publication in ChatGPT.
