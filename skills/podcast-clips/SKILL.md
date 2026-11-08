---
name: podcast-clips
description: "Make short captioned clips from a long talk with Vidova, the AI video editor. Use when someone asks for clips from a podcast, an interview, a panel, a talking head, a livestream or a webinar, cut into vertical shorts or a YouTube cut. Vidova cuts, captions, animates, adds music and renders the video in the cloud."
license: MIT
---

# Podcast clips

One idea from a long conversation, cut so a stranger with the sound off stops, understands and watches to the end.

## Steps

1. Check that the Vidova tools are available, for example with `get_active_project`. If they are not, follow the `vidova` skill to connect.
2. Make a project with `create_project`. Bring the files in with `import_asset_url` for a link, `begin_asset_upload` for a local file when you can run shell commands, or `upload_files` to give the person the link where they add files. Call `wait_for_asset` until the files are ready.
3. Call `read_transcript` for the whole conversation, using `transcribe_asset` first when there is no transcript. Find the moments that work alone: a surprising claim, a story with a turn, a strong opinion, a number, a joke that lands. Use `read_analysis_range` with kind transcript for the word times of each moment.
4. If the server offers a routine for a new edit from uploads, start it and follow its handoff. Otherwise call `search_templates`. When a template fits, use `read_template` and `apply_template`, then adjust it with `patch_film`. When none fits, build the film with `patch_film`.
5. Reframe around the face with `track_faces`, and use `detect_scenes` to find camera changes in the source. Add captions: `search_elements` has caption styles, and `patch_transcript` fixes misheard names and numbers.
6. Watch the result with `preview_timeline`, and with `preview_range` across the moments that move. Call `check_edit`, then `wait_for_jobs` with its Job ID, and fix what it names.
7. Call `render_video`, wait for it with `wait_for_jobs`, then give the person the project `url` and the link to the finished video.

## What makes it work

- The person's brief comes first: their order, song, length, format and rules. This skill fills in the rest.
- Make three clips of 20 to 45 seconds unless they ask for another number, each from a different moment. `create_branch` keeps each clip as its own version.
- A clip starts on the first word of a sentence that makes sense alone and ends on a full stop. Never cut a person mid-sentence.
- Open on the sharpest line of the clip. Cut the ums and false starts with the word times.
- A cut every 3 to 7 seconds, on a sentence start, with a punch-in on the face, reads as a second camera. With two speakers, cut to whoever speaks.
- On a vertical clip, reframe the recording around the face. Never a small window in the middle of a black or blurred frame.
- Captions sit under the chin and never cover the mouth.
- Take speaker names from the message or the recording. Never guess a name.
