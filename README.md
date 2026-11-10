# Lucy · Bangkok Rush

A mobile 3D scooter runner through Bangkok. Static HTML, CSS, JavaScript and locally vendored Three.js. No build step or external runtime services.

## Play

Thai is the default language. The header language selector switches between Thai and English and saves the preference locally.

Swipe anywhere in the game: left/right to change lanes, up to jump, down to duck under overhead barriers. Four introductory gestures teach the controls. There are no driving buttons. Arrow keys and A/D/W/S also work; Space jumps and P/Escape pauses.

At a junction, swipe in the displayed direction before reaching the corner. The input is queued; the actual road and scenery follow a quarter-circle bend. A missed turn costs one hull point. Coins build a double-score bonus. Cars move at individual speeds and animate their wheels and suspension. Near misses and completed turns award points. Three hits end the ride. Scores and preferences are stored per browser; no shared leaderboard is configured.

## Run and publish

Run `python3 -m http.server 8000` and open `http://localhost:8000`. WebGL is required. GitHub Pages serves the repository root from main.

## Rendering and mobile input

The viewport follows visualViewport and safe-area insets. Pointer Events recognize one action per swipe across the game. The HUD and notifications stay at the edges. World geometry uses a shared centerline and a moving coordinate frame through turns. Street meshes use instancing; repeated traffic models share cached geometry. Rendering density adapts to sustained load. Steering uses a frame-rate-independent damped spring.

## Checks

With Playwright and Chromium available, run `node tests/browser-smoke.cjs`. Optional environment variables: GAME_URL (default http://127.0.0.1:8000) and CHROME_PATH. Tests cover native touch gestures in four directions, Thai/English persistence, queued turns and road curvature, overhead collision clearance, absence of driving buttons/hearts, and JavaScript errors.

## Third-party code

Three.js 0.160.1 is included under the MIT license; see vendor/THREE-LICENSE.txt. Models and textures are generated locally by the game code.
