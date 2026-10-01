# Link2Machine

**Use the computer you already have from the AI client you already use.**

Link2Machine is the public distribution package for the Link2Machine remote MCP service from Nichols SI.

It connects compatible AI clients to explicitly enrolled computers through:

- exact-machine routing;
- typed file, data, process, runtime, Git, test, service, PDF, and spreadsheet tools;
- local machine policy that remains authoritative;
- fail-closed behavior when a selected node is offline or revoked;
- structured execution receipts.

Production MCP endpoint:

`https://mcp.nicholsai.com/mcp`

## Install surfaces

### ChatGPT / OpenAI

The repository root contains the portable OpenAI plugin files:

- `plugin.json`
- `mcp.json`
- `assets/`
- `skills/link2machine/SKILL.md`

Public listing: pending directory review.

Product page: https://nicholsai.com/link2machine/

### Claude

The repository also contains the Claude plugin layout:

- `.claude-plugin/plugin.json`
- `.mcp.json`
- `skills/link2machine/SKILL.md`

This layout is intended for Claude's public plugin marketplace/directory and points to the same production remote MCP endpoint.

### Native computer agent (Linux x64 / ARM64)

Connect a Linux x64 or ARM64 computer with the hosted bootstrap package. This one command installs the verified native 0.6.1 controller if needed, starts account pairing, and opens the dashboard:

```bash
npx --yes --package=https://downloads.nicholsai.com/bootstrap/v0.6.2/nicholsai-link2machine-0.6.2.tgz link2machine-bootstrap connect --root /path/to/your/project
```

The bootstrap selects the current native platform artifact, verifies its SHA-256, and checks the installed version before enrollment. It then shows a short code and opens the Nichols SI dashboard, where the signed-in user reviews the exact root and requested local permissions before approval.

Read-only is the default. Add `--allow-write`, `--allow-programs`, `--allow-secret-import`, or `--compat` only when the computer owner explicitly wants those capabilities. Secret import also requires write permission. The scoped npm registry package is not published yet; the immutable HTTPS bootstrap URL above is the supported public installer. See [tool coverage](TOOL_COVERAGE.md).

### Generic MCP clients

Any compatible client can connect to:

`https://mcp.nicholsai.com/mcp`

The public MCP Registry manifest is included here as `server.json` and points at the same production remote MCP endpoint.

## What stays private

This repository is intentionally thin. It does **not** publish the Link2Machine controller, relay implementation, credentials, customer data, internal infrastructure, or enrolled-machine details.

The public package contains only the files necessary to describe and connect to the hosted MCP service. The MIT license in this repository applies to this public distribution package only; it does not publish or license the private controller/relay implementation.

## Safety model

Link2Machine does not silently substitute another computer when the chosen machine is unavailable.

The enrolled machine enforces its own root, write, process, program, service, and capability boundaries. The remote service cannot grant permissions that the machine did not enable locally.

## Links

- Product: https://nicholsai.com/link2machine/
- Support: https://nicholsai.com/link2machine/support/
- Privacy: https://nicholsai.com/link2machine/privacy/
- Terms: https://nicholsai.com/link2machine/terms/
- Publisher: https://nicholsai.com/

## Publisher

**Nichols SI**

The 0.7.6 plugin targets the 0.6.1 remote controller and the 0.6.2 bootstrap. It includes self-service computer enrollment plus public computer and repository helpers, including local downloaded-secret import. See [tool coverage](TOOL_COVERAGE.md) for equivalents and local permission requirements.
