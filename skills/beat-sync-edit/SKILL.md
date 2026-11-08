---
name: beat-sync-edit
description: "Make a beat-synced edit with Vidova, the AI video editor. Use when someone asks for an edit cut hard to a song: a fan edit, a car or bike edit, a gaming, anime or movie montage, a phonk or hype edit. Vidova cuts, captions, animates, adds music and renders the video in the cloud."
license: MIT
---

# Beat-sync edit

A song and the best few seconds of every clip, cut so each hit of the song lands on something happening.

## Steps

1. Check that the Vidova tools are available, for example with `get_active_project`. If they are not, follow the `vidova` skill to connect.
2. Make a project with `create_project`. Bring the files in with `import_asset_url` for a link, `begin_asset_upload` for a local file when you can run shell commands, or `upload_files` to give the person the link where they add files. Call `wait_for_asset` until the files are ready.
3. Call `detect_beats` on the song for the beats, the downbeats and the drop. Read each clip with `read_asset` and note its peak moment to a tenth of a second. Those peaks are what the edit is made of. Leave out clips where the subject is small or off screen.
4. If the server offers a routine for a new edit from uploads, start it and follow its handoff. Otherwise call `search_templates`. When a template fits, use `read_template` and `apply_template`, then adjust it with `patch_film`. When none fits, build the film with `patch_film`.
5. Start 4 bars before the drop, where a bar lasts 4 x 60 / bpm seconds. Use 2 to 4 slower shots for the intro, then one beat each, then half a beat in the last bar. Put the best clip on the drop, and one beat or half a beat per shot after it. End on the strongest image, slowed so it still moves.
6. Watch the result with `preview_timeline`, and with `preview_range` across the moments that move. Call `check_edit`, then `wait_for_jobs` with its Job ID, and fix what it names.
7. Call `render_video`, wait for it with `wait_for_jobs`, then give the person the project `url` and the link to the finished video.

## What makes it work

- The person's brief comes first: their order, song, length, format and rules. This skill fills in the rest.
- Use the song they named or uploaded. Never swap it for another.
- Every shot shows the subject of the edit.
- Put every clip's peak on a beat: rush into it, slow hard to about quarter speed on the beat, and rush out. It never stops.
- Frame 0 is the thumbnail: a bright, readable frame of the subject.
- Vary the shot lengths. An even run of equal shots reads as a metronome.
- `search_effects` and `apply_effect` put one effect on the drop. Never put effects on every cut.
