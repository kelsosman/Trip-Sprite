# ✦ Trip Sprite

**A distance-aware, dog-friendly, budget-smart weekend trip planner.**

Trip Sprite is a frontend demo for an AI-powered trip planning app. Built as part of an AI-assisted development portfolio, it showcases a full planning wizard UI with destination tiles, multi-day itineraries, budget breakdowns, packing lists, and group-ready share summaries.

---

## 🌄 Features

- **6-step planning wizard** — trip basics, vibes, group personality profiles, transport, lodging, and flex toggles
- **Destination tile system** — 3–5 matched destinations with drive time, budget, dog-friendliness, and highlight activities
- **Full itineraries** — day-by-day plans with weather-aware alternates and activity timing
- **Budget breakdowns** — per-person cost estimates across gas, lodging, food, and activities
- **Specialized packing lists** — only the unusual stuff (microspikes, dog booties, hot springs gear)
- **Group share card** — one-tap copy for group chat with budget snapshot and booking links
- **Flex toggles** — dog on/off, budget up/down, more relaxing, more adventurous, region swap
- **Booking links** — BringFido, Airbnb, VRBO, AllTrails, and Google Maps per destination

---

## 🚀 Getting Started

This is a static HTML/CSS/JS project. No build step required.

```bash
git clone https://github.com/YOUR_USERNAME/trip-sprite.git
cd trip-sprite
open index.html
```

Or serve locally:

```bash
npx serve .
# or
python3 -m http.server 8080
```

---

## 🤖 AI Integration (not included in this repo)

This repo is the **frontend shell** — the UI, wizard flow, and demo data. The full Trip Sprite experience is powered by the **Claude API** (by Anthropic).

### Where AI plugs in

All AI integration points are marked with `// [AI]` comments in `js/wizard.js`. Key hooks:

| Step | What the AI does |
|------|-----------------|
| Step 5 load | Generates 3–5 destination tiles based on user inputs |
| Destination pick | Generates the full itinerary for the chosen destination |
| Flex toggle | Recalculates destinations + itinerary with updated params |
| Share card | Formats a group-ready trip summary |

### Claude API call pattern (not in this repo)

```javascript
// Example: generate destination tiles
const response = await fetch("https://api.anthropic.com/v1/messages", {
  method: "POST",
  headers: {
    "Content-Type": "application/json",
    "x-api-key": process.env.CLAUDE_API_KEY,
    "anthropic-version": "2023-06-01"
  },
  body: JSON.stringify({
    model: "claude-sonnet-4-20250514",
    max_tokens: 1000,
    system: "You are Trip Sprite, a weekend trip planner...",
    messages: [{ role: "user", content: JSON.stringify(userInputs) }]
  })
});
```

### Data sources used by the AI version

- **Reddit** (r/solotravel, r/Colorado, regional subreddits) — hidden gems and current condition reports
- **Lonely Planet** — destination overviews and cultural context
- **AllTrails** — trail conditions, dog-friendly filters, recent comments
- **BringFido** — dog-friendly lodging, no-pet-fee properties
- **Airbnb / VRBO** — cabin and unique stay availability
- **Weather API** — current + forecast for weather-aware alternates

---

## 📁 Project Structure

```
trip-sprite/
├── index.html          # Main app shell
├── css/
│   └── style.css       # All styles (CSS variables, responsive)
├── js/
│   ├── data.js         # Demo destination + itinerary data
│   └── wizard.js       # Wizard logic, state, rendering
└── README.md
```

---

## 🎨 Design

- **Typography**: Fraunces (display/serif) + DM Sans (body)
- **Color palette**: Warm cream, terracotta, sage, gold — inspired by Utah desert landscapes
- **Aesthetic**: Editorial travel mag meets practical planning tool
- **Fully responsive** — mobile-first layout

---

## 📍 Demo Destinations

The demo includes three fully built-out destinations from Denver, CO:

| Destination | Drive | Budget | Vibe |
|-------------|-------|--------|------|
| **Moab, UT** | 3.5 hrs | $$–$$$ | Red rock, arches, stargazing |
| **Salida, CO** | 2.5 hrs | $–$$ | Hot springs, artsy, hiking |
| **Pagosa Springs, CO** | 4 hrs | $$–$$$ | Hot springs, wellness, San Juans |

---

## 🛠️ Built With

- Vanilla HTML / CSS / JavaScript (no framework required)
- [Fraunces](https://fonts.google.com/specimen/Fraunces) + [DM Sans](https://fonts.google.com/specimen/DM+Sans) via Google Fonts
- Claude AI (Anthropic) — powers the full AI version

---

## 📄 License

MIT — free to use, fork, and build on.

---

*Built with Claude · Part of an AI-powered development portfolio*
