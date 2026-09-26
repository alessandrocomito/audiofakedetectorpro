# Audio Fake Detector PRO

**Truly Free Alternative**

<a href="https://github.com/alessandrocomito/audiofakedetectorpro/blob/main/README.md#-preview">
  <img src="https://img.shields.io/badge/Preview%20%26%20Download%20v8.5%20(x64)-0088cc" alt="Preview & Download v8.5 (x64)" />
</a>

---

Advanced audio analysis tool designed to detect fake and artificially upscaled audio using signal processing techniques.

Audio Fake Detector PRO is a high-performance audio authenticity checker focused on identifying fake high-quality audio files, including 320 kbps MP3s, lossless formats, Hi-Res/Ultra-Hi-Res PCM, and native DSD (SACD-derived .dsf / .dff).

---

## 💡 Why Audio Fake Detector PRO?

Many audio files distributed online are not truly high quality but have been upscaled from lower-bitrate sources.

Audio Fake Detector PRO is designed to help users identify these cases with a modern, multi-layered detection approach, serving as an independent alternative for users familiar with other tools.

---

## 📸 Screenshots

Start_script_no_move.cmd (Intel Core 2 Duo test)

![Screenshot 1](Screenshot%201.png)

![Screenshot 2](Screenshot%202.png)

![Screenshot 3](Screenshot%203.png)

![Screenshot 4](Screenshot%204.png)

Performance note: Audio Fake Detector PRO prioritizes detection coverage and cross-verification over raw analysis speed.  
Some lossless files require significantly more processing time, particularly when LAC and FLAD are both used for independent verification.  

If you want to evaluate detection performance rather than speed alone, you can use the following known test files:  
mp4 192kbps zansei.flac - a FLAC created from an AAC 192 kbps source  
👁️ <a href="https://bit.ly/4zMVTww">mp4 192kbps zansei.flac</a>  <sub><img src="https://images.icon-icons.com/1011/PNG/512/Google_Drive_icon-icons.com_75713.png" width="18" height="18" alt="Google Drive"></sub> Google Drive (101 MB)  
Self explained  
👁️ <a href="https://bit.ly/3V7apiF">FAKE_LOSSLESS__MP3_294kbps__DSRE__96kHz_24bit.flac</a> <sub><img src="https://images.icon-icons.com/1011/PNG/512/Google_Drive_icon-icons.com_75713.png" width="18" height="18" alt="Google Drive"></sub> Google Drive (170 MB)

---

## ⚙️ Key Features

* Detection of fake 320 kbps MP3 files
* Detection of fake lossless audio (FLAC, WAV, APE, AIFF, WV)
* Hi-Res / Ultra-Hi-Res PCM analysis (up to 384 kHz and beyond) and native DSD support (.dsf, .dff), with DSD-to-PCM noise-shaping recognition to avoid false positives on genuine SACD/DSD-derived content
* Spectral cutoff and compression artifact detection
* Multi-segment frequency analysis
* Joint stereo anomaly detection
* Selectable lossless verification engines: LAC 2.0.5 + FLAD, AudioAuditorCLI + FLAD, or FlacCompagnonCLI + FLAD
* Statistical validation using LAC (Lossless Audio Checker), FLAD, AudioAuditorCLI, and FlacCompagnonCLI for lossless PCM verification
* Automatic dependency management (FFmpeg, FFprobe, FLAD, and AudioAuditorCLI when selected)
* High-performance spectrogram processing
* Detailed reporting: LOG - CSV  
On selection window, click to cycle: [CSV ( )] → [CSV (,)] → [CSV (;)] → [CSV ( )]
* Moves detected files to the ~Fake folder while preserving the original directory structure

---

## 🧠 Detection Technology

Audio Fake Detector PRO uses a hybrid analysis engine:

