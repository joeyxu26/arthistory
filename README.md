# The Salon Hang

An interactive, vintage-styled gallery-wall game built for **CS85, Introduction to Generative AI and Software Toolcraft (Fall 2026)**, in the spirit of Module 5 (Art History). You import real paintings from museum open-access collections, hang them on a wall, and arrange them by kinship. The wall shows how related each pair of works is, helps you form subgroups, drafts curatorial notes around one connecting theme, and exports a cropped image of your hang with or without those notes.

The project was built entirely through a sequence of natural-language prompts to Claude, and the history below records what each prompt asked for and how it shaped the result.

---

## What is in this folder

| File | What it is |
|---|---|
| `salon-hang-v2.html` | The current game. A single self-contained HTML file with no build step. |
| `README.md` | This note. |

Two earlier pieces from the same conversation are separate artifacts:

- **Art history web**, a growing, editable web of artists and the people around them (patrons, rulers, teachers, rivals, influences, legacy). It is stored in the artifact's shared database. <https://claude.ai/artifact/2PiswSFhrCEVg3Y4UMtSSn>
- **Salon Hang, first version**, an early prototype that used a built-in demo shelf with generated paintings. It is superseded by `salon-hang-v2.html`. <https://claude.ai/artifact/1Aqh6W8J6WRr1Uy21CH2WK>

---

## How to run it

1. Download `salon-hang-v2.html`.
2. Open it directly in a desktop browser (Chrome, Edge, Firefox, or Safari) **with an internet connection**.
3. Press the **+** button at the top right.

It must be opened as a local file or from your own site. Claude's published preview pages block requests to other websites, so they cannot load paintings from museums. If the museums cannot be reached, the page says so and shows nothing in place of real paintings.

Optional: to add Harvard Art Museums as a third source, use "Add Harvard" at the bottom left and paste a free API key from <https://harvardartmuseums.org/collections/api>. The key is kept only in your browser's local storage.

---

## Features

### Real paintings
- **Sources:** Art Institute of Chicago (public domain), Cleveland Museum of Art (CC0), and optionally Harvard Art Museums.
- **Import:** each press of **+** brings ten paintings with their real images, mixed across the sources.
- **Resolution:** Chicago images upgrade to a larger size when you zoom in. The other sources load at one size.
- **Palette:** read from the actual image pixels where the museum's server permits it.

### Museum labels
- **Floating label:** a transparent, legible line under each painting reads *Title*, Artist, Date, in a colour chosen to suit the wall.
- **Hover:** shows the full museum label, with artist details, date, medium, dimensions, credit line, repository and city, accession number, gallery, department, and palette swatches.
- **Double-click:** pins the label and adds a link to the work's page on the museum website.

### Hanging by kinship
Every pair of paintings gets a correlation score from seven features:

| Feature | Weight |
|---|---|
| Palette (hue, lightness, saturation) | 26% |
| Date | 20% |
| Style or movement | 14% |
| Artist | 12% |
| Subject (genre, inferred from title and description) | 12% |
| Medium | 8% |
| Culture or origin | 8% |

Scores are rescaled across the current wall so differences are visible.

- **Dragging a painting:** a web of threads shows its kinship with nearby works. Related works glow and unrelated works dim. **The other paintings never move.**
- **Resistance:** unrelated works resist the painting you are dragging, and related ones draw it in. It never overlaps another frame.
- **Open wall:** beyond a reach distance, no correlation is shown, so you can start a new subgroup in empty space.
- **Subgroups:** works that sit close together form a group, outlined with a faint dashed line.
- **Harmony meter:** scores how well related works share a group and unrelated works sit apart.
- **Idle paintings stay still.**
- **Discard:** drag a work to the velvet strip on the left to return it to the vault. Adding and discarding can be repeated as often as you like.

### Zoom, pan, and frames
- **Zoom and pan:** scroll wheel or trackpad pinch zooms from 20% to 500% around your cursor, and dragging empty wall pans. The plaque at the bottom right has − / + and **Fit all**.
- **Frames:** click a painting to cycle through eight frame styles (ornate gilt, slim gilt, wood moulding, ebonised, silvered, tinted cove, gallery float, painted gesso). Colours are derived from each painting's own palette, so warm works get gold and cool works get silver. Double-click steps back one style.
- **Keyboard:** arrow keys nudge a focused painting (hold Shift for larger steps), Enter swaps the frame, L pins the label, and Delete discards.

