# Vidova

<img src="assets/logo.png" alt="Vidova" width="96" align="right">

Vidova is an AI video editor that your agent drives. Ask for a product ad, podcast clips, a travel recap or a music video, and the agent cuts your footage on a real timeline, adds captions, music, voiceover, motion graphics and effects, and renders the video in the cloud. You can open every project in the web editor at [editor.vidova.ai](https://editor.vidova.ai) and keep editing by hand.

This repository holds the Vidova MCP server configuration and the Vidova skills for Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Kiro and other agents.

## Install

**Claude Code**

```
/plugin marketplace add youneslaaroussi/vidova-skills
/plugin install vidova@vidova
```

**Skills only (any agent that reads Agent Skills)**

```
npx skills add youneslaaroussi/vidova-skills
```

**Gemini CLI**

```
gemini extensions install https://github.com/youneslaaroussi/vidova-skills
```

**Any MCP client**

Add a remote MCP server with this URL and sign in with your Vidova account when the client asks:

```
https://mcp.vidova.ai/mcp
```

## Skills

| Skill | What it makes |
| --- | --- |
| `vidova` | Any edit: connects the server and runs the editing loop |
| `product-ad-video` | A 6 to 30 second product ad or UGC-style ad |
| `podcast-clips` | Captioned vertical clips from a podcast, interview or talk |
| `music-video` | A music video, visualizer or lyric video |
| `travel-recap-video` | A trip video with places on a map or in titles |
| `birthday-video` | A birthday reel or a montage of photos and wishes |
| `explainer-video` | A short animated explainer with voiceover or on-screen words |
| `motion-graphics` | Animated type, numbers and logos for a launch or promo |
| `sports-highlights` | Match highlights, player edits and training reels |
| `event-recap-video` | An event recap or aftermovie |
| `beat-sync-edit` | An edit cut hard to the beat of a song |
| `family-video` | A family montage, tribute, wedding or holiday video |

## Example prompts

- "Cut these clips into a 30-second product ad with music and captions."
- "Turn this podcast episode into five vertical clips with captions."
- "Make a beat-synced travel recap from my trip footage."

## Links

- Website: https://vidova.ai
- Privacy policy: https://vidova.ai/privacy
- Terms: https://vidova.ai/terms
- Support: contact@vidova.ai

## License

MIT. See [LICENSE](LICENSE).
