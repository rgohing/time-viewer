# DMS Clock Time Viewer

This folder contains a small browser-based time viewer. It keeps the original two-column `Time Viewer.html` output, but the clock rows are driven by one configuration file: `time-viewer.config.json`.

The table shows each configured row with its label, current time, and current date.

The page uses a modern card-style layout with a light/dark theme toggle. The selected theme is saved in the browser, and the table uses alternating row background colors for easier scanning.

## Files

- `Time Viewer.html` - the clock page.
- `time-viewer.config.json` - the list of clocks and display settings.
- `README.md` - this documentation.

## How to Add or Remove a Clock

Edit the `clocks` array in `time-viewer.config.json`.

The file is loaded directly by the browser when `Time Viewer.html` is opened from disk, so it starts with `window.TIME_VIEWER_CONFIG =` and ends with `;`.

Example:

```json
{
  "label": "Singapore",
  "UTC": "+8"
}
```

To remove a clock, delete its object from the `clocks` array. The HTML page reads the configuration and dynamically creates one row per clock.

Use UTC offset values such as `+1`, `+8`, `-4`, or `+5:30`. For Central European Time with automatic daylight saving behavior, use `CET/CEST`.

## CET and CEST Behavior

The Germany row uses `CET/CEST` in the configuration. Internally, the page maps that value to `Europe/Copenhagen`, which is Central European Time in the browser's IANA time-zone data. The browser automatically switches that clock between CET and CEST depending on the season.

The page also shows the current year's exact CET/CEST change dates above the table:

- CEST start date and transition time.
- CET resume date and transition time.
- The next CET/CEST change.

## Running the Page

Double-click `Time Viewer.html` or open it directly in a browser.

The page automatically loads `time-viewer.config.json` from the same folder and dynamically creates the clock rows.