# Your life in weeks

A single-file, dark-themed website that shows a life as a grid of weeks. Each square is one week, each row is one year (52 squares), and the number of rows is the length of the life you choose to show.

## Features

- **Grid:** set a birth date and the number of years (1 to 120, default 90). Past weeks are bright, future weeks are dimmed, and the current week is highlighted.
- **Phases:** color-code stretches of life by dates or by ages. Later phases override earlier ones.
- **Events:** pick a date, a color and how many weeks to mark (1 to 520). Events show as circles and override phase colors. Titles can be shown on the grid or hidden with a checkbox.
- **Hover or tap a square:** shows its week number from birth, age, start date, phase and event.
- **Share as an image:** downloads a tall PNG infographic (1080 px wide) for social media or WhatsApp. A native Share button appears on browsers that support it.
- **Save and load:** export everything to a `.txt` file and import it later.

## Run it

Open `index.html` in a browser. There is no build step and no server. Your data stays in your browser (localStorage) and is never uploaded.

Google Fonts (Fraunces) loads if online and falls back to Georgia if not.

## Data file format

The exported `.txt` file is JSON:

```json
{
  "version": 1,
  "showTitles": true,
  "birthDate": "1990-05-14",
  "years": 90,
  "phases": [
    { "name": "School", "color": "#6ea8ff", "mode": "ages", "start": "5", "end": "18" },
    { "name": "First job", "color": "#6fcf9f", "mode": "dates", "start": "2012-09-01", "end": "2015-08-31" }
  ],
  "events": [
    { "name": "Graduation", "color": "#f0b45a", "date": "2008-06-20", "weeks": 1 }
  ]
}
```

- `mode: "dates"` uses `YYYY-MM-DD`, with the end date included.
- `mode: "ages"` runs from the start age's birthday up to the end age's birthday.
- Colors are `#rrggbb`. A missing `end` means the phase continues to the end of the grid.

## How weeks are counted

Rows restart on each birthday, so row 0 is age 0. Each row has 52 squares, and the last square in a row covers 8 or 9 days so the next row begins on the birthday.

## Publish it

It is a static site, so any static host works:

- **GitHub Pages:** put `index.html` in a repo and enable Pages.
- **Netlify Drop:** drag the file onto the page for an instant link.
- **Cloudflare Pages:** upload the file or connect a repo.
- **Vercel:** import a repo with `index.html` at the root.

For a custom domain, buy one from a registrar and point it at your host.
