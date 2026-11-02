# Rubik's Cube Simulator

A Python simulator for the 3×3 Rubik's cube. It models every move as a permutation, runs algorithms written in standard cube notation, and visualises the results.

I'm building it to learn Python and to explore the maths behind the cube: group theory, algorithm structure, and the statistics of scrambling.

> **Status:** In progress. Started November 2026.

---

## Features

Planned features, ticked off as they're built:

- [ ] Cube state model (54 stickers)
- [ ] All face turns (`R L U D F B`), slice moves (`M E S`) and cube rotations (`x y z`)
- [ ] Notation parser: type `R U R' U'` and run it
- [ ] Algorithm tools: inverse, order (how many repeats until solved), commutators and conjugates
- [ ] Pattern library: checkerboard, superflip, cube-in-cube, and more
- [ ] 2D net visualisation
- [ ] Interactive 3D interface
- [ ] **Statistics study:** how many random moves does it take before a scramble is truly random?
- [ ] Stretch goal: optimal solver for the 2×2 cube

---

## How it works

The cube is stored as an array of 54 sticker colours, 9 for each of the 6 faces.

Every move is a **permutation**: a list saying which position each sticker moves to. Applying a move is just reindexing the array:

```python
new_state = state[move]
```

That one idea makes the rest simple:

| Operation | How |
|---|---|
| Apply a move | `state[move]` |
| Combine two moves | apply them one after another |
| Undo a move | its inverse permutation (`np.argsort(move)`) |
| Order of an algorithm | apply it repeatedly until the cube is solved again |

For example, the algorithm `R U R' U'` returns the cube to solved after exactly **6** repetitions.

---

## Cube notation

| Symbol | Meaning |
|---|---|
| `R` `L` `U` `D` `F` `B` | Turn the Right, Left, Up, Down, Front or Back face 90° clockwise (as if you're looking straight at that face) |
| `R'` | Prime: turn anticlockwise |
| `R2` | Turn 180° |
| `M` `E` `S` | Middle slice moves |
| `x` `y` `z` | Rotate the whole cube |

---

## Project structure (planned)

```
rubiks-cube-sim/
├── cube/          # core engine: state, moves, notation parser
├── viz/           # 2D net and 3D interface
├── analysis/      # statistics experiments and plots
├── tests/         # automated tests
└── README.md
```

---

## Getting started

Requires Python 3.12 or newer.

```bash
git clone https://github.com/nishaad-j/rubiks-cube-sim.git
cd rubiks-cube-sim
```

Install and usage instructions will be added as the project develops.

---

## Roadmap

| Period | Milestone |
|---|---|
| November 2026 | Python fundamentals; single-face rotation |
| Late Nov – Dec | Full cube engine, notation parser, tests |
| December | 2D visualisation, algorithm explorer, pattern library |
| January 2027 | Interactive 3D interface |
| February 2027 | Statistics study, documentation, polish |

---

## Acknowledgements

Parts of this project, mainly the 3D interface, were developed with help from Claude (Anthropic). The cube engine, tests and analysis are my own work, with AI-assisted code review.

## License

MIT
