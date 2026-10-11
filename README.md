# Choo-Choo Loop

A 3D train game for young kids (around age 5), made for phones and tablets. Draw a railway loop that joins every station, then watch the steam train take the animal passengers for a ride.

- Drag a finger across the grass squares to lay track. It snaps into straights and curves, and each new piece plays a note.
- The track has to make one closed loop that goes through **every station**. A station's track goes straight through, along the platform.
- Trees, rocks, houses, ponds, cows, sheep and hay bales are in the way. From level 3 there's a river you can only cross on a bridge, and from level 4 a hill you can only get through by its tunnel (both straight across).
- Fixing mistakes is easy: drag back over a piece you just laid to take it away again, tap a piece to remove it, use the **eraser** to rub out whole stretches, or draw a new line straight through old track and the new line wins. The **broom** clears everything (tap it again within 5 seconds to undo).
- The **💡** button shows one way to do it with glowing dots. On the first two levels a finger shows how to draw.
- When the loop is complete the green train button starts to pulse. Press it: any leftover bits of track get tidied away, the steam engine appears in a puff of smoke at the red ★ home station, and the passengers hop aboard. Each one wears a party hat in the colour of the station they're going to. The train chuffs round the loop, stops at every station where its passengers jump off and new ones get on, and finally brings everyone back home for a party.
- If the loop isn't finished, the train gives a sad toot, red rings mark the gaps, a **?** floats over any station the track misses, and a voice says what's wrong. Nothing is lost; just fix it and press again.
- Every level is new and made up on the spot, but always has a solution. Later levels have bigger boards, more stations and more things in the way. The game remembers which level you reached.
- 🏠 in the corner goes back to the list of all games.

## Run it

It's one page. Serve the folder (for example `python -m http.server 5211`) and open it in a browser; it needs an internet connection the first time for the 3D library and the title font. No build step. Opening `index.html` straight from disk works too.

Built with [three.js](https://threejs.org/). All sounds (chuffing, whistle, bell, notes) are made in the browser, and the spoken lines use the device's own voice.

## Play offline (add to Home Screen)

On iPhone or iPad, open the game in Safari, tap **Share → Add to Home Screen**, then open it once from the new icon while online. After that it starts full screen and works without internet. Changes I publish arrive on their own: the next online launch downloads them and the one after shows them.

(How: `manifest.webmanifest` gives the icon and full-screen mode; `sw.js`, a service worker, keeps a copy of every file the game uses, including three.js and the font.)

## Tuning knobs

At the top of the script in `index.html`:

- `TRAIN_SPEED`: how fast the train goes (world units a second; one square is 2).
- `TRAIN_ACCEL`: how quickly it speeds up and brakes.
- `CHUFF_EVERY`: distance between chuffs and smoke puffs.
- `HINT_TIME`: how long the 💡 dots stay on the board, in seconds.
- `CAM_TILT`: how steeply the camera looks down (90 would be straight down, which is easier to draw on but looks flatter).
- `LEVELS`: one row per level: board size, number of stations, how full the free ground gets (0 to 1), and whether there's a river and a tunnel. Levels after the last row repeat the last row.