### Wall coverings
The folded-corner page icon offers nine coverings: Gallery White, Warm Stone, Museum Grey, Salon Green, Pompeian Red, Prussian Blue, Crimson Damask, Oatmeal Linen, and Black Box. The choice is remembered, and the labels and screenshots adapt to it.

### Curatorial notes (pen icon)
- **Survey:** notes first survey each group, covering dates, main subjects and movements, and the museum's own descriptions.
- **One theme:** they then find one theme that connects most of the paintings and gives a perspective on them. The local drafts match museum text and subjects against ten themes (water, light, women and the gaze, faith, everyday labour, the city, nature as mood, portraiture, myth, objects and time).
- **Each note:** says how that painting enters the theme, or honestly stands outside it, and compares it with its nearest neighbour in the same group.
- **Draft with Claude:** available when the page runs inside the Claude app, and gives richer results. It follows the same steps with fuller evidence.
- **Editing:** title, theme, introduction, and every note are editable.

### Share (arrow-tray icon)
- **Selection window:** drag and resize it over the wall, and scroll to zoom beneath it.
- **Options:** include or leave out the curatorial notes, and re-select the area at any time.
- **Output:** a PNG you can download, share through your device's share sheet, or post on X with a caption.
- **Notes version:** lists only the paintings inside the window, with numbered badges.

---

## How it was built: the prompts

| # | Prompt, in short | What it produced |
|---|---|---|
| 1 | A visual analysis of Caravaggio countering popular arguments, with at least 10 real visual evidences | An interactive analysis of six popular claims and 15 pieces of evidence, tagged as visible, technical study, or interpretation |
| 2 | A growing web of art history: artists, a web of connected people, portrait to six top works with a "+" for more, editable | The shared, editable Art history web, seeded with 10 artists |
| 3 | A vintage drag-and-hang game: "+" imports 10 random framed paintings from Harvard; correlation affects dragging; discard on the left; pen for notes; share | The first Salon Hang, with a demo shelf because live museum calls are blocked in previews |
| 4 | Always real paintings; scroll zoom; "title, artist, year" label plus full museum label on hover; a fourth wallpaper icon | Live Chicago and Cleveland imports, zoom and pan, hover labels, nine wall coverings |
| 5 | Idle paintings must not float; notes should interpret rather than list facts; more frame varieties that swap on click and fit the artwork; labels legible but transparent | Still idle paintings, eight palette-matched frames, interpretive notes, plain legible labels |
| 6 | More chic buttons; a crop window for sharing with or without notes; substantive notes | The glass dock, the selection window, and notes grounded in museum text |
| 7 | Dragging shows the web but moves nothing; open space shows no correlation so subgroups can form; notes survey each group and find one common theme | Reach-limited correlation, subgroup outlines, theme-led notes |
| 8 | This README | This file |

A pattern across the prompts: each one tightened the project's rules. The early version produced something that worked. The later prompts replaced its shortcuts with real data, real interaction logic, and more careful writing.

---

## Technical notes

- A single HTML file with plain JavaScript. No framework and no build step.
- Fonts (IM Fell English, Special Elite) load from Google Fonts, with fallbacks.
- The wall is a transformed "world" layer, so zoom and pan apply to the paintings, threads, and wallpaper together.
- Screenshots are composed on a canvas rather than captured from the screen, which is how the selection window and notes panel can be added.
- Your Harvard key and wallpaper choice are stored in the browser's local storage.

---

## Known limitations

- **Not browser-tested:** the code was syntax-checked but not run against the live museum servers during development. The first real import is the real test.
- **Screenshot images:** some museum servers do not allow their images into exported canvases. Those paintings appear as colour plates in the shared image, and the page tells you when this happens.
- **Genre and theme are inferred:** museum records have no genre field, so genre and theme come from keywords in the title, description, and subject terms. They can be wrong.
- **Local notes are only as good as the museum text:** many records have thin descriptions. Use "Draft with Claude" for the best notes.
- **Palette fallback:** when an image cannot be read for palette, a neutral palette or the museum's single dominant colour is used.
- **Desktop-first:** the layout is not yet adapted for phone-width screens.

---

## Credits and licensing

- Paintings and metadata come from the Art Institute of Chicago, the Cleveland Museum of Art, and (optionally) Harvard Art Museums. Each painting's credit line and repository are shown on its label and in the shared notes. Check each museum's terms before reusing images beyond personal use or sharing.
- Built with Claude for CS85 (Harvard, Fall 2026).
