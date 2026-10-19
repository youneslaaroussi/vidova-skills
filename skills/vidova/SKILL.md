---
name: vidova
description: Edit videos with Vidova, an AI video editor with a real timeline. Cut clips, add captions, music, voiceover, motion graphics and effects, and render in the cloud. Use when someone wants a video made or edited from their footage, photos or an idea.
license: MIT
metadata:
  mcp-server: https://mcp.vidova.ai/mcp
---

# Vidova

Vidova is an AI video editor. Its MCP server gives you the editor's tools: projects, uploads, the timeline, templates, effects, captions, music, previews and cloud renders. The person sees every change in the web editor at https://editor.vidova.ai.

## Connect

If the Vidova tools are not available, add the remote MCP server and sign in with a Vidova account when the client asks.

- Server URL: `https://mcp.vidova.ai/mcp` (Streamable HTTP, OAuth sign-in)
- Claude Code: `claude mcp add --transport http vidova https://mcp.vidova.ai/mcp`
- Other clients: add a remote MCP server with the URL above.

## How to edit

1. Start with `get_active_project`, or pick a project with `list_projects` and `open_project`, or make one with `create_project`.
2. Bring in footage with `upload_files`, `import_asset_url` or `begin_asset_upload`, then `wait_for_asset`.
3. Watch the film with `preview_timeline` before you suggest or make edits.
4. For a whole new edit of a known kind (a product ad, podcast clips, a music video, a travel recap and more), call `read_docs` with id `skills` and read the guide that matches.
5. Call `search_templates` first. When a template fits, `read_template` shows its slots and `apply_template` builds the film. Refine it with `patch_film`.
6. Before the first `patch_film` or `replace_component` that needs them, call `load_skill` with the skills the tool names.
7. Before you render and before you say the edit is done, call `check_film` on the whole film and fix what it lists.
8. Render with `render_video`. Give the person the project `url` so they can open it.

Pass the project's id as `projectId` on every project tool. Another session on the same account can open a different project between your calls.
