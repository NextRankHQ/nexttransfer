<p align="center">
  <img src="icons/nexttransfer_banner.png" alt="NextTransfer — Fast, Secure, Modern File Transfer Client by NextRankHQ" width="100%">
</p>

# NextTransfer

<p align="center">
  <strong>Fast, Modern, Reliable Desktop File Transfer Client for FTP, FTPS, SFTP, and Amazon S3</strong><br>
  Developed and maintained by <a href="https://nextrankhq.com"><strong>NextRankHQ</strong></a>
</p>

<p align="center">
  <a href="https://nextrankhq.com">Website</a> ·
  <a href="https://github.com/NextRankHQ/nexttransfer/releases">Releases & Downloads</a> ·
  <a href="docs/LINUX-DEVELOPMENT.md">Linux Developer Guide</a> ·
  <a href="https://github.com/NextRankHQ/nexttransfer/issues">Report an Issue</a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/version-1.0.0-0284c7" alt="Version 1.0.0" />
  <img src="https://img.shields.io/badge/license-GPL--3.0--or--later-blue" alt="License: GPL-3.0-or-later" />
  <img src="https://img.shields.io/badge/tauri-2.11-24c8db?logo=tauri&logoColor=white" alt="Tauri 2" />
  <img src="https://img.shields.io/badge/rust-1.97-B7410E?logo=rust&logoColor=white" alt="Rust" />
  <img src="https://img.shields.io/badge/react-18-61DAFB?logo=react&logoColor=black" alt="React 18" />
  <img src="https://img.shields.io/badge/Linux-supported-brightgreen?logo=linux&logoColor=black" alt="Linux" />
  <img src="https://img.shields.io/badge/Windows-10%20%2F%2011-0078D4?logo=windows&logoColor=white" alt="Windows" />
  <img src="https://img.shields.io/badge/macOS-Apple%20Silicon%20%26%20Intel-000000?logo=apple&logoColor=white" alt="macOS" />
</p>

---

## Overview

**NextTransfer** is a free, open-source, cross-platform desktop file-transfer application built for developers, freelancers, web designers, hosting customers, and small businesses. Built on a high-performance **Rust (Tauri 2)** backend and a responsive **React 18 + TypeScript** frontend, NextTransfer combines a clean dual-pane workspace with strong security and native multi-protocol support.

### Core Highlights

- **First-Class Protocol Support:**
  - **FTP & Explicit/Implicit FTPS** (`suppaftp` + `rustls` TLS 1.2/1.3, `MLSD`/`MLST` directory listings, passive/active modes, transfer resumption).
  - **SFTP & SCP** (pure-Rust `russh` + `russh-sftp`, password and SSH private key authentication, strict `known_hosts` verification, concurrent read-ahead streaming).
  - **Amazon S3 & S3-Compatible Object Storage** (AWS SigV4 authentication, bucket & prefix navigation, streaming downloads, multipart large-file uploads, presigned URLs).
  - **WebDAV & Cloud Storage Integrations** (Nextcloud, Google Drive, Dropbox, OneDrive, MEGA, Box, pCloud, Backblaze B2, Cloudflare R2, Wasabi, DigitalOcean Spaces, MinIO, and more).
- **Modern Dual-Pane Interface:**
  - Side-by-side Local and Remote file browsers with virtualized file lists, breadcrumbs, quick search, and drag-and-drop transfers.
  - Connection Manager with saved server profiles, protocol presets, and Quick Connect bar.
  - Real-time DAG Transfer Queue with per-file progress, speed indicators, pause/resume/cancel controls, and automatic retry safety.
- **Security by Design:**
  - **Zero Plaintext Credentials:** Passwords, SSH key passphrases, and AWS secret keys are encrypted via **AES-256-GCM** in the Universal Credential Vault (`vault.db`), backed by the OS native keyring (`libsecret` / KWallet on Linux, Credential Manager on Windows, Keychain on macOS) or an optional **Argon2id** Master Password.
  - **Strict Transport Verification:** Preserves SSH host-key verification and TLS certificate validation.
  - **Zero Telemetry:** NextTransfer never transmits server credentials, S3 secrets, filenames, or analytics to NextRankHQ or any third party.

---

## Supported Protocols & Providers

