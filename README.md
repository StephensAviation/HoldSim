# Instrument Procedures Trainer

Live at <https://stephensaviation.github.io/HoldSim>

A single-page trainer for holding patterns and DME arcs. No build step, no
dependencies, no network calls. Drop the folder on any static host and it runs.

The app opens on a menu. Both exercises fly the same aeroplane on the same
panel, so the wind, airspeed, equipment and turn model carry across when you
switch between them.

Picking an exercise opens a setup page for the clearance parameters and the
difficulty; the controls there are the panel's own, moved into the page and
moved back afterwards, so there is one of each in the document.

**Holding patterns** — ATC issues a clearance, you call the entry before the fix
and fly the pattern. VOR timed legs, RNAV mileage legs, holds overhead the
station and holds at a DME fix. Graded a lap at a time on inbound leg timing,
the fix crossing, average course deviation and time on the non-holding side; the
entry is marked for being called in advance, for the right sector, and for
whether you then flew what you called.

**DME arcs** — intercept an arc off a radial, hold the distance round to the
lead radial, then turn inbound on the final course. Graded on the proportion of
the arc held inside tolerance, the worst excursion, the turn against the
computed lead radial, and the final course afterwards.

## Grading

Each item scores 100 for no error, 70 at exactly the tolerance and 0 at twice
it, with the percentage of the tolerance consumed shown beside it. Three
difficulty levels set the tolerances and nothing else — Learning, Proficient,
and Checkride, which is the instrument ACS (back to the fix within ten seconds,
course within three quarters of a dot). Changing the level re-grades the laps
already flown. Lateral navigation and timing only; a run flown with the entry
sector or ideal pattern overlay showing is flagged as practice.

## Panel

A VOR/LOC course deviation head with its own directional gyro, or a Garmin G5,
plus an optional turn coordinator and attitude indicator. A GPS navigator feeds
whichever head is fitted through the GPS/VLOC switch, so a mechanical CDI flies
an RNAV hold perfectly well — the deviation arriving at the OBS is computed
rather than received, and full scale becomes a distance instead of an angle.
The clearance sets the source when it is issued; you can still put it in the
wrong place, which is the point.

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
git commit -m "Instrument procedures trainer"
git remote add origin git@github.com:stephensaviation/HoldSim.git
git push -u origin main
```

Then Settings -> Pages -> Source: **Deploy from a branch** -> Branch: **main**,
folder **/ (root)** -> Save. The repository must be public unless you pay for
Pages on private repositories. The site appears at
`https://stephensaviation.github.io/HoldSim/` after a minute or so.

To publish updates, bump the `CACHE` constant in `sw.js`, then commit and push.

## Netlify

Drag this folder onto <https://netlify.com/drop>. To update, drag it onto the
drop zone at the bottom of the site's Deploys page.

## On an iPad

Open the URL in Safari, then Share -> Add to Home Screen. It launches full
screen, holds a screen wake lock so the display will not dim mid-lap, and works
with no signal once it has loaded once.
