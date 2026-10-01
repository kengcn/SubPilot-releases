# SubPilot

SubPilot translates English subtitles into other languages with an AI
provider of your choice, using your own API key. It runs on Windows as
a console program.

Version 0.9 is an early preview for a few testers. Feedback is very
welcome (see below).

## Download

Get the latest zip from [Releases](https://github.com/kengcn/SubPilot-releases/releases):

- **`SubPilot-<version>-windows-x64-ffmpeg.zip`**: subtitle files and
  video files. Includes FFmpeg (LGPL).
- **`SubPilot-<version>-windows-x64-standard.zip`**: smaller. Subtitle
  files work as is; for video files, add FFmpeg yourself.

The release page lists the SHA-256 of each zip. To check a download in
PowerShell: `Get-FileHash .\SubPilot-0.9.0-windows-x64-ffmpeg.zip`

## You need

- Windows 10 or 11, 64-bit.
- An API key from Google Gemini, OpenAI, xAI Grok, DeepSeek or
  Anthropic Claude. The provider bills your key; some offer a free tier.

## Get started

1. Unzip the whole folder somewhere you can write to, for example
   `Documents\SubPilot`. Do not copy `SubPilot.exe` on its own.
2. Double-click `SubPilot.exe`. SubPilot is not code-signed yet, so
   Windows may show "Windows protected your PC": choose "More info",
   then "Run anyway".
3. Choose "Subtitle file" (or "Video file"), drag your English `.srt`
   into the window and press Enter, choose "Free", your AI provider and
   the target language. The first time, SubPilot asks for your API key.
4. The translation is saved as `<file name>.<language>.srt` in
   `data\outbox`, for example `Movie.zh-CN.srt`.

`QUICKSTART.txt` in the zip covers video files, FFmpeg, resuming an
interrupted task and how your API key is stored. Please read it first.

## What to expect

- Progress is saved as it goes. A task that was closed or stopped
  (for example a used-up quota or a rejected key) resumes without
  translating finished parts again.
- Per-minute rate limits are waited out automatically.
- A few lines the AI cannot translate are kept in English and listed
  at the end.
- Subtitle text is sent to the AI provider you choose. Your API key is
  stored in the `data` folder next to `SubPilot.exe`; do not share or
  upload that folder.

Known limitations of each version are in its release notes.

## Feedback

Please [open an issue](https://github.com/kengcn/SubPilot-releases/issues)
with:

- the version (`SubPilot.exe --version`) and which zip you used,
- the AI provider and target language,
- what you did, what you expected and what happened,
- the console output, and the `error-*.log` / `ai-issues-*.log` files
  from `data\logs` if there are any.

**Never include your API key.** The log files contain subtitle text;
check them before you attach them.

The SubPilot source code is not public.
