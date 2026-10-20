# Dubai Car Prices — Dubai Car Index plugin

Dubai car prices for Claude, ChatGPT, Cursor, Grok and any MCP client: UAE new-car list
prices by trim, used values by model year and mileage, a fair-price check for
an asking price, rental rates and repair costs.

[Dubai Car Index](https://dubaicarindex.com) publishes what a car in Dubai
should cost, to buy, rent or repair. Every list price carries its source and
the date it was checked. Used values, rental rates and repair bands are
modelled from those prices and published quotes, and every answer says which
kind of figure it is.

This plugin connects your AI assistant to that data over MCP and adds skills
that tell it how to quote the figures correctly.

## What you can ask

- "Is AED 165,000 a fair price for a 2021 Toyota Land Cruiser with 80,000 km?"
- "What does a Nissan Patrol cost new in Dubai, trim by trim?"
- "How much is a monthly rental of a Kia Sportage in Dubai?"
- "What does a BMW minor service cost at the dealer versus an independent garage?"
- "Compare the Land Cruiser and the Patrol on price, depreciation and running costs."

## What is in here

| Path | |
| --- | --- |
| `.claude-plugin/plugin.json` | Claude plugin manifest |
| `.claude-plugin/marketplace.json` | Marketplace entry, so this repo can be added as a Claude Code marketplace |
| `.mcp.json` | The remote MCP server, `https://dubaicarindex.com/api/mcp` |
| `skills/` | Three skills: get started, check a used car's price, cite a price |
| `plugin.json`, `mcp.json` | The same plugin in the [Agent Plugins](https://agent-plugins.org) format, for ChatGPT, Codex and other clients |
| `.codex-plugin/plugin.json` | Manifest for OpenAI Agents API sessions; points at `skills/` and `.mcp.json` |
| `.cursor-plugin/` | Cursor manifest and marketplace entry |
| `.grok-plugin/` | Grok manifest |
| `assets/` | Icon |

The skills are plain Markdown instructions. The plugin ships no scripts, hooks
or executables and installs no packages.

## Install

**Claude Code**

```bash
claude plugin marketplace add dubaicarindex/dubaicarindex-plugin
claude plugin install dubai-car-index@dubai-car-index
```

**Cursor** — add this repository from the Cursor plugin marketplace, or point
Cursor at it as a plugin repository.

**Grok** — `grok` loads it from `~/.grok/plugins/`, or pass the cloned
repository with `--plugin-dir`.

**ChatGPT and Codex** — use the root `plugin.json` and `mcp.json`.

**OpenAI Agents API** — upload the plugin folder as a ZIP in
`environment.plugins`, or list it in `environment.capability_directories` on a
self-hosted sandbox. Both read `.codex-plugin/plugin.json`.

**Any MCP client, without the skills**

```bash
claude mcp add --transport http dubai-car-index https://dubaicarindex.com/api/mcp
```

On claude.ai or ChatGPT, add `https://dubaicarindex.com/api/mcp` as a custom
connector.

## Sign-in and the data it sends

Connecting opens a browser sign-in to a free Dubai Car Index account (OAuth
2.1): an email address and a sign-in link or code, no password and no API key.
The plugin requests read access to published price data. Every tool reads;
none writes.

The plugin talks to one server, `dubaicarindex.com`. When the assistant calls a
tool, the tool's arguments, such as a brand, a model, a model year, a mileage
or an asking price, are sent to that server. Dubai Car Index records each tool
call in its product analytics (PostHog): the tool name, its arguments, timing,
errors, the AI client's name and your account identifier. It does not record
its answers. Nothing else from your conversation or your machine is sent. See
the [privacy policy](https://dubaicarindex.com/privacy).

## Scope

UAE only. Prices change; confirm with the dealer, seller, rental company or
garage before you pay. The plugin does not buy, sell, book or pay for anything,
and it does not value a specific car's condition or history.

## Support

[dubaicarindex.com/contact](https://dubaicarindex.com/contact) or
hello@dubaicarindex.com.
