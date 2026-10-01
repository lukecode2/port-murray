# Port Murray site: how it's published

`site/` is generated (gitignored here) by `run.py site`: `index.html` (the tabbed page), `map.html` + `map-data.js` (Leaflet + OpenStreetMap, no API key) and `dates.ics`.

It is published to GitHub Pages from a separate public repo, **lukecode2/port-murray**, through a local clone in `data/site_repo/` (also gitignored):

- `run.py site`: build locally only, never pushes.
- `run.py site --publish`: build, copy into the clone (its `.git` is kept), commit `Update <date>`, `git pull --rebase`, then `git push`. "Nothing to commit" counts as success. The noon job runs this every day.
- `run.py site --setup` (one time, already done): `gh auth status` → `gh auth setup-git` → `gh repo create lukecode2/port-murray --public` → clone → set the commit name to "Port Murray" with the GitHub no-reply email → first push → enable Pages from `main` `/`.

Live at https://lukecode2.github.io/port-murray/. Every page carries `noindex,nofollow`.

GitHub limits: the site can be at most 1 GB; the repo has a recommended limit of 1 GB; bandwidth has a soft cap of 100 GB/month; builds have a soft limit of 10 per hour. Daily pushes of about 1 MB are far inside these. Photos are linked from their sources, not stored, so expired Craigslist and Facebook images show as missing.

OpenStreetMap tiles: light personal traffic is within the OSM tile usage policy, and attribution is on the map.
