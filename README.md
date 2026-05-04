# Audio Fake Detector PRO
**Current version: 6.3**

---

Advanced audio analysis tool designed to detect fake and artificially upscaled audio using signal processing techniques.

Audio Fake Detector PRO is a high-performance audio authenticity checker focused on identifying fake high-quality audio files, including 320 kbps MP3s and lossless formats.

## 🔍 Overview

Audio Fake Detector PRO identifies audio files that have been transcoded or upscaled from lower-quality sources (e.g. 128–160 kbps MP3) into seemingly high-quality formats such as 320 kbps MP3 or FLAC.

It is designed for users who need reliable detection of audio authenticity using a combination of spectral and statistical analysis.

This tool is an independent solution for users searching for alternatives to established tools such as Fakin' The Funk.

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
- Audio quality auditing for DJs, producers, and collectors
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

## 📊 Output

- Files rated as FAKE, or detected below 170 kbps, are moved to `~Fake`
- Reports → saved in `~Report`
- Full directory structure preserved

---

## 🚀 Download

- If not found locally, required tools will be downloaded automatically:
   - Source: Google Drive / SAC Slovak Antivirus Center -> auCDtect (~72 KB)
   - Source: BtbN/FFmpeg-Builds / gyan.dev (GitHub) -> FFmpeg (~210 MB)
   - To avoid the automatic download, you can install it manually beforehand via Command Prompt: winget install --id Gyan.FFmpeg (~104 MB)
- Preview Download (~130 KB): Project site https://alessandrocomito.github.io/audiofakedetectorpro
- Direct Download (~66 KB):
   - Standard (no-install) https://bit.ly/3QAinOY
   - Portable https://bit.ly/4tDVQiM
- ZIP archives via Google Drive

---

## 🧾 Keywords (SEO)

fake audio detector, fake mp3 detector, audio authenticity checker, fake flac detection, audio analysis tool, spectral analysis audio, lossless verification tool, mp3 upscaling detection, Fakin' The Funk alternative

---

## ⚠️ Disclaimer

This tool is independent and not affiliated with any other audio analysis software.
All product names mentioned are used only for descriptive and compatibility reference purposes.
