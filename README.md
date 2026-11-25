SIGNAL // · build to .exe
=========================

WHAT YOU NEED ONCE
 1. Python 3.10+ 64-bit (when installing, check the box “Add python.exe to PATH”)
 2. VLC 64-bit: winget install VideoLAN.VLC
 (VLC is only needed during the build process — it is included entirely inside the .exe)

assembling
 Double-click on build_exe.bat
 Result: dist\SIGNAL\SIGNAL.exe
 dist\SIGNAL-portable.zip

launch
 Copy the SIGNAL folder ENTIRELY (VLC is located inside _internal).
You cannot create a single .exe file: libvlc requires the plugins folder on the disk.

WHERE ARE THE DATA?
 %LOCALAPPDATA%\SignalDeck\.yandex_token — Yandex token
 %LOCALAPPDATA%\SignalDeck\signal_error.log — log if something went wrong
 %TEMP%\signal_demo_*wav — demo track cache
 Interface settings — in the registry (QSettings: SignalDeck / Signal).

IF IT DOESN’T COMPILE
 "VLC not found" -> install VLC 64-bit or:
 set VLC_DIR=C:\Program Files\VideoLAN\VLC
 "Python 32-bit" -> reinstall Python 6

Full VLC: ~250-350 MB
 Trimmed: set SIGNAL_TRIM_VLC=1 before build_exe.bat (~60-90 MB)
Trimming is left disabled: the full set is more reliable.

ANTIVIRUS
 PyInstaller builds sometimes trigger false positives. UPX is intentionally disabled.
 If Defender complains, add the dist\SIGNAL folder to the exclusions.

WITHOUT CONSOLE
 The console window is disabled. Any error is written to signal_error.log and displayed in a dialog — “silent failure” will no longer occur.
