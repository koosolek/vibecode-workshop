# Icon to Component — Figma Plugin

## What this is

A Figma plugin that converts a selected icon frame into a clean Figma component.
Built during a Claude Code workshop. See PRD.md for full spec.

## Tech stack

- TypeScript (compiled to code.js via esbuild or tsc)
- Figma Plugin API
- Vanilla HTML/CSS/JS for UI (no frameworks)
- No external dependencies beyond @figma/plugin-typings

## File structure

```
manifest.json     → plugin metadata
code.ts           → main plugin logic (runs in Figma sandbox)
ui.html           → plugin panel UI
package.json      → build scripts and dev dependencies
tsconfig.json     → TypeScript config
```

## Plugin API constraints

- `code.ts` runs in a sandboxed environment — no DOM, no browser APIs
- `ui.html` runs in an iframe — no direct Figma API access
- Communication between them uses `figma.ui.postMessage` and `parent.postMessage`
- Network requests: only allowed to domains listed in manifest.json networkAccess

## Coding conventions

- Keep code.ts simple and linear — this is workshop code, not production code
- Prefer explicit variable names over clever one-liners
- Add a comment above each function explaining what it does in plain English
- Error handling: use `figma.notify()` for user-facing errors, `console.error()` for debug

## Build

```bash
npm install
npm run build   # compiles code.ts → code.js
```

## Testing

Load in Figma desktop:
1. Plugins → Development → Import plugin from manifest
2. Select a frame with a vector child
3. Run the plugin → click "Create Component"
4. Confirm the frame became a component with correct name and structure
