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
👁️ <a href="https://bit.ly/4yWqK8W">FAKE_DSD64_FLAC_880kbps.dsf</a> <sub><img src="https://img.utdstc.com/icon/929/498/929498844d2aa0f6570d10565bd6cd639d2e0765704368f2b51eb87b1b451bcb%3A600" width="18" height="18" alt="MEGA"></sub> MEGA (271 MB)  

---

## ⚙️ Key Features

* Detection of fake 320 kbps MP3 files
* Detection of fake lossless audio (FLAC, WAV, APE, AIFF, WV)
* Hi-Res / Ultra-Hi-Res PCM analysis (up to 384 kHz and beyond) and native DSD support (.dsf, .dff), analyzed on native DSD slots by FlacCompagnonCLI
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

This approach reduces false positives and improves detection reliability across different audio formats, including Hi-Res/Ultra-Hi-Res PCM and native DSD.

---

### 🔎 Lossless

At startup, a selection menu allows the user to choose the lossless verification mode. **LAC + FLAD is selected by default**, while **AudioAuditorCLI + FLAD** and **FlacCompagnonCLI + FLAD** are available as alternatives.

#### LAC + FLAD mode

Lossless audio is verified using Lossless Audio Checker (LAC 2.0.5) and FLAD (Fake Lossless Audio Detector).

LAC performs the primary command-line analysis. FLAD is used as a second-opinion check when the LAC vote is not already a conclusive FAKE result. If LAC identifies a file as "Fake", no FLAD second-opinion verdict is required to reject the file as genuine lossless.

For slot analysis, FLAC files are temporarily converted to WAV segments (slots) for LAC. LAC and FLAD then analyse the same corresponding temporary WAV segment for each slot.

For full-track analysis, LAC (which reads only WAV) analyses the original WAV directly, or a temporary full-track WAV converted from the original FLAC or any other non-WAV lossless format, while FLAD analyses the original file directly.

Therefore, the temporary FLAC-to-WAV conversion is required only for the LAC analysis path.

Both command-line analyzers run through a unified 3-slot processing pipeline. The LAC + FLAD verification pipeline applies exclusively to lossless PCM audio. Native DSD files are not passed to or analysed by either command-line analyzer. This dual-verification approach replaces auCDtect.

A lossless PCM file is considered genuine only when the combined LAC + FLAD result supports the lossless classification. A negative result from either analyzer is sufficient to reject the file as genuine lossless.

**Note:** This integration specifically uses the LAC 2.0.5 command-line analyzer and should not be confused with LAC 2.0.7, which launches the graphical user interface (GUI). Like LAC 2.0.5, FLAD is also used as a command-line audio analyzer, providing Hi-Res / Ultra-Hi-Res PCM analysis up to 384 kHz and beyond.

#### AudioAuditorCLI + FLAD mode

AudioAuditorCLI V2.0.0 is the Windows x64 command-line client from the AudioAuditor project. It can be selected as an alternative primary lossless command-line analyzer, with FLAD used as the second-opinion engine in the same processing model as LAC + FLAD.

For the 3-slot processing architecture, AudioAuditorCLI and FLAD analyse corresponding native-format slot files. A FLAC source remains FLAC for both analyzers; a WAV source remains WAV. No FLAC-to-WAV conversion is performed for the AudioAuditorCLI + FLAD path.

For full-track analysis, AudioAuditorCLI and FLAD both analyse the original source file directly, in its original format.

AudioAuditorCLI + FLAD applies exclusively to lossless PCM audio. Native DSD files are not passed to either command-line analyzer; they are analysed by FlacCompagnonCLI instead (see the DSD section).

For distribution and automatic download details, see **Automatic Dependencies**.

#### FlacCompagnonCLI + FLAD mode

FlacCompagnonCLI is used as the primary lossless verification engine, with FLAD as an independent second-opinion check.

For lossless PCM audio, FlacCompagnonCLI is paired with FLAD. Native DSD files are analysed by FlacCompagnonCLI alone, in every engine mode (see the DSD section).

No FLAC-to-WAV conversion is performed in either slot or full-track analysis. For slot analysis, FlacCompagnonCLI and FLAD analyse the same corresponding native-format slot: FLAC remains FLAC and WAV remains WAV. For full-track analysis, both analyzers analyse the original source file directly in its original format.

