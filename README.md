# IST → World Time Converter

A single-page web app for converting times between India Standard Time (IST) and
customers' time zones across the US, Europe, and Australia. Built for scheduling
calls without doing timezone math in your head.

🔗 **Live:** https://&lt;your-username&gt;.github.io/ist-converter/

## Features

- **Live IST clock** — current India time, date, and UTC offset, updating every second.
- **Convert in any direction** — enter a time in *any* zone (or IST) and instantly see
  the IST equivalent plus every other city.
- **Pick the date** — choose the actual day (e.g. "next Tuesday") so the result reflects
  the correct weekday, date, and Daylight Saving rules for that date.
- **Day-aware** — shows "next day" / "prev day" when a conversion crosses midnight.
- **Ahead / behind badges** — each city shows how far it is from IST (green ahead, red behind).
- **DST-correct** — offsets and labels (EDT vs EST, CDT vs CST, etc.) are computed
  dynamically from the selected date, never hardcoded.

## Time zones included

| Region | Zones |
|---|---|
| **United States** | Eastern, Central, Mountain, Arizona (no DST), Pacific, Alaska, Hawaii |
| **Europe** | London, Central Europe (Paris / Berlin / Madrid) |
| **Australia** | Sydney / Melbourne, Perth |

## Example

> Customer: *"Can we do a call at 3 PM CT next Tuesday?"*

Pick **Central**, set the time to **3:00 PM**, choose that Tuesday's date →
the app shows **1:30 AM IST, Wednesday (next day)**.

## How it works

Everything runs client-side. All conversions use the browser's built-in
[`Intl.DateTimeFormat`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/DateTimeFormat)
API with [IANA time zone identifiers](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones)
(e.g. `America/Chicago`), so Daylight Saving Time is handled automatically and correctly —
including the southern hemisphere, where Australia's offsets shift opposite to the US.

## Tech

- Single self-contained `index.html` — vanilla HTML, CSS, and JavaScript.
- No build step, no dependencies, no backend, no external API calls.

## Run locally

Just open `index.html` in any modern browser. Or serve it:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Deploy (GitHub Pages)

1. Push `index.html` to a public repo.
2. **Settings → Pages → Source: Deploy from a branch** → `main` / `/ (root)`.
3. Your app goes live at `https://<your-username>.github.io/<repo>/`.
