# ✂️ Rope Rescue — Cut the Rope, Save the Tiles

A physics puzzle inspired by a mobile game ad: *only the left-brained can cut the rope correctly.*

**▶ Play it live: https://january-msemakweli.github.io/rope-rescue-game/**

## How to play

- Tile mascots (and gorillas) hang from a tree branch on ropes. Some are also tied to each other.
- **Swipe across a rope to cut it** (a tap on a rope works too).
- A tile that drops a short way lands safely on the grass. A tile that falls too far gets **knocked out** — level lost.
- If a **gorilla reaches the ground**, it's free — level lost. Keep them hanging.
- Save every tile to win. Your **IQ score** starts at each level's base, rises +13 per tile saved, and drops when you fail — just like the ad.
- Order matters: cutting one rope can dangle a tile from a friend and lower it for a safe final drop. Chains collapse gently if you cut at the top.

## Features

- 5 hand-designed levels: direct drops, tiles tied to a gorilla, a 3-tile chain, gorilla-dangle rescues, and a combined finale
- Real rope physics: a small Verlet-integration engine (gravity, rope constraints that only pull, character collisions, impact-speed detection) written from scratch in vanilla JS
- Every level **playtested by simulation**: scripted runs of the intended solutions win, wrong cuts (e.g. cutting a gorilla's rope) fail, and untouched levels hang perfectly still
- Swipe + tap cutting with a visible slash trail, worried/happy tile faces, IQ counter, hints, level select with progress in `localStorage`
- Single self-contained `index.html` — no build step, no dependencies, works on mobile and desktop

## Run locally

```sh
python3 -m http.server 8000
# open http://localhost:8000
```

## Make your own levels

Levels are plain data at the top of the script in `index.html`:

```js
{ name: "Level 6 · Yours", iq: 85, hint: "...",
  chars: [ [x, y, 'tile'], [x, y, 'gorilla'] ],
  ropes: [ [['a', anchorX, 170], ['c', charIndex]], [['c', 0], ['c', 1]] ] }
```

Rope lengths are computed from the starting geometry (taut at start). A tile's safe fall is
about 320 px in the game's physics — hang tiles you want dropped directly at y ≥ ~670,
and use chains/connectors to lower the higher ones.

## License

Original code in this repo is free to reuse (MIT). The concept was inspired by a third-party
game advertisement; no assets from that ad are used.
