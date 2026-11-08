---
name: sports-highlights
description: "Make a sports or fitness video with Vidova, the AI video editor. Use when someone asks for match highlights, a player edit, a game day video, a training or gym reel, a race or a season recap. Vidova cuts, captions, animates, adds music and renders the video in the cloud."
license: MIT
---

# Sports and fitness

Sport is moments: the release, the strike, the finish, the last rep. A good edit finds the exact frame of each one and lands it on the song's hit.

## Steps

1. Check that the Vidova tools are available, for example with `get_active_project`. If they are not, follow the `vidova` skill to connect.
2. Make a project with `create_project`. Bring the files in with `import_asset_url` for a link, `begin_asset_upload` for a local file when you can run shell commands, or `upload_files` to give the person the link where they add files. Call `wait_for_asset` until the files are ready.
3. Find each clip's peak to a tenth of a second with `read_asset`, `read_analysis_range` and `preview_frame`. Use `pin_moment` to keep it. Read the song with `detect_beats`.
4. If the server offers a routine for a new edit from uploads, start it and follow its handoff. Otherwise call `search_templates`. When a template fits, use `read_template` and `apply_template`, then adjust it with `patch_film`. When none fits, build the film with `patch_film`.
5. Build each moment in three shots: the approach rushing in, the peak on a downbeat easing to about quarter speed, then the replay from another angle.
6. Watch the result with `preview_timeline`, and with `preview_range` across the moments that move. Call `check_edit`, then `wait_for_jobs` with its Job ID, and fix what it names.
7. Call `render_video`, wait for it with `wait_for_jobs`, then give the person the project `url` and the link to the finished video.

## What makes it work

- The person's brief comes first: their order, song, length, format and rules. This skill fills in the rest.
- Open as the brief says. When it says nothing, open on the best moment or on the athlete's face.
- Keep the real sound of the strike or the net on the moment. Let the music dip for half a second before it, then come back on the next downbeat.
- End on the finish: the celebration, the touch at the wall, the last rep or a face, slowed so it still moves.
- Commit to the slow part. A timid slow-down reads as a stutter. Keep the action moving and never freeze it.
- Never crop a head or the ball out of the frame, and never warp a body.
- Use only their names, numbers, scores, teams and times. Never invent a score or a statistic.
