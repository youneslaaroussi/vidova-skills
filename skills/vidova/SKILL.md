---
name: vidova
description: "Edit videos with Vidova, an AI video editor with a real timeline. Cut clips, add captions, music, motion graphics and effects, and render in the cloud. Use when someone wants a video made or edited from their footage and photos."
license: MIT
---

# Vidova

Vidova is an AI video editor. Its MCP server gives you the editor's tools: projects, uploads, the timeline, templates, effects, captions, music, previews and cloud renders. The person sees every change in the web editor at https://editor.vidova.ai.

## Connect

This plugin brings the Vidova MCP server with it. The person signs in with a Vidova account when the client asks. If the tools are still not available, the setup for each client is at https://vidova.ai/docs/mcp.

## How to edit

1. Start with `get_active_project`, or pick a project with `list_projects` and `open_project`, or make one with `create_project`.
2. Bring in the files with `import_asset_url` for a link, `begin_asset_upload` for a local file when you can run shell commands, or `upload_files` to give the person the link where they add files. Then call `wait_for_asset`.
3. Read the footage with `read_asset`, `read_transcript` and `search_footage`. Watch an existing film with `preview_timeline` before you suggest or make edits.
4. If the server offers a routine for a new edit from uploads, start it and follow its handoff. Otherwise call `search_templates`. When a template fits, `read_template` shows its slots and `apply_template` builds the film. Refine it with `patch_film`. When none fits, build the film with `patch_film`.
5. Find graphics and captions with `search_elements`, effects with `search_effects`, and music, sound effects and device frames with `search_stock`.
6. Before you render, call `check_edit`, then `wait_for_jobs` with its Job ID, and fix what it names.
7. Render with `render_video` and wait for it with `wait_for_jobs`. Give the person the project `url` and the link to the finished video.

Pass the project's id as `projectId` on every project tool. Another session on the same account can open a different project between your calls.

Vidova works on the footage the person provides. Use their facts, names and numbers, and never invent them. Follow their brief: their order, song, length, format and rules come first. The skills in this plugin cover the common kinds of edit, such as `product-ad-video`, `podcast-clips` and `beat-sync-edit`.
