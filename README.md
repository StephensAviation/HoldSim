# VOR Holding Trainer

A single-page holding pattern trainer. No build step, no dependencies, no network
calls. Drop the folder on any static host and it runs.

## Files

| file | purpose |
|---|---|
| `index.html` | the whole application |
| `manifest.webmanifest` | makes it install to a Home Screen as a standalone app |
| `sw.js` | offline cache — bump `CACHE` when you deploy a change |
| `icon-*.png` | app icons, including a 180px `apple-touch-icon` for iOS |
| `.nojekyll` | stops GitHub Pages running the files through Jekyll |
| `_headers` | Netlify-only cache rules, ignored by every other host |

Every path in the app is relative, so it works from a repository subpath such as
`https://you.github.io/vor-hold/` just as well as from a domain root.

## GitHub Pages

```bash
git init -b main
git add .
git commit -m "VOR holding trainer"
git remote add origin git@github.com:YOURNAME/vor-hold.git
git push -u origin main
```

Then Settings -> Pages -> Source: **Deploy from a branch** -> Branch: **main**,
folder **/ (root)** -> Save. The repository must be public unless you pay for
Pages on private repositories. The site appears at
`https://YOURNAME.github.io/vor-hold/` after a minute or so.

To publish updates, bump the `CACHE` constant in `sw.js`, then commit and push.

## Netlify

Drag this folder onto <https://netlify.com/drop>. To update, drag it onto the
drop zone at the bottom of the site's Deploys page.

## On an iPad

Open the URL in Safari, then Share -> Add to Home Screen. It launches full
screen, holds a screen wake lock so the display will not dim mid-lap, and works
with no signal once it has loaded once.
