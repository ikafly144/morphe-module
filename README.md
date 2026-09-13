# Morphe Magisk Modules (AdGuard & Prime Video)

Automatically builds Magisk / KernelSU / APatch root mount modules and standalone patched APKs for **AdGuard** and **Amazon Prime Video** using [hoo-dles/morphe-patches](https://github.com/hoo-dles/morphe-patches) and [MorpheApp/morphe-cli](https://github.com/MorpheApp/morphe-cli).

Based on the [j-hc/revanced-magisk-module](https://github.com/j-hc/revanced-magisk-module) builder engine.

---

## 📱 Supported Apps & Patches

| App | Package Name | Architecture | Patches Included |
| :--- | :--- | :--- | :--- |
| **AdGuard** | `com.adguard.android` | `arm64-v8a` | `Enable Premium` |
| **Amazon Prime Video** | `com.amazon.avod.thirdpartyclient` | `arm64-v8a` | `Enable speed control`, `Skip ads` |

---

## 🚀 Features

- **Automated Releases**: Scheduled daily check (`0 16 * * *` UTC) detects new releases of `hoo-dles/morphe-patches` and automatically builds/releases updated modules.
- **Dual Outputs (`build-mode = "both"`)**: Generates both Magisk root modules (`.zip`) and non-root/direct patched APKs (`.apk`).
- **Magisk In-App Auto Update**: Magisk / KernelSU / APatch module updates are tracked via `updateJson` hosted on the `update` branch.
- **Manual Trigger**: Can be manually triggered at any time from the GitHub Actions tab via **Run workflow** (`workflow_dispatch`).
- **Resilient APK Sources**:
  - **AdGuard**: Official GitHub Releases (`AdguardTeam/AdguardForAndroid`) with APKMirror and Uptodown fallbacks.
  - **Prime Video**: APKMirror with Uptodown fallback and automatic sub-version normalization.

---

## 📥 Installation

1. Navigate to the [Releases](../../releases) page.
2. Download the desired file:
   - **For Root (Magisk / KernelSU / APatch)**: Download the `*-module.zip` and flash it in your root manager.
   - **For Non-Root / Standalone**: Download the `.apk` and install directly (note: for Prime Video, ensure clean install or matched signatures).

---

## ⚙️ Configuration

The build configuration is located in `config.toml`:

```toml
enable-module-update = true
parallel-jobs = 1
remove-rv-integrations-checks = false

patches-source = "hoo-dles/morphe-patches"
cli-source = "MorpheApp/morphe-cli"
rv-brand = "Morphe"
build-mode = "both"
arch = "arm64-v8a"

[AdGuard]
app-name = "AdGuard"
pkg-name = "com.adguard.android"
version = "auto"
github-dlurl = "https://github.com/AdguardTeam/AdguardForAndroid"
apkmirror-dlurl = "https://www.apkmirror.com/apk/adguard-software-limited/adguard/"
uptodown-dlurl = "https://adguard.en.uptodown.com/android"
module-prop-name = "adguard-morphe"

[Prime-Video]
app-name = "Prime-Video"
pkg-name = "com.amazon.avod.thirdpartyclient"
version = "auto"
apkmirror-dlurl = "https://www.apkmirror.com/apk/amazon-mobile-llc/amazon-prime-video/"
uptodown-dlurl = "https://amazon-prime-video.en.uptodown.com/android"
excluded-patches = "'Rename shared permissions'"
module-prop-name = "prime-video-morphe"
```

---

## 📜 Credits

- [hoo-dles/morphe-patches](https://github.com/hoo-dles/morphe-patches)
- [MorpheApp/morphe-cli](https://github.com/MorpheApp/morphe-cli)
- [j-hc/revanced-magisk-module](https://github.com/j-hc/revanced-magisk-module)
