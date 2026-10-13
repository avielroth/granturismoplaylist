# GT Music Player

A Gran Turismo 7-style garage music player that runs in the browser. It has 104 songs from the GT5 and GT6 soundtracks and 15 cars turning in a dark studio. The Collector Level ring fills up as you listen. Car Info has each car's history and specs, and the Track List has tabs for GT5, GT6, Shop and your ★ Favourites.

## The music is not in this repo

The songs are game soundtrack rips, so they aren't uploaded anywhere. To hear them, click **Play my music…** (or press **L**) and pick the folder that has your own MP3s of the soundtrack. The files stay on your computer: the browser plays them directly and nothing is uploaded. Songs are matched by file name, using the `file` names in [`playlist.json`](playlist.json). Without music the player still runs, silently.

The folder picker needs a desktop browser: Chrome, Edge, Firefox or Safari.

## Controls

Use the keyboard, or click the remote beside the picture.

| Key | Action |
|---|---|
| Arrows | Move the cursor |
| Enter | Press the highlighted button |
| Space | Pause / play |
| F | Fast-forward |
| Page Up / Page Down (or P / N) | Previous / next song |
| M or Esc | Track List (the tab you pick is also what plays next) |
| S | Favourite the song (the browser remembers it) |
| I | Car Info |
| − / + | Volume down / up (the browser remembers it) |
| C | Retro TV look on / off |
| L | Pick your music folder |

## Hosting on Netlify

This is a static site with no build step. `netlify.toml` publishes the repo root.

1. In Netlify choose **Add new site → Import an existing project → GitHub**, then pick this repo.
2. Leave **Build command** empty and set **Publish directory** to `.` (this is the default from `netlify.toml`).
3. Deploy. Every push to `main` redeploys the site.

## Running it locally

Opening `index.html` straight from disk doesn't work, because browsers block loading the cars from `file://`. Serve the folder with any static web server instead, for example:

```bash
python -m http.server 8000
```

Then open http://localhost:8000. On `localhost` the player also looks for the songs in a `music/` folder next to the page, at the `path`s in `playlist.json`. That folder is in `.gitignore`, so it never gets committed.

## What's inside

| File | What it is |
|---|---|
| `index.html` | The whole player (three.js r170) |
| `*.gltf.json` | The 15 cars (glTF with WebP textures, packed into one file each) |
| `playlist.json` | Song titles, artists, lengths and file names (the cars take turns, one per song) |
| `fonts/` | TeX Gyre Heros, a free Helvetica clone (GUST Font Licence) |
| `lib/` | three.js r170 and its glTF loader (MIT licence, see `lib/LICENSE`) |
| `CREDITS.txt` | The car model authors and licences, and the song list |

## Credits and licences

- **Cars:** Sketchfab models under CC BY 4.0, CC BY-NC 4.0 and CC BY-NC-SA 4.0. The authors, links and changes are listed in [`CREDITS.txt`](CREDITS.txt). The Lancer Evolution VII, the Skyline R32 and the Fairlady Z are CC BY-NC and the Impreza is CC BY-NC-SA, so this project must stay non-commercial. The changed Impreza model is shared under CC BY-NC-SA 4.0 too.
- **Fonts:** TeX Gyre Heros by GUST e-foundry, GUST Font Licence.
- **three.js:** MIT licence.

This is a personal, non-commercial project. It is not affiliated with or endorsed by Sony Interactive Entertainment or Polyphony Digital. Car names and sponsor marks belong to their owners.
