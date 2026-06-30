# Latitude — Cursor plugin

One-click install of the [Latitude](https://latitude.so) MCP server inside Cursor.

[![Add Latitude MCP server to Cursor](https://cursor.com/deeplink/mcp-install-dark.svg)](cursor://anysphere.cursor-deeplink/mcp/install?name=latitude&config=eyJ0eXBlIjoiaHR0cCIsInVybCI6Imh0dHBzOi8vYXBpLmxhdGl0dWRlLnNvL3YxL21jcCJ9)

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
      "type": "http",
      "url": "https://api.latitude.so/v1/mcp"
    }
  }
}
```

Then **Cursor Settings → Tools & MCPs**, click **Connect** on the `latitude` MCP, sign in, and pick the Latitude organization to authorize.

## Local development

```bash
# From a clone of this repo:
cp -R "$(pwd)" ~/.cursor/plugins/local/latitude
```

Restart Cursor (`Cmd+Shift+P → Developer: Reload Window` is enough), then verify the plugin loads at **Cursor Settings → Tools & MCPs**. Click **Connect** on `latitude`, sign in, and pick the Latitude organization to authorize.

To iterate, re-copy:

```bash
rm -rf ~/.cursor/plugins/local/latitude && cp -R "$(pwd)" ~/.cursor/plugins/local/latitude
# Cmd+Shift+P → Developer: Reload Window
```

### Local-install limitations

- **Don't use `ln -s` to symlink the plugin.** Cursor's official docs suggest symlinks for local development, but current Cursor stable (≥ 3.4.20 tested) does not follow symlinks into `~/.cursor/plugins/local/`. Use `cp -R` and re-copy on changes.
- **The plugin's icon and description won't render locally.** Cursor resolves the manifest's `logo` relative path to a `raw.githubusercontent.com` URL using the marketplace's record of the plugin's repository + commit SHA. For a local install, there's no marketplace record, so the icon falls back to a generic placeholder and the description may not surface in the MCP server picker. Both render correctly once the plugin is installed from the marketplace.

## Layout

```
.
├── .cursor-plugin/
│   └── plugin.json     # Manifest
├── mcp.json            # Latitude MCP server config
├── assets/             # Icons
├── LICENSE
└── README.md
```

Single-plugin layout per [Cursor docs](https://cursor.com/docs/plugins): the plugin lives at the repo root and there is no `.cursor-plugin/marketplace.json`.

## Submission

Once tested, submit at <https://cursor.com/marketplace/publish>. Plugins are manually reviewed; every update is reviewed too.

## License

[MIT](./LICENSE)
