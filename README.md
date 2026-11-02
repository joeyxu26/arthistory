# The Hang

An interactive, vintage-styled gallery-wall game built for CS85 (Fall 2026), in the spirit of Module 5 (Art History). You import real paintings from museum open-access collections, hang them on a wall, and arrange them per curatorial scrutiny. The game shows how related each pair of works is, helps you form subgroups, drafts curatorial notes around one connecting theme, and eventually shares a full image of your hang.

The project was built through a sequenced natural-language prompts to Claude, and below explains the functionality of the program.
---

In this folder

| File | What it is |
|---|---|
| `index.html` | The current game. A single self-contained HTML file with no build step. |
| `README.md` | This note. |

Import: the + button brings ten real paintings from museum collections.
Labels: a plain label under each painting, a full museum label on hover, and a pinned label with a link to the museum page.
Hang by kinship: the correlation web, open-wall subgroups, and the Harmony meter.
Discard: the velvet strip on the left edge.
Zoom and pan: scroll to zoom, drag to pan, and “Fit all”.
Frames: eight styles that swap on click.
Wallpaper: nine museum wall coverings.
Curatorial notes: the group survey and one connecting theme.
Share: a selection window, with or without notes.
Keyboard: the shortcut keys.

The project is designed to make use of open archive of digital art collection; it allows an efficient build-up of hang solutions, and a quick visualization of curated spaces. 
