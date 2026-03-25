# screen-lock

让 OpenClaw 可以控制 macOS 屏幕锁屏/解锁的工具

[📖 English README](./README_en.md)

## 功能

- 🔐 **锁屏** - 一键锁定屏幕
- 🔓 **解锁** - 自动输入密码解锁（从 Keychain 获取）
- ⌨️ **HID 模拟** - 使用系统级键盘事件模拟输入

## 安装

```bash
git clone https://github.com/CHen3054579806/screen-lock.git
cd screen-lock
```

## ⚠️ 重要提示

安装技能后，你需要告诉 OpenClaw 你的锁屏密码才能使用解锁功能！

**配置方法：**
1. 首次使用解锁功能时，OpenClaw 会引导你设置密码
2. 或者手动运行：
   ```bash
   security add-generic-password -s "screen-lock-password" -w "你的锁屏密码"
   ```

**密码存储在 macOS Keychain 中，安全可靠。**

## 使用方法

### 锁屏
```bash
./ble-unlock lock
```

### 解锁
```bash
./ble-unlock unlock
```

## 系统要求

- macOS 10.13 (High Sierra) 或更高版本
- 已设置屏幕密码

## 作者

- 作者：[CHen3054579806](https://github.com/CHen3054579806) (2026)
- 思路来源：[ts1/BLEUnlock](https://github.com/ts1/BLEUnlock) (MIT License)

## 许可证

本项目采用自定义许可证。

**禁止**未经授权的商业使用。如需商业使用，请联系作者获得授权。

详细信息请查看 [LICENSE](./LICENSE) 文件。
