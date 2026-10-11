# Choo-Choo Loop

A 3D train game for young kids (around age 5), made for phones and tablets. Draw a railway loop that joins every station, then watch the steam train take the animal passengers for a ride.

- Drag a finger across the grass squares to lay track. It snaps into straights and curves, and each new piece plays a note.
- The track has to make one closed loop that goes through **every station**. A station's track goes straight through, along the platform.
- Trees, rocks, houses, ponds, cows, sheep and hay bales are in the way. From level 3 there's a river you can only cross on a bridge, and from level 4 a hill you can only get through by its tunnel (both straight across).
- Fixing mistakes is easy: drag back over a piece you just laid to take it away again, tap a piece to remove it, use the **eraser** to rub out whole stretches, or draw a new line straight through old track and the new line wins. The **broom** clears everything (tap it again within 5 seconds to undo).
- The **💡** button shows one way to do it with glowing dots. On the first two levels a finger shows how to draw.
- When the loop is complete the green train button starts to pulse. Press it: any leftover bits of track get tidied away, the steam engine appears in a puff of smoke at the red ★ home station, and the passengers hop aboard. Each one wears a party hat in the colour of the station they're going to. The train chuffs round the loop, stops at every station where its passengers jump off and new ones get on, and finally brings everyone back home for a party.
- If the loop isn't finished, the train gives a sad toot, red rings mark the gaps, a **?** floats over any station the track misses, and a voice says what's wrong. Nothing is lost; just fix it and press again.
- From level 6 the engine needs **water**. A gauge under the level badge shows its tank, and a full tank doesn't last the whole way round, so the loop has to pass a water tower (blue droplet sign) in time. Level 8 and up has two towers. The train stops under the tower, swings the spout down and fills up with a glug. If the tank runs dry first, the engine sputters to a stop and puffs away, a droplet bubbles over the tower and a voice says to go past it sooner. Shorten the way to the tower and try again. The train always picks whichever direction round the loop makes the water last.
- Each level has its own look, taking turns: a green **meadow**, pink **cherry blossom** with petals drifting down, **autumn** with orange trees, falling leaves and pumpkins, **snow** with snowmen, snowy pines, white roofs and frozen ponds, the **desert** with cacti, palms, camels, adobe houses, an oasis and dunes, and a **sunset** with warm light, glowing windows and fireflies. Then it starts over.
- Every level is new and made up on the spot, but always has a solution. Later levels have bigger boards, more stations and more things in the way. The game remembers which level you reached.
- 🏠 in the corner goes back to the list of all games.

## Run it

It's one page plus the sound clips and music in `assets/`. Serve the folder (for example `python -m http.server 5211`) and open it in a browser; it needs an internet connection the first time for the 3D library and the title font. No build step. Opened straight from disk it still works, but the browser won't load the clips, so you hear the built-in synthesized sounds and the device's own voice instead, and no music.

