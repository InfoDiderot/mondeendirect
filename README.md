# World Live Dashboard — « Le monde en direct »

A single-file HTML dashboard that puts the state of the world on one screen: local time and date, weather, news headlines, about 80 world counters (population, environment, energy, health, food and water, economy, digital, transport) and an interactive 3D globe.

**Live page:** https://infodiderot.github.io/mondeendirect/

The interface is in French.

## What it shows

- **Clock and calendar** — local time, week number, day of year, moon phase, sunrise and sunset in Brussels.
- **World cities** — current time and weather in eight cities.
- **Weather** — current conditions and a 5-day forecast for Brussels.
- **World counters** — grouped in nine panels, one line per counter.
- **3D globe** (Three.js) — real day/night side, aircraft in flight, earthquakes of the last 24 hours, ISS position.
- **News** — latest headlines from three French-language RSS feeds.

## How the numbers are produced

Each figure carries one of three labels:

| Label | Meaning |
|---|---|
| **Direct** (live) | Fetched from a public API while the page is open. |
| **Estimé** (estimate) | Not a measurement. The latest published annual total is spread evenly over the year and counted up from 1 January or from midnight. |
| **Référence** | A fixed published figure. |

The source of every counter is shown on hover, or under each line with the **Sources** button. Annual totals come from the UN, World Bank, IEA, Ember, FAO, WHO, UNCTAD and similar bodies; they were entered by hand and should be checked before being quoted.

## Live data sources (no API key)

| Block | Service |
|---|---|
| Weather | Open-Meteo |
| Earthquakes | USGS |
| Aircraft in flight | OpenSky Network (anonymous quota, refreshed every 15 minutes) |
| ISS position | wheretheiss.at |
| Exchange rates | Frankfurter (ECB reference rates) |
| News | RSS feeds through public CORS relays — the most fragile block |
| Coastlines on the globe | Natural Earth via the `world-atlas` package |

If a service does not answer, its block is marked unavailable and the rest of the page keeps working. Ships and electricity prices have no free key-less source, so the page links to MarineTraffic and Electricity Maps instead.

## Usage

Open `index.html` in a browser, or host it on any static web server. There is no build step and no dependency to install; Three.js and two web fonts load from public CDNs.

Buttons in the header switch between dark and light themes, enlarge the text for projection, show the sources, and toggle full screen. To change the home city, the list of cities or the news feeds, edit the `HOME`, `CITIES` and `FEEDS` constants at the top of the script.

## Credits

Inspired by Worldometers, World Metrics, Horloge de la planète, Unitconv world counters and Electricity Maps. All counters are recomputed from the primary sources named in the page.