<!-- BEGIN PROVIDERS-GRID -->

<!-- Generated from PROVIDER_GRID in src/components/providerCatalog.ts by `npm run gen:providers-table`. Do not edit by hand. -->
<table align="center">
  <tr>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/google-drive"><img src="public/icons/providers/grid/Google_Drive.png" width="36" alt="Google Drive" /></a><br><sub>Google Drive</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/onedrive" title="Microsoft OneDrive"><img src="public/icons/providers/grid/onedrive.png" width="36" alt="OneDrive" /></a><br><sub>OneDrive</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/dropbox"><img src="public/icons/providers/grid/dropbox.png" width="36" alt="Dropbox" /></a><br><sub>Dropbox</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/mega"><img src="public/icons/providers/grid/mega.png" width="36" alt="MEGA" /></a><br><sub>MEGA</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/box"><img src="public/icons/providers/grid/box.png" width="36" alt="Box" /></a><br><sub>Box</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/pcloud"><img src="public/icons/providers/grid/pcloud.png" width="36" alt="pCloud Drive" /></a><br><sub>pCloud Drive</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/filen"><img src="public/icons/providers/grid/filen.png" width="36" alt="Filen" /></a><br><sub>Filen</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/internxt"><img src="public/icons/providers/grid/internxt.png" width="36" alt="Internxt" /></a><br><sub>Internxt</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/proton-drive"><img src="public/icons/providers/grid/protondrive.png" width="36" alt="Proton Drive" /></a><br><sub>Proton Drive</sub></td>
  </tr>
  <tr>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/zoho"><img src="public/icons/providers/grid/ZohoWorkDrive.png" width="36" alt="Zoho WorkDrive" /></a><br><sub>Zoho WorkDrive</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/koofr"><img src="public/icons/providers/grid/Koofr.png" width="36" alt="Koofr" /></a><br><sub>Koofr</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/twake"><img src="public/icons/providers/grid/twake.png" width="36" alt="Twake Drive" /></a><br><sub>Twake Drive</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/kdrive"><img src="public/icons/providers/grid/kdrive.png" width="36" alt="kDrive" /></a><br><sub>kDrive</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/jottacloud"><img src="public/icons/providers/grid/jottacloud.png" width="36" alt="Jottacloud" /></a><br><sub>Jottacloud</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/drime"><img src="public/icons/providers/grid/drime.png" width="36" alt="Drime" /></a><br><sub>Drime</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/filelu"><img src="public/icons/providers/grid/filelu.png" width="36" alt="FileLu" /></a><br><sub>FileLu</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/opendrive"><img src="public/icons/providers/grid/opendrive.png" width="36" alt="OpenDrive" /></a><br><sub>OpenDrive</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/yandex"><img src="public/icons/providers/grid/YandexDisk.png" width="36" alt="Yandex Disk" /></a><br><sub>Yandex Disk</sub></td>
  </tr>
  <tr>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/4shared"><img src="public/icons/providers/grid/4shared.png" width="36" alt="4shared" /></a><br><sub>4shared</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/backblaze-b2"><img src="public/icons/providers/grid/backblaze.png" width="36" alt="Backblaze B2" /></a><br><sub>Backblaze B2</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/blomp"><img src="public/icons/providers/grid/blomp.png" width="36" alt="Blomp" /></a><br><sub>Blomp</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/aws-s3" title="Amazon Web Services (AWS)"><img src="public/icons/providers/grid/Amazon_Web_Services.png" width="36" alt="AWS S3" /></a><br><sub>AWS S3</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/google-cloud-storage"><img src="public/icons/providers/grid/googlecloud.png" width="36" alt="Google Cloud Storage" /></a><br><sub>Google Cloud Storage</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/protocols/azure" title="Microsoft Azure Blob"><img src="public/icons/providers/grid/azure.png" width="36" alt="Azure Blob" /></a><br><sub>Azure Blob</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/wasabi"><img src="public/icons/providers/grid/wasabi.png" width="36" alt="Wasabi" /></a><br><sub>Wasabi</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/cloudflare-r2"><img src="public/icons/providers/grid/cloudfare.png" width="36" alt="Cloudflare R2" /></a><br><sub>Cloudflare R2</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/digitalocean-spaces"><img src="public/icons/providers/grid/digitalocean.png" width="36" alt="DigitalOcean Spaces" /></a><br><sub>DigitalOcean Spaces</sub></td>
  </tr>
  <tr>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/tencent-cloud-cos"><img src="public/icons/providers/grid/tencent.png" width="36" alt="Tencent COS" /></a><br><sub>Tencent COS</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/alibaba-cloud-oss"><img src="public/icons/providers/grid/alibabacloud.png" width="36" alt="Alibaba OSS" /></a><br><sub>Alibaba OSS</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/oracle-cloud"><img src="public/icons/providers/grid/oracle_cloud.png" width="36" alt="Oracle Cloud" /></a><br><sub>Oracle Cloud</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/storj"><img src="public/icons/providers/grid/storj.png" width="36" alt="Storj" /></a><br><sub>Storj</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/idrive-e2"><img src="public/icons/providers/grid/idrive_e2.png" width="36" alt="IDrive e2" /></a><br><sub>IDrive e2</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/filebase"><img src="public/icons/providers/grid/filebase.png" width="36" alt="Filebase" /></a><br><sub>Filebase</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/tigris"><img src="public/icons/providers/grid/tigris.png" width="36" alt="Tigris Data" /></a><br><sub>Tigris Data</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/fastly-object-storage"><img src="public/icons/providers/grid/fastly.png" width="36" alt="Fastly" /></a><br><sub>Fastly</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/minio"><img src="public/icons/providers/grid/minio.png" width="36" alt="MinIO" /></a><br><sub>MinIO</sub></td>
  </tr>
  <tr>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/yandex-object-storage"><img src="public/icons/providers/grid/yandexcloud.png" width="36" alt="Yandex Object Storage" /></a><br><sub>Yandex Object Storage</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/s3drive"><img src="public/icons/providers/grid/s3drive.png" width="36" alt="S3Drive" /></a><br><sub>S3Drive</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/quotaless"><img src="public/icons/providers/grid/quotaless.png" width="36" alt="Quotaless" /></a><br><sub>Quotaless</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/ibm-cloud-object-storage" title="IBM Cloud Object Storage"><img src="public/icons/providers/grid/ibm-cloud.png" width="36" alt="IBM COS" /></a><br><sub>IBM COS</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/nextcloud"><img src="public/icons/providers/grid/nextcloud.png" width="36" alt="Nextcloud" /></a><br><sub>Nextcloud</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/felicloud"><img src="public/icons/providers/grid/felicloud.png" width="36" alt="Felicloud" /></a><br><sub>Felicloud</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/tabdigital"><img src="public/icons/providers/grid/tabdigital.png" width="36" alt="TAB.DIGITAL" /></a><br><sub>TAB.DIGITAL</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/cloudme"><img src="public/icons/providers/grid/cloudme.png" width="36" alt="CloudMe" /></a><br><sub>CloudMe</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/infinicloud"><img src="public/icons/providers/grid/infiniCloud.png" width="36" alt="InfiniCloud" /></a><br><sub>InfiniCloud</sub></td>
  </tr>
  <tr>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/jianguoyun"><img src="public/icons/providers/grid/jianguoyun.png" width="36" alt="Jianguoyun" /></a><br><sub>Jianguoyun</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/seafile"><img src="public/icons/providers/grid/seafile.png" width="36" alt="Seafile" /></a><br><sub>Seafile</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/drivehq"><img src="public/icons/providers/grid/drivehq.png" width="36" alt="DriveHQ" /></a><br><sub>DriveHQ</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/mailru-cloud"><img src="public/icons/providers/grid/mailru-cloud.png" width="36" alt="Mail.ru Cloud" /></a><br><sub>Mail.ru Cloud</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/hetzner-storage-box"><img src="public/icons/providers/grid/hetzner.png" width="36" alt="Hetzner Storage Box" /></a><br><sub>Hetzner Storage Box</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/github"><img src="public/icons/providers/grid/github.png" width="36" alt="GitHub" /></a><br><sub>GitHub</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/gitlab"><img src="public/icons/providers/grid/gitlab.png" width="36" alt="GitLab" /></a><br><sub>GitLab</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/sourceforge"><img src="public/icons/providers/grid/sourceforge.png" width="36" alt="SourceForge" /></a><br><sub>SourceForge</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/immich"><img src="public/icons/providers/grid/immich.png" width="36" alt="Immich" /></a><br><sub>Immich</sub></td>
  </tr>
  <tr>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/pixelunion"><img src="public/icons/providers/grid/pixelunion.png" width="36" alt="PixelUnion" /></a><br><sub>PixelUnion</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/imagekit"><img src="public/icons/providers/grid/imagekit.png" width="36" alt="ImageKit" /></a><br><sub>ImageKit</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/uploadcare"><img src="public/icons/providers/grid/uploadcare.png" width="36" alt="Uploadcare" /></a><br><sub>Uploadcare</sub></td>
    <td align="center" width="80"><a href="https://docs.aeroftp.app/providers/cloudinary"><img src="public/icons/providers/grid/cloudinary.png" width="36" alt="Cloudinary" /></a><br><sub>Cloudinary</sub></td>
  </tr>