Built with [three.js](https://threejs.org/). Voices and sounds: [elevenlabs.io](https://elevenlabs.io). Music: Eleven Music.

## Play offline (add to Home Screen)

On iPhone or iPad, open the game in Safari, tap **Share → Add to Home Screen**, then open it once from the new icon while online. After that it starts full screen and works without internet. Changes I publish arrive on their own: the next online launch downloads them and the one after shows them.

(How: `manifest.webmanifest` gives the icon and full-screen mode; `sw.js`, a service worker, keeps a copy of every file the game uses, including three.js, the font, the sound clips and the music.)

## Tuning knobs

At the top of the script in `index.html`:

- `TRAIN_SPEED`: how fast the train goes (world units a second; one square is 2).
- `TRAIN_ACCEL`: how quickly it speeds up and brakes.
- `CHUFF_EVERY`: distance between chuffs and smoke puffs.
- `HINT_TIME`: how long the 💡 dots stay on the board, in seconds.
- `CAM_TILT`: how steeply the camera looks down (90 would be straight down, which is easier to draw on but looks flatter).
- `WATER_SLACK`: on water levels, how many squares further than strictly needed a full tank reaches. Raise it to make water levels easier.
- `LEVELS`: one row per level: board size, number of stations, how full the free ground gets (0 to 1), whether there's a river and a tunnel, and how many water towers there are. Levels after the last row repeat the last row.
- `THEMES` (next to the level maker): the six looks, in the order they take turns: grass, sky, light, tree and flower colours, which obstacles appear, and what falls from the sky.

At the top of the sound section in `index.html`:

- `CLIP_VOL` and `VOICE_VOL`: how loud the sound effects and the spoken lines are (0 to 1).
- `MUSIC_VOL` and `RIDE_MUSIC_VOL`: how loud the music is while drawing and during the ride.
- `MUSIC_DUCK`: how far the music drops while the voice is speaking (0.35 = to about a third).
- `MUSIC_XFADE`: seconds of each track's end blended into its start so the loop has no seam.
- `CLIP_TRIM`: per-clip volume trims that even out the clips, which ElevenLabs made at different levels (measured in the browser). Lower a number if a sound is too loud.
- `ASSET_V`: bump it after replacing any file in `assets/`, so phones don't keep the old one.

## Audio credits

Voices and sounds: [elevenlabs.io](https://elevenlabs.io). Music: Eleven Music. The credit also shows on the title screen and the win card. Every clip was made on **2026-10-11** with the ElevenLabs **Starter** (paid) plan. Starter-plan voices and sounds may be used commercially. The Eleven Music terms don't allow the tracks in "Studio Games" (games sold or made money from in any way), so this game must stay free, with no ads or payments. The music must not be offered for others to download or reuse as a music library. The clips are here only as the game's own sounds: they are not licensed to anyone else, and none of the audio is covered by any licence that may later be put on this game's code. All of it was made by AI (ElevenLabs), in a stock voice; no real person's voice was used. Terms checked on 2026-10-11 (ElevenLabs Terms of Use and Music Terms, both last updated 2026-10-09; the voice, sound effect and music_v2 models used are not marked beta).

The 3D library ([three.js](https://threejs.org/), MIT licence) and the title font ([Luckiest Guy](https://fonts.google.com/specimen/Luckiest+Guy), Apache licence) are loaded from their CDNs, not copied into this repo.

- **Spoken lines** (`assets/say-*.mp3`, 17 clips, plus 4 for the water levels below): voice "Jessica - Playful, Bright, Warm" (a stock ElevenLabs voice), model Eleven Multilingual v2. "Draw a track that joins all the stations!", "Join all the stations!", "All joined up! Press the green train!", "All aboard!", "Blue station!", "Yellow station!", "Green station!", "Purple station!", "Back home!", "Hooray! Everyone had a ride!", "Oops! The track has a gap.", "Every station needs the track!", "Draw a track from station to station!", "Trains go straight through the station!", "Cross the river on a bridge!", "Go straight through the tunnel!", "Follow the dots!".
- **Sound effects** (`assets/sfx-*.mp3`, 17 clips, plus 2 for the water levels below): ElevenLabs Sound Effects. Two steam chuffs, a toot-toot whistle, a long departure whistle, a sad droopy whistle, the station bell, brake squeal with steam hiss, idle steam hiss, a magic poof (the train appearing), a track clack, eraser rub, broom sweep, undo whoosh, a boing (passengers hopping), a soft bonk, little animals cheering, and the win fanfare.
- **Music** (`assets/music-*.mp3`, 2 tracks): Eleven Music (model music_v2), instrumental. `music-draw` (1:00), a gentle ukulele and glockenspiel loop while drawing; `music-ride` (0:45), a bouncy "chugga-chugga" tune for the train ride.

- **Water levels** (also 2026-10-11, Starter plan): 4 more spoken lines in the same voice and model, `say-water` ("The engine needs water! Go past the water tower."), `say-dry` ("Oh no! Out of water!"), `say-sooner` ("Go past the water tower sooner!") and `say-tip-tower` ("Trains go straight past the water tower!"); and 2 more sound effects, `sfx-fill` (water pouring into the tank) and `sfx-sputter` (the engine running out of steam).

The rising notes as each piece of track is laid, the "ready" chime and the hint sparkle are synthesized in the browser, and so is every sound when a clip can't load.
