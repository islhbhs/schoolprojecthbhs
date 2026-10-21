# shooters.lol — Wildlands

A static browser survival-shooter project refactored from the uploaded single-file prototype into separate HTML, CSS and JavaScript files.

## Run locally
Open `index.html` in a modern browser. For best results, use a local static server (VS Code Live Server or `python -m http.server`) rather than opening the file directly.

## Publish with GitHub Pages
1. Create a GitHub repository and upload **all** files/folders in this project.
2. Open **Settings → Pages**.
3. Choose **Deploy from a branch**, select `main` and `/ (root)`, then Save.
4. Wait for GitHub Pages to publish and open the provided HTTPS URL.

GitHub Pages hosts static HTML/CSS/JS only; it does not run a Node/WebSocket game server. See GitHub's docs: https://docs.github.com/en/pages/getting-started-with-github-pages/what-is-github-pages

## Multiplayer prototype (PeerJS / WebRTC)
- Publish the game over HTTPS.
- Player A clicks **Multiplayer → Create Room**, then shares the displayed room code.
- Player B opens the same published game URL, clicks **Multiplayer**, pastes the code and clicks **Join Room**.
- Both players then start/play the game. Remote friend markers are drawn in the arena.

This is a lightweight peer-to-peer **presence prototype**, not yet a production-authoritative multiplayer shooter: player positions/names/health are shared, but bullets, damage, loot, bot AI, match state and anti-cheat are not server-authoritative or synchronized. PeerJS's public signalling service and WebRTC connectivity are external dependencies; some networks may require a TURN server or a self-hosted PeerServer. Do not treat client-side state as secure.

For a real competitive multiplayer release, use a dedicated authoritative server (e.g. Node.js + WebSocket/Colyseus) hosted separately on a service that supports long-running servers. Keep GitHub Pages for the frontend.

## Controls
- WASD: move
- Mouse: aim / fire
- E: pick up loot
- 1 / 2 / 3: weapon slots
- R: reload
- Esc: pause

## Notes
- Progression is stored in the local browser via `localStorage`; it does not sync across devices.
- PeerJS is loaded from unpkg at runtime, so multiplayer requires internet access.
