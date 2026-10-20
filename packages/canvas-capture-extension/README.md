---
title: 'Remotion Canvas Capture Chrome Extension'
tags: ['chrome-extension', 'canvas', 'screen-recording', 'h264', 'vp9', 'mediabunny']
category: 'tooling'
created: '2026-10-20'
updated: '2026-10-20'
source: 'external'
type: 'index'
status: 'stable'
lifecycle: 'active'
---

# Remotion Canvas Capture Chrome Extension

> Record an area—or a whole webpage—as a high-resolution H.264 MP4 or VP9 WebM using Chromium's experimental HTML-in-canvas implementation.

---

💡 概述

Canvas Capture 是一个 Chrome 浏览器扩展，利用 Chromium 的实验性 HTML-in-canvas 实现，将网页区域或整个页面录制为高分辨率 H.264 MP4 或 VP9 WebM 视频。录制内容可直接导入 Remotion 进行进一步编辑。

---

⚡ 功能

- **区域/整页录制**：选择页面任意区域或整个视口进行录制
- **高分辨率输出**：默认 2K (2560x1440) 分辨率，支持通过缩放滑块调整
- **多格式支持**：H.264 MP4 和 VP9 WebM 编码
- **Agentic shot 设置**：向 WebMCP 代理暴露 `setup_shot`、`get_shot`、`save_recording` 接口
- **拖拽预览捕获**：在录制中保留拖拽操作的预览图像
- **一键导入 Remotion**：录制完成后直接发送至 remotion.dev 进行编辑

---

📊 指标

「待补充」

---

🏛️ 设计

### 录制原理

整页 DOM 子树以显示器原生像素密度绘制到 `content="drawable"` 的 canvas 中，选中区域裁剪后复制到可复用的 `OffscreenCanvas`。控件挂载在录制区域之外，不会出现在画面中。录制结束后页面内容恢复原状。

### 传输协议

录制文件通过 Chrome 扩展的 `externally_connectable` 消息通道传输至 remotion.dev。扩展生成一次性传输令牌（10 分钟有效），通过 URL fragment 传递。目标页面验证来源、目标路径、标签页 ID 和令牌后接收分块数据，确认后扩展删除本地录制文件。中断传输可在令牌过期前从同一标签页重试。

### Canvas 兼容性

录制期间，现有 canvas 元素和录制区域内新建的 canvas 会临时设置 `content="drawable"` 以避免 Chromium 在原点处裁剪位图，录制完成后恢复原始属性。

### 拖拽预览

- 默认预览：在页面绘制拖拽起始变化后快照可拖拽源元素，保留抓取点
- 自定义预览：通过 `DataTransfer.setDragImage()` 提供的预览替换默认快照，使用指定的热点偏移
- 普通元素保留合成背景；自身建立层叠上下文的图像和元素保留透明度
- 预览仅添加到录制帧中，拖拽结束或放置后消失
- 不支持：文本选择拖拽、跨标签页/应用拖拽、Shadow DOM 和跨域内容

---

📁 目录

「待补充」

---

🔗 资源

- [Agentic shot setup 文档](https://www.remotion.dev/docs/canvas-capture/agentic-shot-setup)

---

🚀 快速开始

### 浏览器要求

需要 Chrome 157.0.8080.0 或更新版本，并启用 Canvas Draw Element。可使用 Chrome、Chrome Canary 或 Chrome for Testing。

控件打开时，工具栏上方的红色提示会说明未满足的浏览器要求。过旧的浏览器会显示最低 Chrome 版本。如果所需 API 不可用，提示中提供 **Open Chrome flags** 按钮，打开 `chrome://flags/#canvas-draw-element` 并启用后重启 Chrome。

### 安装兼容浏览器

```bash
packages/canvas-capture-extension/scripts/install-browser.sh
```

安装位置：

```text
/Users/jonathanburger/Applications/Recorder Chrome.app
```

启动命令：

```bash
'/Users/jonathanburger/Applications/Recorder Chrome.app/Contents/MacOS/Google Chrome for Testing' \
  --user-data-dir='/Users/jonathanburger/Library/Application Support/Remotion Canvas Capture' \
  --enable-features=CanvasDrawElement \
  --no-first-run \
  --no-default-browser-check
```

加载扩展目录：

```text
/Users/jonathanburger/Applications/Remotion Canvas Capture Extension
```

### 构建与安装（生产）

1. 从仓库根目录运行 `.agents/skills/canvas-capture-extension/scripts/rebuild-extension.sh --repo "$PWD"`，此脚本创建生产 WXT 构建并将完整扩展安装到工作树之外
2. 在 Chrome 中打开 `chrome://extensions`，启用 **开发者模式**，选择 **加载已解压的扩展程序**
3. 选择 `/Users/jonathanburger/Applications/Remotion Canvas Capture Extension`
4. 如尚未启用，在 `chrome://flags/#canvas-draw-element` 中启用 Canvas Draw Element 并重启 Chrome

### 使用

点击扩展图标切换页面内控件。选择区域或选择 **Entire page** 以录制完整视口，然后开始录制。点击选中区域旁的缩放值可显示滑块并调整录制缩放比例。缩放滑块的最大值根据选中区域自适应，输出上限约为 4K。控件显示选定格式和取整后的输出尺寸，仅在浏览器确认支持 Mediabunny 的高质量实时配置后才启用录制。

停止录制后，可直接在 [remotion.dev/new](https://remotion.dev/new) 中打开、在 [remotion.dev/convert](https://remotion.dev/convert) 中检查，或保存到磁盘。

---

⚙️ 技术栈

- **Chrome Extension (Manifest V3)**：扩展框架
- **WXT**：扩展开发工具，Vite 驱动的 HMR
- **Canvas Draw Element API**：Chromium 实验性 HTML-in-canvas 渲染
- **Mediabunny**：高质量实时编码配置
- **OffscreenCanvas**：录制帧的离屏渲染