</table>

<!-- END PROVIDERS-GRID -->

| Protocol | Authentication | Key Capabilities |
|----------|----------------|------------------|
| **FTP** | Username / Password, Anonymous | Passive/Active modes, `MLSD`/`MLST` listings, `REST`/`APPE` resume, directory & file management |
| **FTPS** | Explicit TLS (`AUTH TLS`), Implicit TLS | TLS 1.2 / 1.3 via `rustls`, configurable certificate verification, encrypted control & data channels |
| **SFTP / SCP** | Password, SSH Private Key (`.pem`/Ed25519/RSA), SSH Agent | Interactive `known_hosts` verification, multi-stream parallel range downloads, automatic SCP fallback |
| **Amazon S3** | Access Key ID + Secret Access Key, STS Session Token | Bucket browsing, prefix navigation, multipart uploads for large objects, custom endpoints (MinIO, R2, Wasabi, B2) |

---

## Platform Support & Release Artifacts

| Operating System | Architectures | Release Artifacts | Status |
|------------------|---------------|-------------------|--------|
| **Linux** | `x86_64` | `NextTransfer-Linux-x64-AppImage` (`.AppImage`)<br>`NextTransfer-Linux-x64-DEB` (`.deb`)<br>`NextTransfer-Linux-x64-RPM` (`.rpm`) | Verified on CachyOS / Arch Linux & Ubuntu |
| **Windows 10 / 11** | `x86_64` | `NextTransfer-Windows-x64` (`.msi`, `-setup.exe`, portable `.zip`) | Automated CI Build via GitHub Actions |
| **macOS** | Apple Silicon (`aarch64`)<br>Intel (`x86_64`) | `NextTransfer-macOS-AppleSilicon` (`.dmg`)<br>`NextTransfer-macOS-Intel` (`.dmg`) | Automated CI Build via GitHub Actions |

