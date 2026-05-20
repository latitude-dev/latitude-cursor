# Latitude — Cursor plugin

One-click install of the [Latitude](https://latitude.so) MCP server inside Cursor.

After installing and authorizing, the Cursor Agent can read and manage your Latitude workspace: projects, members, keys, traces, annotations, scores, searches, issues, datasets, and more. The full tool catalog is dynamically generated from the [Latitude API](https://api.latitude.so/docs).

## Install

### From the marketplace
Install **Latitude** from the [Cursor Marketplace](https://cursor.com/marketplace).

### Manual
Edit `~/.cursor/mcp.json` and add:

```json
{
  "mcpServers": {
    "latitude": {
      "url": "https://api.latitude.so/v1/mcp"
    }
  }
}
```

Then **Cursor Settings → Tools & MCPs**, click **Connect** on the `latitude` MCP, sign in, and pick the Latitude organization to authorize.

## Local development

```bash
# From the repo root:
ln -s "$(pwd)/cursor" ~/.cursor/plugins/local/latitude
```

Restart Cursor (or run **Developer: Reload Window**) and verify the plugin loads at **Cursor Settings → Features → Model Context Protocol**.

## Layout

```
cursor/
├── .cursor-plugin/
│   └── plugin.json     # Manifest
├── mcp.json            # Latitude MCP server config
├── assets/             # Icons
└── README.md
```

Single-plugin layout per Cursor docs: the plugin lives at the root of this folder and there is no `.cursor-plugin/marketplace.json`.

## Submission

Once tested, submit at <https://cursor.com/marketplace/publish>. Plugins are manually reviewed; every update is reviewed too.

## License

[MIT](./LICENSE)
