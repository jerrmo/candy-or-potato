# 🎃 Candy or Potato?!

A haunted game for your front porch. One big button, one spooky
slot machine, and a kid's fate decided in a 2.5-second spin.

Connect a device (a laptop, a Raspberry Pi, whatever you've got), plug in a
USB button, and hook it up to a screen.

It's built for trick-or-treaters who mash buttons and don't read
instructions, so there aren't any. Tap the screen once to wake it up, then
it just sits there glowing in the dark until someone hits the button.

## How it works

1. **Start**: one tap unlocks audio and goes fullscreen. You only need to do this once all night.
2. **Idle**: a pumpkin pulses, candy and potato icons drift across the screen like bats, ghosts float by, and "PRESS THE BUTTON" begs to be pressed.
3. **Spin**: the reel spins slot-machine style with a synced tick sound.
4. **Reveal**: a kid finds out their fate, with sound, a screen flash, and (for the good ones) confetti.
5. It goes back to idle automatically, a few seconds later.

## What can happen

| Outcome | Odds | What happens |
|---|---|---|
| 🍬 Candy | 52% | The good outcome, plain and simple |
| 🥔 Potato | 16% | Also a good outcome, a cheerful comedic *boing*, not a letdown |
| 🍬🥔 Your Choice! | 12% | Candy and potato appear side by side, kid points at the one they want |
| 🍬🍬 Double Candy | 12% | Bigger fanfare, sparkly text, some confetti |
| 🥔🥔 Double Potato | 4% | Two boings, screen shake, bouncing potato confetti. The goofiest outcome. |
| 🍬🎉🥔 BOTH!! | 4% | The jackpot. Full fanfare, timpani, 140 pieces of confetti raining down. |

All the odds are configurable, see below.

## How many potatoes to buy

A potato shows up on 36% of spins, but it only costs you one when the kid
actually takes it. Averaged out that's about **a third of a potato per kid**,
so figure 110 for 300 kids or 170 for 500.

You don't have to guess exactly right, though. Set `POTATO_BUDGET` to however
many you actually bought and the game counts them down as it goes. Once
they're gone the potato outcomes quietly drop off the reel and the rest of
the night runs candy only. Nobody gets promised a potato you don't have.

| Potatoes bought | Typically lasts through |
|---|---|
| 100 | ~250 kids |
| 140 | ~350 kids |
| 150 | ~375 kids |
| 180 | ~450 kids |
| 200 | ~500 kids |

Buying short on purpose is a perfectly good plan. The reel just gets sweeter
as the night goes on.

## Why it's a little extra

Every sound is generated in code. There are no audio files, just oscillators,
filtered noise bursts, and a "boioioing" pitch-bend, all built live with the
Web Audio API. Even the flickering-lightbulb ambience.

The winner is picked before the reel even starts spinning, then the
animation eases toward it. That's why the tick sounds and the landing
position are always perfectly in sync, no matter how long the reel spins.

Double Potato gets its own personality: an extra-goofy squash-and-stretch
wobble and a full screen shake, so it reads as funnier than its candy
counterpart.

There's zero build step. It's one `index.html` file, no npm, no bundler,
nothing to install. Open it in a browser and it runs.

## Running it

Just open `index.html` in a browser. For an actual kiosk setup:

- Point a browser at the file in fullscreen/kiosk mode.
- Wire up a USB arcade button configured as a keyboard HID device (any
  keypress works out of the box).
- Tap the start screen once to unlock audio and fullscreen, then walk away.

## Tuning it for your own night

Everything you'd want to change lives in one `CONFIG` object at the top of
the `<script>` tag in `index.html`. Edit a value, save, hit refresh.

- `OUTCOMES`: add, remove, or reweight any outcome. Weights are relative,
  not percentages, so they don't need to add up to anything in particular.
  Each one also carries a `potatoes` cost that `POTATO_BUDGET` counts down.
- `POTATO_BUDGET`: how many potatoes you bought. Potato outcomes disappear
  once you run out. Set it to `null` if you'd rather never run dry.
  Reloading the page starts the count over.
- `SPIN_DURATION_MS` / `RESULT_HOLD_MS`: how long the reel spins, and how
  long the result stays on screen before it resets itself.
- `MASTER_VOLUME`: turn the whole night up or down.
- `ACCEPTED_KEYS`: restrict which key(s) trigger a spin, if "literally any
  key" is too permissive for your button.

No build step, nothing else to run. Happy haunting. 🎃
