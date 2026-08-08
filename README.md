# AB-Talks-Website-redesign
# Hackathon Dashboard Redesign

A mobile-first (390px) redesign of the ABTalks 60-day coding challenge: landing page, student dashboard, and a single challenge-day view. Single self-contained `index.html`, no build step, no dependencies beyond two Google Fonts.

## Route map
```
/
/dashboard
/day/12
```
Client-side router reads `location.pathname` (not hash-based), so these are real paths. `vercel.json` rewrites all paths to `index.html` so direct loads/refreshes on `/dashboard` and `/day/12` work correctly when deployed.

## Deploy
1. Push this folder to a GitHub repo.
2. Import it in Vercel (framework preset: "Other" — no build command needed).
3. Deploy. `vercel.json` handles the routing.

## Demo data
No backend, no auth — everything is mocked in-memory in `index.html`. A **"Demo profile" switcher** in the top bar lets a reviewer see all three required edge cases without needing real accounts:
- **Active** — Day 12, mid-streak, one earlier day already covered by a Grace Day
- **Fresh** — Day 1, empty profile, zero streak
- **Broken** — Day 12, a missed day (Day 8) still uncovered

## The one thoughtful idea: Grace Days
Students get **2 Grace Days per challenge** to retroactively cover a missed day within 48 hours. It's not a hidden pass — a Grace-covered day is visibly marked distinct from a normal "shipped" day on the streak grid, so recruiters still see an honest record. This exists because the real failure mode for a 60-day streak isn't laziness, it's a bad exam week — and one missed day shouldn't erase 11 days of real proof. Try it: switch to the **"Missed day" demo profile**, open **Day 8**, and use the Grace Day button — the streak recalculates live.
