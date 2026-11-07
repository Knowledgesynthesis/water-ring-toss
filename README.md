# Water Ring Toss

The handheld water game (輪投げ, *wanage*), rebuilt in 3D in a single HTML file. Pump water jets to blast rings off the bottom of the tank, tilt the toy to steer them as they sink, and hook every ring onto the pegs.

Open `index.html` in a browser, or serve the folder with any static host such as GitHub Pages. It loads Three.js and two Google Fonts from a CDN and has no build step.

## Controls

| | Phone | Keyboard and mouse |
|---|---|---|
| Pump left / right jet | Hold the left or right half of the toy's base | `Z` / `X` (also `J` / `K`, the Shift keys) · `Space` pumps both |
| Tilt | Tilt the phone, or drag across the tank | `←` / `→` (also `A` / `D`), or drag across the tank |
| Pause / restart / mute | Pause button | `P` or `Esc` · `R` · `M` |

On iPhone, the game asks for motion access when you tap Play. If the sensor isn't available, it switches to drag steering. You can switch steering modes from the title screen or the pause menu.

## Levels

Five levels: Lagoon, Tide Pool, Coral Reef, Undertow (a tidal current that keeps changing direction) and The Deep. The timer starts on your first pump. Beat the level's target time for three stars. Progress and best times are saved in the browser.

## How it works

- **Rings are real rigid bodies.** Each ring is a torus simulated with substepped XPBD (extended position-based dynamics), with collisions sampled around the ring. A ring only scores when it has physically threaded over a peg and stays there.
- **The water is simulated.** A small 2D stable-fluids grid with vorticity confinement carries the swirls, wakes and recirculation. An analytic plume adds the jet core on top. Rings, bubbles, glitter and confetti all move with that flow. Rings feel more drag face-on than edge-on and turn broadside to the flow, so they sink flat and flutter like the real toy.
- **Tilt changes gravity.** Tilting rotates gravity in the tank's frame. The air pocket keeps its volume, so the water surface stays level as the toy tilts.
- **Rendering.** Custom shaders draw the animated caustics, light shafts, the waterline, and soft ring shadows on the printed back card. The back card art, badge and all sounds are generated in code, so the game ships no image or audio files.
