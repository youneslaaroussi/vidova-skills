---
name: product-ad-video
description: "Make a short product ad with Vidova, the AI video editor. Use when someone asks for a product ad, a UGC-style ad, a launch or drop video, or a promo with a price or offer, from product footage or photos, for Reels, TikTok, Shorts or a store page. Vidova cuts, captions, animates, adds music and renders the video in the cloud."
license: MIT
---

# Product ad

One product, one promise, one action, in the time it takes to scroll past.

## Steps

1. Check that the Vidova tools are available, for example with `get_active_project`. If they are not, follow the `vidova` skill to connect.
2. Make a project with `create_project`. Bring the files in with `import_asset_url` for a link, `begin_asset_upload` for a local file when you can run shell commands, or `upload_files` to give the person the link where they add files. Call `wait_for_asset` until the files are ready.
3. Read each file with `read_asset`: the best angle, the moment of use, where the product sits in the frame. Use `remove_background` on a logo that sits on a box.
4. If the server offers a routine for a new edit from uploads, start it and follow its handoff. Otherwise call `search_templates`. When a template fits, use `read_template` and `apply_template`, then adjust it with `patch_film`. When none fits, build the film with `patch_film`.
5. Cut on the downbeats of the music. Find a track with `search_stock` kind music, add it with `import_stock`, and read its beats with `detect_beats`.
6. Watch the result with `preview_timeline`, and with `preview_range` across the moments that move. Call `check_edit`, then `wait_for_jobs` with its Job ID, and fix what it names.
7. Call `render_video`, wait for it with `wait_for_jobs`, then give the person the project `url` and the link to the finished video.

## What makes it work

- The person's brief comes first: their order, song, length, format and rules. This skill fills in the rest.
- Show the product in use, or its best detail, in the first second. No logo first and no black frame.
- A 15 second ad has four parts: the hook to 1 s, the reason to 9 s (the problem and the fix, or three details, one idea per shot), the peak to 12 s with the offer said once, and the product still moving with the brand and the action to the end. Scale this to 6 or 30 seconds.
- Use 8 to 10 shots in 15 seconds, with lengths that follow the beat.
- Use only the person's facts. Never invent a feature, a price, a claim or a review. Add no medical or performance claim unless they wrote it.
- Keep the product's true colours, and keep it the sharpest thing in the frame. Text never sits on the product or on a face.
- Use 9:16 for Reels, TikTok and Stories unless they say otherwise, 1:1 or 4:5 for a feed, and 16:9 for YouTube or a website. For an app or a website, `search_stock` has device frames.