* **Spectral Analysis**: detects frequency cutoffs, compression artifacts, and artificial bandwidth extension
* **Statistical Validation**: verifies lossless authenticity using the selected lossless engine. LAC + FLAD, AudioAuditorCLI + FLAD, and FlacCompagnonCLI + FLAD use FLAD as a second-opinion check.
* **Segment-Based Voting System**: improves accuracy by analyzing multiple independent audio segments

This approach reduces false positives and improves detection reliability across different audio formats, including Hi-Res/Ultra-Hi-Res PCM and native DSD, where a dedicated noise-shaping signature check tells a genuine SACD/DSD-derived source apart from an upsampled fake.

---

### 🔎 Lossless

At each startup, a console prompt allows the user to choose the lossless verification mode.  
**LAC + FLAD mode is selected by default**, while **AudioAuditorCLI + FLAD** and **FlacCompagnonCLI + FLAD** can be selected as alternatives.

#### LAC + FLAD mode

Lossless audio is verified using Lossless Audio Checker (LAC 2.0.5) and FLAD (Fake Lossless Audio Detector).  
LAC performs the primary command-line analysis. FLAD is used as a second-opinion check when the LAC vote is not already a conclusive FAKE result.  
If LAC identifies a file as "Fake", no FLAD second-opinion verdict is required to reject the file as genuine lossless.

For slot analysis, FLAC files are temporarily converted to WAV segments (slots) for LAC. LAC and FLAD then analyse the same corresponding temporary WAV segment for each slot.  
For full-track analysis, LAC analyses the temporary full-track WAV converted from the original FLAC, while FLAD analyses the original FLAC file directly.  
Therefore, the temporary FLAC-to-WAV conversion is required only for the LAC analysis path.

Both command-line analyzers run through a unified 3-slot processing pipeline. The LAC/FLAD verification pipeline applies exclusively to lossless PCM audio.  
Native DSD files are not passed to, or analyzed by, either command-line analyzer. This dual-verification approach replaces auCDtect.

A lossless PCM file is considered genuine only when the combined LAC + FLAD result supports the lossless classification. A negative result from either analyzer is sufficient to reject the file as genuine lossless.

Note: This integration specifically uses the LAC 2.0.5 command-line analyzer and should not be confused with LAC 2.0.7, which launches the graphical user interface (GUI). Like LAC 2.0.5, FLAD is also used as a command-line audio analyzer, providing Hi-Res / Ultra-Hi-Res PCM analysis up to 384 kHz and beyond.

#### AudioAuditorCLI + FLAD mode

AudioAuditorCLI can be selected as an alternative primary lossless command-line analyzer, with FLAD used as the second-opinion engine in the same processing model as LAC + FLAD.

AudioAuditorCLI is the Windows x64 command-line client from the AudioAuditor project.

For the 3-slot processing architecture, AudioAuditorCLI and FLAD analyse corresponding native-format slot files. A FLAC source remains FLAC for both analyzers; a WAV source remains WAV. No FLAC-to-WAV conversion is performed for the AudioAuditorCLI + FLAD path.  
For full-track analysis, AudioAuditorCLI and FLAD both analyse the original source file directly, in its original format.

AudioAuditorCLI + FLAD applies exclusively to lossless PCM audio. Native DSD files are not passed to either command-line analyzer and continue to use Audio Fake Detector PRO's native DSD analysis path.

The AudioAuditorCLI executable is not included in the base distribution when absent; when this engine is selected, Audio Fake Detector PRO can download `AudioAuditorCLI-win-x64.exe` automatically from the project's official GitHub release after the user has selected the corresponding mode.

#### FlacCompagnonCLI + FLAD mode

FlacCompagnonCLI is used as the primary lossless verification engine, with FLAD as an independent second-opinion check.  
FlacCompagnonCLI is used exclusively for lossless PCM audio; native DSD files are not passed to, or analyzed by, FlacCompagnonCLI.  
No FLAC-to-WAV conversion is performed in either slot or full-track analysis. For slot analysis, FlacCompagnonCLI and FLAD analyze the same corresponding native-format slot: FLAC remains FLAC and WAV remains WAV. For full-track analysis, both analyzers analyze the original source file directly in its original format.  
FlacCompagnonCLI is a custom command-line frontend based on the open-source FlacCompagnon project.

