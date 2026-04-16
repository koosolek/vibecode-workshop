# Icon to Component — Plugin PRD

## What it does

A Figma plugin that converts a selected icon frame into a clean, properly structured
Figma component ready for use in a design system.

## The problem

When working with icon frames in Figma, they are often raw frames or groups with
inconsistent naming, wrong sizing, or no component wrapper. Manually converting each
one is slow and error-prone.

## The solution

Select one icon frame → run the plugin → it becomes a properly named Figma component.

## Input

- A single selected frame in Figma
- The frame contains a vector shape (the icon path)

## Output

A Figma component with:
- Size: 24×24
- Fill: none (transparent background)
- A single child layer named `Shape` containing the vector
- Component name: taken from the selected frame's name
- Clips content: off

## Behavior

1. User selects a frame in Figma
2. User runs the plugin (via Plugins menu)
3. Plugin shows a simple UI: title, description, "Create Component" button
4. User clicks "Create Component"
5. Plugin converts the selected frame to a component (in place)
6. Plugin shows a success notification: "✓ [frame name] converted"
7. Plugin closes

## Error states

- Nothing selected → show notification: "Select an icon frame first"
- Selected item is not a frame → show notification: "Selection must be a frame"
- Frame has no vector child → still convert, but skip the Shape rename step

## UI

Simple panel, no icon browser, no search.

```
┌─────────────────────────────┐
│  Icon to Component          │
│  ─────────────────────────  │
│  Select a frame, then click │
│  Create Component.          │
│                             │
│  [ Create Component ]       │
└─────────────────────────────┘
```

Panel size: 300 × 160px

## Out of scope

- Bulk conversion (multiple frames at once)
- Variant creation (regular + filled)
- Color variable binding
- Icon search or browsing

## Tech

- Figma Plugin API (no framework)
- TypeScript → compiled to `code.js`
- Minimal `ui.html` (vanilla HTML/CSS/JS)
- No external network requests
- No dependencies beyond the Figma type definitions
