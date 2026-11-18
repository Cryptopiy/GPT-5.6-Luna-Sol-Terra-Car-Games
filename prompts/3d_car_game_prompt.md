# Task 2: 3D Game "Road with Obstacles"

## Context
You are a game developer. Create a **fully working 3D game** as a single self-contained HTML file, using WebGL (Three.js via CDN is recommended, e.g. `https://cdnjs.cloudflare.com/ajax/libs/three.js/...`). No external 3D models or textures from remote servers — all objects must be built from primitives (boxes, cylinders, cones, etc.) and/or procedural geometry, and all textures must be programmatic (canvas textures, solid materials, gradients), or the scene can go without textures entirely (flat-colored materials).

## Game concept
Third-person view (camera positioned behind and slightly above the car, following it). The car automatically drives forward along a straight road at a constant (or gradually increasing) speed. The player only controls **horizontal movement** of the car (left/right between lanes, or free movement within the road width) to dodge obstacles.

## Required mechanics

1. **The car**
   - A simple but recognizable 3D car model built from primitives (body, roof/cabin, 4 wheels that rotate while driving, headlights).
   - Controls: left/right arrow keys or A/D — smooth horizontal movement with inertia/easing (not an instant teleport), constrained so the car cannot leave the road.
   - A slight body tilt/lean when turning left/right for realism.

2. **The road**
   - A road stretching forward endlessly (or for the full length of the level) with lane markings, and shoulders on both sides (e.g., grass or barriers).
   - The road must visually "move" toward the car (either the texture/segments scroll, or the road is made of repeating, reused segments).
   - At least 3 lanes.

3. **Obstacles**
   - Spawned along the road in different lanes (randomly or via a predefined pattern) — e.g., barrels, blocks, other cars (also buildable from primitives).
   - Obstacles should appear with increasing difficulty as progress is made (denser/harder patterns closer to the end of the level).
   - At least 15–20 obstacles per level.

4. **Collision and explosion**
   - Accurate collision detection (bounding box or bounding sphere) between the car and an obstacle.
   - On collision:
     - The car "explodes" — a visual explosion effect (particles: scattering cubes/spheres with gravity and fade-out, a flash of light/sphere, possibly a color shift to orange-red).
     - A Game Over screen appears ("You crashed!") with a "Retry" button (restarts the level from the beginning).
     - The game stops (car and road stop moving) until restarted.

5. **Finish line**
   - A clearly marked finish line/arch at the end of the road (e.g., a checkered pattern via a canvas texture, or simply a contrasting stripe).
   - On crossing the finish line:
     - The game stops and a "Level Complete!" screen is shown with the completion time (in seconds) and a "Play Again" button.

6. **Camera**
   - Third-person, positioned behind and slightly above the car, smoothly follows it (including slight lag/easing in camera movement).
   - Optional subtle sway/reaction to speed for extra dynamism.

7. **UI overlay**
   - A speed or distance-traveled indicator (meters covered / percentage of level completed).
   - A start screen with a brief explanation of the controls and a "Start" button.
   - Game Over and Victory screens should overlay the game with a semi-transparent layer and a centered panel.

## Technical requirements
- A single `index.html` file, fully self-contained (aside from the Three.js CDN include).
- Game loop driven by `requestAnimationFrame`, frame-rate independent (use delta time).
- Scene lighting (at least one directional + one ambient light); shadows are welcome (`castShadow`/`receiveShadow`) but not mandatory if they hurt performance too much.
- Controls must support key-hold (continuous smooth movement, not "one tap = one step").
- Code must correctly handle browser window resize (adapting to viewport size).
- No console errors; the game should run stably at 60 FPS on a typical laptop.

## Evaluation criteria (for the model test)
1. The game is genuinely 3D and runs without errors.
2. Controls are responsive and smooth.
3. Collisions are accurate (no clipping through obstacles, no exploding "in mid-air").
4. The explosion looks like a real effect (not just the car disappearing).
5. Win/lose logic works correctly, including restart.
6. Overall visual quality (lighting, materials, scene composition) and how "playable" it feels.

## Output format
Provide a single `index.html` file, fully ready to run in a browser.
