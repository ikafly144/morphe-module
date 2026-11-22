# Morphe Magisk Modules (AdGuard, Prime Video, Duolingo, Twitch & Amazon Music)

Automatically builds Magisk / KernelSU / APatch root mount modules and standalone patched APKs for **AdGuard**, **Amazon Prime Video**, **Duolingo**, **Twitch**, and **Amazon Music** using [ginDoki19/GinArena-patch](https://github.com/ginDoki19/GinArena-patch), [semicoloncolonel/mobile-morphe-patches](https://github.com/semicoloncolonel/mobile-morphe-patches), [hxreborn/morphe-patches](https://github.com/hxreborn/morphe-patches), [RookieEnough/De-Vanced](https://github.com/RookieEnough/De-Vanced), and [MorpheApp/morphe-desktop](https://github.com/MorpheApp/morphe-desktop).

Based on the [j-hc/revanced-magisk-module](https://github.com/j-hc/revanced-magisk-module) builder engine.

---

## 📱 Supported Apps & Patches

| App | Package Name | Architecture | Patches Included | Patch Source |
| :--- | :--- | :--- | :--- | :--- |
| **AdGuard** | `com.adguard.android` | `arm64-v8a` | `Unlock AdGuard Premium` | `ginDoki19/GinArena-patch` |
| **Amazon Prime Video** | `com.amazon.avod.thirdpartyclient` | `arm64-v8a` | `Skip ads`, `Rename shared permissions` | `semicoloncolonel/mobile-morphe-patches` |
| **Duolingo** | `com.duolingo` | `arm64-v8a` | `Unlock premium`, `Disable login integrity` | `hxreborn/morphe-patches` |
| **Twitch** *(disabled)* | `tv.twitch.android.app` | `arm64-v8a` | `Block audio ads`, `Block embedded ads`, `Block video ads`, `Show deleted messages`, `Auto claim channel points` | `RookieEnough/De-Vanced` |
| **Amazon Music** *(disabled)* | `com.amazon.mp3` | `arm64-v8a` | `Unlimited track skipping`, `Unlock Unlimited`, `Prevent log upload` | `RookieEnough/De-Vanced` |

---

## 🚀 Features

- **Automated Releases**: Scheduled daily check (`0 16 * * *` UTC) detects new releases of configured patch sources and automatically builds/releases updated modules.
- **Dual Outputs (`build-mode = "both"`)**: Generates both Magisk root modules (`.zip`) and non-root/direct patched APKs (`.apk`).
- **Magisk In-App Auto Update**: Magisk / KernelSU / APatch module updates are tracked via `updateJson` hosted on the `update` branch.
- **Manual Trigger**: Can be manually triggered at any time from the GitHub Actions tab via **Run workflow** (`workflow_dispatch`).
- **Resilient APK Sources**:
  - **AdGuard**: Official GitHub Releases (`AdguardTeam/AdguardForAndroid`) with APKMirror and Uptodown fallbacks.
  - **Prime Video / Duolingo**: APKMirror with Uptodown fallback and automatic sub-version normalization.

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

patches-source = "MorpheApp/morphe-patches"
cli-source = "MorpheApp/morphe-desktop"
rv-brand = "Morphe"
build-mode = "both"
arch = "arm64-v8a"
include-stock = "split"

[AdGuard]
app-name = "AdGuard"
pkg-name = "com.adguard.android"
patches-source = "ginDoki19/GinArena-patch"
version = "auto"
github-dlurl = "https://github.com/AdguardTeam/AdguardForAndroid"
apkmirror-dlurl = "https://www.apkmirror.com/apk/adguard-software-limited/adguard/"
uptodown-dlurl = "https://adguard.en.uptodown.com/android"
module-prop-name = "adguard-morphe"

[Prime-Video]
app-name = "Prime-Video"
pkg-name = "com.amazon.avod.thirdpartyclient"
patches-source = "semicoloncolonel/mobile-morphe-patches"
version = "auto"
apkmirror-dlurl = "https://www.apkmirror.com/apk/amazon-mobile-llc/amazon-prime-video/"
uptodown-dlurl = "https://amazon-prime-video.en.uptodown.com/android"
module-prop-name = "prime-video-morphe"

[Duolingo]
app-name = "Duolingo"
pkg-name = "com.duolingo"
patches-source = "hxreborn/morphe-patches"
version = "auto"
apkmirror-dlurl = "https://www.apkmirror.com/apk/duolingo/duolingo-duolingo/"
uptodown-dlurl = "https://duolingo.en.uptodown.com/android"
module-prop-name = "duolingo-morphe"
```

---

## 📜 Credits

- [ginDoki19/GinArena-patch](https://github.com/ginDoki19/GinArena-patch)
- [semicoloncolonel/mobile-morphe-patches](https://github.com/semicoloncolonel/mobile-morphe-patches)
- [hxreborn/morphe-patches](https://github.com/hxreborn/morphe-patches)
- [RookieEnough/De-Vanced](https://github.com/RookieEnough/De-Vanced)
- [MorpheApp/morphe-desktop](https://github.com/MorpheApp/morphe-desktop)
- [j-hc/revanced-magisk-module](https://github.com/j-hc/revanced-magisk-module)
