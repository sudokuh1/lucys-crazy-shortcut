# Lucy’s Crazy Shortcut — Bangkok Ride

A mobile-first 3D scooter runner through a stylized Bangkok. Static HTML, CSS and JavaScript with a locally vendored Three.js renderer. Original procedural models, Canvas textures and Web Audio. No build step, backend, external asset service or API keys.

## Play

Swipe left/right anywhere on the game surface to change lanes. Swipe up to jump over cones and potholes. Large on-screen buttons and arrow keys / A, D, W, Space are also supported. P/Escape pauses. The first ride includes an interactive three-gesture tutorial.

At a junction, follow the large arrow by swiping or tapping the corresponding direction. Turns award 250 points. A missed turn is assisted. Shortcut phases add traffic and award 500 points for surviving. Collect ten hearts for seven seconds of double points; consecutive pickups raise the multiplier. Three collisions end the ride. Best score and tutorial completion persist in localStorage. Sound is opt-in.

## Run

Run `python3 -m http.server 8000` from the project root and open `http://localhost:8000`. WebGL is required. Current mobile Safari and Chrome support it.

## Deploy

GitHub Pages: Settings → Pages → Deploy from a branch → main → / (root). All runtime dependencies are included in the repository.

## Mobile rendering

The layout follows `visualViewport` and safe-area insets, reserves space above browser overlays, and prevents page scrolling inside the game. Pointer Events recognize one action per swipe over the entire play area. Camera distance adapts to narrow portrait screens. Device pixel ratio is capped at 1.65. Static scenery is merged, traffic models share cached geometry, and lighting uses inexpensive blob shadows. Animation is delta-time based. The game pauses when the tab is hidden.

## Third-party code

`vendor/three.min.js`: Three.js 0.160.1, MIT license. See `vendor/THREE-LICENSE.txt`. Models and textures are generated locally by the game code.
