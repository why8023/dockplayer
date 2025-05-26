# DockPlayer

一个在 macOS Dock 上播放视频的创新应用

## 项目概述

DockPlayer 是一个独特的 macOS 应用程序，允许用户直接在 Dock 图标上播放视频文件。这个项目旨在为用户提供一种全新的多媒体体验，让视频播放变得更加便捷和有趣。

## 核心功能

- 📹 在 Dock 图标上直接播放视频
- 🎮 支持播放控制（播放/暂停/停止）
- 📁 支持多种视频格式（MP4、MOV、AVI 等）
- 🔊 音频控制
- 📱 迷你播放器模式
- 🎨 自定义 Dock 图标样式

## 技术选型

### 主要技术栈

1. **开发语言**: Swift
   - 原生 macOS 开发，性能最优
   - 完整的 Cocoa 框架支持
   - 现代化的语言特性

2. **UI 框架**: SwiftUI + AppKit
   - SwiftUI: 现代化 UI 开发
   - AppKit: 系统级功能和 Dock 集成

3. **视频处理**: AVFoundation
   - 苹果官方音视频框架
   - 支持多种格式
   - 硬件加速支持

4. **系统集成**: 
   - NSApplication.shared.dockTile
   - NSImageView for Dock tile customization
   - NSWorkspace for file handling

### 备选方案

1. **Objective-C + Cocoa** (传统方案)
   - 更成熟的文档和示例
   - 更直接的系统 API 访问

2. **Electron + Node.js** (跨平台方案)
   - 快速开发
   - 但性能较差，系统集成受限

## 实现思路

### 1. Dock 图标视频播放
```
NSApplication.shared.dockTile.contentView = customVideoView
NSApplication.shared.dockTile.display()
```

### 2. 核心架构
```
DockPlayer/
├── Core/
│   ├── VideoPlayer.swift          # 视频播放引擎
│   ├── DockManager.swift          # Dock 集成管理
│   └── FileManager.swift          # 文件处理
├── UI/
│   ├── MainWindow.swift           # 主窗口
│   ├── PlayerControls.swift       # 播放控制
│   └── SettingsView.swift         # 设置界面
├── Utils/
│   ├── VideoDecoder.swift         # 视频解码
│   └── Extensions.swift           # 扩展功能
└── Resources/
    ├── Assets.xcassets           # 图标资源
    └── Info.plist               # 应用配置
```

### 3. 关键技术点

#### Dock 集成
- 使用 `NSDockTile` API 自定义 Dock 图标
- 实现视频帧的实时更新
- 处理 Dock 图标的点击事件

#### 视频播放
- `AVPlayer` 播放视频
- `AVPlayerLayer` 渲染到自定义视图
- 视频帧提取和处理

#### 性能优化
- 视频帧率控制（避免过度消耗 CPU）
- 内存管理和缓存策略
- 后台播放优化

## 开发计划

### 第一阶段：基础功能 (1-2 周)
- [ ] 创建基本的 macOS 应用项目
- [ ] 实现基础的视频播放功能
- [ ] 集成 Dock 图标自定义功能
- [ ] 实现简单的播放/暂停控制

### 第二阶段：核心功能 (2-3 周)
- [ ] 优化视频在 Dock 上的显示效果
- [ ] 添加文件选择和拖拽支持
- [ ] 实现播放控制菜单
- [ ] 添加音频控制功能
- [ ] 支持多种视频格式

### 第三阶段：用户体验 (1-2 周)
- [ ] 设计和实现用户界面
- [ ] 添加设置和配置选项
- [ ] 实现快捷键支持
- [ ] 添加播放历史记录

### 第四阶段：高级功能 (2-3 周)
- [ ] 迷你播放器模式
- [ ] 视频质量和尺寸优化
- [ ] 播放列表支持
- [ ] 自动播放功能
- [ ] 性能优化和内存管理

### 第五阶段：测试和发布 (1-2 周)
- [ ] 全面测试和 Bug 修复
- [ ] 性能优化
- [ ] 用户文档编写
- [ ] App Store 准备和发布

## 技术挑战

1. **Dock 图标限制**
   - Dock 图标尺寸限制
   - 刷新率平衡（性能 vs 流畅度）
   - 系统权限和兼容性

2. **视频处理**
   - 不同格式的兼容性
   - 大文件处理
   - 硬件加速利用

3. **用户体验**
   - 直观的控制方式
   - 最小化系统资源占用
   - 稳定性保证

## 环境要求

- macOS 12.0+ (Monterey)
- Xcode 14.0+
- Swift 5.7+

## 开始开发

```bash
# 克隆项目
git clone https://github.com/yourusername/dockplayer.git

# 进入项目目录
cd dockplayer

# 使用 Xcode 打开项目
open DockPlayer.xcodeproj
```

## 贡献指南

欢迎提交 Issue 和 Pull Request！

## 许可证

MIT License - 详见 [LICENSE](LICENSE) 文件

---

**注意**: 这是一个实验性项目，某些功能可能需要系统权限，请确保了解相关的 macOS 安全和隐私政策。