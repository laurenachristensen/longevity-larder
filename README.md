The Longevity Larder

A single-file, self-curated functional-food apothecary. No server, no build step, no AI dependency — the entire site is index.html, and the entire database lives inside it.

How it works

The contents of the larder are stored in one place:

html<script type="application/json" id="larder-data"> … </script>

That JSON is the database. Everything else in the file just renders and edits it. The shape of each item:

json{
  "name": "Wild Salmon",
  "latin": "Salmo salar",
  "fill": "linear-gradient(180deg,#e08a6e,#b85c45)",
  "ev": "strong",                       // "strong" | "promising" | "emerging"
  "benefits": [
    { "h": "Heading", "p": "Hedged claim — never a cure.",
      "ref": { "s": "Source name", "u": "https://source-url" } }
  ],
  "note": "One honest caveat (optional)"
}

Items are grouped into shelves: { "title": "...", "tag": "...", "items": [ … ] }.

Two ways to edit


By hand (code): open index.html, edit the JSON in the larder-data block, save.
In the browser: open the page, click ℞ curate the larder in the footer (or add #curate to the URL). Add / edit / delete jars, then Publish · download page to get a fresh index.html with your changes baked in. Save data file exports a JSON backup; Load data file restores one.


Republishing (GitHub Pages)

The deployed file must be named index.html at the repository root. To update the live site:

bashgit add index.html
git commit -m "Add <food> to the larder"
git push

GitHub Pages rebuilds automatically in a minute or two. Editing index.html directly in GitHub's web editor and committing works the same way.

Notes


The in-browser editor's changes are in memory until you Publish or push — they don't autosave.
Search matches the start of a word (so "oliv" finds Olive Oil; "live" does not).
Nothing here is medical or dietary advice. Evidence tiers are a reading of the literature, not a verdict.