FlacCompagnonCLI is a custom command-line frontend based on the open-source FlacCompagnon project.

---

### 🎧 DSD

Native DSD files (.dsf / .dff) are analyzed by FlacCompagnonCLI, in every engine mode (LAC + FLAD, AudioAuditorCLI + FLAD and FlacCompagnonCLI + FLAD). LAC, FLAD and AudioAuditorCLI are not used for DSD.  
The 3 analysis slots are native DSD files in the same container as the source: a DSF slot is a DSF file and a DFF slot is a DFF file. The DSD bitstream is copied as-is from the original file; FFmpeg is not involved and nothing is decoded or resampled.  
The 3 slots are analyzed in parallel, each by its own `ForceRedirect.exe` + `FlacCompagnonCLI.exe` pair, with FlacCompagnonCLI, and every process it spawns (such as ffmpeg), running at BelowNormal priority. The final verdict is the vote of the 3 slot results, using the same table as lossless audio; if no slot returns a usable verdict, the file is reported as UNKNOWN.  
The container is checked a priori: for a DST-compressed DFF, native slots are not possible, so its 3 slots are extracted as WAV by FFmpeg (float32, decoder PCM rate, no extra resampling) and analyzed by FlacCompagnonCLI. DSF and uncompressed DFF always use native DSD slots.  
`FlacCompagnonCLI.exe` must be present for DSD analysis in every engine mode.

---

### 🛡️ Dual-Engine Precision

The combination of a primary lossless analyzer and FLAD provides complementary validation for lossless PCM audio. The three selectable dual-engine modes are:

* **LAC + FLAD**: LAC is the primary command-line analyzer and FLAD provides the independent second check.
* **AudioAuditorCLI + FLAD**: AudioAuditorCLI is the primary command-line analyzer and FLAD provides the independent second check.
* **FlacCompagnonCLI + FLAD**: FlacCompagnonCLI is the primary command-line analyzer and FLAD provides the independent second check.

LAC is useful for detecting sample-rate upscaling (e.g. 44.1 → 48 kHz).  
FLAD helps identify lossy-to-lossless transcodes (e.g. MP3/AAC → WAV/FLAC).  
AudioAuditorCLI provides an additional independent lossless analysis path, returning explicit REAL / FAKE / UNKNOWN classifications.  
LAC, FLAD and AudioAuditorCLI are not used for native DSD analysis, which is handled by FlacCompagnonCLI alone (see the DSD section).

These complementary analysis paths can expose different types of suspicious lossless material that may be missed by one analyzer alone.

---

### 🎯 Full Lossless Analysis

The **Full lossless** toggle in the selection window analyzes the entire file instead of 3 slots, for every lossless format and for native DSD.  
Lossless files are analyzed in their original format whenever the selected engine reads it natively. A temporary full-length WAV is made only when it does not, and the engine and FLAD then analyze that same WAV:  
* **AudioAuditorCLI** reads FLAC, WAV, AIFF/AIF, APE, WV, ALAC, TTA, TAK and AU/SND natively.  
* **FlacCompagnonCLI** reads FLAC, WAV, AIFF/AIF, ALAC and CAF natively; APE, WV, TTA, TAK and AU/SND are converted.  
* **LAC** reads only WAV: a FLAC, and any other non-WAV source, is converted.  
For formats other than FLAC and WAV, CLEAN is reported only when both the engine and FLAD return a verdict: if one of them cannot analyze the file, or a needed conversion fails, the result is UNKNOWN. A FAKE or SUSPECT from either stands.  
In the per-slot analysis the second engine is always FLAD, whose supported input formats are not documented: slots stay in their native format only for FLAC and WAV, and every other format is cut as WAV.  
Native DSD is always analyzed by FlacCompagnonCLI alone, whatever engine combination is selected, directly on the original file. Only a DST-compressed DFF is first decoded to a temporary full-length WAV by FFmpeg.  
Full-track results are written to the main CSV only.

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
MP3, MP2, AAC, M4A, M4B, M4R, MP4, 3GP, 3G2, OGG, OPUS, WMA, Musepack (MPC, MP+), AC3, WEBM

