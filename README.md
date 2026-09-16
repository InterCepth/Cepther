# Cepther v1

**By Intrcepth**

A Windows desktop app for downloading video and audio from the web, with a
clean, modern interface. Paste a link, pick a format and quality, and the
file lands in your downloads folder — no command line, no browser extensions,
no ads, and no accounts.

> 🚧 **Cepther is upcoming and under active development.** Watch this repo
> for the first release.

---

## What it does

### Downloading
- **Downloads from a very wide range of sites** — whatever the bundled yt-dlp
  engine supports (1,700+ sites).
- **Format & quality picker** — a card per available stream (resolution, fps,
  codec, size), or "Best Output" to follow your saved defaults.
- **Multi-threaded downloads** — aria2c splits a file into parallel segments;
  the thread count (1–32) is configurable and can be switched off.
- **Queue, playlists and bulk import** — paste a list or load a `.txt` file,
  with concurrent processing.
- **Resume interrupted downloads** — picks back up where it left off instead
  of starting over.
- **Live stream recording** — Record from Start, or capture from now onwards.
  Recording never begins on its own; you always choose.
- **Smart clipboard monitoring** — copy a video link and Cepther offers to
  grab it, without you needing to switch back to the app.
- **Floating Dock** — an always-on-top mini window that detects the link
  you're currently looking at in your browser, so you can save or download it
  without alt-tabbing back. Saved links get their own searchable, taggable
  library.

### Media processing
- **Audio extraction** — MP3, M4A, WAV, FLAC, AAC, OGG, OPUS.
- **Format conversion** — any format to any format via FFmpeg (MKV → MP4,
  WebM → MP3, and more).
- **Cover art & ID3 metadata tagging** — title, artist, album, year, genre,
  track number and album art, embedded automatically.
- **Subtitles** — auto-detected, multiple languages, embedded in the file or
  saved separately.
- **SponsorBlock segment removal** and **per-download trimming.**

### Organization & workflow
- **Download history** — searchable, with open-file / open-folder / re-download
  / copy-link actions.
- **Optional file organisation** — auto-sort finished downloads into
  per-platform, per-creator and video/audio folders, or keep the simple
  default layout.
- **Creator Watch** — follow creators across platforms and have new uploads
  either downloaded automatically or announced with a Windows notification.
  Checks run only while the app is open.
- **Runs quietly in the background** — optional close-to-tray and start-with-
  Windows, with a single-instance guard so it never doubles up.
- **Custom yt-dlp flags and saved presets** for anything the UI doesn't cover.

### Privacy & access
- **Built-in cookie browser** — sign in to a site inside the app to unlock
  private, members-only or age-gated content, no separate browser extension
  needed.
- **Proxies, network-interface binding (VPN kill-switch) and a download
  speed limit** — set globally, or per download in the picker.

No telemetry, no analytics, no usage tracking, and no personal data is stored —
only the metadata of what you downloaded.

## Built with

- **Python** and **PySide6** for the interface (Qt stylesheets, with dark/
  light themes and colour presets).
- Two third-party packages beyond PySide6: its bundled **WebEngine** module
  (the in-app cookie browser) and **windows-toasts** (actionable Windows
  notifications). Everything else is the Python standard library.
- **SQLite** for history, presets and the Creator Watch list.

## Bundled engines

All six live in `engines/` and are always called by their full path — none is
ever taken from the system PATH, and nothing needs installing separately:

| Engine | What it does |
|---|---|
| **yt-dlp** | the download engine — site extraction, formats, metadata |
| **FFmpeg** | merging, converting, embedding, trimming |
| **ffprobe** | reading media properties (durations, streams) |
| **aria2c** | multi-connection download acceleration |
| **gallery-dl** | image and gallery sites |
| **Deno** | runs YouTube's JavaScript challenges for yt-dlp |

They can be updated from inside the app: **Settings → Maintenance**.

## Platform

Windows only.
