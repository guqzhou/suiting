# 随听 (SuiTing Music) - 官方全平台生产包与技术架构说明

---

## 最新稳定版生产打包产物下载 (v1.0.0)

| 平台 / 类型 | 安装包 / 构建包 | 文件大小 | 核心特性 / 运行环境 |
| :--- | :--- | :--- | :--- |
| **iOS 客户端** | [`SuiTing_iOS.ipa`](./SuiTing_iOS.ipa) | **33 MB** | 支持 iOS 16.1+ 灵动岛 / 锁屏实时活动（支持 TrollStore / 自签一键直装） |
| **Android 客户端** | [`SuiTing_Android.apk`](./SuiTing_Android.apk) | **26 MB** | 适配 Android 8.0 ~ Android 14+ 全机型 |
| **macOS 桌面端** | [`SuiTing_macOS.dmg`](./SuiTing_macOS.dmg) | **29 MB** | 原生 Universal 架构，深度适配 Apple Silicon (M1/M2/M3/M4) 与 Intel 芯片 |
| **Web 纯编译生产包** | [`SuiTing_Production_Web.zip`](./SuiTing_Production_Web.zip) | **9.7 MB** | 生产环境编译打包后的纯静态代码，解压即可直接部署至 GitHub Pages / Nginx / Vercel 在线播放 |

---

## 客户端核心技术栈架构 (Music Client Architecture)

```
+-------------------------------------------------------------+
|                       SuiTing Client                        |
+------------------------------+------------------------------+
|      Flutter 3.22 / Dart     |     SwiftUI & ActivityKit    |
|   (跨端 UI / 状态路由 / 解析)  |     (iOS 灵动岛 / 实时活动)    |
+------------------------------+------------------------------+
|              CoreAudio / WASAPI / AudioTrack                |
|                   (系统独占级底层高保真解码)                   |
+-------------------------------------------------------------+
```

1. **跨端核心架构**：
   * **Flutter 3.22.x & Dart 3.4.x**：高性能跨平台声明式渲染引擎，负责 iOS、Android、macOS 及 Windows 桌面端的一致性 UI 与业务流转。
2. **iOS 原生灵动岛与实时活动扩展**：
   * **Swift 5.9+ & SwiftUI**：原生编写的 WidgetKit 与 ActivityKit 拓展组件；
   * **Dynamic Island 自适应**：支持灵动岛紧凑态（Leading 珊瑚音符 Logo + Trailing 专辑封面与实时跳动波形）、展开态多维控制器与锁屏常驻超清播放卡片。
3. **音频引擎与高保真管线**：
   * **just_audio & audio_service**：底层系统级无缝音频调度管线；
   * 原生调用 macOS CoreAudio、Windows WASAPI 及 Android AudioTrack 底层通道，支持无损音频解析与后台低功耗常驻。
4. **状态流与持久化**：
   * **Provider 响应式状态总线**：统一管理播放列表、播放进度、歌词行实时同步与用户收藏；
   * **shared_preferences / 内存级缓存**：实现毫秒级设置持久化与本地数据存储。

---

## 法律免责与独立性声明

1. 本项目代码及客户端为**纯前端技术研究与个人学习探索成果，不含任何商业用途、盈利行为与商业价值**。
2. 本软件**不提供、不托管、不存储任何音频、歌词及图片等媒体文件**，所有播放内容均由用户端直接检索公开网络接口。音频版权均归各大原始版权方所有。
3. 使用者产生的一切使用、分发、下载等行为**均属于个人自主行为，与软件开发者及本项目无任何关联，开发者不承担任何直接或连带法律责任**。
