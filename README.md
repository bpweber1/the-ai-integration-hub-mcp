# The AI Integration Hub

The [AI Integration Hub](https://www.theaiintegrationhub.com) gives business owners ready-made AI agents that connect to Claude or ChatGPT and run in that account. [1001 agents are available now](https://www.theaiintegrationhub.com/agents). Connect them from [theaiintegrationhub.com/connect](https://www.theaiintegrationhub.com/connect).

Search 1,000+ vetted AI use cases by industry and workflow, with AI consulting services.

The AI Integration Hub is a free, read-only library of 1,000+ practical AI use cases across 18 industries and 104 types of business. Ask how AI can help a business, what to automate in a workflow, or which ideas fit an industry, and the connector returns specific, vetted use cases: the workflow it improves, how it works, the tools involved, and a link to the full write-up on [theaiintegrationhub.com](https://www.theaiintegrationhub.com).

When a team is ready to implement, it also returns The AI Integration Hub's services — AI enablement, AI process reengineering, custom AI builds, and AI strategy consulting — with a contact link. Built for CEOs, COOs, CTOs, CIOs, compliance leaders, and operators at companies with $5M+ revenue.

No sign-in, no API key, and no user data collected. Operated by Integrated AI Solutions LLC.

This repository is listing metadata only. The server runs separately at the public endpoint below.

| | |
| --- | --- |
| Endpoint | `https://www.theaiintegrationhub.com/mcp` |
| Transport | Streamable HTTP |
| Auth | None |
| How to connect | [theaiintegrationhub.com/connect](https://www.theaiintegrationhub.com/connect) |
| Registry name | `com.theaiintegrationhub/use-cases` |

## Tools

Confirmed with an MCP client against the live endpoint on 22 October 2026. Server `the-ai-integration-hub` 1.0.0. Every tool is annotated `readOnlyHint: true`, `destructiveHint: false`, `idempotentHint: true`, `openWorldHint: false`.

### search_use_cases — Search AI Use Cases

Search 1,000+ vetted AI use cases by keyword, industry, or business workflow (e.g. 'invoice', 'dental', 'customer support'). Use when someone asks how AI can help their business, wants AI ideas for an industry, or looks for automation opportunities. Returns titles, summaries, and links.

| Argument | Required | Notes |
| --- | --- | --- |
| `query` | yes | String, 1–200 characters. Example: invoice, patient intake, HVAC dispatch. |
| `industry` | no | Area or sub-industry slug, such as `accounting`, `hvac`, or `home-trade/hvac`. |
| `limit` | no | Integer 1–20. Defaults to 10. Maximum 20. |

### get_use_case — Get AI Use Case Details

Full detail for one use case by slug: the problem, how the AI workflow works, tools, implementation notes, and source link.

| Argument | Required | Notes |
| --- | --- | --- |
| `slug` | yes | Use case slug, such as `shipper-past-due-invoice-collections`. |

### list_industries — List Industries

All industries and sub-industries covered, with use-case counts. Use to browse or when the user's industry is unclear.

No arguments.

### get_industry — Get Industry AI Use Cases

Top AI use cases for one industry or sub-industry, with links.

| Argument | Required | Notes |
| --- | --- | --- |
| `slug` | yes | Area slug, sub-industry slug, or `area/sub-industry`. |

### get_ai_services — Get AI Consulting Services

The AI Integration Hub's implementation services (AI enablement, process reengineering, custom AI builds, AI strategy consulting) with a contact link. Use when the user wants an AI consultant or help implementing.

No arguments.

### Live `tools/list` result

```json
{
  "tools": [
    {
      "name": "search_use_cases",
      "title": "Search AI Use Cases",
      "description": "Search 1,000+ vetted AI use cases by keyword, industry, or business workflow (e.g. 'invoice', 'dental', 'customer support'). Use when someone asks how AI can help their business, wants AI ideas for an industry, or looks for automation opportunities. Returns titles, summaries, and links.",
      "inputSchema": {
        "type": "object",
        "properties": {
          "query": {
            "type": "string",
            "minLength": 1,
            "maxLength": 200,
            "description": "Words to match. Example: invoice, patient intake, HVAC dispatch."
          },
          "industry": {
            "description": "Optional area or sub-industry slug that limits the search, such as accounting, hvac, or home-trade/hvac.",
            "type": "string",
            "minLength": 1,
            "maxLength": 160,
            "pattern": "^[a-z0-9]+(?:-[a-z0-9]+)*(?:\\/[a-z0-9]+(?:-[a-z0-9]+)*)?$"
          },
          "limit": {
            "description": "How many matches to return. Defaults to 10. Maximum 20.",
            "type": "integer",
            "minimum": 1,
            "maximum": 20
          }
        },
        "required": ["query"],
        "$schema": "https://json-schema.org/draft/2020-12/schema"
      },
      "annotations": {
        "readOnlyHint": true,
        "destructiveHint": false,
        "idempotentHint": true,
        "openWorldHint": false
      }
    },
    {
      "name": "get_use_case",
      "title": "Get AI Use Case Details",
      "description": "Full detail for one use case by slug: the problem, how the AI workflow works, tools, implementation notes, and source link.",
      "inputSchema": {
        "type": "object",
        "properties": {
          "slug": {
            "type": "string",
            "minLength": 1,
            "maxLength": 160,
            "pattern": "^[a-z0-9]+(?:-[a-z0-9]+)*$",
            "description": "Use case slug, such as shipper-past-due-invoice-collections."
          }
        },
        "required": ["slug"],
        "$schema": "https://json-schema.org/draft/2020-12/schema"
      },
      "annotations": {
        "readOnlyHint": true,
        "destructiveHint": false,
        "idempotentHint": true,
        "openWorldHint": false
      }
    },
    {
      "name": "list_industries",
      "title": "List Industries",
      "description": "All industries and sub-industries covered, with use-case counts. Use to browse or when the user's industry is unclear.",
      "inputSchema": {
        "type": "object",
        "properties": {},
        "$schema": "https://json-schema.org/draft/2020-12/schema"
      },
      "annotations": {
        "readOnlyHint": true,
        "destructiveHint": false,
        "idempotentHint": true,
        "openWorldHint": false
      }
    },
    {
      "name": "get_industry",
      "title": "Get Industry AI Use Cases",
      "description": "Top AI use cases for one industry or sub-industry, with links.",
      "inputSchema": {
        "type": "object",
        "properties": {
          "slug": {
            "type": "string",
            "minLength": 1,
            "maxLength": 160,
            "pattern": "^[a-z0-9]+(?:-[a-z0-9]+)*(?:\\/[a-z0-9]+(?:-[a-z0-9]+)*)?$",
            "description": "Area slug, sub-industry slug, or area/sub-industry."
          }
        },
        "required": ["slug"],
        "$schema": "https://json-schema.org/draft/2020-12/schema"
      },
      "annotations": {
        "readOnlyHint": true,
        "destructiveHint": false,
        "idempotentHint": true,
        "openWorldHint": false
      }
    },
    {
      "name": "get_ai_services",
      "title": "Get AI Consulting Services",
      "description": "The AI Integration Hub's implementation services (AI enablement, process reengineering, custom AI builds, AI strategy consulting) with a contact link. Use when the user wants an AI consultant or help implementing.",
      "inputSchema": {
        "type": "object",
        "properties": {},
        "$schema": "https://json-schema.org/draft/2020-12/schema"
      },
      "annotations": {
        "readOnlyHint": true,
        "destructiveHint": false,
        "idempotentHint": true,
        "openWorldHint": false
      }
    }
  ]
}
```

## Install

The same URL works in any client that speaks remote MCP over Streamable HTTP. Leave authentication empty.

```
https://www.theaiintegrationhub.com/mcp
```

### Claude

Custom connectors are available on Free, Pro, Max, Team, and Enterprise. Free plans are limited to one custom connector. Claude connects from Anthropic's network, so the server must be public.

Individual plans (Pro and Max):

1. Open **Customize**, then **Connectors**.
2. Choose **Add**, then **Add custom connector**.
3. Name it **The AI Integration Hub**.
4. Paste `https://www.theaiintegrationhub.com/mcp`.
5. Set authentication to **No sign in**.

Team and Enterprise owners add it under **Organization settings**, **Connectors**, **Add**, **Custom**, **Web**, with the same URL and no sign-in. Members then connect it from **Customize**, **Connectors**.

Turn it on in a chat from the **+** menu, then **Connectors**.

Claude Code:

```bash
claude mcp add --transport http the-ai-integration-hub https://www.theaiintegrationhub.com/mcp
```

### Claude Desktop

Claude Desktop uses the same custom-connector flow as Claude. Remote connectors are stored on the Claude account and reached from Anthropic's servers, including when the desktop app is the client. Do not put this URL in `claude_desktop_config.json`; that file is for local stdio servers.

1. Open **Settings**, then **Connectors** (or **Customize**, **Connectors**).
2. Choose **Add custom connector**.
3. Name it **The AI Integration Hub**.
4. Paste `https://www.theaiintegrationhub.com/mcp`.
5. Leave authentication empty (**No sign in**).
6. Enable the connector in a chat from **+**, then **Connectors**.

On a Team or Enterprise plan, an owner adds it first under **Organization settings**, **Connectors**, **Add**, **Custom**, **Web**.

### ChatGPT

On a Business, Enterprise, or Edu workspace, add a custom MCP server with no authentication:

1. Open **Plugins**, then the plus button, then **Add custom MCP server**.
2. Enter the name **The AI Integration Hub** and the URL `https://www.theaiintegrationhub.com/mcp`.
3. Set authentication to none, review the risk notice, and create the app.

Some accounts still use **Settings**, **Apps**, **Advanced settings**, **Developer mode**, then the same URL.

### Cursor

Marketplace installs use the plugin manifest in this repo (`.cursor-plugin/plugin.json` and root `mcp.json`). Submit the repository at [cursor.com/marketplace/publish](https://cursor.com/marketplace/publish).

To add it by hand, put this in `~/.cursor/mcp.json` (every project) or `.cursor/mcp.json` (one project):

```json
{
  "mcpServers": {
    "the-ai-integration-hub": {
      "url": "https://www.theaiintegrationhub.com/mcp"
    }
  }
}
```

Cursor treats a `url` entry as remote HTTP. You can also add the server from **Cursor Settings**, **MCP**.

### VS Code

VS Code uses `servers`, not `mcpServers`, and requires `type`. Add this to the user MCP config or to `.vscode/mcp.json`:

```json
{
  "servers": {
    "the-ai-integration-hub": {
      "type": "http",
      "url": "https://www.theaiintegrationhub.com/mcp"
    }
  }
}
```

Or run **MCP: Add Server** from the Command Palette and choose HTTP. Use the tools from Copilot Chat in agent mode.

### Windsurf

Windsurf (Devin Desktop) Cascade reads a remote server from `serverUrl`. Add it under **Settings**, **Tools**, **Windsurf Settings**, **Add Server**, or edit the MCP config:

- macOS and Linux: `~/.config/devin/mcp_config.json` (or `$XDG_CONFIG_HOME/devin/mcp_config.json`)
- Windows: `%APPDATA%\devin\mcp_config.json`

```json
{
  "mcpServers": {
    "the-ai-integration-hub": {
      "serverUrl": "https://www.theaiintegrationhub.com/mcp"
    }
  }
}
```

`url` is accepted in place of `serverUrl`. The editor's own discovery file is separate: `~/.codeium/windsurf/mcp_config.json` (stable) or `~/.codeium/windsurf-next/mcp_config.json` (Next). The same JSON works there. Refresh MCP servers after saving.

## Example prompts

These should call the connector:

1. How can AI help a dental practice?
2. How can AI help my auto repair shop?
3. Give me AI ideas for reducing invoice reconciliation work at a courier company.
4. List the industries the AI Integration Hub covers.
5. I want an AI consultant to help implement this — what services are there?
6. Run the sales forecast agent

These should not call it, or should not invent an action the connector cannot take:

1. Write me a poem about the ocean.
2. What's the weather in Boston?
3. Book me a meeting with a consultant for tomorrow at 3pm. The connector is read-only. It can return the contact link. It cannot book the meeting.

## Privacy and support

- Privacy policy: [https://www.theaiintegrationhub.com/privacy](https://www.theaiintegrationhub.com/privacy)
- Support: [admin@theaiintegrationhub.com](mailto:admin@theaiintegrationhub.com)
- Connect guide: [https://www.theaiintegrationhub.com/connect](https://www.theaiintegrationhub.com/connect)

## Listing files

| File | Purpose |
| --- | --- |
| `.cursor-plugin/plugin.json` | Cursor Marketplace manifest. `mcp.json` stays at the repo root, which is where Cursor discovers a single-plugin repository. |
| `mcp.json` | Remote HTTP server for the Cursor plugin (`type: http`). |
| `server.json` | Official MCP Registry manifest (`com.theaiintegrationhub/use-cases`). |
| `glama.json` | Glama maintainer claim for `bpweber1`. |
| `assets/logo.png`, `assets/logo.svg` | Icons copied from the live site (`/icon-512.png`, `/icon.svg`). |

There is no `smithery.yaml`. Smithery's current publish flow for a hosted server is the public URL itself: open [smithery.ai/new](https://smithery.ai/new) and enter `https://www.theaiintegrationhub.com/mcp`, or run `smithery mcp publish` with that URL. A `smithery.yaml` `startCommand` is not how Smithery documents remote URL servers.

Publishing `server.json` to the official registry still needs a DNS TXT proof for `theaiintegrationhub.com`. This repo does not contain that key.

## License

The MIT license in this repository covers the listing metadata. Copyright Integrated AI Solutions LLC. The connector implementation lives in a separate private repository.
