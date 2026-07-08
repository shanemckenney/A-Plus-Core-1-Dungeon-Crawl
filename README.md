# Core 1 Dungeon Crawl

A multiplayer, dungeon-crawl-style review game for **CompTIA A+ Core 1 (220-1101)**, built for live classroom cohorts. Students join from their own phones as party members and battle exam-domain "monsters" — Mobile Devices, Networking, Hardware, and Virtualization & Cloud — culminating in a multi-part troubleshooting boss fight.

Built as a single-file HTML app with Firebase Realtime Database for live multiplayer sync. No build step, no framework, no npm install.

## How it works

- **Host** opens the file on a shared screen (projector/TV) and creates a room.
- **Players** join from their phones using a 4-character room code, pick a class (cosmetic), and answer questions using colored/shaped buttons — the actual question and answer text only appears on the host screen, so everyone has to watch the room.
- Correct majority answers damage the current room's monster; missed rounds cost the party HP.
- Progress is tracked through each exam domain via the corridor bar at the top of the host screen, ending in a boss fight and leaderboard.

## Setup

1. Create a Firebase project (or reuse an existing one) and enable **Realtime Database**.
2. Register a Web App under Project Settings → General → "Your apps" to get your config values.
3. Paste your `firebaseConfig` values into the placeholder object near the top of `core1-dungeon-crawl.html`.
4. Set Realtime Database rules to scope read/write access to the `dungeonCrawl` path only (see rules example below).
5. Host the file (e.g. GitHub Pages) and share the URL with students.

### Example database rules
```json
{
  "rules": {
    "dungeonCrawl": {
      ".read": true,
      ".write": true
    },
    "$other": {
      ".read": false,
      ".write": false
    }
  }
}
```

## Editing the question bank

All questions live in the `ROOMS` and `BOSS` arrays inside the `<script>` block. Each question is a simple object with `q`, `options`, and `correct` (index of the correct option) — no build tooling required to update content.

## Disclaimer

This tool is provided for educational and training purposes as part of classroom instruction. It is not an official CompTIA product and is not affiliated with, endorsed by, or sponsored by CompTIA. Exam objective references are used for study/review alignment only. No warranty is provided; use at your own discretion in your own classroom or training environment.
