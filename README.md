# Audio Fake Detector PRO

**Truly Free Alternative**  
[v8.3 (x64) 2026-08-01](#-preview)

> 🚀 Audio Analyzer Update: Significantly reduced waiting times during analysis compared to v7.7 versions - same detection precision.

---

## 📌 Requirements

* Windows 10/11 (32-bit or 64-bit) / v8.x: Windows 10/11 64-bit + .NET 8 Runtime (web download and auto install offered)
* PowerShell 5.1 (already installed on Windows 10/11)
* Internet connection (first run only, for dependencies)

---

Advanced audio analysis tool designed to detect fake and artificially upscaled audio using signal processing techniques.

Audio Fake Detector PRO is a high-performance audio authenticity checker focused on identifying fake high-quality audio files, including 320 kbps MP3s and lossless formats.

## 🔍 Overview

Audio Fake Detector PRO analyses whether an audio file genuinely contains the frequency content its container bitrate implies.

Files are processed using FFmpeg (decoding to standardized PCM) and ffprobe (metadata extraction such as codec, bitrate, and stream info) as a preprocessing step.

It is specifically designed to detect fake high-bitrate lossy files, such as MP3 audio upsampled or re-encoded to appear as 320 kbps, as well as lossy material (MP3) placed inside lossless containers (FLAC, WAV) to simulate higher quality.

The engine splits each file into multiple non-final segments plus one end segment. Each non-final segment is analysed independently via spectrogram bitmap inspection. A half-or-strict-majority wall vote aggregates the per-segment findings into a single file-level verdict. Lossless files are additionally validated through auCDtect statistical PCM analysis.

---

## 📸 Screenshots

![Screenshot 1](Screenshot%201.png)

![Screenshot 2](Screenshot%202.png)

![Screenshot 3](Screenshot%203.png)

---

## ⚙️ Key Features

* Detection of fake 320 kbps MP3 files
* Detection of fake lossless audio (FLAC, WAV, APE, AIFF, WV)
* Spectral cutoff and compression artifact detection
* Multi-segment frequency analysis
* Joint stereo anomaly detection
* Statistical validation using auCDtect
* Automatic dependency management (FFmpeg, FFprobe)
* High-performance spectrogram processing
* Detailed reporting: LOG - CSV  
On selection window, click to cycle: \[CSV ( )] → \[CSV (,)] → \[CSV (;)] → \[CSV ( )]
* Moves detected files to the \~Fake folder while preserving the original directory structure

---

## 🧠 Detection Technology

Audio Fake Detector PRO uses a hybrid analysis engine:

* **Spectral Analysis**: detects frequency cutoffs, compression artifacts, and artificial bandwidth extension
* **Statistical Validation**: verifies lossless authenticity using auCDtect scoring
* **Segment-Based Voting System**: improves accuracy by analyzing multiple independent audio segments

This approach reduces false positives and improves detection reliability across different audio formats.

---

## 🎯 Use Cases

* Verifying authenticity of downloaded music files
* Detecting fake FLAC / WAV conversions from lossy sources
* Audio authenticity analysis for DJs, producers, and collectors
* Library cleaning and archival verification

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

## 🚀 Download

### ⚙️ Automatic Dependencies

If required tools are not found locally, they will be downloaded automatically:

- auCDtect (72 KB) - source: SAC Slovak Antivirus Center  
📥 https://www.sac.sk/download/utildisk/aucdtect.zip

- FFmpeg - source for v7.7: gyan.dev (~105 MB) / v8.x: BtbN (67.2 MB)  
📥 https://www.gyan.dev/ffmpeg/builds/ffmpeg-release-essentials.zip  
📥 https://github.com/BtbN/FFmpeg-Builds/releases/download/latest/ffmpeg-n8.1-latest-win64-lgpl-shared-8.1.zip  

To avoid automatic download of FFmpeg from gyan.dev, install manually via Command Prompt:
```bash
winget install --id Gyan.FFmpeg.Essentials
```
To update:
```bash
winget upgrade --id Gyan.FFmpeg.Essentials
```
- .NET 8 Runtime (27.3 MB, web download and auto install offered) - source: dotnet.microsoft.com  
📥 https://builds.dotnet.microsoft.com/dotnet/Runtime/8.0.29/dotnet-runtime-8.0.29-win-x64.exe  

To avoid automatic download of .NET 8 Rutime from dotnet.microsoft.com, install manually via Command Prompt:
```bash
winget install Microsoft.DotNet.Runtime.8
```

## 🌐 Preview

* AudioFakeDetector8.7z/zip (x64) (Portable+Standard editions, FFmpeg web update offered)  
📄 https://bit.ly/4hu7ucW 📥 https://bit.ly/4fS44iY 📥 https://bit.ly/45oOWU9  📁 Google Drive (32.8 MB / 57.6 MB)  
* AudioFakeDetector8_slim.zip (x64) (Portable+Standard editions, web downloads)  
👁️ https://bit.ly/4fQq38N  📥 https://bit.ly/3RGAALQ 📁 Google Drive (543 KB)  
- Portable : delete AudioFakeDetector\_v8.x.ps1 from zip  
- Standard: delete AudioFakeDetector\_v8.x\_Portable.ps1 from zip

v7.7_2026-07-21 (x86/x64)  
* AudioFakeDetector\_v7.7.7z (Portable+Standard editions, FFmpeg web update offered)  
📄 https://bit.ly/4uYeh1O  📥 https://bit.ly/4oOsywh    📁 Google Drive (28.7 MB)  
* AudioFakeDetector\_v7.7\_slim.zip (Portable+Standard editions, web downloads)  
👁️ https://bit.ly/4xgBhLV  📥 https://bit.ly/4g0jlyA    📁 Google Drive (172 KB)  
- Portable : delete AudioFakeDetector\_v7.7.ps1 from zip  
- Standard: delete AudioFakeDetector\_v7.7\_Portable.ps1 from zip

## 💬 Support \& Community

Have questions, bug reports, or want to discuss features? Join the official thread on Audio Science Review:  
👉 [Audio Science Review - Audio Fake Detector PRO Forum Thread](https://www.audiosciencereview.com/forum/index.php?threads/audio-fake-detector-pro.71538/)

---

## ℹ️ Technical Notes

Smart Temp Management

* Portable: all data is stored locally next to the script - no AppData / Temp touched:  
.\\Data\\App\\ ← auCDtect, FFmpeg, state/stamp files  
.\\Data\\App\\Temp\\ ← spectrogram PNGs, WAV segments (deleted after each run)  
If FFmpeg is already installed system-wide it is used as-is
* Standard: tools and state files are stored in:  
%LOCALAPPDATA%\\AudioFakeDetector\\ ← auCDtect, FFmpeg, state/stamp files  
%TEMP%\\ ← spectrogram PNGs, WAV segments (deleted after each run)

---

## 🧾 Keywords (SEO)

fake audio detector, fake mp3 detector, audio authenticity checker, fake flac detection, audio analysis tool, spectral analysis audio, lossless verification tool, mp3 upscaling detection, Fakin' The Funk alternative

---

## ⚠️ Disclaimer

This tool is independent and not affiliated with any other audio analysis software.
All product names mentioned are used only for descriptive and compatibility reference purposes.

