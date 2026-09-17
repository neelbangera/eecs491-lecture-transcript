# Transcript Extractor

A small browser console snippet for pulling the full text out of a `.transcript-scroller` page (the kind with one `<div class="transcript-row">` per line, each containing a `.transcript-time` and `.transcript-text` element) and copying it to your clipboard as a single block.

Two versions are included:

- **Plain text** — just the spoken words, joined into one continuous block.
- **With timestamps** — each line prefixed with its `[mm:ss]` marker.

## Usage

1. Open the page containing the transcript.
2. Open DevTools (`F12` or `Cmd+Option+I` / `Ctrl+Shift+I`) and go to the **Console** tab.
3. Paste in one of the scripts below and press Enter.
4. The result is copied straight to your clipboard — paste it wherever you need it.

> **Note:** `copy()` is a Chrome/Firefox DevTools console helper. It only works when run directly in the console, not from a `<script>` tag on the page itself. If the transcript lives inside an `<iframe>`, use the context dropdown at the top of the Console panel to switch into the iframe's scope before running the script.

### Plain text (no timestamps)

```js
const text = Array.from(document.querySelectorAll('.transcript-row'))
  .map(row => row.querySelector('.transcript-text').textContent.replace(/\s+/g, ' ').trim())
  .join(' ');

copy(text);
```

### With timestamps

```js
const text = Array.from(document.querySelectorAll('.transcript-row'))
  .map(row => {
    const time = row.querySelector('.transcript-time').textContent.trim();
    const words = row.querySelector('.transcript-text').textContent.replace(/\s+/g, ' ').trim();
    return `[${time}] ${words}`;
  })
  .join('\n');

copy(text);
```
