# Koskamo for Gemini CLI

Connect Gemini CLI to [Koskamo](https://koskamo.com), a public knowledge service
for AI agents. Find MCP servers and local packages, inspect their capabilities
and provenance, and retrieve reference passages with source citations.

This extension connects directly to Koskamo's existing public MCP server at
`https://koskamo.com/api/mcp` using Streamable HTTP. No Koskamo account or API key
is required. No local server or additional dependencies are installed.

## Install

With [Gemini CLI](https://geminicli.com/docs/get-started/installation/) installed:

```sh
gemini extensions install https://github.com/empline/koskamo-gemini
```

Restart an existing Gemini CLI session after installation. Run `/mcp` inside
Gemini CLI to inspect the connection and available tools.

## Try it

- "Use Koskamo to find vendor-published MCP servers for developer documentation.
  Compare their transports, authentication requirements, and source links."
- "List Koskamo's public datasets, then retrieve reference passages about the
  speed of light. Include the returned source citations and document versions."
- "Use Koskamo to inspect a listed MCP server's tool schemas and provenance."

Koskamo returns candidate passages and source-attributed directory metadata.
Check the returned citations, verification states, and timestamps; a similarity
score ranks matches and is not a measure of factual confidence.

## Available tools

| Tool | Purpose |
| --- | --- |
| `koskamo_find_mcp_server` | Find remote servers and local packages by capabilities, publisher, transport, and authentication. |
| `koskamo_get_mcp_server` | Inspect a published listing's schemas, provenance, and maintenance events. |
| `koskamo_list_datasets` | Browse public datasets. |
| `koskamo_retrieve` | Retrieve passages with citations and document versions. |
| `koskamo_get_history` | Inspect public document version history. |
| `koskamo_list_revisions` | Inspect dataset revisions, subject to the server's access checks. |
| `koskamo_report_fact` | Submit a disputed passage to Koskamo's review queue. |
| `koskamo_register_mcp_server` | Register a server you operate using ownership proof. |

Reporting a fact and registering a server submit data to Koskamo. Use those tools
only when you intend to make that submission. The extension does not configure
automatic tool approval. Contributor-only revision proposals and decisions are
outside this public integration.

Tool arguments are sent to Koskamo over HTTPS. Avoid sending secrets or private
content to this public service. See [Privacy](https://koskamo.com/privacy),
[Terms](https://koskamo.com/terms), and [connection documentation](https://koskamo.com/connect).

## Update or uninstall

```sh
gemini extensions update koskamo
gemini extensions uninstall koskamo
```

## Maintainers

The root `gemini-extension.json` is the complete integration. The extension's
version is independent of the remote MCP server version. Validate installation
and the live connection before publishing manifest changes.

Google's [extension gallery](https://geminicli.com/extensions/) discovers public
GitHub repositories with the `gemini-cli-extension` topic and a root manifest.
Google documents a daily crawl; publication here does not establish gallery
inclusion or endorsement. See the [release requirements](https://geminicli.com/docs/extensions/releasing/#list-your-extension-in-the-gallery).
