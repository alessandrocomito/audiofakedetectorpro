# Audio Fake Detector PRO
**Truly Free Alternative**  
[Current Version: 7.6](#-preview) <img src="date3.svg" style="height: 1em; vertical-align: -3em;">  
[Display Configuration Guide](#️-display-configuration-guide) <img src="date.svg" style="height: 1em; vertical-align: -3em;">

---

Advanced audio analysis tool designed to detect fake and artificially upscaled audio using signal processing techniques.

Audio Fake Detector PRO is a high-performance audio authenticity checker focused on identifying fake high-quality audio files, including 320 kbps MP3s and lossless formats.

## 🔍 Overview

Audio Fake Detector PRO analyses whether an audio file genuinely contains the frequency content its container bitrate implies.

Files are processed using FFmpeg (decoding to standardized PCM) and ffprobe (metadata extraction such as codec, bitrate, and stream info) as a preprocessing step.

It is specifically designed to detect fake high-bitrate lossy files, such as MP3 audio upsampled or re-encoded to appear as 320 kbps, as well as lossy material (MP3) placed inside lossless containers (FLAC, WAV) to simulate higher quality.

The engine splits each file into multiple non-final segments plus one end segment. Each non-final segment is analysed independently via spectrogram bitmap inspection. A half-or-strict-majority wall vote aggregates the per-segment findings into a single file-level verdict. Lossless files are additionally validated through auCDtect statistical PCM analysis.

---

## ⚙️ Key Features

- Detection of fake 320 kbps MP3 files
- Detection of fake lossless audio (FLAC, WAV, APE, AIFF, WV)
- Spectral cutoff and compression artifact detection
- Multi-segment frequency analysis
- Joint stereo anomaly detection
- Statistical validation using auCDtect
- Automatic dependency management (FFmpeg, FFprobe)
- High-performance spectrogram processing
- Detailed reporting (LOG, CSV, HTML)
- Moves detected files to the ~Fake folder while preserving the original directory structure

---

## 🧠 Detection Technology

Audio Fake Detector PRO uses a hybrid analysis engine:

- **Spectral Analysis**: detects frequency cutoffs, compression artifacts, and artificial bandwidth extension
- **Statistical Validation**: verifies lossless authenticity using auCDtect scoring
- **Segment-Based Voting System**: improves accuracy by analyzing multiple independent audio segments

This approach reduces false positives and improves detection reliability across different audio formats.

---

## 🎯 Use Cases

- Verifying authenticity of downloaded music files
- Detecting fake FLAC / WAV conversions from lossy sources
- Audio authenticity analysis for DJs, producers, and collectors
- Library cleaning and archival verification

---

## 📦 Supported Formats

**Lossy:**
MP3, AAC, M4A, OGG, OPUS, WMA

**Lossless:**
FLAC, WAV, APE, AIFF, AIF, WV

---

## 💡 Why Audio Fake Detector PRO?

Many audio files distributed online are not truly high quality but have been upscaled from lower-bitrate sources.

Audio Fake Detector PRO is designed to help users identify these cases with a modern, multi-layered detection approach.

It can be used as an independent alternative for users familiar with tools such as Fakin' The Funk.

---

## 📌 Requirements

- Windows 10/11 (32-bit or 64-bit)
- PowerShell 5+
- Internet connection (first run only, for dependencies)

---

## 🖥️ Display Configuration Guide
This guide explains how to correctly configure the console window for optimal readability and proper text output. This is a one-time setup per executable or script.

### 1. Open Application
Double-click the executable (`.exe`) or double-click `Start_script.cmd` and select, if 2 scripts are in the current folder:
1. **Portable version**
2. **Standard version**

### 2A. Console Host (Classic Method)
Minimize the selection window. Right-click on the window title bar of the `.exe` or Windows PowerShell and select **Properties**.

#### Font Settings
* Select **TAB: Font**
* **Font name:** `Consolas` / `Lucida Console`
* **Size:** `20` / `16`

#### Layout Settings
* Select **TAB: Layout**
* **Window Size - Width:** `118` / `118`
* **Window Size - Height:** `32` / `40`
* Click **OK** to confirm.

> ⚠️ **Important Notes:** Only modify the settings shown above. Do not change other options. Console Host stores settings per executable.

---

### 2B. Windows Terminal (Graphical Interface Method)
Minimize the selection window. Open Settings by clicking the down arrow in the tab bar and selecting **Settings** (or press `Ctrl + ,`).

#### Font Profile Configuration
1. In the left sidebar, under the "Profiles" section, click on **Windows PowerShell**.
2. Select the **Appearance** tab.
3. Locate the **Font face** option and select either `Consolas`, `Lucida Console`, `Cascadia Mono` or `Cascadia Code`.
4. Set the **Font size** to `13` (for Consolas) or `12` (for Cascadia Mono/Code or Lucida Console).
5. Click **Save** in the bottom right corner.

#### Window Size Configuration
1. In the left sidebar, click on the top option: **Startup**.
2. Locate the **Launch columns** and **Launch rows** settings.
3. Set **Launch columns** to `120`.
4. Set **Launch rows** to `32` (or `40` if using Lucida Console).
5. Click **Save** in the bottom right corner.

> ⚠️ **Important Notes:** Only modify the settings shown above. Do not change other options. Windows Terminal stores settings per profile.

---

### 📌 Expected Result
* Clear text output
* No line wrapping issues
* Full log visibility
* Scrollback enabled

#### Quick Summary Matrix

| Environment | Font Face | Font Size | Window Size |
| :--- | :--- | :--- | :--- |
| **Console Host** | Consolas <br> Lucida Console | 20 <br> 16 | 118 x 32 <br> 118 x 40 |
| **Windows Terminal** | Consolas <br> Cascadia Mono <br> Cascadia Code <br><br> Lucida Console | 13 <br> 12 <br> 12 <br><br> 12 | 120 x 32 <br> 120 x 32 <br> 120 x 32 <br><br> 120 x 40 |

---

## 📊 Output

- Files rated as FAKE, or detected below 170 kbps, are moved to `~Fake`
- Reports → saved in `~Report`
- Full directory structure preserved

---

## 🚀 Download

### ⚙️ Automatic Dependencies
If required tools are not found locally, they will be downloaded automatically:

- auCDtect (72 KB) — source: SAC Slovak Antivirus Center https://www.sac.sk/download/utildisk/aucdtect.zip
- FFmpeg (~105 MB) — source: gyan.dev https://www.gyan.dev/ffmpeg/builds/ffmpeg-release-essentials.zip 

To avoid automatic download of FFmpeg, install manually via Command Prompt:

```bash
winget install --id Gyan.FFmpeg
```

To update:

```bash
winget upgrade --id Gyan.FFmpeg
```

🌐 Preview
- All-in-One (Project Site — ≤ 500 KB) https://alessandrocomito.github.io/audiofakedetectorpro
- All-in-One v7.6 (mirror — ≤ 500 KB) https://bit.ly/3PvzH7Q
- All-in-One 💡 CMD Edition (Double-click PS1 launcher, no EXE — ≤ 400 KB, reduces AV false positives)

---

### ⬇️ Direct Download
- Standard (No-install — ≤ 200 KB)  https://bit.ly/3QAinOY  
- Portable (standalone — ≤ 200 KB) https://bit.ly/4tDVQiM  

---

### 📁 Archive
- ZIP packages (Google Drive)  
  Full releases, backups, and bundled builds

## 🧾 Keywords (SEO)

fake audio detector, fake mp3 detector, audio authenticity checker, fake flac detection, audio analysis tool, spectral analysis audio, lossless verification tool, mp3 upscaling detection, Fakin' The Funk alternative

---

## ⚠️ Disclaimer

This tool is independent and not affiliated with any other audio analysis software.
All product names mentioned are used only for descriptive and compatibility reference purposes.
