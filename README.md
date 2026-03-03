# ⚡ Speed Lab

A clean, minimal, and fully interactive performance testing web app built with React.

Speed Lab lets users measure:

* ⌨️ Typing Speed (WPM + Accuracy)
* 🖱️ Clicking Speed (CPS)
* ⚡ Reaction Time (ms)

Designed to be modern, responsive, and future-proof.

---

## 🚀 Features

### ⌨️ Typing Test

* Randomized word generation
* Real-time word validation (correct = green, incorrect = red)
* Timer starts only when user begins typing
* Accurate WPM calculation (based on correct characters / 5 / minutes)
* Accuracy percentage tracking
* Personal best tracking
* Per-test graph visualization

### 🖱️ Clicking Speed Test

* Adjustable duration: 1s / 5s / 10s / 30s
* Accurate CPS (clicks per second)
* Real-time click counter
* Personal best tracking
* Graph history per attempt

### ⚡ Reaction Time Test

* Randomized delay (red → yellow → green)
* Early click detection
* High precision timing using `performance.now()`
* Reaction rating feedback
* Graph tracking per attempt

---

## 📊 Analytics & Tracking

* Personal best calculation per mode
* Session history stored in state
* Per-mode graph visualization using Recharts
* Post-test performance popup with rating system

---

## 🎨 UI / UX

* Minimal & modern design
* Dark / Light mode toggle
* Fully responsive (mobile + desktop)
* Smooth animations via Framer Motion
* Clean card-based layout

---

## 🛠 Tech Stack

* React
* Tailwind CSS
* Framer Motion
* Recharts
* ShadCN UI components

---

## 📦 Installation

```bash
npm install
npm run dev
```

Make sure the following dependencies are installed:

```bash
npm install framer-motion recharts
```

---

## 📁 Project Structure

```
SpeedLab/
 ├── components/
 ├── SpeedTestApp.jsx
 ├── package.json
 └── README.md
```

---

## 🔮 Future Improvements

* Save history to localStorage
* Add session averages
* Export stats as JSON
* Leaderboard system
* Trend smoothing on graphs
* Sound effects for reaction mode

---

## 🧠 How Scoring Works

### WPM

Correct characters ÷ 5 ÷ minutes

### Accuracy

Correct characters ÷ total characters × 100

### CPS

Total clicks ÷ time duration

### Reaction Time

Milliseconds between green state and user click

---

## 📜 License

MIT License

---

Built for performance testing, optimization, and skill tracking.
