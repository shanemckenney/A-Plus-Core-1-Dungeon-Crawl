# A+ Core 1 Dungeon Crawl

A multiplayer, dungeon-crawl-style review game for **CompTIA A+ Core 1 (220-1101)**, built for live classroom cohorts. Students join from their own phones as party members and battle exam-domain "monsters" — Mobile Devices, Networking, Hardware, and Virtualization & Cloud — culminating in a multi-part troubleshooting boss fight.

Built as a single-file HTML app with Firebase Realtime Database for live multiplayer sync. No build step, no framework, no npm install.
# ⚔️ Core 1 Dungeon Crawl

*A live, multiplayer dungeon crawl built for classroom review nights — and a template you can steal for whatever you teach.*

---

## The Tale of How This Came to Be

Every dungeon needs an origin, and this one starts with a retired Army Sergeant First Class sitting alone at nearly midnight, class having just wrapped over Zoom, scrolling YouTube to unwind. An ad came on for a D&D-style game aimed at kids. I watched maybe ten seconds of it before my brain did the thing it does — an ADHD spike, mid-scroll, at the worst possible hour — and landed on: *that's not just for kids. That's exactly what my Core 1 review night is missing.*

I'm an instructor with the MyComputerCareer, teaching the Cyber Warrior Program — a CompTIA certification track for veterans transitioning into tech careers — entirely over Zoom. My students are adults with full-time jobs, families, a career change already underway, showing up after a long day to sit through a review session. The actual problem I'm solving for isn't "make studying fun" in the abstract — it's *how do you hold the attention of 30-plus tired adult veterans through a 40-slide lecture recap, on a screen, at the end of their day, without it feeling like homework.* That's a much harder problem than it sounds, and slides alone were losing that fight.

I've got an ADHD brain that hyperfocuses hard once something clicks, and this project is what happens when that midnight spark turns into a full Firebase-backed multiplayer RPG with voice-acted monsters, built in a single hyperfocus tunnel that didn't really end until it was done. That's more or less how everything in our classroom gets built: not a straight line, just a tunnel that eventually surfaces with something usable.

This particular tunnel started with a simple question: *what if exam review actually felt like a raid instead of a study session?* CompTIA A+ Core 1 breaks down naturally into domains — Mobile Devices, Networking, Hardware, Virtualization & Cloud — and troubleshooting scenarios already read like encounters if you squint. So the material became dungeon rooms. The exam domains became monsters. The class became a party.

The build itself was a two-AI collaboration: **Claude** (Anthropic) wrote and iterated on all of the actual game — the Firebase multiplayer logic, the scoring system, the UI, the sound design, this README you're reading right now — while **Google Gemini** generated the monster and party crest artwork from prompts describing each creature's design and mood, kept consistent across the set so they'd feel like one cohesive cast. The monster voice lines were recorded separately using **ElevenLabs**, with custom-designed voices for each character.

## What This Is Actually For

This is a **live, host-driven review game** for a classroom or Zoom cohort. Students join from their own phones as party members with a class specialty. The instructor runs a shared screen — a projector, a shared Zoom tab, whatever's in the room — and narrates the raid while the game handles scoring, HP, and pacing in real time.

