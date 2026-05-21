# Audio Fake Detector PRO
**Truly Free Alternative**  
Current version: 7.2 updated <img src="date2.svg" style="height: 1em; vertical-align: -3em;">

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

## 🖥 Requirements

- Windows 10/11 (32-bit or 64-bit)
- PowerShell 5+
- Internet connection (first run only, for dependencies)

---

## 🖥️ Display Configuration Guide
[cite_start]This guide explains how to correctly configure the console window for optimal readability and proper text output[cite: 1]. [cite_start]This is a one-time setup per executable or script[cite: 2].

### 1. Open Application
[cite_start]Double-click the executable (`.exe`) or double-click `Start_script.cmd` and select, if 2 scripts are in the current folder[cite: 2]:
1. [cite_start]**Portable version** [cite: 2]
2. [cite_start]**Standard version** [cite: 2]

### 2A. Console Host (Classic Method)
[cite_start]Minimize the selection window[cite: 3]. [cite_start]Right-click on the window title bar of the `.exe` or Windows PowerShell and select **Properties**[cite: 3, 4].

#### Font Settings
* [cite_start]Select **TAB: Font** [cite: 4]
* [cite_start]**Font name:** `Consolas` / `Lucida Console` [cite: 4]
* [cite_start]**Size:** `20` / `16` [cite: 4]

#### Layout Settings
* [cite_start]Select **TAB: Layout** [cite: 4]
* [cite_start]**Window Size - Width:** `118` / `118` [cite: 4]
* [cite_start]**Window Size - Height:** `32` / `40` [cite: 4]
* [cite_start]Click **OK** to confirm[cite: 4].

---

### 2B. Windows Terminal (Graphical Interface Method)
[cite_start]Open Settings by clicking the down arrow in the tab bar and selecting **Settings** (or press `Ctrl + ,`)[cite: 5].

#### Font Profile Configuration
1. [cite_start]In the left sidebar, under the "Profiles" section, click on **Windows PowerShell**[cite: 6].
2. [cite_start]Select the **Appearance** tab[cite: 6].
3. [cite_start]Locate the **Font face** option and select either `Consolas`, `Lucida Console`, `Cascadia Mono` or `Cascadia Code`[cite: 7].
4. [cite_start]Set the **Font size** to `13` (for Consolas) or `12` (for Cascadia Mono/Code or Lucida Console)[cite: 8].
5. [cite_start]Click **Save** in the bottom right corner[cite: 9].

#### Window Size Configuration
1. [cite_start]In the left sidebar, click on the top option: **Startup**[cite: 9].
2. [cite_start]Locate the **Launch columns** and **Launch rows** settings[cite: 10].
3. [cite_start]Set **Launch columns** to `120`[cite: 10].
4. [cite_start]Set **Launch rows** to `32` (or `40` if using Lucida Console)[cite: 10].
5. [cite_start]Click **Save** in the bottom right corner[cite: 11].

> ⚠️ **Important Notes:** Only modify the settings shown above. [cite_start]Do not change other options[cite: 11]. [cite_start]Console Host stores settings per executable, while Windows Terminal stores settings per profile[cite: 12].

---

### 📌 Expected Result
* [cite_start]Clear text output [cite: 13]
* [cite_start]No line wrapping issues [cite: 13]
* [cite_start]Full log visibility [cite: 13]
* [cite_start]Scrollback enabled [cite: 13]

#### Quick Summary Matrix

| Environment | Font Face | Font Size | Window Size |
| :--- | :--- | :--- | :--- |
| **Console Host** | Consolas <br> Lucida Console | 20 <br> 16 | [cite_start]118 x 32 <br> 118 x 40 [cite: 13] |
| **Windows Terminal** | Consolas <br> Lucida Console <br> Cascadia Mono <br> Cascadia Code | [cite_start]13 <br> 12 <br> 12 <br> 12 [cite: 13, 14] | [cite_start]120 x 32 <br> 120 x 40 [cite: 14] |

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

---

### 🌐 Preview
- All-in-One (Project Site — ≤ 200 KB) https://alessandrocomito.github.io/audiofakedetectorpro  
- All-in-One CMD Edition (No EXE launcher — ≤ 100 KB) https://bit.ly/4tvBk3h  

---

### ⬇️ Direct Download
- Standard (No-install — ≤ 100 KB)  https://bit.ly/3QAinOY  
- Portable (standalone — ≤ 100 KB) https://bit.ly/4tDVQiM  

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