### Code Signing & Notarization Notes

- **Windows:** Release builds generated without a commercial Authenticode EV/OV certificate will display a Windows SmartScreen prompt on first launch (*More info -> Run anyway*). To sign releases in production, configure `TAURI_SIGNING_PRIVATE_KEY` and Windows certificate secrets in GitHub Actions.
- **macOS:** Unsigned `.dmg` bundles are blocked by macOS Gatekeeper by default. After dragging `NextTransfer.app` to `/Applications`, clear the quarantine attribute before first launch:
  ```bash
  sudo xattr -rd com.apple.quarantine /Applications/NextTransfer.app
  ```
  Apple Developer ID signing and notarization (`APPLE_CERTIFICATE`, `APPLE_ID`, `APPLE_PASSWORD`, `APPLE_TEAM_ID`) can be enabled as a separate release step once an Apple Developer account is configured.

---

## Screenshots

> _Screenshots of the NextTransfer dual-pane workspace, Connection Manager, and Transfer Queue:_

| Dual-Pane File Browser | Connection Manager & Saved Profiles | Transfer Queue & Progress |
|------------------------|-------------------------------------|---------------------------|
| ![File Manager](screenshots/multi-tab-file-manager.png) | ![Connection Screen](screenshots/connection-screen-protocols.png) | ![Transfer Queue](screenshots/sync-transfer-queue.png) |

---

## Installation

### Linux

