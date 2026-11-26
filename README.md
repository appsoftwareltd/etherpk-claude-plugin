# EtherPK for Claude Code

The EtherPK plugin for Claude Code gives Claude one of your [EtherPK](https://etherpk.com) graphs:
a knowledge base of Markdown notes linked by wikilinks, with journal entries, pages and tasks. Claude
can search your notes by words or by meaning, follow links, list tasks, and read and edit documents
without breaking the format.

The plugin holds two things:

- **The Headless Client**, EtherPK's MCP server ([`@appsoftwareltd/etherpk-mcp`](https://www.npmjs.com/package/@appsoftwareltd/etherpk-mcp) on npm),
  started for the graph you choose. It runs on your device.
- **The `etherpk` skill**, which teaches Claude the EtherPK Format and how to create, edit and publish
  a graph folder.

## Install

In Claude Code:

```text
/plugin install etherpk --marketplace appsoftwareltd/etherpk-claude-plugin
/plugin configure etherpk@etherpk
```

Set one of the options:

| Option | What to set |
| --- | --- |
| **Synced graph** | The name or id of a synced graph |
| **Graph folder** | A graph folder on your device, which holds `journals` and `pages` folders |
| **Sync Server** | Only for a synced graph on a Sync Server of your own, when your device is logged in to more than one |

A synced graph is end-to-end encrypted, so only your devices can read it. The Headless Client logs in
as one of your devices: run the login command from the graph's **Settings → Agents** tab in EtherPK
once on each device. Until then, each EtherPK tool answers with the command to run.

The plugin serves one graph. The Headless Client needs Node.js 24 or later on your device.

The [Claude Code Plugin](https://docs.etherpk.com/claude-code-plugin) page has the rest, and
[Using AI Agents With Your Notes](https://docs.etherpk.com/using-ai-agents-with-your-notes) covers the
Headless Client.

## What it runs and reads

- `npx @appsoftwareltd/etherpk-mcp serve`, with the options you set. Its source is in
  [`appsoftwareltd/etherpk-client`](https://github.com/appsoftwareltd/etherpk-client), under `apps/mcp`.
- For a synced graph, it connects to the Sync Server and keeps a copy of the graph on your device
  to serve Claude from. For a graph folder, it reads and writes the files in that folder.

## Source

This repository is exported from EtherPK's own repository on each change. Report a problem as an
issue on [`appsoftwareltd/etherpk-client`](https://github.com/appsoftwareltd/etherpk-client/issues).

## Licence

The plugin is available under the [Elastic License 2.0](LICENSE). The starter folders in
`etherpk/assets/` are under the [MIT License](https://github.com/appsoftwareltd/etherpk-client/blob/main/format/LICENSE).
