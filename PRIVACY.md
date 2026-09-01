# Privacy Policy — browser-annotations

**Short version: the extension collects nothing, sends nothing, and has no server to send it to.**

## What it stores

Your notes — the text you type, plus the element anchor or quoted text they're attached to — are saved
in the **`localStorage` of the page you annotated**, on your own machine. They stay there until you
clear them (panel **Clear**, **Alt+Shift+X**, or clearing site data in your browser).

The extension also stores a per-tab on/off flag through `chrome.storage`, so it remembers whether the
overlay is active. That flag holds no page content.

## What leaves your browser

Nothing, unless you make it: pressing **Copy** (or **Alt+Shift+C**) puts your notes on your system
clipboard so you can paste them where you want. No network requests are made by this extension at all —
no analytics, no telemetry, no crash reporting, no remote code, no account.

## Permissions and why

| Permission | Why it's needed |
|---|---|
| `activeTab` | Reach the tab you're currently on, only when you activate the extension. |
| `scripting` | Inject the annotation overlay into that tab. |
| `storage` | Remember whether the overlay is on or off, per tab. |
| `clipboardWrite` | Let the copy shortcut put the notes on your clipboard. |

There are **no `host_permissions`** — the extension has no standing access to any website. It touches a
page only after you turn it on there.

## Third parties

None. No SDKs, no external scripts, no hosted services.

## Contact

Questions or concerns: open an issue at
https://github.com/kuzmany/browser-annotations/issues
