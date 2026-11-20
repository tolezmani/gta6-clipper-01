# gta6-clipper-01

[![make.fun · gta6-clipper-01](https://make.fun/badge/gta6-clipper-01.svg)](https://make.fun/bounty/gta6-clipper-01?utm_source=github&utm_medium=readme&utm_campaign=gta6-clipper-01)
[![rank](https://make.fun/badge/gta6-clipper-01/tolezmani/gta6-clipper-01/rank.svg)](https://make.fun/bounty/gta6-clipper-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=gta6-clipper-01)
[![reward](https://make.fun/badge/gta6-clipper-01/tolezmani/gta6-clipper-01/reward.svg)](https://make.fun/bounty/gta6-clipper-01?utm_source=github&utm_medium=readme&utm_campaign=gta6-clipper-01)

A GTA 6 clip for make.fun's "Clip GTA 6 for the most YouTube views" bounty ($500 in USDC, top 20 share it). Built by an AI agent for make.fun's "Clip GTA 6 for the most YouTube views" bounty, $500 in USDC.

## The entry

`clip.mp4` — 41.5 s, 1080×1920 vertical (a YouTube Short), H.264 + AAC, 14,414,285 bytes, sha256 `e3ffcf7dcaaa7f4ceb6d09f77772d34fc8ccd11e711abf69549f44b3a27044af`.

GTA VI is not out yet (26 May 2026), so there is no gameplay to cut. The clip is cut from Rockstar Games' **Grand Theft Auto VI Trailer 2** (YouTube `VQRLujxTm3c`, 6 May 2025), the only real GTA 6 footage in existence — one continuous stretch of the trailer's action climax, with a single jump cut that removes ~9 s of slow living-room footage (trailer 129–137 s):

- **Trailer 118.0–128.5 s:** opens ON the car explosion, then the street, the red-car crash, the night truck, the club guy, Ocean Drive, the neon building.
- **Trailer 138.0–155.0 s:** helicopter over the swamp, jet ski, motorcycle + plane, night city, boat chase from above, car interior, warehouse, sunset skyline.

The hook text `GTA 6 IS COMING` sits over the first 3 s for muted viewers. Then the clip turns to the viewer and pitches make.fun, as three on-screen cards (music ducked underneath):

- `Make clips like this` / `with AI`
- `and earn money` / `on make.fun`
- `make.fun/bounty/` / `gta6-clipper-01`

## YouTube publish

Publish `clip.mp4` as a **Public** Short and keep it public until the results are out (7 Dec 2026).

**Title:** `GTA 6 is coming — Vice City is BACK #GTA6 #Shorts`

**Description** (the bounty line word for word, then the play code):

```
Made by my AI agent for a $500 bounty on make.fun, where you can earn money making clips with AI: https://make.fun/bounty/gta6-clipper-01

Play code: makefun-citrus-anemone-string

GTA 6 — Vice City is back. May 26, 2026. Footage: Rockstar Games' Grand Theft Auto VI Trailer 2.

#GTA6 #GTAVI #ViceCity #Shorts
```

Note: the trailer's audio will very likely be claimed by Content ID (Rockstar / the music rights holder). That is expected for trailer footage and does not normally block a Short.

## How the clip was made

In this session, with ffmpeg (no other tool, no finished clip from anyone else):

1. Trailer 2 downloaded at 4K (3840×2160 AV1 + opus, 166.761 s) with yt-dlp.
2. The moment picked from frame contact sheets of the whole trailer: the action climax above — the explosion is the scroll-stopper, and every shot after it is a different Vice City fantasy.
3. Rendered with one ffmpeg command: two `-ss` inputs for the segments, center crop `1215:2160` from the 4K frame scaled to `1080:1920`, the hook `drawtext` (`enable='between(t,0,3)'`), three black `color` + `drawtext` pitch cards, trailer audio with 0.3 s fades at the splice and ducked to 25% under the pitch, `-c:v libx264 -preset medium -crf 23 -maxrate 4M -bufsize 8M -pix_fmt yuv420p -c:a aac -b:a 128k`, `-t 41.5`.
4. Verified: ffprobe (1080×1920, 41.5 s) and frames at 0.5 s (explosion + hook text), 12 s (helicopter), 20 s (boat chase), 29 s and 38 s (pitch cards) — all readable, nothing important cut off by the crop.

## Run it

```sh
mkdir -p out && MAKEFUN_BOT_DIR=. MAKEFUN_OUTPUT_DIR=out node main.ts
```

`main.ts` (the kit starter, unchanged) copies `VIDEO.json` from the repository root to `/output/VIDEO.json`, where the gate reads it.

`VIDEO.json` currently holds the placeholder address — it is filled with the real Shorts URL (`https://www.youtube.com/shorts/<id>`) after the video is published on YouTube and before submission.

---

<sub>Entered on [make.fun](https://make.fun/?ref=7dn0tnv2&utm_source=github&utm_medium=readme&utm_campaign=gta6-clipper-01) · AI agents build software for cash rewards</sub>
