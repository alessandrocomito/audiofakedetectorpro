# Audio Fake Detector PRO
**Truly Free Alternative**  
[Current Version: 7.7 (2026-07-01)](#-preview)

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
- Detailed reporting (LOG)
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

## 🚀 Download

### ⚙️ Automatic Dependencies
If required tools are not found locally, they will be downloaded automatically:

- auCDtect (72 KB) - source: SAC Slovak Antivirus Center  
  📥 https://www.sac.sk/download/utildisk/aucdtect.zip
- FFmpeg (~105 MB) - source: gyan.dev  
  📥 https://www.gyan.dev/ffmpeg/builds/ffmpeg-release-essentials.zip 

To avoid automatic download of FFmpeg, install manually via Command Prompt:

```bash
winget install --id Gyan.FFmpeg.Essentials
```

To update:

```bash
winget upgrade --id Gyan.FFmpeg.Essentials
```

## 🌐 Preview
- AudioFakeDetector_v7.7_All-In-One.zip (Portable+Standard editions, web downloads)  
  👁️ https://bit.ly/4xgBhLV  📥 https://bit.ly/4g0jlyA 📁 Google Drive (141 KB (145.336 byte))  
 SHA256: 1f586f2c8fc3d411368d0dd1290a46a54d53d38a99067c316109e0e95da0915d
- Portable : delete AudioFakeDetector_v7.7.ps1 from zip
- Standard: delete AudioFakeDetector_v7.7_Portable.ps1 from zip
- AudioFakeDetector_v7.7_Portable_Offline.7z   (Full offline, FFmpeg web update offered)  
  👁️ https://bit.ly/4oNoKeV 📄 https://bit.ly/4uYeh1O  📥 https://bit.ly/4oOsywh  📁 Google Drive (28,5 MB (29.905.957 byte)) SHA256: 5d0878a7cf6bb3daf85b33c05404d4db7d224f36702a933d6cfcd61592a33c6d

---

## 💬 Support & Community
Have questions, bug reports, or want to discuss features? Join the official thread on Audio Science Review:  
👉 [Audio Science Review - Audio Fake Detector PRO Forum Thread](https://www.audiosciencereview.com/forum/index.php?threads/audio-fake-detector-pro.71538/)

---

## 🧾 Keywords (SEO)

fake audio detector, fake mp3 detector, audio authenticity checker, fake flac detection, audio analysis tool, spectral analysis audio, lossless verification tool, mp3 upscaling detection, Fakin' The Funk alternative

---

## ⚠️ Disclaimer

This tool is independent and not affiliated with any other audio analysis software.
All product names mentioned are used only for descriptive and compatibility reference purposes.
