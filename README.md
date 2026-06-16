<div align="center">

# browser-annotations

**Click what you want changed. Type the fix. Paste into your AI coding agent.**

A tiny Chrome extension that turns *"make the button greener, move it left"* into precise notes your
agent can act on — with the **exact source file** (or the text to search for) attached.

No account. No server. Nothing leaves your browser.

![License: MIT](https://img.shields.io/badge/License-MIT-10A37F.svg)
![Manifest V3](https://img.shields.io/badge/Chrome-MV3-555.svg)
![Works with](https://img.shields.io/badge/works%20with-Claude%20Code%20·%20Cursor%20·%20Codex-10A37F.svg)

<img src="docs/demo.png" alt="browser-annotations: numbered green pins on a live page + the annotations panel" width="820">

</div>

---

## Your agent edits the UI blind. This gives it eyes.

You ask for a change. Your agent writes code it can't see. Then you squint at the browser and type a
whole paragraph — *"the CTA's too big, move it left, wrong green."* Slow, and a lot gets lost on the way.

**Point at the real page instead.** Click the element → type the change → **Copy** → paste to your agent.
Every note carries exactly what's needed to find the code:

- **On a dev build** — the component's **file and line** (e.g. `src/components/Cart.tsx:48`), read straight
  from React / Next, Vue, Svelte or Angular.
- **Always** — the element's tag, `id`, `data-testid`, nearby label and visible text — the exact strings
  your agent can search for. Random build-generated class names get flagged as noise so it ignores them.

So your agent edits the **right** code instead of guessing.

## Install (30 seconds)

Not on the Chrome Web Store yet, so load it by hand:

1. Download this repo (green **Code** button → **Download ZIP**, then unzip). Or `git clone` it.
2. Open **`chrome://extensions`** and turn on **Developer mode** (top-right toggle).
3. Click **Load unpacked** and pick the **`extension/`** folder.
4. Pin **browser-annotations** to your toolbar so it's one click away.

## Use it

1. **Turn it on** — click the toolbar button (or press **Alt+Shift+A**). The icon shows a green ●.
2. **Annotate** — hover, click an element, type what to change, hit **Save**. Repeat for as many as you like.
3. **Copy** — click **Copy** (or **Alt+Shift+C**) and paste into your agent.
4. Turn it off when done. Your notes are saved per page and come back next time you turn it on.

Works on any normal web page. (It can't run on `chrome://` pages, the Web Store, or PDFs — you'll see a red `!` if you try.)

### Shortcuts

| Key | What it does |
|---|---|
| **Alt+Shift+A** | turn the overlay on / off |
| **Alt+Shift+C** | copy all notes (ready to paste) |
| **Alt+A** | pause / resume clicking (clicks pass through while paused) |
| **Alt+Shift+X** | clear all notes (asks first) |
| **⌘/Ctrl+Enter** | save the note · **Esc** to cancel |

Not sure? Click **? shortcuts** at the bottom of the panel for the full list. If **Alt+A** does nothing,
Chrome left it unassigned — that link opens `chrome://extensions/shortcuts` where you can set it.

## What your agent gets

Each note starts with **how to find the element in your code**, then your change and the current styles:

```markdown
App: react (dev build — source file:line per note; grep by data-testid / id / text, ignore hashed classes).

## [#2] make this the primary button — brand green
source: src/components/Cart.tsx:48  <CheckoutButton>
`<button class="btn" data-testid="checkout" type="submit">`  — text: "Place order"
label: "Place your order"
instance: 2 of 3 matching button.btn
dom-path (positional fallback): `main > form > button` · box 180x44 @640,520 · css fontSize:15px fontWeight:600 padding:12px 20px borderRadius:8px
```

- **Dev build?** Your agent opens `src/components/Cart.tsx:48` directly — no searching.
- **Otherwise** it searches for `data-testid="checkout"` / `"Place order"`, and **instance** ("2 of 3")
  tells it which copy you meant when an element repeats.
- The **css** line is the "before" state, so a change like *"make the padding smaller"* has a starting point.

## Why it works on real apps

- **Finds your source** — on a dev build it reads the component's file and line right off the framework
  (React / Next, Vue, Svelte, Angular). On a production site it instead picks the best thing to search for
  (`data-testid` › `id` › visible text) and ignores random build-generated class names.
- **Survives navigation** — in single-page apps (React, Vue, Next…) your notes stay attached to the right
  page as you click around.
- **Tiny and safe** — one small script (~36 KB, plain JavaScript, no build step, no framework). Your notes
  live only in the page, on your machine.
- **Barely any permissions** — `activeTab`, `scripting`, `storage`, and `clipboardWrite` (so the copy
  shortcut works). No website access, no tracking, no account, no server.

## Roadmap

Edit/undo, smarter pin re-locating, an options page, shadow-DOM & iframe support, a Web Store listing,
and more — see **[extension/ROADMAP.md](extension/ROADMAP.md)**.

## License

[MIT](LICENSE) © kuzmany