It was built for CompTIA A+ Core 1 (220-1201) review specifically, but the underlying framework doesn't know or care what subject it's testing. See the **[Fork This For Your Own Subject](#fork-this-for-your-own-subject)** section below if you teach something else entirely.

## The Monsters

<table>
<tr>
<td width="30%"><img src="the-cracked-screen-wraith.png" alt="The Cracked Screen Wraith"></td>
<td>

### The Cracked Screen Wraith
*Domain: Mobile Devices*

It used to be someone's phone. Then the free flashlight app happened, and everything went downhill from there. Now it's just static, regret, and a battery that never quite holds a charge. It doesn't attack — it just flickers ominously and waits for you to say "have you tried factory resetting it."

</td>
</tr>
<tr>
<td width="30%"><img src="the-rogue-router-golem.png" alt="The Rogue Router Golem"></td>
<td>

### The Rogue Router Golem
*Domain: Networking*

Built from tangled cable and a router nobody labeled before running it through the ceiling. Slow, unbothered, and will absolutely try to convince you the problem is your ISP. Statistically speaking, it's never the golem's fault. It's always someone else's fault. That's kind of the whole bit.

</td>
</tr>
<tr>
<td width="30%"><img src="the-bent-pin-beholder.png" alt="The Bent-Pin Beholder"></td>
<td>

### The Bent-Pin Beholder
*Domain: Hardware*

Every eye on this thing used to be a RAM stick that got seated wrong. It floats, it twitches, it mutters to itself, and it will not POST no matter how nicely you ask. Somewhere inside it, three beeps are happening, and none of them are good news.

</td>
</tr>
<tr>
<td width="30%"><img src="the-shape-shifting-hypervisor.png" alt="The Shape-Shifting Hypervisor"></td>
<td>

### The Shape-Shifting Hypervisor
*Domain: Virtualization & Cloud*

Cut it down here, and two more of it spin up somewhere else — nobody ever set a budget alert, so here we are. Unnervingly calm about its own destruction, in the way of a hold-music voice that has become sentient. Elastic, by design. Your monthly bill will never quite catch all of it either.

</td>
</tr>
<tr>
<td width="30%"><img src="the-ticket-queue-lich.png" alt="The Ticket Queue Lich"></td>
<td>

### The Ticket Queue Lich
*Boss — Mixed Troubleshooting*

Every ticket you've ever ignored lives in this thing now, and it has ignored so many. It doesn't die when defeated — it just gets closed, which it will remind you is not the same thing as resolved. Three phases. No mercy. Reassigning itself to your next sprint the moment you look away.

</td>
</tr>
</table>

## How It Plays

- **Host** opens the game on a shared screen and creates a room — a 4-character code and a scannable QR code both work for joining. Built for a Zoom cohort with the host sharing their screen, though it works just as well projected in a physical classroom
- **Players** join from their own phones, pick a class with a real mechanical specialty (Field Tech, Network Mage, Cloud Cleric, Help Desk Rogue — each hits harder in their home domain), and answer using colored shape buttons so the actual question only lives on the shared screen
- Each room opens with a **monster reveal** — full portrait, voiced intro line, room for the instructor to narrate — before the fight begins
- Correct-majority answers deal a fixed hit to the monster; missed majorities cost the party HP, and the math holds the same whether there are 4 students or 40
- Each room resolves into one of four outcomes based on remaining monster HP: **escaped**, **knocked out**, **defeated**, or an instant **critical kill** if the party nails the final question above a set threshold — each with its own voice line and sound cue
- The final room is a multi-phase boss fight with sequential troubleshooting questions and phase-specific taunts
- A DM script (`DM-SCRIPT.md`) is included with full narration, pacing notes, and a quick-reference table so the instructor never has to guess what to say next

## Repo Structure

```
core1-dungeon-crawl.html      — the entire game (single file, no build step)
README.md                    — this file
DM-SCRIPT.md                 — narration script and pacing guide for running it live
the-*.png                    — monster and party crest artwork (repo root)
audio/                       — recorded monster voice lines (ElevenLabs)
```

## Setup

1. Create a Firebase project (or reuse an existing one) and enable **Realtime Database**
2. Register a Web App under Project Settings → General → "Your apps" to get your config values
3. Paste those values into the placeholder `firebaseConfig` object near the top of `core1-dungeon-crawl.html`
4. Set Realtime Database rules to scope access to just this game's path:

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

5. Host the file (GitHub Pages works well) and share the URL — or just the QR code — with students

## Fork This For Your Own Subject

Nothing about the underlying game actually knows it's teaching CompTIA. The domain-room structure, HP/scoring math, class specialties, live meter, and voice-line hooks are all generic — the only thing that's A+-specific is the content sitting inside a couple of JavaScript arrays.

To retheme this for your own subject:

1. **Edit the `ROOMS` and `BOSS` arrays** near the top of the script — each room just needs a name, an icon, a monster name, an image filename, and a list of questions with 4 options and a correct index. Swap in your own subject's domains.
2. **Generate your own monster art** — any image generator works; keeping one consistent style prompt across the set (like "dark fantasy ink illustration... isolated on a plain black background") is what makes them feel like one cohesive cast rather than five random images.
3. **Record your own voice lines** (optional) — or skip this entirely and rely on the built-in Web Audio sound effects, which need no external files at all.
4. **Rewrite `DM-SCRIPT.md`** — swap the flavor text for whatever fits your subject's "monsters."
5. **Keep the scoring math as-is** — the percentage-based hit system and class-specialty weighting were built to scale from a handful of students to a full class without any adjustment.

## Disclaimer

This tool is provided for educational and training purposes as part of classroom instruction. It is not an official CompTIA product and is not affiliated with, endorsed by, or sponsored by CompTIA. Exam objective references are used for study/review alignment only. No warranty is provided; use at your own discretion in your own classroom or training environment.

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
