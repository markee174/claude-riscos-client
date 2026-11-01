# Changelog

All notable changes to !Claude. Version numbers match `!Help` and the Info box.

## 0.07 (1 Nov 2026)

### Added
- File attachments. Drag files onto the conversation window or the icon bar icon, or click **Attach...** in the toolbar to open the Attachments window, where you can drag files or type a pathname. Files from other applications arrive through `<Wimp$Scrap>`.
- Text files are sent in full as part of your message. JPEG, PNG, GIF, WebP and PDF files are sent as image and document blocks with the next message; the conversation history keeps a note of them, so later messages do not resend them.
- The window title shows how many files are attached. Attachments are cleared once Claude replies, and kept if the request fails so you can send again.
- Up to 8 files and 3MB per message. !Claude checks file contents, not file types, and warns about anything Claude cannot read.

### Changed
- WimpSlot raised from 1024K to 5120K to hold attachments.

## 0.06 (1 Nov 2026)

### Added
- CLAUDE.md: instructions sent to Claude as the system prompt with every message. Stored as `<Choices$Write>.Claude.CLAUDE/md`, so it appears as `CLAUDE.md` when copied to other systems.
- **Edit...** button in Choices. It opens CLAUDE.md in your text editor, creating it first with starter instructions if it does not exist. Changes apply to the next message; there is no need to restart !Claude.

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
