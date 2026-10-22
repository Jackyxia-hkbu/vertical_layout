# Vertical Layout

A small personal web page for keeping lists of file names in stacked rows.
It is a single HTML file with no build step or server. The only dependency is
[html-to-image](https://github.com/bubkoo/html-to-image) 1.11.11, loaded from
jsDelivr for the PNG export, so that feature needs an internet connection.

## Features

- **Page title:** a large title at the top of the page. Click it to rename;
  it defaults to "Vertical Layout" and is also used as the browser tab name.
- **Stacked rows:** rows run top to bottom and split the screen height evenly.
  Each row is at least 140px tall, and the page scrolls once there are more
  rows than fit.
- **Named rows:** click a row's title to rename it. Unnamed rows show a
  placeholder ("Row 1", "Row 2", …). A new row puts the cursor in its title
  straight away.
- **File names:** "+ Add file" opens a text box in that row. Type a name and
  press Enter (or click Add). The box stays open for the next name; Esc or
  Cancel closes it. Each name has a × to remove it. Only the names are kept;
  there are no real files.
- **Add / delete rows:** "+ Add row" at the bottom adds a row. "Delete row"
  removes one, asking first if it still has file names.
- **Save as PNG:** the button next to the title downloads all rows as an
  image (2× resolution, named after the page title). The image contains only
  row names and file names: the page title, buttons, open text boxes and
  "No files yet" are left out.
- **Saved automatically:** everything is stored in the browser's
  `localStorage` and comes back after a refresh.
- **Journal style:** white and blue only, with navy rules framing the title
  and the bottom of the page, light blue tint on alternate rows, serif row titles, and a centered
  column about 960px wide on large screens. It stays light even when the
  system is in dark mode.

## Usage

The page is published with GitHub Pages at
<https://jackyxia-hkbu.github.io/vertical_layout/>.

To run it locally instead, open the file in a browser:

```sh
xdg-open index.html
```

### Publishing to GitHub Pages

The page is served straight from the repository, with no build step. In the
repository's **Settings → Pages**, set **Source** to "Deploy from a branch",
pick `main` and `/ (root)`, and save. GitHub serves `index.html` at the URL
above, and every push to `main` updates the site within a minute or two.

## Data storage

The page title is stored under the `localStorage` key `vertical-layout-title`
as plain text. Rows live under `vertical-layout-rows` as JSON:

```json
[
  { "name": "Drafts", "files": ["intro.md", "notes.txt"] },
  { "name": "", "files": [] }
]
```

Things to know:

- The data is per browser and per address. A different browser or
  computer starts empty, and the GitHub Pages site and a local copy of
  `index.html` keep separate data.
- Clearing browser site data erases it. There is no export or backup yet.

## Customizing

Colors are CSS variables at the top of the `<style>` block in `index.html`:

| Variable | Use | Value |
|---|---|---|
| `--bg` | Page background | `#ffffff` |
| `--ink` | Text | `#12386b` |
| `--navy` | Titles, buttons, top/bottom rules | `#0b3d78` |
| `--rule` | Lines between rows and around file names | `#c9d8ec` |
| `--row1` | Odd rows | `#ffffff` |
| `--row2` | Even rows | `#eef4fc` |

## Files

```
index.html   the whole app (HTML, CSS, JavaScript)
README.md    this file
```
