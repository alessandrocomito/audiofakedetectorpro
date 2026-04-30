Audio Fake Detector PRO v6.1.1
(c) 2026 Alessandro Comito


Short Description
- Detects fake 320 kbps MP3s and fake lossless files made from lower-quality sources using spectral analysis.

Tagline
- Advanced audio authenticity checker for detecting upscaled lossy and lossless files.

Description
- Identifies audio sourced from low-bitrate material (e.g. 128–160 kbps MP3) that has been transcoded or upscaled to higher formats.

It uses a hybrid analysis engine combining spectral analysis and statistical verification:
- Lossy formats (MP3, AAC, M4A, etc.): Analyzed using spectrogram-based detection,
  multi-segment frequency analysis, abrupt high-frequency drop detection near the track
  end, and joint stereo channel anomaly detection.
- Lossless formats (FLAC, WAV, APE, AIFF, AIF, WV): Verified using auCDtect statistical
  analysis.

Each file is split into multiple non-final segments (plus one end segment used as a
secondary indicator only) and evaluated independently. A half-or-strict-majority wall vote
determines the final verdict, eliminating false negatives caused by short clean sections
or mixed content.

Key Features
- Detects lossy-to-lossless and lossy-to-lossy transcodes.
- half-or-strict-majority wall vote (see Detection Logic below for exact threshold rules).
- Spectral cutoff and compression artifact detection.
- Abrupt high-frequency drop detection near the track end.
- Joint stereo channel anomaly detection.
- Automatic dependency management (ffmpeg, ffprobe, auCDtect).
- Resilient metadata recovery via a 3-step fallback analysis.
- Ultra-fast spectrogram processing (optimized GDI+ LockBits implementation).
- Intelligent segment selection to reduce CPU load.
- Generates comprehensive reports in LOG, CSV, and HTML formats.
- Preserves folder structure when moving suspicious files to ~Fake.

Detection Logic (Simplified)
- Audio is split into several segments. The final (end) segment is used only as a
  secondary corroborating indicator and is excluded from the vote.
- Each non-final segment is analyzed for high-frequency cutoff behavior.
- Decision Rule -- Half-or-Strict-Majority Wall Vote:
    The file is flagged as FAKE if half or more (N even) or a strict majority (N odd) of non-final segments show a spectral wall
    at or below 16.5 kHz. In the event of an exact tie between walled and clean segments,
    the verdict defaults to FAKE.
    In practice, with the typical 3-segment analysis this requires at least 2 out of 3
    segments to be walled (>= 66.7%). With an even number of segments, exactly 50% is
    sufficient to trigger FAKE via the tie-break rule.
- Grey Zone: The 16.5-18.5 kHz range is excluded from the half-or-strict-majority wall vote to prevent
  false positives on high-quality 192 kbps encodes. Files whose best segment falls in
  this range are classified as SUSPECT rather than FAKE.
- Lossless Validation: Files are validated using auCDtect confidence scoring. If
  auCDtect returns "Unknown", the tool falls back to spectral analysis.
- Metadata Fallback: If headers are unreadable, a 3-step probe is used:
  1. Format probe
  2. Stream probe
  3. Size-based duration estimation (lossless only).

Supported Formats
- Lossy:    MP3, M4A, AAC, OGG, OPUS, WMA.
- Lossless: FLAC, WAV, APE, AIFF, AIF, WV.

Requirements
- Windows 10/11 (32/64-bit).
- PowerShell 5 or higher.
- Internet connection (required only on first run to download dependencies).

Output
- Suspicious files: Moved to ~Fake folder.
- Reports: Detailed analysis saved in the ~Report folder.
- Original directory structure is always preserved.

Limitations
Less reliable on:
- Speech or voice-only content.
- Very old, degraded, or acoustic recordings with limited bandwidth.
- Close-quality transcodes (e.g., MP3 192 kbps -> AAC 224 kbps).
- High-bitrate AAC (320 kbps) -> FLAC, as modern AAC encodes preserve near full-band
  spectral content without stable artifacts.

Technical Notes
- Built using PS2EXE: High-performance PowerShell executable.
- Session Resume Support: Detects interrupted scans and offers to resume from the last
  processed file.
- Smart Temp Management:
   - Standard version: Temp files stored in %TEMP%\AudioFakeDetector\.
   - Portable version:  Temp files stored in .\Data\App\Temp\ (deleted after each run).
- Reliability: Fully supports Unicode/special characters (e.g., Japanese, symbols) and
  hidden files.
- Optimized for local drives and mounted volumes (Windows 10/11).
- Zero-Footprint (Portable): No admin rights required and no system-wide changes.

Download
- If not found locally, required tools will be downloaded automatically
   - Source: Google Drive -> auCDtect
   - Source: Official developer site -> FFmpeg
- Preview Download: Project site https://alessandrocomito.github.io/audiofakedetectorpro
- Direct Download: Standard (no-install) https://bit.ly/3QAinOY - Portable https://bit.ly/4tDVQiM
- ZIP archives via Google Drive
