# 🛠️ Flutter Build & Telegram Release Action

[![Build Status](https://img.shields.io/badge/Build%20Status-Online-brightgreen?style=for-the-badge&logo=github)](https://github.com/Afnanafsal/flutter-build/actions/workflows/example.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
![Flutter](https://img.shields.io/badge/Flutter-%E2%9D%A4-blue?logo=flutter)
![GitHub Release](https://img.shields.io/github/v/release/afnanafsal/flutter-build)
![Last Commit](https://img.shields.io/github/last-commit/afnanafsal/flutter-build)
![Platform](https://img.shields.io/badge/platform-GitHub%20Actions-blue)
![Telegram](https://img.shields.io/badge/Telegram-Bot-blue?logo=telegram)

> Automatically build your Flutter project (APK / AAB / Web), auto-increment version, create GitHub Releases, and send the final build directly to a Telegram group! 🚀

---

## ✨ Features

- 🔨 Build for **APK**, **AAB**, or **Web**
- 🔁 **Auto-versioning** in `pubspec.yaml`
- 🚀 **Release** generated artifacts to **GitHub Releases**
- 📤 **Upload to Telegram** bot / group
- 🧪 Trigger on push, PR, or manually (`workflow_dispatch`)
- 📦 Supports **split-per-ABI APKs**

---

## 🔧 Inputs

| Input              | Description                             | Required | Default     |
|--------------------|-----------------------------------------|----------|-------------|
| `telegram_token`   | Telegram Bot Token                      | ✅       |             |
| `telegram_chat_id` | Telegram Chat or Group ID               | ✅       |             |
| `github_token`     | GitHub Token (for creating releases)    | ✅       |             |
| `flutter_version`  | Flutter version                         | ❌       | `3.19.0`    |
| `java_version`     | Java version                            | ❌       | `17`        |
| `build_mode`       | `apk`, `aab`, `web`, or `all`           | ❌       | `apk`       |

---

## 🚀 Quick Usage

```yaml
name: Flutter Build & Release

on:
  push:
    branches: [main]
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: 🔨 Flutter Build & Telegram Release
        uses: afnanafsal/flutter-build@v1
        with:
          telegram_token: ${{ secrets.TELEGRAM_BOT_TOKEN }}
          telegram_chat_id: ${{ secrets.TELEGRAM_CHAT_ID }}
          github_token: ${{ secrets.GITHUB_TOKEN }}
          flutter_version: '3.19.0'
          java_version: '17'
          build_mode: 'all'
```

---

## 📤 Telegram Bot Setup

1. Open Telegram and search for [@BotFather](https://t.me/BotFather).
2. Send `/newbot` and follow the prompts to set a name and username.
3. Copy the bot token provided.
4. Add your bot to your group and make it an admin.
5. Get the Chat ID:
   - Visit: `https://api.telegram.org/bot<YOUR_BOT_TOKEN>/getUpdates`
   - Send a message in the group.
   - Find `"chat":{"id":-123456789,...}` in the response.

---

## 📁 Outputs

After each run, your build is:

- ✅ Uploaded to **GitHub Releases**
- 📤 Sent to **Telegram** (with progress messages)

### Artifacts:

- `build/app/outputs/flutter-apk/*.apk`
- `build/app/outputs/bundle/release/*.aab`
- `build/web/` folder (if web mode enabled)

---

## ✅ Best Practices

- Use this in private repos or secure your secrets properly.
- Set appropriate `build_mode` to optimize CI time.
- Keep your Telegram bot admin-only in the group to prevent spam.

---

## 🏷️ Tags

`Flutter`, `GitHub Actions`, `Telegram`, `CI/CD`, `Automation`, `APK`, `AAB`, `Web`

---
