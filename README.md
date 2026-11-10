# GharMap — GPS Road and House Survey MVP

A mobile-first static web app for walking/driving a route, recording its GPS trail, and marking houses on the left or right side of travel.

## Run locally

```bash
cd up-house-survey
python3 -m http.server 8080
```

Open http://localhost:8080. For real GPS access on a phone, deploy over **HTTPS** (e.g. Netlify, Cloudflare Pages, Vercel). Browser GPS requires permission and a secure context.

## Features
- Live GPS via `watchPosition`, map following and a GPS trail
- Demo mode: tap the map to trace a route and test turns
- Automatic road segment splitting on sufficiently sharp turns (heuristic, not map matching)
- Left/right house buttons, independent numbering by road segment
- Drag house markers to correct positions
- LocalStorage persistence, pause, undo, manual road split
- CSV house export and GeoJSON route + houses export
- Basic service worker caching of app shell; map tiles require network unless previously cached by browser

## Limitations and next steps
- No backend or multi-device sync yet. Export regularly; clearing browser data deletes local records.
- GPS drift can misdetect turns. The turn detector is deliberately basic and needs field testing, smoothing, and road map-matching.
- Left/right house positions are estimated 10 m from the travel point; manually drag them for accuracy.
- Roads/lanes are survey segments, not verified legal road boundaries.
- Browser background GPS is not reliable when the phone locks or app is suspended; keep the app foregrounded.
- Avoid collecting resident names or personal details without an appropriate lawful basis.
- OpenStreetMap tiles and Leaflet scripts require internet on first load; for dependable offline use, self-host assets and provide permitted offline map tiles.