# Colour-Reveal Word Search V4

A colourful browser-based word search game where players find hidden words, unlock paintable letter-squares, and gradually reveal a hidden pixel-art picture. V4 improves the larger board modes with better letter visibility, zoom controls, big-letter mode, and a clean final-picture viewer with no letters or grid lines.

## Overview

Colour-Reveal Word Search V4 combines three activities in one single-file HTML game:

1. **Find hidden words** in a word-search grid.
2. **Paint the revealed letter-squares** using theme-based colours.
3. **Reveal a hidden picture** as more of the grid is completed.

The game is designed to be playful, visual, and easy to run. It does not need a server, build tool, package manager, database, or external assets.

## Features

### Core gameplay

* Interactive word-search grid.
* Drag-to-select word finding.
* Separate **Find** and **Paint** modes.
* Emoji-based mode buttons for clearer controls.
* Glowing paintable squares after a word is found.
* Manual painting by tapping or dragging across unlocked squares.
* Optional **Auto-paint** mode.
* Hidden pixel-art image revealed through gameplay.
* Completion modal with a **Well done!** message.

### V4 improvements

* Improved large-board readability.
* Better dynamic cell sizing for bigger grid modes.
* **Zoom slider** for board scaling.
* **Big letters** toggle for easier reading.
* **Picture mode** toggle that shows the board as clean pixel art.
* **Clean picture viewer** with no letters, borders, or grid lines.
* More user-friendly top controls.
* Cleaner mode dock with large Find/Paint buttons.
* Improved UI layout and visual polish.

### Game modes and helpers

* Hint button that highlights the first and last letter of a remaining word.
* Focus clues when tapping a word chip.
* Colour Burst power-up charged by finding words.
* Paint All Found button for quickly colouring unlocked squares.
* Streak, mistakes, hints-used, and rank tracking.
* Timer.
* Progress meters for words found and painted squares.

### Themes

The game includes multiple themed puzzle sets, each with its own:

* Word list.
* Colour palette.
* Hidden picture generator.
* Stickers.
* Background accent colours.

Included themes:

* Space Rocket
* Ocean Fish
* Garden Flower
* Dino Valley
* Candy Land
* Robot Lab
* Jungle Tiger
* Pirate Treasure
* Unicorn Rainbow
* Weather Wizard

### Grid sizes

Available board sizes:

| Difficulty | Grid Size | Description                           |
| ---------- | --------: | ------------------------------------- |
| Mini       |       7×7 | Very quick puzzle                     |
| Easy       |       8×8 | Small, gentle puzzle                  |
| Medium     |     10×10 | Balanced default mode                 |
| Hard       |     12×12 | Larger grid with more word directions |
| Expert     |     14×14 | Big picture grid                      |
| Poster     |     16×16 | Largest reveal image                  |

## How to play

1. Open the HTML file in a browser.
2. Choose a theme and size, or use the surprise option.
3. Press **New puzzle**.
4. Use **Find mode** to drag across hidden words.
5. When a word is found, its squares become paintable.
6. Switch to **Paint mode** and colour the glowing squares.
7. Keep finding and painting until every word is found.
8. Use **Clean picture** to view the final art without letters or grid lines.

## Controls

| Control             | What it does                                         |
| ------------------- | ---------------------------------------------------- |
| 🔎 Find             | Lets you drag across letters to find words           |
| 🎨 Paint            | Lets you colour unlocked glowing squares             |
| 🎲 New puzzle       | Generates a new puzzle                               |
| 💡 Hint             | Highlights the start and end of a remaining word     |
| 🌈 Colour burst     | Paints all currently unlocked squares when charged   |
| 🪄 Paint all found  | Paints all currently unlocked squares immediately    |
| 📋 Copy colour key  | Copies the full row/column colour instructions       |
| 🔗 Copy puzzle code | Copies the theme, difficulty, and seed               |
| 🖼️ Clean picture   | Opens the hidden image without letters or grid lines |
| 🖼️ Picture mode    | Turns the live board into clean pixel art            |
| 🔠 Big letters      | Enlarges the letters for readability                 |
| Zoom slider         | Scales the board up or down                          |
| 🖨️ Print           | Opens the browser print dialog                       |
| Reset               | Restarts the current puzzle layout                   |

