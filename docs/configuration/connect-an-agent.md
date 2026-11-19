---
description: Connect Copilot, Claude, Antigravity, Codex, or another local MCP client to the world open in TEdit.
---

# Connect an agent to TEdit

You can use a local agent to inspect the world open in TEdit, draw on it, or run a script. Start with inspection so you can check that the agent sees the right world.

1. Open your world in TEdit. In **File > Settings**, [enable the local MCP server and token-free sharing](settings.md#connect-a-local-agent). New setups have **Allow drawing tools** selected. For inspection only, clear it. Select **Save**.

   ![MCP settings with the server, token-free sharing, and drawing tools enabled. Scripts are off.](/img/v5/configuration/settings-mcp.png)

2. Reopen **File > Settings** and expand **MCP > Connect an agent**. Choose your client. If you want the connection to apply to one project, select the workspace option where available.
3. Select **Check connection** to test the connection from TEdit. Copy the setup preview or export it to a new file. If you already have a configuration file, add the `tedit` entry alongside your other servers. If TEdit shows a PowerShell command, run it instead.
4. Reload MCP servers in your client or start a new agent session. Ask **“What are the dimensions of the world open in TEdit?”** Compare the answer with your world. Keep TEdit open while you use the agent.

## Where to add the connection

| Client | How to use the setup preview |
| --- | --- |
| GitHub Copilot in VS Code | Run **MCP: Open User Configuration** in the Command Palette, or open `.vscode/mcp.json` for one workspace. Add the entry, start the **tedit** server, and select its tools in Agent mode. |
| GitHub Copilot CLI | Add the entry to `~/.copilot/mcp-config.json`. |
| Claude Code | Run the user setup command, or add the workspace entry to `.mcp.json`. Check registration with `claude mcp list`. |
| Claude Desktop | Open **Settings > Developer > Edit Config**. Add the entry to `claude_desktop_config.json`, then quit and reopen Claude Desktop. The preview uses the bridge included with TEdit. |
| Antigravity IDE | In the agent panel, open **… > MCP Servers > Manage MCP Servers > View raw config** and add the entry. |
| Codex CLI or Codex desktop | Add the TOML table to `~/.codex/config.toml` or to `.codex/config.toml` in a trusted project. Check registration with `codex mcp list` or in the desktop app’s MCP settings. |
| Other MCP clients | For Streamable HTTP, use the URL shown in TEdit. For stdio, use the bridge executable path and arguments from the preview. |

## Try an edit

[Save a separate backup copy of your world](saves-and-backups.md) before each editing session. If you previously turned drawing off, select **Allow drawing tools** in **File > Settings > MCP**, save, and reconnect the client.

With your test world open, ask the agent to draw a filled 2 × 2 rectangle of stone wall starting at tile (10, 10). Ask it to read the four tiles back. Check the result in TEdit, then select **Undo** to restore the original tiles.

To run a script, also select **Also allow JavaScript and Lua scripts**, save, and reconnect. Ask the agent to read the scripting reference for your chosen language before it runs the script. If a script stops partway through, review the changes in TEdit. You can undo them in one step.

## Disconnect or reconnect

If the client stops responding after you restart TEdit, reopen **MCP > Connect an agent** in the editor window you want to use. Copy the current setup and reconnect your client. If it can inspect the world but cannot edit, check the drawing and script permissions and reconnect to refresh the tool list.

To disconnect one client, remove its `tedit` entry. To disconnect all clients, clear **Enable local MCP server** and select **Save**.
