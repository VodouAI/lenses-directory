# Vodou Lenses — Community Directory

Curated index of community-contributed [Vodou](https://github.com/VodouAI/OS) Lenses.

A **Lens** is a small JavaScript module that takes a URL and returns a structured render model — recipe steps, PR diffs, map directions, Wikipedia excerpts, etc. Lenses are MIT, community-owned, and discoverable in any Vodou gateway.

## How users install a lens

```bash
# Browse the directory
vodou-core lenses search recipe

# Install from a directory entry
vodou-core lenses install recipe.allrecipes

# Or install directly from a git URL
vodou-core lenses install https://github.com/<author>/vodou-lens-<id>
```

## How to submit a lens

1. Publish your lens to a public GitHub repo with:
   - `manifest.json` at repo root
   - `index.js` at repo root (the LensModule export)
   - MIT `LICENSE`
2. Open a PR adding `lenses/<your-id>.json` to this repo. See `lenses/_template.json`.
3. A maintainer reviews:
   - License is MIT
   - Manifest claims match what the code actually does (no exfiltration, no surprises)
   - Health check passes against a current URL pattern
4. PR merged → lens appears in `_index.json` (rebuilt by CI) and is browseable in the Vodou gateway within 1 hour.

## File layout

```
lenses-directory/
├── README.md
├── _index.json          ← auto-generated; concatenation of every entry
└── lenses/
    ├── _template.json   ← copy this when adding a lens
    ├── recipe.allrecipes.json
    ├── github.pr.json
    └── ...
```

## Curation principles

- **Every lens is MIT.** No paid layer in the lens protocol.
- **The manifest is the trust contract.** The `extracts`, `requires`, and `actions` declared in the manifest must match what the runtime lens does. Drift is grounds for removal.
- **Sites change.** Authors are expected to keep their selectors current. Stale selectors auto-flag in the gateway UI; persistent failures may delist.
- **No surveillance.** Lenses must not exfiltrate user data or call analytics endpoints.

## Schema

See [`lenses/_template.json`](lenses/_template.json).

---

Built for [Vodou](https://vodou.ai) — the AI that lives in your browser.
