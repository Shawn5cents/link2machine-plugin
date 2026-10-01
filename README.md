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

### Generic MCP clients

Any compatible client can connect to:

`https://mcp.nicholsai.com/mcp`

The public MCP Registry manifest is included here as `server.json` and points at the same production remote MCP endpoint.

## What stays private

This repository is intentionally thin. It does **not** publish the Link2Machine controller, relay implementation, credentials, customer data, internal infrastructure, or enrolled-machine details.

The public package contains only the files necessary to describe and connect to the hosted MCP service.

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

The 0.7.2 plugin targets the 0.6.1 remote controller. It adds public computer and repository helpers, including local downloaded-secret import. See [tool coverage](TOOL_COVERAGE.md) for equivalents and local permission requirements.
