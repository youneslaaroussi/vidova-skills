---
name: motion-graphics
description: Make a motion graphics piece with Vidova, the AI video editor. Use when someone asks for animated type, shapes, numbers and logos for a launch, an announcement, a promo, stats or a brand sting, with or without footage. Vidova cuts, captions, animates, adds music and renders the video in the cloud.
license: MIT
metadata:
  vidova-guide: skills/motion-graphics
---

# Motion graphics

Vidova edits this video on a real timeline and renders it in the cloud. The full guide for a motion graphics piece is on Vidova's server, so it is always current.

## Steps

1. Check that the Vidova tools are available (for example `get_active_project`). If they are not, follow the `vidova` skill to connect the Vidova MCP server.
2. Call `read_docs` with id `skills/motion-graphics`. Follow that guide for the whole edit.
3. Put the person's footage in a project: `create_project`, then `upload_files`, `import_asset_url` or `begin_asset_upload`.
4. Call `search_templates`. When one fits, use `read_template` and `apply_template`. Otherwise build the film with `patch_film`.
5. Watch the result with `preview_timeline`. Call `check_film` on the whole film and fix what it lists.
6. Call `render_video`, then give the person the project `url` and the finished video.