---

### 🎧 DSD

Audio Fake Detector PRO provides native DSD support (.dsf / .dff) independently of LAC, FLAD, AudioAuditorCLI, and FlacCompagnonCLI. Native DSD files are analyzed by the application's own DSD processing and are not processed through any of the selectable lossless verification pipelines.  
The application also provides SACD/DSD-to-PCM noise-shaping detection, allowing DSD-derived characteristics to be identified when analyzing PCM material. This functionality is part of Audio Fake Detector PRO and is not performed by LAC, FLAD, AudioAuditorCLI, or FlacCompagnonCLI.

---

### 🛡️ Dual-Engine Precision

The combination of a primary lossless analyzer and FLAD provides complementary validation for lossless PCM audio. The three selectable dual-engine modes are:

* **LAC + FLAD**: LAC is the primary command-line analyzer and FLAD provides the independent second check.
* **AudioAuditorCLI + FLAD**: AudioAuditorCLI is the primary command-line analyzer and FLAD provides the independent second check.
* **FlacCompagnonCLI + FLAD**: FlacCompagnonCLI is the primary command-line analyzer and FLAD provides the independent second check.

LAC is useful for detecting sample-rate upscaling (e.g. 44.1 → 48 kHz).  
FLAD helps identify lossy-to-lossless transcodes (e.g. MP3/AAC → WAV/FLAC).  
AudioAuditorCLI provides an additional independent lossless analysis path, returning explicit REAL / FAKE / UNKNOWN classifications.  
Neither LAC, FLAD, AudioAuditorCLI, nor FlacCompagnonCLI is responsible for native DSD analysis; DSD processing is handled independently by Audio Fake Detector PRO since version 8.4.

These complementary analysis paths can expose different types of suspicious lossless material that may be missed by one analyzer alone.

---

### 🎚️ Analysis Segment Control

In the selection window, you can define the duration of each **non-final analysis segment**, from **10 to 160 seconds**. The default value is **40 seconds**. The final end-spot segment used for lossy audio always has a fixed duration of **10 seconds**.  

The number of analysis slots depends on the audio type:

* **Lossless PCM and DSD:** **3 analysis slot**  
* **Lossy:** **5 analysis slots** in total: **4 regular segments plus a final end-spot segment** with a fixed duration of 10 seconds.  

The program automatically determines the position of each segment within the track based on its total duration.

Shorter analysis segments provide faster analysis, while longer segments may provide more representative results for some files.

---

## 📦 Supported Formats

**Lossy:**
MP3, AAC, M4A, OGG, OPUS, WMA

**Lossless:**
FLAC, WAV, APE, AIFF, AIF, WV (up to Ultra-Hi-Res, e.g. 352.8/384 kHz and beyond)

