Copy it straight to your clipboard:

const text = Array.from(document.querySelectorAll('.transcript-row'))
  .map(row => row.querySelector('.transcript-text').textContent.replace(/\s+/g, ' ').trim())
  .join(' ');

copy(text); // Chrome/Firefox DevTools shortcut, puts it on your clipboard

keep the timestamps too
const text = Array.from(document.querySelectorAll('.transcript-row'))
  .map(row => `[${row.querySelector('.transcript-time').textContent}] ${row.querySelector('.transcript-text').textContent.replace(/\s+/g, ' ')
  .trim()}`)
