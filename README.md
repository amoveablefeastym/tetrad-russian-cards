# Тетрадь

Russian flashcards on squared school-notebook paper. *Тетрадь* means "exercise book".

Everything lives in one file, `index.html`, with no build step and no dependencies to install.

## Features

- Cards grouped into nouns, verbs, adjectives, adverbs, phrases and sentences
- Two study modes: see the English and recall the Russian, or see the Russian and type the English
- Gender on nouns, and the stressed vowel marked in red
- Mark each card **Know** or **Don't know**, then review your Unknown or Known cards later
- Add cards by hand, typing `'` after a vowel to mark stress (`вода'` becomes `вода́`)
- Add cards from photos of vocabulary (Claude Artifacts only, see below)
- Light and dark themes, and a layout that works at phone width

## Run it

Open `index.html` in a browser, or serve the folder with any static host such as GitHub Pages.

Run this way, cards are saved in that browser's `localStorage`, so they stay on that device. The deck starts empty.

## Where it runs

The page was built as a [Claude Artifact](https://claude.ai) and uses the runtime that Artifacts provide when it is available. Outside Claude it falls back without any setup.

| Feature | Claude Artifact | Standalone |
| --- | --- | --- |
| Flashcards and known/unknown sorting | Yes | Yes |
| Saving | Claude account, syncs across devices | This browser only |
| Reading photos | Yes, on the viewer's Claude usage | Not available, the button is hidden |

To run it as an Artifact, publish the page with these capabilities:

```json
{
  "sample": { "images": true },
  "db": { "rules": [{ "path": "cards", "read": "view", "write": "admin" }] },
  "user": {}
}
```

## Card format

```json
{
  "ru": "вода́",
  "en": "water",
  "pos": "noun",
  "gender": "f",
  "note": "",
  "status": "known",
  "createdAt": 1793374511000
}
```

- `ru` marks stress with the combining acute accent U+0301 after the vowel.
- `pos` is one of `noun`, `verb`, `adj`, `adv`, `phrase` or `sentence`.
- `gender` is `m`, `f`, `n` or `pl` on nouns, and empty otherwise.
- `status` is `known` or `unknown`. A card without it counts as new.

## Contributing

Issues and pull requests are welcome. Keep it a single file with no build step, and check both themes and phone width before opening a pull request. Stress or gender corrections to the photo prompt are especially useful.

## License

[MIT](LICENSE)
