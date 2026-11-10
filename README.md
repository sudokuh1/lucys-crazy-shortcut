# Lucy’s Crazy Shortcut

A mobile-first three-lane scooter arcade game. Original Canvas artwork, vanilla JavaScript, no dependencies or build step.

## Run locally

Run `python3 -m http.server 8000` in this directory and open `http://localhost:8000`.

## Controls

Swipe horizontally, tap the arrow buttons, or use arrow keys / A and D. Space, P or Escape pauses. Collect hearts and snacks to fill the Cute Meter for seven seconds of double points. Shortcut events begin after 18 seconds and award 300 points for surviving. The best score is stored locally. Sound is optional and starts only after enabling it.

## GitHub Pages

1. Create a public repository named `lucys-crazy-shortcut`.
2. Upload `index.html`, `style.css`, `game.js` and this README to its root on `main`.
3. In Settings → Pages, choose **Deploy from a branch**, **main**, **/ (root)** and Save.
4. Open `https://YOUR-USERNAME.github.io/lucys-crazy-shortcut/` after deployment completes.

No backend, external assets, API keys or package installation required. Canvas scales to device pixel ratio; the game pauses when the tab is hidden. Current Safari and Chrome are supported.