**Native DSD:**
DSF, DFF (DSD64/128/256/512 - decimated to DXD 352.8 kHz/24-bit PCM for analysis; requires ffmpeg.exe/ffprobe.exe, always available with v8.x's bundled or auto-installed FFmpeg)

**Matroska:**
MKV, MKA, MKS, MK3D

---

## 📌 Requirements

- OS: Windows 10/11 (64-bit)  
- .NET 8 Runtime (automated download and silent install provided)  
- PowerShell: 5.1 (pre-installed on Windows 10/11)  
- Network: Internet connection required on first run (for dependencies download)  

---

## 🛠️ Technical Limitations

**High-Bitrate Lossy Re-encoding**

Re-encoding a 192 kbps (or higher) lossy file into a higher-bitrate lossy format (e.g. 320 kbps) can be challenging to detect. Modern lossy encoders at 192 kbps already maintain a very high frequency cutoff, leaving little to no detectable spectral gap for cutoff-based analysis.

---

## 🚀 Download & Dependencies

### 🔗 Automatic Dependencies

If required tools are not found locally, they will be downloaded automatically when Start is clicked in the window selection:

- **FFmpeg** - source: BtbN/FFmpeg-Builds (76.4 MB) / Gyan (104 MB)  
📥 <a href="https://github.com/BtbN/FFmpeg-Builds/releases/download/latest/ffmpeg-n8.1-latest-win64-lgpl-shared-8.1.zip">v8.1.2 LGPL Zip</a> / 📥 <a href="https://www.gyan.dev/ffmpeg/builds/packages/ffmpeg-8.1.2-essentials_build.zip">v8.1.2 Essentials Zip</a> 

- **Lossless Audio Checker (LAC) 2.0.5** - source: <sub><img src="https://images.icon-icons.com/1011/PNG/512/Google_Drive_icon-icons.com_75713.png" width="18" height="18" alt="Google Drive"></sub>
 / V1REU (105 KB)  
📥 <a href="https://bit.ly/4wVDdc6">Google Drive Mirror</a> / <a href="https://www.v1r.eu/files/audio_tools/Lossless_Audio_Checker/[Windows]%20[CLI]%202.0.5/LAC-Windows-64bit.zip">LAC-Windows-64bit.zip</a> 

- **7-Zip Console Executable** - source: 7-Zip (588 KB)  
📥 <a href="https://github.com/ip7z/7zip/releases/download/26.03/7zr.exe">EXE (GitHub)</a>
   
- **FLAD** - source: Sg4Dylan/FLAD (27 MB)  
📥 <a href="https://github.com/Sg4Dylan/FLAD/releases/download/v0.2/FLAD-0.2-x86_64-windows.7z">7-Zip (GitHub)</a>

- **AudioAuditorCLI** - source: Angel2mp3/AudioAuditor (43.5 MB)  
📥 <a href="https://github.com/Angel2mp3/AudioAuditor/releases/download/V2.0.0/AudioAuditorCLI-win-x64.exe">Direct EXE (GitHub)</a>  
Downloaded only when **AudioAuditorCLI + FLAD** is selected and the executable is not already present.

- **.NET 8 Runtime** (27.3 MB, automated download and silent install provided) - source: dotnet.microsoft.com  
📥 <a href="https://builds.dotnet.microsoft.com/dotnet/Runtime/8.0.31/dotnet-runtime-8.0.31-win-x64.exe">Direct EXE Installer</a>  

To avoid automatic download of .NET 8 Runtime from dotnet.microsoft.com, install manually via Command Prompt:
   
```bash

winget install Microsoft.DotNet.Runtime.8

```

---

## 🌐 Preview

Source: <sub><img src="https://images.icon-icons.com/1011/PNG/512/Google_Drive_icon-icons.com_75713.png" width="18" height="18" alt="Google Drive"></sub> Google Drive

* AudioFakeDetector8.7z/zip (x64) (PowerShell 5.1 scripts: Standard + Portable)  
  📄 <a href="https://bit.ly/4hu7ucW">Preview</a> 📥 <a href="https://bit.ly/4fS44iY">7-Zip</a> (34.5 MB) 📥 <a href="https://bit.ly/45oOWU9">Zip</a> (59.9 MB)  
* AudioFakeDetector8_slim.zip (Portable+Standard editions, web downloads)  
  👁️ <a href="https://bit.ly/4fQq38N">Preview</a> 📥 <a href="https://bit.ly/3RGAALQ">Zip</a> (2.20 MB)
  * **Note:**
    * Portable only: delete `AudioFakeDetector_v8.x.ps1` from archive  
    * Standard only: delete `AudioFakeDetector_v8.x_Portable.ps1` from archive

---

### 📁 Files and Folders

Executables, DLL, JSON, state/stamp files  
Standard: `%LOCALAPPDATA%\AudioFakeDetector\` | Portable: `.\Data\App\`

For the 3-slot lossless analysis pipeline (**LAC + FLAD**), each of the 3 parallel slots runs against its own physical copy of `ForceRedirect.exe`, `lac.exe`, `flad_cli.exe`, and FLAD's model folder. Slot 1 uses the copies in the main tool folder; slots 2 and 3 use their own copies, verified and repaired by file size on startup and again before every full-track file:  
Standard: `%LOCALAPPDATA%\AudioFakeDetector\slot2\`, `%LOCALAPPDATA%\AudioFakeDetector\slot3\` | Portable: `.\Data\App\slot2\`, `.\Data\App\slot3\`  
Full-track analysis uses the main tool folder's `lac.exe`; FLAD reuses slot2's `flad_cli.exe` / `ForceRedirect.exe` and model folder instead of requiring a third on-disk FLAD copy, since full-track and the 3-slot pipeline never run at the same time.

For the 3-slot lossless analysis pipeline (**AudioAuditorCLI + FLAD**), each slot uses its own physical copy of `ForceRedirect.exe`, `AudioAuditorCLI-win-x64.exe`, `flad_cli.exe`, and FLAD's model folder. The slot input remains in its original audio format: **AudioAuditorCLI does not require FLAC-to-WAV conversion**. The same slot2/slot3 copy verification and repair described above applies. Full-track analysis uses the main tool folder's `AudioAuditorCLI-win-x64.exe`, while FLAD reuses slot2's FLAD tool copy instead of requiring a third on-disk copy.

For **FlacCompagnonCLI + FLAD** mode, each slot uses its own physical copy of `ForceRedirect.exe`, `FlacCompagnonCLI.exe`, `flad_cli.exe`, and FLAD's model folder in the same slot-tool infrastructure. The slot input remains in its original audio format: **no FLAC-to-WAV conversion is performed**. Full-track analysis uses the original file directly; FLAD reuses slot2's FLAD tool copy instead of requiring a third on-disk FLAD copy.

Temporary analysis files are stored in a **temporary working folder created automatically for each analysis session**. The folder name contains a unique identifier generated for that session; this identifier is only used to keep the temporary files of different sessions separate. The session folder is removed during cleanup when the corresponding analysis work is finished.  
Standard: `%TEMP%\AudioFakeDetector\Session_<unique-ID>\`  
Portable: `.\Data\App\Temp\Session_<unique-ID>\`

In **LAC + FLAD** mode, this session directory may contain spectrogram PNGs, temporary WAV segments/full-track WAV data required by the LAC path, and TXT logs.  
In **AudioAuditorCLI + FLAD** mode, it contains native-format slot data, AudioAuditorCLI/FLAD TXT logs, and analysis intermediates; **no FLAC-to-WAV conversion is required by AudioAuditorCLI**.  
In **FlacCompagnonCLI + FLAD** mode, it contains native-format slot data, FLAD TXT logs, and analysis intermediates; **no FLAC-to-WAV conversion is performed**.

FLAD's own per-slot spectrogram PNGs are stored separately and deleted after each track's FLAD check. They are used only by modes that include FLAD:  
Standard: `%LOCALAPPDATA%\AudioFakeDetector\tmp\`, `...\slot2\tmp\`, `...\slot3\tmp\` | Portable: `.\Data\App\tmp\`, `.\Data\App\slot2\tmp\`, `.\Data\App\slot3\tmp\`

---

## 💬 Support & Community

Have questions, bug reports, or want to discuss features? Join the official thread on Audio Science Review:  
👉 [Audio Science Review - Audio Fake Detector PRO Forum Thread](https://www.audiosciencereview.com/forum/index.php?threads/audio-fake-detector-pro.71538/)

---

## ⚠️ Disclaimer

This tool is independent and not affiliated with any other audio analysis software.  

---

## 🧾 Keywords (SEO)

fake audio detector, fake mp3 detector, audio authenticity checker, fake flac detection, audio analysis tool, spectral analysis audio, lossless verification tool, mp3 upscaling detection, fake DSD detector, DSF DFF authenticity, SACD rip verification, Hi-Res audio verification
