# claude-riscos-client

A vibe-coded RISC OS desktop client for Claude, written in BBC BASIC.

**Unofficial.** Not affiliated with or endorsed by Anthropic.

## What it does

!Claude puts an icon on the icon bar and opens a conversation window. Type in the field at the top, press Return, and Claude's reply appears in the window below. Requests run through curl in a TaskWindow, so the desktop keeps multitasking while you wait.

It is deliberately simple:

- No streaming: replies appear when they are complete.
- Markdown appears as typed (`**bold**`, `# headings`).
- Characters outside Latin-1 show as `?`.
- The conversation lives in memory and is lost when you quit.

## Requirements

- RISC OS 5. Tested on RISCOSbits FAST, RISC OS 5.30
- curl with HTTPS support. curl is not in PackMan's default sources: add the riscos.info source first, then install curl:
  `pkg http://www.riscos.info/packages/pkg/autobuilt`
  Check it works by typing `curl --version` in a Task window (Ctrl-F12).
- An Anthropic API key from [console.anthropic.com](https://console.anthropic.com). Your claude.ai chat subscription cannot be used directly, but Team and Max plans include monthly API credits you can link to a Console organisation. Otherwise the API is pay-as-you-go.

## Installing

1. Download the zip from the [latest release](../../releases/latest), not the green Code button. The release zip keeps RISC OS file types.
2. Unzip it with SparkFS or Info-ZIP and copy `!Claude` wherever you keep applications.
3. Run `!Claude`, choose **Choices...** from the icon bar menu, paste in your API key and click **Set**.

## Using it

- **SELECT** on the icon bar icon opens the conversation window.
- **MENU** on the icon bar icon: Info, Choices, Quit.
- **MENU** over the window: Export as text, Save reply, Save code, Save attachment, Copy, Select all, Save conversation, Saved conversations, Usage, Clear, Choices.
- **Saved conversations:** Save conversation (or F3) keeps the conversation; Saved conversations lists them by date and title so you can reload one and carry on.
- **Selecting text:** drag with SELECT over the conversation, click ADJUST to extend, double-click for a paragraph. **Copy** puts it on the clipboard.
- **Saving:** each Save item opens a Save as box; drag its icon to a Filer window. **Save code** saves the code blocks from Claude's last reply, with BBC BASIC saved as BASIC text ready to run.
- Interactive Help works on every window.
- **Attaching files:** drag files onto the conversation window or the icon bar icon, or click **Attach...**. Text files are sent in full; JPEG, PNG, GIF, WebP and PDF files are sent as images and documents. Up to 8 files and 3MB per message.

**CLAUDE.md** holds instructions sent to Claude with every message, such as "Reply in plain British English". Click **Edit...** in Choices to open it in your text editor; save it there and the change applies to your next message. It is stored as `<Choices$Write>.Claude.CLAUDE/md`.

**Token usage:** a note after each reply shows the tokens it used. **Usage...** in the window menu shows totals and, once you enter your credit balance and prices, an estimate of the credit left. The API cannot report your real balance, so it is an estimate.

**Updates:** when !Claude starts, it checks GitHub for a newer release and offers to copy the Releases page address to the clipboard. You can skip a particular release, or turn the check off in Choices.

Choices are saved in `<Choices$Write>.Claude.Choices`. **Your API key is stored there in plain text.** The temporary curl config holding the key is deleted after each request.

## Troubleshooting

- **"No reply after three minutes" or "curl: ..."**: curl is missing or not on Run$Path. If PackMan put it somewhere else, add an alias to your boot sequence:
  `Set Alias$curl <path to curl>.curl %*0`
- **Certificate errors**: put the path of a CA bundle in the CA file field in Choices.
- **Red "API: ..." messages**: these come from Anthropic. A bad key gives `authentication_error`; an account without credit gives a billing message.

## How it was made

!Claude was written by Claude (Anthropic's AI) from a one-sentence prompt, then debugged over four rounds of feeding error messages back in. This is a spare time passion project to learn about AI. The code is commented, but treat it as a working prototype rather than a polished product.

## Repository layout

- BASIC is stored as text (`!RunImage,fd1`), so changes show up as readable diffs.
- File types are carried as `,xxx` filename suffixes (`,feb` Obey, `,fd1` BASIC text, `,ff9` Sprite, `,fff` Text).
- Development happens on a Linux, Mac or RISC OS machine with git, and tested on RISC OS 5 machines.

## Contributing

Issues and pull requests are welcome. Please test changes on real RISC OS before submitting, and keep to the RISC OS Style Guide.

## Licence

Copyright 2026 Mark Stephens.

Licensed under the Apache License, Version 2.0. See `LICENSE`.