## Installation

No installation is required.

Save the game as an HTML file, for example:

```text
colour-reveal-word-search-v4.html
```

Then open it in any modern browser:

* Chrome
* Edge
* Firefox
* Safari

## Running locally

You can run the file directly by double-clicking it.

For local development, you can also use a simple local server:

```bash
python -m http.server 8000
```

Then open:

```text
http://localhost:8000
```

## File structure

This is a single-file project:

```text
colour-reveal-word-search-v4.html
```

The file contains:

* HTML layout.
* CSS styling and responsive design.
* JavaScript puzzle generation.
* Theme data.
* Pixel-art generators.
* Save/load state logic.
* Sound, animation, and modal UI.

## Browser storage

The game uses `localStorage` to save progress in the browser.

Saved progress includes:

* Current theme.
* Difficulty.
* Puzzle seed.
* Found words.
* Painted cells.
* Brush meter.
* Completion state.
* Streak, mistakes, hints, and timer data.

To clear saved progress, use the in-game **Reset** or **New puzzle** buttons, or clear the browser site data.

## Customisation

### Add a new theme

Themes are stored in the `THEMES` object.

A theme needs:

* `name`
* `icon`
* `accents`
* `stickers`
* `letters`
* `words`
* `palette`
* `art` function

Example shape:

```js
myTheme: {
  name: "My Theme",
  icon: "⭐",
  accents: ["#7c5cff", "#18c7a7", "#0d1020", "#171d34"],
  stickers: ["⭐", "✨", "🎉"],
  letters: "MYTHEMELETTERS",
  words: ["WORD", "SEARCH", "PAINT"],
  palette: {
    B: { name: "Background", hex: "#101827", text: "#ffffff" },
    Y: { name: "Yellow", hex: "#fde047", text: "#111827" }
  },
  art: artMyTheme
}
```

### Add a new difficulty

Difficulties are stored in the `DIFFICULTIES` object.

Each difficulty controls:

* Grid size.
* Number of words.
* Allowed word directions.
* Description.

Example:

```js
large: {
  label: "Large 18×18",
  size: 18,
  wordCount: 28,
  dirs: [[0,1],[0,-1],[1,0],[-1,0],[1,1],[-1,-1],[1,-1],[-1,1]],
  description: "Extra-large puzzle."
}
```

### Add a new pixel-art generator

Pixel art is generated as a square matrix of palette keys.

Example:

```js
function artMyTheme(n) {
  const m = matrix(n, "B");
  ellipse(m, Math.floor(n / 2), Math.floor(n / 2), n * 0.25, n * 0.25, "Y");
  return m;
}
```

## Accessibility notes

* Buttons use readable labels and emoji icons.
* The board uses ARIA grid roles.
* Cells include row, column, letter, and colour labels.
* Big-letter mode helps on larger grids.
* Zoom helps with readability on smaller screens.
* Picture mode provides a cleaner visual view for the final art.

## Design goals

The game is built around these goals:

* Easy to play.
* Visually rewarding.
* No setup required.
* Works as a single HTML file.
* Good for quick puzzles or longer poster-sized challenges.
* Combines word searching, colouring, and reveal-art mechanics.

## Known notes

* The game is fully client-side, so progress is stored only in the current browser.
* Puzzle codes can be copied, but the current version does not include a paste/import puzzle-code interface.
* Sound is optional and disabled by default.
* Very large grids may still benefit from using zoom and big-letter mode depending on screen size.

## Future ideas

Possible future improvements:

* Puzzle-code import box.
* Daily challenge mode.
* Achievement badges.
* Export final picture as PNG.
* Custom word-list editor.
* Custom palette editor.
* More pixel-art themes.
* Better mobile gesture support.
* Difficulty stars and score grades.
* Classroom/printable worksheet mode.

## Credits

Created as a single-file HTML, CSS, and JavaScript game project.

No external libraries or assets are required.

## License

You can use, modify, and share this project for personal, educational, or experimental purposes. Add your preferred license before publishing publicly.
