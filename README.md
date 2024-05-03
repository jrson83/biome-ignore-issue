# @biomejs/biome issue

If 'format on save' is turned on, using `formatter.ignore` the Biome.js extension will format files that should be ignored.

```json
// .vscode/settings.json
"settings": {
  "editor.formatOnSave": true
}
```

Using `files.ignore` the issue is fixed.

See <https://github.com/biomejs/biome-vscode/issues/189>

```json
// biome.json
{
  "files": {
    "ignore": ["node_modules", "no-format.js"]
  }
}
```

Using `formatter.ignore` the issue still persists.

```json
// biome.json
{
  "formatter": {
    "ignore": ["node_modules", "no-format.js"]
  }
}
```

---

To reproduce:

```sh
git clone https://github.com/jrson83/biome-ignore-issue.git
cd biome-ignore-issue
pnpm install
```

Open `packages/core/src/no-format.js` and save the file. It should not format.
