# claude-riscos-client

A vibe-coded RISC OS desktop client for Claude, written in BBC BASIC.

**Unofficial.** Not affiliated with or endorsed by Anthropic.

## What it does

!Claude puts an icon on the icon bar and opens a conversation window. Type in the field at the top, press Return, and Claude's reply appears in the window below. Requests run through curl in a TaskWindow, so the desktop keeps multitasking while you wait.

It is deliberately simple:

- Text only: no images, attachments or streaming.
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
- **MENU** over the window: Clear, Choices.
- Interactive Help works on every window.

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
- Development happens on a Linux, Mac or Windows machine with git, and the files are copied to RISC OS for testing.

## Contributing

Issues and pull requests are welcome. Please test changes on real RISC OS before submitting, and keep to the RISC OS Style Guide.

## Licence

Copyright 2026 Mark Stephens.

Licensed under the Apache License, Version 2.0. See `LICENSE`.
```

The copyright line matches the header I suggested for `!RunImage`. If you'd rather the copyright sat with IDRsolutions, change it in both places.
