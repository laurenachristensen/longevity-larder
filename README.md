# The Longevity Larder

A self-curated functional-food apothecary. The public site is **read-only**; the contents live in a separate data file that only the owner edits and republishes. Have fun.

## Files

| File | Goes in the repo? | Purpose |
|------|-------------------|---------|
| `index.html` | **Yes** | The public site. Read-only. Loads its contents from `larder.json`. Contains no editing tools. |
| `larder.json` | **Yes** | The database — every jar. This is the only file you edit to change the site. |
| `larder-editor.html` | **No — keep local** | Your private visual editor. Open it on your machine to add/edit jars, then save an updated `larder.json`. |

Only commits to this repository change the live site. Visitors to the public page cannot edit anything — there are no editing tools in `index.html` at all.

## The data shape

`larder.json` is an array of shelves; each shelf holds items:

```json
[
  {
    "title": "The Cold Store",
    "tag": "fridge",
    "items": [
      {
        "name": "Wild Salmon",
        "latin": "Salmo salar",
        "fill": "linear-gradient(180deg,#e08a6e,#b85c45)",
        "ev": "strong",
        "benefits": [
          { "h": "Heading", "p": "Hedged claim — never a cure.",
            "ref": { "s": "Source name", "u": "https://source-url" } }
        ],
        "note": "One honest caveat (optional)"
      }
    ]
  }
]
```

`ev` is one of `"strong"`, `"promising"`, `"emerging"`.

## Editing — two ways

**By hand:** open `larder.json` in your code editor, edit, save.

**Visually:** open `larder-editor.html` on your machine. It opens straight into curate mode. Add / edit / delete jars (colours, evidence tier, benefits, sources, caveat), then click **Save larder.json** to download the updated file. If you opened it from the live URL it pre-loads the current data; if you opened it from disk, click **Load larder.json** first to pull in your file.

## Republishing

Replace `larder.json` in the repo with your updated version and push:

```bash
git add larder.json
git commit -m "Add <food> to the larder"
git push
```

GitHub Pages rebuilds in a minute or two and the live site shows the new contents. (You can also drag the updated `larder.json` into the repo via GitHub's web UI and commit there.)

## Notes

- The public page reads `larder.json` over the web, so open `index.html` via the published URL (or a local server) — double-clicking it from disk won't load the data.
- Search matches the **start of a word**: "oliv" finds Olive Oil; "live" does not.
- Nothing here is medical or dietary advice. Evidence tiers are a reading of the literature, not a verdict.
