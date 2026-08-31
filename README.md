# 🎃 Candy or Potato?!

A haunted game for your front porch. One big button, one spooky
slot machine, and a kid's fate decided in a 2.5-second spin.

Connect your device (computer, Raspberry Pi etc), plug in a USB button and connect to a giant screen!

Built for trick-or-treaters who mash buttons and don't read instructions —
so there aren't any. Tap the screen once to wake it up, then it just sits
there glowing in the dark until someone hits the button.

## How it works

1. **Start** — one tap unlocks audio and goes fullscreen. Only needed once all night.
2. **Idle** — a pumpkin pulses, candy and potato icons drift across the screen like bats, ghosts float by, and "PRESS THE BUTTON" begs to be pressed.
3. **Spin** — the reel spins slot-machine style with a synced tick sound.
4. **Reveal** — a kid finds out their fate, with sound, screen flash, and (for the good ones) confetti.
5. Back to idle, automatically, a few seconds later.

## What can happen

| Outcome | Odds | What happens |
|---|---|---|
| 🍬 Candy | 35% | The good outcome, plain and simple |
| 🥔 Potato | 35% | The bit. A single sad comedic *boing*. |
| 🍬🥔 Your Choice! | 10% | Candy **and** potato appear side by side — kid points at the one they want |
| 🍬🍬 Double Candy | 8% | Bigger fanfare, sparkly text, some confetti |
| 🥔🥔 Double Potato | 8% | Two boings, screen shake, bouncing potato confetti — the goofiest outcome |
| 🍬🎉🥔 BOTH!! | 4% | The jackpot. Full fanfare, timpani, 140 pieces of confetti raining down. |

All the odds are configurable — see below.

## Why it's a little extra

- **Every sound is generated in code.** No audio files — oscillators, filtered
  noise bursts, and a "boioioing" pitch-bend all built live with the Web Audio
  API. Even the flickering-lightbulb ambience.
- **The winner is picked before the reel even starts spinning**, then the
  animation eases toward it — so the tick sounds and the landing position are
  always perfectly in sync, no matter how long the reel spins.
- **Double Potato gets its own personality**: an extra-goofy squash-and-stretch
  wobble and a full screen shake, so it reads as funnier than its candy
  counterpart.
- Zero build step. It's one `index.html` file — no npm, no bundler, nothing to
  install. Open it in a browser and it runs.

## Running it

Just open `index.html` in a browser. For an actual kiosk setup:

- Point a browser at the file in fullscreen/kiosk mode.
- Wire up a USB arcade button configured as a keyboard HID device (any
  keypress works out of the box).
- Tap the start screen once to unlock audio and fullscreen, then walk away.

## Tuning it for your own night

Everything you'd want to change lives in one `CONFIG` object at the top of
the `<script>` tag in `index.html` — edit a value, save, hit refresh:

- `OUTCOMES` — add, remove, or reweight any outcome. Weights are relative,
  not percentages, so they don't need to add up to anything in particular.
- `SPIN_DURATION_MS` / `RESULT_HOLD_MS` — how long the reel spins, and how
  long the result stays on screen before it resets itself.
- `MASTER_VOLUME` — turn the whole night up or down.
- `ACCEPTED_KEYS` — restrict which key(s) trigger a spin, if "literally any
  key" is too permissive for your button.

No build step, nothing else to run. Happy haunting. 🎃
