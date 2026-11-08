---
name: explainer-video
description: "Make an explainer video with Vidova, the AI video editor. Use when someone asks for an explainer: an idea, a product, a process, a lesson or a set of facts turned into a short animated story with the person's own voice or on-screen words. Vidova cuts, captions, animates, adds music and renders the video in the cloud."
license: MIT
---

# Explainer video

One idea made clear in under a minute, so a viewer can repeat it to a friend.

## Steps

1. Check that the Vidova tools are available, for example with `get_active_project`. If they are not, follow the `vidova` skill to connect.
2. Make a project with `create_project`. Bring the files in with `import_asset_url` for a link, `begin_asset_upload` for a local file when you can run shell commands, or `upload_files` to give the person the link where they add files. Call `wait_for_asset` until the files are ready.
3. Write the one sentence the viewer should know at the end, then the script. A hook of up to 3 seconds, three to five steps of one sentence each, and a takeaway of 3 to 5 seconds. A script the person wrote is the script.
4. If the server offers a routine for a new edit from uploads, start it and follow its handoff. Otherwise call `search_templates`. When a template fits, use `read_template` and `apply_template`, then adjust it with `patch_film`. When none fits, build the film with `patch_film`.
5. With a recorded voice, call `transcribe_asset` for the word times and cut each scene on its sentence. Without a voice, show one short line per step. Give each step its own picture: their footage, a screen, an element from `search_elements`, or a device frame from `search_stock`.
6. Watch the result with `preview_timeline`, and with `preview_range` across the moments that move. Call `check_edit`, then `wait_for_jobs` with its Job ID, and fix what it names.
7. Call `render_video`, wait for it with `wait_for_jobs`, then give the person the project `url` and the link to the finished video.

## What makes it work

- The person's brief comes first: their order, song, length, format and rules. This skill fills in the rest.
- Open on the question or the surprising fact, in the viewer's words, over a picture that already shows it.
- A step that holds two ideas becomes two steps.
- Use only facts the person gave or common knowledge. Never invent a statistic, a date, a study or a quote.
- Never use the same picture for two steps, or footage that has nothing to do with the sentence.
- Punch in on the detail the voice names, landing on the word. A caption never covers that detail.
- Make 30 to 60 seconds for social, or 60 to 120 seconds for a lesson. Use 9:16 unless they ask for YouTube, a course or a presentation.
