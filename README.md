# 🥋 Kyorugi Scoreboard

**A real-time Taekwondo sparring scoring system for local tournaments. Judges score from their own phones, it runs fully offline, and it costs almost nothing.**

> 🚧 **Status: in progress.** Design stage. See the [roadmap](#roadmap).

## The problem

Official electronic scoring systems (sensor vests, headgear and scoring software) cost thousands of dollars. In my region of southern Mexico, most local tournaments can't afford that, so matches are scored by hand or by a single referee. That leads to mistakes and disputes.

## The idea

- **3–4 corner judges score from their own phones**, in the browser, with nothing to install.
- **A point only counts when at least 2 judges agree within a 1-second window** (consensus).
- **The scoreboard** shows on a laptop or TV for athletes and spectators.
- **Works fully offline:** the server runs on a laptop and phones connect over local Wi-Fi or a phone hotspot. No internet or mobile data needed.
- **Built for cheap phones:** a lightweight PWA, with no special hardware.

## Engineering challenges

| Challenge | Approach |
|---|---|
| Judges press at slightly different times | Group events by technique inside a consensus window, using **server time** instead of phone clocks |
| A phone disconnects mid-match | Every event has a unique ID, so retries are **idempotent**: no lost or duplicated points |
| The scoreboard must feel instant | Target **< 200 ms** from tap to scoreboard on a local network |
| Race conditions between judges | A single authoritative match state on the server; clients only send events |

## Tech stack

Node.js · Socket.IO (WebSockets) · SQLite · PWA

## Roadmap

- [ ] One match: 3 judges + scoreboard + consensus window on a local network
- [ ] Reconnection, round timer, penalties (gam-jeom)
- [ ] Tournament brackets, match history, event replay
- [ ] Pilot at a real local tournament with instructors from my region

## Author

**Ricardo Pinto**, Computer Systems Engineering student at ITTG and Taekwondo instructor, Mexico · [GitHub](https://github.com/RicardoPVX)