**Lossless:**
FLAC, WAV, AIFF, AIF, APE, WV, ALAC, TTA, TAK, CAF, AU, SND (up to Ultra-Hi-Res, e.g. 352.8/384 kHz and beyond)  
ALAC is recognized by its codec inside M4A/MP4 files and analyzed as lossless.

**Native DSD:**
DSF, DFF (DSD64/128/256/512 - analyzed on native DSD slots by FlacCompagnonCLI; ffprobe.exe is used to read duration and metadata)

**Matroska:**
MKV, MKA, MKS, MK3D

---

## 📌 Requirements

- OS: Windows 10/11 (64-bit)  
- .NET 8 Runtime (automated download and silent install provided)  
- PowerShell: 5.1 (pre-installed on Windows 10/11)  
- Network: Internet connection required on first run (for dependencies download)  
- FlacCompagnonCLI.exe: required for native DSD analysis in every engine mode, and as the primary engine in FlacCompagnonCLI + FLAD mode  

---

## 🛠️ Technical Limitations

**High-Bitrate Lossy Re-encoding**

Re-encoding a 192 kbps (or higher) lossy file into a higher-bitrate lossy format (e.g. 320 kbps) can be challenging to detect. Modern lossy encoders at 192 kbps already maintain a very high frequency cutoff, leaving little to no detectable spectral gap for cutoff-based analysis.

---

## 🚀 Download & Dependencies

### 🔗 Automatic Dependencies

When **Start** is clicked in the PowerShell script-selection window, Audio Fake Detector PRO checks whether the required tools are available locally. Missing dependencies are downloaded automatically when a download source is configured for them.

**Already included in the distribution archive AudioFakeDetector8.7z/zip:**
- FFmpeg
- Lossless Audio Checker (LAC) 2.0.5
- 7-Zip Console Executable (`7zr.exe`)
- FlacCompagnonCLI

The following links provide download sources for the corresponding tools if they need to be obtained separately.

