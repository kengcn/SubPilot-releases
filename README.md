# SubPilot

[中文说明](#中文说明)

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
PowerShell: `Get-FileHash .\SubPilot-0.9.2-windows-x64-ffmpeg.zip`

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
- A malformed entry in a subtitle file is skipped; the rest is
  translated and the skipped lines are listed at the end.
- Subtitle text is sent to the AI provider you choose. Your API key is
  stored in the `data` folder next to `SubPilot.exe`; do not share or
  upload that folder.
- When a task starts, SubPilot downloads its current model settings
  from the SubPilot server; nothing is sent with that request. If it
  fails, the last saved or built-in settings are used.

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

---

## 中文说明

SubPilot 使用你自己的 AI 服务 API key，把英文字幕翻译成其他语言。它是
Windows 上的命令行（控制台）程序，界面为英文。

0.9 版是给少数试用者的早期预览版，非常欢迎反馈（见下方"反馈"）。

### 下载

在 [Releases](https://github.com/kengcn/SubPilot-releases/releases) 下载最新的 zip：

- **`SubPilot-<版本>-windows-x64-ffmpeg.zip`**：可处理字幕文件和视频文件，
  已附带 FFmpeg（LGPL）。
- **`SubPilot-<版本>-windows-x64-standard.zip`**：体积较小。字幕文件可直接
  使用；处理视频文件需要自行放入 FFmpeg。

发布页列出了每个 zip 的 SHA-256。在 PowerShell 中核对下载文件：
`Get-FileHash .\SubPilot-0.9.2-windows-x64-ffmpeg.zip`

### 使用前准备

- Windows 10 或 11，64 位。
- 以下任一服务的 API key：Google Gemini、OpenAI、xAI Grok、DeepSeek 或
  Anthropic Claude。费用由服务商向你的 key 收取，部分服务有免费额度。

### 开始使用

1. 把整个文件夹解压到你有写入权限的位置，例如 `Documents\SubPilot`。不要只
   复制 `SubPilot.exe`。
2. 双击 `SubPilot.exe`。SubPilot 暂未做代码签名，Windows 可能提示"Windows
   已保护你的电脑"：点"更多信息"，再点"仍要运行"。
3. 选择 "Subtitle file"（或 "Video file"），把英文 `.srt` 拖进窗口后按回车，
   再选择 "Free"、你的 AI 服务和目标语言。第一次使用时会要求输入 API key。
4. 译文保存在 `data\outbox`，文件名为 `<文件名>.<语言>.srt`，例如
   `Movie.zh-CN.srt`。

zip 中的 `QUICKSTART.txt`（英文）说明了视频文件、FFmpeg、继续中断的任务，以及
API key 的保存方式，请先阅读。

### 预期行为

- 进度随时保存。被关闭或中途停止的任务（例如额度用完、key 被拒绝）可以继续，
  已完成的部分不会重新翻译。
- 遇到每分钟请求次数限制时会自动等待。
- AI 无法翻译的少数几行会保留英文，并在结束时列出。
- 字幕文件中格式错误的条目会被跳过，其余照常翻译，结束时列出所在行号。
- 字幕文本会发送给你选择的 AI 服务。API key 保存在 `SubPilot.exe` 旁边的
  `data` 文件夹中；不要分享或上传这个文件夹。
- 每次开始任务时，SubPilot 会从 SubPilot 服务器下载当前的模型设置，这个请求
  不发送任何内容；下载失败时使用上次保存的或内置的设置。

各版本的已知限制见对应的发布说明。

### 反馈

请[提交 issue](https://github.com/kengcn/SubPilot-releases/issues)，中文或英文
均可，并附上：

- 版本（`SubPilot.exe --version`）和使用的 zip，
- AI 服务和目标语言，
- 你的操作、预期结果和实际结果，
- 控制台输出，以及 `data\logs` 中的 `error-*.log` / `ai-issues-*.log`（如有）。

**切勿包含你的 API key。** 日志文件含有字幕文本，附上前请先检查。

SubPilot 源代码暂不公开。
