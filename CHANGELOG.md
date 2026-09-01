# Changelog

All notable changes to this extension. Versions follow the `manifest.json` version.

## [1.7.0] — 2026-09-01

### Added
- **Content notes.** Select a run of text instead of clicking an element to leave a review note about
  the *content* — a question, a fact-check, a rewrite request. Anchored by the quote plus its
  surrounding context and heading path (W3C TextQuoteSelector model), so the agent greps the content
  source instead of resolving a DOM path. Repeated phrases are disambiguated by their context.
- Selected text is painted with the **CSS Custom Highlight API** — no DOM mutation — and re-resolves
  from `localStorage` after a reload.
- The note box gained a header: a **DESIGN** / **CONTENT** badge showing which kind you're writing, and
  a drag handle to move the box off whatever it covers.

### Changed
- Markdown export and the agent preamble describe both note kinds.
- Cheatsheet regrouped: `Alt+A` and `Alt+Shift+X` moved to the browser-shortcuts group; the two capture
  gestures are listed under "While annotating".

## [1.6.0]

### Added
- In-panel shortcuts cheatsheet behind the footer's **? shortcuts** link.

### Fixed
- Shortcut handling made reliable across keyboard layouts and macOS Option-remapping (matches the
  physical key), with debouncing so the browser command and the in-page handler never double-toggle.

## [1.4.0]

### Added
- Dev-build **source mapping** — reads the component's file and line off React / Next, Vue, Svelte and
  Angular, so a note points straight at `src/…/Component.tsx:48`.
- Richer anchors: nearest accessible label, instance ordinal ("2 of 3 matching .btn"), and the relevant
  computed styles as a before-state.

### Changed
- Overlay redesign (dark surfaces, green accent), wider panel, motion respecting `prefers-reduced-motion`.

## [1.2.0]

### Added
- Toolbar toggle and keyboard shortcuts; SPA route awareness; markdown / JSON / prompt exports;
  honest failure feedback on pages that can't be injected.

### Changed
- Repository reduced to the Chrome extension only.

## [1.0.0]

- First release: click an element, type a note, copy the notes as markdown for an AI coding agent.
