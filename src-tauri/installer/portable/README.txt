NextTransfer Portable - Windows
===============================

QUICK START
-----------

1. Extract this ZIP to any folder you can write to (Desktop, USB drive, network
   share, anywhere). NO admin rights required.

2. Double-click NextTransfer.exe to launch.

3. All your data (saved servers, credentials, cache, logs) stays inside the
   NextTransfer folder under "data\". You can move the whole folder to another
   machine and pick up where you left off.


REQUIREMENTS
------------

  - Windows 10 1809+ or Windows 11
  - Microsoft Visual C++ Redistributable for Visual Studio 2015-2022 (x64)
      Download:  https://aka.ms/vs/17/release/vc_redist.x64.exe
  - WebView2 Runtime (preinstalled on Windows 11 and on Windows 10 since
    2021 via Windows Update; install manually if missing)
      Download:  https://developer.microsoft.com/microsoft-edge/webview2/


AUTO-UPDATES
------------

The portable build checks GitHub Releases for updates and replaces the
.exe in place. No installer wizard, no admin prompt. After download +
Sigstore verification NextTransfer swaps the executable, restarts itself, and
cleans up the old version automatically.

You can also trigger an update check manually from Help -> Check for Updates.


UNINSTALL
---------

Delete this folder. There is no registry footprint, no service, no leftover
file outside the folder.


SUPPORT
-------

  - Website & Docs: https://nextrankhq.com/next-transfer
  - Issues:         https://github.com/NextRankHQ/nexttransfer/issues
  - Changelog:      https://github.com/NextRankHQ/nexttransfer/blob/main/CHANGELOG.md


LICENSE
-------

GNU General Public License v3.0. See LICENSE.txt.
