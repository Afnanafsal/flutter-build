# 🚀 Flutter Build & Telegram Release Action

This GitHub Action builds your Flutter APK and sends it to a Telegram group automatically on every push to `main` or on manual trigger.

## 🔧 Inputs

| Name              | Description                    | Required | Default     |
|-------------------|--------------------------------|----------|-------------|
| `telegram_token`  | Telegram Bot Token             | ✅       |             |
| `telegram_chat_id`| Telegram Chat or Group ID      | ✅       |             |
| `github_token`    | GitHub Token for release       | ✅       |             |
| `flutter_version` | Flutter version                | ❌       | `3.19.0`    |
| `java_version`    | Java version                   | ❌       | `17`        |

## 🚀 Usage

```yaml
name: Flutter Build & Release

on:
  push:
    branches: [main]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: 🔨 Flutter Build & Telegram Release
        uses: afnanafsal/flutter-build-release@v1
        with:
          telegram_token: ${{ secrets.TELEGRAM_BOT_TOKEN }}
          telegram_chat_id: ${{ secrets.TELEGRAM_CHAT_ID }}
          github_token: ${{ secrets.GITHUB_TOKEN }}
