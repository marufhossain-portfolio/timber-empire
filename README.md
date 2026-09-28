# 🌲 TIMBER EMPIRE

Grow a tiny logging operation into a global timber empire — a polished idle/tycoon
game that runs entirely in your browser. No dependencies, no network, no images:
everything is drawn procedurally on an HTML5 Canvas and every sound is synthesized
with WebAudio.

**Live demo:** `https://<user>.github.io/timber-empire/`

---

## 🎮 Core Loop

You start as a broke lumberjack with a rusty hand saw. **Chop trees actively** to earn
logs, sell them on a fluctuating market, and reinvest into tools, workers, trucks,
factories and railways — growing from a single tree to a global empire.

Active play is always the most rewarding:

- **Timed swinging** — a meter oscillates; hit the green sweet spot for a **critical
  hit** (2–3× damage + screen shake + wood chips + vibration).
- **Stamina** — every swing costs stamina. Rest, or buy boots / energy drinks.
- **Tree fall direction** — tap left/right (or arrows/swipe) as a tree falls. Drop it
  on your cart for a bonus; it'll clear in slow motion.
- **4 tree types** — Pine, Oak, Redwood, and the rare **Golden Tree** (sparkles!).
- **Sustainability** — trees regrow; over-harvesting thins the forest and cuts income.
  Plant saplings and expand the forest. Watch the **Forest Health** meter.
- **Market** — log prices fluctuate. Store logs in your warehouse and sell high
  (or use `S` to sell all).
- **Random events** — storms, forest fires, big orders, market booms, wildlife.
- **Idle income** — workers & machines keep producing offline (capped, and always less
  than active play).

## 🚀 Progression (6 eras)

`Hand Saw Lumberjack → Axe & Cart → Chainsaw & Pickup → Sawmill Town →
Factory Complex → Global Empire`

Each era changes the world visuals and unlocks richer content. Money milestones trigger
a celebratory banner.

## 👑 Prestige

Retire and start a fresh forest to earn **Legacy Points**, spent in an 8-node skill
tree for permanent bonuses.

## 📅 Daily login

A streak-based daily reward grows each consecutive day you open the game.

## 🏆 Achievements

15 achievements with toast notifications and coin rewards.

---

## 🕹️ Controls

| Input | Action |
|---|---|
| Tap tree / `Space` / `Enter` | Swing axe |
| `←` / `→` (or tap side / swipe) | Choose fall direction |
| `1–9` | Buy shortcuts (tools 1–5, workers 6–9) |
| `S` | Sell all logs |
| `M` | Mute / unmute |
| `Esc` | Close panels |

Works with touch and mouse (pointer events). No double-tap zoom, no pull-to-refresh,
no text selection.

---

## 💾 Save system

- Auto-saves every **3 seconds**, and on tab hide / close.
- Saves the **complete state** (money, logs, stamina, era, all purchases, tree
  positions & HP, forest health, market price history, active event, prestige,
  achievements, stats, settings, timestamp).
- **Versioned** with a migration function.
- **Offline progress** (capped at 8 hours) with a "Welcome back" popup.
- **Export / Import** save as copy-paste text (base64).
- **Multi-tab protection** via a session id + `storage` event.
- All storage wrapped in `try/catch`.

---

## 🔊 Audio

All sound is synthesized with WebAudio (chop, crit, tree fall, coin, cash register,
storm, UI clicks) plus a per-era ambient drone. Starts only after your first
interaction. Mute toggle is saved.

---

## 🏃 Run locally

This is a single static site — no build step. Just serve the folder:

```bash
# Python
python -m http.server 8000
# or Node
npx serve .
# or just open index.html directly in a browser
```

Then visit `http://localhost:8000`.

> Note: the service worker needs `http://localhost` or `https://` to register.

---

## 🌐 Deploy on GitHub Pages

1. Push this folder to a repository named `timber-empire` (or anything).
2. Go to the repo → **Settings** → **Pages**.
3. Under **Build and deployment** → **Source**, choose **Deploy from a branch**.
4. Select branch **`main`** and folder **`/ (root)`** → **Save**.
5. Wait a minute; the site goes live at `https://<user>.github.io/timber-empire/`.

The `.nojekyll` file is already included so GitHub serves the raw files as-is.

To **install on your phone**: open the live URL in Chrome/Safari → **Add to Home
Screen**. It will run full-screen and offline.

---

## ⚖️ Rebalance

All balance data (costs, incomes, growth rates, timers, event chances, tree values,
era thresholds, skill costs, achievements) lives in the single `CONFIG` object at the
top of `index.html`.
