# Key Mapper 简体中文开发分支

本仓库是 [keymapperorg/KeyMapper](https://github.com/keymapperorg/KeyMapper) 的独立 Fork，保留上游 GPL-3.0 许可证。原版介绍见 [README.upstream.md](README.upstream.md)。

## 开发目标

为自定义蓝牙键盘提供易懂的按键映射：按一次打开 DiPlay、豆包或其他安卓应用，支持短按、长按和多个动作。重点验证无密码专用手机上“熄屏收键 → 唤醒 → 收起锁屏 → 启动应用”的完整流程。上述实机链路尚待本分支验证，不能当作兼容性承诺。

## 简体中文界面

上游已包含 `base/src/main/res/values-zh-rCN/strings.xml`，无需从头翻译。手机系统语言设置为简体中文时，应用会使用已有中文资源；未翻译的新条目可能回退到英文。专家模式、熄屏触发与启动应用等已有中文说明。

首次使用：启用 Key Mapper 无障碍服务；需要熄屏收键时，启用专家模式，并在专家模式下重新录入蓝牙键盘按键。root 授权可以简化专家模式启动。先配置“启动应用”动作，再单独验证熄屏与无密码锁屏行为。

## 分支与源码

- `develop`：保留上游开发基线，便于同步。
- `codex/zh-cn`：中文说明与后续本地化开发。
- 上游远程：`upstream`；自己的仓库：`origin`。

```powershell
git clone -b codex/zh-cn https://github.com/Ronnie2026/KeyMapper.git
cd KeyMapper
.\gradlew.bat assembleDebug
```

构建依赖以 Gradle 配置为准，包含 Android SDK、JDK、NDK 和 Rust 原生模块。当前开发基线要求 compileSdk 37，不可直接沿用旧三键项目的 API 30 构建脚本。详细规范见 CLAUDE.md；此分支暂未构建自定义 APK。

## 安装与签名

Fork 不会自动复制上游 Release。体验版本请使用 [上游官方 Release](https://github.com/keymapperorg/KeyMapper/releases)。本分支自编译 APK 与上游签名不同，不能保证覆盖官方版；调试版本使用独立的 `.debug` 包名。此前 `android-ble-key-mapper` 是独立项目，不会被此 Fork 替换。
