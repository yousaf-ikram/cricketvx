# CricketVX

A cricket statistics website powered by the **Avcros Datalink API**.

> **Data provider:** CricketVX uses **Avcros Datalink** ([avcros.com](https://avcros.com))
> as its sole data source. There is no local database and no mock data layer —
> all cricket data is requested directly from the Avcros Datalink API.
> See the [API documentation](https://avcros.com/docs).

## Overview

**CricketVX** is a static, no-build cricket website built with plain HTML,
plain CSS, and minimal vanilla JavaScript. It provides player search and player
profiles using the Avcros Datalink player endpoints.

The Avcros Datalink API is currently **under development**. Only the player
endpoints are documented:

| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/v1/cricket/players?name={query}` | Search players by name |
| `GET` | `/v1/cricket/players/{id}` | Retrieve a full player profile by ID |

Match, scorecard, team, and series endpoints are expected but not yet
available. Those pages are static placeholders until Avcros publishes the
endpoints. No fake match data is used.

## Tech Stack

| Layer | Choice |
|-------|--------|
| Markup | Plain HTML5 |
| Styling | Plain CSS (no Tailwind, no frameworks) |
| Behaviour | Vanilla JavaScript (`fetch` only, no libraries) |
| Build step | None |
| Package manager | None |
| Hosting | GitHub Pages |
| Data source | Avcros Datalink API |

There is nothing to install and nothing to compile. Open the HTML files or
serve the folder with any static file server.

## Project Structure
cricketvx/
├── index.html # Home / search
├── players.html # Player search results
├── player.html # Player profile (reads ?id= from URL)
├── css/
│ └── style.css # All styles
├── js/
│ ├── config.js # API base URL and API key
│ ├── avcros.js # fetch wrapper for Avcros endpoints
│ ├── search.js # Player search page logic
│ └── player.js # Player profile page logic
├── assets/
│ └── favicon.ico
└── README.md


## Pages

### Working against the Avcros API
- `index.html` — landing page with a search box
- `players.html` — search results for `GET /v1/cricket/players?name=...`
- `player.html?id={id}` — profile for `GET /v1/cricket/players/{id}`

### Static placeholders (awaiting Avcros endpoints)
- `match.html` — layout only, no data until match endpoints exist
- `team.html` — layout only, no data until team endpoints exist
- `series.html` — layout only, no data until series endpoints exist

## API Configuration

All Avcros calls live in `js/avcros.js`. Configuration is in `js/config.js`:

```js
// js/config.js
const AVCROS_CONFIG = {
  baseUrl: "https://api.avcros.com/v1",
  apiKey: "avcros_live_your_api_key"
};
