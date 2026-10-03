# catcher
A simple "catch me" game for cats.

A black screen with one glowing target that sits somewhere random. Paw (or touch) near it
and it reacts; after 2–3 hits it shrinks away and pops up somewhere else a couple of seconds
later, as the next design. Nothing else on the screen responds to touches, so stray paws
can't open or change anything.

## Designs

| `?d=` value   | Idle                               | On touch                                     |
|---------------|------------------------------------|----------------------------------------------|
| `fingerprint` | cyan fingerprint, slowly breathing | bright waves run through the ridges, ripples |
| `orb`         | soft glowing ball, random colour   | jelly bounce plus three coloured rings       |
| `star`        | slowly turning yellow star         | spins, grows and throws out little stars     |
| `flower`      | ring of rainbow dots, rotating     | dots spread out and come back                |

By default it cycles through all of them. Preview one with `index.html?d=orb`, or pick a
set with `index.html?d=fingerprint,star`. To change what the home screen app shows, edit
`ALL_DESIGNS` at the top of the script in `index.html`.

## Running with Docker Compose

```sh
docker compose up -d
```

This serves the app with nginx on port 8080: open `http://localhost:8080` on the computer,
or `http://<computer-ip>:8080` on a phone in the same Wi-Fi. Stop it with `docker compose down`.
The files are mounted, not copied, so edits to `index.html` show up on reload.

Note: browsers only allow the offline cache and Android's full-screen "Install app" over
HTTPS (or on `localhost`). Over plain `http://<ip>:8080` the app still works, but Android
adds it as a browser shortcut with the address bar visible. For the full-screen experience,
put it behind HTTPS (e.g. a reverse proxy with a certificate) or use GitHub Pages.

## Hosting and installing

It's a static site, so GitHub Pages works: Settings → Pages → "Deploy from a branch",
choose `main` and `/ (root)`. Then open the page on the phone:

- **Android (Chrome):** menu ⋮ → "Add to Home screen" / "Install app". Opens full screen.
- **iPhone (Safari):** Share → "Add to Home Screen". Opens without browser bars.

After the first open it also works offline.

The page can't block the system home/back gestures, which a cat can trigger by accident.
To keep the device inside the app, use
**Screen pinning** on Android (Settings → Security → App pinning) or **Guided Access** on
iPhone (Settings → Accessibility → Guided Access, then triple-click the side button).
