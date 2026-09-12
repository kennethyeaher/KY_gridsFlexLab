# Homework 2: Grids and Flex

Responsive page built with plain HTML and CSS for INST630. It recreates the
`component-compex` post card from the course Figma file, repeats it three
times, and places the page regions with CSS Grid. The cards sit in a row on
wide screens and stack into a column under 48rem.

Live page: https://kennethyeaher.github.io/KY_gridsFlexLab/

## What it demonstrates

Grid handles the page. `.page-layout` on `body` defines four named areas
(header, hero, list, footer) on a three column grid. The outer columns are
flexible gutters and the middle column caps content at 72rem, so the footer
never runs wider than the content above it. The header spans all three
columns so its background reaches the edges.

Flexbox handles everything inside a region. The nav is a flex row with
`space-between`. Each card is a flex column, and inside it the image and
description form a row, the title and author form a row, the three
engagement metrics form a row, and the comments stack as a column. Every
nesting level in the CSS mirrors the layer tree in Figma.

The box model shows up in the cards: a 1px border, 1.5rem of padding, the
content boxes inside, and the gap between cards standing in for margin.
`box-sizing: border-box` is set on everything so padding and borders count
toward declared widths.

External resources are two Google Fonts (Space Grotesk and DM Sans) and
Font Awesome 6 for the icons in the header, cards, and footer.

## Project structure

```
KY_gridsFlexLab/
  README.md
  .gitignore
  index.html        page markup, three copies of the card
  css/
    style.css       tokens, page grid, flex components, breakpoint
```

There is no build step and no JavaScript.

## Run it locally

Clone the repo and open `index.html` in a browser. The fonts and icons load
from their CDNs, so an internet connection is needed for them to appear.
Without one the layout still works with the system font fallbacks.

To check the responsive behavior, resize the window below 768px (48rem) or
use the device toolbar in the browser dev tools.

## Publish with GitHub Pages

1. Push the repo to GitHub.
2. Open Settings, then Pages.
3. Set the source to the `main` branch, root folder, and save.
4. The page appears at `https://<username>.github.io/KY_gridsFlexLab/`
   after a minute or two.

## Component reference

Source: INST630 Figma Demos (2026, Kunesh), Components page,
`component-compex`. Layer tree recreated in the HTML:

```
component-compex
  main-content
    image
    description
      header
        title-date
        author
      text
  engagement-bar
    engagement-metric x3 (icon, label)
  comment-section
    comment x3
      header (author, time)
      text
```

## Known limitations

The image is a placeholder box with an icon rather than a real photo, since
the Figma component uses a placeholder too. Colors and fonts are my own
choices, not pulled from the Figma file. The breakpoint is a single jump at
48rem, so at tablet widths the three cards get narrow before they stack.
