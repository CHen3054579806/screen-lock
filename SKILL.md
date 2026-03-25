# 屏幕锁屏/解锁技能

## 功能
- 锁定屏幕
- 解锁屏幕（自动从 Keychain 获取密码）

## 使用方式

### 锁屏
```bash
~/.hanako/skills/screen-lock/ble-unlock lock
```

### 解锁
```bash
~/.hanako/skills/screen-lock/ble-unlock unlock
```

## 技术原理

基于 [BLEUnlock](https://github.com/ts1/BLEUnlock) 开源项目，提取核心解锁逻辑封装。

### 解锁流程
1. **唤醒屏幕**：`IOPMAssertionDeclareUserActivity` 唤醒显示器
2. **输入密码**：
   - 创建 HID 事件源：`CGEventSourceCreate(kCGEventSourceStateHIDSystemState)`
   - 使用 `CGEventCreateKeyboardEvent` + `CGEventKeyboardSetUnicodeString` 输入 Unicode 字符串
   - 使用 `CGEventPost(kCGHIDEventTap, event)` 投递事件
3. **提交登录**：按 Return 键 (virtualKey 52)

### 锁屏原语
使用 IOKit 关闭显示器：
```c
io_registry_entry_t reg = IORegistryEntryFromPath(kIOMainPortDefault, "IOService:/IOResources/IODisplayWrangler");
IORegistryEntrySetCFProperty(reg, CFSTR("IORequestIdle"), kCFBooleanTrue);
```

## 依赖
- macOS 系统
- 辅助功能权限（用于 HID 事件模拟）

## ⚠️ 首次使用

安装技能后，你需要告诉 OpenClaw 你的锁屏密码：

```bash
security add-generic-password -s "screen-lock-password" -w "你的锁屏密码"
```

密码存储在 macOS Keychain 中，安全可靠。

## 作者
- 作者：[CHen3054579806](https://github.com/CHen3054579806) (2026)
- 思路来源：[ts1](https://github.com/ts1/BLEUnlock) (MIT License)