#### AppImage (Universal — CachyOS, Arch, Ubuntu, Fedora, Debian)
```bash
chmod +x NextTransfer_*.AppImage
./NextTransfer_*.AppImage
```

#### Debian / Ubuntu (`.deb`)
```bash
sudo apt install ./NextTransfer_*_amd64.deb
```

#### Fedora / RHEL / openSUSE (`.rpm`)
```bash
sudo dnf install ./NextTransfer-*.x86_64.rpm
```

### Windows 10 & Windows 11
- **Installer:** Run `NextTransfer_1.0.0_x64-setup.exe` (NSIS) or `NextTransfer_1.0.0_x64_en-US.msi` (MSI).
- **Portable:** Extract `NextTransfer-1.0.0-portable-windows-x64.zip` to any folder and launch `NextTransfer.exe`.

### macOS (Apple Silicon & Intel)
- Open `NextTransfer_1.0.0_aarch64.dmg` (Apple Silicon M1/M2/M3/M4) or `NextTransfer_1.0.0_x64.dmg` (Intel) and drag **NextTransfer** into `/Applications`.

---

## Development Setup & Building from Source

Linux (specifically **CachyOS / Arch Linux**) is the primary development platform for NextTransfer. For detailed Linux instructions, troubleshooting, and packaging details, see the [**Linux Developer Guide (`docs/LINUX-DEVELOPMENT.md`)**](docs/LINUX-DEVELOPMENT.md).

### 1. Prerequisites (CachyOS / Arch Linux)

```bash
sudo pacman -S --needed base-devel cmake clang pkgconf openssl \
  rustup nodejs npm \
  webkit2gtk-4.1 gtk3 libayatana-appindicator librsvg \
  fuse3 acl patchelf squashfs-tools imagemagick libicns \
  gstreamer gst-plugins-base gst-plugins-good gst-plugins-bad

rustup toolchain install 1.97.1 --component clippy rustfmt
```

### 2. Clone & Install Dependencies

```bash
git clone https://github.com/NextRankHQ/nexttransfer.git
cd nexttransfer
npm ci
```

### 3. Run in Development Mode

```bash
npm run tauri dev
```

### 4. Run Quality Checks & Tests

```bash
# Verify version lockstep across all manifests
npm run check:version-sites

# TypeScript typecheck, security regression suite, and frontend unit tests
npm run typecheck
npm run security:regression
npm run test:unit

# Rust backend test suite
cd src-tauri && cargo test
```

### 5. Build Production Packages

```bash
# Build frontend + Rust release binary + platform installers
npm run tauri build
```

---

## Cloud & Object Storage Provider Matrix

<!-- BEGIN PROVIDERS-TABLE -->

<!-- Generated from src/components/providerCatalog.ts by `npm run gen:providers-table`. Do not edit by hand. -->

