---
name: travel-recap-video
description: "Make a travel recap with Vidova, the AI video editor. Use when someone asks for a trip video from the person's clips: a holiday, a road trip, a city break or a honeymoon, with the places on a map or in titles, cut to the beat. Vidova cuts, captions, animates, adds music and renders the video in the cloud."
license: MIT
---

# Travel recap

A trip told in under a minute, so the person relives it and their friends want to go.

## Steps

1. Check that the Vidova tools are available, for example with `get_active_project`. If they are not, follow the `vidova` skill to connect.
2. Make a project with `create_project`. Bring the files in with `import_asset_url` for a link, `begin_asset_upload` for a local file when you can run shell commands, or `upload_files` to give the person the link where they add files. Call `wait_for_asset` until the files are ready.
3. Work out where they went, in what order and when, from the message, the file names and what `read_asset` shows (landmarks, signs, food, dates). For each clip, note the place, the moment, and whether its sound is worth keeping.
4. If the server offers a routine for a new edit from uploads, start it and follow its handoff. Otherwise call `search_templates`. When a template fits, use `read_template` and `apply_template`, then adjust it with `patch_film`. When none fits, build the film with `patch_film`.
5. Cut on the downbeats. Find a track with `search_stock` kind music, add it with `import_stock`, and read it with `detect_beats`. `search_elements` has maps and route graphics for the stops.
6. Watch the result with `preview_timeline`, and with `preview_range` across the moments that move. Call `check_edit`, then `wait_for_jobs` with its Job ID, and fix what it names.
7. Call `render_video`, wait for it with `wait_for_jobs`, then give the person the project `url` and the link to the finished video.

## What makes it work

- The person's brief comes first: their order, song, length, format and rules. This skill fills in the rest.
- Build a journey: leaving, getting there, the best days, the last evening.
- Open on the most striking shot, already moving, with the place name or the start of the route.
- Speed up toward the best days. Hold the last evening for 3 to 4 seconds while it keeps moving.
- Name each place once, on the first shot of its section. Text stays off landmarks and faces.
- Keep the real sound where it adds something: waves, a street musician, a laugh.
- Make 20 to 45 seconds for a short, or 60 to 90 seconds for a 16:9 film. Never invent a place.
