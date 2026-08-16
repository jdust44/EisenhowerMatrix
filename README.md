# Task Matrix

A single-page web app that plots your tasks on an Importance × Time chart, so you can see what's urgent and what can wait, all in one glance. Built to be installed as a home-screen app on your phone — no app store required.

## What it does

- **Chart**: tasks are plotted by importance (High / Med / Low) and by how many days out their deadline is. Tap a bubble to zoom in and see its full name; tap again (or tap the background) to shrink it back.
- **Time filters**: Week, Month, 6 Month, Year, or a Custom date range. Tasks outside the selected window simply don't appear on the chart.
- **Task list**: a scrollable table below the chart, sortable by name, priority, or date. Tap a row to edit or delete that task.
- **Add task**: the "Insert New Task" button opens a form for name, importance, and deadline.
- **Auto-refresh**: dates are stored as absolute values, so tasks naturally drift left on the chart as days pass. If the app is left open overnight, it checks every minute and redraws automatically at the day change.
- **Offline-friendly**: once installed, a service worker caches the app shell so it still opens without a signal.

## Files

| File | Purpose |
|---|---|
| `index.html` | The entire app — HTML, CSS, and JS in one file |
| `manifest.json` | Tells the phone this is an installable app (name, icon, launch behavior) |
| `sw.js` | Service worker; caches the app for offline use and installability |
| `icon-192.png` / `icon-512.png` | Home-screen icons |

## Data & storage

Tasks are saved in the browser's `localStorage`, scoped to whatever device and browser you installed it from. There's no server and no account — which also means **no sync between devices**. If you install it on a second phone, it starts with its own separate task list (seeded with a few example tasks on first launch).

## Hosting it yourself

GitHub Pages (free) needs a **public** repo unless you're on a paid GitHub plan:

1. Create a public repo and upload all 5 files above to its root (not inside a subfolder).
2. In the repo, go to **Settings → Pages** → set Source to "Deploy from a branch," branch `main`, folder `/ (root)` → Save.
3. Wait a minute for it to build, then visit the `https://<username>.github.io/<repo>/` URL it gives you — you should see the app itself, not a GitHub file listing.

If you'd rather not make the repo public, **Netlify** or **Vercel** both offer free static hosting without that requirement.

## Installing on your phone (Android / Samsung)

1. Open the live URL above in Chrome or Samsung Internet.
2. Tap the **⋮** menu → **Add to Home screen** (or accept the "Install app" prompt if one appears).
3. The icon on your home screen will now open the app full-screen, like a normal app.

## Known limitations

- No cross-device sync (local storage only).
- No reminders/notifications — this is a visual planner, not an alarm system.
- Very long task names still get truncated in list/chart views; tap to see the full name.