- **FFmpeg** - source: BtbN/FFmpeg-Builds (77 MB) / Gyan (104 MB)  
  📥 [v8.1.2 LGPL Zip](https://github.com/BtbN/FFmpeg-Builds/releases/download/latest/ffmpeg-n8.1-latest-win64-lgpl-shared-8.1.zip) / 📥 [v8.1.2 Essentials Zip](https://www.gyan.dev/ffmpeg/builds/packages/ffmpeg-8.1.2-essentials_build.zip)

- **Lossless Audio Checker (LAC) 2.0.5** - source:  <sub><img src="https://images.icon-icons.com/1011/PNG/512/Google_Drive_icon-icons.com_75713.png" width="18" height="18" alt="Google Drive"></sub> Google Drive / V1REU (105 KB)  
  📥 [Google Drive Mirror](https://bit.ly/4wVDdc6) / [LAC-Windows-64bit.zip](https://www.v1r.eu/files/audio_tools/Lossless_Audio_Checker/%5BWindows%5D%20%5BCLI%5D%202.0.5/LAC-Windows-64bit.zip)

- **7-Zip Console Executable** - source: 7-Zip (588 KB)  
  📥 [EXE (GitHub)](https://github.com/ip7z/7zip/releases/download/26.04/7zr.exe)

**Not included in the distribution archive:**

- **FLAD** - source: Sg4Dylan/FLAD (27 MB). Downloaded automatically when required by the selected engine and not already present locally.  
  📥 [7-Zip (GitHub)](https://github.com/Sg4Dylan/FLAD/releases/download/v0.2/FLAD-0.2-x86_64-windows.7z)

- **AudioAuditorCLI V2.0.0** - source: Angel2mp3/AudioAuditor (43.5 MB). Downloaded only when **AudioAuditorCLI + FLAD** is selected, **Start** is clicked, and the executable is not already present locally. The downloaded executable is retained locally for subsequent use.  
  📥 [Direct EXE (Official GitHub Release)](https://github.com/Angel2mp3/AudioAuditor/releases/download/V2.0.0/AudioAuditorCLI-win-x64.exe)

- **.NET 8 Runtime** (27.3 MB) - source: dotnet.microsoft.com. Automatic download and silent installation are provided when required.  
  📥 [Direct EXE Installer](https://builds.dotnet.microsoft.com/dotnet/Runtime/8.0.32/dotnet-runtime-8.0.32-win-x64.exe)

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

Standard: `%LOCALAPPDATA%\AudioFakeDetector\`  
Portable: `.\Data\App\`

For the 3-slot lossless analysis pipeline (LAC + FLAD), each of the 3 parallel slots runs its own instance of `flad_cli.exe` against a physical per-slot copy of `ForceRedirect.exe`, `flad_cli.exe`, and FLAD's model folder. `lac.exe` itself is not duplicated per slot; all 3 slots share the single copy in the main tool folder. Slot 1 uses the main tool folder's FLAD copy directly; slots 2 and 3 use their own FLAD-related copies, verified and repaired by file size on startup and again before every full-track file:

Standard: `%LOCALAPPDATA%\AudioFakeDetector\slot2\`, `%LOCALAPPDATA%\AudioFakeDetector\slot3\`  
Portable: `.\Data\App\slot2\`, `.\Data\App\slot3\`

Full-track analysis uses the main tool folder's `lac.exe`; FLAD reuses slot2's `flad_cli.exe` / `ForceRedirect.exe` and model folder instead of requiring a third on-disk FLAD copy, since full-track and the 3-slot pipeline never run at the same time.

For the 3-slot lossless analysis pipeline (AudioAuditorCLI + FLAD), each slot uses its own physical copy of `ForceRedirect.exe`, `flad_cli.exe`, and FLAD's model folder. `AudioAuditorCLI-win-x64.exe` itself is not duplicated per slot; all 3 slots share the single copy in the main tool folder. The slot input remains in its original audio format: AudioAuditorCLI does not require FLAC-to-WAV conversion. The same slot2/slot3 copy verification and repair described above applies. Full-track analysis uses the main tool folder's `AudioAuditorCLI-win-x64.exe`, while FLAD reuses slot2's FLAD tool copy instead of requiring a third on-disk copy.

For FlacCompagnonCLI + FLAD mode, each slot uses its own physical copy of `ForceRedirect.exe`, `flad_cli.exe`, and FLAD's model folder in the same slot-tool infrastructure. `FlacCompagnonCLI.exe` itself is not duplicated per slot; all 3 slots share the single copy in the main tool folder. The slot input remains in its original audio format: no FLAC-to-WAV conversion is performed. Full-track analysis uses the original file directly; FLAD reuses slot2's FLAD tool copy instead of requiring a third on-disk FLAD copy.

Native DSD analysis (all engine modes) uses the same per-slot `ForceRedirect.exe` copies as above; `FlacCompagnonCLI.exe` is shared from the main tool folder. FLAD is not used for DSD.

Temporary analysis files are stored in a temporary working folder created automatically for each analysis session. The folder name contains a unique identifier generated for that session; this identifier is only used to keep the temporary files of different sessions separate. The session folder is removed during cleanup when the corresponding analysis work is finished. Any session folder that holds no audio file, only the TXT output of the analysis workers, for example one left by a window closed during an analysis, is removed at the next startup and at the end of every run; while another instance of the program is running, only folders whose own session lock is inactive are removed. The Temp root folder is removed with them when nothing else is left in it:

Standard: `%TEMP%\AudioFakeDetector\Session_<unique-ID>\`  
Portable: `.\Data\App\Temp\Session_<unique-ID>\`

In LAC + FLAD mode, this session directory may contain spectrogram PNGs, temporary WAV segments/full-track WAV data required by the LAC path, and TXT logs.
In AudioAuditorCLI + FLAD mode, it contains native-format slot data, AudioAuditorCLI/FLAD TXT logs, and analysis intermediates; no FLAC-to-WAV conversion is required by AudioAuditorCLI.
In FlacCompagnonCLI + FLAD mode, it contains native-format slot data, FLAD TXT logs, and analysis intermediates; no FLAC-to-WAV conversion is performed.
For native DSD files (all engine modes), it contains the 3 temporary native DSD slot files and the FlacCompagnonCLI TXT logs; the slot files are deleted when the track's analysis ends.

FLAD's own per-slot spectrogram PNGs are stored separately and deleted after each track's FLAD check. They are used only by modes that include FLAD:

Standard: `%LOCALAPPDATA%\AudioFakeDetector\tmp\`, `...\slot2\tmp\`, `...\slot3\tmp\`  
Portable: `.\Data\App\tmp\`, `.\Data\App\slot2\tmp\`, `.\Data\App\slot3\tmp\`

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
