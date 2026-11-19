# December · Coming Home to Myself

A single-file self-love tracker: December monthly goals (tick days, running totals, or book tracking with pages and a finish date), daily mood and note, a daily quote, and a 2027 goals tab.

## Run it
Open `index.html` in a browser. No build step, no dependencies (fonts load from Google Fonts if online).

## Storage
- **Outside Claude:** saves to the browser's `localStorage` (key `selflove-dec-v2`) on that device only. The footer shows "Offline · saved on this device only".
- **Inside a Claude artifact (Pro and above):** the page calls `claude.use("db")` and syncs to the signed-in user's private store: doc `state` (December data) and doc `y27` (2027 tab). See `initSync()`, `save()` and `push()`.
- To sync elsewhere, replace the `remote`/`remoteY` `.get()` / `.set()` calls in `initSync()`/`push()` with your own backend (e.g. Supabase, Firebase).

## Data shape
```
state: { goals:[{id,e,n,k:"days"|"total"|"book",t,u}], done:{goalId:{day:value}},
         fin:{goalId:{day:1}}, mood:{day:1-5}, note:{day:text}, upd }
y27:   { theme, vision, items:[{id,t,c,q,s:0|1|2,note}], upd }
```
Conflict rule: the copy with the newer `upd` timestamp wins.

## Ideas to build next
Monthly targets for 2027 goals, weekly review prompts, export/import JSON backup, reminders.
