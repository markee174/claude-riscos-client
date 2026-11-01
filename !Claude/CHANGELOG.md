# Changelog

All notable changes to !Claude. Version numbers match `!Help` and the Info box.

## 0.05 (1 Nov 2026)

### Added
- Start-up checks. If no API key is set, or curl cannot be found as an `Alias$curl` alias or a file on `Run$Path`, !Claude shows a warning dialogue explaining what to do. It still loads, so you can open Choices and set the key.

## 0.04 (26 Oct 2026)

### Fixed
- "Mistake" errors when drawing the conversation and when showing API errors. Function names ending in `$` (`FNhead$`, `FNline$`, `FNjson$`, `FNpreview$`, `FNsmall$`, `FNbytes$`) failed when called. They are now plain names (`FNhead`, `FNline` and so on) and still return strings.

### Added
- Apache License 2.0 header at the top of `!RunImage`.

## 0.03 (26 Oct 2026)

### Changed
- Functions now return once, at the end, instead of returning early with `IF ... THEN =value`. This was an attempt to fix the "Mistake" error at the start of `FNhead$`. It did not fix it; 0.04 found the real cause.

## 0.02 (26 Oct 2026)

### Fixed
- "Syntax error" at start-up. The constant `TOOLH%` begins with the keyword `TO`, so BASIC tokenised it as `TO OLH%`. All upper-case variable names are now lower case (`toolh%`, `lh%`, `margin%`, `maxl%`, `bufsize%`), which BASIC never tokenises.

## 0.01 (26 Oct 2026)

First version, written by Claude from a one-sentence prompt.

- Icon bar icon with Info, Choices and Quit menu.
- Conversation window with a toolbar pane: type a message and press Return or click Send.
- Requests go to the Anthropic Messages API through curl in a TaskWindow, so the desktop keeps multitasking.
- Replies drawn in the desktop font and word-wrapped to the window width.
- Choices window for the API key, model and an optional CA file, saved to `<Choices$Write>.Claude.Choices`.
- Interactive Help for every window.
- Text only. Markdown appears as typed, and characters outside Latin-1 show as `?`.
