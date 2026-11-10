# Lucy’s Crazy Shortcut — Bangkok Rush

A three-lane scooter runner with a rear chase camera, perspective road, original Canvas artwork and procedural Web Audio. Built with vanilla HTML, CSS and JavaScript. No dependencies, build step, backend or external assets.

## Play

Swipe left/right or use A/D and arrow keys to dodge. Swipe up, press Up/W/Space, or tap Jump to clear cones and potholes. Cars and tuk-tuks must be dodged. Three hits end the ride. P/Escape or the pause button pauses; hiding the tab also pauses.

Collect ten hearts or snacks to trigger seven seconds of double points. Consecutive pickups increase the score multiplier. Near misses award 50 points. Shortcut events start after twelve seconds and award 500 points for surviving. Highscores are stored in localStorage.

Sound is opt-in. Enable it with the Sound button for the engine, wind, arcade rhythm, horns and gameplay effects.

## Local development

Run `python3 -m http.server 8000` and open `http://localhost:8000`. There are no package installation steps.

## Hosting

Serve the repository root as a static site. GitHub Pages: Settings → Pages → Deploy from a branch → main → / (root).

## Rendering

World-space objects use a shared perspective projection for the road, traffic and scenery. Collisions use lane position and longitudinal distance, independent of screen resolution. Canvas output uses device pixel ratio capped at two. Movement uses delta time and requestAnimationFrame. Mobile controls use Pointer Events with touch scrolling disabled inside the game.
