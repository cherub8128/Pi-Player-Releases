# Third-party notices / 제3자 구성요소 고지

Pi Player 데스크톱 앱 자체에는 LICENSE.txt의 무료 사용 독점 라이선스가 적용됩니다. 아래 구성요소는 그 약관으로 재라이선스하지 않으며, 각 원래 라이선스와 법률상 권리가 우선합니다. 앱의 **설정 → 정보 → 이용약관과 오픈소스 고지**에서 이 문서를 오프라인으로 읽을 수 있습니다.

## Shipped application libraries

The renderer is bundled by Vite into `dist/`; these are the only libraries it contains.

| Component | Version | License | Complete notice |
| --- | --- | --- | --- |
| React | 19.3.0 | MIT | licenses/React-MIT.txt |
| React DOM | 19.3.0 | MIT | licenses/React-DOM-MIT.txt |
| Scheduler | 0.28.0 | MIT | licenses/Scheduler-MIT.txt |
| Lucide React icons | 1.48.0 | ISC (portions derived from Feather, MIT; retained in the notice) | licenses/Lucide-ISC.txt |
| node-qrcode (QR code for Wi-Fi sharing) | 1.5.4 | MIT | licenses/qrcode-MIT.txt |
| dijkstrajs (used by node-qrcode) | 1.0.3 | MIT | licenses/dijkstrajs-MIT.txt |

The phone page served by Wi-Fi sharing (`electron/remote/`) is Pi Player's own code and uses no third-party library. No fonts are bundled; the app uses the operating system's fonts. No analytics, advertising or tracking SDK is included.

## Desktop runtime

Electron 44.4.5 is distributed under the MIT license together with Chromium, Node.js, V8, FFmpeg and other components under their respective licenses. The official Electron runtime is redistributed unmodified apart from packaging, branding and (on macOS) an ad-hoc signature. `LICENSE.electron.txt` and `LICENSES.chromium.html` from the official runtime are kept beside the Windows/Linux executable and inside the macOS app bundle's resources; those complete notices are authoritative. Electron's MIT license is also reproduced in licenses/Electron-MIT.txt.

Source references: https://github.com/electron/electron/tree/v44.4.5 — its `DEPS` file identifies the matching Chromium, Node.js and V8 revisions.

### FFmpeg (LGPL-2.1-or-later)

Media decoding uses the FFmpeg build that ships with Electron as a separate shared library (`ffmpeg.dll` on Windows, `libffmpeg.so` on Linux, `libffmpeg.dylib` inside the macOS framework). It is built without `--enable-gpl`, so the LGPL v2.1+ applies. Pi Player does not modify or statically link it; you may replace the library with a compatible build. The FFmpeg license text is included in `LICENSES.chromium.html`. The corresponding source is available from the Chromium source tree referenced by the Electron release above (`third_party/ffmpeg`) and from https://github.com/electron/electron/releases/tag/v44.4.5. For at least three years after we distribute a given version, we will also provide the complete corresponding FFmpeg source on request (https://github.com/cherub8128/Pi-Player-Releases/issues or cherub8128@gmail.com).

### Codecs

Playback relies on Chromium's decoders and, where available, the operating system's hardware decoders (for example HEVC on Windows with the HEVC extension, or on macOS). Pi Player adds no codec of its own. Formats that the runtime cannot decode (AVI, WMV, some MKV) are offered to the system's default player instead.

## Installers and packages

- **Windows**: the setup program is built with NSIS (zlib/libpng-style license, https://nsis.sourceforge.io/License) by electron-builder (MIT).
- **Linux AppImage**: the AppImage type-2 runtime (MIT) is prepended to the package. It may statically include libfuse (LGPL-2.1) and squashfuse (BSD-2-Clause). Their sources are available at https://github.com/AppImage/type2-runtime, https://github.com/libfuse/libfuse and https://github.com/vasi/squashfuse. The runtime is a separate program from Pi Player and can be replaced by extracting the AppImage (`--appimage-extract`). If you prefer not to use it, install the `.deb` package.
- **macOS**: dmg/zip built by electron-builder; no additional runtime.

## Build tools (not shipped)

Vite, TypeScript, @vitejs/plugin-react, electron-builder, Playwright, sharp (libvips) and png-to-ico are used only to build and test the app and are not included in the installers.

## Android edition

The Android app on Google Play is a separate Flutter build. Its bundled package licenses are listed in the app under **Settings → About → Licenses**.
