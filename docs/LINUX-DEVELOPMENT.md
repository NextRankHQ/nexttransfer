# NextTransfer — Linux Developer Guide (CachyOS / Arch / Ubuntu / Fedora)

This guide explains how to set up, run, test, and package **NextTransfer** on Linux, with first-class instructions for **CachyOS Linux** (Arch-based).

---

## 1. System Prerequisites

### CachyOS / Arch Linux

Install the C/C++ build toolchain, Rustup, Node.js, WebKitGTK 4.1, and packaging utilities:

```bash
sudo pacman -S --needed base-devel cmake clang pkgconf openssl \
  rustup nodejs npm \
  webkit2gtk-4.1 gtk3 libayatana-appindicator librsvg \
  fuse3 acl patchelf squashfs-tools imagemagick libicns \
  gstreamer gst-plugins-base gst-plugins-good gst-plugins-bad
```

### Ubuntu 22.04 / 24.04 & Debian

```bash
sudo apt-get update
sudo apt-get install -y build-essential cmake clang pkg-config libssl-dev \
  libwebkit2gtk-4.1-dev libgtk-3-dev libayatana-appindicator3-dev librsvg2-dev \
  libfuse3-dev libacl1-dev patchelf squashfs-tools rpm imagemagick icnsutils
```

### Fedora

```bash
sudo dnf install -y @development-tools cmake clang openssl-devel \
  webkit2gtk4.1-devel gtk3-devel libayatana-appindicator-gtk3-devel librsvg2-devel \
  fuse3-devel libacl-devel patchelf squashfs-tools rpm-build ImageMagick libicns-utils
```

---

## 2. Rust & Node.js Setup

NextTransfer pins its Rust toolchain in [`rust-toolchain.toml`](../rust-toolchain.toml) (`1.97.1` with `clippy` and `rustfmt`) so local builds match GitHub Actions CI:

```bash
# Install and activate the pinned Rust toolchain
rustup toolchain install 1.97.1 --component clippy rustfmt

# Install exact npm dependencies from package-lock.json
npm ci
```

---

## 3. Running NextTransfer in Development Mode

To start the Vite dev server (`127.0.0.1:5173`) and compile/launch the Tauri desktop window with hot-reload:

```bash
npm run tauri dev
```

### Tip: Faster Rust Compiles Without Local Whisper STT
By default, the Cargo crate compiles `local-stt` (`whisper-rs-sys`, which builds `whisper.cpp` via CMake). During rapid protocol or UI iteration on Linux, you can skip `local-stt` when running `cargo check` or `cargo test`:

```bash
cd src-tauri
cargo check --no-default-features --features aerorsync,proton-native
```

---

## 4. Running Tests & Quality Gates

Before committing or pushing changes:

```bash
# 1. Verify all 8 version sites and manifests agree on the version (e.g. 1.0.0)
npm run check:version-sites

# 2. TypeScript compiler check
npm run typecheck

# 3. Security regression suite (shell denylist, host-key fail-closed, vault isolation)
npm run security:regression

# 4. Frontend Vitest suite + GUI controller tests
npm run test:unit

# 5. Production frontend bundle build + production boundary verification
npm run build

# 6. Rust backend unit tests (FTP, SFTP, S3, credential vault, DAG transfer engine)
cd src-tauri && cargo test --lib
```

---

## 5. Building Production Linux Packages

To build the release binaries (`aeroftp`, `aeroftp-cli`, `aeroftp-dispatch`) and Linux bundles:

```bash
# Build only the release binary without packaging (fast verification on CachyOS):
npx tauri build --no-bundle

# Build DEB, RPM, or AppImage packages:
npx tauri build --bundles deb,rpm,appimage
```

### Regenerating Application Icons from Master SVG

If you edit [`icons/nexttransfer_icon.svg`](../icons/nexttransfer_icon.svg), regenerate all PNG, Windows `.ico`, and macOS `.icns` assets using:

```bash
for sz in 128 310 512 1024; do
  rsvg-convert -w $sz -h $sz icons/nexttransfer_icon.svg -o icons/AeroFTP_simbol_color_${sz}x${sz}.png
  rsvg-convert -w $sz -h $sz icons/nexttransfer_icon.svg -o icons/NextTransfer_icon_${sz}x${sz}.png
done
rsvg-convert -w 32 -h 32 icons/nexttransfer_icon.svg -o src-tauri/icons/32x32.png
rsvg-convert -w 128 -h 128 icons/nexttransfer_icon.svg -o src-tauri/icons/128x128.png
rsvg-convert -w 256 -h 256 icons/nexttransfer_icon.svg -o src-tauri/icons/128x128@2x.png
rsvg-convert -w 512 -h 512 icons/nexttransfer_icon.svg -o src-tauri/icons/icon.png
magick icons/AeroFTP_simbol_color_1024x1024.png -define icon:auto-resize=256,128,64,48,32,24,16 src-tauri/icons/icon.ico
```

---

## 6. Cross-Platform Builds via GitHub Actions

You do **not** need a Windows or macOS machine for everyday development:

- Pushing to `main`, opening a Pull Request, or triggering **Actions -> Build NextTransfer -> Run workflow** runs:
  - `linux-validate` (`ubuntu-22.04`: version lockstep, `tsc`, `i18n:validate`, `cargo clippy`, `cargo test`).
  - `build-and-release` matrix across:
    - **Linux (`ubuntu-22.04`)**: produces `NextTransfer-Linux-x64-AppImage`, `NextTransfer-Linux-x64-DEB`, `NextTransfer-Linux-x64-RPM`.
    - **Windows (`windows-latest`)**: produces `NextTransfer-Windows-x64` (`.msi`, `-setup.exe`, and portable `.zip`).
    - **macOS (`macos-15`)**: produces `NextTransfer-macOS-AppleSilicon` (`aarch64` `.dmg`) and `NextTransfer-macOS-Intel` (`x86_64` `.dmg`).
- Pushing a version tag (e.g. `git tag v1.0.0 && git push origin v1.0.0`) automatically signs all artifacts with Sigstore Cosign and publishes a GitHub Release.
