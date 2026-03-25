# screen-lock

A tool that enables OpenClaw to control macOS screen lock/unlock

[📖 中文说明](./README.md)

## Features

- 🔐 **Lock** - Lock your screen instantly
- 🔓 **Unlock** - Auto-type password from Keychain
- ⌨️ **HID Simulation** - System-level keyboard event simulation

## Installation

```bash
git clone https://github.com/CHen3054579806/screen-lock.git
cd screen-lock
```

## ⚠️ Important

After installing the skill, you need to configure your screen lock password with OpenClaw to use the unlock feature!

**Setup:**
1. When first using unlock, OpenClaw will guide you to set up the password
2. Or run manually:
   ```bash
   security add-generic-password -s "screen-lock-password" -w "your_password"
   ```

**Your password is stored securely in macOS Keychain.**

## 📋 Platform

- ✅ **macOS**: Tested and working
- ⚠️ **Windows**: Not verified, not supported yet

## Usage

### Lock Screen
```bash
./ble-unlock lock
```

### Unlock Screen
```bash
./ble-unlock unlock
```

## Requirements

- macOS 10.13 (High Sierra) or later
- Screen password configured

## Authors

- Author: [CHen3054579806](https://github.com/CHen3054579806) (2026)
- Inspired by: [ts1/BLEUnlock](https://github.com/ts1/BLEUnlock) (MIT License)

## License

This project uses a custom license.

**Commercial use is prohibited** without prior written permission from the author. For commercial licensing, please contact via GitHub.

See [LICENSE](./LICENSE) for details.
