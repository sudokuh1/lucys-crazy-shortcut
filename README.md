# Lucy · Bangkok Rush

A mobile 3D scooter runner through Bangkok. Static HTML, CSS, JavaScript and locally vendored Three.js. No build step or external runtime services.

## Play

Thai is the default language. The header language selector switches between Thai and English and saves the preference locally.

Swipe anywhere in the game: left/right to change lanes, up to jump, down or hold to duck under overhead barriers. Four introductory gestures teach the controls. There are no driving buttons. Arrow keys and A/D/W/S also work; Space jumps and P/Escape pauses.

Corners are planned 360 world units in advance, outside the visible road. Direction warnings start 110 units before the bend; the final approach slows down and is kept clear of traffic. A coin trail marks the route. At a junction, swipe in the displayed direction before reaching the corner. The input is queued; the actual road and scenery follow a quarter-circle bend. A missed turn costs one hull point. Coins build a double-score bonus. Cars move at individual speeds and animate their wheels and suspension. Near misses and completed turns award points. Three hits end the ride. Scores and preferences are stored per browser; no shared leaderboard is configured.

## Run and publish

Run `python3 -m http.server 8000` and open `http://localhost:8000`. WebGL is required. GitHub Pages serves the repository root from main.

## Rendering and mobile input

The viewport follows visualViewport and safe-area insets. Pointer Events recognize one action per swipe across the game. The HUD and notifications stay at the edges. World geometry uses a shared centerline and a moving coordinate frame through turns. Street meshes use instancing; repeated traffic models share cached geometry. Rendering density adapts to sustained load. Steering uses a frame-rate-independent damped spring.

## Checks

With Playwright and Chromium available, run `node tests/browser-smoke.cjs`. Optional environment variables: GAME_URL (default http://127.0.0.1:8000) and CHROME_PATH. Tests cover native left/right/up swipes and hold-to-duck, queued turns and road curvature, clear corner approaches, and JavaScript errors.

## Third-party code

Three.js 0.160.1 is included under the MIT license; see vendor/THREE-LICENSE.txt. Models and textures are generated locally by the game code.

## Home Screen and offline launch

The menu includes an illustrated Thai/English guide for Safari on iPhone/iPad and Chrome on Android. On a first mobile browser visit, Play opens that guide with an explicit option to continue in the browser. In standalone mode the guide is not automatically shown. A browser-provided installation prompt is offered when available.

The manifest requests standalone display and portrait orientation. Original icons are supplied at 192/512 pixels, as a maskable icon, and as a 180-pixel Apple touch icon. The service worker precaches the local shell and uses network-first fetching with a cached offline fallback. Cache names and versioned asset URLs must be updated together for future releases.

Native browser or operating-system dismissal gestures cannot be reliably blocked by a webpage. Hold-to-duck provides an alternative without on-screen driving buttons. The guide recommends starting gestures away from system edges and launching the Home Screen icon.

The browser checks also cover the first-visit installation guide, both platform instructions, native press-and-hold, the full planned bend, manifest/icon availability and offline reload. Actual iPhone installation and native system gestures require device testing.