| Provider | HQ | Free tier | Connection methods |
| --- | --- | --- | --- |
| 4shared | VG | 15 GB | OAuth, WebDAV |
| Alibaba OSS | CN | new-user trial, overseas | S3* |
| Amazon Web Services (AWS) | US | 12-month trial | S3* |
| Backblaze B2 | US | 10 GB | API, S3 |
| Blomp | US | 40 GB (+40 GB per referral) | Swift |
| Box | US | 10 GB | OAuth |
| Cloudflare R2 | US | 10 GB (egress-free, card req.) | S3* |
| Cloudinary | US | credit-based | API |
| CloudMe | SE | 3 GB | WebDAV |
| DigitalOcean Spaces | US | paid plan | S3* |
| Drime | FR | 20 GB | API |
| DriveHQ | US | 5 GB | WebDAV |
| Dropbox | US | 2 GB | OAuth |
| Fastly | US | 5 GB (card req.) | S3* |
| Felicloud | EU | 10 GB (Nextcloud host) | WebDAV |
| Filebase | US | 5 GB | S3 |
| FileLu | US | 1 GB | API, FTP, WebDAV, S5 (S3) |
| Filen | DE | 10 GB (E2E) | API, S3, WebDAV |
| GitHub | US | repo storage | API |
| GitLab | US | repo storage | API |
| Google Cloud Storage | US | 5 GB (always-free, card req.) | S3* |
| Google Drive | US | 15 GB | OAuth |
| Hetzner Storage Box | DE | paid plan | SFTP* |
| IBM Cloud Object Storage | US | 12-month trial | S3* |
| IDrive e2 | US | 7-day trial | S3* |
| ImageKit | IN | 20 GB (media CDN) | API |
| Immich | - | self-hosted | API |
| InfiniCloud | JP | 25 GB | WebDAV |
| Internxt | ES | 1 GB (E2E) | API |
| Jianguoyun | CN | 3 GB (monthly traffic cap) | WebDAV |
| Jottacloud | NO | 5 GB | API |
| kDrive | CH | 15 GB | API |
| Koofr | SI | 10 GB | API, WebDAV |
| Mail.ru Cloud | RU | 8 GB (app password required) | WebDAV |
| MEGA | NZ | 20 GB (E2E) | API, MEGAcmd, S4 (S3)* |
| Microsoft Azure Blob | US | 12-month trial | Blob* |
| Microsoft OneDrive | US | 5 GB | OAuth |
| MinIO | - | self-hosted | S3 |
| Nextcloud | - | self-hosted | WebDAV |
| OpenDrive | US | 5 GB | API, WebDAV |
| Oracle Cloud | US | 20 GB (always-free, card req.) | S3* |
| pCloud Drive | CH | 10 GB | OAuth, WebDAV* |
| PixelUnion | EU | 16 GB (managed Immich) | API |
| Proton Drive | CH | 5 GB (E2E) | API / CLI |
| Quotaless | - | trial / invite | S3*, WebDAV* |
| S3Drive | - | 12 GB (via Storj) | S3 |
| Seafile | - | self-hosted | WebDAV |
| SourceForge | US | OSS hosting | SFTP |
| Storj | US | 30-day trial | S3* |
| TAB.DIGITAL | EU | 8 GB (managed Nextcloud) | WebDAV |
| Tencent COS | CN | 6-month trial | S3* |
| Tigris Data | US | 5 GB | S3 |
| Twake Drive | FR | 5 GB | OAuth |
| Uploadcare | US | 1 GB (media CDN) | API |
| Wasabi | US | 30-day trial | S3* |
| Yandex Disk | RU | 5 GB | OAuth, WebDAV* |
| Yandex Object Storage | RU | 1 GB (always-free, card req.) | S3* |
| Zoho WorkDrive | IN | 5 GB | OAuth |

<sub>58 providers, 72 connection methods. `*` marks a paid / credit-card-gated plan. HQ is the ISO 3166-1 alpha-2 of the company HQ (EU = pan-European). Free-tier sizes are approximate: verify with the provider.</sub>

<!-- END PROVIDERS-TABLE -->

---

## Contributing

Contributions, bug reports, and feature requests are welcome!

1. Fork [NextRankHQ/nexttransfer](https://github.com/NextRankHQ/nexttransfer) and create a feature branch.
2. Run `npm run typecheck`, `npm run test:unit`, and `npm run check:version-sites` before submitting a pull request.
3. Follow the guidelines in [CONTRIBUTING.md](CONTRIBUTING.md) and [SECURITY.md](SECURITY.md).

---

## Licence & Attribution

**NextTransfer** is free and open-source software licensed under the **GNU General Public License v3.0 or later (`GPL-3.0-or-later`)** — see [LICENSE](LICENSE) for the full text.

- **Developed & Maintained by:** [NextRankHQ](https://nextrankhq.com) (<https://github.com/NextRankHQ/nexttransfer>)
- **Upstream Attribution:** NextTransfer is a derivative fork of [AeroFTP](https://github.com/axpdev-lab/aeroftp), originally created by **axpdev (axpnet)** and contributors (`Copyright © 2024-2026 axpdev`). All original copyright notices and GPL-3.0-or-later terms are preserved in accordance with Section 5 of the GNU GPL v3.
- **Third-Party Libraries:** Powered by Tauri (`Apache-2.0 OR MIT`), Tokio (`MIT`), suppaftp (`MIT OR Apache-2.0`), russh (`Apache-2.0`), rustls (`Apache-2.0 OR ISC OR MIT`), reqwest (`MIT OR Apache-2.0`), Argon2 / AES-GCM (`MIT OR Apache-2.0`), and React (`MIT`).
