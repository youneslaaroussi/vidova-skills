---
name: family-video
description: "Make a family video with Vidova, the AI video editor. Use when someone asks for a family edit from the person's own clips and photos: a summer, a holiday, a year with the kids, a tribute, a wedding or an anniversary. Vidova cuts, captions, animates, adds music and renders the video in the cloud."
license: MIT
---

# Family video

The person's own clips of people they love, cut to music, made to be shared in the family chat.

## Steps

1. Check that the Vidova tools are available, for example with `get_active_project`. If they are not, follow the `vidova` skill to connect.
2. Make a project with `create_project`. Bring the files in with `import_asset_url` for a link, `begin_asset_upload` for a local file when you can run shell commands, or `upload_files` to give the person the link where they add files. Call `wait_for_asset` until the files are ready.
3. Read every clip and photo with `read_asset`: the moment with the most feeling and its time, where the faces are, whether its sound is worth keeping, and whether it is dark, shaky or soft.
4. If the server offers a routine for a new edit from uploads, start it and follow its handoff. Otherwise call `search_templates`. When a template fits, use `read_template` and `apply_template`, then adjust it with `patch_film`. When none fits, build the film with `patch_film`.
5. Cut to the music. Find a track with `search_stock` kind music, add it with `import_stock`, and read it with `detect_beats`. Grade every clip to one look.
6. Watch the result with `preview_timeline`, and with `preview_range` across the moments that move. Call `check_edit`, then `wait_for_jobs` with its Job ID, and fix what it names.
7. Call `render_video`, wait for it with `wait_for_jobs`, then give the person the project `url` and the link to the finished video.

## What makes it work

- The person's brief comes first: their order, song, length, format and rules. This skill fills in the rest.
- Use fewer, better moments, and leave out the soft, dark and shaky clips. A 25 second edit of eight good moments beats 60 seconds of everything.
- Make 20 to 40 seconds for sharing, or up to 60 seconds for a tribute.
- Open on the best moment, already happening, with people in frame 0.
- Cut every two beats in the lively parts. A hug or a sentence gets a whole bar. A wedding or a tribute is slower.
- Lower the music once for 1 to 2 seconds under a real sound, such as a laugh, then bring it back on a downbeat.
- End on the warmest wide shot for 3 seconds or more, still moving, with the music fading out with the picture.
- Use the names, places and years they wrote. Never invent them. Never darken a face, and keep text off faces.
