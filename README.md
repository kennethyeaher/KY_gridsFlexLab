# Design Notes

INST630 Homework 2: Grids and Flex.

A static feed of three short notes about this page's layout, built with
plain HTML and CSS. The cards adapt the documented `component-compex`
structure from the course Figma file. They share a row on screens wider
than 64rem and stack into a column at 64rem and narrower.

The notes cover the shared page frame, the groups inside each card, and
the use of spacing. Comments are example discussion prompts from named
demo readers. Likes and saves are illustrative counts. None of these
counts represent measured use of the project.

Live page: https://kennethyeaher.github.io/KY_gridsFlexLab/

## What it demonstrates

Grid handles the page. `.page-layout` on `body` defines three named areas
(header, content, footer) on a three column grid. The outer columns are
flexible gutters and the middle column caps content at 72rem. The header
spans all three columns so its background reaches the edges. A nested grid
on `.page-content` places the hero, list, and About section inside one main
landmark. The footer shares the main content width.

Flexbox handles everything inside a region. The nav is a flex row with
`space-between`. Each card is a flex column, and inside it the image and
description form a row, the title and author form a row, the three
engagement metrics form a row, and the comments stack as a column. The card
groups retain the documented Figma layer tree. Rows can wrap when their
contents need more room, including long names or enlarged text.

The box model shows up in the cards: a 1px border, 1.5rem of desktop padding
(1rem in the stacked layout), and the content boxes inside. The heading uses
`margin-bottom` to separate it from the introduction, and `margin: 0 auto`
centers the header navigation. Flex `gap` separately controls space between
cards and between their inner groups; it is not part of a card's margin.
`box-sizing: border-box` makes declared widths include padding and borders.

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

There is no build step and no JavaScript. Feed and About link to sections
on the page. View source opens this repository; the About section also
links to the course Figma reference. Each card contains three comments,
and its comment count matches those visible examples.

## Run it locally

Clone the repo and open `index.html` in a browser. The fonts and icons load
from their CDNs, so an internet connection is needed for them to appear.
Without one the layout still works with the system font fallbacks.

## Responsive and keyboard checks

Use the browser's responsive tools at 320px, 390px, 768px, 1024px, 1025px,
and 1440px. With the default 16px browser font size, 64rem equals 1024px:
three cards should share one row above that width, and stack at or below it.
Check for overlap, clipped text, and unwanted horizontal scrolling. Also
check browser zoom at 200% and 400%.

Press Tab from the top of the page. The first link should become visible
as "Skip to main content"; Enter should move focus to the main landmark.
Continue with Tab and Shift+Tab to check the visible focus outlines on
header and footer links. Follow Feed and About to their labeled sections,
and check the repository and Figma links.

Secondary text uses a darker shared color, and navigation links have a
minimum height of 2.75rem. These changes support readability and keyboard
use; they do not establish a complete accessibility audit. The checks above
are a manual verification procedure, not a record of completed browser tests.

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
choices, not pulled from the Figma file. This is a static demonstration;
comments, likes, and saves have no interactive controls or persistence.
Reference fidelity and browser behavior need verification before submitting
a revised live version.
